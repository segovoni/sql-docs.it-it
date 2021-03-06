---
title: Implementazione della compressione di riga | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- compression [SQL Server], row
- row compression [Database Engine]
ms.assetid: dcd97ac1-1c85-4142-9594-9182e62f6832
caps.latest.revision: 17
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cddc9636612e5e96c067f4c1c0d87b46976372ba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37160472"
---
# <a name="row-compression-implementation"></a>Implementazione della compressione di riga
  In questo argomento vengono riepilogate le modalità di implementazione della compressione di riga nel [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Tale riepilogo fornisce informazioni di base che consentono di pianificare lo spazio di archiviazione necessario per i dati.  
  
 L'abilitazione della compressione modifica solo il formato di archiviazione fisica dei dati associato a un tipo di dati, ma non la relativa sintassi o semantica. Le modifiche alle applicazioni non sono obbligatorie quando una o più tabelle sono abilitate per la compressione. Al nuovo formato di archiviazione del record sono associate le seguenti modifiche principali:  
  
-   Riduzione dell'overhead di metadati associati al record. Tali metadati rappresentano informazioni su colonne e sui relativi offset e lunghezze. In alcuni casi, l'overhead di metadati potrebbe essere maggiore del formato di archiviazione obsoleto.  
  
-   Usa il formato di archiviazione a lunghezza variabile per i tipi numerici (ad esempio `integer`, `decimal`, e `float`) e i tipi di base numerici (ad esempio `datetime` e `money`).  
  
-   Archiviazione di stringhe di caratteri a lunghezza fissa utilizzando un formato a lunghezza variabile senza archiviare i caratteri vuoti.  
  
> [!NOTE]  
>  Ottimizzazione dei valori NULL e 0 per tutti i tipi di dati in modo che non occupino alcun byte.  
  
## <a name="how-row-compression-affects-storage"></a>Influenza della compressione di riga sull'archiviazione  
 Nella tabella seguente viene descritto il modo in cui la compressione di riga influisce sui tipi esistenti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nella tabella non sono inclusi i risparmi in termini di spazio che possono essere ottenuti usando la compressione di pagina.  
  
|Tipo di dati|Influenza sull'archiviazione|Description|  
|---------------|--------------------------|-----------------|  
|`tinyint`|no|Lo spazio di archiviazione minimo necessario è 1 byte.|  
|`smallint`|Sì|Se il valore può essere archiviato in 1 byte, verrà utilizzato solo 1 byte.|  
|`int`|Sì|Utilizza solo i byte necessari. Ad esempio, se un valore può essere archiviato in 1 byte, verrà utilizzato solo 1 byte.|  
|`bigint`|Sì|Utilizza solo i byte necessari. Ad esempio, se un valore può essere archiviato in 1 byte, verrà utilizzato solo 1 byte.|  
|`decimal`|Sì|Questa archiviazione corrisponde al formato di archiviazione vardecimal.|  
|`numeric`|Sì|Questa archiviazione corrisponde al formato di archiviazione vardecimal.|  
|`bit`|Sì|L'overhead di metadati aumenta questo valore a 4 bit.|  
|`smallmoney`|Sì|Rappresenta i dati Integer utilizzando un numero intero di 4 byte. Il valore della valuta viene moltiplicato per 10.000 e il valore intero risultante viene archiviato rimuovendo tutte le cifre dopo il separatore decimale. e un'ottimizzazione dell'archiviazione analoga a quella associata ai tipi Integer.|  
|`money`|Sì|Rappresenta i dati Integer utilizzando un Integer a 8 byte. Il valore della valuta viene moltiplicato per 10.000 e il valore intero risultante viene archiviato rimuovendo tutte le cifre dopo il separatore decimale. A questo tipo sono associati un intervallo maggiore rispetto a `smallmoney` e un'ottimizzazione dell'archiviazione analoga a quella associata ai tipi Integer.|  
|`float`|Sì|Il byte meno significativi con zeri non sono archiviati. `float` la compressione si applica soprattutto per valori non frazionari in mantissa.|  
|`real`|Sì|Il byte meno significativi con zeri non sono archiviati. `real` la compressione si applica soprattutto per valori non frazionari in mantissa.|  
|`smalldatetime`|no|Rappresenta i dati Integer usando due numeri interi a 2 byte. Per una data, sono necessari due 2 byte. La data rappresenta il numero di giorni dall'1/1/1901. Poiché a partire dal 1902 è necessario utilizzare 2 byte, dopo tale data non viene ottenuto alcun risparmio in termini di spazio.<br /><br /> L'ora rappresenta il numero di minuti a partire dalla mezzanotte. Per i valori di ora appena successivi alle 04.00, viene utilizzato il secondo byte.<br /><br /> Se un tipo di dati `smalldatetime` viene utilizzato solo per rappresentare una data (caso comune), l'ora è 00.00. La compressione consente di risparmiare 2 byte archiviando l'ora nel formato con byte più significativo per la compressione di riga.|  
|`datetime`|Sì|Rappresenta i dati Integer utilizzando due numeri interi di 4 byte. Il numero intero rappresenta il numero di giorni con data di base 1/1/1900. I primi 2 byte possono rappresentare gli anni fino al 2079. In questo caso la compressione consente di risparmiare sempre 2 byte fino a quella data. Ogni valore intero rappresenta 3,33 millisecondi. Poiché la compressione esaurisce i primi 2 byte nei i primi cinque minuti e deve utilizzare il quarto byte dopo le 16.00, a partire da tale ora è possibile risparmiare solo 1 byte in termini di spazio. Quando si `datetime` viene compresso come qualsiasi altro numero intero, la compressione consente di risparmiare 2 byte nell'archiviazione della data.|  
|`date`|no|Rappresenta i dati Integer usando 3 byte. In questo modo è possibile rappresentare la data a partire dall'1/1/0001. Poiché per le date contemporanee la compressione di riga utilizza tutti i 3 byte, non viene ottenuto alcun risparmio in termini di spazio.|  
|`time`|no|Rappresenta i dati Integer usando da 3 a 6 byte. Sono disponibili diversi valori di precisione, da 0 a 9, rappresentabili con un numero di byte compreso tra 3 e 6. La compressione di riga non comporta alcuna modifica nell'archiviazione. In generale, non molto risparmi è possibile prevedere se si comprime il `time` tipo di dati. Lo spazio compresso viene utilizzato nel modo seguente:<br /><br /> Precisione = 0. Byte = 3. Ogni valore intero rappresenta un secondo. La compressione può rappresentare le ore fino alle 18.00 utilizzando 2 byte, con un risparmio potenziale di 1 byte.<br /><br /> Precisione = 1. Byte = 3. Ogni valore intero rappresenta 1/10 secondi. Poiché la compressione utilizza il terzo byte prima delle 02.00, il risparmio in termini di spazio è ridotto.<br /><br /> Precisione = 2. Byte = 3. Caso analogo al precedente. È improbabile ottenere un risparmio.<br /><br /> Precisione = 3. Byte = 4. Poiché i primi 3 byte vengono utilizzati prima delle 05.00, il risparmio ottenuto è ridotto.<br /><br /> Precisione = 4. Byte = 4. Poiché i primi 3 byte vengono utilizzati nei primi 27 secondi, non viene ottenuto alcun risparmio in termini di spazio.<br /><br /> Precisione = 5, byte = 5. Il quinto byte verrà utilizzato dopo le 12.00.<br /><br /> Precisione = 6 e 7. Byte = 5. Non viene ottenuto alcun risparmio in termini di spazio.<br /><br /> Precisione = 8. Byte = 6. Il sesto byte verrà utilizzato dopo le 03.00.|  
|`datetime2`|Sì|Rappresenta i dati Integer utilizzando un numero di byte compreso tra 6 e 9. I primi 4 byte rappresentano la data. I byte utilizzati per rappresentare l'ora dipenderanno dalla precisione dell'ora specificata.<br /><br /> Il valore intero rappresenta il numero di giorni a partire dall'1/1/0001. Il limite superiore è la data del 31/12/9999. Per rappresentare una data nell'anno 2005, la compressione utilizza 3 byte.<br /><br /> Non viene ottenuto alcun risparmio nella rappresentazione dell'ora, poiché è consentito l'utilizzo di un numero di byte compreso tra 2 e 4 per valori di precisione dell'ora diversi. Di conseguenza, per rappresentare l'ora con valore di precisione di un secondo, la compressione utilizza 2 byte e il secondo byte viene utilizzato dopo 255 secondi.|  
|`datetimeoffset`|Sì|È simile a `datetime2`, ad eccezione del fatto che sono disponibili 2 byte del fuso orario del formato (hh.mm).<br /><br /> Analogamente a `datetime2`, la compressione consente di risparmiare 2 byte.<br /><br /> Per i valori del fuso orario, il valore MM potrebbe essere uguale a 0 per la maggior parte dei casi. Di conseguenza, la compressione consente di risparmiare 1 byte.<br /><br /> La compressione di riga non apporta alcuna modifica all'archiviazione.|  
|`char`|Sì|I caratteri di riempimento finali vengono rimossi. Si noti che in [!INCLUDE[ssDE](../../includes/ssde-md.md)] viene inserito lo stesso carattere di riempimento indipendentemente dalle regole di confronto utilizzate.|  
|`varchar`|no|Nessun effetto.|  
|`text`|no|Nessun effetto.|  
|`nchar`|Sì|I caratteri di riempimento finali vengono rimossi. Si noti che in [!INCLUDE[ssDE](../../includes/ssde-md.md)] viene inserito lo stesso carattere di riempimento indipendentemente dalle regole di confronto utilizzate.|  
|`nvarchar`|no|Nessun effetto.|  
|`ntext`|no|Nessun effetto.|  
|`binary`|Sì|Gli zero finali vengono rimossi.|  
|`varbinary`|no|Nessun effetto.|  
|`image`|no|Nessun effetto.|  
|`cursor`|no|Nessun effetto.|  
|`timestamp` / `rowversion`|Sì|Rappresenta i dati Integer utilizzando 8 byte. È disponibile un contatore timestamp gestito per ogni database, il cui valore iniziale è pari a 0. È possibile comprimere questo tipo in modo analogo a qualsiasi altro valore intero.|  
|`sql_variant`|no|Nessun effetto.|  
|`uniqueidentifier`|no|Nessun effetto.|  
|`table`|no|Nessun effetto.|  
|`xml`|no|Nessun effetto.|  
|Tipi definiti dall'utente|no|Rappresentati internamente come `varbinary`.|  
|FILESTREAM|no|Rappresentati internamente come `varbinary`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Compressione dei dati](data-compression.md)   
 [Implementazione della compressione di pagina](page-compression-implementation.md)  
  
  
