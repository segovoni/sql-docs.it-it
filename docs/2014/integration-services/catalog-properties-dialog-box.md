---
title: Finestra di dialogo proprietà del catalogo | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.iscatalogprop.general.f1
- sql12.ssis.ssms.iscreatecatalog.f1
ms.assetid: 3e2fcf11-e010-41c6-bc26-e4b281c0bfbc
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 717b3d818ddd01868506a3787a698ea8f2f45433
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312061"
---
# <a name="catalog-properties-dialog-box"></a>Finestra di dialogo Proprietà catalogo
  Utilizzare la finestra di dialogo Proprietà catalogo per configurare il catalogo di SSISDB. Le proprietà del catalogo consentono di definire come vengono crittografati i dati sensibili, come vengono mantenuti i dati del controllo delle versioni dei progetti e quando si verifica il timeout delle operazioni di convalida. Il catalogo di SSISDB rappresenta un punto centrale di archiviazione e amministrazione di progetti, pacchetti, parametri e ambienti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Inoltre, è possibile visualizzare le proprietà del catalogo nella vista catalog.catalog_property e impostare le proprietà tramite la stored procedure catalog.configure_catalog. Per altre informazioni, vedere [catalog.catalog_properties &#40;database SSISDB&#41;](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database) e [catalog.configure_catalog &#40;database SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database).  
  
 Per informazioni sulla creazione del catalogo di SSISDB, vedere [Creare il catalogo SSIS](catalog/ssis-catalog.md).  
  
 **Per saperne di più**  
  
-   [Aprire la finestra di dialogo Proprietà catalogo](#open_dialog)  
  
-   [Configurare le opzioni](#options)  
  
##  <a name="open_dialog"></a> Aprire la finestra di dialogo Proprietà catalogo  
  
1.  Aprire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
2.  Connettersi al motore di database di Microsoft SQL Server.  
  
3.  In Esplora oggetti espandere il nodo **Integration Services** , fare clic con il pulsante destro del mouse su **SSISDB**, quindi fare clic su **Proprietà**.  
  
##  <a name="options"></a> Configurare le opzioni  
  
### <a name="options"></a>Opzioni  
 Nella tabella seguente sono descritte determinate proprietà nella finestra di dialogo e le proprietà corrispondenti nella vista catalog.catalog_property.  
  
|Nome proprietà (finestra di dialogo Proprietà catalogo)|Nome proprietà (vista catalog.catalog_property)|Description|  
|-----------------------------------------------------|------------------------------------------------------|-----------------|  
|Nome algoritmo di crittografia|ENCRYPTION_CLEANUP_ENABLED|Consente di specificare il tipo di crittografia utilizzato per crittografare i valori di parametro sensibili nel catalogo. Di seguito sono indicati i valori possibili:<br /><br /> **DES**<br /><br /> **TRIPLE_DES**<br /><br /> **TRIPLE_DES_3KEY**<br /><br /> **DESPX**<br /><br /> **AES_128**<br /><br /> **AES_192**<br /><br /> **AES_256** (impostazione predefinita)|  
|Timeout di convalida (secondi)|VALIDATION_TIMEOUT|Specificare il numero massimo di secondi durante i quali è possibile eseguire la convalida di un progetto o di un pacchetto prima dell'arresto. Il valore predefinito è 300 secondi.<br /><br /> L'esecuzione della convalida è un'operazione asincrona. Più grande è il progetto o il pacchetto, più tempo richiederà la convalida.<br /><br /> Per informazioni sulla convalida di progetti e pacchetti, vedere [Tipi di dati nelle espressioni di Integration Services](expressions/integration-services-data-types-in-expressions.md).|  
|Pulisci log periodicamente|OPERATION_CLEANUP_ENABLED|Impostare la proprietà su True per indicare l'esecuzione della pulizia di operazioni da parte del processo di SQL Server Agent. In caso contrario, impostare la proprietà su False.|  
|Periodo di memorizzazione (giorni)|RETENTION_WINDOW|Specificare la validità massima di dati di operazioni consentiti (in giorni). I dati che superano il numero di giorni specificato saranno rimossi dalla pulizia di operazioni del processo di SQL Agent.|  
|Numero massimo di versioni per progetto|MAX_PROJECT_VERSIONS|Specificare il numero di versioni di un progetto che verranno archiviate nel catalogo. Versioni precedenti di progetti che superano il numero massimo saranno rimosse quando verrà eseguito il processo di pulizia della versione del progetto.|  
  
  
