---
title: catalog.executable_statistics | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 3dda28d6-10d8-4294-9b5e-a6048c07faf9
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0d3963a3908fe50ddf0a00ac0263009f033abe1a
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35408893"
---
# <a name="catalogexecutablestatistics"></a>catalog.executable_statistics
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Consente di visualizzare una riga per ogni file eseguibile in esecuzione, inclusa ogni iterazione di un file eseguibile.  
  
 Un eseguibile è un'attività o un contenitore aggiunto al flusso di controllo di un pacchetto.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|Statistics_id|BIGINT|ID univoco dei dati.|  
|Execution_id|BIGINT|ID univoco per l'istanza dell'esecuzione.<br /><br /> La vista catalog.executions fornisce informazioni aggiuntive sulle esecuzioni. Per altre informazioni, vedere [catalog.executions &#40;database SSISDB&#41;](../../integration-services/system-views/catalog-executions-ssisdb-database.md).|  
|Executable_id|BIGINT|ID univoco per il componente del pacchetto.<br /><br /> La vista catalog.executables fornisce informazioni aggiuntive sui file eseguibili. Per altre informazioni, vedere [catalog.executables](../../integration-services/system-views/catalog-executables.md).|  
|Execution_path|nvarchar(max)|Percorso di esecuzione completo del componente del pacchetto, inclusa ogni iterazione del componente.|  
|Start_time|datetimeoffset(7)|Ora in cui il file eseguibile passa nella fase di pre-esecuzione.|  
|End_time|datetimeoffset(7)|Ora in cui il file eseguibile passa nella fase di post-esecuzione.|  
|Execution_duration|INT|Durata di tempo di esecuzione del file eseguibile. Il valore è espresso in millisecondi.|  
|Execution_result|SMALLINT|Di seguito sono indicati i valori possibili:<br /><br /> 0 (Esito positivo)<br /><br /> 1 (Esito negativo)<br /><br /> 2 (Completamento)<br /><br /> 3 (Esecuzione annullata)|  
|Execution_value|sql_variant|Valore restituito dall'esecuzione. Si tratta di un valore definito dall'utente.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ per l'istanza dell'esecuzione.  
  
-   Appartenenza al ruolo del database **ssis_admin**.  
  
-   Appartenenza al ruolo del server **sysadmin**.  
  
  
