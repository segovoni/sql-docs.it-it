---
title: Aggiungere un'azione Standard | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4a6af04d1ed2b8db53425ad0aaf83d95d73dd6f8
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34020638"
---
# <a name="add-a-standard-action"></a>Aggiungere un'azione standard
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Utilizzando la visualizzazione Azioni in Progettazione cubi è possibile aggiungere un'azione a un database. L'accesso a tale visualizzazione può essere effettuato da [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Una volta creata, un'azione diventa disponibile agli utenti dopo aver rielaborato il cubo attinente. Per altre informazioni, vedere [Elaborazione di oggetti di Analysis Services](../../analysis-services/multidimensional-models/processing-analysis-services-objects.md).  
  
### <a name="to-create-an-action"></a>Per creare un'azione  
  
1.  Aprire il cubo per il quale si desidera creare un'azione, quindi fare clic sulla scheda **Azioni** .  
  
2.  Nella barra degli strumenti fare clic sull'icona **Nuova azione** , quindi effettuare i passaggi seguenti nel riquadro dell'espressione:  
  
    -   In **Nome**digitare un nome per l'azione.  
  
    -   Nell'elenco a discesa **Tipo di destinazione** selezionare il tipo di oggetto al quale si desidera collegare l'azione. L'oggetto selezionato in **Tipo di destinazione** consente di determinare gli oggetti disponibili e il tipo di selezione che è possibile effettuare in **Oggetto di destinazione**. Nella tabella seguente sono elencate le selezioni **Oggetto di destinazione** valide per ogni tipo di destinazione.  
  
        |Se si seleziona il tipo di destinazione seguente|Effettuare la selezione seguente in Oggetto di destinazione|  
        |---------------------------------------------|---------------------------------------------------|  
        |Membri dell'attributo|L'unica selezione valida è una sola gerarchia dell'attributo. Il tipo di destinazione dell'azione saranno tutti i membri dell'attributo indipendentemente dalla posizione di visualizzazione, ovvero l'azione verrà applicata anche alle gerarchie definite dall'utente.|  
        |Celle|Tutte le celle è l'unica selezione disponibile. Se si sceglie **Celle** come tipo di destinazione, è possibile digitare un'espressione in **Condizione** per limitare le celle alle quali è associata l'azione.|  
        |Cube|CURRENTCUBE è l'unica selezione disponibile. L'azione è associata al cubo corrente.|  
        |Membri della dimensione|Selezionare un'unica dimensione. L'azione sarà associata a tutti i membri della dimensione.|  
        |Gerarchia|Selezionare un'unica gerarchia. L'azione sarà associata solo all'oggetto gerarchia. Le gerarchie dell'attributo vengono visualizzate nell'elenco solo se le proprietà **AttributeHierarchyEnabled** e **AttributeHierarchyVisible** vengono impostate su **True**.|  
        |Membri della gerarchia|Selezionare un'unica gerarchia. L'azione sarà associata a tutti i membri della gerarchia selezionata. Le gerarchie dell'attributo vengono visualizzate nell'elenco solo se le proprietà **AttributeHierarchyEnabled** e **AttributeHierarchyVisible** vengono impostate su **True**.|  
        |Level|Selezionare un unico livello. L'azione sarà associata solo all'oggetto livello.|  
        |Membri del livello|Selezionare un unico livello. L'azione sarà associata a tutti i membri del livello selezionato.|  
  
    -   In **Oggetto di destinazione** fare clic sulla freccia a destra della casella di testo e nella visualizzazione albero che viene aperta fare clic sull'oggetto al quale si desidera collegare l'azione, quindi selezionare **OK**.  
  
    -   Facoltativo. In **Condizione** creare un'espressione MDX per limitare la destinazione dell'azione. È possibile digitare manualmente l'espressione oppure trascinare gli elementi dalle schede **Metadati** e **Funzioni**.  
  
    -   Nell'elenco a discesa **Tipo** selezionare il tipo di azione che si desidera creare. Nella tabella seguente sono elencati i tipi di azioni disponibili.  
  
        |Tipo|Description|  
        |----------|-----------------|  
        |Set di dati|Consente di recuperare un set di dati.|  
        |Proprietario|Consente di eseguire un'operazione utilizzando un'interfaccia diversa da quelle elencate in questa tabella.|  
        |Set di righe|Consente di recuperare un set di righe.|  
        |Istruzione|Esegue un comando OLE DB.|  
        |URL|Consente di visualizzare una pagina Web in un browser Internet.|  
  
    -   In **Espressione azione**creare un'espressione che definisca l'azione. L'espressione deve restituire una stringa. È possibile digitare manualmente l'espressione oppure trascinare gli elementi dalle schede **Metadati** e **Funzioni**.  
  
3.  Facoltativo. Espandere **Proprietà aggiuntive**, quindi effettuare uno dei passaggi seguenti:  
  
    -   Nell'elenco a discesa **Chiamata** specificare come viene richiamata l'azione. Nella tabella seguente sono descritte le opzioni disponibili per il richiamo di un'azione.  
  
        |Opzione|Description|  
        |------------|-----------------|  
        |Interattiva|L'azione viene attivata dall'interazione dell'utente.|  
        |Batch|L'azione viene eseguita come operazione batch.|  
        |Su apertura|L'azione viene eseguita in seguito all'apertura del cubo da parte dell'utente.|  
  
    -   In **Applicazione**digitare il nome dell'applicazione associata all'azione. Ad esempio, se si crea un'azione che consente a un utente di visualizzare un particolare sito Web, l'applicazione associata all'azione deve essere Microsoft Internet Explorer o un altro Web browser.  
  
        > [!NOTE]  
        >  Le azioni proprietarie non vengono restituite al server a meno che l'applicazione client non consenta di limitare in modo esplicito il set di righe dello schema in modo da restituire solo le azioni che corrispondono al nome specificato in **Applicazione**.  
  
    -   In **contenuto azione**, se si utilizza il tipo di URL, racchiudere l'indirizzo Internet tra virgolette, ad esempio, "http://www.adventure-works.com".  
  
    -   In **Descrizione**digitare una descrizione per l'azione.  
  
    -   In **Didascalia**digitare una didascalia o un'espressione MDX che consenta la restituzione di una didascalia. Questa didascalia viene visualizzata agli utenti finali all'avvio dell'azione. Se non si specifica nessuna didascalia, viene utilizzato il nome dell'azione.  
  
    -   Nell'elenco a discesa **Didascalia MDX** specificare se la didascalia è MDX. Questo campo consente di indicare al server se restituire il contenuto di **Didascalia** come espressione MDX.  
  
  
