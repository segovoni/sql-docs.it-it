---
title: Proprietà SQL Server Browser (scheda servizio) | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 98ace9b0-72d5-4b72-9b7b-11fbc490981a
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6e8ba31710865718b18e4797daf4250867ebb799
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33068768"
---
# <a name="sql-server-browser-properties-service-tab"></a>Proprietà - SQL Server Browser (scheda Servizio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Il programma [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser viene eseguito come servizio nel server. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser rimane in attesa delle richieste in entrata di risorse di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e fornisce informazioni sulle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installate nel computer.  
  
 Utilizzare la scheda **Servizio** della finestra delle proprietà di **SQL Server Browser** per visualizzare le opzioni seguenti. Tutte le proprietà sono in sola lettura, fatta eccezione per **Modalità di avvio** .  
  
## <a name="options"></a>Opzioni  
 **Percorso binario**  
 Visualizza il percorso dei file di programma utilizzati dal servizio.  
  
 **Controllo errori**  
 1 indica `SERVICE_ERROR_NORMAL`. In caso di problemi di avvio del servizio durante l'avvio del computer, il programma di avvio registra l'errore e visualizza una finestra di messaggio popup ma continua l'operazione di avvio. Questo valore non può essere modificato.  
  
 **Codice di uscita**  
 Quando si verifica un errore, il numero dell'errore viene visualizzato in questa casella. Questo numero può risultare utile per la risoluzione dei problemi. È possibile cercarlo nella [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base oppure comunicarlo al personale del supporto tecnico.  
  
 **Host Name**  
 Visualizza il nome del computer o del cluster che esegue il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser.  
  
 **Nome**  
 Indica il nome visualizzato del servizio.  
  
 **ID processo**  
 Visualizza l'ID di processo di Windows.  
  
 **Tipo di servizio**  
 Visualizza il tipo di servizio fornito ai processi chiamanti. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono installati diversi servizi.  
  
 **Modalità di avvio**  
 Impostare una delle opzioni seguenti per il servizio:  
  
-   Manuale: il servizio non viene avviato automaticamente all'avvio del computer. In questo caso è necessario avviare il servizio tramite Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o un altro strumento.  
  
-   Automatico: viene eseguito un tentativo automatico di avvio del servizio all'avvio del computer.  
  
-   Disabilitato: il servizio non può essere avviato.  
  
 **State**  
 Indica se il servizio è in esecuzione, arrestato o disabilitato. "**…**" indica una modifica di stato in sospeso.  
  
## <a name="see-also"></a>Vedere anche  
 [Servizio SQL Server Browser](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
