---
title: Il recupero dei dati come flusso usando il Driver SQLSRV | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 17dc9129-04cd-430c-b5b3-82824116425d
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: be1e84c923dad3ed92c4c2b983a1e5592741eead
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35309250"
---
# <a name="retrieving-data-as-a-stream-using-the-sqlsrv-driver"></a>Recupero di dati come flusso usando il driver SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Il recupero dei dati come un flusso è disponibile nel driver SQLSRV dei solo il [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]e non è disponibile nel driver PDO_SQLSRV.  
  
I [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] usano i flussi per recuperare grandi quantità di dati. Negli argomenti di questa sezione vengono fornite informazioni dettagliate su come recuperare i dati come flusso.  
  
Di seguito sono elencati i passaggi principali per il recupero dei dati sotto forma di flusso:  
  
1.  Preparare ed eseguire una query Transact-SQL con [sqlsrv_query](../../connect/php/sqlsrv-query.md) o la combinazione di [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)/[sqlsrv_execute](../../connect/php/sqlsrv-execute.md).  
  
2.  Usare [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md) per spostarsi alla riga successiva nel set di risultati.  
  
3.  Usare [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) per recuperare un campo dalla riga. Specificare che i dati deve essere recuperata come flusso con **SQLSRV_PHPTYPE_STREAM (<encoding>)** come terzo parametro nella chiamata di funzione. Nella tabella sono elencate le costanti usate per specificare le codifiche e le relative descrizioni:  
  
    |Costante SQLSRV|Description|  
    |-------------------|---------------|  
    |SQLSRV_ENC_BINARY|I dati vengono restituiti come flusso di byte non elaborati proveniente dal server senza alcuna codifica o conversione.|  
    |SQLSRV_ENC_CHAR|I dati vengono restituiti come caratteri a 8 bit come specificato nella tabella codici delle impostazioni locali di Windows impostate nel sistema. Eventuali caratteri multibyte o che non eseguono il mapping in questa tabella codici vengono sostituiti con un carattere punto interrogativo (?) a byte singolo.|  
  
> [!NOTE]  
> Alcuni tipi di dati vengono restituiti come flussi per impostazione predefinita. Per altre informazioni, vedere [Default PHP Data Types](../../connect/php/default-php-data-types.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|---------|---------------|  
|[Tipi di dati con supporto di flusso tramite il driver SQLSRV](../../connect/php/data-types-with-stream-support-using-the-sqlsrv-driver.md)|Elenca i tipi di dati di SQL Server che possono essere recuperati come flussi.|  
|[Procedura: Recupero di dati di tipo carattere come flusso usando il driver SQLSRV](../../connect/php/how-to-retrieve-character-data-as-a-stream-using-the-sqlsrv-driver.md)|Descrive come recuperare i dati di tipo carattere come flusso.|  
|[Procedura: Recuperare dati binari come flusso usando il driver SQLSRV](../../connect/php/how-to-retrieve-binary-data-as-a-stream-using-the-sqlsrv-driver.md)|Descrive come recuperare i dati binari come flusso.|  
  
## <a name="see-also"></a>Vedere anche  
[Recupero di dati](../../connect/php/retrieving-data.md)

[Costanti &#40;driver Microsoft per PHP per SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
  
