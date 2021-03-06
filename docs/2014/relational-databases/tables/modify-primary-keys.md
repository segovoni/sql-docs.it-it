---
title: Modificare chiavi primarie | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying primary keys
- primary keys [SQL Server], modifying
ms.assetid: 8e2a15ba-1cd1-4408-b860-16c3ee37d635
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3e0907ed53de354f6515c3ebc3910beb7a7200f8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175768"
---
# <a name="modify-primary-keys"></a>Modifica di chiavi primarie
  È possibile modificare chiave primaria in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. È possibile modificare la chiave primaria di una tabella modificando l'ordine della colonna, il nome dell'indice, l'opzione cluster o il fattore di riempimento.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per modificare una chiave primaria:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessario disporre dell'autorizzazione ALTER per la tabella.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-modify-a-primary-key"></a>Per modificare una chiave primaria  
  
1.  Aprire Progettazione tabelle per la tabella di cui modificare la chiave primaria, fare clic con il pulsante destro del mouse in Progettazione tabelle e scegliere **Indici/chiavi** dal menu di scelta rapida.  
  
2.  Nella finestra di dialogo **Indici/chiavi** selezionare l'indice di chiave primaria dall'elenco **Indice o chiave primaria/univoca** .  
  
3.  Completare un'operazione dalla tabella seguente:  
  
    |Per|seguire le operazioni di seguito riportate|  
    |--------|------------------------|  
    |Rinominare la chiave primaria|Digitare un nuovo nome nella casella **Nome** . Scegliere un nome che non sia ancora presente nell'elenco **Indice o chiave primaria/univoca** .|  
    |Impostare l'opzione cluster|Per creare un indice cluster per la chiave primaria, selezionare **Crea come CLUSTERED**, quindi selezionare l'opzione dall'elenco a discesa. Per ogni tabella è possibile creare un solo indice cluster. Se questa opzione non è disponibile per l'indice desiderato, deselezionare dapprima la relativa opzione sull'indice cluster esistente.<br /><br /> Se questa opzione non viene selezionata, viene creato un indice unico non cluster.|  
    |Definire un fattore di riempimento|Espandere la categoria **Specifica riempimento** e digitare un numero intero compreso tra 0 e 100 nella casella **Riempimento** . Per altre informazioni sui fattori di riempimento e sul loro uso, vedere [Specificare un fattore di riempimento per un indice](../indexes/specify-fill-factor-for-an-index.md).|  
    |Cambiare l'ordine delle colonne|Selezionare **Colonne**, quindi fare clic sui puntini di sospensione **(…)** a destra della proprietà. Nella finestra di dialogo  **Colonne indice** rimuovere le colonne dalla chiave primaria, quindi aggiungerle nuovamente nell'ordine desiderato. Per rimuovere una colonna dalla chiave, eliminare semplicemente il nome colonna dall'elenco **Nome colonna** .|  
  
4.  Scegliere **Salva***nome tabella* dal menu **File**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per modificare una chiave primaria**  
  
 Per modificare un vincolo PRIMARY KEY utilizzando Transact-SQL, è innanzitutto necessario eliminare il vincolo PRIMARY KEY esistente e quindi crearlo di nuovo con la nuova definizione. Per ulteriori informazioni, vedere [Delete Primary Keys](delete-primary-keys.md) e [Create Primary Keys](create-primary-keys.md).  
  
###  <a name="TsqlExample"></a>  
