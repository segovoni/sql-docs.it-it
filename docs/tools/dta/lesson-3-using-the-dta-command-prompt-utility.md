---
title: "Lezione 3: Utilizzo dell'utilità del prompt dei comandi dta | Documenti Microsoft"
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: 30f27f4d-8852-4b12-ba62-57f63e496f1d
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 086a2051f5ef1900c90e55c2de21d365b24905d7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33070168"
---
# <a name="lesson-3-using-the-dta-command-prompt-utility"></a>Lezione 3: Uso dell'utilità del prompt dei comandi dta
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
L'utilità del prompt dei comandi **dta** offre una funzionalità aggiuntiva rispetto allo strumento Ottimizzazione guidata motore di database.  
  
È possibile utilizzare gli strumenti XML preferiti per creare file di input per l'utilità adottando XML Schema di Ottimizzazione guidata motore di database. Questo schema viene installato con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ed è disponibile in: C:\Programmi (x86)\Microsoft SQL Server\110\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd.  
  
XML Schema di Ottimizzazione guidata motore di database è inoltre disponibile online nel [sito Web Microsoft](http://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409).  
  
XML Schema dello strumento Ottimizzazione guidata motore di database garantisce una maggiore flessibilità per l'impostazione delle opzioni di ottimizzazione. Ad esempio, questo schema consente di eseguire analisi di simulazione. Nell'analisi di simulazione è necessario specificare un set di strutture di progettazione fisica ipotetica per il database che si desidera ottimizzare e quindi eseguire l'analisi con lo strumento Ottimizzazione guidata motore di database per verificare se questa progettazione fisica ipotetica sarà in grado di migliorare le prestazioni dell'elaborazione delle query. Questo tipo di analisi offre il vantaggio di valutare la nuova configurazione evitando l'overhead che sarebbe necessario per implementarla. Se la progettazione fisica ipotetica non determina i miglioramenti nelle prestazioni desiderati, è possibile modificarla e analizzarla nuovamente con facilità fino a quando non sarà stata raggiunta la configurazione che produce i risultati richiesti.  
  
Usando l'XML Schema dello strumento Ottimizzazione guidata motore di database e l'utilità del prompt dei comandi **dta** , è anche possibile integrare la funzionalità dello strumento Ottimizzazione guidata motore di database negli script e usarla con altri strumenti per la progettazione del database.  
  
In questa lezione non verrà illustrata la funzionalità relativa agli input in formato XML dello strumento Ottimizzazione guidata motore di database.  
  
Questa lezione offre un'introduzione alla sintassi di base dell'utilità del prompt dei comandi **dta** , all'accesso alla Guida e alle procedure per ottimizzare semplici carichi di lavoro.  
  
Questa lezione contiene l'argomento seguente:  
  
-   Avvio dell'utilità del prompt dei comandi **dta** e ottimizzazione di un carico di lavoro  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Avvio dell'utilità del prompt dei comandi dta e ottimizzazione di un carico di lavoro](../../tools/dta/lesson-3-1-starting-the-dta-command-prompt-utility-and-tuning-a-workload.md)  
  
  
  
