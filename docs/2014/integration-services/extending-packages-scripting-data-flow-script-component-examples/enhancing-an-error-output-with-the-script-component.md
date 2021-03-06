---
title: Ottimizzazione di un output degli errori con il componente script | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- transformations [Integration Services], components
- Script component [Integration Services], examples
- error outputs [Integration Services], enhancing
- Script component [Integration Services], transformation components
ms.assetid: f7c02709-f1fa-4ebd-b255-dc8b81feeaa5
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9caf48a0ba48956e6f732a2cd2514422a3d6139a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245231"
---
# <a name="enhancing-an-error-output-with-the-script-component"></a>Ottimizzazione di un output degli errori con il componente script
  Per impostazione predefinita, le due colonne supplementari in un output degli errori di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], ovvero ErrorCode e ErrorColumn, contengono solo codici numerici che rappresentano un numero di errore, nonché l'ID della colonna in cui si è verificato l'errore. Questi valori numerici possono avere un'utilità limitata senza la descrizione dell'errore corrispondente.  
  
 In questo argomento viene descritto come aggiungere una colonna di descrizioni degli errori ai dati dell'output degli errori esistente nel flusso di dati tramite il componente Script. Nell'esempio viene aggiunta la descrizione dell'errore che corrisponde a un codice di errore specifico predefinito di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilizzando il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> dell'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>, disponibile tramite la proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> del componente script.  
  
> [!NOTE]  
>  Se si desidera creare un componente da riutilizzare più facilmente con più attività Flusso di dati e più pacchetti, è possibile utilizzare il codice di questo esempio di componente script come punto iniziale per un componente del flusso di dati personalizzato. Per altre informazioni, vedere [Sviluppo di un componente del flusso di dati personalizzato](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio illustrato viene utilizzato un componente script configurato come trasformazione per aggiungere una colonna di descrizione degli errori ai dati dell'output degli errori esistente nel flusso di dati.  
  
 Per altre informazioni su come configurare il componente Script per l'utilizzo come trasformazione nel flusso di dati, vedere [creazione di una trasformazione sincrona con il componente Script](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)e [creando un asincrono Trasformazione con il componente Script](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Per configurare l'esempio di componente script  
  
1.  Prima di creare il nuovo componente script, configurare un componente a monte nel flusso di dati per reindirizzare righe all'output degli errori quando si verifica un errore o un troncamento. A scopo di test, è possibile configurare un componente in modo da assicurarsi che si verificheranno errori, ad esempio configurando una trasformazione Ricerca tra due tabelle in cui la ricerca avrà esito negativo.  
  
2.  Aggiungere un nuovo componente script all'area di progettazione del flusso di dati e configurarlo come trasformazione.  
  
3.  Connettere l'output degli errori del componente a monte a questo nuovo componente script.  
  
4.  Aprire **Editor trasformazione Script** e nella pagina **Script** selezionare il linguaggio di scripting per la proprietà **ScriptLanguage**.  
  
5.  Fare clic su **Modifica script[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per aprire l'IDE di**  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tools for Applications (VSTA) e aggiungere il codice di esempio illustrato di seguito.  
  
6.  Chiudere VSTA.  
  
7.  Nell'Editor trasformazione Script sul **colonne di Input** pagina, selezionare la colonna ErrorCode.  
  
8.  Nel **ingressi e uscite** pagina, aggiungere una nuova colonna di output di tipo `String` denominato **ErrorDescription**. Aumentare la lunghezza predefinita della nuova colonna fino a 255 per supportare messaggi lunghi.  
  
9. Chiudere l'**Editor trasformazione Script.**  
  
10. Connettere l'output del componente script a una destinazione appropriata. Le destinazioni file flat sono le più facili da configurare per test ad hoc.  
  
11. Eseguire il pacchetto.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  Row.ErrorDescription = _  
    Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
    End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
{  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
  Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
    }  
}  
  
```  
  
![Icona di Integration Services (piccola)](../media/dts-16.gif "icona di Integration Services (piccola)")**rimangono fino a Date con Integration Services** <br /> Per i download, gli articoli, gli esempi e i video Microsoft più recenti, oltre alle soluzioni selezionate dalla community, visitare la pagina [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sul sito MSDN:<br /><br /> [Visita la pagina di Integration Services su MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Per ricevere una notifica automatica su questi aggiornamenti, sottoscrivere i feed RSS disponibili nella pagina.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione degli errori nei dati](../data-flow/error-handling-in-data.md)   
 [Uso degli output degli errori in un componente flusso di dati](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [Creazione di una trasformazione sincrona con il componente script](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
