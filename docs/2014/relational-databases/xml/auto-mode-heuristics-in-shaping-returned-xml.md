---
title: Approccio euristico della modalità AUTO per la determinazione della struttura dei valori XML restituiti | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, heuristics in shaping returned XML
ms.assetid: 6c5cb6c1-2921-4ba1-8100-0bf8074f9103
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fad7c50665d9a2d3f4641d99ba37e4c4e240b19b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37162242"
---
# <a name="auto-mode-heuristics-in-shaping-returned-xml"></a>Approccio euristico della modalità AUTO per la determinazione della struttura dei valori XML restituiti
  La modalità AUTO determina la struttura del valore XML restituito in base alla query. Per determinare come devono essere nidificati gli elementi, la modalità AUTO, che utilizza un approccio euristico, confronta i valori delle colonne nelle righe adiacenti. Vengono confrontate colonne di tutti i tipi, ad eccezione di **ntext**, **text**, **image**e **xml**. Vengono confrontate le colonne di tipo **(n)varchar(max)** e **varbinary(max)** .  
  
 Nell'esempio seguente viene illustrato l'approccio euristico utilizzato dalla modalità AUTO per determinare la struttura del valore XML risultante:  
  
```  
SELECT T1.Id, T2.Id, T1.Name  
FROM   T1, T2  
WHERE ...  
FOR XML AUTO  
ORDER BY T1.Id  
```  
  
 Per determinare la posizione iniziale dell'elemento <`T1`>, se non è specificata la chiave della tabella T1 vengono confrontati tutti i valori di colonna di T1, ad eccezione di quelli di tipo **ntext**, **text**, **image** e **xml**. Supporre quindi che la colonna **Name** sia di tipo **nvarchar(40)** e che l'istruzione SELECT restituisca il set di righe seguente:  
  
```  
T1.Id  T1.Name  T2.Id  
-----------------------  
1       Andrew    2  
1       Andrew    3  
1       Nancy     4  
```  
  
 Utilizzando un approccio euristico, la modalità AUTO confronta tutti i valori della tabella T1, ovvero le colonne Id e Name. Le prime due righe contengono gli stessi valori nelle colonne Id e Name, quindi al risultato viene aggiunto un elemento \<T1> con due elementi figlio \<T2>.  
  
 Il valore XML restituito è il seguente:  
  
```  
<T1 Id="1" Name="Andrew">  
    <T2 Id="2" />  
    <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
      <T2 Id="4" />  
</T>  
```  
  
 Si supponga ora che la colonna Name sia di tipo **text** . A causa dell'approccio euristico, la modalità AUTO non confronta valori di questo tipo, ma presuppone che siano diversi. Viene pertanto generato il valore XML illustrato di seguito:  
  
```  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="2" />  
</T1>  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
  <T2 Id="4" />  
</T1>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo della modalità AUTO con FOR XML](use-auto-mode-with-for-xml.md)  
  
  
