---
title: Vergleichen von verschiedenen Datenbankdefinitionen mithilfe des Schemavergleichs
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
f1_keywords:
- sql.data.tools.schemacompare.SchemaCompareOptionsDialog
- sql.data.tools.schemacompare.watermark.f1
- sql.data.tools.schemacompare.f1
- sql.data.tools.schemacompare.connectiondialog.f1
- sql.data.tools.schemacompare.connectiondialog.error.f1
ms.assetid: 7f0905a4-081c-46e2-bd7d-325b63e5c675
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: f31d543906e4bfedb16e412be703ebc8cd797a04
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75226854"
---
# <a name="how-to-use-schema-compare-to-compare-different-database-definitions"></a>Gewusst wie: Vergleichen von verschiedenen Datenbankdefinitionen mithilfe des Schemavergleichs

SQL Server Data Tools (SSDT) enthält ein Hilfsprogramm für den Schemavergleich, mit dem Sie zwei Datenbankdefinitionen vergleichen können.  Bei der Quelle und dem Ziel des Vergleichs kann es sich um eine beliebige Kombination von verbundener Datenbank, SQL Server-Datenbankprojekt bzw. -Momentaufnahme oder DACPAC-Datei handeln.  Die Ergebnisse des Vergleichs werden als Satz von Aktionen angezeigt, die für das Ziel ausgeführt werden müssen, damit es mit der Quelle identisch ist.  Nach Abschluss des Vergleichs können Sie das Ziel direkt aktualisieren (wenn das Ziel ein Projekt oder eine Datenbank ist) oder ein Updateskript generieren, das den gleichen Zweck erfüllt.  
  
Die Unterschiede zwischen Quelle und Ziel werden zur einfachen Überprüfung in einem Raster angezeigt.  Sie können einen Drilldown auf die einzelnen Unterschiede im Ergebnisraster oder im Skriptformular ausführen und sie überprüfen.  Anschließend können Sie bestimmte Unterschiede selektiv ausschließen.  
  
Sie können Vergleiche als Teil eines SQL Server-Datenbankprojekts oder als eigenständige Datei speichern.  Sie können außerdem Optionen festlegen, mit denen der Bereich des Vergleichs und Aspekte des Updates gesteuert werden.  Anschließend können Sie den Vergleich speichern, sodass Sie denselben Vergleich später einfach wiederholen oder als Ausgangspunkt für einen neuen Vergleich verwenden können.  
  
In der folgenden Prozedur wird das Schema eines Datenbankprojekts mit einer verbundenen Datenbank verglichen.  
  
> [!WARNING]  
> Beim Angeben eines Projekts als Ziel für den Vergleich beträgt die unterstützte Pfadlänge für das Projekt (ohne Laufwerkbuchstabe, Doppelpunkt und führenden umgekehrten Schrägstrich) maximal 256 Zeichen. Wenn der Projektpfad 256 Zeichen überschreitet, sind Sie immer noch in der Lage, das zugehörige Schema mit einer Datenbank oder einem anderen Projekt zu vergleichen. Sie können jedoch das Schema nicht aktualisieren.  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden Entitäten verwendet, die in vorherigen Vorgehensweisen in den Abschnitten [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) und [Projektorientierte Entwicklung von Offlinedatenbanken](../ssdt/project-oriented-offline-database-development.md) erstellt wurden.  
  
### <a name="to-compare-database-definitions"></a>So vergleichen Sie Datenbankdefinitionen  
  
1.  Klicken Sie im Menü **SQL** auf **Schemavergleich**, und klicken Sie dann auf **Neuer Schemavergleich**.  
  
    Sie können auch im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **TradeDev** klicken und **Schemavergleich** auswählen.  
  
    Das Fenster **Schemavergleich** wird geöffnet, und Visual Studio weist diesem automatisch einen Namen zu, z.B. `SqlSchemaCompare1`.  
  
    Direkt unter der Symbolleiste des Fensters **Schemavergleich** werden zwei Dropdownmenüs angezeigt, zwischen denen sich ein grüner Pfeil befindet. In diesen Menüs können Sie Datenbankdefinitionen für die Quelle und das Ziel des Vergleichs auswählen.  
  
2.  Wählen Sie im Dropdownmenü **Quelle auswählen** die Option **Quelle auswählen** aus. Das Dialogfeld **Quellschema auswählen** wird geöffnet.  
  
    Wenn Sie das Fenster **Schemavergleich** durch Klicken mit der rechten Maustaste auf den Projektnamen geöffnet haben, ist das Quellschema bereits aufgefüllt, und Sie können mit Schritt 4 fortfahren.  
  
3.  Aktivieren Sie das Optionsfeld **Projekt**, und wählen Sie dann das Datenbankprojekt **TradeDev** aus, das Sie im vorherigen Verfahren erstellt haben.  
  
4.  Wählen Sie im Dropdownmenü **Ziel auswählen** des Fensters **Schemavergleich** die Option **Ziel auswählen** aus. Daraufhin wird das Dialogfeld **Zielschema auswählen** geöffnet. Klicken Sie im Abschnitt **Schema** auf das Optionsfeld **Datenbank**. Klicken Sie anschließend auf die Schaltfläche **Neue Verbindung**.  
  
5.  Geben Sie im Dialogfeld **Verbindungseigenschaften** den Namen des Servers ein, auf dem sich die Datenbank `TradeDev` befindet. Stellen Sie sicher, dass richtige Anmeldeinformationen zur Authentifizierung angegeben sind. Wählen Sie dann im Feld **Mit Datenbank verbinden** die Datenbank **TradeDev** aus, und klicken Sie auf **OK**.  
  
    Sie können auch auf der Symbolleiste des Fensters **Schemavergleich** auf die Schaltfläche **Optionen** klicken, um die miteinander zu vergleichenden Objekte, die zu ignorierenden Unterschiede und weitere Einstellungen anzugeben.  
  
6.  Klicken Sie auf der Symbolleiste des Fensters **Schemavergleich** auf die Schaltfläche **Vergleichen**, um den Vergleichsvorgang zu starten.  
  
    Bei Abschluss des Vergleichs werden im oberen Teil des Fensters im **Ergebnisbereich** die strukturellen Unterschiede zwischen dem Projekt und der Datenbank angezeigt. In den Vergleichsergebnissen sind standardmäßig alle Unterschiede nach Aktion (z. B. "Löschen", "Ändern" oder "Hinzufügen") gruppiert. Im **Ergebnisbereich** wird eine Zeile für jedes Datenbankobjekt angezeigt, das sich in den Datenbankdefinitionen unterscheidet. In jeder Zeile werden das Objekt im Quell- oder Zielschema (oder in beiden Schemas) und die für das Zielschema auszuführende Aktion angegeben, durch die das Zielobjekt mit dem Quellobjekt identisch wird.  Wenn ein Objekt umgestaltet und entweder umbenannt oder in ein neues Schema verschoben wurde, sind der Quell- und Zielname unterschiedlich, und der Quellname wird fett formatiert angezeigt, um den Unterschied hervorzuheben.  
  
    Standardmäßig werden in der Ergebnisliste Objekte ausgeblendet, die in beiden Schemas gleich sind oder deren Update nicht unterstützt wird (z. B. integrierte Objekte).  Sie können auf der Symbolleiste auf die entsprechenden Filterschaltflächen klicken, um diese Objekte anzuzeigen.  
  
    Um die Gruppierungseinstellung zu ändern, klicken Sie auf der Symbolleiste auf die Dropdownliste **Ergebnisse gruppieren**.  Wählen Sie **Typ** aus, um die Ergebnisse nach Objekttyp (z.B. nach Tabellen, Sichten oder gespeicherten Prozeduren) zu gruppieren.  
  
7.  Suchen Sie in der Gruppe `Products` die Tabelle `Tables`. Klicken Sie auf die Zeile, und beachten Sie, dass im Bereich **Objektdefinitionen** die Quell- und Zieldefinition der Tabelle angezeigt werden, wobei die Unterschiede markiert sind. Sie können auch im Bereich **Ergebnisse** die Tabellenzeile `Products` erweitern, um die Elemente in der Tabelle zu untersuchen, die unterschiedlich sind.  
  
8.  Standardmäßig sind im Anwendungsbereich der Aktion "Ziel aktualisieren" alle Unterschiede enthalten. Sie können Unterschiede ausschließen, die nicht synchronisiert werden sollen. Hierzu deaktivieren Sie in der Mitte jeder Zeile die Spalte **Aktion**. Sie können auch im Bereich „Schema“ mit der rechten Maustaste auf eine Zeile klicken und **Ausschließen** auswählen. Beachten Sie, dass die Zeile sofort ausgegraut wird. Beim Aktualisieren der Zieldatenbank wird diese Zeile bei ausstehenden Änderungen nicht berücksichtigt.  
  
    Sie können auch mit der rechten Maustaste auf eine Gruppenzeile klicken und **Alle ausschließen** oder **Alle einschließen** auswählen. Dies entspricht dem Markieren bzw. Aufheben der Markierung aller Unterschiede in der Gruppe. Wenn Sie Ergebnisse nach Schema gruppieren, empfiehlt sich dieses Verfahren, um alle Änderungen an einem bestimmten Schema einzuschließen oder auszuschließen.  
  
    > [!WARNING]  
    > Wenn die ausgeschlossene Zeile über abhängige Objekte verfügt (z.B. eine **Tabellen**-Zeile, auf die von einer **Sicht**-Zeile verwiesen wird), wird die ausgeschlossene Zeile deaktiviert, jedoch nicht das zugehörige Kontrollkästchen. Wenn alle davon abhängigen Zeilen deaktiviert wurden, wird auch das Kontrollkästchen der deaktivierten Zeile deaktiviert. Wenn eine Zeile außerdem umgestaltet (umbenannt oder in ein anderes Schema verschoben) wird, werden das Kontrollkästchen für die Zeile und alle abhängigen untergeordneten Zeilen deaktiviert.  
    >   
    > Beachten Sie, dass die zu überspringenden Unterschiede beim Aktualisieren des Vergleichs ignoriert werden.  
  
Sie haben zwei Möglichkeiten zum Aktualisieren des Schemas der Zieldatenbank. Sie können das Ziel direkt über das Fenster **Schemavergleich** aktualisieren, wenn das Ziel eine Datenbank oder ein Projekt ist, oder Sie können ein Updateskript generieren, wenn das Ziel eine Datenbank oder Datenbankdatei ist.  Ein generiertes Skript wird im Transact\-SQL-Editor angezeigt. Dort können Sie das Skript untersuchen und für eine Datenbank ausführen. Diese Optionen werden in den folgenden Prozeduren ausführlicher beschrieben.  
  
> [!WARNING]  
> Das Update schlägt fehl, weil durch die Änderung eine Spalte von NOT NULL in NULL geändert wird und dies zu Datenverlust führt. Wenn Sie mit dem Update fortfahren möchten, klicken Sie auf der Symbolleiste für „Schemavergleich“ auf die Schaltfläche **Optionen** (die fünfte Schaltfläche von links), und deaktivieren Sie die Option **Inkrementelle Bereitstellung bei Datenverlust blockieren**.  
  
### <a name="to-update-directly-in-the-schema-compare-window"></a>So führen Sie ein direktes Update im Fenster "Schemavergleich" aus  
  
1.  Klicken Sie auf der Symbolleiste für das Fenster „Schemavergleich“ auf die Schaltfläche **Aktualisieren**.  
  
2.  Untersuchen Sie das generierte Änderungsskript. Sie können das Skript speichern, indem Sie im Menü "Datei" die Option "Neu" auswählen. Dies kann sich in Situationen empfehlen, wenn Sie nicht berechtigt sind, eine Produktionsdatenbank zu aktualisieren. In einem solchen Fall können Sie das Skript zur späteren Bereitstellung an einen Datenbankadministrator übermitteln.  
  
3.  Wenn Sie über die erforderliche Berechtigung zum Aktualisieren der Datenbank verfügen, klicken Sie auf der Symbolleiste des Bearbeitungsbereichs auf die Schaltfläche **Abfrage ausführen**, um das Skript auszuführen.  
  
### <a name="to-update-by-script"></a>So aktualisieren Sie mithilfe eines Skripts  
  
1.  Klicken Sie auf der Symbolleiste für das Fenster Schemavergleich auf die Schaltfläche **Skript generieren** (die vierte Schaltfläche von links).  
  
    Das generierte Skript wird in einem neuen Transact\-SQL-Editor-Fenster geöffnet.  
  
    > [!WARNING]  
    > Dieses Verhalten wird nur von DACPAC-Dateien unterstützt, die durch SSDT-Momentaufnahmen erzeugt werden.  Sie können zu diesem Zeitpunkt keine DACPAC-Datei als Ziel auswählen, die von den SQL Server-Datenebenenanwendungs-Tools (DAC) oder dem SQL Server-Datenebenenanwendungs-Framework erzeugt wurden.  
  
2.  Untersuchen Sie das generierte Änderungsskript. Sie können das Skript mit dem Menübefehl **Datei/Speichern** oder „Datei/Speichern unter“ speichern.  
  
    Ein gespeichertes Skript kann in Situationen hilfreich sein, wenn Sie nicht berechtigt sind, eine Produktionsdatenbank zu aktualisieren. In einem solchen Fall können Sie das Skript zur späteren Bereitstellung an einen Datenbankadministrator übermitteln.  
  
    Alternativ können Sie eine Verbindung zwischen dem Transact\-SQL-Editor und einem entsprechenden Server herstellen und das Skript direkt ausführen. Bevor Sie diese Prozedur ausführen können, müssen Sie über die Berechtigung zum Erstellen oder Aktualisieren der Datenbank verfügen. Wenn Sie über die erforderliche Berechtigung zum Aktualisieren der Datenbank verfügen, klicken Sie auf der Symbolleiste des Bearbeitungsbereichs auf die Schaltfläche **Abfrage ausführen**, um das Skript auszuführen.  
  
3.  Klicken Sie auf die Schaltfläche **Verbinden**. Hierdurch wird entweder eine Verbindung mit dem aktuellen Server hergestellt, oder Sie werden im Dialogfeld "Verbindung mit Server herstellen" aufgefordert, einen Server einzugeben oder auszuwählen.  Der Datenbankname ist im Skript als Befehlsvariable definiert.  
  
4.  Überprüfen Sie das Skript, und nehmen Sie ggf. Änderungen an den Befehlsvariablen vor, die den Namen der Zieldatenbank sowie das zugehörige Präfix und die Dateipfade definieren.  
  
5.  Klicken Sie auf der Symbolleiste des Bearbeitungsbereichs auf die Schaltfläche **Ausführen**, um das Skript auszuführen.  
  
