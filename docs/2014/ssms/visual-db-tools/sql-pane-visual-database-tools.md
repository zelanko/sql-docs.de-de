---
title: SQL-Bereich (Visual Database Tools) | Microsoft-Dokumentation
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
- Query Designer [SQL Server], SQL pane
- View Designer, SQL pane
- SQL pane [Visual Database Tools]
ms.assetid: dbabab18-0614-415b-a2ef-9bcd0d320d5c
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3d6261a52d4ff41923e87402327b98ff60622af7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058414"
---
# <a name="sql-pane-visual-database-tools"></a>SQL-Bereich (Visual Database Tools)
  Sie können den SQL-Bereich verwenden, um eine eigene SQL-Anweisung zu erstellen. Sie können auch den Kriterienbereich und den Diagrammbereich verwenden, um die Anweisung zu erstellen, wobei dadurch die SQL-Anweisungen im SQL-Bereich erstellt werden. Beim Erstellen einer Abfrage wird der SQL-Bereich automatisch aktualisiert und neu formatiert, um die Lesbarkeit zu verbessern.  
  
 Öffnen Sie zuerst den Abfrage- und Sicht-Designer, um den SQL-Bereich zu öffnen. (Wählen Sie dazu im Server-Explorer ein Datenbankobjekt aus, und klicken Sie im Menü **Datenbank** auf **Neue Abfrage**.) Zeigen Sie dann im Menü **Abfrage-Designer** auf **Bereich** , und klicken Sie auf **SQL**.  
  
 Im SQL-Bereich können Sie folgende Aktionen ausführen:  
  
-   neue Abfragen durch die Eingabe von SQL-Anweisungen erstellen  
  
-   die SQL-Anweisung ändern, die vom Abfrage- und Sicht-Designer basierend auf Ihren Einstellungen im Diagrammbereich und im Kriterienbereich erstellt wurde.  
  
-   Anweisungen eingeben, die auf spezielle Funktionen der von Ihnen verwendeten Datenbank zugreifen  
  
> [!NOTE]  
>  Machen Sie sich mit den Regeln vertraut, über die Datenbankobjekte in der von Ihnen verwendeten Datenbank identifiziert werden können. Ausführliche Informationen finden Sie in der Dokumentation des Datenbankverwaltungssystems.  
  
## <a name="statements-in-the-sql-pane"></a>Anweisungen im SQL-Bereich  
 Sie können die aktuelle Abfrage direkt im SQL-Bereich bearbeiten. Sobald Sie in einen anderen Bereich wechseln, formatiert der Abfrage- und Sicht-Designer automatisch Ihre Anweisung und aktualisiert anschließend die Angaben im Diagrammbereich und im Kriterienbereich.  
  
 Wenn der Diagramm- und der Kriterienbereich angezeigt werden und Ihre Anweisung nicht in diesen Bereichen dargestellt werden kann, meldet der Abfrage- und Sicht-Designer einen Fehler und bietet Ihnen zwei Optionen an:  
  
-   Ignorieren, dass die Anweisung nicht im Diagrammbereich und im Kriterienbereich dargestellt werden kann.  
  
-   Rückgängigmachen der nicht darstellbaren Änderung und Zurücksetzen auf die aktuellste Version der SQL-Anweisung.  
  
 Wenn Sie ignorieren, dass die Anweisung nicht im Diagrammbereich und im Kriterienbereich dargestellt werden kann, werden die anderen Bereiche im Abfrage- und Sicht-Designer ausgeblendet. Damit wird angegeben, dass der Inhalt des SQL-Bereichs in diesen Bereichen nicht wiedergegeben wird.  
  
 Sie können mit dem Bearbeiten der Anweisung fortfahren und diese wie jede andere SQL-Anweisung ausführen.  
  
> [!NOTE]  
>  Wenn Sie eine SQL-Anweisung eingeben und anschließend weitere Änderungen an der Abfrage im Diagrammbereich bzw. Kriterienbereich vornehmen, erstellt der Abfrage- und Sicht-Designer die SQL-Anweisung neu und aktualisiert ihre Anzeige. In einigen Fällen wird hierbei eine SQL-Anweisung generiert, die in ihrer Struktur von der ursprünglich eingegebenen Anweisung abweicht (jedoch nach wie vor die gleichen Ergebnisse liefert). Diese Abweichung tritt häufig dann auf, wenn Sie Suchbedingungen verwenden, in denen mehrere Klauseln durch AND und OR verknüpft wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Ausführen von Abfragen &#40;Visual Database Tools&#41;](run-queries-visual-database-tools.md)   
 [Entwerfen von Abfragen und Sichten Gewusst-wie-Themen &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Diagrammbereich &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md)   
 [Im Kriterienbereich &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md)   
 [Ergebnisbereich &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md)  
  
  