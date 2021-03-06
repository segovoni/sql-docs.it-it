---
title: Metodo getEncrypt (SQLServerDataSource) | Documenti Microsoft
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
- getEncrypt Method (SQLServerDataSource)
apilocation:
- getEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 1cdb12dd-6e6f-4bbd-8f5f-9e630f3ee2c9
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9262c2fb18160f5072d21a71c082bd00d17fc302
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32835006"
---
# <a name="getencrypt-method-sqlserverdatasource"></a>Metodo getEncrypt (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce un **booleano** valore che indica se la proprietà di crittografia è abilitata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean getEncypt()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se la crittografia è abilitata. In caso contrario, **false**.  
  
## <a name="remarks"></a>Osservazioni  
 Se la proprietà encrypt è impostata su **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] assicura che [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] utilizza la crittografia SSL per tutti i dati inviati tra il client e il server se il server è installato un certificato.  
  
 Se la proprietà di crittografia non viene specificata o impostata su **false**, il driver non imporrà la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] per supportare la crittografia SSL. Se il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] istanza non è configurata per forzare la crittografia SSL, viene stabilita una connessione senza crittografia. Se il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] istanza è configurata per forzare la crittografia SSL, il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] verrà automaticamente abilita la crittografia SSL quando eseguono correttamente configurato Java Virtual Machine (JVM), altrimenti la connessione viene terminata e il driver genera un errore. Se la proprietà di crittografia non è impostata, il [getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md) il metodo restituisce il valore predefinito di **false**.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
