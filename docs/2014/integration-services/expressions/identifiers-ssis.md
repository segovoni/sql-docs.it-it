---
title: Identificatori (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- regular identifiers [Integration Services]
- variables [Integration Services], expressions
- identifiers [Integration Services]
- expressions [Integration Services], variables
- lineage identifiers
- columns [Integration Services], identifiers
- names [Integration Services]
- expressions [Integration Services], identifiers
- qualified identifiers [Integration Services]
ms.assetid: 56af984d-88b4-4db8-b6a2-6b07315a699e
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 322a91c77eaac5433cada0cfef056e1688020dc6
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084003"
---
# <a name="identifiers-ssis"></a>Identificatori (SSIS)
  Nelle espressioni gli identificatori sono colonne e variabili disponibili per l'operazione. Le espressioni possono utilizzare identificatori regolari e qualificati.  
  
## <a name="regular-identifiers"></a>Identificatori regolari  
 Un identificatore regolare è un identificatore per cui non sono necessari ulteriori qualificatori. È un identificatore regolare ad esempio la colonna **MiddleName**della tabella **Contacts** del database **AdventureWorks** .  
  
 Per gli identificatori regolari sono previste le regole di denominazione seguenti:  
  
-   Il primo carattere del nome deve essere una lettera, come definito dallo standard Unicode 2.0, o un carattere di sottolineatura (_).  
  
-   I caratteri successivi possono includere lettere o numeri, come definito dallo Standard Unicode 2.0, il carattere di sottolineatura (_), \@, $ e & caratteri.  
  
> [!IMPORTANT]  
>  Gli identificatori regolari non possono contenere spazi e caratteri speciali diversi da quelli indicati. Se si desidera includere spazi e caratteri speciali, sarà necessario utilizzare un identificatore qualificato anziché un identificatore regolare.  
  
## <a name="qualified-identifiers"></a>Identificatori qualificati  
 Un identificatore qualificato è un identificatore delimitato da parentesi quadre. Può essere necessario un delimitatore perché il nome dell'identificatore include spazi o il primo carattere del nome non è una lettera né il carattere di sottolineatura (_). Se si usa il nome di colonna **Middle Name** in un'espressione, ad esempio, sarà necessario qualificarlo racchiudendolo tra parentesi quadre, in modo da ottenere [Middle Name].  
  
 Se il nome dell'identificatore include spazi o non è un nome di identificatore regolare valido, sarà necessario qualificarlo. Per qualificare gli identificatori l'analizzatore di espressioni utilizza le parentesi quadre aperta e chiusa ([]), che occupano rispettivamente la prima e l'ultima posizione della stringa. L'identificatore 5$> diventa ad esempio [5$>]. È possibile utilizzare parentesi quadre con nomi di colonne, variabili e funzioni.  
  
 Nelle espressioni compilate utilizzando le finestre di dialogo di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , gli identificatori regolari vengono automaticamente racchiusi tra parentesi quadre. Le parentesi quadre sono tuttavia necessarie solo se il nome include caratteri non validi. Il nome di colonna **MiddleName** , ad esempio, è valido anche senza parentesi quadre.  
  
 Nelle espressioni non è possibile fare riferimento a nomi di colonne che includono parentesi quadre. Il nome di colonna **Column[1]** , ad esempio, non può essere usato in un'espressione. Per utilizzarlo in un'espressione, è necessario modificarlo in un nome che non includa parentesi quadre.  
  
## <a name="lineage-identifiers"></a>identificatori di derivazione  
 Nelle espressioni è possibile utilizzare identificatori di derivazione per fare riferimento alle colonne. Gli identificatori di derivazione vengono assegnati automaticamente al momento della creazione del pacchetto. L'identificatore di derivazione di una colonna è visualizzato nella scheda **Proprietà colonna** della finestra di dialogo **Editor avanzato** di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Per fare riferimento a una colonna tramite il relativo identificatore di derivazione, è necessario anteporre a quest'ultimo un simbolo di cancelletto (#) come prefisso. Se ad esempio una colonna ha identificatore di derivazione 147, per farvi riferimento sarà necessario specificare #147.  
  
 Se l'analisi di un'espressione viene completata regolarmente, l'analizzatore di espressioni sostituirà gli identificatori di derivazione con i nomi delle colonne nella finestra di dialogo.  
  
## <a name="unique-column-names"></a>Nomi di colonna univoci  
 In uno stesso pacchetto possono essere utilizzati più componenti che espongono colonne con lo stesso nome. Per consentire l'analisi delle espressioni che utilizzano tali colonne, è necessario eliminare le ambiguità. L'analizzatore di espressioni supporta la notazione con punto per l'identificazione dell'origine della colonna. Due colonne con il nome **Age** possono ad esempio diventare **FlatFileSource.Age** e **OLEDBSource.Age**, per indicare che le rispettive origini sono FlatFileSource e OLEDBSource. L'analizzatore gestisce il nome completo come un singolo nome di colonna.  
  
 I nomi dei componenti di origine e di colonna vengono qualificati separatamente. Negli esempi seguenti viene illustrato il corretto utilizzo delle parentesi quadre nella notazione con punto:  
  
-   Il nome del componente di origine include spazi.  
  
    ```  
    [MySo urce].Age  
    ```  
  
-   Il primo carattere del nome della colonna non è valido.  
  
    ```  
    MySource.[#Age]  
    ```  
  
-   Il nome del componente di origine e quello della colonna contengono caratteri non validi.  
  
    ```  
    [MySource?].[#Age]  
    ```  
  
> [!IMPORTANT]  
>  Se nella notazione con punto entrambi gli elementi sono racchiusi da una coppia di parentesi quadre, l'analizzatore di espressioni interpreta la coppia come un identificatore unico, non come combinazione origine-colonna.  
  
## <a name="variables-in-expressions"></a>Variabili nelle espressioni  
 Le variabili, quando viene fatto riferimento nelle espressioni, è necessario includere il \@ prefisso. Ad esempio, il **contatore** tramite cui viene fatto riferimento variabile \@contatore. Il \@ carattere non è parte del nome della variabile, identifica solo la variabile per l'analizzatore di espressioni. Se si compila espressioni in base a usando la finestra di dialogo e nelle caselle [!INCLUDE[ssIS](../../includes/ssis-md.md)] progettazione sono disponibili, il \@ carattere viene aggiunto automaticamente al nome della variabile. Non è consentito includere spazi tra il \@ carattere e il nome della variabile.  
  
 Per i nomi delle variabili valgono le stesse regole applicate agli altri identificatori regolari:  
  
-   Il primo carattere del nome deve essere una lettera, come definito dallo standard Unicode 2.0, o un carattere di sottolineatura (_).  
  
-   I caratteri successivi possono includere lettere o numeri, come definito dallo Standard Unicode 2.0, il carattere di sottolineatura (_), \@, $ e & caratteri.  
  
 I nomi di variabile contenenti caratteri diversi da quelli elencati devono essere racchiusi tra parentesi quadre. È ad esempio necessario racchiudere tra parentesi quadre i nomi di variabili che includono spazi. Segue la parentesi di apertura di \@ carattere. Ad esempio, il **My Name** variabile viene fatto riferimento come \@[My Name]. Non è consentito includere spazi tra il nome della variabile e le parentesi quadre.  
  
> [!NOTE]  
>  I nomi delle variabili di sistema e delle variabili definite dall'utente devono essere specificati rispettando la distinzione tra maiuscole e minuscole.  
  
## <a name="unique-variable-names"></a>Nomi di variabile univoci  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sono supportare le variabili personalizzate ed è disponibile un set di variabili di sistema. Per impostazione predefinita, le variabili personalizzate appartengono allo spazio dei nomi **User** mentre le variabili di sistema appartengono allo spazio dei nomi **System** . È possibile creare ulteriori spazi dei nomi per le variabili personalizzate e aggiornare i nomi degli spazi dei nomi in base alle esigenze della propria applicazione. Il generatore di espressioni elenca le variabili comprese nell'ambito corrente, a qualsiasi spazio dei nomi appartengano.  
  
 Tutte le variabili appartengono a uno spazio dei nomi e hanno un ambito, che può essere costituito da un pacchetto oppure da un contenitore o da un'attività in un pacchetto. Il generatore di espressioni di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] elenca solo le variabili comprese nell'ambito corrente. Per altre informazioni, vedere [Variabili di Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md) e [Usare variabili nei pacchetti](../use-variables-in-packages.md).  
  
 L'analizzatore di espressioni può valutare correttamente un'espressione solo se le variabili utilizzate hanno nomi univoci. Se un pacchetto utilizza più variabili con lo stesso nome, i relativi spazi dei nomi devono essere diversi. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include un operatore di risoluzione degli spazi dei nomi composto da un doppio segno di due punti (::), per qualificare una variabile con il relativo spazio dei nomi. Nell'espressione seguente, ad esempio, vengono usate due variabili con il nome **Count**, una appartenente allo spazio dei nomi **User** e l'altra allo spazio dei nomi **MyNamespace** .  
  
```  
@[User::Count] > @[MyNamespace::Count]  
```  
  
> [!IMPORTANT]  
>  Per consentire all'analizzatore di espressioni di riconoscere tali variabili, è necessario racchiudere tra parentesi quadre la combinazione costituita dallo spazio dei nomi e dal nome qualificato della variabile.  
  
 Se il valore di **conteggio** nel **utente** dello spazio dei nomi è 10, mentre il valore di **Count** nel **MyNamespace** è 2, l'espressione restituisce `true` perché l'analizzatore di espressioni le riconosce come due variabili diverse.  
  
 Se i nomi delle variabili non sono univoci, non verrà generato alcun errore, ma l'analizzatore di espressioni valuterà l'espressione utilizzando una sola istanza della variabile e restituirà un risultato non corretto. Ad esempio, l'espressione seguente ha scopo di confrontare i valori (10 e 2) di due **conteggio** variabili, ma l'espressione viene valutata `false` perché l'analizzatore di espressioni usa la stessa istanza di  **Conteggio** variabile due volte.  
  
```  
@Count > @Count  
```  
  
## <a name="related-content"></a>Contenuto correlato  
 Articolo tecnico relativo al [foglio d'aiuto per le espressioni SSIS](http://go.microsoft.com/fwlink/?LinkId=217683)sul sito Web pragmaticworks.com  
  
  
