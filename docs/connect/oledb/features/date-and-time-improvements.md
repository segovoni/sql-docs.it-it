---
title: Data e ora miglioramenti | Documenti Microsoft
description: Miglioramenti di data e ora nel Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 622df9211c29c60cfdb42034f6284164f8d9af3b
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611606"
---
# <a name="date-and-time-improvements"></a>Data e ora miglioramenti
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Questo argomento viene descritto il Driver OLE DB per il supporto di SQL Server per i tipi di dati di data e ora che sono stati aggiunti in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
 Per ulteriori informazioni sui miglioramenti di data/ora, vedere [data e ora miglioramenti &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md).  
  
 Per informazioni sulle applicazioni di esempio che illustrano questa funzionalità, vedere [esempi di programmazione dati di SQL Server](http://msftdpprodsamples.codeplex.com/).  
  
## <a name="usage"></a>Utilizzo  
 Nelle sezioni seguenti vengono descritte le diverse modalità di utilizzo dei nuovi tipi di data e ora.  
  
### <a name="use-date-as-a-distinct-data-type"></a>Utilizzare il tipo date come tipo di dati distinto  
 A partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], supporto avanzato per i tipi di data/ora rende più efficiente per utilizzare il tipo DBTYPE_DBDATE OLE DB.  
  
### <a name="use-time-as-a-distinct-data-type"></a>Utilizzare il tipo time come tipo di dati distinto  
 OLE DB include già un tipo di dati che contiene solo l'ora, ovvero DBTYPE_DBTIME, che garantisce precisione pari a 1 secondo.
  
 Il nuovo [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ora il tipo di dati ha frazionaria dei secondi precisione di 100 nanosecondi. Ciò richiede un nuovo tipo di Driver OLE DB per SQL Server: DBTYPE_DBTIME2. Le applicazioni esistenti scritte per utilizzare le ore senza secondi frazionari possono utilizzare colonne time(0). Il tipo OLE DB DBTYPE_TIME esistente e relative strutture corrispondenti funzioneranno correttamente, a meno che le applicazioni si basano sul tipo restituito nei metadati.  
  
### <a name="use-time-as-a-distinct-data-type-with-extended-fractional-seconds-precision"></a>Utilizzare il tipo time come tipo di dati distinto con precisione frazionaria dei secondi estesa  
 Alcune applicazioni, ad esempio le applicazioni di controllo dei processi e di produzione, richiedono la possibilità di gestire i dati di tipo time con una precisione pari a fino 100 nanosecondi. Nuovo tipo per questo scopo in OLE DB è DBTYPE_DBTIME2.  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision"></a>Utilizzare il tipo datetime con precisione frazionaria dei secondi estesa  
 OLE DB definisce già un tipo con una precisione pari fino a 1 nanosecondo. Questo tipo, tuttavia, è già utilizzato dalle applicazioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] esistenti, che garantiscono una probabile precisione pari solo a 1/300 di secondo. Il nuovo **datetime2(3)** tipo non è direttamente compatibile con il tipo datetime esistente. Se vi è un rischio che tale tipo di dati influisca negativamente sul comportamento dell'applicazione, le applicazioni devono utilizzare un nuovo flag DBCOLUMN per determinare il tipo di server effettivo.    
  
### <a name="use-datetime-with-extended-fractional-seconds-precision-and-timezone"></a>Utilizzare il tipo datetime con precisione frazionaria dei secondi estesa e fuso orario  
 Alcune applicazioni richiedono valori datetime con informazioni sul fuso orario. Questa è supportata per il nuovo tipo DBTYPE_DBTIMESTAMPOFFSET.
  
### <a name="use-datetimedatetimedatetimeoffset-data-with-client-side-conversions-consistent-with-existing-conversions"></a>Utilizzare dati di tipo date/time/datetime/datetimeoffset con conversioni sul lato client coerenti con le conversioni esistenti  
 Le conversioni vengono estesi in modo coerente per includere conversioni tra tutti i tipi di data e ora introdotti in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per funzionalità di SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
