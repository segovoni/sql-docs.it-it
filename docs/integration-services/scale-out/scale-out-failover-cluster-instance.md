---
title: Supporto di SQL Server Integration Services (SSIS) Scale Out per disponibilità elevata tramite istanza di cluster di failover di SQL Server | Microsoft Docs
description: Questo articolo descrive come configurare SSIS Scale Out per la disponibilità elevata con un'istanza del cluster di failover di SQL Server
ms.custom: performance
ms.date: 04/10/2018
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
ms.openlocfilehash: 57dcddf0b4568546c299f298976ef300d5bd6301
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35407223"
---
# <a name="scale-out-support-for-high-availability-via-sql-server-failover-cluster-instance"></a>Supporto di Scale Out per disponibilità elevata tramite istanza del cluster di failover di SQL Server

Per configurare la disponibilità elevata sul lato Scale Out Master con l'istanza del cluster di failover di SQL Server, seguire la procedura qui riportata:

## <a name="1-prerequisites"></a>1. Prerequisites
Configurare un cluster di failover di Windows Vedere il post di blog [Installing the Failover Cluster Feature and Tools for Windows Server 2012](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) (Installazione della funzionalità di clustering di failover e degli strumenti per Windows Server 2012) per le istruzioni. Installare la funzionalità e gli strumenti in tutti i nodi del cluster.

## <a name="2-install-sql-server-failover-cluster"></a>2. Installare cluster di failover di SQL Server
Installare un cluster di failover di SQL Server. Per istruzioni, vedere [Installazione del cluster di failover di SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md). Durante l'installazione, selezionare Servizi motore di database nella pagina Selezione funzionalità. Registrare il nome rete di SQL Server per la configurazione futura.

![Nome rete SQL](media/sql-network-name.PNG)

Aggiungere un nodo secondario al cluster di failover di SQL Server.

## <a name="3-install-scale-out-master-on-the-primary-node"></a>3. Installare Scale Out Master nel nodo primario
Installare Integration Services e Scale Out Master nel nodo primario con l'installazione guidata per l'installazione non cluster. 

Durante l'installazione, includere il nome rete SQL Server nei nomi comuni del certificato di Scale Out Master.

> [!NOTE]
> Se si vuole eseguire il failover di SSISDB e del servizio Scale Out Master separatamente, seguire [2. Installare Scale Out Master nel nodo primario](scale-out-support-for-high-availability.md#2-install-scale-out-master-on-the-primary-node) per la configurazione di Scale Out Master.

## <a name="4-install-scale-out-master-on-the-secondary-node"></a>4. Installare Scale Out Master nel nodo secondario
Seguire [3. Installare Scale Out Master nel nodo secondario](scale-out-support-for-high-availability.md#3-install-scale-out-master-on-the-secondary-node)

## <a name="5-update-the-scale-out-master-service-configuration-file"></a>5. Aggiornare il file di configurazione del servizio Scale Out Master
Aggiornare il file di configurazione del servizio Scale Out Master, \<unità\>:\Programmi\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config nei nodi primario e secondario. Aggiornare **SqlServerName** in [nome rete SQL Server]//[Nome istanza] o [nome rete SQL Server] per l'istanza predefinita.

## <a name="6-add-scale-out-master-service-to-sql-server-role-in-windows-failover-cluster"></a>6. Aggiungere il servizio Scale Out Master al ruolo di SQL Server nel cluster di failover di Windows
In Gestione cluster di failover connettersi al cluster per Scale Out. Selezionare Ruoli in Explorer, fare clic con il pulsante destro del mouse sul ruolo di SQL Server e selezionare Add Resource (Aggiungi risorsa) e Generic Service (Servizio generico). 

![Servizio generico](media/generic-service.PNG)

Nella creazione guidata nuova risorsa, selezionare il servizio Scale Out Master e completare la procedura guidata. 

Portare il servizio Scale Out Master online.

![Portare il servizio online](media/bring-online.PNG)

> [!NOTE]
> Se si vuole eseguire il failover di SSISDB e del servizio Scale Out Master separatamente, seguire [7. Configurare il ruolo del servizio Scale Out Master del cluster di failover di Windows](scale-out-support-for-high-availability.md#7-configure-the-scale-out-master-service-role-of-the-windows-server-failover-cluster)

## <a name="7-install-scale-out-workers"></a>7. Installare i ruoli di lavoro di Scale Out
Installare il ruolo di lavoro di Scale Out nei nodi ruolo di lavoro. Durante l'installazione, specificare https://[nome rete di SQL Server]:[porta master] per l'endpoint master. 

> [!NOTE]
> Se si vuole eseguire il failover di SSISDB e del servizio Scale Out Master separatamente, specificare il nome host DNS del servizio Scale Out Master invece del nome rete di SQL Server.

## <a name="8-install-scale-out-worker-client-certificate"></a>8. Installare il certificato client del ruolo di lavoro di Scale Out
Installare il certificato di lavoro in tutti i nodi del cluster di failover di SQL Server. Vedere [Installare il certificato client del ruolo di lavoro di Scale Out](walkthrough-set-up-integration-services-scale-out.md#InstallCert).

> [!NOTE]
> Scale Out Manager non supporta il cluster di failover di SQL Server. Anche se è stato usato Scale Out Manager per aggiungere il ruolo di lavoro di Scale Out, sarà comunque necessario installare il certificato del ruolo di lavoro in tutti i nodi master manualmente.

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni, vedere gli articoli seguenti:
-   [Integration Services (SSIS) Scale Out Master](integration-services-ssis-scale-out-master.md)
-   [Integration Services (SSIS) Scale Out Worker](integration-services-ssis-scale-out-worker.md)
