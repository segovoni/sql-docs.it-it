---
title: Requisiti di sistema per il Driver JDBC | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 447792bb-f39b-49b4-9fd0-1ef4154c74ab
caps.latest.revision: 73
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 306c7bcd764ed70f23c51667580fb9f8e79f0e65
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34563949"
---
# <a name="system-requirements-for-the-jdbc-driver"></a>Requisiti di sistema per il driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Per accedere ai dati da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] utilizzando il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], sono necessari i seguenti componenti installati nel computer:

- [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ([scaricare](download-microsoft-jdbc-driver-for-sql-server.md))
- Java Runtime Environment

## <a name="java-runtime-environment-requirements"></a>Requisiti di Java Runtime Environment  
 A partire da 6.4 di Driver JDBC di Microsoft per SQL Server, sono supportati Sun Java SE Development Kit (JDK) 9.0 e Java Runtime Environment (JRE) 9.0.

 A partire da Microsoft JDBC Drivers 4.2 per SQL Server, sono supportati Sun Java SE Development Kit (JDK) 8.0 e Java Runtime Environment (JRE) 8.0. Il supporto per l'API della specifica Java Database Connectivity (JDBC) è stato esteso in modo da includere l'API di JDBC 4.1 e 4.2.  
  
 A partire da Microsoft JDBC Driver 4.1 per SQL Server, sono supportati Sun Java SE Development Kit (JDK) 7.0 e Java Runtime Environment (JRE) 7.0.  
  
 A partire dal [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], il supporto del driver JDBC per l'API della specifica Java Database Connectivity (JDBC) è stato esteso per includere l'API di JDBC 4.0. L'API di JDBC 4.0 è stata introdotta come parte di Sun Java SE Development Kit (JDK) 6.0 e Java Runtime Environment (JRE) 6.0. JDBC 4.0 è un superset dell'API di JDBC 3.0.  
  
 Quando si distribuisce il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] nei sistemi operativi Windows e UNIX, è necessario utilizzare i pacchetti di installazione *sqljdbc_\<versione > _enu.exe*, e *sqljdbc_\<versione > _ ENU.tar.gz*, rispettivamente. Per ulteriori informazioni su come distribuire il Driver JDBC, vedere [distribuzione del Driver JDBC](../../connect/jdbc/deploying-the-jdbc-driver.md) argomento.  
  
**Microsoft JDBC Driver 6.4 per SQL Server:**  

  Il 6.4 Driver JDBC include tre librerie di classi JAR in ogni pacchetto di installazione: **mssql-jdbc-6.4.0.jre7.jar**, **mssql-jdbc-6.4.0.jre8.jar**, e **mssql-jdbc-6.4.0.jre9.jar** .

  Il 6.4 Driver JDBC è progettato per funzionare con ed essere supportati da tutti i principali Sun macchine virtuali Java equivalenti, ma è stato testato solo su Sun JRE 7.0, 8.0 e 9.0.
  
  Di seguito viene riepilogato il supporto fornito dai tre file JAR inclusi con Microsoft JDBC driver 6.4 per SQL Server:  
  
  |JAR|Conformità versione JDBC|Versione di Java consigliata|Description|  
|---------|-----------------------------|----------------------|-----------------|   
|mssql-jdbc-6.4.0.jre7.jar|4.1|7|Richiede un Java Runtime Environment (JRE) versione 7.0. Utilizzo di JRE 6.0 o inferiore genera un'eccezione.<br /><br /> Nuove funzionalità in 6.4 includono: autenticazione di Azure AD per Linux, il metodo/Password dell'entità per il rilevamento automatico dell'area di autenticazione nome SPN per l'autenticazione tra domini, la delega vincolata Kerberos, Timeout di Query, il timeout del Socket, Kerberos e preparate handle di istruzione utilizzata nuovamente. |  
|mssql-jdbc-6.4.0.jre8.jar|4.2|8|Richiede un Java Runtime Environment (JRE) versione 8.0. Utilizzo di JRE 7.0 o inferiore genera un'eccezione.<br /><br /> Nuove funzionalità in 6.4 includono: autenticazione di Azure AD per Linux, il metodo/Password dell'entità per il rilevamento automatico dell'area di autenticazione nome SPN per l'autenticazione tra domini, la delega vincolata Kerberos, Timeout di Query, il timeout del Socket, Kerberos e preparate handle di istruzione utilizzata nuovamente. |    
|mssql-jdbc-6.4.0.jre9.jar|4.3|9|Richiede un Java Runtime Environment (JRE) 9.0. Utilizzo di JRE 8.0 o inferiore genera un'eccezione.<br /><br /> Nuove funzionalità in 6.4 includono: autenticazione di Azure AD per Linux, il metodo/Password dell'entità per il rilevamento automatico dell'area di autenticazione nome SPN per l'autenticazione tra domini, la delega vincolata Kerberos, Timeout di Query, il timeout del Socket, Kerberos e preparate handle di istruzione utilizzata nuovamente. |    


  6.4 il Driver JDBC è disponibile anche per il Repository centrale Maven e può essere aggiunto a un progetto di Maven aggiungendo il codice seguente nel POM. XML 
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.4.0.jre9</version>
</dependency>
```    
**Microsoft JDBC Driver 6.2 per SQL Server:**  
  
  Il 6.2 Driver JDBC include due librerie di classi JAR in ogni pacchetto di installazione: **mssql-jdbc-6.2.1.jre7.jar**, e **mssql-jdbc-6.2.1.jre8.jar**. 
  
 Il 6.2 Driver JDBC è progettato per funzionare con ed essere supportati da tutti i principali Sun macchine virtuali Java equivalenti, ma è stato testato solo su Sun JRE 5.0, 6.0, 7.0 e 8.0. 
  
 Di seguito viene riepilogato il supporto fornito dai due file JAR inclusi con Microsoft JDBC driver 6.0 e 4.2 per SQL Server:  
  
|JAR|Conformità versione JDBC|Versione di Java consigliata|Description|  
|---------|-----------------------------|----------------------|-----------------|   
|mssql-jdbc-6.2.1.jre7.jar|4.1|7|Richiede un Java Runtime Environment (JRE) versione 7.0. Utilizzo di JRE 6.0 o inferiore genera un'eccezione.<br /><br /> Nuove funzionalità in 6.2 includono: autenticazione di Azure AD per Linux, il metodo/Password dell'entità per il rilevamento automatico dell'area di autenticazione nome SPN per l'autenticazione di domini, la delega vincolata Kerberos, il Timeout di Query, il timeout del Socket, Kerberos e preparate handle di istruzione utilizzata nuovamente. |  
|mssql-jdbc-6.2.1.jre8.jar|4.2|8|Richiede un Java Runtime Environment (JRE) versione 8.0. Utilizzo di JRE 7.0 o inferiore genera un'eccezione.<br /><br /> Nuove funzionalità in 6.2 includono: autenticazione di Azure AD per Linux, il metodo/Password dell'entità per il rilevamento automatico dell'area di autenticazione nome SPN per l'autenticazione di domini, la delega vincolata Kerberos, il Timeout di Query, il timeout del Socket, Kerberos e preparate riutilizzo dei handle di istruzione|    

  6.2 eseguire il Driver JDBC è disponibile anche per il Repository centrale Maven e può essere aggiunto a un progetto di Maven aggiungendo il codice seguente nel POM. XML 
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.2.1.jre8</version>
</dependency>
```    

 **Microsoft JDBC Driver 6.0 e 4.2 per SQL Server:**  
  
  JDBC driver 6.0 e 4.2 includono due librerie di classi JAR in ogni pacchetto di installazione: **sqljdbc41.jar**, e **sqljdbc42.jar**. 
  
 Il driver JDBC 6.0 e 4.2 sono progettati per funzionare con ed essere supportati da tutti i principali Sun macchine virtuali Java equivalenti, ma è stato testato solo su Sun JRE 5.0, 6.0, 7.0 e 8.0. 
  
 Di seguito viene riepilogato il supporto fornito dai due file JAR inclusi con Microsoft JDBC driver 6.0 e 4.2 per SQL Server:  
  
|JAR|Conformità versione JDBC|Versione di Java consigliata|Description|  
|---------|-----------------------------|----------------------|-----------------|   
|sqljdbc41.jar|4.1|7|Richiede un Java Runtime Environment (JRE) versione 7.0. Utilizzo di JRE 6.0 o inferiore genera un'eccezione.<br /><br /> Le nuove funzionalità nei pacchetti 6.0 & 4.2 includono: conformità a JDBC 4.1 e copia bulk<br /><br /> Inoltre, nuove funzionalità nel solo pacchetto 6.0 includono: Always Encrypted, Table-Valued Parameters, Azure Active Directory l'autenticazione, le connessioni trasparenti ai gruppi di disponibilità AlwaysOn, miglioramento per il recupero di metadati di parametro preparato le query e IDN (Internationalized Domain Name)|  
|sqljdbc42.jar|4.2|8|Richiede un Java Runtime Environment (JRE) versione 8.0. Utilizzo di JRE 7.0 o inferiore genera un'eccezione.<br /><br /> Le nuove funzionalità nei pacchetti 6.0 & 4.2 includono: conformità a JDBC 4.1, conformità a JDBC 4.2 e copia bulk<br /><br /> Inoltre, nuove funzionalità nel solo pacchetto 6.0 includono: Always Encrypted, Table-Valued Parameters, Azure Active Directory l'autenticazione, le connessioni trasparenti ai gruppi di disponibilità AlwaysOn, miglioramento per il recupero di metadati di parametro preparato le query e IDN (Internationalized Domain Name)|  
  
 **Microsoft JDBC Driver 4.1 per SQL Server:**  
  
 JDBC Driver 4.1 include una libreria di classi JAR in ogni pacchetto di installazione: **sqljdbc41.jar**.  
    
|JAR|Description|  
|---------|-----------------|  
|sqljdbc41.jar|**sqljdbc41.jar** libreria di classi fornisce il supporto per API di JDBC 4.0. Include tutte le funzionalità del driver JDBC 4.0, nonché i metodi dell'API di JDBC 4.0. JDBC 4.1 non è supportato (verrà generata un'eccezione "SQLFeatureNotSupportedException").<br /><br /> **sqljdbc41.jar** libreria di classi richiede un Java Runtime Environment (JRE) 7.0. Utilizzando **sqljdbc41.jar** in JRE 6.0 o 5.0, viene generata un'eccezione.<br /><br /> 
  
 Il driver JDBC è progettato per funzionare con ed essere supportati da tutti i principali Sun macchine virtuali Java equivalenti, ma è stato testato solo su Sun JRE 5.0, 6.0 e 7.0.  
  
 Di seguito viene riepilogato il supporto fornito dal file JAR incluso con Microsoft JDBC Driver 4.1 per SQL Server.  
  
|JAR|Versione JDBC|JRE (esecuzione)|JDK (compilazione)|  
|---------|------------------|---------------------|-------------------------|   
|sqljdbc41.jar|4|7|7 6 5|  
  
## <a name="sql-server-requirements"></a>Requisiti di SQL Server  
 Il driver JDBC supporta le connessioni al database SQL di Azure e SQL Server. Per Microsoft JDBC Driver 4.2 e 4.1 per SQL Server, il supporto inizia con SQL Server 2008.
  
## <a name="operating-system-requirements"></a>Requisiti del sistema operativo  
 Il driver JDBC è stato sviluppato per essere utilizzato su qualsiasi sistema operativo che supporti l'utilizzo di Java Virtual Machine (JVM). Ufficialmente, tuttavia, sono stati testati solo i sistemi operativi Sun Solaris, SUSE Linux e Windows.  
  
## <a name="supported-languages"></a>Lingue supportate  
 Il driver JDBC supporta tutte [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] le regole di confronto di colonna. Per ulteriori informazioni sulle regole di confronto supportate dal driver JDBC, vedere [funzionalità internazionali del Driver JDBC](../../connect/jdbc/international-features-of-the-jdbc-driver.md).  
  
 Per ulteriori informazioni sulle regole di confronto, vedere "Utilizzo delle regole di confronto" nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
