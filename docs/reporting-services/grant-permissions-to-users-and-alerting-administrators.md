---
title: Concedere autorizzazioni a utenti e amministratori di avvisi | Microsoft Docs
ms.custom: ''
ms.date: 08/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 166808e1-ada7-48d2-bda8-8f7c017fb3aa
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 136406ea820f89ff52df5921511227af80178054
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33016798"
---
# <a name="grant-permissions-to-users-and-alerting-administrators"></a>Concedere autorizzazione a utenti e amministratori di avvisi

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../includes/ssrs-appliesto-not-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

Per poter creare, modificare, eliminare e visualizzare avvisi dati, è necessario che agli utenti e agli amministratori di avvisi vengano concesse le autorizzazioni di SharePoint. Non esistono autorizzazioni speciali da usare con la funzionalità relativa agli avvisi dati di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . È possibile usare le autorizzazioni predefinite di SharePoint.

> [!NOTE]
> L'integrazione di Reporting Services con SharePoint non è più disponibile nelle versioni successive a SQL Server 2016.

**Information Worker**: le autorizzazioni devono includere le autorizzazioni Creazione avvisi e Visualizzazione elementi di SharePoint. I livelli di autorizzazione predefiniti di SharePoint denominati Progettazione, Collaborazione, Lettura e Solo visualizzazione includono le autorizzazioni di SharePoint relative alla creazione di avvisi e alla visualizzazione di elementi. È inoltre possibile creare un livello di autorizzazione personalizzato con le autorizzazioni necessarie per gli utenti che creano, modificano, eseguono e visualizzano avvisi dati.

**Amministratori di avvisi**: le autorizzazioni devono includere l'autorizzazione di SharePoint relativa alla gestione degli avvisi. Per impostazione predefinita solamente il livello di autorizzazione Controllo completo include questa autorizzazione per i siti creati con il modello di sito del team. Se si utilizzano altri modelli di sito, vengono visualizzati elenchi diversi di gruppi di SharePoint predefiniti. È possibile aggiungere l'autorizzazione Gestione avvisi a uno dei livelli di autorizzazione predefiniti oppure creare un livello di autorizzazione personalizzato con l'autorizzazione necessaria per supportare gli amministratori di avvisi che visualizzano ed eliminano gli avvisi dati.

Per altre informazioni sulle autorizzazioni di SharePoint, vedere la pagina relativa alle [autorizzazioni utente e ai livelli di autorizzazione (SharePoint Server 2010)](http://technet.microsoft.com/library/cc721640.aspx).

## <a name="grant-permissions"></a>Concedi autorizzazioni
  
1.  Accedere al sito di SharePoint in cui si desidera concedere autorizzazioni.  
  
2.  Nella barra degli strumenti, fare clic su **Azioni sito** , quindi su **Autorizzazioni sito**.  
  
     Se questa opzione non viene visualizzata, non si dispone del livello di autorizzazione sufficiente per concedere autorizzazioni ad altri.  
  
3.  Fare clic su **Concedi autorizzazioni**.  
  
4.  In **Utenti/Gruppi**digitare i nomi degli utenti, i nomi dei gruppi e gli indirizzi di posta elettronica a cui si vuole concedere autorizzazioni.  
  
5.  Selezionare l'opzione **Aggiungi utenti a un gruppo di SharePoint** o **Concedi direttamente le autorizzazioni agli utenti** . A seconda del fatto che sia stata selezionata l'opzione **Aggiungi utenti a un gruppo di SharePoint** o **Concedi direttamente le autorizzazioni agli utenti** , effettuare una delle operazioni seguenti:  
  
    -   Se è stata selezionata l'opzione **Aggiungi utenti a un gruppo di SharePoint**, selezionare un livello di autorizzazione nell'elenco a discesa.  
  
    -   Se è stato selezionato **Concedi direttamente le autorizzazioni agli utenti**, selezionare un livello di autorizzazione.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  

## <a name="see-also"></a>Vedere anche

[Impostare autorizzazioni per gli elementi del server di report in un sito di SharePoint &#40;Reporting Services in modalità integrata SharePoint&#41;](../reporting-services/security/set-permissions-for-report-server-items-on-a-sharepoint-site.md)   
[Avvisi dati di Reporting Services](../reporting-services/reporting-services-data-alerts.md)  

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
