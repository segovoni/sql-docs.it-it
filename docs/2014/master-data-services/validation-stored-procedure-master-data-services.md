---
title: Stored procedure di convalida (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 1eac3e49af2f5caa615a35f4a1d55f288a6fde28
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37170962"
---
# <a name="validation-stored-procedure-master-data-services"></a>Stored procedure di convalida (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]convalidare una versione per applicare le regole di business a tutti i membri nella versione del modello.  
  
 In questo argomento viene illustrato come usare la stored procedure **mdm.udpValidateModel** per convalidare i dati. Se si è un amministratore nell'applicazione Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , è possibile eseguire la convalida nell'interfaccia utente. Per altre informazioni, vedere [Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md).  
  
> [!NOTE]  
>  Se si richiama la convalida prima del completamento del processo di gestione temporanea, i membri che non hanno completato la gestione temporanea non saranno convalidati.  
  
## <a name="example"></a>Esempio  
  
```  
DECLARE @ModelName nVarchar(50) = 'Customer'   
DECLARE @Model_id int   
DECLARE @UserName nvarchar(50)= 'DOMAIN\user_name'   
DECLARE @User_ID int   
DECLARE @Version_ID int   
  
SET @User_ID = (SELECT ID    
                 FROM mdm.tblUser u   
                 WHERE u.UserName = @UserName)   
SET @Model_ID = (SELECT Top 1 Model_ID   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_Name = @ModelName)   
SET @Version_ID = (SELECT MAX(ID)   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_ID = @Model_ID)  
  
EXECUTE mdm.udpValidateModel @User_ID, @Model_ID, @Version_ID, 1  
  
```  
  
## <a name="parameters"></a>Parametri  
 I parametri di questa procedura sono i seguenti:  
  
|Parametro|Description|  
|---------------|-----------------|  
|UserID|L'ID utente.|  
|Model_ID|L'ID modello.|  
|Version_ID|L'ID versione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Importazione di dati &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [Convalidare una versione rispetto alle regole Business &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md)  
  
  
