---
title: Configurare un gruppo di disponibilità SQL Server con scalabilità in lettura per Windows | Microsoft Docs
description: ''
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.reviewer: ''
ms.date: 05/24/2018
ms.topic: conceptual
ms.prod: sql
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.openlocfilehash: 926e97d7aa6026946235d7abebdd5d3fd7023891
ms.sourcegitcommit: 9e83f308008c9e0da505a6064f652c638b8dfe76
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/13/2018
ms.locfileid: "35513006"
---
# <a name="configure-a-sql-server-availability-group-for-read-scale-on-windows"></a>Configurare un gruppo di disponibilità SQL Server con scalabilità in lettura per Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

È possibile configurare un gruppo di disponibilità SQL Server Always On per i carichi di lavoro di scalabilità in lettura in Windows. Esistono due tipi di architettura per i gruppi di disponibilità:
* L'architettura per la disponibilità elevata che usa una gestione cluster per garantire la continuità operativa e può includere repliche secondarie leggibili. Per la creazione di un'architettura a disponibilità elevata, vedere [Creazione e configurazione di gruppi di disponibilità (SQL Server)](creation-and-configuration-of-availability-groups-sql-server.md). 
* Un'architettura che supporta solo i carichi di lavoro di scalabilità in lettura. 

Questo articolo illustra come creare un gruppo di disponibilità senza una gestione cluster per i carichi di lavoro di scalabilità in lettura. Questa architettura fornisce solo la scalabilità in lettura. Non fornisce la disponibilità elevata.

>[!NOTE]
>Un gruppo di disponibilità con `CLUSTER_TYPE = NONE` può includere repliche che sono ospitate in piattaforme di sistema operativo diverse. Non può tuttavia supportare la disponibilità elevata. Per il sistema operativo Linux, vedere [Configurare un gruppo di disponibilità SQL Server con scalabilità in lettura per Linux](../../../linux/sql-server-linux-availability-group-configure-rs.md).

[!INCLUDE [Create prerequisites](../../../includes/ss-availability-group-rs-prereq.md)]

## <a name="create-an-availability-group"></a>Creare un gruppo di disponibilità

Creare un gruppo di disponibilità. Impostare `CLUSTER_TYPE = NONE`. Impostare anche ogni replica con `FAILOVER_MODE = NONE`. Le applicazioni client che eseguono carichi di lavoro di analisi e report possono connettersi direttamente ai database secondari. È anche possibile creare un elenco di routing di sola lettura. Le connessioni alla replica primaria inoltrano le richieste di connessione in lettura a ogni replica secondaria dell'elenco di routing in base a uno schema round-robin.

Lo script Transact-SQL seguente crea un gruppo di disponibilità denominato `ag1`. Lo script configura le repliche del gruppo di disponibilità con `SEEDING_MODE = AUTOMATIC`. In base a questa impostazione, SQL Server crea automaticamente il database in ciascun server secondario dopo l'aggiunta al gruppo di disponibilità. 

Aggiornare lo script seguente per il proprio ambiente. Sostituire i valori `<node1>` e `<node2>` con i nomi delle istanze di SQL Server che ospitano le repliche. Sostituire il valore `<5022>` con la porta impostata per l'endpoint. Nella replica primaria di SQL Server eseguire lo script Transact-SQL seguente:

```sql
CREATE AVAILABILITY GROUP [ag1]
    WITH (CLUSTER_TYPE = NONE)
    FOR REPLICA ON
        N'<node1>' WITH (
            ENDPOINT_URL = N'tcp://<node1>:<5022>',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
                    SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
        N'<node2>' WITH (
            ENDPOINT_URL = N'tcp://<node2>:<5022>',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
            SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            );

ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

### <a name="join-secondary-sql-server-instances-to-the-availability-group"></a>Creare un join fra le istanze di SQL Server secondarie e il gruppo di disponibilità

Lo script Transact-SQL seguente aggiunge un server al gruppo di disponibilità con nome `ag1`. Aggiornare lo script per il proprio ambiente. Per creare un join per il gruppo di disponibilità, eseguire lo script Transact-SQL seguente su ciascuna replica secondaria di SQL Server:

```sql
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);

ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create post](../../../includes/ss-availability-group-rs-postactivity.md)]

Questo gruppo di disponibilità non è una configurazione a disponibilità elevata. Se è necessaria la disponibilità elevata, seguire le istruzioni in [Configure an Always On Availability Group for SQL Server on Linux](../../../linux/sql-server-linux-availability-group-configure-ha.md) (Configurare un gruppo di disponibilità Always On per SQL Server in Linux) o in [Creazione e configurazione di gruppi di disponibilità in Windows](creation-and-configuration-of-availability-groups-sql-server.md).

## <a name="connect-to-read-only-secondary-replicas"></a>Eseguire la connessione a repliche secondarie di sola lettura

Ci sono due modi per eseguire la connessione a repliche secondarie di sola lettura:
* Le applicazioni possono connettersi direttamente all'istanza di SQL Server che ospita la replica secondaria ed eseguire query sui database. Per altre informazioni, vedere [Repliche secondarie leggibili](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).
* Le applicazioni possono anche usare il routing di sola lettura, per il quale è necessario un listener. Per altre informazioni, vedere [Routing di sola lettura](listeners-client-connectivity-application-failover.md#ConnectToSecondary).

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>Eseguire il failover della replica primaria in un gruppo di disponibilità per scalabilità in lettura

[!INCLUDE[Force failover](../../../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>Passaggi successivi

* [Configurare un gruppo di disponibilità distribuito](distributed-availability-groups-always-on-availability-groups.md)
* [Altre informazioni sui gruppi di disponibilità](overview-of-always-on-availability-groups-sql-server.md)
* [Eseguire un failover manuale forzato](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)
