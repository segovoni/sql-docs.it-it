---
title: Append (metodo) (ADOX Views) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Views::raw_Append
- Views::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6070fd58-3237-4c77-a966-5b39ce5d57e4
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a524be12a721d86e0e5afd1029f486ca7c8ecaa9
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35285210"
---
# <a name="append-method-adox-views"></a>Append (metodo) (ADOX Views)
Crea un nuovo [vista](../../../ado/reference/adox-api/view-object-adox.md) dell'oggetto e lo aggiunge al [viste](../../../ado/reference/adox-api/views-collection-adox.md) insieme.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Views.Append Name, Command  
```  
  
#### <a name="parameters"></a>Parametri  
 *Nome*  
 Oggetto **stringa** valore che specifica il nome della vista da creare.  
  
 *Command*  
 Un oggetto ADO [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto che rappresenta la visualizzazione da creare.  
  
## <a name="remarks"></a>Remarks  
 Crea una nuova visualizzazione nell'origine dati con il nome e gli attributi specificati nel **comando** oggetto.  
  
 Se il testo del comando specificato dall'utente rappresenta una stored procedure, anziché una vista, il comportamento è dipende dal provider. **Aggiungere** avrà esito negativo se il provider non supporta i comandi di persistenza.  
  
> [!NOTE]
>  Quando si utilizza il Provider OLE DB per Microsoft Jet, la **viste** raccolta **Append** metodo consente di specificare un **procedura** piuttosto che un **visualizzazione**  nel *comando* parametro. Il **procedura** verrà aggiunto all'origine dati e verrà aggiunto al **viste** insieme. Dopo il **Append**, se il **procedure** e **viste** raccolte vengono aggiornate, il **procedura** non sarà più possibile nel **Viste** insieme e verranno visualizzati di **procedure** insieme.  
  
## <a name="applies-to"></a>Si applica a  
 [Raccolta di oggetti View (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di esempio del metodo Append (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Append (metodo) (ADOX colonne)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append (metodo) (ADOX gruppi)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append (metodo) (ADOX indici)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append (metodo) (ADOX chiavi)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append (metodo) (ADOX procedure)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append (metodo) (ADOX tabelle)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Metodo Append (oggetti User ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)
