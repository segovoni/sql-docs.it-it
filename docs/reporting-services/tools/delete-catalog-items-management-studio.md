---
title: Elimina elementi catalogo (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: tools
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.deleteitems.f1
ms.assetid: b0599e01-6dc3-4484-80d4-022a412e0ebd
caps.latest.revision: 16
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: d3d92d7345862149380565911def8eb3a52454fa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33030028"
---
# <a name="delete-catalog-items-management-studio"></a>Elimina elementi catalogo (Management Studio)
  Questa pagina consente di eliminare pianificazioni condivise e definizioni di ruolo.  
  
 Se si elimina una pianificazione condivisa utilizzata da più report e sottoscrizioni, nel server di report vengono create singole pianificazioni per ogni report e sottoscrizione da cui è stata utilizzata in precedenza la pianificazione condivisa. Ogni nuova pianificazione conterrà la data, l'ora e il criterio di occorrenza specificati nella pianificazione condivisa. Si noti che in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non è disponibile una funzionalità di gestione centrale delle singole pianificazioni. Se si elimina una pianificazione condivisa, è necessario gestire le informazioni sulla pianificazione per ogni singolo elemento. Prima di eliminare una pianificazione condivisa, utilizzare la pagina [Report](../../reporting-services/tools/schedule-properties-reports-page.md) per verificare i report da cui attualmente viene utilizzata la pianificazione.  
  
 Per le definizioni di ruolo, è possibile eliminare solo le definizioni non attivamente utilizzate in un'assegnazione di ruolo. Se si tenta di eliminare un ruolo attualmente in uso, tale ruolo non viene eliminato dal server di report e viene visualizzato un messaggio di errore. Se la pagina contiene una singola definizione di ruolo non attualmente in uso, la definizione viene eliminata quando si fa clic su **OK**. Se la pagina contiene più ruoli, non è possibile selezionare i ruoli da conservare o da rimuovere. Facendo clic su **OK**vengono eliminate tutte le definizioni di ruolo non utilizzate.  
  
 Non è possibile annullare un'operazione di eliminazione. Se si desidera recuperare un elemento eliminato, è necessario ricrearlo o ripristinare una copia di backup del database del server di report.  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Indica il nome dell'elemento che si sta eliminando.  
  
 **Tipo**  
 Visualizza il tipo di elemento che si sta eliminando.  
  
 **Proprietario**  
 Visualizza il nome del proprietario. Nella maggior parte dei casi, si tratta di System.  
  
 **Stato**  
 Visualizza le informazioni sullo stato dell'operazione di eliminazione.  
  
 **Errore**  
 Visualizza un codice se si verifica un errore durante l'eliminazione di un elemento.  
  
## <a name="see-also"></a>Vedere anche  
 [Eliminare un elemento &#40;Management Studio&#41;](../../reporting-services/tools/delete-an-item-management-studio.md)   
 [Guida sensibile al contesto del server di report in Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Creare, modificare ed eliminare pianificazioni](../../reporting-services/subscriptions/create-modify-and-delete-schedules.md)  
  
  
