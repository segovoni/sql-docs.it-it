---
title: Finestra di dialogo Proprietà pacchetto | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackageprop.general.f1
- sql12.ssis.ssms.packageproperties.f1
ms.assetid: a70acbf4-5f5c-4606-8ce4-8eb3684233de
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a85a05d5a0b18701ed9b8a480ef0bb7c05e873d4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37304211"
---
# <a name="package-properties-dialog-box"></a>Finestra di dialogo Proprietà pacchetto
  Utilizzare la finestra di dialogo **Proprietà pacchetto** per visualizzare le proprietà dei pacchetti archiviati nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Per altre informazioni, vedere [Server Integration Services &#40;SSIS&#41;](integration-services-ssis-server-and-catalog.md).  
  
 **Per saperne di più**  
  
-   [Aprire la finestra di dialogo Proprietà pacchetto](#open_dialog)  
  
-   [Configurare le opzioni](#options)  
  
##  <a name="open_dialog"></a> Aprire la finestra di dialogo Proprietà pacchetto  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi al server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Verrà eseguita la connessione all'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in cui è ospitato il database SSISDB.  
  
2.  In Esplora oggetti espandere l'albero per visualizzare il nodo dei **cataloghi di Integration Services** .  
  
3.  Espandere il nodo **SSISDB** .  
  
4.  Espandere la cartella che contiene il pacchetto di cui si desidera visualizzare le proprietà.  
  
5.  Fare clic con il pulsante destro del mouse sul pacchetto, quindi scegliere **Proprietà**.  
  
##  <a name="options"></a> Configurare le opzioni  
 Utilizzare la pagina **Generale** per visualizzare le proprietà del pacchetto selezionato.  
  
 Tutte le proprietà nella pagina **Generale** sono di sola lettura.  
  
 **Nome**  
 Viene visualizzato il nome del pacchetto.  
  
 **Identificatore**  
 Viene elencato l'ID del pacchetto.  
  
 **Punto di ingresso**  
 Il valore di `True` indica che il pacchetto viene avviato direttamente. Il valore di `False` indica che il pacchetto viene avviato da un altro pacchetto tramite l'attività Esegui pacchetto. Il valore predefinito è `True`.  
  
 Questa proprietà si imposta in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] sia per il pacchetto padre che per i pacchetti figlio facendo clic con il pulsante destro del mouse sul pacchetto in Esplora soluzioni e selezionando **Pacchetto punto di ingresso**.  
  
 **Descrizione**  
 Viene visualizzata la descrizione facoltativa del pacchetto.  
  
  
