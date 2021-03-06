---
title: Ambienti multiutente (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- users [SQL Server], multiuser environments
- conflict resolution [Visual Database Tools]
- multiple users making database changes
- multiuser environments [Visual Database Tools]
- database modifications [SQL Server]
- version control [Visual Database Tools]
- Visual Database Tools [SQL Server], multiuser environments
ms.assetid: 330bd48c-9427-4967-b58e-b7c492d5ee36
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 41d58d45e9411caa3734f95986f3d22a7cb77529
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33049498"
---
# <a name="multiuser-environments-visual-database-tools"></a>Ambienti multiutente (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Un ambiente multiutente è un ambiente in cui altri utenti possono connettersi e apportare modifiche allo stesso database sul quale si sta lavorando. È quindi possibile che numerosi utenti modifichino contemporaneamente gli stessi oggetti di database. In un ambiente multiutente è pertanto possibile che sul database in cui si stanno apportando le proprie modifiche incidano le modifiche apportate contemporaneamente da altri utenti e viceversa.  
  
Un aspetto fondamentale quando si utilizza un database in un ambiente multiutente è rappresentato dalle autorizzazioni di accesso. Le autorizzazioni di cui si dispone per il database determinano la gamma di attività che è possibile eseguire sul database. Per apportare, ad esempio, modifiche a oggetti in un database, è necessario disporre delle autorizzazioni di scrittura appropriate per il database. Per ulteriori informazioni sulle autorizzazioni per il database in uso, vedere la documentazione del database. Per altre informazioni, vedere [Autorizzazioni e Visual Database Tools &#40;Visual Database Tools&#41](../../ssms/visual-db-tools/permissions-and-visual-database-tools-visual-database-tools.md).  
  
Quando si salvano le modifiche apportate alle tabelle, in Progettazione tabelle viene verificato che il database non sia stato modificato dall'ultimo salvataggio delle modifiche. Se un altro utente ha apportato modifiche, si verrà informati che il database è stato modificato. A quel punto, è possibile decidere di riconciliare tali modifiche. Per altre informazioni, vedere [Riconciliare le modifiche apportate da più utenti &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/reconcile-changes-made-by-multiple-users-visual-database-tools.md).  
  
In un ambiente multiutente è opportuno prendere alcune precauzioni per evitare che le modifiche generino conflitti. Per altre informazioni, vedere [Problemi legati all'evoluzione del database & #40; Visual Database Tools & #41;](../../ssms/visual-db-tools/issues-of-database-evolution-visual-database-tools.md).  
  
Per evitare che si verifichino problemi, è possibile apportare le modifiche desiderate in una copia del database, ad esempio un database di verifica, quindi creare uno script delle modifiche da eseguire per estendere le modifiche al database originale dopo avere risolto i conflitti offline. Per altre informazioni, vedere [Database di sviluppo, verifica e produzione &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/development-test-and-production-databases-visual-database-tools.md).  
  
