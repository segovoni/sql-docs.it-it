---
title: Controllare il comportamento di trigger e vincoli nella sincronizzazione | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- identities [SQL Server replication]
- constraints [SQL Server], replication
- triggers [SQL Server], replication
- triggers [SQL Server replication]
- constraints [SQL Server replication]
- NOT FOR REPLICATION option
- NFR option
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
caps.latest.revision: 36
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9a4a6c79b7f7d719321ce731fd9b379719ca68ab
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37349223"
---
# <a name="control-behavior-of-triggers-and-constraints-in-synchronization"></a>Controllare il comportamento di trigger e vincoli nella sincronizzazione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Durante la sincronizzazione gli agenti di replica eseguono istruzioni [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md), [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md) e [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md) in tabelle replicate che possono causare l'esecuzione di trigger DML (Data Manipulation Language) in tali tabelle. In alcuni casi è necessario impedire l'attivazione di questi trigger o l'applicazione di vincoli durante la sincronizzazione. Questo comportamento dipende dalla modalità di creazione del trigger o del vincolo.  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a>Per impedire l'esecuzione di trigger durante la sincronizzazione  
  
1.  Quando si crea un nuovo trigger, specificare l'opzione NOT FOR REPLICATION di [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md).  
  
2.  Per un trigger esistente specificare l'opzione NOT FOR REPLICATION di [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md).  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a>Per impedire l'applicazione di vincoli durante la sincronizzazione  
  
1.  Quando si crea un nuovo vincolo CHECK o FOREIGN KEY, specificare l'opzione CHECK NOT FOR REPLICATION nella definizione del vincolo di [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creare tabelle &#40;Motore di database&#41;](../../relational-databases/tables/create-tables-database-engine.md)  
  
  
