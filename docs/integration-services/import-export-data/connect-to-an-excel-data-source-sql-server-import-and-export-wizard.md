---
title: Connettersi a un'origine dati Excel (Importazione/Esportazione guidata SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/02/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 43fbaca0-36d8-4583-9056-af7010209b87
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cd8b3e57a6aa39fc5523a693d31d5d4e3c6a31d2
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35401283"
---
# <a name="connect-to-an-excel-data-source-sql-server-import-and-export-wizard"></a>Connettersi a un'origine dati Excel (Importazione/Esportazione guidata SQL Server)
Questo articolo illustra come connettersi a un'origine dati **Microsoft Excel** dalla pagina **Scelta origine dati** o **Scelta destinazione** dell'Importazione/Esportazione guidata di SQL Server.

La schermata seguente mostra una connessione di esempio a una cartella di lavoro di Microsoft Excel.

![Connessione di Excel](../../integration-services/import-export-data/media/excel-connection.png) 

Per connettersi ai file Excel, può essere necessario scaricare e installare file aggiuntivi. Per altre informazioni, vedere [Ottenere i file necessari per connettersi a Excel](../load-data-to-from-excel-with-ssis.md#files-you-need).

> [!IMPORTANT]
> Per informazioni dettagliate sulla connessione ai file di Excel e sulle limitazioni e i problemi noti per il caricamento di dati da o a file di Excel, vedere [Caricare i dati da o in Excel con SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md).

## <a name="options-to-specify"></a>Opzioni da specificare

> [!NOTE]
> Le opzioni di connessione per il provider di dati sono le stesse sia nel caso in cui Excel rappresenti l'origine sia nel caso in cui rappresenti la destinazione. Ovvero, le opzioni visualizzate sono le stesse in entrambe le pagine **Scelta origine dati** e **Scelta destinazione** della procedura guidata.

**Percorso file di Excel**  
 Specificare il percorso e il nome del file Excel. Ad esempio
-   Per un file nel computer locale, **C:\\MyData.xlsx**.
-   Per un file in una condivisione di rete, **\\\\Sales\\Database\\Northwind.xlsx**.

In alternativa, fare clic su **Sfoglia**.  
  
 **Sfoglia**  
 Consente di individuare il foglio di calcolo tramite la finestra di dialogo **Apri**.  

> [!NOTE]
> La procedura guidata non può aprire un file di Excel protetto da password.

 **Versione di Excel**  
Selezionare la versione di Excel usata dalla cartella di lavoro di origine o di destinazione.

**Nomi di colonna nella prima riga**  
Specificare se la prima riga di dati contiene nomi di colonna.
-   Se i dati non contengono nomi di colonna e si abilita questa opzione, la procedura guidata considera la prima riga dei dati di origine come nomi di colonna.
-   Se i dati contengono nomi di colonna e si disabilita questa opzione, la procedura guidata considera la riga dei nomi di colonna come prima riga di dati.

Se si specifica che i dati non contengono nomi di colonna, la procedura guidata usa F1, F2 e così via come intestazioni di colonna.

## <a name="i-dont-see-excel-in-the-list-of-data-sources"></a>Excel non è incluso nell'elenco delle origini dati
Se Excel non è incluso nell'elenco delle origini dati, controllare se è in esecuzione la procedura guidata a 64 bit. I provider per Excel e Access sono in genere a 32 bit e non sono visibili nella procedura guidata a 64 bit. Eseguire la procedura guidata a 32 bit.

> [!NOTE]
> Per usare la versione a 64 bit dell'Importazione/Esportazione guidata SQL Server, è necessario installare SQL Server. SQL Server Data Tools (SSDT) e SQL Server Management Studio (SSMS) sono applicazioni a 32 bit e installano solo i file a 32 bit, inclusa la versione a 32 bit della procedura guidata.

## <a name="see-also"></a>Vedere anche
[Caricare i dati da o in Excel con SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md)  
[Scelta origine dati](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Scelta destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)

