---
title: Raccolta di colonne (ADOX) | Documenti Microsoft
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
- Index::Columns
- Table::Columns
- Key::Columns
- Columns
helpviewer_keywords:
- Columns collection [ADOX]
ms.assetid: 23b9fea8-4f76-4a51-95ce-1a6ce4560b34
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65b5ae6a15ee5da44c2876c75dc21e658b50fed6
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35285196"
---
# <a name="columns-collection-adox"></a>Raccolta di colonne (ADOX)
Contiene tutti [colonna](../../../ado/reference/adox-api/column-object-adox.md) gli oggetti di una tabella, indice o chiave.  
  
## <a name="remarks"></a>Remarks  
 Il [Append](../../../ado/reference/adox-api/append-method-adox-columns.md) metodo per un **colonne** insieme è univoco in ADOX. È possibile effettuare le operazioni seguenti:  
  
-   Aggiungere una nuova colonna alla raccolta con il **Append** metodo.  
  
 Le proprietà e i metodi rimanenti sono standard per le raccolte di ADO. È possibile effettuare le operazioni seguenti:  
  
-   Accedere a una colonna nella raccolta con il [elemento](../../../ado/reference/ado-api/item-property-ado.md) proprietà.  
  
-   Restituire il numero di colonne contenute nella raccolta con il [conteggio](../../../ado/reference/ado-api/count-property-ado.md) proprietà.  
  
-   Rimuovere una colonna dalla raccolta con il [eliminare](../../../ado/reference/adox-api/delete-method-adox-collections.md) metodo.  
  
-   Aggiornare gli oggetti nella raccolta in base allo schema del database corrente con il [aggiornamento](../../../ado/reference/ado-api/refresh-method-ado.md) metodo.  
  
> [!NOTE]
>  Si verifica un errore quando si accoda un **colonna** per il **colonne** raccolta di un [indice](../../../ado/reference/adox-api/index-object-adox.md) se il **colonna** non esiste un [Tabella](../../../ado/reference/adox-api/table-object-adox.md) già aggiunto al [tabelle](../../../ado/reference/adox-api/tables-collection-adox.md) insieme.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi della raccolta di oggetti Column](../../../ado/reference/adox-api/columns-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Le colonne e tabelle aggiungere metodi, esempio di proprietà Name (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connessione Close (metodo), esempio di proprietà di tipo tabella (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Chiavi Aggiungi metodo, tipo di chiave, RelatedColumn, RelatedTable e UpdateRule proprietà esempio (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Esempio di proprietà ParentCatalog (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Esempio di proprietà SortOrder (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Oggetto Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)
