---
title: Finestra di dialogo Join (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.ppg.joinline
- vdtsql.chm:69638
ms.assetid: 0d9516bb-4ad3-4fcf-bb77-93474dea698f
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 57490e0592f11e78ffddf44f0d3c3f60d90925a4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238171"
---
# <a name="join-dialog-box-visual-database-tools"></a>Finestra di dialogo Join (Visual Database Tools)
  Questa finestra di dialogo consente di specificare le opzioni per il join delle tabelle. Per accedere a tale finestra di dialogo, nel riquadro **Progettazione** selezionare una linea di join. Quindi nella finestra **Proprietà** fare clic su **Tipo e condizione di join**e sui puntini di sospensione **(…)** a destra della proprietà.  
  
 Per impostazione predefinita, le tabelle correlate vengono unite utilizzando un inner join che crea un set di risultati basato su righe contenenti informazioni corrispondenti nelle colonne join. Impostando le opzioni nella finestra di dialogo **Join** , è possibile specificare sia un join basato su un diverso operatore che un outer join.  
  
 Per altre informazioni sull'unione delle tabelle, vedere [Esecuzione di query con join &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
## <a name="options"></a>Opzioni  
  
|**Nome**|**Definizione**|  
|--------------|--------------------|  
|**Tabella**|I nomi delle tabelle o degli oggetti con valori di tabella coinvolti nel join. Non è possibile modificare i nomi delle tabelle in questa casella. Tali nomi vengono visualizzati solo a scopo informativo.|  
|**Colonna**|I nomi delle colonne utilizzate per l'unione delle tabelle. L'operatore nell'elenco degli operatori specifica la relazione fra i dati nelle colonne. Non è possibile modificare i nomi delle colonne in questa casella. Tali nomi vengono visualizzati solo a scopo informativo.|  
|**Operatore**|Specifica l'operatore utilizzato per mettere in relazione le colonne join. Per specificare un operatore diverso da uguale (=), selezionarlo nell'elenco. Quando si chiude la pagina delle proprietà, l'operatore selezionato verrà visualizzato nell'immagine a rombo della linea di join, come illustrato di seguito:<br /><br /> ![Icona di Visual Database Tools](../../database-engine/media//dv3wbii.gif "Icona di Visual Database Tools")|  
|**Tutte le righe da \<table1 >**|Specifica che tutte le righe della tabella di sinistra compaiono nell'output anche se non esistono corrispondenze nella tabella di destra. Le colonne senza dati corrispondenti nella tabella di destra appaiono come Null. Selezionare questa opzione equivale a specificare LEFT OUTER JOIN nell'istruzione SQL.|  
|**Tutte le righe da \<table2 >**|Specifica che tutte le righe della tabella di destra compaiono nell'output anche se non esistono corrispondenze nella tabella di sinistra. Le colonne senza dati corrispondenti nella tabella di sinistra appaiono come Null. Selezionare questa opzione equivale a specificare RIGHT OUTER JOIN nell'istruzione SQL.|  
  
 Selezionare tutte le **righe dal \<table1 >** e **tutte le righe da \<table2 >** equivale a specificare FULL OUTER JOIN nell'istruzione SQL.  
  
 Quando si seleziona un'opzione per creare un outer join, l'immagine a rombo nella linea di join cambia per indicare che il join è di tipo left outer, right outer o full outer.  
  
> [!NOTE]  
>  Le parole "left" e "right" non corrispondono necessariamente alla posizione delle tabelle nel riquadro Diagramma. "Left" fa riferimento alla tabella il cui nome viene visualizzato a sinistra della parola chiave JOIN nell'istruzione SQL, mentre "right" fa riferimento alla tabella il cui nome viene visualizzato a destra della parola chiave JOIN. Lo spostamento delle tabelle nel riquadro **Diagramma** pertanto non incide in alcun modo su quale sia la tabella di sinistra o di destra.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire una query con join &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Procedure per la progettazione di query e viste &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
