---
title: DLL di conversione | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- translation DLLs [ODBC]
ms.assetid: 38975059-b346-410f-bb27-326f3f7bbf39
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ab283e0086afadd5fc5bbd9e465241ca997890e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915962"
---
# <a name="translation-dlls"></a>DLL di conversione
L'applicazione e l'origine dei dati spesso memorizzano i dati in set di caratteri diversi. ODBC fornisce un meccanismo generico che consente al driver di convertire i dati da un set di caratteri da un altro. È costituito da una DLL che implementa le funzioni di conversione **SQLDriverToDataSource** e **SQLDataSourceToDriver**, che vengono chiamati dal driver per convertire tutti i dati che si propagano tra l'origine dati e il driver. Questa DLL può essere scritto dallo sviluppatore dell'applicazione, lo sviluppatore di driver, o di terze parti.  
  
 DLL di conversione per una determinata origine dati è possibile specificare le informazioni di sistema per l'origine dati; Per ulteriori informazioni, vedere [sottochiavi specifica di origine dati](../../../odbc/reference/install/data-source-specification-subkeys.md). Può anche essere impostata in fase di esecuzione con gli attributi di connessione SQL_ATTR_TRANSLATE_DLL e SQL_ATTR_TRANSLATE_OPTION.  
  
 L'opzione di conversione è un valore che può essere interpretato solo da una determinata DLL di conversione. Ad esempio, se la conversione DLL conversione tra tabelle codici diverse, l'opzione possibile assegnare i numeri delle tabelle codici utilizzate dall'applicazione e l'origine dati. Non è necessario per la DLL di conversione per utilizzare l'opzione di conversione.  
  
 Dopo la conversione che è stata specificata DLL, il driver viene caricato e viene chiamato per convertire tutti i dati che si propagano tra l'applicazione e l'origine dati. Questo include tutti i parametri di tipo carattere inviati all'origine dati e le istruzioni SQL e tutti i risultati di carattere, i metadati di carattere, ad esempio nomi di colonna e i messaggi di errore recuperati dall'origine dati. Dati di connessione non viene tradotta, in quanto la traduzione DLL viene caricata solo dopo l'applicazione ha stabilito la connessione all'origine dati.
