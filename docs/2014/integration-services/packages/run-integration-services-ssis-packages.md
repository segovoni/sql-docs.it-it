---
title: Esecuzione di progetti e pacchetti | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
- executing packages [Integration Services]
- running packages [Integration Services]
- Integration Services, (See also Integration Services packages)
ms.assetid: c5fecc23-6f04-4fb2-9a29-01492ea41404
caps.latest.revision: 56
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cc9e292b67bd282351bdea60068a58a39ecb0aad
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287607"
---
# <a name="execution-of-projects-and-packages"></a>Esecuzione di progetti e pacchetti
  Per eseguire un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , è possibile usare vari strumenti, a seconda della posizione in cui sono archiviati tali pacchetti. Gli strumenti sono descritti nella tabella seguente.  
  
 Per archiviare un pacchetto nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , è possibile utilizzare il modello di distribuzione del progetto per distribuire il progetto nel server. Per informazioni, vedere [Distribuire progetti nel server Integration Services](../deploy-projects-to-integration-services-server.md).  
  
 Per archiviare un pacchetto nell'archivio pacchetti SSIS, nel database msdb o nel file system, è possibile utilizzare il modello di distribuzione del pacchetto. Per altre informazioni, vedere [pacchetto di distribuzione &#40;SSIS&#41;](legacy-package-deployment-ssis.md).  
  
|Strumento|Pacchetti archiviati nel server Integration Services|Pacchetti archiviati nell'archivio pacchetti SSIS o nel database msdb|Pacchetti archiviati nel file system, all'esterno del percorso che fa parte dell'archivio pacchetti SSIS|  
|----------|-----------------------------------------------------------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|  
|**SQL Server Data Tools**|no|no<br /><br /> È tuttavia possibile aggiungere un pacchetto esistente a un progetto dall'archivio pacchetti di [!INCLUDE[ssIS](../../includes/ssis-md.md)] , in cui è incluso il database msdb. L'aggiunta di un pacchetto esistente al progetto comporta la creazione di una copia locale del pacchetto nel file system.|Sì|  
|**SQL Server Management Studio, quando si è connessi a un'istanza del motore di database in cui è ospitato il server Integration Services**<br /><br /> Per altre informazioni, vedere [Finestra di dialogo Esecuzione pacchetto](../execute-package-dialog-box.md)|Sì|no<br /><br /> È tuttavia possibile importare un pacchetto nel server da questi percorsi.|no<br /><br /> È tuttavia possibile importare un pacchetto nel server dal file system.|  
|**SQL Server Management Studio, quando è connesso al servizio Integration Services che gestisce l'archivio pacchetti SSIS**|no|Sì|no<br /><br /> È tuttavia possibile importare un pacchetto nell'archivio pacchetti di [!INCLUDE[ssIS](../../includes/ssis-md.md)] dal file system.|  
|**dtexec**<br /><br /> Per altre informazioni, vedere [dtexec Utility](dtexec-utility.md).|Sì|Sì|Sì|  
|**dtexecui**<br /><br /> Per altre informazioni, vedere [Riferimento all’interfaccia utente dell’utilità di esecuzione pacchetti &#40;DtExecUI&#41;](execute-package-utility-dtexecui-ui-reference.md)|no|Sì|Sì|  
|**SQL Server Agent**<br /><br /> Per pianificare un pacchetto, è possibile utilizzare un processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.<br /><br /> Per altre informazioni, vedere [Processi di SQL Server Agent per i pacchetti](sql-server-agent-jobs-for-packages.md).|Sì|Sì|Sì|  
|**Stored procedure predefinita**<br /><br /> Per altre informazioni, vedere [catalog.start_execution &#40;database SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)|Sì|no|no|  
|**API gestita, tramite tipi e membri dello spazio dei nomi ** <xref:Microsoft.SqlServer.Management.IntegrationServices>|Sì|no|no|  
|**API gestita, tramite tipi e membri dello spazio dei nomi ** <xref:Microsoft.SqlServer.Dts.Runtime>|Non attualmente|Sì|Sì|  
  
## <a name="execution-and-logging"></a>Esecuzione e registrazione  
 È possibile abilitare la registrazione per i pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], nonché acquisire informazioni di run-time in file di log. Per altre informazioni, vedere [registrazione di Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md).  
  
 Per monitorare i pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che vengono distribuiti ed eseguiti nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], utilizzare i report delle operazioni. I report sono disponibili in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per altre informazioni, vedere [report per il server Integration Services](../reports-for-the-integration-services-server.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Pianificare un pacchetto tramite SQL Server Agent](../schedule-a-package-by-using-sql-server-agent.md)  
  
-   [Eseguire un pacchetto in SQL Server Data Tools](../run-a-package-in-sql-server-data-tools.md)  
  
-   [Eseguire un pacchetto sul server SSIS mediante SQL Server Management Studio](../run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità dtexec](dtexec-utility.md)   
 [Importazione/Esportazione guidata SQL Server](../import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)  
  
  
