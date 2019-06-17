---
title: Erstellen von Löschabfragen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- row removal [SQL Server], Delete query
- Delete query
- queries [SQL Server], types
- removing rows
- removing data
- data deletions [SQL Server]
- deleting rows
- deleting data
ms.assetid: 0db3af43-1ec4-48c8-b769-2bb9c76d3434
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f1103e1715c01cfc868c59af17ee0f95fa7cedff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62661684"
---
# <a name="create-delete-queries-visual-database-tools"></a>Löschen von Abfragen (Visual Database Tools)
  Sie können alle Zeilen in einer Tabelle löschen, indem Sie eine Löschabfrage verwenden.  
  
> [!NOTE]  
>  Wenn Sie alle Zeilen in einer Tabelle löschen, werden zwar die enthaltenen Daten, jedoch nicht die Tabelle selbst gelöscht. Um eine Tabelle in einer Datenbank zu löschen, klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Tabelle, und klicken Sie dann auf **Löschen**.  
  
 Wenn Sie eine Löschabfrage erstellen, ändert sich der Kriterienbereich entsprechend und zeigt die verfügbaren Optionen zum Löschen von Zeilen an. Da in einer Löschabfrage keine Daten angezeigt werden, sind die Spalten "Ausgabe", "Sortieren nach" und "Sortierreihenfolge" ausgeblendet. Außerdem werden die Kontrollkästchen neben den Spaltennamen in dem Rechteck, das die Tabelle oder das Tabellenwertobjekt darstellt, nicht mehr angezeigt, da keine einzelnen Spalten zum Löschen angegeben werden können.  
  
 Falls der Abfrage- und Sicht-Designer eine oder mehrere der Zeilen nicht löschen kann, werden keine Zeilen gelöscht. Eine Meldung gibt an, welche Zeilen Informationen enthalten, die nicht aus der Datenbank gelöscht werden können.  
  
> [!CAUTION]  
>  Eine ausgeführte Löschabfrage kann nicht mehr rückgängig gemacht werden. Erstellen Sie vorsichtshalber vor Ausführung der Löschabfrage eine Sicherungskopie der Daten.  
  
### <a name="to-create-a-delete-query"></a>So erstellen Sie eine Löschabfrage  
  
1.  Fügen Sie dem Diagrammbereich die Tabelle hinzu, aus der Zeilen gelöscht werden sollen.  
  
2.  Zeigen Sie im Menü **Abfrage-Designer** auf **Typ ändern**, und klicken Sie dann auf **Löschen**. **Hinweis** Wenn beim Starten der Löschabfrage mehrere Tabellen im Diagrammbereich angezeigt werden, zeigt der Abfrage- und Sicht-Designer das [Dialogfeld „Tabelle löschen“](visual-database-tools.md) an, in dem Sie zur Eingabe des Namens der Tabelle aufgefordert werden, aus der Zeilen gelöscht werden sollen.  
  
 Beim Ausführen einer Löschabfrage werden keine Ergebnisse im [Ergebnisbereich](results-pane-visual-database-tools.md)angezeigt. Stattdessen wird eine Meldung mit der Anzahl der gelöschten Zeilen angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützte Abfragetypen &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md)   
 [Themen zur Vorgehensweise: Entwerfen von Abfragen und Sichten &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
