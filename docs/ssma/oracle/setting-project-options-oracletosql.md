---
title: Impostazione delle opzioni progetto (OracleToSQL) | Documenti Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Configuration Options and Modes
ms.assetid: a324d07d-cfdf-43bd-98a0-acf332c5a4db
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 5c606de3c03038f7e2fbb9f974ba96dd64bef779
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34777977"
---
# <a name="setting-project-options-oracletosql"></a>Impostazione delle opzioni progetto (OracleToSQL)
Per ogni progetto SSMA è possibile impostare opzioni del livello di progetto. Queste opzioni specificano la conversione degli oggetti, il caricamento di oggetti, impostazioni di migrazione di dati e di interfaccia utente. Prima di convertire oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o la migrazione dei dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], verificare che le opzioni di configurazione siano appropriate per il progetto.  
  
SSMA consente di configurare le opzioni predefinite per tutti i progetti. Queste opzioni vengono applicate a qualsiasi nuovo progetto creato. È quindi possibile personalizzare le opzioni per ogni progetto.  
  
## <a name="configuration-options-and-modes"></a>Modalità e le opzioni di configurazione  
SSMA con cinque set di impostazioni di progetto:  
  
-   Informazioni sul progetto  
  
-   Generale (conversione, la migrazione, il caricamento di oggetti)  
  
-   Synchronization  
  
-   GUI  
  
-   Mapping dei tipi  
  
Include inoltre quattro modalità per la configurazione di queste impostazioni:  
  
-   Default  
  
-   Optimistic  
  
-   Full  
  
-   Personalizzato  
  
La modalità predefinita è consigliata per la maggior parte degli utenti. La modalità ottimistica mantiene più la sintassi Oracle corrente e più facile la lettura. Tuttavia, mantenendo la sintassi corrente potrebbe non essere accurata. Se è necessario convertire la sintassi Oracle equivalente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi, la modalità completa esegue la conversione più completa, ma il codice risulta potrebbe essere più difficile da leggere. In modalità personalizzata, impostare le opzioni.  
  
Per ulteriori informazioni sulle impostazioni e come le impostazioni vengono applicate in ogni modalità, vedere gli argomenti seguenti:  
  
-   [Le impostazioni del progetto &#40;conversione&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md)  
  
-   [Le impostazioni del progetto &#40;migrazione&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-migration-oracletosql.md)  
  
-   [Le impostazioni del progetto&#40;sincronizzazione&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md)  
  
-   [Le impostazioni del progetto &#40;interfaccia utente grafica&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-gui-oracletosql.md)  
  
-   [Le impostazioni del progetto &#40;Mapping dei tipi di&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-type-mapping-oracletosql.md)  
  
## <a name="setting-project-options"></a>Impostazione delle opzioni di progetto  
In SSMA, è possibile configurare le impostazioni predefinite per tutti i progetti. Queste impostazioni vengono salvate nel file di configurazione di SSMA e applicate a qualsiasi nuovo progetto creato.  
  
**Per impostare opzioni di progetto predefinite**  
  
1.  Nel **strumenti** menu, fare clic su **impostazioni di progetto predefinite**.  
  
2.  Nel **impostazioni di progetto predefinite** la finestra di dialogo, utilizzare una delle procedure seguenti:  
  
    -   Selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** elenco a discesa fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi selezionare la conversione o la migrazione.  
  
    -   Per selezionare una modalità predefinita, il **modalità** casella di riepilogo a discesa, selezionare **predefinito**, **Optimistic**, o **completo**.  
  
    -   Per specificare le impostazioni personalizzate, selezionare o immettere le nuove impostazioni o i valori.  
  
3.  Fare clic su **OK** per salvare le impostazioni.  
  
È anche possibile personalizzare le impostazioni per il progetto corrente. Queste impostazioni vengono salvate nel file di progetto corrente.  
  
**Per personalizzare le impostazioni per il progetto corrente**  
  
1.  Nel **strumenti** menu, fare clic su **impostazioni progetto**.  
  
2.  Nel **impostazioni progetto** la finestra di dialogo, utilizzare una delle procedure seguenti:  
  
    -   Per selezionare una modalità predefinita, il **modalità** casella di riepilogo a discesa, selezionare **predefinito**, **Optimistic**, o **completo**.  
  
    -   Per specificare una modalità personalizzata, nel **modalità** , quindi selezionare **personalizzato**e quindi selezionare le impostazioni di progetto appropriate.  
  
3.  Fare clic su **OK** per salvare le impostazioni.  
  
## <a name="next-steps"></a>Passaggi successivi  
Il passaggio successivo della migrazione dipende dalle esigenze del progetto:  
  
-   Per personalizzare il mapping dei tipi di dati di origine e di destinazione, vedere [Mapping Oracle e tipi di dati di SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
-   In caso contrario, è possibile convertire le definizioni degli oggetti di database Oracle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] definizioni di oggetti. Per altre informazioni, vedere [conversione di schemi Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md).  
  
## <a name="see-also"></a>Vedere anche  
[Mapping di tipi di dati SQL Server e Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md)  
  
