---
title: Funzione SQLRemoveDSNFromIni | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLRemoveDSNFromIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDSNFromIni
helpviewer_keywords:
- SQLRemoveDSNFromIni function [ODBC]
ms.assetid: bb2e8273-7b61-4113-bfc8-f7ccc607c811
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8acffa07dd34eab295884f348ed02e1749492c6a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32917496"
---
# <a name="sqlremovedsnfromini-function"></a>SQLRemoveDSNFromIni (funzione)
**Conformità**  
 Introdotta: versione ODBC 1.0  
  
 **Riepilogo**  
 **SQLRemoveDSNFromIni** rimuove un'origine dati dalle informazioni di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLRemoveDSNFromIni(  
     LPCSTR   lpszDSN);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszDSN*  
 [Input] Nome dell'origine dati da rimuovere.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se rimuove l'origine dati o l'origine dati non è presente nel file Odbc.ini. Restituisce FALSE se non è possibile rimuovere l'origine dati.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLRemoveDSNFromIni** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_INVALID_DSN|DSN non valido.|Il *lpszDSN* argomento non valido.|  
|ODBC_ERROR_REQUEST_FAILED|Richiesta non riuscita|Il programma di installazione: Impossibile rimuovere le informazioni DSN dal Registro di sistema.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 **SQLRemoveDSNFromIni** rimuove il nome dell'origine dati dalla sezione [origini dati ODBC] le informazioni di sistema. Rimuove inoltre la sezione specifica di origine dati dalle informazioni di sistema.  
  
 Questa funzione deve essere chiamata solo da una libreria di programma di installazione di driver.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Aggiunta, modifica o rimozione di un'origine dati|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Aggiunta, modifica o rimozione di un'origine dati|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Rimuovendo l'origine dati predefinito|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Aggiunta di un nome di origine dati per le informazioni di sistema|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
