---
title: Tabella di gestione temporanea dei membri foglia (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2014
helpviewer_keywords:
- members staging table [Master Data Services]
- database [Master Data Services], members staging table
ms.assetid: a8c953da-ec20-47dc-8656-ed5f0dfed89b
caps.latest.revision: 15
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 41c59703917460b06b3457cd013309f13e4b1288
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37184828"
---
# <a name="leaf-member-staging-table-master-data-services"></a>Tabella di gestione temporanea dei membri foglia (Master Data Services)
  Utilizzare la tabella di gestione temporanea dei membri foglia (stg.name_Leaf) nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] per creare, aggiornare, disattivare ed eliminare i membri foglia. Inoltre, è possibile utilizzarla per aggiornare i valori degli attributi per i membri foglia.  
  
##  <a name="TableColumns"></a> Colonne della tabella  
 Nella seguente tabella viene illustrato il motivo per cui viene utilizzato ogni campo della tabella di staging Foglia.  
  
|Nome colonna|Description|  
|-----------------|-----------------|  
|**ID**|Un identificatore assegnato automaticamente. Non immettere un valore in questo campo. Se il batch non è stato elaborato, questo campo è vuoto.|  
|**ImportType**<br /><br /> Obbligatorio|Quanto segue **ID** valori determinano azioni da intraprendere quando dati di staging corrisponda ai dati già esistente nel [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database:<br /><br /> **0**: Crea nuovi membri. Sostituire i dati MDS esistenti con i dati in gestione temporanea, ma solo se tali dati non sono NULL. I valori NULL vengono ignorati. Per impostare un valore dell'attributo della stringa su NULL, scegliere **~NULL~**. Per impostare un valore dell'attributo del numero su NULL, scegliere **-98765432101234567890**. Per impostare un valore dell'attributo datetime su NULL, scegliere **5555-11-22T12:34:56**.<br /><br /> **1**: Crea solo i nuovi membri. Qualsiasi aggiornamento ai dati MDS esistenti avrà esito negativo.<br /><br /> **2**: Crea nuovi membri. Sostituire i dati MDS esistenti con i dati in gestione temporanea. Se si importano valori NULL, i valori MDS esistenti verranno sovrascritti.<br /><br /> **3**: Disattiva il membro, in base al valore di Code. Tutti gli attributi, le appartenenze a gerarchie e raccolte e le transazioni vengono gestiti, ma non sono più disponibili nell'interfaccia utente. Se il membro viene utilizzato come valore di attributo basato su dominio di un altro membro, la disattivazione ha esito negativo. Vedere **ImportType5** per un'alternativa.<br /><br /> **4**: Elimina definitivamente il membro, in base al valore di Code. Tutti gli attributi, le appartenenze a gerarchie e raccolte e le transazioni vengono eliminati in modo definitivo. Se il membro viene utilizzato come valore di attributo basato su dominio di un altro membro, l'eliminazione ha esito negativo. Vedere **ImportType6** per un'alternativa.<br /><br /> **5**: Disattiva il membro, in base al valore di **Code** . Tutti gli attributi, le appartenenze a gerarchie e raccolte e le transazioni vengono gestiti, ma non sono più disponibili nell'interfaccia utente. Se il membro viene utilizzato come valore di attributo basato su dominio di altri membri, i valori correlati verranno impostati su NULL. ImportType 5 è solo per i membri foglia.<br /><br /> **6**: Elimina definitivamente il membro, in base al valore di **Code** . Tutti gli attributi, le appartenenze a gerarchie e raccolte e le transazioni vengono eliminati in modo definitivo. Se il membro viene utilizzato come valore di attributo basato su dominio di altri membri, i valori correlati verranno impostati su NULL. ImportType 6 è solo per i membri foglia.|  
|**ImportStatus_ID**<br /><br /> Obbligatorio|Lo stato del processo di importazione. I valori possibili sono:<br /><br /> **0**, specificato per indicare che il record è pronto per la gestione temporanea.<br /><br /> **1**, assegnato automaticamente indica che il processo di gestione temporanea del record ha avuto esito positivo.<br /><br /> **2**, assegnato automaticamente e indica che il processo di gestione temporanea del record non è riuscito.|  
|**Batch_ID**<br /><br /> Richiesto solo dal servizio Web|Un identificatore assegnato automaticamente che raggruppa i record per la gestione temporanea. A tutti i membri nel batch viene assegnato questo identificatore, visualizzato nella colonna [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ID **dell'interfaccia utente di** .<br /><br /> Se il batch non è stato elaborato, questo campo è vuoto.|  
|**BatchTag**<br /><br /> Richiesto, salvo che dal servizio Web|Un nome univoco per il batch, composto da un massimo di 50 caratteri.|  
|**ErrorCode**|Visualizza un codice di errore. Per tutti i record con **ImportStatus_ID** di **2**, vedere [Staging Process Errors &#40;Master Data Services&#41;](staging-process-errors-master-data-services.md).|  
|**Code**<br /><br /> Richiesto, tranne quando i codici vengono generati automaticamente per **ImportType1** o **2**. Per altre informazioni, vedere [Creazione di codice automatica &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md)|Un codice univoco per il membro.|  
|**Nome**<br /><br /> Facoltativo|Nome per il membro.|  
|**NewCode**|Utilizzare solo se si sta modificando il codice membro.|  
|\<Nome attributo >|Esiste una colonna per ogni attributo dell'entità. Utilizzarlo con **ImportType** uguale a **0** o a **2**. Per gli attributi in formato libero specificare il nuovo testo o valore stringa per l'attributo. Per gli attributi basati su dominio specificare il codice del membro che sarà utilizzato come attributo. Per gli attributi di collegamento, l'URL deve iniziare con **http://**.<br /><br /> Nota: non è possibile usare la gestione temporanea per gli attributi di file.|  
  
##  <a name="feedback"></a> È stato in questo articolo utile? Commenti e suggerimenti  
 Quali informazioni si stanno cercando? La ricerca ha restituito i risultati desiderati? Microsoft incoraggia gli utenti a inviare i propri commenti per migliorare i contenuti Inviare eventuali commenti all'indirizzo [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Leaf%20Member%20Staging%20Table%20page)  
  
## <a name="see-also"></a>Vedere anche  
 [Caricare o aggiornare membri in Master Data Services tramite il processo di gestione temporanea](/sql/2014/master-data-services/add-update-and-delete-data-master-data-services)   
 [Importazione di dati &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [Visualizzare gli errori che si verificano durante il processo di gestione temporanea &#40;Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md)   
 [Errori del processo di gestione temporanea &#40;Master Data Services&#41;](staging-process-errors-master-data-services.md)  
  
  
