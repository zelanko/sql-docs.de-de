---
title: Verwenden des Transact-SQL-Editors zum Bearbeiten und Ausführen von Skripts | Microsoft-Dokumentation
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL.DATA.TOOLS.SQLEDITOR
ms.assetid: fa78e2cf-3c64-49f5-93cc-a3d50b1e7d05
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eccaf60d648824e2f170bf1fd78b8a8f1a16dc28
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094165"
---
# <a name="use-transact-sql-editor-to-edit-and-execute-scripts"></a>Verwenden des Transact-SQL-Editors zum Bearbeiten und Ausführen von Skripts
Der Transact\-SQL-Editor stellt vielfältige Funktionen zum Bearbeiten und Debuggen von Skripts bereit. Er wird aufgerufen, wenn Sie eine Datenbankentität in einer verbundenen Datenbank oder einem Projekt über das Kontextmenü **Code anzeigen** öffnen. Er wird auch automatisch geöffnet, wenn Sie das Kontextmenü **Neue Abfrage** im SQL Server-Objekt-Explorer aufrufen und wenn Sie einem Datenbankprojekt ein neues Skriptobjekt hinzufügen.  
  
Wenn Sie mit keiner Datenbank verbunden sind, aber eine Abfrage für eine Datenbank ausführen möchten, können Sie auch mit dem Dialogfeld **Neue Abfrageverbindung** (Menüoption **SQL** -> **Transact\-SQL-Editor**) eine Verbindung mit einer Datenbank herstellen und den Transact\-SQL-Editor starten.  
  
Der Transact\-SQL-Editor enthält den **T-SQL**-Hauptbereich, in dem Sie Transact\-SQL-Skripts schreiben und bearbeiten können. Der Editor unterstützt IntelliSense sowie die Farbcodierung der Syntax, um die Lesbarkeit von komplexen Anweisungen zu verbessern. Darüber hinaus werden Suchen und Ersetzen, Massenkommentare, benutzerdefinierte Schriftarten und Farben sowie Zeilennummerierung unterstützt. Sie können auch die Datenbank ändern, für die das Skript im Editor ausgeführt wird. Weitere Informationen finden Sie unter [Gewusst wie: Klonen einer vorhandenen Datenbank](../ssdt/how-to-clone-an-existing-database.md). Die Abfrageergebnisse werden im Bereich **Ergebnisse** in einem Raster oder als Text angezeigt. Außerdem können Sie Abfrageergebnisse in eine Datei umleiten. Im Bereich **Meldung** werden Fehler, Warnungen und Informationsmeldungen angezeigt, die bei der Ausführung eines Skripts zurückgegeben wurden. Wenn Clientstatistiken aktiviert sind, werden im Bereich **Statistik** nach Kategorien geordnete Informationen zur Abfrageausführung angezeigt. Im Bereich **Ausführungsplan** werden die von SQL Server ausgewählten Datenabrufmethoden angezeigt. Zudem werden die Ausführungskosten für bestimmte Anweisungen und Abfragen angegeben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|und Beschreibung|  
|---------|---------------|  
|[Gewusst wie: Gliedern und Hinzufügen von Ausschnitten zu Transact-SQL-Skripts](../ssdt/how-to-outline-and-add-snippets-to-transact-sql-script.md)|Verwenden Sie die Codeausschnittauswahl, um fertigen Transact\-SQL-Code in die Abfrage einzufügen.|  
|[Gewusst wie: Navigieren zwischen Skripts](../ssdt/how-to-navigate-between-scripts.md)|Navigieren Sie mithilfe von "Gehe zu Definition" und "Alle Verweise suchen" zwischen Skripts.|  
|[Gewusst wie: Vornehmen von Änderungen an Datenbankobjekten durch Umbenennen und Refactoring](../ssdt/how-to-use-rename-and-refactoring-to-make-changes-to-your-database-objects.md)|Benennen Sie ein Objekt für alle Skripts um, und überprüfen Sie die Änderungen in der Vorschau.|  
|[Gewusst wie: Ausführen einer Teilabfrage](../ssdt/how-to-execute-a-partial-query.md)|Heben Sie ein bestimmtes Segment des Skripts hervor, und führen Sie es als Einzelabfrage aus.|  
|[Gewusst wie: Debuggen von gespeicherten Prozeduren](../ssdt/how-to-debug-stored-procedures.md)|Erstellen und debuggen Sie eine gespeicherte Transact\-SQL-Prozedur, indem Sie sie in Einzelschritten ausführen.|  
|[Analysieren der Skriptleistung](../ssdt/analyze-script-performance.md)|Bestimmen Sie anhand von Ausführungsplänen, Clientstatistiken und Codeanalysen, ob die Leistung von Abfragen, gespeicherten Prozeduren oder Skripts verbessert werden kann.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Gewusst wie: Erstellen von neuen Datenbankobjekten mit Abfragen](../ssdt/how-to-create-new-database-objects-using-queries.md)  
  
