---
title: Metodo InitializeReportServer (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- InitializeReportServer (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- InitializeReportServer method
ms.assetid: 0304acc2-1fd7-437b-94d9-1c1073dd3ca4
caps.latest.revision: 21
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 68fc4cf97c6f05723628df50ffb267e12111de93
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33030408"
---
# <a name="configurationsetting-method---initializereportserver"></a>Metodo di ConfigurationSetting - InitializeReportServer
  Inizializza l'istanza di servizio di report specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub InitializeReportServer(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void InitializeReportServer(string InstallationID,   
    out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Parametri  
 *InstallationID*  
 Stringa utilizzata per crittografare la chiave di crittografia prima che venga restituita.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
 *ExtendedErrors[]*  
 [out] Matrice di stringhe che contiene errori aggiuntivi restituiti dalla chiamata.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## <a name="remarks"></a>Remarks  
 Quando viene chiamato questo metodo, la chiave di crittografia che accede alle informazioni protette del database del server di report viene crittografata tramite la chiave pubblica del server di report identificato da *InstallationID*.  
  
 La chiave pubblica del server di report specificato deve essere stata precedentemente scritta nel database del server di report.  
  
 Il metodo *InitializeReportServer* deve essere chiamato per un server di report che dispone già dell'accesso alle informazioni protette in modo che sia in grado di decrittografare la chiave di crittografia. La chiave di crittografia crittografata risultante viene quindi archiviata nel database del server di report.  
  
 Se la proprietà [IsInitialized](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-isinitialized.md) del server di report è impostata su **true** quando viene chiamato il metodo InitializeReportServer, il metodo ha esito positivo senza provare a crittografare la chiave di crittografia.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
