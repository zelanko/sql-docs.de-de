---
title: Erstellen von Tabellenerstellungsabfragen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- queries [SQL Server], types
- table creation [SQL Server], Make Table query
- inserting tables
- Make Table query
- adding tables
ms.assetid: 4493cffa-7b2d-4c24-8ef0-d49329198972
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 39adb0d3729ac171c10d3faf4d3a5956cd1c0429
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058819"
---
# <a name="create-make-table-queries-visual-database-tools"></a>Erstellen von Tabellenerstellungsabfragen (Visual Database Tools)
  Mit einer Tabellenerstellungsabfrage können Sie Zeilen in eine neue Tabelle kopieren. Dies ist hilfreich, wenn Datenteilmengen als Arbeitsgrundlage erstellt oder der Inhalt einer Tabelle von einer Datenbank in eine andere kopiert werden soll. Eine Tabellenerstellungsabfrage ähnelt einer Abfrage zum Einfügen von Ergebnissen. Jedoch wird im Unterschied dazu eine neue Tabelle erstellt, in die Zeilen kopiert werden sollen.  
  
 Beim Erstellen einer Tabellenerstellungsabfrage müssen folgende Angaben gemacht werden:  
  
-   Der Name der neuen Datenbanktabelle (der Zieltabelle)  
  
-   Die Tabelle oder Tabellen, aus der Zeilen kopiert werden sollen (die Quelltabelle) Das Kopieren ist aus einer einzelnen oder aus verknüpften Tabellen möglich.  
  
-   Die Spalten der Quelltabelle, deren Inhalt Sie kopieren möchten  
  
-   Die Sortierreihenfolge, wenn die Zeilen in einer besonderen Reihenfolge kopiert werden sollen  
  
-   Suchbedingungen zum Definieren der zu kopierenden Zeilen  
  
-   Gruppierungsoptionen, wenn Sie nur Kurzinformationen kopieren möchten.  
  
 Die folgende Abfrage erstellt z. B. eine neue Tabelle mit dem Namen `uk`_`customers` und kopiert Informationen aus der Tabelle `customers` hinein:  
  
```  
SELECT *   
INTO uk_customers  
FROM customers  
WHERE country = 'UK'  
```  
  
 Folgende Bedingungen müssen erfüllt sein, damit eine Tabellenerstellungsabfrage erfolgreich verwendet werden kann:  
  
-   Die Datenbank muss die SELECT...INTO-Syntax unterstützen.  
  
-   Sie müssen über eine Berechtigung zum Erstellen von Tabellen in der Zieldatenbank verfügen.  
  
### <a name="to-create-a-make-table-query"></a>So erstellen Sie eine Tabellenerstellungsabfrage  
  
1.  Fügen Sie dem Diagrammbereich die Quelltabellen hinzu.  
  
2.  Zeigen Sie im Menü **Abfrage-Designer** auf **Typ ändern**, und klicken Sie dann auf **Tabelle erstellen**.  
  
3.  Geben Sie im Dialogfeld **Tabelle erstellen** den Namen der Zieltabelle ein. Der Abfrage- und Sicht-Designer überprüft nicht, ob der Name bereits verwendet wird oder ob Sie über eine Berechtigung zum Erstellen der Tabelle verfügen.  
  
     Geben Sie zum Erstellen einer Zieltabelle in einer anderen Datenbank einen vollständigen Tabellennamen an, der den Namen der Zieldatenbank, den Besitzer (falls erforderlich) und den Namen der Tabelle enthält.  
  
4.  Legen Sie die zu kopierenden Spalten fest, indem Sie diese der Abfrage hinzufügen. Ausführliche Informationen finden Sie unter [Hinzufügen von Spalten zu Abfragen &#40;Visual Database Tools&#41;](visual-database-tools.md). Spalten werden nur kopiert, wenn sie der Abfrage hinzugefügt werden. Um vollständige Zeilen zu kopieren, wählen Sie  **\* (alle Spalten)**.  
  
     Der Abfrage- und Sicht-Designer fügt die ausgewählten Spalten der Spalte **Spalte** im Kriterienbereich hinzu.  
  
5.  Geben Sie eine Sortierreihenfolge an, falls Sie die Zeilen in einer bestimmten Reihenfolge kopieren möchten. Weitere Informationen finden Sie unter **Sortieren und Gruppieren von Abfrageergebnissen**.  
  
6.  Geben Sie die zu kopierenden Zeilen durch Eingabe von Suchbedingungen an. Weitere Informationen finden Sie unter [Angeben von Suchbedingungen &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).  
  
     Wenn Sie keine Suchbedingung festlegen, werden alle Zeilen der Quelltabelle in die Zieltabelle kopiert.  
  
    > [!NOTE]  
    >  Wenn Sie dem Kriterienbereich eine zu durchsuchende Spalte hinzufügen, wird diese vom Abfrage- und Sicht-Designer ebenfalls in die Liste der zu kopierenden Spalten aufgenommen. Wenn Sie eine Spalte für eine Suche verwenden, aber nicht kopieren möchten, deaktivieren Sie das Kontrollkästchen in dem Rechteck neben dem Spaltennamen, das die Tabelle oder das Objekt mit Tabellenstruktur darstellt.  
  
7.  Geben Sie Gruppierungsoptionen an, wenn Sie Kurzinformationen kopieren möchten. Weitere Informationen finden Sie unter [Zusammenfassen von Abfrageergebnissen &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md).  
  
 Beim Ausführen einer Tabellenerstellungsabfrage werden keine Ergebnisse im [Ergebnisbereich](results-pane-visual-database-tools.md)angezeigt. Stattdessen wird eine Meldung mit der Anzahl der kopierten Zeilen ausgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwerfen von Abfragen und Sichten Gewusst-wie-Themen &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Typen von Abfragen &#40;Visual Database Tools&#41;](types-of-queries-visual-database-tools.md)  
  
  