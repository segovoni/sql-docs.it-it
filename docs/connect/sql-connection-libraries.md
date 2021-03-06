---
title: Raccolte di connessioni per i database SQL di Microsoft | Documenti Microsoft
description: Fornisce i collegamenti ai download per i moduli che consentono la connessione a Microsoft SQL Server e Database SQL di Azure da una vasta gamma di linguaggi di programmazione client.
author: MightyPen
ms.suite: sql
ms.prod: sql
ms.prod_service: connectivity
ms.technology: dbe-data-tier-apps
ms.custom: ''
ms.topic: article
ms.date: 06/18/2018
ms.author: genemi
ms.openlocfilehash: b7d00ed25392e979cc0d5037bef6b7d8eccc66bf
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36246843"
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Moduli di connessione per i database SQL di Microsoft

Questo articolo fornisce collegamenti ai moduli di connessione per il download o *driver* che i programmi client possono utilizzare per l'interazione con [Microsoft SQL Server](../relational-databases/database-features.md)e con il relativo alla presenza nel cloud [Azure Database SQL](http://docs.microsoft.com/azure/sql-database/). Sono disponibili driver per una varietà di linguaggi di programmazione che eseguono sistemi operativi seguenti:

- Linux (Ubuntu)
- MacOS
- Windows

#### <a name="oop-to-relational-mismatch"></a>Mancata corrispondenza OOP-relational

*Relazionale*: i programmi Client che vengono scritti in un linguaggio (OOP) programmazione orientata agli oggetti spesso utilizzare i driver SQL che restituiscono dati sottoposti a query in un formato più relazionali rispetto orientata agli oggetti. Linguaggio c# tramite ADO.NET è un esempio. La mancata corrispondenza tra formato relazionale OOP talvolta rende il codice OOP più difficile la scrittura e la comprensione.

*ORM*: altri driver o Framework restituiscono dati sottoposti a query in formato OOP, evitando la mancata corrispondenza. Questi driver utilizzare, è previsto che le classi sono state definite in modo che corrisponda le colonne di dati delle tabelle SQL particolare. Il driver esegue quindi il *mapping relazionale a oggetti* ORM () per restituire i dati di query come un'istanza di una classe. Microsoft Entity Framework (EF) per c# e sospensione per Java, sono riportati due esempi.

Il presente articolo dedica sezioni separate per questi due tipi di driver di connessione.

<a name="anchor-20-drivers-relational-access" />

## <a name="drivers-for-relational-access"></a>Driver per un accesso relazionale


<!--
Each given Microsoft Download Center page should be enhanced
with a link to the next NEWER version page, on the day that the
original page is no longer the latest because the newer page is being added.
But this policy is not agreed on or observed,
putting the links in the following table at risk for being outdated.

PHP driver in Github.com also uses this FWLink:  http://go.microsoft.com/fwlink/?LinkID=518036 ,
although the FWLink is less precise than is http://github.com/Microsoft/msphpsql/tree/dev#install-unix .
-->

| Linguaggio | Scaricare il driver SQL |
| :------- | :---------------------- |
| C# | [ADO.NET](http://www.microsoft.com/net/download/)<br /><br />[.NET core, per Ubuntu Linux](https://www.microsoft.com/net/core#Ubuntu)<br />[.NET core, per MacOS](https://www.microsoft.com/net/core#macos)<br />[.NET core, per Windows](https://www.microsoft.com/net/core) |
| C++ | [ODBC](./odbc/download-odbc-driver-for-sql-server.md)<br /><br />[OLE DB](./oledb/download-oledb-driver-for-sql-server.md) |
| Java | [JDBC](./jdbc/download-microsoft-jdbc-driver-for-sql-server.md) |
| Node.js | [Driver di Node. js, le istruzioni di installazione](./node-js/step-1-configure-development-environment-for-node-js-development.md) |
| PHP | [PHP](./php/download-drivers-php-sql-server.md) |
| Python | [pyodbc, le istruzioni di installazione](./python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development.md)<br />[Scaricare ODBC](./odbc/download-odbc-driver-for-sql-server.md) |
| Ruby | [Driver Ruby, le istruzioni di installazione](./ruby/step-1-configure-development-environment-for-ruby-development.md)<br />[Pagina di download Ruby](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |

<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>Driver per l'accesso ORM


Nella tabella seguente sono elencati esempi di Framework relazionale Mapping ORM (Object) utilizzata dalle applicazioni client per connettersi ai database SQL di Microsoft.


| Linguaggio | Download del driver ORM |
| :------- | :------------------ |
| C# | [Entity Framework Core](http://docs.microsoft.com/ef/core/)<br />[Entity Framework (6 o versioni successive)](http://docs.microsoft.com/ef/) |
| Java | [Lo stato di ibernazione ORM](http://hibernate.org/orm)|
| PHP | [ORM intuitivo, inclusa in Laravel installazione](http://laravel.com/docs/) |
| Node.js | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | [Django](http://www.djangoproject.com/) |
| Ruby | [Ruby su Guide](http://rubyonrails.org/) |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Pagine di compilazione un'app Web
[http://aka.ms/sqldev](http://aka.ms/sqldev) Consente di accedere a un set di *compilazione un'app* pagine Web. Le pagine Web per informazioni sulle diverse combinazioni di programmazione Java, sistema operativo e driver di connessione SQL. Tra le informazioni contenute nelle pagine compilazione un'app Web sono i seguenti elementi:

- Informazioni dettagliate su come iniziare a fin dall'inizio, per ogni combinazione di lingua del sistema operativo + driver.
    - Istruzioni per installare i driver di connessione SQL più recenti.
- Esempi di codice per ognuno dei seguenti elementi:
    - Esempi di codice relazionale a oggetti.
    - Esempi di codice ORM.
    - Demo di indice ColumnStore per livello di prestazioni più veloce.

#### <a name="first-page-of-build-an-app-webpages"></a>Prima pagina, delle pagine di compilazione un'app Web
![Pagine di compilazione un'app Web, prima schermata della pagina][image-ref-163-buildanapp-webpages-first-page]

#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Menu per Java - Ubuntu, delle pagine di compilazione un'app Web
![Pagine di compilazione un'app Web, menu Ubuntu Java][image-ref-167-buildanapp-webpages-menu-java-ubuntu]

&nbsp;

## <a name="related-links"></a>Collegamenti correlati
- [Esempi di codice per la connessione al Database SQL di Azure nel cloud, con Java e altri linguaggi](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java).

<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
