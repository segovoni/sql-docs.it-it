---
title: Editor trasformazione campionamento percentuale | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.percentagesamplingtransformation.f1
helpviewer_keywords:
- Percentage Sampling Transformation Editor
ms.assetid: 2c40d804-26a3-4d35-809b-bc923d83d451
caps.latest.revision: 24
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ca7b3d4dcbb4643076aa62e05299e3b42332d528
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250601"
---
# <a name="percentage-sampling-transformation-editor"></a>Editor trasformazione Campionamento percentuale
  Utilizzare la finestra di dialogo **Editor trasformazione Campionamento percentuale** per dividere parte di un input in un campione utilizzando la percentuale di righe specificata. La trasformazione divide l'input in due output separati.  
  
 Per ulteriori informazioni sulla trasformazione Campionamento percentuale, vedere [Percentage Sampling Transformation](data-flow/transformations/percentage-sampling-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Percentuale di righe**  
 Consente di specificare la percentuale di righe dell'input da utilizzare come campione.  
  
 È possibile specificare il valore di questa proprietà tramite un'espressione di proprietà.  
  
 **Nome output campione**  
 Consente di specificare un nome univoco per l'output che includerà le righe campionate. Il nome specificato verrà visualizzato in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Nome output non selezionato**  
 Consente di specificare un nome univoco per l'output che conterrà le righe escluse dal campionamento. Il nome specificato verrà visualizzato in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Usa il valore di inizializzazione casuale seguente**  
 Consente di specificare il valore di inizializzazione del campionamento per il generatore di numeri casuali utilizzato dalla trasformazione per creare un campione. È consigliato solo a scopo di sviluppo e test. Se non viene specificato alcun valore di inizializzazione casuale, la trasformazione utilizza il conteggio tick di Microsoft Windows.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Trasformazione Campionamento righe](data-flow/transformations/row-sampling-transformation.md)  
  
  
