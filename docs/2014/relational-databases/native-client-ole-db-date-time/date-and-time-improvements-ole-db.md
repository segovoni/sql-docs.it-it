---
title: Data e ora miglioramenti (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
ms.assetid: 71614aaf-0fa4-4fe0-b522-68e2e0b66f43
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cd6e01f8fbacfae69e81d3779e0e1fc8b54182c7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410720"
---
# <a name="date-and-time-improvements-ole-db"></a>Data e ora miglioramenti (OLE DB)
  In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] sono stati introdotti nuovi tipi di dati di data e ora. Questa sezione viene descritto come questi nuovi tipi vengono esposti come estensioni in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Per una panoramica del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporto di Native Client per i nuovi tipi data e ora dei dati, vedere [data e ora miglioramenti](../native-client/features/date-and-time-improvements.md). Per un esempio, vedere [utilizzo avanzate di data e ora funzionalità &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).  
  
 Per informazioni più generali sui tipi di dati di data e ora, vedere [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Supporto dei tipi di dati per i miglioramenti relativi a data e ora OLE DB](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 Fornisce informazioni su OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) i tipi che supportano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipi di dati di data e ora.  
  
 [Metadati &#40;OLE DB&#41;](../../database-engine/dev-guide/metadata-ole-db.md)  
 Contiene informazioni sulla struttura DBBINDING, `ICommandWithParameters::GetParameterInfo`, `ICommandWithParameters::SetParameterInfo`, `IColumnsRowset::GetColumnsRowset` e `ColumnsInfo::GetColumnInfo`. Vengono inoltre fornite informazioni sugli aggiornamenti ai set di righe dello schema OLE DB.  
  
 [Associazioni e conversioni &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
 Vengono illustrate le regole per la conversione fra server e client per tipi di dati sia nuovi che esistenti.  
  
 [Modifiche apportate alla copia di massa per i tipi avanzati di data e ora &#40;OLE DB e ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Vengono descritti i miglioramenti apportati ai tipi di data/ora per supportare le operazioni di copia bulk.  
  
 [Supporto dell'API OLE DB per i miglioramenti relativi a data e ora](ole-db-api-support-for-date-and-time-enhancements.md)  
 Vengono descritte le API OLE DB che supportano le caratteristiche avanzate dei tipi di dati date/time.  
  
 [Possibilità di confronto per IRowsetFind](../../relational-databases/native-client-ole-db-date-time/comparability-for-irowsetfind.md)  
 Vengono descritti i tipi date/time e `IRowsetFind`.  
  
 [Nuove caratteristiche data e ora con versioni precedenti di SQL Server &#40;OLE DB&#41;](new-date-and-time-features-with-previous-sql-server-versions-ole-db.md)  
 Viene descritto il comportamento previsto quando un'applicazione client che utilizza le caratteristiche avanzate dei tipi date e time comunica con una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e quando un client compilato con una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client invia comandi a un server che supporta tali caratteristiche avanzate.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
