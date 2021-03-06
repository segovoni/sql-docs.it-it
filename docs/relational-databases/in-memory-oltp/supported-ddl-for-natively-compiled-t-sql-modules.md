---
title: Costrutti DDL supportati per i moduli T-SQL compilati in modo nativo | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 422b2394c9467c80d92d3dd7164966d8b0e08bec
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34327093"
---
# <a name="supported-ddl-for-natively-compiled-t-sql-modules"></a>Costrutti DDL supportati per i moduli T-SQL compilati in modo nativo
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Questo argomento elenca i costrutti DDL supportati per i moduli T-SQL compilati in modo nativo, ad esempio stored procedure, funzioni definite dall'utente scalari, funzioni con valori di tabella inline e trigger.  
  
 Per informazioni sulle funzionalità e sulla superficie di attacco di T-SQL che possono essere usate nei moduli T-SQL compilati in modo nativo, vedere [Funzionalità supportate per i moduli T-SQL compilati in modo nativo](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).  
  
 Per altre informazioni su costrutti non supportati, vedere [Costrutti Transact-SQL non supportati da OLTP in memoria](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
 Sono supportati gli elementi seguenti:  
  
-   [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)  
  
-   [DROP PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-procedure-transact-sql.md)  
  
-   [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md)  
  
-   [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md) e istruzioni INSERT SELECT  
  
-   SCHEMABINDING e BEGIN ATOMIC (obbligatori per le stored procedure compilate in modo nativo)  
  
     Per altre informazioni, vedere [Creazione di stored procedure compilate in modo nativo](../../relational-databases/in-memory-oltp/creating-natively-compiled-stored-procedures.md).  
  
-   NATIVE_COMPILATION  
  
     Per altre informazioni, vedere [Compilazione nativa di tabelle e stored procedure](../../relational-databases/in-memory-oltp/native-compilation-of-tables-and-stored-procedures.md).  
  
-   Parametri e variabili possono essere dichiarati come NOT NULL (disponibile solo per i moduli compilati in modo nativo: stored procedure compilate in modo nativo e funzioni scalari definite dall'utente compilate in modo nativo).  
  
-   Parametri con valori di tabella.  
  
     Per altre informazioni, vedere [Usare parametri con valori di tabella &#40;Motore di database&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
-   EXECUTE AS OWNER, SELF, CALLER e utente.  
  
-   Autorizzazioni GRANT e DENY per tabelle e procedure.  
  
     Per altre informazioni, vedere [GRANT - autorizzazioni per oggetti &#40;Transact-SQL&#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md) e [DENY - autorizzazioni per oggetti &#40;Transact-SQL&#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure compilate in modo nativo](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
