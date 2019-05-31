---
title: 'Gewusst wie: Erstellen eines neuen Datenbankprojekts | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.dbprojectwizard.importschema
- sql.data.tools.SqlProjectImportDatabaseDialog.dialog
- sql.data.tools.importscriptwizard.welcome
- sql.data.tools.importscriptwizard.summary
- sql.data.tools.SqlProjectImportDatabaseSummaryDialog.dialog
- sql.data.tools.importscriptwizard.fileselection
ms.assetid: 0b7883fa-b6e1-4ccf-b1d8-f522fd03a59d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5861f16d20d95ae6ba9d2024d2199b853934d355
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65098120"
---
# <a name="how-to-create-a-new-database-project"></a>Gewusst wie: Erstellen eines neuen Datenbankprojekts
Sie können ein neues Datenbankprojekt erstellen und das Datenbankschema aus einer vorhandenen Datenbank, einer SQL-Skriptdatei oder einer Datenebenenanwendung (".dacpac") importieren. Anschließend können Sie die gleichen Visual Designer-Tools (Transact\-SQL-Editor, Tabellen-Designer) aufrufen, die für die Entwicklung verbundener Datenbanken verfügbar sind, um Änderungen am Offlinedatenbankprojekt vorzunehmen, und die Änderungen dann wieder in der Produktionsdatenbank veröffentlichen. Die Änderungen können auch als Skript gespeichert werden, um sie später zu veröffentlichen. Mithilfe des Bereichs **Projekteigenschaften** können Sie die Zielplattform in andere Versionen von SQL Server (einschließlich SQL Azure) ändern.  
  
In den folgenden beiden Prozeduren wird durch das Erstellen eines neuen Datenbankprojekts und das Importieren des Schemas aus einer vorhandenen Datenbank im Grunde das gleiche Ziel erreicht. Jedes Datenbankobjekt wird im **Projektmappen-Explorer** als SQL-Skriptdatei (SQL) dargestellt. Weitere Informationen zum Importieren eines Datenbankschemas aus einer Momentaufnahme finden Sie unter [Vorgehensweise: Erstellen einer Momentaufnahme eines Projekts](../ssdt/how-to-create-a-snapshot-of-a-project.md).  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden die Entitäten verwendet, die in vorherigen Vorgehensweisen im Abschnitt [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) erstellt wurden.  
  
### <a name="to-create-a-new-database-project-off-a-connected-database"></a>So erstellen Sie ein neues Datenbankprojekt aus einer verbundenen Datenbank  
  
1.  Klicken Sie im **SQL Server-Objekt-Explorer** mit der rechten Maustaste auf den Knoten **TradeDev**, und klicken Sie auf **Neues Projekt erstellen**.  
  
2.  Beachten Sie, dass im Dialogfeld **Datenbank importieren** die Einstellungen für **Quelldatenbankverbindung** durch die Datenbank vordefiniert wurden, die Sie im **SQL Server-Objekt-Explorer** ausgewählt haben. Ändern Sie in der Einstellung **Zielprojekt** den Namen des Projekts in **TradeDev**.  
  
3.  Beachten Sie im Abschnitt **Importeinstellungen** die Optionen zum Importieren von bestimmten Objekten und Einstellungen sowie zum Erstellen von Ordnern für die einzelnen Schemas und/oder Objekttypen. Übernehmen Sie für eine hierarchische Anordnung sämtlicher Datenbankobjekte alle Standardeinstellungen, und klicken Sie auf **Starten**.  
  
4.  Im Dialogfeld **Datenbank importieren** werden eine Statusanzeige und eine Liste der Objekte angezeigt, die von SSDT importiert werden. Wenn der Importvorgang abgeschlossen wurde, klicken Sie auf **Fertig stellen**, um den letzten Bildschirm zu schließen.  
  
5.  Untersuchen Sie die Hierarchie im **Projektmappen-Explorer**. Erweitern Sie den Ordner **dbo**. Anschließend werden einzelne Ordner für **Funktionen**, **Tabellen** und **Sichten** angezeigt. Beachten Sie, dass die Tabellen und Funktion unter den entsprechenden Schemaordnern angeordnet sind.  
  
6.  Doppelklicken Sie unter **Tabellen** auf **Products.sql**. Der **Tabellen-Designer** wird geöffnet. Im Spaltenraster wird die visuelle Interpretation der Tabelle und im Skriptbereich die Skriptdefinition der Tabelle angezeigt. Dieser Vorgang ist mit dem Vorgang im Abschnitt [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) identisch.  
  
7.  Deaktivieren Sie das Kontrollkästchen **NULL-Werte zulassen** für die Spalte **CustomerId**. Drücken Sie STRG+S, um die Datei zu speichern.  
  
8.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **TradeDev**, und wählen Sie **Erstellen** aus, um das Datenbankprojekt zu erstellen.  
  
    Die Ergebnisse des Erstellungsvorgangs werden im Ausgabefenster angezeigt.  
  
### <a name="to-create-a-new-project-and-import-existing-database-schema"></a>So erstellen Sie ein neues Projekt und importieren ein vorhandenes Datenbankschema  
  
1.  Klicken Sie auf **Datei**, **Neu** und dann auf **Projekt**. Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** die Option **SQL Server** aus. Beachten Sie, dass nur ein Typ von Datenbankprojekt vorhanden ist: das **SQL Server-Datenbankprojekt**. Es gibt kein plattformspezifisches Projekt wie in früheren Versionen von Visual Studio. Sie können im Dialogfeld **Projekteinstellungen** die Zielplattform festlegen, nachdem das Projekt erstellt wurde. Diese Aufgabe wird im Thema [Vorgehensweise: Ändern der Zielplattform und Veröffentlichen eines Datenbankprojekts](../ssdt/how-to-change-target-platform-and-publish-a-database-project.md) behandelt.  
  
2.  Ändern Sie den Namen des Projekts in **TradeDev**, und klicken Sie auf **OK**, um das neue Projekt zu erstellen.  
  
3.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das neu erstellte Projekt **TradeDev**, und wählen Sie **Importieren** und dann **Datenbank** aus.  
  
    Das Dialogfeld **Datenbank importieren** wird geöffnet. Klicken Sie im Abschnitt **Quelldatenbankverbindung** auf **Datenbank auswählen**, und wählen Sie dann **TradeDev** aus. Wenn **TradeDev** nicht in der Dropdownliste enthalten ist, verwenden Sie die Schaltfläche **Neue Verbindung**, um die Verbindungseigenschaften zu bearbeiten.  
  
4.  Beachten Sie im Abschnitt **Importeinstellungen** die Optionen zum Importieren von bestimmten Objekten und Einstellungen sowie zum Erstellen von Ordnern für die einzelnen Schemas und/oder Objekttypen. Übernehmen Sie für eine hierarchische Anordnung sämtlicher Datenbankobjekte alle Standardeinstellungen, und klicken Sie auf **Starten**.  
  
5.  Im Dialogfeld **Datenbank importieren** werden eine Statusanzeige und eine Liste der Objekte angezeigt, die von SSDT importiert werden. Wenn der Importvorgang abgeschlossen wurde, klicken Sie auf **Fertig stellen**, um den letzten Bildschirm zu schließen.  
  
6.  Untersuchen Sie die Hierarchie im **Projektmappen-Explorer**. Erweitern Sie den Ordner **dbo**. Anschließend werden einzelne Ordner für **Funktionen**, **Tabellen** und **Sichten** angezeigt. Beachten Sie, dass die Tabellen und Funktion unter den entsprechenden Schemaordnern angeordnet sind.  
  
7.  Doppelklicken Sie unter **Tabellen** auf **Products.sql**. Der **Tabellen-Designer** wird geöffnet. Im Spaltenraster wird die visuelle Interpretation der Tabelle und im Skriptbereich die Skriptdefinition der Tabelle angezeigt. Dieser Vorgang ist mit dem Vorgang im Abschnitt [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) identisch.  
  
8.  Deaktivieren Sie das Kontrollkästchen **NULL-Werte zulassen** für die Spalte **CustomerId**. Drücken Sie STRG+S, um die Datei zu speichern.  
  
9. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **TradeDev**, und wählen Sie **Erstellen** aus, um das Datenbankprojekt zu erstellen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Vorgehensweise: Ändern der Zielplattform und Veröffentlichen eines Datenbankprojekts](../ssdt/how-to-change-target-platform-and-publish-a-database-project.md)  
  
