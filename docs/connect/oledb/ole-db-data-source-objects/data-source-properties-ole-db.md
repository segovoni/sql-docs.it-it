---
title: Proprietà (OLE DB) dell'origine dati | Documenti Microsoft
description: Proprietà dell'origine dati (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- OLE DB data source properties [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 1b426d49bd6a37167c16889f1e17c27ee72531c0
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2018
ms.locfileid: "35665501"
---
# <a name="data-source-properties-ole-db"></a>Proprietà delle origini dati (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server implementa proprietà origine dati come indicato di seguito.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|DBPROP_CURRENTCATALOG|L/S: Lettura/scrittura Impostazione predefinita: Nessuna<br /><br /> Descrizione: Il valore di DBPROP_CURRENTCATALOG indica il database corrente per un Driver OLE DB per la sessione di SQL Server. Impostando il valore della proprietà ha l'effetto identico come impostazione del database corrente utilizzando il [!INCLUDE[tsql](../../../includes/tsql-md.md)] utilizzare *database* istruzione.<br /><br /> A partire da [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], se si chiama [sp_defaultdb](../../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md) e specificare il nome del database in caratteri minuscoli, anche se il database è stato creato con un nome di case misto, DBPROP_CURRENTCATALOG restituirà il nome in minuscolo. Con le versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], DBPROP_CURRENTCATALOG restituisce invece la combinazione di maiuscole e minuscole prevista.|  
|DBPROP_MULTIPLECONNECTIONS|L/S: Lettura/scrittura Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: Se la connessione esegue un comando che non produce un set di righe o produce un set di righe che non è un cursore server e si esegue un altro comando, verrà creata una nuova connessione per eseguire il nuovo comando se DBPROP_MULTIPLECONNECTIONS è VARIANT_TRUE.<br /><br /> Il Driver OLE DB per SQL Server non creerà un'altra connessione se DBPROP_MULTIPLECONNECTION è VARIANT_FALSE o se una transazione è attiva nella connessione. Il Driver OLE DB per SQL Server restituisce DB_E_OBJECTOPEN se DBPROP_MULTIPLECONNECTIONS è VARIANT_FALSE e restituisce E_FAIL se è presente una transazione attiva. Le transazioni e il blocco vengono gestiti da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per singola connessione. Se viene generata una seconda connessione, i comandi sulle connessioni separate non condividono blocchi. Per assicurarsi che un comando non blocchi un altro comando, mantenere attivi i blocchi sulle righe richieste da quest'ultimo. Ciò vale anche nel caso di creazione di più sessioni.<br /><br /> Ogni sessione ha una connessione separata.|  
  
 Nel set di proprietà specifiche del provider DBPROPSET_SQLSERVERDATASOURCE, il Driver OLE DB per SQL Server definisce le proprietà dell'origine dati aggiuntivi seguenti.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|SSPROP_ENABLEFASTLOAD|L/S: Lettura/scrittura Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: Per abilitare la copia bulk dalla memoria, la proprietà SSPROP_ENABLEFASTLOAD deve essere impostata su VARIANT_TRUE. Con questa proprietà è impostata sull'origine dati, la sessione appena creata consente consumer di accedere al [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md) interfaccia.<br /><br /> Se la proprietà è impostata su VARIANT_TRUE, **IRowsetFastLoad** interfaccia è disponibile tramite **IOpenRowset:: OPENROWSET** richiedendo il **IID_IRowsetFastLoad** interfaccia oppure impostando **SSPROP_IRowsetFastLoad** su VARIANT_TRUE.|  
|SSPROP_ENABLEBULKCOPY|L/S: Lettura/scrittura Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: Per abilitare la copia bulk dai file, la proprietà SSPROP_ENABLEBULKCOPY deve essere impostata su VARIANT_TRUE. Se questa proprietà è impostata sull'origine dati, l'accesso del consumer all'interfaccia IBCPSession è disponibile allo stesso livello delle sessioni.<br /><br /> Anche SSPROP_IRowsetFastLoad deve essere impostato su VARIANT_TRUE.|  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti origine dati &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
