---
title: Registrazione degli oggetti Business sul Client per l'utilizzo con DCOM | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 75a21910-607f-463a-ae18-a17130dafb7e
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2be8421c2d1b09887d50a49c0fdb71d2a5d92886
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274220"
---
# <a name="registering-business-objects-on-the-client-for-use-with-dcom"></a>Registrazione degli oggetti Business sul Client per l'utilizzo con DCOM
Gli oggetti business personalizzati devono verificare che sul lato client può eseguire il mapping al nome di programma (ProgId) a un identificatore di classe (CLSID) che può essere utilizzato su DCOM. Per questo motivo, il ProgID dell'oggetto DCOM deve essere nel Registro di sistema sul lato client e il mapping all'ID classe dell'oggetto business sul lato server. Per altri protocolli supportati (HTTP, HTTPS e in-process), ciò non è necessario.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Ad esempio, se si espone un oggetto business sul lato server denominato MyBObj con un ID di classe specifici, ad esempio, quale "{00112233-4455-6677-8899-00AABBCCDDEE}", assicurarsi che le voci seguenti vengono aggiunti al Registro di sistema sul lato client:  
  
```  
[HKEY_CLASSES_ROOT]  
\MyBObj\Clsid\(Default) "{00112233-4455-6677-8899-00AABBCCDDEE}"  
```


