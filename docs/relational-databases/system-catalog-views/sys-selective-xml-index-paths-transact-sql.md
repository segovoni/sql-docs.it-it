---
title: selective_xml_index_paths (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- xml_schema_attributes_TSQL
- xml_schema_attributes
- sys.xml_schema_attributes_TSQL
- sys.xml_schema_attributes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_attributes catalog view
ms.assetid: 07a73d71-ec3e-4894-947a-5859ca62c606
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0078ffca12182f0478f67b05d03dd14eb64b3ef8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33221412"
---
# <a name="sysselectivexmlindexpaths-transact-sql"></a>sys.selective_xml_index_paths (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Disponibili a partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1, ogni riga in sys.selective_xml_index_paths rappresenta un percorso promosso per un determinato indice XML selettivo.  
  
 Se si crea un indice XML selettivo per la colonna xmlcol della tabella T con l'istruzione seguente:  
  
```  
CREATE SELECTIVE XML INDEX sxi1 ON T(xmlcol)   
FOR ( path1 = '/a/b/c' AS XQUERY 'xs:string',  
      path2 = '/a/b/d' AS XQUERY 'xs:double'  
    )  
```  
  
 Verranno aggiunte due nuove righe in sys.selective_xml_index_paths corrispondenti all'indice sxi1.  

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID della tabella con la colonna XML.|  
|**index_id**|**int**|ID univoco dell'indice XML selettivo.|  
|**path_id**|**int**|ID del percorso XML promosso|  
|**path**|**nvarchar(4000)**|Percorso promosso. Ad esempio, '/a/b/c/d/e'.|  
|**name**|**sysname**|Nome del percorso.|  
|**path_type**|**tinyint**|0 = XQUERY<br /><br /> 1 = SQL|  
|**path_type_desc**|**sysname**|In base a **path_type** il valore 'XQUERY' o 'SQL'.|  
|**xml_component_id**|**int**|ID univoco del componente di XML Schema nel database.|  
|**xquery_type_description**|**nvarchar(4000)**|Nome del tipo XSD specificato.|  
|**is_xquery_type_inferred**|**bit**|1 = il tipo viene dedotto.|  
|**xquery_max_length**|**smallint**|Lunghezza massima (in caratteri) del tipo XSD.|  
|**is_xquery_max_length_inferred**|**bit**|1 = la lunghezza massima viene dedotta.|  
|**is_node**|**bit**|0 = hint node() non presente.<br /><br /> 1 = hint di ottimizzazione node() applicato.|  
|**system_type_id**|**tinyint**|ID del tipo di sistema della colonna.|  
|**user_type_id**|**tinyint**|ID del tipo di utente della colonna.|  
|**max_length**|**smallint**|Lunghezza massima (in byte) del tipo.<br /><br /> -1 = La colonna è di tipo varchar(max), nvarchar(max), varbinary(max) o xml.|  
|**precisione**|**tinyint**|Precisione massima del tipo se numerico. In caso contrario, 0|  
|**scala**|**tinyint**|Scala massima del tipo se numerico. Altrimenti, è impostato su 0.|  
|**nome_regole_di_confronto**|**sysname**|Nome delle regole di confronto del tipo se di tipo carattere. In caso contrario, NULL.|  
|**is_singleton**|**bit**|0 = hint SINGLETON non presente.<br /><br /> 1 = hint di ottimizzazione SINGLETON applicato.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML schema &#40;sistema di tipi XML&#41; viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
