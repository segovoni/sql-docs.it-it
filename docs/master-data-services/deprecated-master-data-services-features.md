---
title: Funzionalità deprecate di Master Data Services | Microsoft Docs
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
ms.assetid: d8506bda-66dd-45a4-bfc9-3a10fa665acc
caps.latest.revision: 18
author: leolimsft
ms.author: lle
manager: erikre
ms.openlocfilehash: edc5d786ebfd5093c1caf284122345cfb344f07e
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35401163"
---
# <a name="deprecated-master-data-services-features"></a>Funzionalità deprecate di Master Data Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In questo argomento verranno descritte le funzionalità deprecate di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ancora disponibili in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Tali funzionalità verranno rimosse a partire da una delle prossime versioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. È consigliabile non usare le funzionalità deprecate nelle nuove applicazioni.  
  
## <a name="explicit-hierarchies-collections-and-related-components"></a>Gerarchie esplicite, raccolte e componenti correlati  
 Le gerarchie esplicite, le raccolte e i componenti correlati sono deprecati. I membri che prima erano modellati come tipi di membro consolidati (padre di gerarchia esplicita) e tipi di membro raccolta verranno modellati come membri foglia nelle gerarchie derivate. Le nuove funzionalità seguenti abilitano l'uso delle gerarchie derivate al posto delle gerarchie esplicite.  
  
-   Le gerarchie derivate ricorsive ora possono essere usate per assegnare le autorizzazioni di sicurezza per i membri.  
  
     Una gerarchia esplicita è analoga a una gerarchia derivata ricorsiva con un unico livello non ricorsivo sotto il livello ricorsivo. Una gerarchia derivata ricorsiva può essere complessa includendo i livelli al di sotto e/o al di sopra di un livello ricorsivo.  
  
-   In Visualizzatore la pagina della gerarchia derivata ora mostra i membri non assegnati (inutilizzati) per ogni livello della gerarchia. I nodi inutilizzati vengono raggruppati per livello di gerarchia. I membri possono essere spostati tra i nodi Inutilizzato e Radice, mediante trascinamento o con operazioni di taglia e incolla.  
  
     In Amministrazione sistema i nodi inutilizzati sono visibili nel riquadro **Anteprima** . In Sicurezza i nodi inutilizzati sono visibili nel riquadro **Autorizzazioni membri gerarchia** . A tutti i membri nel nodo **Radice** o **Inutilizzato** è possibile assegnare un'autorizzazione. È possibile assegnare autorizzazioni anche agli pseudo membri **Radice**, **Inutilizzato** e **Inutilizzato**.  
  
-   La stored procedure mdm.udpConvertCollectionAndConsolidatedMembersToLeaf converte le gerarchie esplicite in gerarchie derivate ricorsive e converte i membri consolidati e della raccolta in membri foglia.  
  
     Le gerarchie esplicite e i membri di tipo consolidato e raccolta sono ancora supportati, quindi l'esecuzione della stored procedure è facoltativa. Se però si usano questi elementi è consigliabile eseguire la stored procedure perché sono deprecati.  
  
 Per informazioni sulle gerarchie esplicite, sulle raccolte e sui membri consolidati, vedere gli argomenti seguenti.  
  
-   [Gerarchie esplicite &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [Raccolte &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)  
  
-   [Membri &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)  
  
## <a name="attribute-entity-transaction-log-type"></a>Tipo di log delle transazioni di entità attributo  
Il tipo di log delle transazioni di entità "Attributo" è deprecato. Eseguire la migrazione al tipo di log delle transazioni di entità "Membro". Per informazioni sui tipi di log delle transazioni di entità, vedere l'argomento seguente:
* [Modificare il tipo di log delle transazioni dell'entità (Master Data Services)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)
* [Cronologia delle revisioni del membro](../master-data-services/member-revision-history-master-data-services.md)
  
## <a name="external-resources"></a>Risorse esterne  
 Post di blog [Deprecated: Explicit Hierarchies and Collections](http://go.microsoft.com/fwlink/p/?LinkId=615373)(Deprecato: gerarchie esplicite e raccolte) su msdn.com.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità di Master Data Services non più supportate](../master-data-services/discontinued-master-data-services-features.md)  
  
  
