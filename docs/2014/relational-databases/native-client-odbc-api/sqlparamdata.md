---
title: SQLParamData | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 710dd24d49507ff9065315631fcca95b7077e458
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415100"
---
# <a name="sqlparamdata"></a>SQLParamData
  Quando la funzione SQLParamData restituisce il *ValuePtrPtr* associato a un parametro con valori di tabella, l'applicazione deve chiamare con SQLPutData *StrLen_Or_Ind*. Se *StrLen_Or_Ind* ha un valore maggiore di 0, significa che l'applicazione è pronta per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client raccolga dati dei parametri per la successiva riga di parametro con valori di tabella. Se *StrLen_Or_Ind* ha un valore pari a 0, significa che non sono presenti altre righe di dati per il parametro con valori di tabella. Per altre informazioni, vedere [valori di colonna e parametri Data Transfer of Table-Valued e associazione](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Per altre informazioni sui parametri con valori di tabella, vedere [parametri con valori di tabella &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=80706)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  
