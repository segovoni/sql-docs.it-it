---
title: Sys.sensitivity_classifications (Transact-SQL) | Microsoft Docs
ms.date: 06/17/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology: t-sql
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.custom: ''
ms.manager: craigg
ms.author: giladm
author: giladmit
f1_keywords:
- 'sys.sensitivity_classifications '
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sensitivity_classifications statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: d0adbbeb82c06d6a44f3a7439bcbf479d7358401
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37993793"
---
# <a name="syssensitivityclassifications-transact-sql"></a>Sys.sensitivity_classifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Restituisce una riga per ogni elemento classificato nel database.

|Nome colonna|Tipo di dati|Description|
|-----------------|---------------|-----------------|  
|**class**|**int**|Identifica la classe dell'elemento su cui è inclusa la classificazione|  
|**class_desc**|**varchar(16)**|Una descrizione della classe dell'elemento su cui è inclusa la classificazione|  
|**major_id**|**int**|ID dell'elemento su cui è inclusa la classificazione. < br \>< br \>se classe è 0, major_id è sempre 0.<br>Se la classe è 1, 2 o 7, major_id è object_id.|  
|**minor_id**|**int**|ID secondario dell'elemento su cui è inclusa la classificazione, interpretato in base alla relativa classe.<br><br>Se classe = 1, minor_id è column_id (se colonna), altrimenti 0 (se oggetto).<br>Se la classe è 2, minor_id è parameter_id.<br>Se classe = 7, minor_id è index_id. |  
|**label**|**sysname**|L'etichetta (leggibili) assegnata per la classificazione di riservatezza|  
|**label_id**|**sysname**|Un ID associato all'etichetta, che può essere usato da un sistema di protezione delle informazioni, ad esempio Azure Information Protection (AIP)|  
|**information_type**|**sysname**|Il tipo di informazioni (leggibili) assegnato per la classificazione di riservatezza|  
|**information_type_id**|**sysname**|Un ID associato al tipo di informazioni, che può essere usato da un sistema di protezione delle informazioni, ad esempio Azure Information Protection (AIP)|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>Note  

- Questa visualizzazione fornisce visibilità dello stato di classificazione del database. Può essere utilizzato per gestire le classificazioni di database, nonché per la generazione di report.
- È supportata attualmente solo la classificazione delle colonne di database. Di conseguenza:
    - **classe** -avrà sempre il valore 1, che rappresenta una colonna,
    - **class_desc** -il valore è sempre *OBJECT_OR_COLUMN*
    - **major_id** -rappresenta l'ID della tabella contenente la colonna classificata, with sys.all_objects.object_id corrispondente
    - **minor_id** -rappresenta l'ID della colonna in cui la classificazione è presente, corrispondente con sys.all_columns.column_id

## <a name="examples"></a>Esempi

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. Elenco di colonne classificate tutte e la relativa classificazione corrispondente

Nell'esempio seguente viene restituita una tabella che elenca il nome della tabella, nome di colonna, l'etichetta, assegnare un'etichetta, informazioni tipo ID, ID di tipo di informazioni per ogni colonna classificata nel database.

```sql
SELECT
    sys.all_objects.name AS TableName, sys.all_columns.name As ColumnName,
    Label, Label_ID, Information_Type, Information_Type_ID
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="see-also"></a>Vedere anche  

[AGGIUNGERE la SENSIBILITÀ CLASSIFICTION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[ELIMINARE la SENSIBILITÀ CLASSIFICTION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[Introduzione a SQL Information Protection](http://aka.ms/sqlip)
