---
title: MSSQLSERVER_17194 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- "17194"
helpviewer_keywords:
- 17194 (Database Engine error)
ms.assetid: 0d03eb20-28a7-4ceb-8903-7f9420a620f7
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 86b31ea758d754e4c70402ad478ef0ea7ee5707c
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34320562"
---
# <a name="mssqlserver17194"></a>MSSQLSERVER_17194
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17194|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico||  
|Testo del messaggio|Impossibile caricare la libreria di provider SSL necessaria per l'accesso. La connessione è stata chiusa. SSL viene utilizzato per crittografare la sequenza di accesso o tutte le comunicazioni, a seconda della configurazione del server. Consultare la documentazione online per informazioni su questo messaggio di errore:  0xXXXX. [CLIENT: 11.11.11.11]|  
  
## <a name="explanation"></a>Spiegazione  
Questo errore indica che la connessione è stata chiusa dal client. Questo errore potrebbe verificarsi poiché è scaduto il timeout della connessione. Nel messaggio di errore viene visualizzato un valore del sistema operativo che descrive il problema sottostante.  
  
## <a name="user-action"></a>Azione dell'utente  
Se il codice di errore nel messaggio è 0x2746 (valore decimale 10054), la connessione è stata reimpostata dal client, in genere a causa di un timeout. Per risolvere l'errore, aumentare il timeout della connessione nel client o nel programma che esegue la chiamata.  
  
Per determinare una possibile soluzione per altri valori del messaggio di errore, usare il comando **net helpmsg** del sistema operativo e specificare il valore decimale del codice di errore.  
  
Per altre informazioni sulla connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Configurazione di rete del server](~/database-engine/configure-windows/server-network-configuration.md) e [Configurazione di rete dei client](~/database-engine/configure-windows/client-network-configuration.md).  
  
## <a name="internal-only"></a>Solo interno  
