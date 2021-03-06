---
title: Aggiungere un'istanza di SSIS Scale Out Worker con Scale Out Manager | Microsoft Docs
description: Questo articolo descrive come aggiungere un SSIS Scale Out Worker a un ambiente Scale Out esistente usando Scale Out Manager.
ms.custom: performance
ms.date: 12/19/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: f4f9f055cefe4e3212066ea06868e88e399eaf36
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35335905"
---
# <a name="add-a-scale-out-worker-with-scale-out-manager"></a>Aggiungere un'istanza di Scale Out Worker con Scale Out Manager

Integration Services Scale Out Manager semplifica il processo di aggiunta di un'istanza di Scale Out Worker all'ambiente Scale Out esistente. 

Seguire questa procedura per aggiungere un'istanza di Scale Out Worker alla topologia Scale Out esistente:

## <a name="1-install-scale-out-worker"></a>1. Installare Scale Out Worker
Nell'installazione guidata di SQL Server selezionare Integration Services e Scale Out Worker nella pagina **Selezione funzionalità**. 
![Selezione della funzionalità Ruolo di lavoro](media/feature-select-worker.PNG)

Nella pagina **Configurazione di Integration Services Scale Out - Nodo di lavoro** è possibile fare clic su **Avanti** per ignorare la configurazione corrente e usare **Scale Out Manager** per eseguire la configurazione dopo l'installazione.

Terminare l'installazione guidata.

## <a name="2-open-the-firewall-on-the-scale-out-master-computer"></a>2. Aprire il firewall nel computer Scale Out Master
Aprire la porta specificata durante l'installazione di Scale Out Master (8391 per impostazione predefinita) e la porta di SQL Server (1433 per impostazione predefinita) in Windows Firewall nel computer Scale Out Master.

## <a name="3-add-a-scale-out-worker-with-scale-out-manager"></a>3. Aggiungere un'istanza di Scale Out Worker con Scale Out Manager
Eseguire SQL Server Management Studio come amministratore e connettersi all'istanza di SQL Server di Scale Out Master.

In Esplora oggetti fare clic con il pulsante destro del mouse su **SSISDB** e selezionare **Gestisci Scale Out**. 

![Gestisci Scale Out](media/manage-scale-out.PNG)

Nella finestra di dialogo **Scale Out Manager** passare a **Strumento di gestione dei ruoli di lavoro**. Selezionare **+** e seguire le istruzioni nella finestra di dialogo **Connect Worker** (Connettere il nodo di lavoro). 

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni, vedere [Scale Out Manager](integration-services-ssis-scale-out-manager.md).