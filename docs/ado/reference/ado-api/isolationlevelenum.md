---
title: IsolationLevelEnum | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- IsolationLevelEnum
helpviewer_keywords:
- IsolationLevelEnum enumeration [ADO]
ms.assetid: 8e17a7bc-b8a3-4ae2-b6c9-ce088ad31fdf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8fbf9db6b578bc886862069ddc31bc07f18d673b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279160"
---
# <a name="isolationlevelenum"></a>IsolationLevelEnum
Specifica il livello di isolamento delle transazioni per un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adXactUnspecified**|-1|Indica che il provider utilizza un livello di isolamento diverso da quello specificato, ma che non è possibile determinare il livello.|  
|**adXactChaos**|16|Indica che le modifiche da più isolate transazioni in sospeso non può essere sovrascritto.|  
|**adXactBrowse**|256|Indica che da una transazione è possibile visualizzare le modifiche non salvate in altre transazioni.|  
|**adXactReadUncommitted**|256|Uguale a **adXactBrowse**.|  
|**adXactCursorStability**|4096|Indica che da una transazione è possibile visualizzare le modifiche in altre transazioni solo dopo il commit.|  
|**adXactReadCommitted**|4096|Uguale a **adXactCursorStability**.|  
|**adXactRepeatableRead**|65536|Indica che da una transazione non è possibile visualizzare le modifiche apportate in altre transazioni, ma tale ripetizione di query è stato possibile recuperare nuovi **Recordset** oggetti.|  
|**adXactIsolated**|1048576|Indica che le transazioni vengono eseguite in isolamento dalle altre transazioni.|  
|**adXactSerializable**|1048576|Uguale a **adXactIsolated**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.IsolationLevel.UNSPECIFIED|  
|AdoEnums.IsolationLevel.CHAOS|  
|AdoEnums.IsolationLevel.BROWSE|  
|AdoEnums.IsolationLevel.READUNCOMMITTED|  
|AdoEnums.IsolationLevel.CURSORSTABILITY|  
|AdoEnums.IsolationLevel.READCOMMITTED|  
|AdoEnums.IsolationLevel.REPEATABLEREAD|  
|AdoEnums.IsolationLevel.ISOLATED|  
|AdoEnums.IsolationLevel.SERIALIZABLE|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md)
