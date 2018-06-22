---
title: Sortieren in aufsteigender oder absteigender Reihenfolge (Visual Database Tools) | Microsoft-Dokumentation
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
- descending sorts
- ascending sorts
ms.assetid: d61cc55b-9ee8-4ecf-a32f-6459ae43910b
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 62263168add17a8a31145a8fe4552bab0b9d6691
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048876"
---
# <a name="sort-in-ascending-or-descending-order-visual-database-tools"></a>Sortieren in aufsteigender oder absteigender Reihenfolge (Visual Database Tools)
  Mithilfe der Schlüsselwörter `ASC` und `DESC` und der `ORDER BY`-Klausel können Abfrageergebnisse in einer oder mehreren Spalten des Resultsets in auf- oder absteigender Reihenfolge sortiert werden.  
  
> [!NOTE]  
>  Die Sortierreihenfolge wird teilweise durch die Sortierreihenfolge der Spalte bestimmt. Sie können die Sortierreihenfolge im [Dialogfeld Sortierreihenfolge](visual-database-tools.md)ändern.  
  
 Bei der folgenden Prozedur wird vorausgesetzt, dass im Abfrage- und Sicht-Designer eine Abfrage geöffnet ist, in der zum Sortieren einer oder mehrerer Spalten die ORDER BY-Klausel verwendet wird.  
  
### <a name="to-specify-or-change-the-order-in-which-results-are-sorted"></a>So geben Sie die Sortierreihenfolge der Ergebnisse an und ändern diese  
  
1.  Klicken Sie im [Kriterienbereich](criteria-pane-visual-database-tools.md)für die neu zu sortierende Spalte auf das Feld **Sortierungsart** .  
  
2.  Wählen Sie **Aufsteigend** oder **Absteigend** aus, um die Sortierreihenfolge für die Spalte anzugeben.  
  
 Beachten Sie beim Arbeiten im Kriterienbereich, dass die UNION-Klausel der Abfrage entsprechend der zuletzt ausgeführten Aktionen geändert wird.  
  
> [!NOTE]  
>  Geben Sie beim Sortieren mehrerer Spalten mithilfe der Spalte Sortierreihenfolge die Reihenfolge an, in der die Spalten relativ zueinander durchsucht werden. Weitere Informationen finden Sie unter [Sortieren mehrerer Spalten in Abfragen &#40;Visual Database Tools&#41;](sort-multiple-columns-in-queries-visual-database-tools.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Sortieren und gruppieren Abfrageergebnisse &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Zusammenfassen von Abfrageergebnissen &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)   
 [Themen zur Vorgehensweise: Entwerfen von Abfragen und Sichten &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  