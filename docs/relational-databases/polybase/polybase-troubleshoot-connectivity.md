---
title: Risolvere i problemi di connettività di PolyBase Kerberos | Microsoft Docs
author: alazad-msft
ms.author: alazad
manager: craigg
ms.technology: polybase
ms.suite: sql
ms.custom: ''
ms.tgt_pltfrm: na
ms.devlang: ''
ms.topic: article
ms.date: 07/19/2017"
ms.prod: sql
ms.prod_service: polybase, sql-data-warehouse, pdw
ms.openlocfilehash: f4786785dd046fea0c8758d2739c645c9a2312c8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151302"
---
# <a name="troubleshoot-polybase-kerberos-connectivity"></a>Risolvere i problemi di connettività di PolyBase Kerberos
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
È possibile usare uno strumento di diagnostica interattivo integrato in PolyBase per risolvere i problemi di autenticazione quando si usa PolyBase per un cluster Hadoop protetto con Kerberos. 

Questo articolo può essere usato come guida per eseguire il debug dei problemi usando lo strumento di diagnostica.

## <a name="prerequisites"></a>Prerequisites

1. SQL Server 2016 RTM CU6 / SQL Server 2016 SP1 CU3 / SQL Server 2017 o versione successiva con PolyBase installato
1. Un cluster Hadoop (Cloudera o Hortonworks) protetto con Kerberos (Active Directory o MIT)

## <a name="introduction"></a>Introduzione
È utile per capire il protocollo Kerberos a livello generale. Sono tre gli attori coinvolti:
1. Client Kerberos (SQL Server)
1. Risorsa protetta (HDFS, MR2, YARN, cronologia processo e così via)
1. Centro distribuzione chiavi (definito controller di dominio in Active Directory)

Ogni risorsa protetta di Hadoop è registrata nel **Centro distribuzione chiavi (KDC)** con un **nome dell'entità servizio (SPN)** univoco come parte del processo di protezione del cluster Hadoop con Kerberos. L'obiettivo è consentire al client di ottenere un ticket utente temporaneo, detto **Ticket Granting Ticket (TGT)**, in modo da richiedere un altro ticket temporaneo, detto **ticket di servizio (ST)**, dal KDC per il nome dell'entità servizio specifico a cui si vuole accedere.  
In PolyBase, quando è richiesta l'autenticazione per qualsiasi risorsa protetta con Kerberos, viene eseguito il seguente handshake a quattro vie:
1. SQL Server si connette a KDC e ottiene un ticket TGT per l'utente. Il TGT viene crittografato usando la chiave privata del KDC.
1. SQL Server chiama la risorsa protetta di Hadoop, ad esempio Hadoop Distributed File System (HDFS), e determina per quale SPN è necessario un ST.
1. SQL Server torna al KDC, passa di nuovo il TGT e richiede un ST per accedere a quella particolare risorsa protetta. Il ticket ST viene crittografato usando la chiave privata del servizio protetto.
1. SQL Server inoltra il ticket ST in Hadoop e viene autenticato per la creazione di una sessione per quel servizio.

![](./media/polybase-sqlserver.png)

I problemi di autenticazione rientrano in uno o più dei quattro passaggi precedenti. Per rendere il debug più veloce, PolyBase ha introdotto uno strumento di diagnostica integrato per l'identificazione del punto di errore.

## <a name="troubleshooting"></a>Risoluzione dei problemi
PolyBase ha più XML di configurazione che contengono le proprietà del cluster Hadoop. In particolare, questi sono i file:
- core-site.xml
- hdfs-site.xml
- hive-site.xml
- jaas.conf
- mapred-site.xml
- yarn-site.xml

Questi file si trovano in:

\\[Unità di sistema\\]: {percorso installazione}\\{istanza}\\{nome}\\MSSQL\\Binn\\Polybase\\Hadoop\\conf

Ad esempio, il valore predefinito per SQL Server 2016 sarebbe "C:\\Programmi\\Microsoft SQL Server\\MSSQL13. MSSQLSERVER\\MSSQL\\Binn\\Polybase\\Hadoop\\conf".

Aggiornare uno dei file di configurazione di PolyBase, **core-Site.xml**, con le tre proprietà indicate di seguito con i valori impostati in base all'ambiente:
```xml
<property>
    <name>polybase.kerberos.realm</name>
    <value>CONTOSO.COM</value>
</property>
<property>
    <name>polybase.kerberos.kdchost</name>
    <value>kerberos.contoso.com</value>
</property>
<property>
    <name>hadoop.security.authentication</name>
    <value>KERBEROS</value>
</property>
```
Gli altri XML in un secondo tempo dovranno essere a loro volta aggiornati se si vogliono eseguire operazioni di distribuzione, ma con solo questo file configurato, deve essere almeno possibile accedere al file system HDFS.

Lo strumento viene eseguito in modo indipendente da SQL Server, quindi non è necessario che sia in esecuzione, né che venga riavviato se vengono aggiornati gli XML di configurazione. Per eseguire lo strumento, usare i comandi seguenti nell'host in cui è installato SQL:

```
> cd C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase  
> java -classpath ".\Hadoop\conf;.\Hadoop\*;.\Hadoop\HDP2_2\*" com.microsoft.polybase.client.HdfsBridge {Name Node Address} {Name Node Port} {Service Principal} {Filepath containing Service Principal's Password} {Remote HDFS file path (optional)}
```

## <a name="arguments"></a>Argomenti
| Argomento | Descrizione|
| --- | --- |
| *Indirizzo del nodo del nome* | IP o nome di dominio completo del nodo del nome. Si riferisce all'argomento "LOCATION" in CREATE EXTERNAL DATA SOURCE T-SQL.|
| *Porta del nodo del nome* | La porta del nodo del nome. Si riferisce all'argomento "LOCATION" in CREATE EXTERNAL DATA SOURCE T-SQL. In genere è 8020. |
| *Entità servizio* | L'entità servizio di amministratore per il KDC. Deve corrispondere all'oggetto usato come argomento "IDENTITY" in CREATE DATABASE SCOPED CREDENTIAL T-SQL.|
| *Password del servizio* | Anziché digitare la password nella console, archiviarla in un file e passare il percorso del file qui. Il contenuto del file deve corrispondere all'oggetto usato come argomento "SECRET" in CREATE DATABASE SCOPED CREDENTIAL T-SQL. |
| *Percorso del file HDFS remoto (facoltativo)* | Percorso di un file esistente a cui accedere. Se non è specificato, verrà usata la radice "/". |

## <a name="example"></a>Esempio
```dos
java -classpath ".\Hadoop\conf;.\Hadoop\*;.\Hadoop\HDP2_2\*" com.microsoft.polybase.client.HdfsBridge 10.193.27.232 8020 admin_user C:\temp\kerberos_pass.txt
```
L'output è dettagliato per il debug avanzato, ma esistono solo quattro checkpoint principali da cercare indipendentemente dal fatto che si usi MIT o Active Directory. Corrispondono ai quattro passaggi descritti in precedenza. 

I seguenti estratti provengono da un centro distribuzione chiavi (KDC) MIT. I riferimenti agli output di esempio completi per MIT e AD sono riportati alla fine di questo articolo.

## <a name="checkpoint-1"></a>Checkpoint 1
Deve essere presente un dump esadecimale di un ticket con entità server = krbtgt /*MYREALM.COM@MYREALM.COM*. Questo indica SQL Server ha eseguito correttamente l'autenticazione nel KDC e ha ricevuto un TGT. In caso contrario, il problema riguarda esclusivamente SQL Server e il KDC e non Hadoop.

PolyBase **non** supporta le relazioni di trust tra AD e MIT e deve essere configurato per lo stesso KDC come è stato configurato nel cluster Hadoop. In tali ambienti la creazione manuale di un account di servizio per il KDC e l'uso dell'account per eseguire l'autenticazione funzionano.
```dos
|>>> KrbAsReq creating message 
 >>> KrbKdcReq send: kdc=kerberos.contoso.com UDP:88, timeout=30000, number of retries =3, #bytes=143 
 >>> KDCCommunication: kdc=kerberos.contoso.com UDP:88, timeout=30000,Attempt =1, #bytes=143 
 >>> KrbKdcReq send: #bytes read=646 
 >>> KdcAccessibility: remove kerberos.contoso.com 
 >>> EType: sun.security.krb5.internal.crypto.Des3CbcHmacSha1KdEType 
 >>> KrbAsRep cons in KrbAsReq.getReply myuser 
 [2017-04-25 21:34:33,548] INFO 687[main] - com.microsoft.polybase.client.KerberosSecureLogin.secureLogin(KerberosSecureLogin.java:97) - Subject: 
 Principal: admin_user@CONTOSO.COM 
 Private Credential: Ticket (hex) = 
 0000: 61 82 01 48 30 82 01 44 A0 03 02 01 05 A1 0E 1B a..H0..D........ 
 0010: 0C 41 50 53 48 44 50 4D 53 2E 43 4F 4D A2 21 30 .CONTOSO.COM.!0 
 0020: 1F A0 03 02 01 02 A1 18 30 16 1B 06 6B 72 62 74 ........0...krbt 
 0030: 67 74 1B 0C 41 50 53 48 44 50 4D 53 2E 43 4F 4D gt..CONTOSO.COM 
 0040: A3 82 01 08 30 82 01 04 A0 03 02 01 10 A1 03 02 ....0........... 
 *[…Condensed…]* 
 0140: 67 6D F6 41 6C EB E0 C3 3A B2 BD B1 gm.Al...:... 
 Client Principal = admin_user@CONTOSO.COM 
 Server Principal = krbtgt/CONTOSO.COM@CONTOSO.COM 
 *[…Condensed…]* 
 [2017-04-25 21:34:34,500] INFO 1639[main] - com.microsoft.polybase.client.HdfsBridge.main(HdfsBridge.java:1579) - Successfully authenticated against KDC server. 
```
## <a name="checkpoint-2"></a>Checkpoint 2
PolyBase tenterà di accedere all'HDFS con esito negativo perché la richiesta non contiene il ticket di servizio necessario.
```dos
 [2017-04-25 21:34:34,501] INFO 1640[main] - com.microsoft.polybase.client.HdfsBridge.main(HdfsBridge.java:1584) - Attempting to access external filesystem at URI: hdfs://10.193.27.232:8020 
 Found ticket for admin_user@CONTOSO.COM to go to krbtgt/CONTOSO.COM@CONTOSO.COM expiring on Wed Apr 26 21:34:33 UTC 2017 
 Entered Krb5Context.initSecContext with state=STATE_NEW 
 Found ticket for admin_user@CONTOSO.COM to go to krbtgt/CONTOSO.COM@CONTOSO.COM expiring on Wed Apr 26 21:34:33 UTC 2017 
 Service ticket not found in the subject 
```
## <a name="checkpoint-3"></a>Checkpoint 3
Un secondo dump esadecimale indica che SQL Server ha usato correttamente il TGT e ha acquisito il ticket di servizio applicabile per il nome dell'entità servizio del nodo del nome dal KDC.
```dos
 >>> KrbKdcReq send: kdc=kerberos.contoso.com UDP:88, timeout=30000, number of retries =3, #bytes=664 
 >>> KDCCommunication: kdc=kerberos.contoso.com UDP:88, timeout=30000,Attempt =1, #bytes=664 
 >>> KrbKdcReq send: #bytes read=669 
 >>> KdcAccessibility: remove kerberos.contoso.com 
 >>> EType: sun.security.krb5.internal.crypto.Des3CbcHmacSha1KdEType 
 >>> KrbApReq: APOptions are 00100000 00000000 00000000 00000000 
 >>> EType: sun.security.krb5.internal.crypto.Des3CbcHmacSha1KdEType 
 Krb5Context setting mySeqNumber to: 1033039363 
 Created InitSecContextToken: 
 0000: 01 00 6E 82 02 4B 30 82 02 47 A0 03 02 01 05 A1 ..n..K0..G...... 
 0010: 03 02 01 0E A2 07 03 05 00 20 00 00 00 A3 82 01 ......... ...... 
 0020: 63 61 82 01 5F 30 82 01 5B A0 03 02 01 05 A1 0E ca.._0..[....... 
 0030: 1B 0C 41 50 53 48 44 50 4D 53 2E 43 4F 4D A2 26 ..CONTOSO.COM.& 
 0040: 30 24 A0 03 02 01 00 A1 1D 30 1B 1B 02 6E 6E 1B 0$.......0...nn. 
 0050: 15 73 68 61 73 74 61 2D 68 64 70 32 35 2D 30 30 .hadoop-hdp25-00 
 0060: 2E 6C 6F 63 61 6C A3 82 01 1A 30 82 01 16 A0 03 .local....0..... 
 0070: 02 01 10 A1 03 02 01 01 A2 82 01 08 04 82 01 04 ................ 
 *[…Condensed…]* 
 0240: 03 E3 68 72 C4 D2 8D C2 8A 63 52 1F AE 26 B6 88 ..hr.....cR..&.. 
 0250: C4 . 
```
## <a name="checkpoint-4"></a>Checkpoint 4
Infine, le proprietà del file del percorso di destinazione devono essere stampate insieme a un messaggio di conferma. Ciò indica che SQL Server è stato autenticato da Hadoop usando il ticket ST e che è stato concesso a una sessione di accedere alla risorsa protetta.

Quando si raggiunge questo punto viene confermato che: (i) i tre attori sono in grado di comunicare correttamente, (ii) core-site.xml e jaas.conf sono corretti e (iii) il KDC ha riconosciuto le credenziali.
```dos
 [2017-04-25 21:34:35,096] INFO 2235[main] - com.microsoft.polybase.client.HdfsBridge.main(HdfsBridge.java:1586) - File properties for "/": FileStatus{path=hdfs://10.193.27.232:8020/; isDirectory=true; modification_time=1492028259862; access_time=0; owner=hdfs; group=hdfs; permission=rwxr-xr-x; isSymlink=false} 
 [2017-04-25 21:34:35,098] INFO 2237[main] - com.microsoft.polybase.client.HdfsBridge.main(HdfsBridge.java:1587) - Successfully accessed the external file system. 
```
## <a name="common-errors"></a>Errori comuni
Se è stato eseguito lo strumento e le proprietà del file del percorso di destinazione *non* sono state stampate (Checkpoint 4), deve essere stata generata un'eccezione in un punto intermedio. Esaminarla e considerare il contesto in cui si è verificato nel flusso in quattro passaggi. Prendere in considerazione i seguenti problemi comuni che si possono essere verificati, nell'ordine:
| Eccezione e messaggi | Causa | 
| --- | --- |
| org.apache.hadoop.security.AccessControlException<br>SIMPLE authentication is not enabled. Available:[TOKEN, KERBEROS] | Per core-site.xml la proprietà hadoop.security.authentication non è impostata su "KERBEROS".|
|javax.security.auth.login.LoginException<br>Client not found in Kerberos database  (6) - CLIENT_NOT_FOUND |    L'entità servizio dell'amministratore specificata non esiste nell'area di autenticazione specificata in core-site.xml.|
| javax.security.auth.login.LoginException<br> Checksum failed |    L'entità servizio dell'amministratore esiste, ma la password non è valida. |
| Native config name: C:\Windows\krb5.ini<br>Loaded from native config | Questa non è un'eccezione, ma indica che krb5LoginModule di Java ha rilevato configurazioni client personalizzate nel computer. Controllare le impostazioni client personalizzate perché possono essere la causa del problema. |
| javax.security.auth.login.LoginException<br>java.lang.IllegalArgumentException<br>Illegal principal name admin_user@CONTOSO.COM: org.apache.hadoop.security.authentication.util.KerberosName$NoMatchingRule: No rules applied to admin_user@CONTOSO.COM | Aggiungere la proprietà "hadoop.security.auth_to_local" a core-site.xml con le regole appropriate in base al cluster Hadoop. |
| java.net.ConnectException<br>Attempting to access external filesystem at URI: hdfs://10.193.27.230:8020<br>Call From IAAS16981207/10.107.0.245 to 10.193.27.230:8020 failed on connection exception | L'autenticazione per il KDC è riuscita, ma non è stato possibile accedere al nodo del nome Hadoop. Controllare l'IP e la porta del nodo del nome. Verificare che il firewall sia disabilitato in Hadoop. |
| java.io.FileNotFoundException<br>File does not exist: /test/data.csv |    L'autenticazione è riuscita, ma il percorso specificato non esiste. Controllare il percorso o eseguire prima un test con la radice "/" . |
## <a name="debugging-tips"></a>Suggerimenti per il debug
### <a name="mit-kdc"></a>KDC MIT  
Tutti i nomi dell'entità servizio registrati con il KDC, tra cui gli amministratori, possono essere visualizzati eseguendo **kadmin.local** > (account di accesso dell'amministratore) > **listprincs** sull'host KDC o qualsiasi client KDC configurato. Se il cluster Hadoop è stato correttamente protetto con Kerberos, deve essere presente un nome dell'entità servizio per ognuno dei diversi servizi disponibili nel cluster (ad esempio nn, dn, rm, yarn, spnego e così via). I file keytab corrispondenti (sostituti delle password) possono essere visualizzati in **/etc/security/keytabs** per impostazione predefinita. Vengono crittografati usando la chiave privata del KDC.  

Può essere anche opportuno usare lo strumento [kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html) per verificare le credenziali di amministratore nel KDC a livello locale. Un esempio di utilizzo è: *kinit identity@MYREALM.COM*. La richiesta di una password indica che l'identità esiste.  
Per impostazione predefinita, i log del KDC sono disponibili in **/var/log/krb5kdc.log**, che include tutte le richieste di ticket, con l'indirizzo IP del client che ha effettuato la richiesta. Devono essere presenti due richieste provenienti dall'indirizzo IP del computer SQL Server in cui è stato eseguito lo strumento: la prima per il ticket TGT del server di autenticazione specificata come **AS\_REQ** e la seconda, **TGS\_REQ**, per il ticket ST proveniente dal server di concessione dei ticket.
```bash
 [root@MY-KDC log]# tail -2 /var/log/krb5kdc.log 
 May 09 09:48:26 MY-KDC.local krb5kdc[2547](info): **AS_REQ** (3 etypes {17 16 23}) 10.107.0.245: ISSUE: authtime 1494348506, etypes {rep=16 tkt=16 ses=16}, admin_user@CONTOSO.COM for **krbtgt/CONTOSO.COM@CONTOSO.COM** 
 May 09 09:48:29 MY-KDC.local krb5kdc[2547](info): **TGS_REQ** (3 etypes {17 16 23}) 10.107.0.245: ISSUE: authtime 1494348506, etypes {rep=16 tkt=16 ses=16}, admin_user@CONTOSO.COM for **nn/hadoop-hdp25-00.local@CONTOSO.COM** 
```
### <a name="active-directory"></a>Active Directory 
In Active Directory è possibile visualizzare i nomi dell'entità servizio passando a Pannello di controllo > Utenti e computer di Active Directory > *AreaAutenticazione* > *UnitàOrganizzativa*. Se il cluster Hadoop è stato correttamente protetto con Kerberos, deve essere presente un nome dell'entità servizio per ognuno dei diversi servizi disponibili (ad esempio nn, dn, rm, yarn, spnego e così via).

## <a name="see-also"></a>Vedere anche
[Blog sull'integrazione di PolyBase con Cloudera usando l'autenticazione di Active Directory](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/10/17/integrating-polybase-with-cloudera-using-active-directory-authentication)  
[Guida di Cloudera per la configurazione di Kerberos per CDH](https://www.cloudera.com/documentation/enterprise/5-6-x/topics/cm_sg_principal_keytab.html)  
[Guida di Hortonworks per la configurazione di Kerberos per HDP](https://docs.hortonworks.com/HDPDocuments/Ambari-2.2.0.0/bk_Ambari_Security_Guide/content/ch_configuring_amb_hdp_for_kerberos.html)  
[Risoluzione dei problemi di Polybase](polybase-troubleshooting.md)


