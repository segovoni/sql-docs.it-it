---
title: 'Lesson 2: Specifying Connection Information (Reporting Services) (Lezione 2: Specifica delle informazioni di connessione (Reporting Services)) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
caps.latest.revision: 47
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: c9e828696135d13263a68219c1a248325a14676d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196791"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Lezione 2: Specifica delle informazioni di connessione (Reporting Services)
  Dopo aver aggiunto un report al progetto Tutorial, è necessario definire un' *origine dati*, vale a dire informazioni di connessione usate dal report per accedere ai dati da un database relazionale, da un database multidimensionale o da un'altra risorsa.  
  
 In questa lezione come origine dati verrà utilizzato il database di esempio [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]. L'esercitazione presuppone che il database si trovi in un'istanza predefinita del [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] di [!INCLUDE[ssDE](../includes/ssde-md.md)] installata nel computer locale.  
  
### <a name="to-set-up-a-connection"></a>Per impostare una connessione  
  
1.  Nel riquadro **Dati report** , fare clic su **Nuova** , quindi su **Origine dati**.  
  
    > [!NOTE]  
    >  Se il riquadro **Dati report** non è visualizzato, scegliere **Dati report** dal menu **Visualizza**.  
  
2.  In **Nome**digitare [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)].  
  
3.  Accertarsi che sia selezionata l'opzione **Connessione incorporata** .  
  
4.  In **Tipo**selezionare **Microsoft SQL Server**.  
  
5.  In **Stringa di connessione**digitare quanto segue:  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
     Per questa stringa di connessione si presuppone che [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], il server di report e il database [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] siano installati nel computer locale e che si disponga dell'autorizzazione per l'accesso al database [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)].  
  
    > [!NOTE]  
    >  Se si utilizza [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services oppure un'istanza denominata, è necessario includere nella stringa di connessione le informazioni sull'istanza:  
    >   
    >  `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2012`  
    >   
    >  Per altre informazioni sulle stringhe di connessione, vedere [connessioni dati, origini dati e stringhe di connessione in Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md) e [finestra di dialogo Proprietà origine dati, generale](data-source-properties-dialog-box-general.md).  
  
6.  Fare clic su **Credenziali** nel riquadro sinistro e selezionare **Usa autenticazione di Windows (sicurezza integrata)**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)] zdroj dat [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] viene aggiunto per il **i dati del Report** riquadro.  
  
## <a name="next-task"></a>Attività successiva  
 È stata definita correttamente una connessione per il [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database di esempio. Verrà successivamente creato il report. Vedere [Lezione 3: Definizione di un set di dati per il report tabella &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Connessioni dati, origini dati e stringhe di connessione in Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
