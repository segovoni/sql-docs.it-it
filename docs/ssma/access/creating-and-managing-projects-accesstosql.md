---
title: Creazione e gestione di progetti (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- creating projects
- new projects
- opening projects
- projects
- projects, creating and managing
- saving metadata
- saving projects
ms.assetid: f2d1f0b0-5394-4adb-b3f3-abd71eb68ca7
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b8b8be30f9a8619ef3e2887c37387e1f4ef68e6d
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985643"
---
# <a name="creating-and-managing-projects-accesstosql"></a>Creazione e gestione di progetti (AccessToSQL)
Eseguire la migrazione di database di Access in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è necessario creare innanzitutto un progetto SSMA. Il progetto è un file che contiene metadati sui database di Access che si desidera eseguire la migrazione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, i metadati relativi all'istanza di destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure in cui verranno inseriti gli oggetti migrati e dati, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] informazioni di connessione e le impostazioni del progetto.  
  
## <a name="reviewing-default-project-settings"></a>Esame impostazioni predefinite del progetto  
SSMA contiene diverse opzioni per la conversione e la sincronizzazione degli oggetti di database e per la conversione dei dati. L'impostazione predefinita per queste opzioni è appropriata per molti utenti. Tuttavia, prima di creare un nuovo progetto SSMA, si deve esaminare le opzioni e, se si desidera, modificare le impostazioni predefinite che verranno usate per tutti i nuovi progetti.  
  
**Per controllare le impostazioni di progetto predefinito**  
  
1.  Nel **degli strumenti** dal menu **impostazioni di progetto predefinite**.  
  
2.  Selezionare il tipo di progetto in **versione di destinazione della migrazione** elenco a discesa per quali impostazioni devono essere visualizzati o modificati e quindi fare clic su **generali** scheda.  
  
3.  Nel riquadro sinistro, fare clic su **conversione**.  
  
4.  Nel riquadro di destra, esaminare le opzioni. Per altre informazioni su queste opzioni, vedere [impostazioni progetto (conversione)](http://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388).  
  
5.  Modificare le opzioni in base alle esigenze.  
  
6.  Ripetere i passaggi precedenti per il **migrazione**, **GUI**, e **Mapping di tipo** pagine.  
  
    -   Per informazioni sulle opzioni di migrazione, vedere [impostazioni progetto (migrazione)](http://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d).  
  
    -   Per informazioni sulle opzioni dell'interfaccia utente, vedere [impostazioni progetto (GUI)](http://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693).  
  
    -   Per altre informazioni sulle impostazioni di mapping dei tipi di dati, vedere [impostazioni progetto (Mapping dei tipi)](http://msdn.microsoft.com/b87b9683-abed-4677-8c50-18bdba704655).  
  
    -   Per informazioni sulle impostazioni di SQL Azure, vedere [impostazioni progetto (SQL Azure)](http://msdn.microsoft.com/bbb8a204-d0e4-4f0b-9709-271feb1f136e).  
  
**Nota** le impostazioni di SQL Azure saranno disponibili solo quando si seleziona la migrazione a SQL Azure durante la creazione di un progetto.  
  
## <a name="creating-new-projects"></a>Creazione di nuovi progetti  
SSMA viene avviato senza il caricamento di un progetto predefinito. Per eseguire la migrazione dei dati dal database di Access in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è necessario creare un progetto.  
  
**Per creare un nuovo progetto**  
  
1.  Scegliere **Nuovo progetto** dal menu **File**.  
  
    Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  Nel **nome** immettere un nome per il progetto.  
  
3.  Nel **posizione** casella, immettere o selezionare una cartella per il progetto  
  
4.  Nell'elenco per la migrazione verso il basso, selezionare uno di SQL Server 2005 / SQL Server 2008 o SQL Server 2012 o SQL Server 2014 / SQL Server 2016 / Azure SQL DB, quindi fare clic su **OK**.  
  
SSMA consente di creare il file di progetto. È ora possibile eseguire il passaggio successivo della [aggiunta di uno o più database di Access](http://msdn.microsoft.com/e944c740-4c8a-4bc1-b0ed-be57bc06dced).  
  
## <a name="customizing-project-settings"></a>Personalizzazione delle impostazioni di progetto  
Oltre a definire impostazioni di progetto predefinite, che si applicano a tutti i nuovi progetti SSMA, è anche possibile personalizzare le impostazioni per ogni progetto. Per altre informazioni, vedere [impostazione di conversione e le opzioni di migrazione](http://msdn.microsoft.com/0a7304df-2f35-4453-96ef-7ac83dea1167).  
  
Quando si personalizzano i mapping tra i database di origine e di destinazione, è possibile definire i mapping per il progetto, database o a livello di oggetto. Per altre informazioni sul mapping dei tipi, vedere [tipi di dati di destinazione e origine del Mapping](http://msdn.microsoft.com/b362a075-16e7-423f-b63f-e1e9f02844a9).  
  
## <a name="saving-projects"></a>Il salvataggio dei progetti  
Quando si salva un progetto, SSMA rende persistenti le impostazioni del progetto e, facoltativamente, i metadati del database, al file di progetto.  
  
**Per salvare un progetto**  
  
-   Nel **File** dal menu **Salva progetto**.  
  
    Se i database all'interno del progetto sono stati modificati o non sono stati convertiti, SSMA richiederà di salvare i metadati nel progetto. Salvataggio dei metadati consente di lavorare offline. Consente inoltre di inviare un file di progetto completo ad altre persone, tra cui il personale di supporto tecnico. Se viene chiesto di salvare i metadati, eseguire le operazioni seguenti:  
  
    1.  Per ogni database che viene visualizzato lo stato **i metadati mancanti**, selezionare la casella di controllo accanto al nome del database.  
  
        Salvataggio di metadati potrebbe richiedere alcuni minuti. Se non si desidera salvare i metadati a questo punto, non selezionare le caselle di controllo.  
  
    2.  Fare clic su **Salva**.  
  
        Analizza gli schemi di accesso e salvare i metadati del file di progetto SSMA.  
  
## <a name="opening-projects"></a>Apertura di progetti  
Quando si apre un progetto, questo viene disconnesso dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Ciò consente di lavorare offline. Per aggiornare gli oggetti di database carica i metadati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Per eseguire la migrazione dei dati, è necessario riconnettersi alla [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
**Per aprire un progetto**  
  
1.  Usare una delle procedure riportate di seguito:  
  
    -   Nel **File** dal menu **progetti recenti**e quindi selezionare il progetto da aprire.  
  
    -   Nel **File** dal menu **aprire il progetto**, individuare il file di progetto .a2ssproj, selezionare il file e quindi fare clic su **Open**.  
  
2.  Per riconnettersi [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]via il **File** dal menu **Riconnetti a SQL Server**.  
  
3.  Per riconnettersi a SQL Azure, nelle **File** dal menu **ristabilire la connessione a SQL Azure.**  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione consiste [aggiungere uno o più database di Access](http://msdn.microsoft.com/e944c740-4c8a-4bc1-b0ed-be57bc06dced).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione dei database di Access a SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Aggiunta e rimozione di file di Database di Access](http://msdn.microsoft.com/e944c740-4c8a-4bc1-b0ed-be57bc06dced)  
  
