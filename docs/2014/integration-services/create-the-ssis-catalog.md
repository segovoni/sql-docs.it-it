---
title: Creare il catalogo SSIS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6ed56d36-18d9-40c2-b51f-f2a4c71d1e73
caps.latest.revision: 17
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 82965dd45ba5152aea9d6ec5751de9dfbf7cf232
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178498"
---
# <a name="create-the-ssis-catalog"></a>Creare il catalogo SSIS
  Dopo avere progettato e testato i pacchetti in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], è possibile distribuire i progetti che contengono i pacchetti in un server di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Prima di poter distribuire i progetti in cui il [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, il server deve contenere il `SSISDB` catalogo. Tramite il programma di installazione per [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] non viene creato automaticamente il catalogo. Sarà necessario crearlo manualmente usando le istruzioni seguenti.  
  
 Il catalogo SSISDB può essere creato in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Il catalogo può essere creato anche a livello di programmazione utilizzando Windows PowerShell.  
  
### <a name="to-create-the-ssisdb-catalog-in-sql-server-management-studio"></a>Per creare il catalogo SSISDB in SQL Server Management Studio  
  
1.  Aprire [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Connettersi al motore di database di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
3.  In Esplora oggetti espandere il nodo del server, fare clic con il pulsante destro del mouse sul nodo **Cataloghi di Integration Services** , quindi fare clic su **Creazione catalogo**.  
  
4.  Fare clic su **Abilitazione integrazione con CLR**.  
  
     Nel catalogo vengono utilizzate stored procedure CLR.  
  
5.  Fare clic su **Abilita l'esecuzione automatica della stored procedure di Integration Services all'avvio di SQL Server** per abilitare l'esecuzione della stored procedure [catalog.startup](/sql/integration-services/system-stored-procedures/catalog-startup) a ogni riavvio dell’istanza del server [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
     La stored procedure esegue la manutenzione dello stato delle operazioni per il catalogo SSISDB. Corregge lo stato di eventuali pacchetti in esecuzione in caso di arresto dell'istanza del server [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
6.  Immettere una password quindi fare clic su **Ok**.  
  
     La password consente di proteggere la chiave del database master utilizzata per crittografare i dati del catalogo. Salvare la password in un percorso sicuro. È consigliabile eseguire inoltre il backup della chiave master del database. Per altre informazioni, vedere [Backup della chiave master di un database](../relational-databases/security/encryption/back-up-a-database-master-key.md).  
  
### <a name="to-create-the-ssisdb-catalog-programmatically"></a>Per creare il catalogo SSISDB a livello di programmazione  
  
1.  Eseguire il seguente script di PowerShell:  
  
    ```  
    # Load the IntegrationServices Assembly  
    [Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Management.IntegrationServices")  
  
    # Store the IntegrationServices Assembly namespace to avoid typing it every time  
    $ISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"  
  
    Write-Host "Connecting to server ..."  
  
    # Create a connection to the server  
    $sqlConnectionString = "Data Source=localhost;Initial Catalog=master;Integrated Security=SSPI;"  
    $sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString  
  
    # Create the Integration Services object  
    $integrationServices = New-Object $ISNamespace".IntegrationServices" $sqlConnection  
  
    # Provision a new SSIS Catalog  
    $catalog = New-Object $ISNamespace".Catalog" ($integrationServices, "SSISDB", "P@assword1")  
    $catalog.Create()  
  
    ```  
  
     Per altri esempi di come usare Windows PowerShell e lo spazio dei nomi <xref:Microsoft.SqlServer.Management.IntegrationServices>, vedere l'intervento sul blog relativo a [SSIS e PowerShell in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=242539) nel sito blogs.msdn.com. Per una panoramica dello spazio dei nomi e degli esempi di codice, vedere l'intervento sul blog relativo a [uno sguardo rapido del modello a oggetti gestito del catalogo SSIS](http://go.microsoft.com/fwlink/?LinkId=254267)sul sito blogs.msdn.com.  
  
## <a name="see-also"></a>Vedere anche  
 [Catalogo SSIS](catalog/ssis-catalog.md)   
 [Backup, ripristino e spostamento del catalogo SSIS](../../2014/integration-services/backup-restore-and-move-the-ssis-catalog.md)  
  
  
