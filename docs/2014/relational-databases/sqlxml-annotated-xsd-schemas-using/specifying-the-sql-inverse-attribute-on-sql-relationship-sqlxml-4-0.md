---
title: "Specifica l'attributo SQL: inverse in SQL: Relationship (SQLXML 4.0) | Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- bulk load [SQLXML]
- inverse attribute
- relationships [SQLXML], inverse orders
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- updategrams [SQLXML], relationships
- sql:inverse
ms.assetid: 08904cbd-9c86-493d-90c3-f5e1d13ce59d
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ac3bf643dc5237b6bbdc819a170ae7b8f2435d00
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194921"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>Specifica dell'attributo sql:inverse in sql:relationship (SQLXML 4.0)
  L'attributo `sql:inverse` risulta utile solo quando lo schema XSD viene utilizzato per il caricamento bulk o da un updategram. Il `sql:inverse` attributo può essere specificato per il  **\<SQL: Relationship >** elemento. Negli updategram la relativa logica interpreta lo schema nella determinazione delle tabelle e delle colonne aggiornate dall'operazione dell'updategram. Le relazioni padre-figlio specificate nello schema determinano l'ordine di modifica (inserimento o eliminazione) dei record.  
  
 Nel caso di uno schema XSD in cui la relazione padre-figlio viene specificata nell'ordine inverso a quello della relazione chiave primaria/chiave esterna tra le colonne del database corrispondenti, l'operazione di inserimento o eliminazione dell'updategram non riuscirà a causa della violazione della relazione chiave primaria/chiave esterna. In questi casi, il `sql:inverse` attributo è specificato (`sql:inverse="true"`) nella  **\<SQL: Relationship >** elemento e la logica dell'updategram inverte l'interpretazione della relazione padre-figlio specificata nello schema.  
  
 L'attributo `sql:inverse` utilizza un valore booleano (0=false, 1=true). I valori possibili sono 0, 1, true e false.  
  
 Per un esempio di utilizzo con il `sql:inverse` annotazione, vedere [specifica di uno Schema di Mapping con annotazioni in un Updategram](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Specifica di relazioni tramite SQL: Relationship &#40;SQLXML 4.0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
