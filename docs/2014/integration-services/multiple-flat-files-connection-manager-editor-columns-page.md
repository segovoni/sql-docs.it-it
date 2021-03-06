---
title: Editor gestione connessione (pagina colonne) più file Flat | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multifile.columns.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: ad0cb668-0df2-4d4e-9a20-d20692a0b67a
caps.latest.revision: 29
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 23d3e2a6bbee792686267930d329f85753320031
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37258977"
---
# <a name="multiple-flat-files-connection-manager-editor-columns-page"></a>Editor gestione connessione per più file flat (pagina Colonne)
  Utilizzare il nodo **Colonne** della finestra di dialogo **Editor gestione connessione per più file flat** per specificare informazioni sulla riga e la colonna e visualizzare l'anteprima del primo file selezionato.  
  
 Per ulteriori informazioni sulla gestione connessione per più file flat, vedere [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).  
  
## <a name="static-options"></a>Opzioni statiche  
 **Nome gestione connessione**  
 Consente di specificare un nome univoco per la connessione per più file flat nel flusso di lavoro. Il nome specificato verrà visualizzato in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Descrizione**  
 Consente di aggiungere una descrizione per la connessione. È consigliabile includere nella descrizione informazioni sugli scopi della connessione, in modo da ottenere pacchetti autodocumentati e semplificarne quindi la gestione.  
  
## <a name="flat-file-format-dynamic-options"></a>Opzioni dinamiche relative al formato file flat  
  
### <a name="format--delimited"></a>Formato = Delimitato  
 **Delimitatore di riga**  
 Consente di selezionare il delimitatore di riga desiderato nell'elenco dei delimitatori disponibili oppure di immettere il testo per il delimitatore.  
  
|valore|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Le righe sono delimitate dalla combinazione di caratteri ritorno a capo/avanzamento riga.|  
|**{CR}**|Le righe sono delimitate da un ritorno a capo.|  
|**{LF}**|Le righe sono delimitate da un avanzamento riga.|  
|**Punto e virgola {;}**|Le righe sono delimitate da un punto e virgola.|  
|**Due punti {:}**|Le righe sono delimitate da un carattere due punti.|  
|**Virgola {,}**|Le righe sono delimitate da una virgola.|  
|**Tabulazione {t}**|Le righe sono delimitate da un carattere di tabulazione.|  
|**Barra verticale {&#124;}**|Le righe sono delimitate da una barra verticale.|  
  
 **Delimitatore di colonna**  
 Consente di selezionare il delimitatore di colonna desiderato nell'elenco dei delimitatori disponibili oppure di immettere il testo per il delimitatore.  
  
|valore|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Le colonne sono delimitate dalla combinazione di caratteri ritorno a capo/avanzamento riga.|  
|**{CR}**|Le colonne sono delimitate da un ritorno a capo.|  
|**{LF}**|Le colonne sono delimitate da un avanzamento riga.|  
|**Punto e virgola {;}**|Le colonne sono delimitate da un punto e virgola.|  
|**Due punti {:}**|Le colonne sono delimitate da due punti.|  
|**Virgola {,}**|Le colonne sono delimitate da una virgola.|  
|**Tabulazione {t}**|Le colonne sono delimitate da una tabulazione.|  
|**Barra verticale {&#124;}**|Le colonne sono delimitate da una barra verticale.|  
  
 **Reimposta colonne**  
 Il pulsante **Reimposta colonne**consente di rimuovere tutte le colonne tranne quelle originali.  
  
### <a name="format--fixed-width"></a>Formato = A larghezza fissa  
 **Carattere**  
 Consente di selezionare il tipo di carattere per la visualizzazione in anteprima dei dati.  
  
 **Colonne dati di origine**  
 Per modificare la larghezza della riga, trascinare l'indicatore di riga verticale, mentre per modificare la larghezza delle colonne, fare clic sul righello nella parte superiore della finestra di anteprima.  
  
 **Larghezza riga**  
 Consente di specificare la larghezza della riga prima dell'aggiunta dei delimitatori per le singole colonne. In alternativa, trascinare la linea verticale nella finestra di anteprima per contrassegnare la fine della riga. Il valore relativo alla larghezza della riga viene aggiornato automaticamente.  
  
 **Reimposta colonne**  
 Il pulsante **Reimposta colonne**consente di rimuovere tutte le colonne tranne quelle originali.  
  
### <a name="format--ragged-right"></a>Formato = Non allineato a destra  
  
> [!NOTE]  
>  Nei file con formato non allineato a destra, ogni colonna ha una larghezza fissa, ad eccezione dell'ultima colonna. L'ultima colonna è delimitata dal delimitatore di riga.  
  
 **Carattere**  
 Consente di selezionare il tipo di carattere per la visualizzazione in anteprima dei dati.  
  
 **Colonne dati di origine**  
 Per modificare la larghezza della riga, trascinare l'indicatore di riga verticale, mentre per modificare la larghezza delle colonne, fare clic sul righello nella parte superiore della finestra di anteprima.  
  
 **Delimitatore di riga**  
 Consente di selezionare il delimitatore di riga desiderato nell'elenco dei delimitatori disponibili oppure di immettere il testo per il delimitatore.  
  
|valore|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Le righe sono delimitate dalla combinazione di caratteri ritorno a capo/avanzamento riga.|  
|**{CR}**|Le righe sono delimitate da un ritorno a capo.|  
|**{LF}**|Le righe sono delimitate da un avanzamento riga.|  
|**Punto e virgola {;}**|Le righe sono delimitate da un punto e virgola.|  
|**Due punti {:}**|Le righe sono delimitate da un carattere due punti.|  
|**Virgola {,}**|Le righe sono delimitate da una virgola.|  
|**Tabulazione {t}**|Le righe sono delimitate da un carattere di tabulazione.|  
|**Barra verticale {&#124;}**|Le righe sono delimitate da una barra verticale.|  
  
 **Reimposta colonne**  
 Il pulsante **Reimposta colonne**consente di rimuovere tutte le colonne tranne quelle originali.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor gestione connessione file Flat più &#40;pagina Generale&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor gestione connessione file Flat più &#40;pagina avanzate&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md)   
 [Editor gestione connessione file Flat più &#40;pagina di anteprima&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)  
  
  
