---
title: Master di scalabilità orizzontale di SQL Server Integration Services (SSIS) | Microsoft Docs
description: Questo articolo descrive il componente Scale Out Master di SSIS Scale Out
ms.custom: performance
ms.date: 12/19/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: 25d404552fe71cf79cda57a7d204a5c2263f8e2e
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35405553"
---
# <a name="integration-services-ssis-scale-out-master"></a>Master di scalabilità orizzontale di Integration Services (SSIS)
Scale Out Master gestisce il sistema di scalabilità orizzontale tramite il catalogo SSISDB e il servizio Scale Out Master. 

Il catalogo SSISDB archivia tutte le informazioni relative ai componenti Scale Out Worker, ai pacchetti e alle esecuzioni. Fornisce l'interfaccia per abilitare un ruolo di lavoro di scalabilità orizzontale ed eseguire pacchetti nel servizio di scalabilità orizzontale. Per altre informazioni, vedere [Procedura dettagliata: Installare il servizio Integration Services (SSIS) Scale Out](walkthrough-set-up-integration-services-scale-out.md) ed [Eseguire pacchetti nel servizio Integration Services (SSIS) Scale Out](run-packages-in-integration-services-ssis-scale-out.md).

Scale Out Master è un servizio Windows responsabile delle comunicazioni con i componenti Scale Out Worker. Restituisce lo stato dell'esecuzione di pacchetti nei componenti Scale Out Worker su HTTPS ed elabora i dati nel database SSISDB. 

## <a name="scale-out-views-and-stored-procedures-in-ssisdb"></a>Viste Scale Out e stored procedure in SSISDB

### <a name="views"></a>Viste:
-   [[catalog].[master_properties]](../../integration-services/system-views/catalog-master-properties-ssisdb-database.md)
-   [[catalog].[worker_agents]](../../integration-services/system-views/catalog-worker-agents-ssisdb-database.md).

### <a name="stored-procedures"></a>Stored procedure:

-   Per la gestione di componenti Scale Out Worker:  
    -   [[catalog].[disable_worker_agent]](../../integration-services/system-stored-procedures/catalog-disable-worker-agent-ssisdb-database.md)
    -   [[catalog].[enable_worker_agent]](../../integration-services/system-stored-procedures/catalog-enable-worker-agent-ssisdb-database.md).

- Per l'esecuzione di pacchetti in Scale Out:   
    -   [[catalog].[create_execution]](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md)
    -   [[catalog].[add_execution_worker]](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md)
    -   [[catalog].[start_execution]](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md).   

## <a name="configure-the-scale-out-master-service"></a>Configurare il servizio Scale Out Master
È possibile configurare il servizio Scale Out Master usando il file `\<drive\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config`. Il servizio deve essere riavviato dopo l'aggiornamento del file di configurazione.


Configurazione  |Descrizione  |Valore predefinito  
---------|---------|---------
PortNumber|Numero di porta di rete usato per comunicare con un ruolo di lavoro di scalabilità orizzontale.|8391         
SSLCertThumbprint|Identificazione personale del certificato SSL usato per proteggere la comunicazione con un ruolo di lavoro di scalabilità orizzontale.|Identificazione personale del certificato SSL specificato durante l'installazione del master di scalabilità orizzontale.         
SqlServerName|Nome dell'istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] contenente il catalogo SSISDB. Ad esempio, NomeServer\\\\NomeIstanza.|Nome dell'istanza di SQL Server installata con il master di scalabilità orizzontale.         
CleanupCompletedJobsIntervalInMs|Intervallo per l'eliminazione dei processi di esecuzione completati, espresso in millisecondi.|43200000         
DealWithExpiredTasksIntervalInMs|Intervallo per la gestione dei processi di esecuzione scaduti, espresso in millisecondi.|300000
MasterHeartbeatIntervalInMs|Intervallo per l'heartbeat del master di scalabilità orizzontale, espresso in millisecondi. Specifica la frequenza con cui Scale Out Master aggiorna il proprio stato online nel catalogo SSISDB.|30000
SqlConnectionTimeoutInSecs|Timeout della connessione SQL in secondi per la connessione a SSISDB.|15    
||||    

## <a name="view-the-scale-out-master-service-log"></a>Visualizzare il log del servizio Scale Out Master
Il file di log del servizio Scale Out Master si trova nella cartella `\<drive\>:\Users\\[account]\AppData\Local\SSIS\ScaleOut\Master`. 

Il parametro *[account]* è l'account che esegue il servizio Scale Out Master. Per impostazione predefinita, tale account è `SSISScaleOutMaster140`.

## <a name="next-steps"></a>Passaggi successivi
[Integration Services (SSIS) Scale Out Worker](integration-services-ssis-scale-out-worker.md)
