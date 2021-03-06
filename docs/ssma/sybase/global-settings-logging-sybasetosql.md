---
title: Impostazioni globali (registrazione) (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 4cb4da20-3b99-4aae-8c80-329ee23e796e
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d7f0e5bebca49dfb05d0815386fee7d85d71b80b
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34778907"
---
# <a name="global-settings-logging-sybasetosql"></a>Impostazioni globali (registrazione) (SybaseToSQL)
Utilizzare il **impostazioni globali** la finestra di dialogo per specificare le impostazioni di registrazione per SSMA. In genere, è necessario modificare queste impostazioni solo quando si lavora con il supporto tecnico.  
  
Per accedere a questa finestra di dialogo, scegliere il **strumenti** dal menu **impostazioni globali** e quindi fare clic su di **registrazione** nella parte inferiore del riquadro a sinistra.  
  
## <a name="options"></a>Opzioni  
**Livello di messaggi**  
Le opzioni seguenti sono disponibili in **livello messaggi**:  
  
|Opzione|Description|  
|----------|---------------|  
|**[tutte le categorie]**|Utilizzato per impostare il livello di registrazione per tutte le opzioni seguenti.|  
|**Agente di raccolta**|Raccoglie i metadati relativi a schema di origine e lo salva nel progetto.|  
|**Convertitore di tipi**|Converte le strutture di oggetti di database di origine, ad esempio tabelle e stored procedure, nella corrispondente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] strutture.|  
|**Migrazione di dati**|Esegue la migrazione di dati dal database di origine in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|**Formattatore**|Sottocomponente del convertitore che genera script per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] dello schema.|  
|**Interfaccia utente grafica**|Messaggi che vengono visualizzati quando si utilizza lo strumento SSMA.|  
|**Linker**|Risolve gli identificatori SQL e vengono fornite informazioni per altri componenti.|  
|**Altro**|Tutti i messaggi che non sono presenti in qualsiasi altra categoria.|  
|**Parser**|Analizza lo schema di origine.|  
|**Synchronizer**|Carica gli oggetti di database in di origine [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|**TreeConverter**|Converte gli oggetti di metadati di origine in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] metadati.|  
  
Per ogni opzione in **livello messaggi**, configurare uno dei seguenti livelli di registrazione per SSMA:  
  
|||  
|-|-|  
|**Errore irreversibile**|Scrivere il log solo i messaggi di errore irreversibile.|  
|**Errore**|Scrivere nel registro errori e messaggi di errore irreversibile.|  
|**Avviso**|Scrivere i messaggi di errore irreversibile, errore e avviso per il log.|  
|**informazioni**|Scrivere il log informativi, avvisi, errori e i messaggi di errore irreversibile.|  
|**Debug**|Scrivere tutti i messaggi, compresi i messaggi, nel Registro di debug.|  
  
**Percorso File di log**  
Il percorso del file e il nome dei file di log SSMA. Per specificare un nome diverso, fare clic sul percorso corrente e quindi fare clic su Sfoglia (**...** ) pulsante.  
  
**Dimensioni File di log**  
La dimensione massima del file di log in KB. La dimensione minima è di 10 KB. La dimensione predefinita è 10240 KB.  
  
**Numero totale di file di log**  
Quando un log si riempie, SSMA verrà rinominare il file di log e avvia uno nuovo. Con questa impostazione, specificare il numero massimo di file di log da conservare. Il valore minimo è 2.  
  
