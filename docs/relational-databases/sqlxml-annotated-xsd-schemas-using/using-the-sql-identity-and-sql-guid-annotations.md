---
title: 'Usando la: Identity delle annotazioni e | Microsoft Docs'
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
- sql:guid
- annotated XSD schemas, IDENTITY-type columns
- annotated XSD schemas, GUID values
- DiffGrams [SQLXML], annotations
- identity annotation
- XSD schemas [SQLXML], GUID values
- GUIDs [SQLXML]
- guid annotation
- sql:identity
- IDENTITY-type column
- XSD schemas [SQLXML], IDENTITY-type columns
- updategrams [SQLXML], GUID values
ms.assetid: 7661dfd0-6573-4692-a8f1-3597adcd33c4
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: da967220c77451d807a79d2e10701fd1f76791d2
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050219"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>Utilizzo delle annotazioni sql:identity e sql:guid
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  È possibile specificare il **: Identity** e **sql:guid** annotazioni in uno schema XSD su qualsiasi nodo che esegue il mapping a una colonna di database di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Mentre il formato dell'updategram supporta il **updg: a-identity** e **updg: GUID** attributi, non presenta il formato DiffGram. Il **updg: a-identity** attributo definisce il comportamento di aggiornamento di una colonna di tipo IDENTITY. Il **updg: GUID** attributo consente di ottenere un valore GUID da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e utilizzarlo nell'updategram. Per altre informazioni ed esempi, vedere [inserimento di dati mediante Updategram XML &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
 Il **: Identity** e **sql:guid** annotazioni estendono questa funzionalità ai DiffGram.  
  
 Per eseguire un DiffGram, è necessario prima convertirlo in updategram. Specificando il **: Identity** e **sql:guid** annotazioni nello schema XSD, vengono di fatto si definisce il comportamento di un updategram. Tutte le annotazioni vengono pertanto descritte nel contesto di un updategram. Le annotazioni possono essere utilizzate sia per i DiffGram che per gli updategram. Per gli updategram è tuttavia già disponibile una modalità di gestione dell'identità e dei valori GUID più potente.  
  
 Il **: Identity** e **sql:guid** le annotazioni possono essere definite in un elemento di contenuto complesso.  
  
## <a name="sqlidentity-annotation"></a>Annotazione sql:identity  
 È possibile specificare il **: Identity** annotazione nello schema XSD su qualsiasi nodo che esegue il mapping a una colonna di database di tipo IDENTITY. Il valore specificato per questa annotazione definisce la modalità di aggiornamento della colonna di tipo IDENTITY (ovvero utilizzando il valore fornito nell'updategram per modificare la colonna o ignorando il valore. Nel secondo caso per la colonna viene utilizzato un valore generato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Il **: Identity** annotazione può essere assegnata a due valori:  
  
 ignore  
 Indica all'updategram di ignorare qualsiasi valore fornito nell'updategram per la colonna in oggetto e di generare il valore Identity in base a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 useValue  
 Indica all'updategram di utilizzare il valore fornito nell'updategram per aggiornare la colonna di tipo IDENTITY. Un updategram non controlla se la colonna è un valore Identity.  
  
 Se l'updategram specifica un valore per la colonna di tipo IDENTITY, il **: Identity = "useValue"** deve essere specificato nello schema.  
  
## <a name="sqlguid-annotation"></a>Annotazione sql:guid  
 Un valore GUID può essere generato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e quindi utilizzato nell'updategram. Nel contesto dei DiffGram, è possibile usare la **sql:guid** annotazione per specificare se utilizzare un valore GUID generato da SQL Server o usare il valore fornito nell'updategram per la colonna.  
  
 Il **sql:guid** annotazione può essere assegnata a due valori:  
  
 generate  
 Specifica che il valore GUID generato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere utilizzato per la colonna specifica nell'operazione di aggiornamento.  
  
 useValue  
 Specifica che per la colonna deve essere utilizzato il valore specificato nell'updategram. Si tratta del valore predefinito.  
  
  
