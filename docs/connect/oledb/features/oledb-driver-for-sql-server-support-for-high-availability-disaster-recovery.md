---
title: Driver OLE DB per SQL Server Support for High Availability, Disaster Recovery | Documenti Microsoft
description: Il Driver OLE DB per SQL Server il supporto per il ripristino di emergenza a disponibilità elevato
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 02f6c8da18d94c243ea9c3c07717af5b9750b066
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2018
ms.locfileid: "35612166"
---
# <a name="ole-db-driver-for-sql-server-support-for-high-availability-disaster-recovery"></a>Driver OLE DB per SQL Server Support for High Availability, Disaster Recovery
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Questo articolo illustra i Driver OLE DB per il supporto di SQL Server (aggiunto [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]) per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Per altre informazioni su [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [Listener del gruppo di disponibilità, connettività client e failover dell’applicazione &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md), [Creazione e configurazione di gruppi di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md), [Clustering di failover e gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md) e [Repliche secondarie attive: Repliche secondarie leggibili &#40;Gruppi di disponibilità AlwaysOn&#41;](../../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 È possibile specificare il listener di un determinato gruppo di disponibilità nella stringa di connessione. Se un Driver OLE DB per SQL Server è connesso a un database in un gruppo di disponibilità che esegue il failover, la connessione originale viene interrotta e l'applicazione deve aprire una nuova connessione per continuare a funzionare dopo il failover.  
  
 Se non ci si connette a un listener del gruppo di disponibilità e se più indirizzi IP sono associati un nome host, il Driver OLE DB per SQL Server verranno scorsi in sequenza tutti gli indirizzi IP associati alla voce DNS. Questa operazione può richiedere tempi lunghi se il primo indirizzo IP restituito dal server DNS non è associato ad alcuna scheda di interfaccia di rete. Quando ci si connette a un listener del gruppo di disponibilità, il Driver OLE DB per SQL Server tenta di stabilire connessioni a tutti gli indirizzi IP in parallelo e se un tentativo di connessione ha esito positivo, il driver verrà rimosso qualsiasi tentativo di connessione in sospeso.  
  
> [!NOTE]  
> L'aumento del timeout di connessione e l'implementazione della logica di riesecuzione per le connessioni aumentano le probabilità che un'applicazione si connetta a un gruppo di disponibilità. Inoltre, poiché potrebbe non essere possibile stabilire una connessione a causa del failover di un gruppo di disponibilità, è opportuno implementare la logica di riesecuzione delle connessioni, finché non si ottiene la riconnessione.  
  
## <a name="connecting-with-multisubnetfailover"></a>Connessione con MultiSubnetFailover  
 Specificare sempre **MultiSubnetFailover = Yes** quando ci si connette a un listener di SQL Server gruppo di disponibilità AlwaysOn o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istanza Cluster di Failover. **MultiSubnetFailover** consente il failover più veloce per tutti i gruppi di disponibilità AlwaysOn e le istanze del Cluster di Failover in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], riducendo notevolmente il tempo di failover per singole e multi-subnet topologie AlwaysOn. Durante un failover su più subnet, verranno tentate connessioni in parallelo da parte del client. Durante un failover della subnet, il Driver OLE DB per SQL Server ritenterà la connessione TCP.  
  
 Il **MultiSubnetFailover** proprietà di connessione indica che l'applicazione viene distribuita in un gruppo di disponibilità o l'istanza del Cluster di Failover e il Driver OLE DB per SQL Server tenterà di connettersi al database di primario [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] indirizzi istanza prova a connettersi a tutti l'indirizzo IP. Quando si specifica **MultiSubnetFailover=Yes** per una connessione, i ripetuti tentativi di connessione TCP del client vengono eseguiti più rapidamente rispetto agli intervalli di ritrasmissione TCP predefiniti del sistema operativo. Ciò consente una riconnessione più veloce dopo il failover di un gruppo di disponibilità AlwaysOn o un'istanza del Cluster di Failover ed è applicabile a singolo e con più subnet gruppi di disponibilità sia istanze del Cluster di Failover.  
  
 Per ulteriori informazioni sulle parole chiave delle stringhe di connessione, vedere [Using Connection String Keywords con il Driver OLE DB per SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
 La specifica di **MultiSubnetFailover=Yes** durante la connessione a un oggetto diverso da un listener del gruppo di disponibilità o dall'istanza del cluster di failover non è supportata poiché potrebbe determinare un impatto negativo sulle prestazioni.  
  
 Utilizzare le linee guida seguenti per connettersi a un server in un gruppo di disponibilità o nell'istanza del cluster di failover:  
  
-   Usare la proprietà di connessione **MultiSubnetFailover** in caso di connessione a una singola subnet o a più subnet, in modo da migliorare le prestazioni.  
  
-   Per eseguire la connessione a un gruppo di disponibilità, specificare il listener del gruppo di disponibilità come server nella stringa di connessione.  
  
-   La connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] configurata con più di 64 indirizzi IP determinerà un errore di connessione.  
  
-   Il comportamento di un'applicazione in cui viene usata la proprietà di connessione **MultiSubnetFailover** non è influenzato dal tipo di autenticazione, cioè dall'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], dall'autenticazione Kerberos, o dall’autenticazione di Windows.  
  
-   È possibile aumentare il valore di **loginTimeout** per adattarlo alla durata del failover e ridurre il numero di nuovi tentativi di connessione dell'applicazione.  
  
-   Le transazioni distribuite non sono supportate.  
  
Se il routing di sola lettura non è attivo, non è possibile stabilire una connessione a un percorso di replica secondaria in un gruppo di disponibilità nelle situazioni seguenti:  
  
1.  Se il percorso di replica secondaria non è configurato per accettare le connessioni.  
  
2.  Se un'applicazione usa **ApplicationIntent=ReadWrite** (vedere di seguito) e il percorso di replica secondaria è configurato per l'accesso in sola lettura.  
  
Una connessione non riesce se una replica primaria è configurata per rifiutare i carichi di lavoro in sola lettura e la stringa di connessione contiene **ApplicationIntent=ReadOnly**.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Aggiornamento per l'utilizzo di cluster su più subnet dal mirroring del database  
Si verificherà un errore di connessione se nella stringa di connessione sono presenti le parole chiave di connessione **MultiSubnetFailover** e **Failover_Partner**. Si verificherà un errore anche se viene usato **MultiSubnetFailover** e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] restituisce una risposta del partner di failover in cui viene indicato che fa parte di una coppia del mirroring del database.  
  
Se si aggiorna un Driver OLE DB per SQL Server che attualmente Usa il mirroring del database a uno scenario su più subnet, è necessario rimuovere il **Failover_Partner** proprietà di connessione e sostituirla con  **MultiSubnetFailover** impostato su **Sì** e sostituire il nome del server nella stringa di connessione con un listener del gruppo di disponibilità. Se in una stringa di connessione vengono usati **Failover_Partner** e **MultiSubnetFailover=Yes**, il driver genererà un errore. Se tuttavia in una stringa di connessione vengono usati **Failover_Partner** e **MultiSubnetFailover=No** (o **ApplicationIntent=ReadWrite**), l'applicazione userà il mirroring del database.  
  
Il driver restituirà un errore se il mirroring del database viene usato nel database primario nel gruppo di disponibilità e se **MultiSubnetFailover=Yes** veine usato nella stringa di connessione a un database primario anziché a un listener del gruppo di disponibilità.  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="ole-db"></a>OLE DB  
Il Driver OLE DB per SQL Server supporta sia la **ApplicationIntent** e il **MultiSubnetFailover** parole chiave.   
  
Le due parole chiave stringa di connessione OLE DB sono stati aggiunti per supportare [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] nel Driver OLE DB per SQL Server:  
  
-   **ApplicationIntent** 
-   **MultiSubnetFailover**  
  
 Per ulteriori informazioni sulle parole chiave delle stringhe di connessione nel Driver OLE DB per SQL Server, vedere [Using Connection String Keywords con il Driver OLE DB per SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  

### <a name="application-intent"></a>Finalità dell'applicazione 

Le proprietà di connessione equivalenti sono:  
  
-   **SSPROP_INIT_APPLICATIONINTENT**  
  
-   **DBPROP_INIT_PROVIDERSTRING**  
  
Un Driver OLE DB per SQL Server può utilizzare uno dei metodi per specificare la finalità dell'applicazione:  
  
 -   **IDBInitialize:: Initialize**  
 **IDBInitialize::Initialize** prevede l'uso del set di proprietà precedentemente configurato per inizializzare l'origine dati e creare l'oggetto origine dati. La finalità dell'applicazione viene specificata come proprietà del provider o come parte della stringa di proprietà estesa.  
  
 -   **IDataInitialize:: GetDatasource**  
 **IDataInitialize::GetDatasource** accetta una stringa di connessione di input che può contenere la parola chiave **Application Intent**.  
  
 -   **IDBProperties:: SetProperties**  
 Per impostare il valore della proprietà **ApplicationIntent**, chiamare **IDBProperties::SetProperties** passando la proprietà **SSPROP_INIT_APPLICATIONINTENT** con un valore "**ReadWrite**" o "**ReadOnly**" o la proprietà **DBPROP_INIT_PROVIDERSTRING** con un valore contenente "**ApplicationIntent=ReadOnly**" o "**ApplicationIntent=ReadWrite**".  
  
È possibile specificare la finalità dell'applicazione nel campo delle proprietà della finalità dell’applicazione della scheda Tutte nella finestra di dialogo **Proprietà di Data Link**.  
  
Quando vengono stabilite connessioni implicite, per la connessione viene utilizzata l'impostazione relativa alla finalità dell'applicazione definita per la connessione padre. Analogamente, più sessioni create dalla stessa origine dati ereditano l'impostazione relativa alla finalità dell'applicazione definita per l'origine dati.  
  
### <a name="multisubnetfailover"></a>MultiSubnetFailover

Le proprietà di connessione equivalenti sono:  
  
-   **SSPROP_INIT_MULTISUBNETFAILOVER**  
  
-   **DBPROP_INIT_PROVIDERSTRING**  

Un Driver OLE DB per SQL Server può utilizzare uno dei metodi seguenti per impostare l'opzione MultiSubnetFailover:  

 -   **IDBInitialize:: Initialize**  
 **IDBInitialize::Initialize** prevede l'uso del set di proprietà precedentemente configurato per inizializzare l'origine dati e creare l'oggetto origine dati. La finalità dell'applicazione viene specificata come proprietà del provider o come parte della stringa di proprietà estesa.  
  
 -   **IDataInitialize:: GetDatasource**  
 **IDataInitialize:: GetDatasource** accetta una stringa di connessione di input che può contenere le **MultiSubnetFailover** (parola chiave).  

-   **IDBProperties:: SetProperties**  
Per impostare il **MultiSubnetFailover** valore della proprietà, chiamare **IDBProperties:: SetProperties** passando il **SSPROP_INIT_MULTISUBNETFAILOVER** proprietà con il valore  **VARIANT_TRUE** oppure **VARIANT_FALSE** o **DBPROP_INIT_PROVIDERSTRING** proprietà con un valore contenente "**MultiSubnetFailover = Yes** "o"**MultiSubnetFailover = No**".

#### <a name="example"></a>Esempio

```
DBPROP rgPropMultisubnet;

rgPropMultisubnet.dwPropertyID = SSPROP_INIT_MULTISUBNETFAILOVER;
rgPropMultisubnet.dwOptions = DBPROPOPTIONS_REQUIRED;
rgPropMultisubnet.dwStatus = DBPROPSTATUS_OK;
rgPropMultisubnet.colid = DB_NULLID;
V_VT(&(rgPropMultisubnet.vValue)) = VT_BOOL;
V_BOOL(&(rgPropMultisubnet.vValue)) = VARIANT_TRUE;

DBPROPSET PropSet;

PropSet.rgProperties = &rgPropMultisubnet;
PropSet.cProperties = 1;
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;
IDBProperties* pIDBProperties = NULL;
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);
pIDBProperties->SetProperties(1, &PropSet);
```

## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per la funzionalità di SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [Utilizzo delle parole chiave delle stringhe di connessione con driver OLE DB per SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)  
  
  
