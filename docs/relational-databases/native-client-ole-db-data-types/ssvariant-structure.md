---
title: Struttura SSVARIANT | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5d45c3b54eb6b5e09c00ea94cfef924b3c94fa70
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420480"
---
# <a name="ssvariant-structure"></a>Struttura SSVARIANT
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il **SSVARIANT** struttura, a cui è definita in SQLNCLI. h, corrisponde a un valore DBTYPE_SQLVARIANT nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB di Native Client.  
  
 **SSVARIANT** è un'unione discriminante. A seconda del valore del membro vt, il consumer può determinare il membro da leggere. i valori VT corrispondono a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i tipi di dati. Pertanto, il **SSVARIANT** struttura può contenere qualsiasi tipo di SQL Server. Per altre informazioni sulla struttura dei dati per i tipi OLE DB standard, vedere [indicatori di tipo](http://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Note  
 Quando Datatypecompat==80 = = 80, vari **SSVARIANT** sottotipi diventano stringhe. Ad esempio, i valori vt seguenti verranno visualizzato nella **SSVARIANT** come VT_SS_WVARSTRING:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Quando DateTypeCompat == 0, questi tipi vengono visualizzati nel formato nativo.  
  
 Per altre informazioni su SSPROP_INIT_DATATYPECOMPATIBILITY, vedere [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Il file SQLNCLI. h contiene macro di accesso di tipo variant che semplificano la dereferenziazione di tipi di membri nella **SSVARIANT** struttura. Un esempio è rappresentato da V_SS_DATETIMEOFFSET, che è possibile utilizzare come indicato di seguito:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Per il set completo di macro di accesso per ogni membro del **SSVARIANT** struttura, fare riferimento al file Hi.  
  
 Nella tabella seguente vengono descritti i membri del **SSVARIANT** struttura:  
  
|Membro|Indicatore del tipo OLE DB|Tipo di dati C di OLE DB|valore vt|Commenti|  
|------------|---------------------------|------------------------|--------------|--------------|  
|VT|SSVARTYPE|||Specifica il tipo di valore contenuto nella **SSVARIANT** struct.|  
|bTinyIntVal|DBTYPE_UI1|**BYTE**|**VT_SS_UI1**|Supporta il **tinyint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|sShortIntVal|DBTYPE_I2|**BREVE**|**VT_SS_I2**|Supporta il **smallint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|lIntVal|DBTYPE_I4|**LONG**|**VT_SS_I4**|Supporta il **int** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Supporta il **bigint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Supporta il **reali** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Supporta il **float** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Supporta il **denaro** e **smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i tipi di dati.|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Supporta il **bit** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|Supporta il **uniqueidentifier** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Supporta il **numerico** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Supporta il **data** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Supporta il **smalldatetime**, **datetime**, e **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i tipi di dati.|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Supporta il **tempo** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**BYTE**) consente di specificare il fattore di scala *tTime2Val* valore.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Supporta il **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**BYTE**) consente di specificare il fattore di scala *tsDataTimeVal* valore.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Supporta il **datetimeoffset** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**BYTE**) consente di specificare il fattore di scala *tsoDateTimeOffsetVal* valore.|  
|NCharVal|Nessun indicatore del tipo OLE DB corrispondente.|**struct _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Supporta il **nchar** e **nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i tipi di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *sActualLength* (**breve**) specifica la lunghezza effettiva per la stringa a cui *pwchNCharVal* punti. Non include lo zero finale.<br /><br /> *sMaxLength* (**breve**) specifica la lunghezza massima per la stringa a cui *pwchNCharVal* punti.<br /><br /> *pwchNCharVal* (**WCHAR** \*) puntatore alla stringa.<br /><br /> Membri non utilizzati: *rgbReserved*, *dwReserved*, e *pwchReserved*.|  
|CharVal|Nessun indicatore del tipo OLE DB corrispondente.|**struct _CharVal**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|Supporta il **char** e **varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i tipi di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *sActualLength* (**breve**) specifica la lunghezza effettiva per la stringa da cui *pchCharVal* punti. Non include lo zero finale.<br /><br /> *sMaxLength* (**breve**) specifica la lunghezza massima per la stringa da cui *pchCharVal* punti.<br /><br /> *pchCharVal* (**CHAR** \*) puntatore alla stringa.<br /><br /> Membri non utilizzati:<br /><br /> *rgbReserved*, *dwReserved*, e *pwchReserved*.|  
|BinaryVal|Nessun indicatore del tipo OLE DB corrispondente.|**struct _BinaryVal**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|Supporta il **binario** e **varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i tipi di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *sActualLength* (**breve**) specifica la lunghezza effettiva per i dati a cui *prgbBinaryVal* punti.<br /><br /> *sMaxLength* (**breve**) specifica la lunghezza massima per i dati a cui *prgbBinaryVal* punti.<br /><br /> *prgbBinaryVal* (**BYTE** \*) puntatore ai dati binari.<br /><br /> Membro non utilizzato: *dwReserved*.|  
|Tipo sconosciuto|UNUSED|UNUSED|UNUSED|UNUSED|  
|BLOBType|UNUSED|UNUSED|UNUSED|UNUSED|  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
