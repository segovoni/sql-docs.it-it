---
title: Catalog. move_project (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: ef3b0325-d8e9-472b-bf11-7d3efa6312ff
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5b091ccea1f733ebbf6e52308d17c7bdb7449cbe
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogmoveproject---ssisdb-database"></a>Catalog. move_project - Database SSISDB
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene spostato un progetto da una cartella a un'altra all'interno del catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```tsql  
move_project [ @source_folder = ] source_folder  
    , [ @project_name = ] project_name  
    , [ @destination_folder = ] destination_folder  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @source_folder =] *source_folder*  
 Nome della cartella di origine, in cui si trova il progetto prima dello spostamento. Il *source_folder* è **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Nome del progetto che deve essere spostato. Il *project_name* è **nvarchar (128)**.  
  
 [ @destination_folder =] *destination_folder*  
 Nome della cartella di destinazione, in cui si trova il progetto dopo lo spostamento. Il *destination_folder* è **nvarchar (128)**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY sul progetto che si desidera spostare e autorizzazione CREATE_OBJECTS sulla cartella di destinazione  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono determinare la generazione di un errore da parte della stored procedure:  
  
-   Progetto inesistente  
  
-   Cartella di origine inesistente  
  
-   Cartella di destinazione inesistente o progetto con lo stesso nome già presente nella cartella di destinazione  
  
-   Utente senza autorizzazioni appropriate.  
  
## <a name="remarks"></a>Osservazioni  
 Quando un progetto viene spostato da una cartella di origine a una di destinazione, il progetto nella cartella di origine e i riferimenti all'ambiente corrispondenti vengono eliminati. Nella cartella di destinazione vengono creati un progetto e riferimenti all'ambiente identici. I riferimenti all'ambiente relativi verranno risolti in una cartella diversa dopo lo spostamento. I riferimenti assoluti verranno risolti nella stessa cartella dopo lo spostamento.  
  
> [!NOTE]  
>  Un progetto può disporre di riferimenti all'ambiente relativi o assoluti. I riferimenti relativi fanno riferimento all'ambiente in base al nome. Per tali riferimenti è necessario che l'ambiente si trovi nella stessa cartella del progetto. I riferimenti assoluti fanno riferimento all'ambiente in base al nome e alla cartella. Tali riferimenti fanno riferimento agli ambienti che si trovano in una cartella diversa da quella del progetto.  
  
  