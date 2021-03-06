---
title: Progettare diagrammi di database (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65536
- vdt.DatabaseDesigner
helpviewer_keywords:
- Database Diagram Designer
- Visual Database Tools [SQL Server], database diagrams
- database diagrams [SQL Server], designing
- diagrams [SQL Server], designing
ms.assetid: 6d2c14e1-3d73-4d10-ae5b-7f2b5d6c4ea8
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2b84ab228993294300fa02c65e76e562bea345c6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33050768"
---
# <a name="design-database-diagrams-visual-database-tools"></a>Progettare diagrammi di database (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Progettazione database è uno strumento grafico che consente di progettare e rappresentare graficamente un database a cui si è connessi. Quando si progetta un database, è possibile utilizzare Progettazione database per creare, modificare o eliminare tabelle, colonne, chiavi, indici, relazioni e vincoli. Per rappresentare graficamente un database, è possibile creare uno o più diagrammi che rappresentano alcune o tutte le tabelle, le colonne, le chiavi e le relazioni in esso contenute.  
  
![Diagramma di database che illustra le relazioni tra le tabelle](../../ssms/visual-db-tools/media/dv3w7c1.gif "Diagramma di database che illustra le relazioni tra le tabelle")  
  
Per qualsiasi database è possibile creare il numero desiderato di diagrammi di database. Ciascuna tabella di database può essere inserita in un numero qualsiasi di diagrammi. È quindi possibile creare diagrammi diversi per rappresentare parti diverse del database o per sottolineare aspetti diversi della progettazione. Ad esempio, è possibile creare un diagramma di grandi dimensioni che mostri tutte le tabelle e le colonne e un diagramma di dimensioni più ridotte che mostri tutte le tabelle senza le colonne.  
  
Ciascun diagramma di database creato viene archiviato nel database associato.  
  
## <a name="tables-and-columns-in-a-database-diagram"></a>Tabelle e colonne in un diagramma di database  
In un diagramma di database ogni tabella può presentarsi con tre caratteristiche distinte: una barra del titolo, un selettore di riga e un set di colonne delle proprietà.  
  
**Barra del titolo** La barra del titolo indica il nome della tabella  
  
Se una tabella è stata modificata ma non ancora salvata, alla fine del nome della tabella sarà presente un asterisco (*) per segnalare che le modifiche non sono state salvate. Per informazioni sul salvataggio di tabelle e diagrammi modificati, vedere [Usare i diagrammi di database &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
  
**Selettore di riga** Per selezionare una colonna del database nella tabella, è possibile fare clic sul selettore di riga. Se la colonna è inclusa nella chiave primaria della tabella, con il selettore di riga verrà visualizzato un simbolo di chiave. Per informazioni sulle chiavi primarie, vedere [Utilizzo di chiavi (Visual Database Tools)](http://msdn.microsoft.com/en-us/31fbcc9f-2dc5-4bf9-aa50-ed70ec7b5bcd).  
  
**Colonne delle proprietà** Il set di colonne delle proprietà è visibile solo in determinate viste della tabella. Per semplificare la gestione delle dimensioni e del layout del diagramma, è possibile visualizzare una tabella in cinque viste diverse.  
  
Per altre informazioni sulle viste delle tabelle, vedere [Personalizzazione della quantità di informazioni visualizzate nei diagrammi &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/customize-the-amount-of-information-displayed-in-diagrams-visual-database-tools.md).  
  
## <a name="relationships-in-a-database-diagram"></a>Relazioni in un diagramma di database  
In un diagramma di database ogni relazione può presentarsi con tre caratteristiche distinte: gli endpoint, lo stile linea e le tabelle correlate.  
  
**Endpoint** Gli endpoint della linea indicano se la relazione è di tipo uno-a-uno o uno-a-molti. Quando una relazione presenta una chiave su un endpoint e un simbolo di infinito sull'altro, rappresenta una relazione uno-a-molti. Quando una relazione presenta una chiave su ciascun endpoint, rappresenta una relazione uno-a-uno.  
  
**Stile linea** La linea stessa (non i relativi endpoint) indica se nel sistema di gestione del database (DBMS, Database Management System) viene attivata l'integrità referenziale per la relazione quando vengono aggiunti nuovi dati alla tabella chiave esterna. Se la linea è continua, nel sistema DBMS l'integrità referenziale per la relazione verrà attivata quando vengono aggiunte o modificate alcune righe nella tabella chiave esterna. Se la linea è tratteggiata, nel sistema DBMS l'integrità referenziale per la relazione non verrà attivata quando vengono aggiunte o modificate alcune righe nella tabella chiave esterna.  
  
**Tabelle correlate** La linea della relazione indica che esiste una relazione di chiave esterna fra due tabelle. Per una relazione uno-a-molti, la tabella chiave esterna è la tabella accanto al simbolo di infinito della linea. Se entrambi gli endpoint della linea sono collegati alla stessa tabella, la relazione sarà di tipo riflessivo. Per altre informazioni, vedere [Creazione di relazioni riflessive &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/draw-reflexive-relationships-visual-database-tools.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
[Informazioni sulla proprietà dei diagrammi di database &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/understand-database-diagram-ownership-visual-database-tools.md)  
  
[Navigare all'interno di Progettazione diagrammi di database &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/navigate-in-database-diagram-designer-visual-database-tools.md)  
  
[Impostazione di Progettazione diagrammi di database &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md)  
  
[Aggiornamento di diagrammi di database delle precedenti edizioni &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)  
  
[Apertura di Progettazione diagrammi di database &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/open-database-diagram-designer-visual-database-tools.md)  
  
## <a name="see-also"></a>Vedere anche  
[Utilizzare diagrammi di database &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[Utilizzo di tabelle in diagrammi di database &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/work-with-tables-in-database-diagram-visual-database-tools.md)  
[Utilizzare il layout di un diagramma &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/work-with-diagram-layout-visual-database-tools.md)  
  
