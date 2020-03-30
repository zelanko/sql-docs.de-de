---
title: Erstellen von Löschabfragen
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
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
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: cb40fee1f7176c9d1fe64e22cda220513f88d58e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75254371"
---
# <a name="create-delete-queries-visual-database-tools"></a>Löschen von Abfragen (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Sie können alle Zeilen in einer Tabelle löschen, indem Sie eine Löschabfrage verwenden.  
  
> [!NOTE]  
> Wenn Sie alle Zeilen in einer Tabelle löschen, werden zwar die enthaltenen Daten, jedoch nicht die Tabelle selbst gelöscht. Um eine Tabelle in einer Datenbank zu löschen, klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Tabelle, und klicken Sie dann auf **Löschen**.  
  
Wenn Sie eine Löschabfrage erstellen, ändert sich der Kriterienbereich entsprechend und zeigt die verfügbaren Optionen zum Löschen von Zeilen an. Da in einer Löschabfrage keine Daten angezeigt werden, sind die Spalten "Ausgabe", "Sortieren nach" und "Sortierreihenfolge" ausgeblendet. Außerdem werden die Kontrollkästchen neben den Spaltennamen in dem Rechteck, das die Tabelle oder das Tabellenwertobjekt darstellt, nicht mehr angezeigt, da keine einzelnen Spalten zum Löschen angegeben werden können.  
  
Falls der Abfrage- und Sicht-Designer eine oder mehrere der Zeilen nicht löschen kann, werden keine Zeilen gelöscht. Eine Meldung gibt an, welche Zeilen Informationen enthalten, die nicht aus der Datenbank gelöscht werden können.  
  
> [!CAUTION]  
> Eine ausgeführte Löschabfrage kann nicht mehr rückgängig gemacht werden. Erstellen Sie vorsichtshalber vor Ausführung der Löschabfrage eine Sicherungskopie der Daten.  
  
### <a name="to-create-a-delete-query"></a>So erstellen Sie eine Löschabfrage  
  
1.  Fügen Sie dem Diagrammbereich die Tabelle hinzu, aus der Zeilen gelöscht werden sollen.  
  
2.  Zeigen Sie im Menü **Abfrage-Designer** auf **Typ ändern**, und klicken Sie dann auf **Löschen**. **Hinweis** Wenn beim Starten der Löschabfrage mehrere Tabellen im Diagrammbereich angezeigt werden, zeigt der Abfrage- und Sicht-Designer das [Dialogfeld „Tabelle löschen“](../../ssms/visual-db-tools/delete-table-dialog-box-visual-database-tools.md) an, in dem Sie zur Eingabe des Namens der Tabelle aufgefordert werden, aus der Zeilen gelöscht werden sollen.  
  
Beim Ausführen einer Löschabfrage werden keine Ergebnisse im [Ergebnisbereich](../../ssms/visual-db-tools/results-pane-visual-database-tools.md)angezeigt. Stattdessen wird eine Meldung mit der Anzahl der gelöschten Zeilen angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Unterstützte Abfragetypen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Themen zur Vorgehensweise: Entwerfen von Abfragen und Sichten &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
