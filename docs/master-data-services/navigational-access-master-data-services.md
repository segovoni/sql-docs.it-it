---
title: Accesso per la navigazione (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
caps.latest.revision: 5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 3cc3bdfd0d30a7aac4432f02aa98a12a5c0e098c
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35405443"
---
# <a name="navigational-access-master-data-services"></a>Accesso per la navigazione (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  L'accesso per la navigazione si applica alla sicurezza dell'oggetto modello, assegnata nella scheda **Modelli**.  
  
 L'accesso per la navigazione è l'accesso che si ottiene ai livelli superiori a quello per cui è stata assegnata la sicurezza.  
  
 In questo esempio le autorizzazioni vengono assegnate a un'entità, pertanto l'accesso per la navigazione viene concesso a livello di modello.  
  
 ![mds_conc_inheritance_model](../master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
 **Entità**  
  
 Quando si assegna un'autorizzazione a un'entità, ai relativi membri foglia o membri consolidati, l'accesso per la navigazione consente di leggere o aggiornare il nome e il codice di tutti i membri. È inoltre possibile leggere il nome del modello.  
  
 **Attributi**  
  
 Quando si assegna un'autorizzazione a un attributo, l'accesso per la navigazione consente di leggere o aggiornare il nome e il codice di tutti i membri nell'entità. È inoltre possibile leggere il nome del modello.  
  
 **Raccolte**  
  
 Quando si assegnano autorizzazioni alle raccolte, è possibile leggere o aggiornare nome, codice, descrizione e ID proprietario. È inoltre possibile leggere il nome del modello.  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità di determinazione delle autorizzazioni &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
