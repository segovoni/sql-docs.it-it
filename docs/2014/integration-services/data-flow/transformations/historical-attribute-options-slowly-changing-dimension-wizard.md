---
title: Opzioni attributi cronologici (Configurazione guidata dimensioni a modifica lenta) | Microsoft Docs
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
- sql12.dts.loaddimwizard.histattriboption.f1
ms.assetid: a176ec66-ec39-4c99-99d1-c1afa8450e1e
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7f9b7b2819eec76f3ccc913debea3773cad0b9e4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328081"
---
# <a name="historical-attribute-options-slowly-changing-dimension-wizard"></a>Opzioni attributi cronologici (Configurazione guidata dimensioni a modifica lenta)
  Utilizzare la finestra di dialogo **Opzioni attributi cronologici** per visualizzare gli attributi cronologici in base a date di inizio e fine o per registrare gli attributi cronologici in una colonna creata appositamente a questo scopo.  
  
 Per ulteriori informazioni su questa procedura guidata, vedere [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Usa una singola colonna per mostrare i record correnti e scaduti**  
 Se si sceglie di utilizzare una sola colonna per registrare lo stato degli attributi cronologici, saranno disponibili le opzioni seguenti:  
  
|Opzione|Description|  
|------------|-----------------|  
|**Colonna per l'indicazione del record corrente**|Consente di selezionare una colonna da utilizzare per l'indicazione del record corrente.|  
|**Valore se corrente**|Utilizzare **Vero** o **Corrente** per indicare se si tratta del record corrente.|  
|**Valore se scaduto**|Utilizzare **Falso** o **Scaduto** per indicare se il record è un valore cronologico.|  
  
 **Usa colonne Data inizio e Data fine per identificare i record correnti e scaduti**  
 La tabella della dimensione per questa opzione deve includere una colonna data. Se si sceglie di visualizzare gli attributi cronologici in base alle date di inizio e fine, saranno disponibili le opzioni seguenti:  
  
|Opzione|Description|  
|------------|-----------------|  
|**Colonna Data inizio**|Consente di selezionare la colonna della tabella della dimensione che conterrà la data di inizio.|  
|**Colonna Data fine**|Consente di selezionare la colonna della tabella della dimensione che conterrà la data di fine.|  
|**Variabile per l'impostazione dei valori di data**|Consente di selezionare una variabile per la data nell'elenco.|  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare gli output tramite Configurazione guidata dimensioni a modifica lenta](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
