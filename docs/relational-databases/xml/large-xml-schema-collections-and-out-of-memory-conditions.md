---
title: Raccolte di XML Schema di grandi dimensioni e condizioni di memoria insufficiente | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- out-of-memory conditions
- XML schema collections [SQL Server], large
ms.assetid: 29b9d839-aaaf-48fb-be17-840c751f36f1
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8c0fca0c99b79f84abf5f107ce7fc603206b2219
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33013748"
---
# <a name="large-xml-schema-collections-and-out-of-memory-conditions"></a>Raccolte di XML Schema di grandi dimensioni e condizioni di memoria insufficiente
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Durante una chiamata alla funzione incorporata XML_SCHEMA_NAMESPACE() in una raccolta XML Schema di grandi dimensioni o durante il tentativo di eliminare queste ultime, potrebbe verificarsi una condizione di memoria insufficiente. Per risolvere questo problema, è possibile utilizzare le soluzioni seguenti:  
  
-   Quando il carico di lavoro del sistema è ridotto, è consigliabile utilizzare il comando DROP_XML_SCHEMA_COLLECTION. Se tale tentativo ha esito negativo, configurare il database in modalità utente singolo mediante l'istruzione ALTER DATABASE e provare ad eseguire di nuovo il comando DROP XML SCHEMA COLLECTION. Se la raccolta XML Schema è contenuta nel database **master**, **model**o **tempdb**, per attivare la modalità utente singolo è necessario riavviare il server.  
  
-   Quando si chiama la funzione XML_SCHEMA_NAMESPACE, è possibile provare a recuperare un singolo spazio dei nomi XML Schema ; provare a eseguire la chiamata quando diminuisce il carico di lavoro del sistema oppure provare ad eseguirla in modalità utente singolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Requisiti e limitazioni per l'utilizzo di raccolte di XML Schema nel server](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
