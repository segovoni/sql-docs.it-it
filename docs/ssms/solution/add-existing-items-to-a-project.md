---
title: Aggiungere elementi esistenti a un progetto | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-solutions
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 084b3879-e96b-45a7-b421-6a4b0db2b92b
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a0d1bcd6432154b0b801b9f098fa22308a4fc0dd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33044658"
---
# <a name="add-existing-items-to-a-project"></a>Aggiunta di elementi esistenti a un progetto
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
È possibile aggiungere nuovi elementi a un progetto per estendere la funzionalità dell'applicazione. Un elemento esistente può essere una query o un file esterno. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] sono presenti due tipi di progetto: progetto script di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e progetto script di Analysis Services. I file di query che è possibile aggiungere varieranno a seconda del tipo di progetto. È possibile aggiungere, ad esempio, una query [!INCLUDE[tsql](../../includes/tsql_md.md)] (un file con estensione sql) a un progetto script di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , ma non a un progetto script di Analysis Services. Per associare ulteriori estensioni di file a un tipo di progetto, vedere [Procedura: Associazione di estensioni di file a un editor di codice](http://msdn.microsoft.com/en-us/193630f4-93de-4950-8f36-68702531f925).  
  
### <a name="to-add-an-existing-query-or-a-miscellaneous-file-to-a-project"></a>Per aggiungere una query o un file esterno esistente a un progetto  
  
1.  In Esplora soluzioni selezionare un progetto di destinazione.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi elemento esistente**.  
  
    **Look in**  
    Utilizzare questo elenco per individuare i file o le cartelle da aggiungere al progetto. Per i servizi Web XML e le applicazioni Web ASP.NET, i file si trovano nel server Web.  
  
    **Desktop**  
    Consente di visualizzare i file e le cartelle che si trovano sul desktop.  
  
    **Progetti**  
    Consente di visualizzare i file e le cartelle nella posizione predefinita **Progetti** .  
  
    **Risorse del computer**  
    Consente di visualizzare il contenuto della cartella **Risorse del computer** .  
  
    **Nome file**  
    Questa opzione consente di applicare un filtro alle cartelle e ai file visualizzati. Immettere il nome completo o parziale del file in base al quale applicare il filtro. Utilizzare un asterisco (`*`) come carattere jolly.  
  
    > [!NOTE]  
    > Per spostarsi su percorsi Web e di rete, immettere l'URL o il percorso di rete nella casella **Nome file** . Ad esempio, se si digita **http://mywebsite** vengono visualizzati i file disponibili nel percorso Web mywebsite, mentre se si digita **\\\myserver\myshare** vengono visualizzati i file disponibili nel percorso myshare del server myserver.  
  
    **Tipo file**  
    Questa opzione consente di applicare un filtro ai file in base all'estensione. In ogni prodotto vengono elencati i filtri predefiniti dei tipi di file più comuni.  
  
    **Aggiungi**  
    Utilizzare questo pulsante a discesa per aggiungere l'elemento al progetto e aprirlo nell'editor predefinito.  
  
    -   **Aggiungi**  
  
        Consente di copiare l'elemento esistente nella cartella del progetto memorizzata sul disco e di aggiungerlo sotto il progetto selezionato in Esplora soluzioni. Le modifiche apportate all'elemento non si rifletteranno su quello presente nella posizione originale. Si tratta dell'editor predefinito per il tipo di file.  
  
    -   **Aggiungi come collegamento**  
  
        Consente di aggiungere il file selezionato al progetto e di aprirlo nell'editor predefinito per il tipo di file. Il file selezionato originariamente viene aperto, ma non copiato nella cartella del progetto.  
  
3.  Se vengono aggiunti file di query, nella finestra di dialogo di connessione verrà visualizzato un messaggio in cui si chiede di specificare una connessione per la query. Se non si desidera associare una connessione alla query, fare clic su **Annulla** nella finestra di dialogo di connessione.  
  
4.  Il file verrà aggiunto alla cartella **Query** o **File esterni** del progetto.  
  
## <a name="see-also"></a>Vedere anche  
[Esplora soluzioni](../../ssms/solution/solution-explorer.md)  
[Aggiunta di nuovi elementi a un progetto](../../ssms/solution/add-new-items-to-a-project.md)  
[Rimuovere o eliminare un elemento o un progetto](../../ssms/solution/remove-or-delete-an-item-or-project.md)  
  
