---
title: Modifiche del comportamento di SQL Server Reporting Services in SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- rows [Reporting Services], heights
- leading blanks
- installing Reporting Services, behavior changes with release
- cryptography [Reporting Services]
- Setup [Reporting Services], behavior changes with release
- DefaultValueQueryBased property
- encryption [Reporting Services]
- decryption [Reporting Services]
- blank characters [SQL Server]
- initializing installations [Reporting Services]
- behavior changes [Reporting Services]
ms.assetid: 2a767f0f-84f2-4099-8784-1e37790f858e
caps.latest.revision: 63
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 440066046c13629409eb4c2d332d4543ccd07c57
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37216951"
---
# <a name="behavior-changes-to-sql-server-reporting-services--in-sql-server-2014"></a>Modifiche del comportamento di SQL Server Reporting Services in SQL Server 2014
  In questo argomento vengono descritte le modifiche nel funzionamento introdotte in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Queste modifiche influiscono sulla modalità di utilizzo o di interazione delle funzionalità di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] rispetto alle versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Contenuto dell'argomento:  
  
-   [Modifiche di comportamento SQL Server 2014 Reporting Services](#bkmk_sql14)  
  
-   [Modifiche del comportamento di SQL Server 2012 Reporting Services](#bkmk_rc0)  
  
-   [Modifiche del comportamento di SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Modifiche al comportamento di Reporting Services  
 Esistono nessun [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] modifiche del comportamento [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Modifiche al comportamento di Reporting Services  
 In questa sezione vengono descritte le modifiche di comportamento apportate alla modalità SharePoint di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
### <a name="view-items-permission-will-not-download-shared-datasets-sharepoint-mode"></a>Impossibile scaricare set di dati condivisi (modalità SharePoint) mediante l'autorizzazione Visualizzazione elementi  
 **Nuovo comportamento** . Gli utenti con l'autorizzazione di SharePoint "Visualizzazione elementi" non possono più scaricare il contenuto dei set di dati condivisi di Reporting Services. Questa modifica di comportamento è coerente con le autorizzazioni "Visualizzazione elementi" per report, origini dati e modelli. Gli utenti che dispongono di questa autorizzazione possono visualizzare ed eseguire report, origini dati e modelli, ma non possono scaricare il relativo contenuto.  
  
 **Comportamento precedente** . Gli utenti con l'autorizzazione di SharePoint "Visualizzazione elementi" non potevano scaricare il contenuto dei set di dati condivisi di Reporting Services.  
  
 Per ulteriori informazioni sui livelli di autorizzazione di SharePoint, vedere [Autorizzazioni utente e livelli di autorizzazione](http://technet.microsoft.com/library/cc721640.aspx).  
  
### <a name="report-server-trace-logs-are-in-a-new-location-for-sharepoint-mode-sharepoint-mode"></a>Nuovo percorso dei log di traccia del server di report per la modalità SharePoint (modalità SharePoint)  
 **Nuovo comportamento** . Per un server di report installato in modalità SharePoint, i relativi log di traccia si trovano in %Programmi%\Common Files\Microsoft Shared\Web Server Extensions\14\Web Services\ReportServer\LogFiles.  
  
 **Comportamento precedente:** log di traccia di Server di Report sono stati trovati in un percorso analogo al seguente: %Programfilesdir%\Microsoft SQL Server\\< RS_instance > Services\LogFiles.  
  
### <a name="getserverconfiginfo-soap-api-is-no-longer-supported-sharepoint-mode"></a>API SOAP GetServerConfigInfo non più supportata (modalità SharePoint)  
 **Nuovo comportamento**. Utilizzare il cmdlet di PowerShell "Get-SPRSServiceApplicationServers".  
  
 **Comportamento precedente:** i clienti potevano sviluppare codice client SOAP per comunicare direttamente con il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] punto finale e chiamare getreportserverconfiginfo ().  
  
### <a name="report-server-configuration-and-management-tools"></a>Strumenti di gestione e configurazione del server di report  
  
#### <a name="configuration-manager-is-not-used-for-sharepoint-mode"></a>Gestione configurazione non più utilizzato per la modalità SharePoint  
 **Nuovo comportamento:** il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager non supporta più server di report in modalità SharePoint. Configurazione di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] modalità SharePoint può essere completata tramite Amministrazione centrale SharePoint e pertanto [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager non supporta più modalità SharePoint. Gestione configurazione viene utilizzato solo per i server di report in modalità nativa.  
  
#### <a name="you-cannot-change-the-server-from-one-mode-to-another"></a>Impossibile modificare il server da una modalità a un'altra  
 **Nuovo comportamento** . Non è possibile modificare le modalità server. Se si installa un server di report con il supporto della modalità nativa, non sarà possibile modificare o configurare nuovamente questo server affinché sia in modalità SharePoint. Se l'installazione viene eseguita in modalità SharePoint, è possibile impostare il server di report sulla modalità nativa.  
  
 **Comportamento precedente:** cliente installa un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] server di report in modalità SharePoint. Per passare il server di report alla modalità nativa, poteva aprire Gestione configurazione [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] per eseguire questo passaggio creando una nuova connessione al database in modalità nativa o utilizzando una esistente. Il cliente poteva inoltre utilizzare [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager di passare dalla modalità SharePoint alla modalità nativa.  
  
##  <a name="bkmk_kj"></a> Modifiche del comportamento di SQL Server 2008 R2 Reporting Services  
 In questa sezione vengono descritte le modifiche di comportamento nel [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Poiché SQL Server 2008 R2 è un aggiornamento secondario della versione di SQL Server 2008, è consigliabile rivedere anche il contenuto nella sezione relativa a SQL Server 2008.  
  
### <a name="secureconnectionlevel-property-in-the-reporting-services-wmi-provider-library"></a>Proprietà SecureConnectionLevel nella libreria del provider WMI per Reporting Services  
 Nella libreria del provider WMI per [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], il **SecureConnectionLevel** proprietà ammette i valori di `0`,`1`,`2`,`3`, con `0` che indica che Secure Socket Layer (SSL) non è necessario per uno qualsiasi dei metodi del servizio Web `3` che indica che SSL è obbligatorio per tutti i metodi del servizio Web, e `1` e `2` indicare subset di metodi del servizio Web che richiedono SSL. Nelle [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], questi valori sono associati solo due possibili significati:  
  
-   `0` indica che il protocollo SSL non è necessario per alcun metodo del servizio Web.  
  
-   Un valore intero positivo indica che il protocollo SSL è obbligatorio per tutti i metodi del servizio Web.  
  
 Questa modifica influisce sulle modalità di risposta del server di report alle chiamate del servizio Web. Ad esempio, <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> attualmente restituito alcun valore se **SecureConnectionLevel** è impostata su 0 e tutti i metodi <xref:ReportService2005.ReportingService2005> se **SecureConnectionLevel** è impostata su `1`, `2`, o `3`.  
  
## <a name="see-also"></a>Vedere anche  
 [Novità &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Funzionalità deprecate in SQL Server Reporting Services in SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [Funzionalità non più disponibili di SQL Server Reporting Services in SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)   
 [Modifiche di rilievo di SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)  
  
  
