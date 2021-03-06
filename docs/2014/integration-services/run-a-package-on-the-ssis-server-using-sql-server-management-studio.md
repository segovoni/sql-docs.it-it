---
title: Eseguire un pacchetto nel Server SSIS mediante SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 56dc1bf8-99d4-41dc-bdc4-f64f1ccfd688
caps.latest.revision: 8
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 58348805f20f33124e0a789c79aa2ef71f9d8793
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37225551"
---
# <a name="run-a-package-on-the-ssis-server-using-sql-server-management-studio"></a>Eseguire un pacchetto sul server SSIS mediante SQL Server Management Studio
  Dopo aver distribuito il progetto nel server [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], è possibile eseguire il pacchetto nel server.  
  
 È possibile utilizzare i report relativi alle operazioni per visualizzare informazioni sui pacchetti eseguiti, o che sono attualmente in esecuzione, nel server. Per altre informazioni, vedere [Report per il server Integration Services](../../2014/integration-services/reports-for-the-integration-services-server.md).  
  
### <a name="to-run-a-package-on-the-server-using-sql-server-management-studio"></a>Per eseguire un pacchetto nel server mediante SQL Server Management Studio  
  
1.  Aprire [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] e connettersi all'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in cui è contenuto il catalogo di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
2.  In Esplora oggetti espandere il nodo **Cataloghi di Integration Services** , il nodo **SSISDB** e navigare al pacchetto contenuto nel progetto distribuito.  
  
3.  Fare clic con il pulsante destro del mouse sul nome del pacchetto e selezionare **Esegui**.  
  
4.  Configurare l'esecuzione del pacchetto usando le impostazioni sulle schede **Parametri**, **Gestioni connessioni**e **Avanzate** nella finestra di dialogo **Esegui pacchetto** .  
  
5.  Fare clic su **OK** per eseguire il pacchetto.  
  
     oppure  
  
     Utilizzare le stored procedure per eseguire il pacchetto. Fare clic su **Script** per generare l'istruzione Transact-SQL tramite cui viene creata e avviata un'istanza dell'esecuzione. Nell'istruzione è inclusa una chiamata alle stored procedure catalog.create_execution, catalog.set_execution_parameter_value e catalog.start_execution. Per altre informazioni su queste stored procedure, vedere [catalog.create_execution &#40;database SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database), [catalog.set_execution_parameter_value &#40;database SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) e [catalog.start_execution &#40;database SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).  
  
  
