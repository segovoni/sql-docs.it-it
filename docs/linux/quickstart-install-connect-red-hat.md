---
title: Introduzione a SQL Server 2017 in Red Hat Enterprise Linux | Microsoft Docs
description: Questa Guida introduttiva illustra come installare SQL Server 2017 in Red Hat Enterprise Linux e quindi creare ed eseguire query di un database con sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.openlocfilehash: 4438184f6e14af1097ff05ea6e463f626025bb46
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103742"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-red-hat"></a>Guida introduttiva: Installare SQL Server e creare un database in Red Hat

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questa Guida introduttiva, è prima di tutto installare SQL Server 2017 su Red Hat Enterprise Linux (RHEL) 7.3 +. Ci si connette quindi con **sqlcmd** per creare il primo database ed eseguire query.

> [!TIP]
> Questa esercitazione richiede l'input dell'utente e una connessione a internet. Se è interessati al [automatica](sql-server-linux-setup.md#unattended) oppure [offline](sql-server-linux-setup.md#offline) procedure di installazione, vedere [informazioni aggiuntive sull'installazione per SQL Server in Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Prerequisiti

È necessario disporre una RHEL 7.3 o 7.4 macchina con **almeno 2 GB** di memoria.

Per installare Red Hat Enterprise Linux nel proprio computer, visitare [ http://access.redhat.com/products/red-hat-enterprise-linux/evaluation ](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation). È anche possibile creare macchine virtuali RHEL in Azure. Visualizzare [creare e gestire VM Linux con Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)e usare `--image RHEL` nella chiamata a `az vm create`.

Per altri requisiti di sistema, vedere [requisiti di sistema per SQL Server in Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Installare SQL Server

Per configurare SQL Server in RHEL, eseguire i comandi seguenti in un terminale per installare il **mssql-server** pacchetto:

> [!IMPORTANT]
> Se è stato precedentemente installato una versione CTP o RC di SQL Server 2017, è necessario rimuovere prima il repository precedente prima di registrare uno dei repository GA. Per altre informazioni, vedere [modificare i repository dal repository di anteprima per il repository GA](sql-server-linux-change-repo.md).

1. Scaricare il file di configurazione del repository di Microsoft SQL Server Red Hat:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!NOTE]
   > Questo è il repository di aggiornamenti cumulativi (CU). Per altre informazioni sulle opzioni di repository e le relative differenze, vedere [configurare i repository per SQL Server in Linux](sql-server-linux-change-repo.md).

1. Eseguire i comandi seguenti per installare SQL Server:

   ```bash
   sudo yum install -y mssql-server
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
   
1. Per consentire le connessioni remote, aprire la porta di SQL Server nel firewall in RHEL. La porta di SQL Server predefinita è TCP 1433. Se si usa **FirewallD** per firewall, è possibile usare i comandi seguenti:

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

A questo punto, SQL Server è in esecuzione nel computer RHEL ed è pronto per l'uso.

## <a id="tools"></a>Installare gli strumenti da riga di comando di SQL Server

Per creare un database, è necessario connettersi con uno strumento che è possibile eseguire istruzioni Transact-SQL in SQL Server. La procedura seguente installa gli strumenti da riga di comando di SQL Server: [sqlcmd](../tools/sqlcmd-utility.md) e [bcp](../tools/bcp-utility.md).

1. Scaricare il file di configurazione del repository Microsoft Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. Se si dispone di una versione precedente di **mssql-tools** installato, rimuovere eventuali pacchetti unixODBC meno recenti.

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Eseguire i comandi seguenti per installare **mssql-tools** con il pacchetto di sviluppo unixODBC.

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. Per praticità, aggiungere `/opt/mssql-tools/bin/` per il **percorso** variabile di ambiente. Ciò consente di eseguire gli strumenti senza specificare il percorso completo. Eseguire i comandi seguenti per modificare la **percorso** per sessioni di accesso e le sessioni interattive/senza accesso:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
