---
title: Impostare l'analisi veloce | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
caps.latest.revision: 5
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 79307cdd25f15f34eaaf3be084a3d46045ee7d8d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37162842"
---
# <a name="set-fast-parse"></a>Impostazione dell'analisi veloce
  È necessario impostare la proprietà relativa all'analisi veloce per ogni colonna dell'origine o della trasformazione in cui questa viene utilizzata. Per impostare la proprietà, utilizzare l'editor avanzato dell'origine file flat e della trasformazione Conversione dati.  
  
### <a name="to-set-fast-parse"></a>Per impostare l'analisi veloce  
  
1.  Fare clic con il pulsante destro del mouse sull'origine file flat o sulla trasformazione Conversione dati e quindi scegliere **Visualizza editor avanzato**.  
  
2.  Nella finestra di dialogo **Editor avanzato** fare clic sulla scheda **Proprietà input e output** .  
  
3.  Nel riquadro **Input e output** fare clic sulla colonna per la quale si desidera abilitare l'analisi veloce.  
  
4.  Nella finestra Proprietà espandere la **Custom Properties** nodo e quindi impostare il `FastParse` proprietà `True`.  
  
5.  Fare clic su **OK**.  
  
  
