---
title: SQL Server Backup and Restore with Windows Azure Blob Storage Service | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6a0c9b6a-cf71-4311-82f2-12c445f63935
caps.latest.revision: 28
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 38e20e433b7fed2e34750c300ee7e1489d6df665
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37193551"
---
# <a name="sql-server-backup-and-restore-with-windows-azure-blob-storage-service"></a>Backup e ripristino di SQL Server con il servizio di archiviazione BLOB di Windows Azure
  In questo argomento vengono illustrati i backup di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel [servizio di archiviazione BLOB di Windows Azure](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)e il ripristino dallo stesso. È inoltre disponibile un riepilogo dei vantaggi dell'utilizzo del servizio BLOB di Windows Azure per archiviare i backup di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 SQL Server supporta l'archiviazione di backup nel servizio di archiviazione BLOB di Windows Azure nei modi seguenti:  
  
-   **Gestire i backup in Microsoft Azure:** usando gli stessi metodi per il backup su DISK e TAPE, è ora possibile eseguire il backup in Archiviazione di Microsoft Azure specificando l'URL come destinazione di backup.  È possibile utilizzare questa funzionalità per eseguire il backup manualmente o per configurare la propria strategia di backup allo stesso modo di una risorsa di archiviazione locale o di altre soluzioni esterne. Questa funzionalità viene definita anche **Backup di SQL Server nell'URL**. Per altre informazioni, vedere [SQL Server Backup to URL](sql-server-backup-to-url.md). Questa funzionalità è disponibile in SQL Server 2012 SP1 CU2 o versione successiva.  
  
    > [!NOTE]  
    >  Per le versioni di SQL Server precedenti a SQL Server 2014, è possibile utilizzare lo strumento per il backup di SQL Server in Windows Azure del componente aggiuntivo per creare i backup nel servizio di archiviazione Windows Azure in modo rapido e semplice. Per ulteriori informazioni, vedere l' [Area download](http://go.microsoft.com/fwlink/?LinkID=324399).  
  
-   **Gestire i backup con SQL Server in Microsoft Azure:** configurare SQL Server in modo da gestire la strategia di backup e pianificare i backup per un singolo database o più database oppure impostare i valori predefiniti a livello di istanza. Questa funzionalità viene definita  **[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]**. Per ulteriori informazioni, vedere [SQL Server Managed  Backup to Windows Azure](sql-server-managed-backup-to-microsoft-azure.md). Questa funzionalità è disponibile in SQL Server 2014 o versione successiva.  
  
## <a name="benefits-of-using-the-windows-azure-blob-service-for-includessnoversionincludesssnoversion-mdmd-backups"></a>Vantaggi dell'utilizzo del servizio BLOB di Windows Azure per i backup di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Archiviazione in una posizione esterna flessibile, affidabile e illimitata: L'archiviazione dei backup nel servizio BLOB di Microsoft Azure è un'opzione pratica, flessibile e di facile accesso da posizioni esterne. La creazione dell'archiviazione in una posizione esterna per i backup di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere semplice quanto la modifica degli script o dei processi esistenti. Generalmente, l'archiviazione in una posizione esterna deve essere sufficientemente lontana dalla posizione del database di produzione per impedire che una singola situazione di emergenza possa influire sia sulla posizione esterna sia su quella del database di produzione. Scegliendo la replica a livello geografico dell'archiviazione BLOB si dispone di un ulteriore livello di protezione in caso di evento di emergenza che potrebbe influire sull'intera area. Inoltre, i backup sono disponibili sempre e in qualsiasi punto e possono essere facilmente utilizzati per i ripristini.  
  
-   Archivio di backup: il servizio di archiviazione BLOB di Microsoft Azure offre un'alternativa più efficace rispetto alla tradizionale soluzione su nastro adottata per archiviare i backup. Per l'archiviazione su nastro potrebbero essere necessari il trasporto fisico in una struttura esterna e misure di protezione dei supporti. L'archiviazione dei backup nell'apposito servizio BLOB di Windows Azure garantisce una soluzione di archiviazione immediata, a elevata disponibilità e durevole.  
  
-   Nessun overhead di gestione dell'hardware: non è previsto alcun problema di questo tipo con i servizi Windows Azure. Tramite i servizi Windows Azure viene gestito l'hardware e viene fornita una replica a livello geografico per garantire ridondanza e protezione da eventuali errori dell'hardware.  
  
-   Attualmente, per le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in esecuzione in una macchina virtuale di Windows Azure, il backup nei servizi di archiviazione BLOB di Windows Azure può essere effettuato creando dischi collegati. Tuttavia, esiste un limite al numero di dischi che è possibile collegare a una macchina virtuale di Windows Azure, vale a dire 16 per un'istanza di dimensioni elevate e un po' di meno per istanze di dimensioni inferiori. Abilitando un backup diretto nell'archiviazione BLOB di Windows Azure è possibile evitare il limite di 16 dischi.  
  
     Inoltre, il file di backup che è attualmente archiviato nel servizio di archiviazione BLOB di Windows Azure è direttamente disponibile in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale o in un'altra di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in esecuzione in una macchina virtuale di Windows Azure, senza dover collegare/scollegare il database o scaricare e collegare il disco rigido virtuale.  
  
-   Vantaggi economici: si paga solo il servizio utilizzato. Questo servizio può essere efficace dal punto di vista economico come soluzione di archiviazione esterna e di backup. Per ulteriori informazioni e per i collegamenti, vedere la sezione [Considerazioni sui costi di Windows Azure](#Billing) .  
  
##  <a name="Billing"></a> Considerazioni sui costi di Azure di Windows:  
 Conoscendo i costi correlati all'archiviazione di Windows Azure è possibile prevedere il costo della creazione e dell'archiviazione dei backup in Windows Azure.  
  
 Per stimare i costi è possibile utilizzare il [calcolatore dei costi di Windows Azure](http://go.microsoft.com/fwlink/?LinkId=277060) .  
  
 **Archiviazione:** i costi dipendono dallo spazio usato e vengono calcolati in base a una scala graduata e a livello di ridondanza. Per ulteriori dettagli e informazioni aggiornate, vedere la sezione **Gestione dati** dell'articolo [Dettagli prezzi](http://go.microsoft.com/fwlink/?LinkId=277059) .  
  
 **Trasferimenti di dati:** i trasferimenti in entrata dei dati in Microsoft Azure sono gratuiti. Per i trasferimenti in uscita viene addebitato il costo relativo all'utilizzo della larghezza di banda e il calcolo viene effettuato in base a una scala graduata specifica per l'area. Per ulteriori informazioni, vedere la sezione [Trasferimenti di dati](http://go.microsoft.com/fwlink/?LinkId=277061) nell'articolo Dettagli prezzi.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure consigliate e risoluzione dei problemi per il backup di SQL Server nell'URL](sql-server-backup-to-url-best-practices-and-troubleshooting.md)   
 [Backup e ripristino di database di sistema &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)   
 [Esercitazione: SQL Server Backup e ripristino di Windows Azure Blob Storage Service](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)   
 [Backup di SQL Server nell'URL](sql-server-backup-to-url.md)  
  
  
