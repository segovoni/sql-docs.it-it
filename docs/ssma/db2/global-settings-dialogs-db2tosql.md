---
title: Impostazioni globali (finestre di dialogo) (DB2ToSQL) | Documenti Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 360e01bb-6347-4e2b-acda-0daa161ed33b
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 5ce168a2cfe2937195bffe20c39a9a2a4f3fbf3b
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34774817"
---
# <a name="global-settings-dialogs-db2tosql"></a>Impostazioni globali (finestre di dialogo) (DB2ToSQL)
Utilizzare la pagina di finestre di dialogo del **impostazioni globali** la finestra di dialogo per specificare l'azione predefinita dell'utente e impostazioni di avviso per SSMA.  
  
Per accedere alle impostazioni di finestra di dialogo nel **strumenti** dal menu **impostazioni globali**, fare clic su **GUI** nella parte inferiore del riquadro sinistro, quindi scegliere **finestre di dialogo**.  
  
## <a name="options"></a>Opzioni  
**Avvisa prima di sovrascrivere gli oggetti**  
Quando SSMA converte gli oggetti in SQL Server, alcuni oggetti potrebbero già esistere nei metadati del progetto SQL Server. Questi oggetti possono sono già stati convertiti o gli oggetti siano presenti lo stesso nome all'interno dello schema di destinazione come oggetti di cui che si desidera convertire.  
  
Utilizzare questa opzione per specificare se SSMA venga chiesto di sovrascrivere le definizioni degli oggetti duplicati:  
  
-   Se si seleziona **True**, SSMA verrà visualizzata una finestra di dialogo di avviso quando rileva un oggetto duplicato. In questa finestra di dialogo è possibile specificare per sovrascrivere i singoli oggetti o tutti gli oggetti duplicati o di ignorare i singoli oggetti o tutti gli oggetti duplicati.  
  
-   Se si seleziona **False**, **azione predefinita di sovrascrittura dell'oggetto** opzione viene visualizzata in cui si specifica l'azione predefinita.  
  
**Azione predefinita sovrascrittura di oggetto**  
Questa opzione viene visualizzata se si seleziona **False** per il **Avvisa prima di sovrascrivere gli oggetti** opzione.  
  
Utilizzare questa opzione per specificare l'oggetto predefinito sovrascrivere il comportamento:  
  
-   Se si seleziona **True**, SSMA sovrascrive automaticamente gli oggetti nei metadati del progetto di SQL Server che hanno lo stesso nome e sono nello stesso schema di destinazione dell'oggetto da convertire.  
  
-   Se si seleziona **False**, SSMA non sovrascrive i metadati degli oggetti durante la conversione.  
  
