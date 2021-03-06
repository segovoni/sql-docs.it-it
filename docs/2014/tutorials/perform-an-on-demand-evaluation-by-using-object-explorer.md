---
title: Eseguire una valutazione su richiesta utilizzando Esplora oggetti | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ee6d3b79-18bc-49d3-8a1d-0c0905b990f0
caps.latest.revision: 8
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 95ce7493353fbce70ec10f575b7a637ea4d8809c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37237931"
---
# <a name="perform-an-on-demand-evaluation-by-using-object-explorer"></a>Esecuzione di una valutazione su richiesta utilizzando Esplora oggetti
  In questa attività verrà utilizzato Esplora oggetti per eseguire una valutazione su richiesta di criteri per procedure consigliate per il [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] in una singola istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  È inoltre possibile valutare criteri in un'istanza singola mediante Server registrati. Per altre informazioni, vedere [eseguire una valutazione su richiesta da server registrati tramite](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Questa lezione è basata sulla versione di [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Per eseguire una valutazione su richiesta dei criteri per procedure consigliate ottimali per istanze che eseguono [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], è necessario usare la procedura nell'argomento [eseguire una valutazione su richiesta da server registrati tramite](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).  
  
### <a name="to-perform-an-on-demand-evaluation-by-using-object-explorer"></a>Per eseguire una valutazione su richiesta utilizzando Esplora oggetti  
  
1.  Avviare [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], quindi connettersi al [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  In Esplora oggetti, espandere **Management**, espandere **gestione dei criteri**, fare doppio clic su **criteri**e quindi fare clic su **Evaluate**.  
  
    > [!NOTE]  
    >  Per impostazione predefinita, l'istanza locale viene utilizzata come origine dei criteri. Se in precedenza sono stati importati criteri per procedure consigliate, questi verranno elencati insieme agli altri criteri creati. È possibile selezionare uno qualsiasi dei criteri consigliate importati e quindi fare clic su **Evaluate**. Se non sono stati importati criteri per procedure consigliate, continuare con questa procedura.  
  
3.  Nel **valuta criteri** accanto alla finestra di dialogo il **origine** fare clic sui puntini di sospensione (**...** ) pulsante.  
  
4.  Nel **Seleziona origine** nella finestra di dialogo è possibile selezionare uno **file** oppure **Server** come origine dei file di criteri da valutare. Se si sceglie **Server**, è possibile eseguire una valutazione su richiesta di eventuali criteri consigliate precedentemente importati nella gestione basata su criteri in un server locale o remoto. In questa esercitazione, si farà clic sul **file**e quindi selezionare i file dei criteri individuali che si desidera valutare. A tale scopo, eseguire le operazioni seguenti:  
  
    1.  Fare clic su **file**.  
  
    2.  Accanto a **file**, fare clic sui puntini di sospensione (**...** ) pulsante.  
  
    3.  Nel **Seleziona criteri** della finestra di dialogo passare alla cartella seguente, che contiene i criteri per procedure consigliate migliori:  
  
         **C:\Programmi\Microsoft file (x86) \Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**  
  
        > [!NOTE]  
        >  Il percorso del file può variare in base alla posizione in cui sono stati installati i file di programma di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], all'esecuzione di un sistema operativo a 32 o a 64 bit e all'identificatore di lingua.  
  
    4.  Selezionare uno o più file con estensione XML dei criteri per valutare e quindi fare clic su **aperto**.  
  
         Verrà visualizzato l'elenco di file selezionati nel **file** casella.  
  
    5.  Nel **Seleziona origine** finestra di dialogo, fare clic su **OK**.  
  
    6.  Se il **i criteri di caricamento** verrà visualizzata la finestra di dialogo, fare clic su **Chiudi**.  
  
     I criteri selezionati sono elencati nella **selezione criteri** pagina. L'icona di avviso accanto ai criteri indica che questi contengono script.  
  
5.  Fare clic su **Evaluate** per valutare i criteri.  
  
     Nel **risultati** di tabella, i risultati per ogni criterio sono elencati. Un'icona "x" rossa indica che la conformità di criteri non è riuscita.  
  
6.  Per alcuni errori relativi ai criteri, la gestione basata su criteri consente di applicare immediatamente la conformità di criteri nella destinazione. Per questo tipo di errori verrà visualizzata una casella di controllo accanto ai criteri che presentano errori. Se si seleziona la casella di controllo, il **applica** pulsante diventa disponibile. Quando fa clic su **applica**, l'impostazione non conforme verrà aggiornata automaticamente nell'istanza di destinazione.  
  
    > [!CAUTION]  
    >  Assicurarsi di aver compreso a pieno tutte le impostazioni dei criteri prima di aggiornare automaticamente un'istanza di destinazione. È consigliabile che dopo aver selezionato uno o più caselle di controllo, si fa clic su **Script**, scegliere un percorso di output in modo da poter esaminare sottostante [!INCLUDE[tsql](../includes/tsql-md.md)] prima di applicare le modifiche del codice.  
  
7.  Per visualizzare i risultati dettagliati per un criterio, fare clic sul criterio nel **risultati** tabella.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Esecuzione di una valutazione su richiesta usando Server registrati](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)  
  
  
