---
title: SQL Server Integration Services (SSIS) Scale Out | Microsoft Docs
description: Questo articolo presenta una panoramica della funzionalità SQL Server Integration Services (SSIS) Scale Out, che fornisce l'esecuzione ad alte prestazioni dei pacchetti SSIS
ms.custom: performance
ms.date: 12/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7fc57db9bc8a305450aa2619d9b7c222fda91763
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35334085"
---
# <a name="integration-services-ssis-scale-out"></a>Scalabilità orizzontale di Integration Services (SSIS)
SQL Server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) Scale Out garantisce l'esecuzione ad alte prestazioni dei pacchetti SSIS mediante la distribuzione delle singole esecuzioni su più computer. Dopo aver impostato Scale Out è possibile avviare più esecuzioni di pacchetti in parallelo da SQL Server Management Studio (SSMS) in modalità di scalabilità orizzontale.

## <a name="components"></a>Components
[!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out include un componente [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out Master e uno o più componenti [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out Worker.

-   Il master di scalabilità orizzontale è responsabile della gestione del servizio di scalabilità orizzontale e riceve le richieste di esecuzione dei pacchetti dagli utenti. Per altre informazioni, vedere [Scale Out Master](integration-services-ssis-scale-out-master.md).

-   I componenti Scale Out Worker eseguono il pull di attività di esecuzione da Scale Out Master ed eseguono i pacchetti. Per altre informazioni, vedere [Scale Out Worker](integration-services-ssis-scale-out-worker.md).

## <a name="configuration-options"></a>Opzioni di configurazione
È possibile installare Scale Out nelle configurazioni seguenti:

-   **In un singolo computer**, dove un'istanza di Scale Out Master e un'istanza di Scale Out Worker eseguono in parallelo sullo stesso computer.

-   **In più computer**, dove ogni Scale Out Worker risiede in un computer diverso.

## <a name="what-you-can-do"></a>Operazioni possibili
Dopo aver configurato Scale Out è possibile eseguire le operazioni seguenti:

-   Eseguire in parallelo più pacchetti distribuiti nel catalogo SSISDB. Per altre informazioni, vedere [Eseguire pacchetti in Scale Out](run-packages-in-integration-services-ssis-scale-out.md).

-   Gestire la topologia Scale Out nell'app Scale Out Manager. Per altre informazioni, vedere [Integration Services Scale Out Manager](integration-services-ssis-scale-out-manager.md).

## <a name="next-steps"></a>Passaggi successivi
-   [Introduzione a Integration Services Scale Out (SSIS) in un singolo computer](get-started-with-ssis-scale-out-onebox.md)

-   [Procedura dettagliata: Installare il servizio di scalabilità orizzontale di Integration Services](walkthrough-set-up-integration-services-scale-out.md)
