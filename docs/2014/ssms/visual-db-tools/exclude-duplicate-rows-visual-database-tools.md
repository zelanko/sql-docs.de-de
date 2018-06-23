---
title: Ausschließen doppelter Zeilen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 017385370989983d37f045379de926d0ebbf333f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163056"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a>Ausschließen doppelter Zeilen (Visual Database Tools)
  Wenn in einem Resultset nur eindeutige Werte angezeigt werden sollen, können Sie das Ausschließen von Duplikaten aus dem Resultset angeben.  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a>So schließen Sie doppelte Zeilen aus dem Resultset aus  
  
1.  Klicken Sie mit der rechten Maustaste auf den Hintergrund des Diagrammbereichs, und wählen Sie im Kontextmenü **Eigenschaften** aus.  
  
2.  Klicken Sie im Eigenschaftenfenster auf **DISTINCT-Werte** , und legen Sie als Wert **Ja**fest.  
  
     Der Abfrage- und Sicht-Designer fügt das Schlüsselwort DISTINCT vor der Liste der Anzeigespalten in der SQL-Anweisung ein.  
  
    > [!NOTE]  
    >  Wenn Sie das Schlüsselwort DISTINCT verwenden, können Sie möglicherweise die Ergebnisse im Ergebnisbereich nicht ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [Geben Sie Suchkriterien &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Sortieren und Gruppieren von Abfrageergebnissen &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)  
  
  