---
title: Impostazione ExtendedAnsiSQL | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], setting
ms.assetid: 37b775d1-65ac-45ac-8572-454bc4e3c1a2
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 09db08bfd3aa143ebc91f813ade237048d9878b4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32900876"
---
# <a name="setting-extendedansisql"></a>Impostazione ExtendedAnsiSQL
L'attributo può essere controllato nella stringa di connessione, aggiungere l'attributo ExtendedAnsiSQL:  
  
|Value|Description|  
|-----------|-----------------|  
|ExtendedAnsiSQL = 0 (impostazione predefinita)|Questa impostazione non abilita le nuove funzionalità.|  
|ExtendedAnsiSQL = 1|Questa impostazione abilita le nuove funzionalità.|  
  
 L'attributo può essere impostato anche in un DSN tramite il **opzioni avanzate** la finestra di dialogo quando si configura un DSN tramite il pannello di controllo.  
  
 Impostare l'attributo su 0 disabilita le funzionalità nuove. impostarla su 1 abilita le nuove funzionalità.  
  
 L'attributo può essere impostato anche tramite SQLSetConnectAttr(). Il valore dell'attributo è 65501 e viene impostato su un valore SQLINTEGER 1 o 0, come illustrato nella tabella precedente. Può essere chiamato prima o dopo la connessione, ma è preferibile chiamata dopo la connessione a causa dell'ordine in cui i processi di driver memorizzati nella cache gli attributi di connessione e le stringhe di connessione.
