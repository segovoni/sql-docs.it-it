---
title: Trasformazione Cache | Microsoft Docs
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
- sql12.dts.designer.cachetrans.f1
helpviewer_keywords:
- Cache transform
ms.assetid: a5683fc8-9c32-4634-819e-e9815627e4f1
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 25e7955750c8b2e3cb04bef74a87fada8c8e5e87
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37329880"
---
# <a name="cache-transform"></a>trasformazione Cache
  La trasformazione Cache genera un set di dati di riferimento per la trasformazione Ricerca mediante la scrittura di dati da un'origine dati connessa nel flusso di dati a una gestione connessione cache. La trasformazione Ricerca esegue ricerche unendo in join i dati contenuti nelle colonne di input da un'origine dati connessa con le colonne nel database di riferimento.  
  
 È possibile utilizzare la gestione connessione Cache quando si desidera configurare la trasformazione Ricerca per l'esecuzione in modalità Full Cache. In questa modalità, il set di dati di riferimento viene caricato nella cache prima dell'esecuzione della trasformazione Ricerca.  
  
 Per istruzioni su come configurare la trasformazione Ricerca in modalità Full Cache utilizzando la gestione connessione cache e una trasformazione Cache, vedere [Implementazione di una trasformazione Ricerca in modalità Full Cache utilizzando la gestione connessione della cache](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).  
  
 Per ulteriori informazioni sulla memorizzazione nella cache del set di dati di riferimento, vedere [Lookup Transformation](lookup-transformation.md).  
  
> [!NOTE]  
>  La Trasformazione cache scrive solo righe univoche nella gestione connessione della cache.  
  
 In un pacchetto singolo, solo una trasformazione Cache può scrivere i dati nella stessa gestione connessione della cache. Se il pacchetto contiene più trasformazioni Cache, la prima ad essere chiamata quando il pacchetto viene eseguito è quella che scrive i dati nella gestione connessione. Le operazioni di scrittura delle trasformazioni Cache successive non vengono eseguite.  
  
 Per ulteriori informazioni, vedere [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) e [Cache Connection Manager Editor](../../cache-connection-manager-editor.md).  
  
## <a name="configuration-of-the-cache-transform"></a>Configurazione della trasformazione Cache  
 È possibile configurare la gestione connessione della cache in modo da salvare i dati in un file di cache (con estensione caw).  
  
 Per configurare la trasformazione Cache, procedere nel modo seguente:  
  
-   Specificare la gestione connessione della cache.  
  
-   Eseguire il mapping delle colonne di input nella trasformazione Cache alle colonne di destinazione nella gestione connessione della cache.  
  
    > [!NOTE]  
    >  È necessario eseguire il mapping di ogni colonna di input a una colonna di destinazione e i tipi di dati di colonna devono corrispondere. In caso contrario, in Progettazione [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] viene visualizzato un messaggio di errore.  
  
     È possibile utilizzare **Editor gestione connessione della cache** per modificare i tipi di dati, i nomi e altre proprietà delle colonne.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] . Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** , vedere [Transformation Custom Properties](transformation-custom-properties.md).  
  
 Per altre informazioni su come impostare le proprietà, vedere [Impostazione delle proprietà di un componente del flusso di dati](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Trasformazioni di Integration Services](integration-services-transformations.md)   
 [Flusso di dati](../data-flow.md)  
  
  
