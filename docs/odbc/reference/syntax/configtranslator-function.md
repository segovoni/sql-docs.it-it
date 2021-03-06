---
title: Funzione ConfigTranslator del | Documenti Microsoft
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
- ConfigTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigTranslator
helpviewer_keywords:
- ConfigTranslator [ODBC]
ms.assetid: 7c22f07e-36de-425b-aa67-e32a84afae92
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5b38bc6340ec456ce180eb2a9cc266d5b8a19305
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916396"
---
# <a name="configtranslator-function"></a>Funzione ConfigTranslator del
**Conformità**  
 Introdotta: versione ODBC 2.0  
  
 **Riepilogo**  
 **ConfigTranslator del** restituisce un'opzione di traduzione predefinita per una funzione di conversione. Può essere nella DLL la funzione di conversione o di una DLL di installazione separato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL ConfigTranslator(  
     HWND     hwndParent,  
     DWORD *  pvOption);  
```  
  
## <a name="arguments"></a>Argomenti  
 *hwndParent*  
 [Input] Handle della finestra padre. Se l'handle è null, la funzione non verrà visualizzata alcuna finestra di dialogo.  
  
 *pvOption*  
 [Output] Un'opzione di conversione a 32 bit.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **ConfigTranslator del** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore viene inserito nel buffer di errore del programma di installazione da una chiamata a **SQLPostInstallerError**e può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Handle di finestra non valido.|Il *hwndParent* argomento non valido o NULL.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Errore specifico del driver o funzione di conversione|Un errore specifico del driver per cui non è disponibile alcun errore di programma di installazione ODBC definita. Il *SzError* argomento in una chiamata al **SQLPostInstallerError** la funzione deve contenere il messaggio di errore specifico del driver.|  
|ODBC_ERROR_INVALID_OPTION|Opzione di conversione non valida|Il *pvOption* argomento è contenuto un valore non valido.|  
  
## <a name="comments"></a>Commenti  
 Se il convertitore supporta solo un'opzione di conversione singolo, **ConfigTranslator del** restituisce TRUE e imposta *pvOption* all'opzione di 32 bit. In caso contrario, determina l'opzione di conversione predefinita da utilizzare. **ConfigTranslator del** può visualizzare una finestra di dialogo con cui un utente seleziona un'opzione di conversione predefinita.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Recupero di un'opzione di conversione|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Selezione di una funzione di conversione|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|L'impostazione di un'opzione di conversione|[Funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
