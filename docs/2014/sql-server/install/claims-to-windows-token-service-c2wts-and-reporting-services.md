---
title: Claims nel servizio Token Windows (C2WTS) e Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- c2wts.exe.config
- SharePoint mode
- C2WTS
- WSS_WPG
ms.assetid: 4d380509-deed-4b4b-a9c1-a9134cc40641
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e3a44f0beff9bd3351265caca0ee9490a7c6aeeb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278187"
---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Attestazioni per il servizio token Windows (C2WTS) e Reporting Services
  Il componente attestazioni per il servizio Token Windows (c2WTS) è obbligatorio con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] modalità SharePoint, se si desidera utilizzare l'autenticazione di windows per origini dati all'esterno della farm di SharePoint. La condizione è valida anche se l'utente accede alla origini dati tramite l'autenticazione di Windows perché la comunicazione tra il server front-end Web e il servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] condiviso sarà sempre un'autenticazione delle attestazioni.  
  
 Il servizio c2WTS è necessario anche se l'origine dati si trova nello stesso computer del servizio condiviso, sebbene in questo scenario la delega vincolata non sia richiesta.  
  
 I token creati da c2WTS funzioneranno solo con la delega vincolata (vincoli a servizi specifici) e l'opzione di configurazione che prevede l'uso di qualsiasi protocollo di autenticazione. Come notato in precedenza, se le origini dati si trovano nello stesso computer del servizio condiviso, la delega vincolata non è necessaria.  
  
 Se l'ambiente utilizzerà la delega vincolata Kerberos, le origini dati esterne e il servizio SharePoint Server devono trovarsi nello stesso dominio Windows. Qualsiasi servizio basato su Attestazioni per il servizio token Windows (c2WTS) deve usare la delega **vincolata** Kerberos per consentire a c2WTS di usare la transizione del protocollo Kerberos per convertire le attestazioni in credenziali di Windows. Questi requisiti sono validi per tutti i servizi condivisi SharePoint. Per altre informazioni, vedere [panoramica dell'autenticazione Kerberos per prodotti Microsoft SharePoint 2010 (http://technet.microsoft.com/library/gg502594.aspx)](http://technet.microsoft.com/library/gg502594.aspx).  
  
 La procedura viene riepilogata in questo argomento.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
## <a name="prerequisites"></a>Prerequisiti  
  
> [!NOTE]  
>  Nota: alcuni passaggi della configurazione possono variare o potrebbero non funzionare in determinate topologie farm. Un'installazione in un server singolo, ad esempio, non supporta i servizi c2WTS di Windows Identity Foundation e di conseguenza gli scenari di delega di attestazioni per il servizio token Windows non sono possibili con questa configurazione della farm.  
  
### <a name="basic-steps-needed-to-configure-c2wts"></a>Passaggi di base necessari per configurare c2WTS  
  
1.  Configurare l'account del servizio c2WTS. Aggiungere l'account del servizio al gruppo Administrators locale in ogni server applicazioni in che esegue c2WTS. Verificare anche che l'account abbia i seguenti diritti sui criteri di sicurezza locali:  
  
    -   Agisci come parte del sistema operativo  
  
    -   Rappresenta un client dopo l'autenticazione  
  
    -   Accedi come servizio  
  
     Inoltre, l'account usato per c2WTS deve essere configurato per la delega vincolata con transizione di protocollo e necessita delle autorizzazioni per delegare ai servizi è necessario per comunicare con (ad esempio motore di SQL Server, SQL Server Analysis Services). Per configurare la delega è possibile utilizzare lo snap-in Active Directory Users e Computer.  
  
    1.  Fare clic con il pulsante destro del mouse su ogni account del servizio e aprire la finestra di dialogo delle proprietà. Nella finestra di dialogo fare clic sulla scheda **Delega** .  
  
        > [!NOTE]  
        >  Nota: la scheda relativa alla delega è visibile solo se l'oggetto dispone di un nome SPN assegnato. Sebbene c2WTS non richieda un nome SPN per il proprio account, senza tale nome la scheda **Delega** non sarà visibile. Un modo alternativo per configurare la delega vincolata consiste nell'impiego di un'utilità, ad esempio **ADSIEdit**.  
  
    2.  Di seguito vengono indicate le opzioni di configurazione principali nella scheda relativa alla delega:  
  
        -   Selezionare "Utente attendibile per la delega solo ai servizi specificati"  
  
        -   Selezionare "Utilizza un qualsiasi protocollo di autenticazione"  
  
         Per ulteriori informazioni, vedere la sezione sulla configurazione della delega vincolata Kerberos per computer e account del servizio del white paper relativo alla [configurazione dell'autenticazione Kerberos per prodotti SharePoint 2010 e SQL Server 2008 R2](http://blogs.technet.com/b/tothesharepoint/archive/2010/07/22/whitepaper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products.aspx)  
  
2.  Configurare i chiamanti consentiti per c2WTS  
  
     c2WTS richiede esplicitamente l'identità 'chiamanti' elencati nel file di configurazione **c2wtshost.exe.config**. c2WTS non accetta richieste da tutti gli utenti autenticati nel sistema a meno che non è configurato per eseguire questa operazione. In questo caso il chiamante è il gruppo di Windows WSS_WPG. Il file c2wtshost.exe.confi viene salvato nel percorso seguente:  
  
     **\Programmi\Windows identity Foundation\v3.5\c2wtshost.exe.config**  
  
     Di seguito viene illustrato un esempio del file di configurazione:  
  
    ```  
    <configuration>  
      <windowsTokenService>  
        <!--  
            By default no callers are allowed to use the Windows Identity Foundation Claims To NT Token Service.  
            Add the identities you wish to allow below.  
          -->  
        <allowedCallers>  
          <clear/>  
          <add value="WSS_WPG" />  
        </allowedCallers>  
      </windowsTokenService>  
    </configuration>  
    ```  
  
3.  Avviare il servizio c2WTS del sistema operativo:  
  
    1.  Configurare il servizio per utilizzare l'account servizio configurato nel passaggio precedente.  
  
    2.  Modificare il tipo di avvio in "**Automatico**", quindi avviare il servizio.  
  
4.  Avviare Attestazioni per il servizio token Windows di Share Point tramite Amministrazione centrale SharePoint nella pagina **Gestisci servizi nel server** . Il servizio deve essere avviato nel server che eseguirà l'azione. Ad esempio, in presenza di un front-end Web e di un server applicazioni in cui è in esecuzione il servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] condiviso, è sufficiente avviare c2WTS solo sul server applicazioni. c2WTS non è necessario nel front-end Web.  
  
## <a name="see-also"></a>Vedere anche  
 [Attestazioni per il servizio Token Windows (c2WTS) (panoramicahttp://msdn.microsoft.com/library/ee517278.aspx)](http://msdn.microsoft.com/library/ee517278.aspx)   
 [Panoramica dell'autenticazione Kerberos per prodotti Microsoft SharePoint 2010 (http://technet.microsoft.com/library/gg502594.aspx)](http://technet.microsoft.com/library/gg502594.aspx)  
  
  
