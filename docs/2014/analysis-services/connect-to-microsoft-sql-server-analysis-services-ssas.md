---
title: Connettersi a Microsoft SQL Server Analysis Services (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserveras.f1
ms.assetid: 7f3244ee-b690-471c-893d-68e361c2d416
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 43a7dd31c52c81f7a2bfcbf87d1a8df3f6740081
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323661"
---
# <a name="connect-to-microsoft-sql-server-analysis-services-ssas"></a>Connessione a Microsoft SQL Server Analysis Services (SSAS)
  Questa pagina della finestra di **importazione guidata tabella** consente di specificare le impostazioni per importare dati da un cubo di Microsoft SQL Server Analysis Services o una cartella di lavoro di PowerPivot ospitata in SharePoint. Per accedere alla procedura guidata da [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dal menu **Modello** selezionare **Importa da origine dati**.  
  
 Per connettersi a un'origine dati, è necessario che nel computer sia installato il provider appropriato.  
  
> [!NOTE]  
>  Le credenziali dell'utente corrente vengono utilizzate in caso di selezione di un database in questa pagina. Tuttavia, l'importazione non verrà completata se l'utente specificato nella pagina Impostazioni di rappresentazione non dispone di privilegi sufficienti per leggere dal database selezionato.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **Nome descrittivo connessione**  
 Digitare un nome univoco per questa connessione all'origine dati. Questo campo è obbligatorio.  
  
 **Nome File o server**  
 Eseguire una delle operazioni seguenti:  
  
-   Digitare il nome o l'indirizzo IP del server SQL Server Analysis Services al quale connettersi.  
  
     Per specificare il server locale, è possibile digitare un punto (.), (locale) o localhost.  
  
-   Digitare l'URL di una cartella di lavoro PowerPivot pubblicata in SharePoint.  
  
 **Usa autenticazione di Windows**  
 Specificare se utilizzare l'autenticazione di Windows per connettersi a un server SQL Server Analysis Services.  
  
 La modalità di autenticazione di Windows consente a un utente di connettersi mediante un account utente di Windows. Se possibile, è consigliabile utilizzare l'autenticazione di Windows.  
  
 Quando viene utilizzato questo tipo di autenticazione, le credenziali dell'utente corrente vengono utilizzate in caso di visualizzazione in anteprima e filtro dei dati nella finestra Proprietà tabella e nell'Importazione guidata. Non vengono utilizzate per importare o aggiornare dati; in tal caso vengono infatti utilizzate le credenziali di Windows specificate nella pagina Impostazioni di rappresentazione.  
  
 **Usa autenticazione di SQL Server**  
 Specificare se utilizzare l'autenticazione di SQL Server per connettersi a un server SQL Server Analysis Services.  
  
 Con questo tipo di autenticazione, in SQL Server l'autenticazione viene eseguita verificando che sia stato impostato un account di accesso di SQL Server e che la password specificata corrisponda a quella registrata in precedenza.  
  
 L'autenticazione di SQL Server viene utilizzata quando si crea la stringa di connessione per l'origine dati. Queste credenziali vengono utilizzate anche in caso di visualizzazione in anteprima e filtro dei dati nella finestra Proprietà tabella e nell'Importazione guidata. Non vengono utilizzate per importare o aggiornare dati; in tal caso vengono infatti utilizzate le credenziali di Windows specificate nella pagina Impostazioni di rappresentazione.  
  
 **Nome utente**  
 Specificare un nome utente per la connessione al database. Questa opzione è disponibile solo si è scelto di utilizzare l'autenticazione di Windows per la connessione.  
  
 **Password**  
 Specificare una password per la connessione al database. Questa opzione è modificabile solo se è stata selezionata l'autenticazione di SQL Server per la connessione.  
  
 **Salva password**  
 Specificare se la password immessa nella casella **Password** è stata archiviata. Questa opzione è disponibile solo se è stata selezionata l'autenticazione di SQL Server per la connessione.  
  
 **Nome database**  
 Selezionare un database dall'elenco di database.  
  
 **Advanced**  
 Impostare ulteriori proprietà relative alla connessione tramite la finestra di dialogo **Impostazione delle proprietà avanzate** . Per altre informazioni, vedere [Impostazione delle proprietà avanzate &#40;SSAS&#41;](set-advanced-properties-ssas.md).  
  
 **Test connessione**  
 Provare a stabilire una connessione all'origine dati utilizzando le impostazioni correnti. Viene visualizzato un messaggio che indica se la connessione è stata stabilita.  
  
  
