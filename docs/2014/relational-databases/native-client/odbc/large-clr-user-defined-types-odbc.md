---
title: Tipi definiti dall'utente CLR di grandi dimensioni (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC, large user-defined types
- large user-defined types [ODBC]
ms.assetid: ddce337e-bb6e-4a30-b7cc-4969bb1520a9
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e7e17bf897c91021a06ebb5605b072f27aa624d3
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422360"
---
# <a name="large-clr-user-defined-types-odbc"></a>Tipi CLR definiti dall'utente di grandi dimensioni (ODBC)
  In questo argomento vengono illustrate le modifiche apportate a ODBC in SQL Server Native Client per supportare i tipi CLR (Common Language Runtime) definiti dall'utente (UDT) di grandi dimensioni.  
  
 Per un esempio che illustra il supporto ODBC per i tipi UDT CLR di grandi dimensioni, vedere [supporto per i tipi UDT di grandi dimensioni](../../native-client-odbc-how-to/support-for-large-udts.md).  
  
 Per altre informazioni sul supporto per i tipi UDT CLR di grandi dimensioni in SQL Server Native Client, vedere [Large CLR User-Defined tipi](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
## <a name="data-format"></a>Formato dati  
 SQL Server Native Client utilizza SQL_SS_LENGTH_UNLIMITED per indicare che le dimensioni di una colonna sono maggiori di 8.000 byte per i tipi LOB (Large Object). A partire da SQL Server 2008, lo stesso valore viene utilizzato per i tipi CLR definiti dall'utente quando le dimensioni sono maggiori di 8.000 byte.  
  
 I valori dei tipi definiti dall'utente vengono rappresentati come matrici di byte. Le conversioni da e verso le stringhe esadecimali sono supportate. I valori letterali vengono rappresentati come stringhe esadecimali con il prefisso "0x".  
  
 Nella tabella seguente viene illustrato il mapping dei tipi di dati nei parametri e nei set di risultati:  
  
|Tipo di dati di SQL Server|Tipo di dati SQL|valore|  
|--------------------------|-------------------|-----------|  
|tipo CLR definito dall'utente|SQL_SS_UDT|-151 (sqlncli.h)|  
  
 Nella tabella seguente vengono illustrati il tipo ODBC C e la struttura corrispondente. Essenzialmente, il tipo CLR definito dall'utente è un tipo `varbinary` con metadati aggiuntivi.  
  
|Tipo di dati SQL|Layout in memoria|Tipo di dati C|Valore (sqlext.h)|  
|-------------------|-------------------|-----------------|------------------------|  
|SQL_SS_UDT|SQLCHAR * (unsigned char \*)|SQL_C_BINARY|SQL_BINARY (-2)|  
  
## <a name="descriptor-fields-for-parameters"></a>Campi di descrizione per i parametri  
 Di seguito sono riportate le informazioni restituite nei campi IPD:  
  
|Campo di descrizione|SQL_SS_UDT<br /><br /> (lunghezza minore o uguale a 8.000 byte)|SQL_SS_UDT<br /><br /> (lunghezza maggiore di 8.000 byte)|  
|----------------------|-------------------------------------------------------------------|----------------------------------------------------------|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_SS_UDT|SQL_SS_UDT|  
|SQL_DESC_DATETIME_INTERVAL_CODE|0|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|*n*|SQL_SS_LENGTH_UNLIMITED (0)|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|*n*|SQL_SS_LENGTH_UNLIMITED (0)|  
|SQL_DESC_LOCAL_TYPE_NAME|"udt"|"udt"|  
|SQL_DESC_OCTET_LENGTH|*n*|SQL_SS_LENGTH_UNLIMITED (0)|  
|SQL_DESC_PRECISION|*n*|SQL_SS_LENGTH_UNLIMITED (0)|  
|SQL_DESC_SCALE|0|0|  
|SQL_DESC_TYPE|SQL_SS_UDT|SQL_SS_UDT|  
|SQL_DESC_TYPE_NAME|"udt"|"udt"|  
|SQL_DESC_UNSIGNED|SQL_TRUE|SQL_TRUE|  
|SQL_CA_SS_UDT_CATALOG_NAME|Nome del catalogo che contiene il tipo definito dall'utente.|Nome del catalogo che contiene il tipo definito dall'utente.|  
|SQL_CA_SS_UDT_SCHEMA_NAME|Nome dello schema che contiene il tipo definito dall'utente.|Nome dello schema che contiene il tipo definito dall'utente.|  
|SQL_CA_SS_UDT_TYPE_NAME|Nome del tipo definito dall'utente.|Nome del tipo definito dall'utente.|  
|SQL_CA_SS_UDT_ASSEMBLY_TYPE_NAME|Nome completo del tipo definito dall'utente.|Nome completo del tipo definito dall'utente.|  
  
 Per i parametri di tipo definito dall'utente SQL_CA_SS_UDT_TYPE_NAME deve sempre essere impostata tramite **SQLSetDescField**. SQL_CA_SS_UDT_CATALOG_NAME e SQL_CA_SS_UDT_SCHEMA_NAME sono facoltativi.  
  
 Se il tipo definito dall'utente viene definito nello stesso database con uno schema diverso rispetto alla tabella, è necessario impostare SQL_CA_SS_UDT_SCHEMA_NAME.  
  
 Se il tipo definito dall'utente viene definito in un database diverso rispetto alla tabella, è necessario impostare SQL_CA_SS_UDT_CATALOG_NAME e SQL_CA_SS_UDT_SCHEMA_NAME.  
  
 Se sono presenti errori o omissioni nelle impostazioni per SQL_CA_SS_UDT_TYPE_NAME, SQL_CA_SS_UDT_CATALOG_NAME o SQL_CA_SS_UDT_SCHEMA_NAME, viene generato un record di diagnostica con l'identificativo SQLSTATE HY000 e il testo del messaggio specifico del server.  
  
## <a name="descriptor-fields-for-results"></a>Campi di descrizione per i risultati  
 Di seguito sono riportate le informazioni restituite nei campi IRD:  
  
|Campo di descrizione|SQL_SS_UDT<br /><br /> (lunghezza minore o uguale a 8.000 byte)|SQL_SS_UDT<br /><br /> (lunghezza maggiore di 8.000 byte)|  
|----------------------|-------------------------------------------------------------------|----------------------------------------------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_SS_UDT|SQL_SS_UDT|  
|SQL_DESC_DATETIME_INTERVAL_CODE|0|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|*n*|SQL_SS_LENGTH_UNLIMITED (0)|  
|SQL_DESC_DISPLAY_SIZE|2*n*|SQL_SS_LENGTH_UNLIMITED (0)|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|*n*|SQL_SS_LENGTH_UNLIMITED (0)|  
|SQL_DESC_LITERAL_PREFIX|"0x"|"0x"|  
|SQL_DESC_LITERAL_SUFFIX|""|""|  
|SQL_DESC_LOCAL_TYPE_NAME|"udt"|"udt"|  
|SQL_DESC_OCTET_LENGTH|*n*|SQL_SS_LENGTH_UNLIMITED (0)|  
|SQL_DESC_PRECISION|*n*|SQL_SS_LENGTH_UNLIMITED (0)|  
|SQL_DESC_SCALE|0|0|  
|SQL_DESC_SEARCHABLE|SQL_PRED_NONE|SQL_PRED_NONE|  
|SQL_DESC_TYPE|SQL_SS_UDT|SQL_SS_UDT|  
|SQL_DESC_TYPE_NAME|"udt"|"udt"|  
|SQL_DESC_UNSIGNED|SQL_TRUE|SQL_TRUE|  
|SQL_CA_SS_UDT_CATALOG_NAME|Nome del catalogo che contiene il tipo definito dall'utente.|Nome del catalogo che contiene il tipo definito dall'utente.|  
|SQL_CA_SS_UDT_SCHEMA_NAME|Nome dello schema che contiene il tipo definito dall'utente.|Nome dello schema che contiene il tipo definito dall'utente.|  
|SQL_CA_SS_UDT_TYPE_NAME|Nome del tipo definito dall'utente.|Nome del tipo definito dall'utente.|  
|SQL_CA_SS_UDT_ASSEMBLY_TYPE_NAME|Nome completo del tipo definito dall'utente.|Nome completo del tipo definito dall'utente.|  
  
## <a name="column-metadata-returned-by-sqlcolumns-and-sqlprocedurecolumns-catalog-metadata"></a>Metadati della colonna restituiti da SQLColumns e SQLProcedureColumns (metadati del catalogo)  
 Per i tipi di dati definiti dall'utente vengono restituiti i valori di colonna seguenti:  
  
|Nome colonna|SQL_SS_UDT<br /><br /> (lunghezza minore o uguale a 8.000 byte)|SQL_SS_UDT<br /><br /> (lunghezza maggiore di 8.000 byte)|  
|-----------------|-------------------------------------------------------------------|----------------------------------------------------------|  
|DATA_TYPE|SQL_SS_UDT|SQL_SS_UDT|  
|TYPE_NAME|Nome del tipo definito dall'utente.|Nome del tipo definito dall'utente.|  
|COLUMN_SIZE|*n*|SQL_SS_LENGTH_UNLIMITED (0)|  
|BUFFER_LENGTH|*n*|SQL_SS_LENGTH_UNLIMITED (0)|  
|DECIMAL_DIGITS|NULL|NULL|  
|SQL_DATA_TYPE|SQL_SS_UDT|SQL_SS_UDT|  
|SQL_DATETIME_SUB|NULL|NULL|  
|CHAR_OCTET_LENGTH|*n*|SQL_SS_LENGTH_UNLIMITED (0)|  
|SS_UDT_CATALOG_NAME|Nome del catalogo che contiene il tipo definito dall'utente.|Nome del catalogo che contiene il tipo definito dall'utente.|  
|SS_UDT_SCHEMA_NAME|Nome dello schema che contiene il tipo definito dall'utente.|Nome dello schema che contiene il tipo definito dall'utente.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|Nome completo del tipo definito dall'utente.|Nome completo del tipo definito dall'utente.|  
  
 Le ultime tre colonne sono specifiche del driver. Vengono aggiunti dopo tutte le colonne definite da ODBC, ma prima di tutte le colonne specifiche del driver esistente del set di risultati di SQLColumns o SQLProcedureColumns.  
  
 Viene restituita alcuna riga da SQLGetTypeInfo, per singoli tipi definiti dall'utente o per il tipo generico "udt".  
  
## <a name="bindings-and-conversions"></a>Associazioni e conversioni  
 Di seguito sono riportate le conversioni supportate dai tipi di dati SQL ai tipi di dati C:  
  
|Conversione da e verso:|SQL_SS_UDT|  
|-----------------------------|------------------|  
|SQL_C_WCHAR|Supportato *|  
|SQL_C_BINARY|Supportato|  
|SQL_C_CHAR|Supportato *|  
  
 \* Dati binari vengono convertiti in una stringa esadecimale.  
  
 Di seguito sono riportate le conversioni supportate dai tipi di dati C ai tipi di dati SQL:  
  
|Conversione da e verso:|SQL_SS_UDT|  
|-----------------------------|------------------|  
|SQL_C_WCHAR|Supportato *|  
|SQL_C_BINARY|Supportato|  
|SQL_C_CHAR|Supportato *|  
  
 \* Si verifica la stringa esadecimale alla conversione di dati binari.  
  
## <a name="sqlvariant-support-for-udts"></a>Supporto di SQL_VARIANT per i tipi definiti dall'utente  
 I tipi definiti dall'utente non sono supportati nelle colonne SQL_VARIANT.  
  
## <a name="bcp-support-for-udts"></a>Supporto di BCP per i tipi definiti dall'utente  
 I valori dei tipi definiti dall'utente possono essere importati ed esportati solo come caratteri o valori binari.  
  
## <a name="downlevel-client-behavior-for-udts"></a>Comportamento dei client legacy per i tipi definiti dall'utente  
 I tipi definiti dall'utente sono soggetti al mapping dei tipi con i client legacy nel modo seguente:  
  
|Versione del server|SQL_SS_UDT<br /><br /> (lunghezza minore o uguale a 8.000 byte)|SQL_SS_UDT<br /><br /> (lunghezza maggiore di 8.000 byte)|  
|--------------------|-------------------------------------------------------------------|----------------------------------------------------------|  
|SQL Server 2005|`UDT`|`varbinary(max)`|  
|SQL Server 2008 e versioni successive|`UDT`|`UDT`|  
  
## <a name="odbc-functions-supporting-large-clr-udts"></a>Funzioni ODBC che supportano i tipi CLR definiti dall'utente di grandi dimensioni  
 In questa sezione vengono illustrate le modifiche apportate alle funzioni ODBC di SQL Server Native Client per supportare i tipi CLR definiti dall'utente di grandi dimensioni.  
  
### <a name="sqlbindcol"></a>SQLBindCol  
 I valori della colonna dei risultati dei tipi definiti dall'utente vengono convertiti dai tipi di dati SQL ai tipi di dati C come descritto nella sezione "Associazioni e conversioni" riportata in precedenza in questo argomento.  
  
### <a name="sqlbindparameter"></a>SQLBindParameter  
 I valori necessari per i tipi definiti dall'utente sono i seguenti:  
  
|Tipo di dati SQL|*ParameterType*|*ColumnSizePtr*|*DecimalDigitsPtr*|  
|-------------------|---------------------|---------------------|------------------------|  
|SQL_SS_UDT<br /><br /> (lunghezza minore o uguale a 8.000 byte)|SQL_SS_UDT|*n*|0|  
|SQL_SS_UDT<br /><br /> (lunghezza maggiore di 8.000 byte)|SQL_SS_UDT|SQL_SS_LENGTH_UNLIMITED (0)|0|  
  
### <a name="sqlcolattribute"></a>SQLColAttribute  
 I valori restituiti per i tipi definiti dall'utente sono uguali a quelli descritti nella sezione "Campi di descrizione per i risultati" riportata in precedenza in questo argomento.  
  
### <a name="sqlcolumns"></a>SQLColumns  
 I valori restituiti per i tipi definiti dall'utente sono uguali a quelli descritti nella sezione "Metadati della colonna restituiti da SQLColumns e SQLProcedureColumns (metadati del catalogo)" riportata in precedenza in questo argomento.  
  
### <a name="sqldescribecol"></a>SQLDescribeCol  
 I valori restituiti per i tipi definiti dall'utente sono i seguenti:  
  
|Tipo di dati SQL|*DataTypePtr*|*ColumnSizePtr*|*DecimalDigitsPtr*|  
|-------------------|-------------------|---------------------|------------------------|  
|SQL_SS_UDT<br /><br /> (lunghezza minore o uguale a 8.000 byte)|SQL_SS_UDT|*n*|0|  
|SQL_SS_UDT<br /><br /> (lunghezza maggiore di 8.000 byte)|SQL_SS_UDT|SQL_SS_LENGTH_UNLIMITED (0)|0|  
  
### <a name="sqldescribeparam"></a>SQLDescribeParam  
 I valori restituiti per i tipi definiti dall'utente sono i seguenti:  
  
|Tipo di dati SQL|*DataTypePtr*|*ColumnSizePtr*|*DecimalDigitsPtr*|  
|-------------------|-------------------|---------------------|------------------------|  
|SQL_SS_UDT<br /><br /> (lunghezza minore o uguale a 8.000 byte)|SQL_SS_UDT|*n*|0|  
|SQL_SS_UDT<br /><br /> (lunghezza maggiore di 8.000 byte)|SQL_SS_UDT|SQL_SS_LENGTH_UNLIMITED (0)|0|  
  
### <a name="sqlfetch"></a>SQLFetch  
 I valori della colonna dei risultati dei tipi definiti dall'utente vengono convertiti dai tipi di dati SQL ai tipi di dati C come descritto nella sezione "Associazioni e conversioni" riportata in precedenza in questo argomento.  
  
### <a name="sqlfetchscroll"></a>SQLFetchScroll  
 I valori della colonna dei risultati dei tipi definiti dall'utente vengono convertiti dai tipi di dati SQL ai tipi di dati C come descritto nella sezione "Associazioni e conversioni" riportata in precedenza in questo argomento.  
  
### <a name="sqlgetdata"></a>SQLGetData  
 I valori della colonna dei risultati dei tipi definiti dall'utente vengono convertiti dai tipi di dati SQL ai tipi di dati C come descritto nella sezione "Associazioni e conversioni" riportata in precedenza in questo argomento.  
  
### <a name="sqlgetdescfield"></a>SQLGetDescField  
 I campi di descrizione disponibili con i nuovi tipi sono descritti nelle sezioni "Campi di descrizione per i parametri" e "Campi di descrizione per i risultati" riportate in precedenza in questo argomento.  
  
### <a name="sqlgetdescrec"></a>SQLGetDescRec  
 I valori restituiti per i tipi definiti dall'utente sono i seguenti:  
  
|Tipo di dati SQL|Tipo|Sottotipo|Length|Precisione|Scala|  
|-------------------|----------|-------------|------------|---------------|-----------|  
|SQL_SS_UDT<br /><br /> (lunghezza minore o uguale a 8.000 byte)|SQL_SS_UDT|0|*n*|n|0|  
|SQL_SS_UDT<br /><br /> (lunghezza maggiore di 8.000 byte)|SQL_SS_UDT|0|SQL_SS_LENGTH_UNLIMITED (0)|SQL_SS_LENGTH_UNLIMITED (0)|0|  
  
### <a name="sqlgettypeinfo"></a>SQLGetTypeInfo  
 I valori restituiti per i tipi definiti dall'utente sono uguali a quelli descritti nella sezione "Metadati della colonna restituiti da SQLColumns e SQLProcedureColumns (metadati del catalogo)" riportata in precedenza in questo argomento.  
  
### <a name="sqlprocedurecolumns"></a>SQLProcedureColumns  
 I valori restituiti per i tipi definiti dall'utente sono uguali a quelli descritti nella sezione "Metadati della colonna restituiti da SQLColumns e SQLProcedureColumns (metadati del catalogo)" riportata in precedenza in questo argomento.  
  
### <a name="sqlputdata"></a>SQLPutData  
 I valori dei parametri dei tipi definiti dall'utente vengono convertiti dai tipi di dati C ai tipi di dati SQL come descritto nella sezione "Associazioni e conversioni" riportata in precedenza in questo argomento.  
  
### <a name="sqlsetdescfield"></a>SQLSetDescField  
 I campi di descrizione disponibili con i nuovi tipi sono descritti nelle sezioni "Campi di descrizione per i parametri" e "Campi di descrizione per i risultati" riportate in precedenza in questo argomento.  
  
### <a name="sqlsetdescrec"></a>SQLSetDescRec  
 I valori consentiti per i tipi definiti dall'utente sono i seguenti:  
  
|Tipo di dati SQL|Tipo|Sottotipo|Length|Precisione|Scala|  
|-------------------|----------|-------------|------------|---------------|-----------|  
|SQL_SS_UDT<br /><br /> (lunghezza minore o uguale a 8.000 byte)|SQL_SS_UDT|0|*n*|*n*|0|  
|SQL_SS_UDT<br /><br /> (lunghezza maggiore di 8.000 byte)|SQL_SS_UDT|0|SQL_SS_LENGTH_UNLIMITED (0)|SQL_SS_LENGTH_UNLIMITED (0)|0|  
  
### <a name="sqlspecialcolumns"></a>SQLSpecialColumns  
 I valori restituiti per i tipi di dati definiti dall'utente delle colonne DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH e DECIMAL_DIGTS sono uguali a quelli descritti nella sezione "Metadati della colonna restituiti da SQLColumns e SQLProcedureColumns (metadati del catalogo)" riportata in precedenza in questo argomento.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi CLR definiti dall'utente di grandi dimensioni](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
