---
title: Conversione di schemi XDR a schemi XSD equivalenti (SQLXML 4.0) con annotazioni | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- annotated XDR schemas, converting schemas
- annotated XSD schemas, converting schemas
- XDR to XSD Converter tool [SQLXML]
- XDR schemas [SQLXML], converting
- converting annotated schemas
- mapping schema [SQLXML], conversions
- XSD schemas [SQLXML], converting schemas
ms.assetid: 151c94a8-66d3-4c46-a5ff-a22df456940a
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a841cf9e5bcfe3c1de5c199fa29984c709631598
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38047279"
---
# <a name="converting-annotated-xdr-schemas-to-equivalent-xsd-schemas-sqlxml-40"></a>Conversione di schemi XDR con annotazioni in schemi XSD equivalenti (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Il linguaggio XSD (XML Schema Definition) è il successore del linguaggio XDR (XML-Data Reduced). Con l'introduzione del supporto XSD in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, si presuppone che i nuovi schemi con annotazioni vengano creati utilizzando XSD. SQLXML 4.0 include un convertitore da XDR a XSD progettato per consentire la conversione di schemi XDR con annotazioni in schemi XSD equivalenti.  
  
> [!IMPORTANT]  
>  Dal momento che non si tratta di un convertitore da XDR a XSD universale, è possibile utilizzarlo solo quando si desidera convertire in XSD schemi XDR con annotazioni per l'utilizzo con SQLXML 4.0. Quando vengono utilizzati in altri ambienti, gli schemi XSD convertiti potrebbero non comportarsi come gli schemi XDR originali.  
  
 Se il file XDR di input specifica la codifica all'interno della dichiarazione XML, questa diventa la codifica del file XSD di output generato.  
  
 Il convertitore (Cvtschema.exe) viene installato nella cartella Programmi\SQLXML 4.0\bin ed eseguito nel prompt dei comandi.  
  
 La sintassi generale è la seguente:  
  
```  
cvtschema XDRFileName, [-y], [-w] [-?]  
```  
  
 Dove:  
  
 XDRFileName  
 È il nome del file XDR  da convertire in XSD. Lo strumento legge il file XDR di input e crea un file di output XSD nella directory di lavoro corrente. Se l'estensione del file di input è .xdr o .xml, il file XSD di output viene creato con lo stesso nome ma con estensione .xsd. Se l'estensione del nome file di input è diverso da XML o. XDR (o se l'estensione non è presente), il file di output viene creato con lo stesso nome e l'estensione XSD viene aggiunto al nome del file di input. Se ad esempio il nome del file XDR di input è SampleFile.abc, il file XSD risultante viene salvato come SampleFile.abc.xsd.  
  
 -y  
 (Facoltativo) Sovrascrive il file XSD esistente con il file XSD generato dal convertitore. Se non viene specificato il flag, il convertitore richiede di specificare se si desidera sovrascrivere il file XSD esistente e offre l'opportunità di modificare il nome del file di output.  
  
 -w  
 (Facoltativo) Restituisce avvisi non irreversibili generati nel processo di conversione dallo strumento. Per impostazione predefinita, lo strumento visualizza messaggi solo per gli errori irreversibili.  
  
 -?  
 Restituisce un elenco di opzioni che è possibile specificare con **cvtschema**, e la relativa spiegazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping dei tipi di dati XSD ai tipi di dati XPath &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/mapping-xsd-data-types-to-xpath-data-types-sqlxml-4-0.md)   
 [Annotazioni XSD &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/xsd-annotations-sqlxml-4-0.md)  
  
  
