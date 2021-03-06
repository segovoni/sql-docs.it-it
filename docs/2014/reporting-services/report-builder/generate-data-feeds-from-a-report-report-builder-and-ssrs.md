---
title: Generare i feed di dati da un report (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e68baae2-9f2a-4f13-9179-9ac7f29111c5
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 4ee1402202e08ab4ba718238b454f5eb4e548118
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37210831"
---
# <a name="generate-data-feeds-from-a-report-report-builder-and-ssrs"></a>Generare i feed di dati da un report (Generatore report e SSRS)
  È possibile generare feed di dati conformi ad Atom dai report e quindi usare i feed di dati nelle applicazioni, ad esempio la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] client, che può utilizzare feed di dati.  
  
 Tramite l'estensione per il rendering Atom di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] viene generato un documento di servizio Atom in cui sono elencati i feed di dati disponibili in un report. Nel documento è elencato almeno un feed di dati per ogni area dati nel report. A seconda del tipo di area dati e dei dati in essa visualizzati, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] potrebbe generare più feed di dati da un'area dati.  
  
 Nel documento di servizio Atom è contenuto un identificatore univoco per ogni feed di dati che può essere usato in un URL per visualizzare il contenuto del feed di dati.  
  
 Per altre informazioni, vedere [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-generate-an-atom-service-document"></a>Per generare un documento di servizio Atom  
  
1.  Dalla pagina Gestione report **Home**, accedere al report da cui si desidera generare feed di dati.  
  
2.  Fare clic sul report.  
  
     Il report verrà eseguito.  
  
3.  Nella barra degli strumenti fare clic sull'icona Esporta in feed di dati.  
  
     Verrà visualizzato un messaggio in cui si chiede se si desidera salvare o aprire il documento Atom contenente il feed di dati.  
  
4.  Fare clic su **Salva** per salvare il documento nel file system o su **Apri** per visualizzare il contenuto del documento prima del salvataggio. **Per impostazione predefinita, il documento viene visualizzato in un browser.**  
  
5.  Selezionare il percorso per salvare il documento.  
  
6.  Se lo si desidera, modificare il nome del documento.  
  
    > [!NOTE]  
    >  Per impostazione predefinita, il nome del documento corrisponde a quello del report.  
  
7.  Verificare che il tipo di documento sia **ATOMSVC**, quindi fare clic su **Salva**.  
  
8.  Se lo si desidera, aprire il file con estensione atomsvc in un browser, in un editor di testo o in un editor XML.  
  
### <a name="to-view-an-atom-compliant-data-feed"></a>Per visualizzare un feed di dati conforme ad Atom  
  
1.  Se il documento di servizio Atom non è già aperto, individuarlo e aprirlo in un browser quale Internet Explorer.  
  
2.  Copiare l'URL del feed dei dati che si desidera visualizzare dal documento di servizio Atom nel browser.  
  
     Il formato dell'URL è il seguente:  
  
 `http://<server name>/ReportServer?%2f<ReportName>rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=<Identifier>`  
  
1.  Premere INVIO.  
  
     Verrà visualizzato un messaggio in cui si chiede se si desidera salvare o aprire il documento Atom contenente il feed di dati.  
  
2.  Fare clic su **Salva** per salvare il documento nel file system o su **Apri** per visualizzare il feed di dati prima del salvataggio.  
  
3.  Selezionare il percorso per salvare il documento.  
  
4.  Se lo si desidera, modificare il nome del documento.  
  
    > [!NOTE]  
    >  Per impostazione predefinita, il nome del documento corrisponde a quello del report. Se il documento di servizio Atom dispone di più feed, per impostazione predefinita tutti presentano lo stesso nome ovvero il nome del report. Per differenziarli, rinominarli per usare nomi significativi.  
  
5.  Verificare che il tipo di documento sia **ATOM**, quindi fare clic su **Salva**.  
  
6.  Se lo si desidera, aprire il file con estensione atom in un browser, in un editor di testo o in un editor XML.  
  
## <a name="see-also"></a>Vedere anche  
 [Esportazione di report &#40;Report e SSRS&#41;](export-reports-report-builder-and-ssrs.md)  
  
  
