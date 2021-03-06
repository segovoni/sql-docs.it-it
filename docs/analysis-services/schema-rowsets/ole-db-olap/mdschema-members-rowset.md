---
title: Set di righe mdschema_members | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ffe79581b338941ab4fcd379d7da48ce33028633
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34029502"
---
# <a name="mdschemamembers-rowset"></a>Set di righe MDSCHEMA_MEMBERS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Descrive i membri all'interno di un database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **MDSCHEMA_MEMBERS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Nome del database a cui appartiene il membro.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Nome dello schema a cui appartiene il membro.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Nome del cubo a cui appartiene il membro.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**||Nome univoco della dimensione a cui appartiene il membro.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**||Nome univoco della gerarchia a cui appartiene il membro.|  
|**LEVEL_UNIQUE_NAME**|**DBTYPE_WSTR**||Nome univoco del livello a cui appartiene il membro.|  
|**LEVEL_NUMBER**|**DBTYPE_UI4**||Distanza del membro dalla radice della gerarchia. Il livello radice è zero (0).|  
|**MEMBER_ORDINAL**|**DBTYPE_UI4**||(Obsoleto) Restituisce sempre **0**.|  
|**MEMBER_NAME**|**DBTYPE_WSTR**||Nome del membro.|  
|**MEMBER_UNIQUE_NAME**|**DBTYPE_WSTR**||Nome univoco del membro.|  
|**MEMBER_TYPE**|**DBTYPE_I4**||Tipo del membro:<br /><br /> **MDMEMBER_TYPE_UNKNOWN** (**0**)<br /><br /> **MDMEMBER_TYPE_REGULAR** (**1**)<br /><br /> **MDMEMBER_TYPE_ALL** (**2**)<br /><br /> **A MDMEMBER_TYPE_MEASURE** (**3**)<br /><br /> **MDMEMBER_TYPE_FORMULA** (**4**)<br /><br /> <br /><br /> Si noti che <br />                    **MDMEMBER_TYPE_FORMULA**ha la precedenza su **MDMEMBER_TYPE_MEASURE**. Ad esempio, se è formula (calcolato) membro nella dimensione Measures, è elencato come **MDMEMBER_TYPE_FORMULA**.|  
|**MEMBER_GUID**|**DBTYPE_GUID**||GUID del membro. **NULL** se è presente alcuna GUID.|  
|**MEMBER_CAPTION**|**DBTYPE_WSTR**||Etichetta o didascalia associata al membro. Utilizzata principalmente a scopo di visualizzazione. Se non esiste una didascalia, **MEMBER_NAME** viene restituito.|  
|**CHILDREN_CARDINALITY**|**DBTYPE_UI4**||Numero di elementi figlio del membro. Poiché può trattarsi di una stima, è necessario che i consumer non considerino questo valore come il conteggio esatto. I provider restituiscono la migliore stima possibile.|  
|**PARENT_LEVEL**|**DBTYPE_UI4**||Distanza dell'elemento padre del membro dal livello radice della gerarchia. Il livello radice è zero (0).|  
|**PARENT_UNIQUE_NAME**|**DBTYPE_WSTR**||Nome univoco del nodo padre del membro. Viene restituito**NULL** per tutti i membri al livello di radice.|  
|**PARENT_COUNT**|**DBTYPE_UI4**||Numero di elementi padre del membro.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Questa colonna restituisce sempre un **NULL** valore.<br /><br /> Questa colonna esiste per garantire la compatibilità con le versioni precedenti.|  
|**ESPRESSIONE**|**DBTYPE_WSTR**||L'espressione per i calcoli, se il membro è di tipo **MDMEMBER_TYPE_FORMULA**.|  
|**MEMBER_KEY**|**DBTYPE_WSTR**||Valore della colonna chiave del membro. Restituisce **NULL** se il membro ha una chiave composta.|  
|**IS_PLACEHOLDERMEMBER**|**DBTYPE_BOOL**||Valore booleano che indica se un membro è un membro segnaposto per una posizione vuota in una gerarchia della dimensione.<br /><br /> È valido solo se il **MDX Compatibility** proprietà è stata impostata su 2.|  
|**IS_DATAMEMBER**|**DBTYPE_BOOL**||Valore booleano che indica se il membro è un membro dati.<br /><br /> Restituisce True se il membro è un membro dei dati.|  
|**AMBITO**|**DBTYPE_I4**||Ambito del membro. Il membro può essere un membro calcolato della sessione o un membro calcolato globale. Restituisce la colonna **NULL** per i membri non calcolati. I possibili valori della colonna sono i seguenti:<br /><br /> MDMEMBER_SCOPE_GLOBAL=1<br /><br /> MDMEMBER_SCOPE_SESSION=2|  
|**Zero o più colonne aggiuntive**|**DBTYPE_UI2**||Non viene restituita alcuna proprietà se i membri possono essere restituiti da più livelli. Ad esempio, se è l'operatore di albero **padre** e **SELF** per una gerarchia non padre-figlio, viene restituita alcuna proprietà di membro.<br /><br /> Si applica alle gerarchie incomplete dove gli operatori di albero possono restituire membri da livelli diversi, ad esempio se il livello precedente contiene spazi vuoti ed è necessario che il membro disponga di un elemento padre.|  
  
 Il set di righe viene ordinato in base **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**, **DIMENSION_UNIQUE_NAME**, **HIERARCHY_ UNIQUE_NAME**, **LEVEL_UNIQUE_NAME**, **LEVEL_NUMBER**, **MEMBER_ORDINAL**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **MDSCHEMA_MEMBERS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**LEVEL_UNIQUE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**LEVEL_NUMBER**|**DBTYPE_UI4**|Facoltativa.|  
|**MEMBER_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**MEMBER_UNIQUE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**MEMBER_CAPTION**|**DBTYPE_WSTR**|Facoltativa.|  
|**MEMBER_TYPE**|**DBTYPE_I4**|Facoltativa.|  
|**TREE_OP**|**DBTYPE_I4**|(Facoltativo) Si applica solo a un singolo membro:<br /><br /> **MDTREEOP_ANCESTORS** (**0x20**) restituisce tutti i predecessori.<br /><br /> **MDTREEOP_CHILDREN** (**0x01**) restituisce solo i figli immediati.<br /><br /> **MDTREEOP_SIBLINGS** (**0x02**) restituisce i membri allo stesso livello.<br /><br /> **MDTREEOP_PARENT** (**0x04**) restituisce solo l'oggetto padre.<br /><br /> **MDTREEOP_SELF** (**0x08**) restituisce se stesso nell'elenco di righe restituite.<br /><br /> **MDTREEOP_DESCENDANTS** (**0x10**) restituisce tutti i discendenti.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Facoltativo) Restrizione predefinita è un valore pari a 1. Una bitmap con uno dei valori validi seguenti:<br /><br /> 1 CUBO<br /><br /> 2 DIMENSIONE|  
  
## <a name="see-also"></a>Vedere anche  
 [OLE DB per OLAP i rowset dello Schema](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
