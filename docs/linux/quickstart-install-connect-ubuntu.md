---
title: Introduzione a SQL Server 2017 su Ubuntu | Microsoft Docs
description: Questa Guida introduttiva illustra come installare SQL Server 2017 in Ubuntu e quindi creare ed eseguire query di un database con sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.openlocfilehash: 30c05b25301004afbd1d9ed0b2a365b5a37f256d
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101823"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-ubuntu"></a>Guida introduttiva: Installare SQL Server e creare un database in Ubuntu

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questa Guida introduttiva, è prima di tutto installare SQL Server 2017 su Ubuntu 16.04. Ci si connette quindi con **sqlcmd** per creare il primo database ed eseguire query.

> [!TIP]
> Questa esercitazione richiede l'input dell'utente e una connessione a internet. Se è interessati al [automatica](sql-server-linux-setup.md#unattended) oppure [offline](sql-server-linux-setup.md#offline) procedure di installazione, vedere [informazioni aggiuntive sull'installazione per SQL Server in Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Prerequisiti

È necessario disporre di un computer con Ubuntu 16.04 **almeno 2 GB** di memoria.

Per installare Ubuntu nel proprio computer, visitare [ http://www.ubuntu.com/download/server ](http://www.ubuntu.com/download/server). È anche possibile creare macchine virtuali Ubuntu in Azure. Visualizzare [creare e gestire VM Linux con l'interfaccia della riga di comando Azure](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm).

> [!NOTE]
> A questo punto, il [sottosistema Windows per Linux](https://msdn.microsoft.com/commandline/wsl/about) per Windows 10 non è supportato come destinazione di installazione.

Per altri requisiti di sistema, vedere [requisiti di sistema per SQL Server in Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Installare SQL Server

Per configurare SQL Server in Ubuntu, eseguire i comandi seguenti in un terminale per installare il **mssql-server** pacchetto.

> [!IMPORTANT]
> Se è stato precedentemente installato una versione CTP o RC di SQL Server 2017, è necessario rimuovere prima il repository precedente prima di registrare uno dei repository GA. Per altre informazioni, vedere [modificare i repository dal repository di anteprima per il repository GA](sql-server-linux-change-repo.md).

1. Importare le chiavi GPG repository pubblico:

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Registrare il repository di Microsoft SQL Server Ubuntu:

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

   > [!NOTE]
   > Questo è il repository di aggiornamenti cumulativi (CU). Per altre informazioni sulle opzioni di repository e le relative differenze, vedere [configurare i repository per SQL Server in Linux](sql-server-linux-change-repo.md).

1. Eseguire i comandi seguenti per installare SQL Server:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

1. Dopo il completamento dell'installazione del pacchetto, eseguire **mssql-conf setup** e seguire le istruzioni per impostare la password account SA e scegliere l'edizione.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Se si tenta di SQL Server 2017 in questa esercitazione, sono liberamente concessi in licenza seguenti edizioni: Evaluation, Developer ed Express.

   > [!NOTE]
   > Assicurarsi di specificare una password complessa per l'account SA (caratteri di lunghezza 8 minimo, incluse le lettere maiuscole e lettere minuscole, cifre in base 10 e/o i simboli non alfanumerici).

1. Al termine della configurazione, verificare che il servizio sia in esecuzione:

   ```bash
   systemctl status mssql-server
   ```

1. Se si prevede di connettersi in remoto, si potrebbe essere necessario anche aprire la porta TCP di SQL Server (valore predefinito 1433) nel firewall.

A questo punto, SQL Server è in esecuzione nel computer Ubuntu ed è pronto per l'uso.

## <a id="tools"></a>Installare gli strumenti da riga di comando di SQL Server

Per creare un database, è necessario connettersi con uno strumento che è possibile eseguire istruzioni Transact-SQL in SQL Server. La procedura seguente installa gli strumenti da riga di comando di SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) e [bcp](../tools/bcp-utility.md).

Usare la procedura seguente per installare il **mssql-tools** in Ubuntu. 

1. Importare le chiavi GPG repository pubblico.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Registrare il repository Microsoft Ubuntu.

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. Aggiornare l'elenco delle origini ed eseguire il comando di installazione con il pacchetto di sviluppo unixODBC.

   ```bash
   sudo apt-get update 
   sudo apt-get install mssql-tools unixodbc-dev
   ```

   > [!Note] 
   > Eseguire l'aggiornamento alla versione più recente di **mssql-tools** eseguire i comandi seguenti:
   >    ```bash
   >   sudo apt-get update 
   >   sudo apt-get install mssql-tools 
   >   ```

1. **Facoltativo**: aggiungere `/opt/mssql-tools/bin/` per il **percorso** variabile di ambiente in una shell bash.

   Per rendere **sqlcmd/bcp** accessibile da shell di bash per sessioni di accesso, modificare le **PATH** nel **~/.bash_profile** file con il comando seguente:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Per rendere **sqlcmd/bcp** accessibile da shell di bash per le sessioni interattive/senza accesso, modificare il **PATH** nel **~/.bashrc** file con il comando seguente:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
