---
title: Sortieren in aufsteigender oder absteigender Reihenfolge (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- descending sorts
- ascending sorts
ms.assetid: d61cc55b-9ee8-4ecf-a32f-6459ae43910b
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: baae353ae8528c6c62e41afbec84d30772d561c3
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65099268"
---
# <a name="sort-in-ascending-or-descending-order-visual-database-tools"></a>Sortieren in aufsteigender oder absteigender Reihenfolge (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Mithilfe der Schlüsselwörter **ASC** und **DESC** mit der **ORDER BY** -Klausel können Abfrageergebnisse in einer oder mehreren Spalten des Resultsets in auf- oder absteigender Reihenfolge sortiert werden.  
  
> [!NOTE]  
> Die Sortierreihenfolge wird teilweise durch die Sortierreihenfolge der Spalte bestimmt. Sie können die Sortierreihenfolge im [Dialogfeld Sortierreihenfolge](../../ssms/visual-db-tools/collation-dialog-box-visual-database-tools.md)ändern.  
  
Bei der folgenden Prozedur wird vorausgesetzt, dass im Abfrage- und Sicht-Designer eine Abfrage geöffnet ist, in der zum Sortieren einer oder mehrerer Spalten die ORDER BY-Klausel verwendet wird.  
  
### <a name="to-specify-or-change-the-order-in-which-results-are-sorted"></a>So geben Sie die Sortierreihenfolge der Ergebnisse an und ändern diese  
  
1.  Klicken Sie im [Kriterienbereich](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)für die neu zu sortierende Spalte auf das Feld **Sortierungsart** .  
  
2.  Wählen Sie **Aufsteigend** oder **Absteigend** aus, um die Sortierreihenfolge für die Spalte anzugeben.  
  
Beachten Sie beim Arbeiten im Kriterienbereich, dass die UNION-Klausel der Abfrage entsprechend der zuletzt ausgeführten Aktionen geändert wird.  
  
> [!NOTE]  
> Geben Sie beim Sortieren mehrerer Spalten mithilfe der Spalte Sortierreihenfolge die Reihenfolge an, in der die Spalten relativ zueinander durchsucht werden. Weitere Informationen finden Sie unter [Sortieren mehrerer Spalten in Abfragen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-multiple-columns-in-queries-visual-database-tools.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Sortieren und Gruppieren von Abfrageergebnissen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Zusammenfassen von Abfrageergebnissen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Themen zur Vorgehensweise: Entwerfen von Abfragen und Sichten &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
