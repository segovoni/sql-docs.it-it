---
title: Utilità di avvio del daemon filtri full-text di SQL (scheda Servizio) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6aad7ebe-c4be-4d37-8536-61502f51faa2
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 48dab174565a9abb9790262b4e67e67be066dd8b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sql-full-text-filter-daemon-launcher-service-tab"></a>Utilità di avvio del daemon filtri full-text di SQL (scheda Servizio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  A partire da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], il servizio Utilità di avvio del daemon filtri full-text di SQL (FDHOST Launcher) viene utilizzato dalla ricerca full-text in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se si utilizza la ricerca full-text, questo servizio deve essere in esecuzione. Per informazioni sui processi host del daemon di filtri, vedere "Architettura della ricerca full-text" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Usare la scheda **Servizio**della finestra di dialogo **Proprietà - Utilità di avvio del daemon filtri full-text di SQL** per visualizzare o specificare le opzioni seguenti.  
  
## <a name="options"></a>Opzioni  
 **Percorso binario**  
 Elenca il percorso dei file di programma utilizzati dal servizio.  
  
 **Controllo errori**  
 1 indica `SERVICE_ERROR_NORMAL`. In caso di problemi di avvio del servizio durante l'avvio del computer, il programma di avvio registra l'errore e visualizza una finestra di messaggio popup ma continua l'operazione di avvio. Questo valore non può essere modificato.  
  
 **Codice di uscita**  
 Quando si verifica un errore, il numero dell'errore viene visualizzato in questa casella. Questo numero può risultare utile per la risoluzione dei problemi. È possibile cercarlo nella [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base oppure comunicarlo al personale del supporto tecnico.  
  
 **Host Name**  
 Visualizza il nome del computer o del cluster che esegue il servizio [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Nome**  
 Indica il nome visualizzato del servizio.  
  
 **ID processo**  
 Visualizza l'ID di processo di Windows.  
  
 **Tipo di servizio SQL Server**  
 Visualizza il tipo di servizio fornito ai processi chiamanti. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono installati diversi servizi.  
  
 **Modalità di avvio**  
 Impostare una delle opzioni seguenti per il servizio:  
  
-   Manuale: il servizio non viene avviato automaticamente all'avvio del computer. In questo caso è necessario avviare il servizio tramite Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o un altro strumento.  
  
-   Automatico: viene eseguito un tentativo automatico di avvio del servizio all'avvio del computer.  
  
-   Disabilitato: il servizio non può essere avviato.  
  
 **State**  
 Indica se il servizio è in esecuzione, arrestato o disabilitato. "**…**" indica una modifica di stato in sospeso.  
  
  
