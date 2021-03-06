---
title: DTC del cluster per i gruppi di disponibilità di SQL Server 2016 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a47c5005-20e3-4880-945c-9f78d311af7a
caps.latest.revision: 3
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f5361e96eeb91aaf51d4f0949e3d01d078c6ee95
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768697"
---
# <a name="cluster-dtc-for-sql-server-2016-availability-groups"></a>DTC del cluster per i gruppi di disponibilità di SQL Server 2016

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo argomento descrive i requisiti e i passaggi per il clustering del servizio Microsoft Distributed Transaction Coordinator (DTC) per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Per altre informazioni sulle transazioni distribuite e [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [Transazioni tra database non supportate per il mirroring del database o i gruppi di disponibilità Always On (SQL Server)](../../../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).

 ## <a name="checklist-preliminary-requirements"></a>Elenco di controllo: requisiti preliminari
||Attività|Riferimento|  
|------|-----------------|----------|  
|![Casella di controllo](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Casella di controllo")|Verificare che tutti i nodi, i servizi e il gruppo di disponibilità siano stati configurati correttamente.|[Prerequisiti, restrizioni e consigli per i gruppi di disponibilità AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)|
|![Casella di controllo](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Casella di controllo")|Verificare che i requisiti DTC del gruppo di disponibilità siano soddisfatti.|[Transazioni tra database non supportate per il mirroring del database o i gruppi di disponibilità Always On (SQL Server)](../../../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)

## <a name="checklist-clustered-dtc-resource-dependencies"></a>Elenco di controllo: dipendenze delle risorse DTC cluster
||Attività|Riferimento|  
|------|-----------------|----------|  
|![Casella di controllo](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Casella di controllo")|Unità di archiviazione condivisa.|[Configurazione dell'unità di archiviazione condivisa](https://msdn.microsoft.com/library/cc982358(v=bts.10).aspx). Si consiglia di usare la lettera di unità **M**.|
|![Casella di controllo](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Casella di controllo")|Risorsa nome di rete DTC univoca.  Il nome viene registrato come oggetto computer del cluster in Active Directory.<br /><br />Verificare che una delle due affermazioni seguenti sia vera:<br /><br />• L'utente che crea la risorsa nome di rete DTC ha l'autorizzazione per la creazione di oggetti computer per l'unità organizzativa o il contenitore in cui si trova la risorsa nome di rete DTC.<br /><br />• Se l'utente non ha l'autorizzazione per la creazione di oggetti computer, chiedere all'amministratore di dominio di pre-installare un oggetto computer del cluster per la risorsa nome di rete DTC.|[Pre-installare gli oggetti computer del cluster in Active Directory Domain Services](https://technet.microsoft.com/library/dn466519(v=ws.11).aspx)|
|![Casella di controllo](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Casella di controllo")|Un indirizzo IP statico valido disponibile e la subnet mask appropriata per l'indirizzo IP.||

## <a name="cluster-the-dtc-resource"></a>Inserire la risorsa DTC nel cluster
Dopo aver creato la risorsa gruppo di disponibilità, creare una risorsa DTC cluster e aggiungerla al gruppo di disponibilità.  È possibile visualizzare uno script di esempio in [Creare DTC cluster per un gruppo di disponibilità AlwaysOn](../../../database-engine/availability-groups/windows/create-clustered-dtc-for-an-always-on-availability-group.md).


## <a name="checklist-post-clustered-dtc-resource-configurations"></a>Elenco di controllo: configurazioni successive delle risorse DTC cluster
||Attività|Riferimento|  
|------|-----------------|----------|  
|![Casella di controllo](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Casella di controllo")|Abilitare l'accesso alla rete sicuro per la risorsa DTC cluster.|[Abilitare l'accesso alla rete sicuro per MS DTC](https://technet.microsoft.com/library/cc753620(v=ws.10).aspx)|
|![Casella di controllo](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Casella di controllo")|Arrestare e disabilitare il servizio DTC locale.|[Configurare la modalità di avvio di un servizio](https://technet.microsoft.com/library/cc755249(v=ws.11).aspx)|
|![Casella di controllo](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Casella di controllo")|Eseguire ciclicamente il servizio SQL Server per ogni istanza del gruppo di disponibilità.  Eseguire il failover del gruppo di disponibilità in base alle esigenze.|[Eseguire un failover manuale pianificato di un gruppo di disponibilità (SQL Server)](../../../database-engine/availability-groups/windows/perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)<br /><br />[Avviare, arrestare, sospendere, riprendere, riavviare il motore di database, SQL Server Agent o SQL Server Browser](../../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)|

- Se il server è Windows Server 2012 R2 è necessario che nel sistema operativo sia applicato [KB 3030373](http://support.microsoft.com/kb/3090973) .

- Preparare i server per i gruppi di disponibilità in base agli elenchi di controllo riportati in [Prerequisiti, restrizioni e consigli per i gruppi di disponibilità AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).

- Configurare le istanze del server per i [**gruppi di disponibilità Always On**](../../../database-engine/availability-groups/windows/configuration-of-a-server-instance-for-always-on-availability-groups-sql-server.md).

### <a name="resources"></a>RISORSE


[Altre informazioni sul test del servizio DTC nei gruppi di disponibilità:](https://blogs.technet.microsoft.com/dataplatform/2016/01/25/sql-server-2016-dtc-support-in-availability-groups/)

[Monitorare Gruppi di disponibilità (Transact-SQL)](monitor-availability-groups-transact-sql.md)

[Creare un gruppo di disponibilità (Transact-SQL)](create-an-availability-group-transact-sql.md)


[Supporto DTC di SQL Server 2016 nei gruppi di disponibilità](http://blogs.technet.microsoft.com/dataplatform/2016/01/25/sql-server-2016-dtc-support-in-availability-groups/) 

[Collegamento esterno: Configurare DTC per un'istanza cluster di SQL Server con Windows Server 2008 R2](http://sqlha.com/2013/03/12/how-to-properly-configure-dtc-for-clustered-instances-of-sql-server-with-windows-server-2008-r2/)
