---
title: 'PDO:: rollback | Documenti Microsoft'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d918c1e3-1be0-4001-b3b0-000db6d9e8b8
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d21e1d96c2b891ae02ca747b22f1a1a96066f385
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35309020"
---
# <a name="pdorollback"></a>PDO::rollback
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Elimina i comandi di database che sono stati rilasciati dopo la chiamata a [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) e restituisce la connessione in modalità di commit automatico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDO::rollBack ();  
```  
  
## <a name="return-value"></a>Valore restituito  
true se la chiamata al metodo ha avuto esito positivo; in caso contrario, false.  
  
## <a name="remarks"></a>Remarks  
PDO::rollback non è influenzato e non influisce sul valore di PDO::ATTR_AUTOCOMMIT.  
  
Per un esempio d'uso di PDO::rollback, vedere [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) .  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
