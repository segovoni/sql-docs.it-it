---
title: sys.fn_net_changes_&lt;capture_instance&gt; (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- sys.fn_net_changes_TSQL
- fn_net_changes_TSQL
- fn_net_changes
- sys.fn_net_changes
dev_langs:
- TSQL
helpviewer_keywords:
- fn_net_changes_<capture_instance>
- sys.fn_net_changes_<capture_instance>
ms.assetid: 342fa030-9fd9-4b74-ae4d-49f6038a5073
caps.latest.revision: 16
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 36430bb3303088677debcd65b2e1f10f170ed26b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33238701"
---
# <a name="sysfnnetchangesltcaptureinstancegt-transact-sql"></a>sys.fn_net_changes_&lt;capture_instance&gt; (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wrapper per il **modifiche net** funzioni di query. Gli script necessari per creare queste funzioni vengono generati dalla stored procedure sys.sp_cdc_generate_wrapper_function.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn_net_changes_<capture_instance> ('start_time', 'end_time', '<row_filter_option>' )  
  
<capture_instance> ::= The name of the capture instance.  
<row_filter_option> ::=  
{ all  
  | all with mask  
  | all with merge  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 *start_time*  
 Il **datetime** valore che rappresenta l'endpoint inferiore dell'intervallo di modifica delle voci della tabella da includere nel set di risultati.  
  
 Solo le righe in cdc. < capture_instance > _CT modifiche di tabella che dispone di un'ora di commit associata maggiore di *start_time* sono inclusi nel set di risultati.  
  
 Se viene fornito un valore NULL per questo argomento, l'endpoint inferiore dell'intervallo della query corrisponderà all'endpoint inferiore dell'intervallo valido per l'istanza di acquisizione.  
  
 *end_time*  
 Il **datetime** valore che rappresenta l'endpoint superiore dell'intervallo di modifica delle voci della tabella da includere nel set di risultati.  
  
 Questo parametro può assumere uno dei due significati, a seconda del valore scelto per @closed_high_end_point quando Sys. sp_cdc_generate_wrapper_function viene chiamato per generare lo script per creare la funzione wrapper:  
  
-   @closed_high_end_point = 1  
  
     Solo le righe in cdc. < capture_instance > _CT modifiche di tabella che dispone di un valore in \_ \_$start_lsn e un'operazione di commit corrispondente minore o uguale all'ora **start_time** sono inclusi nel set di risultati.  
  
-   @closed_high_end_point = 0  
  
     Solo le righe in cdc. < capture_instance > _CT modifiche di tabella che dispone di un valore in \_ \_$start_lsn e un oggetto corrispondente ora di commit minore **start_time** sono inclusi nel set di risultati.  
  
 Se viene fornito un valore NULL per questo argomento, l'endpoint superiore dell'intervallo della query corrisponderà all'endpoint superiore dell'intervallo valido per l'istanza di acquisizione.  
  
 *< row_filter_option >* :: = {tutti | all con mask | all con merge}  
 Opzione applicata al contenuto delle colonne dei metadati e alle righe restituite nel set di risultati. Le opzioni possibili sono le seguenti:  
  
 all  
 Restituisce il contenuto finale di una riga modificata nelle colonne di contenuto e l'operazione necessaria per applicare la riga nella colonna di metadati __CDC_OPERATION.  
  
 all with mask  
 Restituisce il contenuto finale di tutte le colonne modificate nelle colonne di contenuto e l'operazione necessaria per applicare ciascuna riga nella colonna di metadati __CDC_OPERATION. Se è stato specificato un elenco di flag di aggiornamento al momento della generazione dello script di creazione della funzione wrapper, questa opzione è necessaria per popolare la maschera di aggiornamento.  
  
 all with merge  
 Restituisce il contenuto finale di tutte le righe modificate nelle colonne di contenuto.  
  
 I due possibili valori per la colonna __CDC_OPERATION sono i seguenti:  
  
-   D, se la riga deve essere eliminata.  
  
-   M, se la riga deve essere inserita o aggiornata.  
  
 La logica per determinare se è necessaria un'operazione di inserimento o di aggiornamento per applicare una modifica alla destinazione aggiunge maggiore complessità alla query. Utilizzare questa opzione per ottenere prestazioni ottimali quando non è necessario distinguere tra le operazioni di inserimento e aggiornamento. Questo approccio funziona meglio negli ambienti di destinazione dove è direttamente disponibile un'operazione di unione, ad esempio un ambiente [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di colonna|Description|  
|-----------------|-----------------|-----------------|  
|\<le colonne da @column_list>|**Varia**|Le colonne identificate nel **column_list** argomento sp_cdc_generate_wrapper_function la funzione quando viene chiamato per generare lo script di creazione del wrapper. Se *column_list* è NULL, tutte le colonne di origine rilevate verranno visualizzati nel set di risultati.|  
|__CDC_OPERATION|**nvarchar(2)**|Codice operativo che indica che l'operazione è necessaria per applicare la riga all'ambiente di destinazione. L'operazione varia in base al valore dell'argomento *row_filter_option* fornito nella chiamata seguente:<br /><br /> *row_filter_option* = "all", 'all with mask'<br /><br /> 'D' - operazione di eliminazione<br /><br /> 'I' - operazione di inserimento<br /><br /> 'UN' - operazione di aggiornamento<br /><br /> *row_filter_option* = 'all with merge'<br /><br /> 'D' - operazione di eliminazione<br /><br /> 'M' - operazione di inserimento oppure di aggiornamento|  
|\<le colonne da @update_flag_list>|**bit**|Flag di bit denominato aggiungendo _uflag al nome della colonna. Il flag assume un valore non null solo quando *row_filter_option* **= 'all with mask'** e \__CDC_OPERATION **=' un' '**. È impostato su 1 se la colonna corrispondente è stata modificata all'interno della finestra di query. Altrimenti, è impostato su 0.|  
  
## <a name="remarks"></a>Osservazioni  
 La funzione fn_net_changes_<capture_instance> viene utilizzata come wrapper per la funzione di query cdc.fn_cdc_get_net_changes_<capture_instance>. La stored procedure sys.sp_cdc_generate_wrapper viene utilizzata per creare lo script per il wrapper.  
  
 Le funzioni wrapper non vengono create automaticamente. Per creare le funzioni wrapper, è necessario eseguire due operazioni:  
  
1.  Eseguire la stored procedure per generare lo script di creazione del wrapper.  
  
2.  Eseguire lo script per creare effettivamente la funzione wrapper.  
  
 Le funzioni wrapper consentono agli utenti di eseguire sistematicamente query per le modifiche che si sono verificati all'interno di un intervallo limitato dai **datetime** anziché i valori da valori LSN. Le funzioni wrapper eseguono tutte le conversioni necessarie tra forniti **datetime** valori e i valori LSN necessari internamente come argomenti alle funzioni di query. Quando le funzioni wrapper vengono utilizzate in sequenza per elaborare un flusso di dati delle modifiche, garantiscono che nessun dato persi o ripetuto purché venga rispettata la convenzione seguente: il @end_time valore dell'intervallo di cui è associata a una chiamata viene fornito come il @start_time valore per l'intervallo associato alla chiamata successiva.  
  
 Utilizzando il parametro @closed_high_end_point durante la creazione dello script, è possibile generare wrapper per supportare un limite superiore chiuso o un limite superiore aperto nella finestra della query specificata, ovvero è possibile decidere se le voci che dispongono di un'ora di commit uguale al limite superiore dell'intervallo di estrazione devono essere incluse nell'intervallo. Per impostazione predefinita, il limite superiore è incluso.  
  
 Il set di risultati restituito dal **modifiche net** wrapper funzione restituisce solo le colonne che sono stati in rilevate di @column_list quando è stato generato il wrapper. Se @column_list è NULL, vengono restituite tutte le colonne di origine rilevate. Le colonne di origine sono seguite dalla colonna __CDC_OPERATION, una colonna di uno o due caratteri che identifica l'operazione.  
  
 I flag di bit vengono quindi aggiunti al set di risultati per ogni colonna identificata nel parametro @update_flag_list. Per il **modifiche net** wrapper, il bit di flag verrà sempre NULL se il @row_filter_option che è utilizzato nella chiamata alla funzione wrapper è ' all'o 'all with merge'. Se il @row_filter_option è impostata su 'all with mask' e cdc_operation è ' o 'I', il valore del flag sarà NULL. Se \__CDC_OPERATION è ' un' ', il flag verrà impostato su 1 o 0, a seconda che il **net** ha causato una modifica alla colonna di operazione di aggiornamento.  
  
 Il modello di configurazione di Change Data Capture 'Instantiate CDC Wrapper TVFs for Schema' mostra come utilizzare la stored procedure sp_cdc_generate_wrapper_function per ottenere gli script CREATE per tutte le funzioni wrapper per le funzioni di query definite di uno schema. Il modello crea quindi tali script. Per ulteriori informazioni sui modelli, vedere [Esplora modelli](http://msdn.microsoft.com/library/b9ee55c5-bb44-4f76-90ac-792d8d83b4c8).  
  
## <a name="see-also"></a>Vedere anche  
 [sys.sp_cdc_generate_wrapper_function &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql.md)   
 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)  
  
  
