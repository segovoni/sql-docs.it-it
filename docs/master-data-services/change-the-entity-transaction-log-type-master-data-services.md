---
title: Modificare il tipo di log delle transazioni dell'entità (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 75250b32-3384-43c2-9b5c-1607cc3aa7b3
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 9fbc998de972b49472bb581fc39b7634d3ed3ada
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35400423"
---
# <a name="change-the-entity-transaction-log-type-master-data-services"></a>Modificare il tipo di log delle transazioni dell'entità (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  È possibile modificare il tipo di log delle transazioni di un'entità in attributo, membro o nessuno.  
  
|Tipo di log delle transazioni|Descrizione|  
|--------------------------|-----------------|  
|attribute|I log di modifica dell'entità vengono salvati al livello di attributo.<br /><br /> Il log delle transazioni viene salvato perché è per [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].|  
|Membro|I log di modifica dell'entità vengono salvati al livello di riga.<br /><br /> Tutte le modifiche dell'attributo attivano una nuova revisione di riga.<br /><br /> Quando si usa il tipo di log delle transazioni di riga, l'entità viene archiviata come dimensione a modifica lenta di tipo 4. Le viste sottoscrizione di tipo 2 e di tipo 4 (cronologia) sono supportate. Per altre informazioni, vedere [Formati di vista sottoscrizioni &#40;Master Data Services&#41;](../master-data-services/subscription-view-formats-master-data-services.md)<br /><br /> Fornisce prestazioni migliori.|  
|None|Non vengono salvati log di modifica.<br /><br /> Fornisce le prestazioni migliori.|  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura:  
  
-   È necessaria l'autorizzazione per accedere all'area funzionale Amministrazione sistema. Per altre informazioni, vedere [Autorizzazioni per aree funzionali &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Deve essere presente l'entità. Per altre informazioni, vedere [Creare un'entità &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
 **Per modificare il tipo di log delle transazioni**  
  
1.  In Gestione dati master fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Gestisci modello** selezionare la riga per il modello dell'entità da modificare, quindi fare clic su **Entità**.  
  
3.  Nella pagina **Gestisci entità** selezionare la riga per l'entità da aggiornare, quindi fare clic su **Modifica**.  
  
4.  Scegliere il tipo di log delle transazioni nell'elenco a discesa.  
  
5.  Fare clic su **Salva**.  
  
  
