---
title: Compilazione di un modello (componente aggiuntivo MDS per Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8ae26ec3-c5d5-4c4f-a810-2951a7454439
caps.latest.revision: 4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: cd4544aefe0f8a5b474b073ef4279f50c4d8a434
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320291"
---
# <a name="building-a-model-mds-add-in-for-excel"></a>Compilazione di un modello (componente aggiuntivo MDS per Excel)
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]gli amministratori possono eseguire un subset delle funzioni amministrative disponibili nell'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
 Le attività di compilazione dei modelli che gli amministratori possono eseguire in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] sono le seguenti:  
  
-   Creare entità. Per altre informazioni sulle entità, vedere [Entities &#40;Master Data Services&#41;](../entities-master-data-services.md).  
  
-   Creare attributi di tutti i tipi, inclusi attributi basati su dominio. Per altre informazioni sugli attributi, vedere [Attributes &#40;Master Data Services&#41;](../attributes-master-data-services.md) e [Domain-Based Attributes &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md).  
  
 Un amministratore deve creare il modello utilizzando il servizio Web o l'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . È quindi possibile utilizzare [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] per creare entità e attributi all'interno del modello. Per altre informazioni sugli oggetti modello, vedere [Models &#40;Master Data Services&#41;](../models-master-data-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 La maggior parte delle attività amministrative deve ancora essere eseguita nell'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] oppure tramite il servizio Web. Nella tabella seguente sono illustrati gli strumenti che gli amministratori possono utilizzare per completare le attività in MDS.  
  
|Descrizione dell'attività|Strumento|Argomento|  
|----------------------|----------|-----------|  
|Creare modelli.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] applicazione Web o servizio Web|[Creare un modello &#40;Master Data Services&#41;](../create-a-model-master-data-services.md)|  
|Creare un'entità.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] (applicazione Web), servizio Web o [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[Creare un'entità &#40;componente aggiuntivo MDS per Excel&#41;](create-an-entity-mds-add-in-for-excel.md)|  
|Creare un attributo basato su dominio.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] (applicazione Web), servizio Web o [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[Creare un attributo basato su dominio &#40;componente aggiuntivo MDS per Excel&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|Creare gruppi di attributi.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] applicazione Web o servizio Web|[Creare un gruppo di attributi &#40;Master Data Services&#41;](../create-an-attribute-group-master-data-services.md)|  
|Creare regole business.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] applicazione Web o servizio Web|[Creare e pubblicare una regola Business &#40;Master Data Services&#41;](../create-and-publish-a-business-rule-master-data-services.md)|  
|Creare viste sottoscrizioni.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] applicazione Web o servizio Web|[Creare una vista sottoscrizioni &#40;Master Data Services&#41;](../create-a-subscription-view-to-export-data-master-data-services.md)|  
|Creare gerarchie.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] applicazione Web o servizio Web|[Creare una gerarchia derivata &#40;Master Data Services&#41;](../create-a-derived-hierarchy-master-data-services.md)<br /><br /> [Creare una gerarchia esplicita &#40;Master Data Services&#41;](../create-an-explicit-hierarchy-master-data-services.md)|  
|Creare raccolte.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] applicazione Web o servizio Web|[Creare una raccolta &#40;Master Data Services&#41;](../create-a-collection-master-data-services.md)|  
|Creare versioni dei dati.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] applicazione Web o servizio Web|[Bloccare una versione &#40;Master Data Services&#41;](../lock-a-version-master-data-services.md)|  
|Distribuire modelli.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] applicazione Web, servizio Web o strumento MDSModelDeploy.|[Creare un pacchetto di distribuzione di modelli tramite MDSModelDeploy](../create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Modelli &#40;Master Data Services&#41;](../models-master-data-services.md)  
  
-   [Entità &#40;Master Data Services&#41;](../entities-master-data-services.md)  
  
-   [Gli attributi &#40;Master Data Services&#41;](../attributes-master-data-services.md)  
  
-   [Attributi basati su dominio &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md)  
  
-   [Gruppi di attributi &#40;Master Data Services&#41;](../attribute-groups-master-data-services.md)  
  
-   [Le regole di business &#40;Master Data Services&#41;](../business-rules-master-data-services.md)  
  
-   [Esportazione di dati &#40;Master Data Services&#41;](../overview-exporting-data-master-data-services.md)  
  
-   [Gerarchie di &#40;Master Data Services&#41;](../hierarchies-master-data-services.md)  
  
-   [Le raccolte &#40;Master Data Services&#41;](../collections-master-data-services.md)  
  
-   [Le versioni &#40;Master Data Services&#41;](../versions-master-data-services.md)  
  
-   [Sicurezza &#40;Master Data Services&#41;](../security-master-data-services.md)  
  
-   [Distribuzione di modelli &#40;Master Data Services&#41;](../deploying-models-master-data-services.md)  
  
  
