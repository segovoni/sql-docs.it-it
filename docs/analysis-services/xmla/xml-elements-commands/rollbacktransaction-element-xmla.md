---
title: Elemento RollbackTransaction (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d1bf63b2e3db0add86927c2f624a01fafa31e3d7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979153"
---
# <a name="rollbacktransaction-element-xmla"></a>Elemento RollbackTransaction (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Rollback di una transazione nella sessione corrente con un'istanza di Analysis Services.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <RollbackTransaction />  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il **RollbackTransaction** comando esegue il rollback di tutte le transazioni attive, definite in modo esplicito tramite il **BeginTransaction** elemento, nella sessione corrente. Se non è già presente alcuna transazione attiva, si verifica un errore. Se è già presente una transazione attiva, l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] decrementa a zero il conteggio dei riferimenti delle transazioni per la sessione corrente, eseguendo il rollback di tutte le transazioni attive.  
  
## <a name="see-also"></a>Vedere anche
 [Elemento BeginTransaction &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)   
 [Elemento Cancel &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [Elemento CommitTransaction &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [I comandi &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
