---
title: Proprietà - SQL Server Agent (scheda Accesso) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 01fc6329-5d6b-4186-9565-395f375477bb
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5d69d6f159e0e1597fdc6b59c0ba4aadf80b3748
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37234391"
---
# <a name="sql-server-agent-properties-log-on-tab"></a>Proprietà - SQL Server Agent (scheda Accesso)
  Utilizzare la scheda **Accesso** della finestra di dialogo **Proprietà SQL Server Agent** per specificare l'account utilizzato dal servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e per avviare e arrestare il servizio. La modifica della password di un account diventa effettiva immediatamente, senza dover riavviare il servizio.  
  
> [!NOTE]  
>  Quando si modifica il nome account utilizzato da un servizio in un'istanza cluster, il nuovo account deve essere membro del gruppo di dominio specificato durante l’installazione per il servizio in corso di modifica oppure è necessario disporre dell’autorizzazione per aggiungere membri a tale gruppo. Se non si dispone dell’autorizzazione per modificare l'appartenenza al gruppo, contattare l’amministratore di dominio.  
  
## <a name="options"></a>Opzioni  
 **Account di sistema locale**  
 Specificare un account di sistema locale che non richiede una password. Tuttavia, a seconda dei privilegi concessi, l'account di sistema locale può impedire le interazioni tra il servizio e gli altri server.  
  
 **Account seguente**  
 Specificare un account utente locale o di dominio che utilizza l’autenticazione di Windows. [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di utilizzare un account utente di dominio con diritti minimi. Per ulteriori informazioni sulla selezione di un account, vedere l'argomento "Impostazione di account di Windows per i servizi" nella documentazione online.  
  
 **Nome account**  
 Specificare il nome dell'account utente locale o di dominio.  
  
 **Password**  
 Digitare la password dell'account.  
  
 **Conferma password**  
 Digitare nuovamente la password dell'account.  
  
 **Start**  
 Avviare il servizio.  
  
 **Arresta**  
 Consente di arrestare il servizio.  
  
 **Sospendi**  
 Consente di sospendere il servizio.  
  
 **Riprendi**  
 Consente di riprendere un servizio sospeso.  
  
  
