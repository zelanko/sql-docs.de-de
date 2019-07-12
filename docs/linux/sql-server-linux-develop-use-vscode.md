---
title: Verwenden Sie die Visual Studio Code-Mssql-Erweiterung für SQL Server
titleSuffix: SQL Server
description: Verwenden Sie die Mssql-Erweiterung für Visual Studio Code zum Bearbeiten und Ausführen von Transact-SQL-Skripts für SQL Server unter Linux.
author: VanMSFT
ms.author: vanto
manager: jroth
ms.date: 12/18/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 9766ee75-32d3-4045-82a6-4c7968bdbaa6
ms.openlocfilehash: fcda7a310e7a9dc77ea9464dd82dbed7260b0b39
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833796"
---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts"></a>Verwenden von Visual Studio Code zum Erstellen und Ausführen von Transact-SQL-Skripts

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird gezeigt, wie Sie mit der **Mssql** -Erweiterung für Visual Studio Code zum Entwickeln von SQL Server-Datenbanken. Da Visual Studio Code plattformübergreifend ist, können Sie **Mssql** Erweiterung für Linux, MacOS und Windows.

## <a name="install-and-start-visual-studio-code"></a>Installieren Sie und starten Sie Visual Studio Code

Visual Studio Code ist ein plattformübergreifendes, grafische-Code-Editor, der Erweiterungen unterstützt.

1. [Herunterladen und installieren Sie Visual Studio Code](https://code.visualstudio.com/) auf Ihrem Computer.

1. Starten Sie Visual Studio Code.

   >[!NOTE]
   >Wenn Visual Studio Code nicht gestartet wird, wenn Sie über eine Remotedesktopsitzung von "xrdp" verbunden sind, finden Sie unter [VS Code funktioniert nicht unter Ubuntu, wenn eine Verbindung besteht, mithilfe von "xrdp"](https://github.com/Microsoft/vscode/issues/3451).

## <a name="install-the-mssql-extension"></a>Installieren Sie die Mssql-Erweiterung

Die [Mssql-Erweiterung für Visual Studio Code](https://aka.ms/mssql-marketplace) ermöglicht die Verbindung mit einer SQL-Server, Abfragen mit Transact-SQL (T-SQL), und die Ergebnisse anzuzeigen.

1. Wählen Sie in Visual Studio Code **Ansicht** > **Befehlspalette**, oder drücken Sie **STRG**+**UMSCHALT** + **P**, oder drücken Sie **F1** zum Öffnen der **Befehlspalette**.

1. In der **Befehlspalette**Option **Erweiterungen: Installieren von Erweiterungen** aus der Dropdownliste aus. 

1. In der **Erweiterungen** im Bereich *Mssql*.

1. Wählen Sie die **SQL Server (Mssql)** -Erweiterung, und wählen Sie dann **installieren**.

   ![Installieren Sie die Mssql-Erweiterung](./media/sql-server-linux-develop-use-vscode/vscode-extension.png)

1. Wählen Sie nach Abschluss der Installation **Reload** zum Aktivieren der Erweiterung.

## <a name="create-or-open-a-sql-file"></a>Erstellen Sie oder öffnen Sie eine SQL-Datei

Die Mssql-Erweiterung Mssql-Befehlen und T-SQL IntelliSense bei der Language-Modus, um festgelegt ist im Code-Editor ermöglicht **SQL**.

1. Wählen Sie **Datei** > **neue Datei** , oder drücken Sie **STRG**+**N**. Visual Studio Code öffnet eine neue nur-Text-Datei wird standardmäßig an. 

1. Wählen Sie **nur-Text** auf der unteren Statusleiste, oder drücken Sie **STRG**+**K** > **M**, und wählen Sie **SQL** aus der Dropdownliste "Sprachen" aus. 

   ![Sprachmodus "SQL"](./media/sql-server-linux-develop-use-vscode/vscode-language-mode.png)

   > [!NOTE]
   > Ist dies beim ersten Verwenden Sie die Erweiterung verwendet haben, wird die Erweiterung unterstützen SQL Server-Tools installiert.

Wenn Sie eine vorhandene Datei öffnen, die eine *.sql* -Erweiterung, der Sprachmodus automatisch auf SQL festgelegt.  

## <a name="connect-to-sql-server"></a>Verbindung mit SQL Server herstellen

Um ein Verbindungsprofil erstellen und eine Verbindung mit einer SQL Server, gehen Sie wie folgt vor.

1. Drücken Sie **STRG**+**UMSCHALT**+**P** oder **F1** zum Öffnen der **Befehlspalette**. 

1. Typ *Sql* zum Anzeigen der Mssql-Befehle oder Typ *Sqlcon*, und wählen Sie dann **MS SQL: Herstellen einer mit** aus der Dropdownliste aus.

   ![MSSQL-Befehlen](./media/sql-server-linux-develop-use-vscode/vscode-commands.png)

   >[!NOTE]
   >Eine SQL-Datei, müssen z. B. die leere SQL-Datei, die Sie erstellt haben, die Fokus im Code-Editor, bevor Sie die Mssql-Befehle ausführen können.

1. Wählen Sie die **MS SQL: Verwalten von Remoteverbindungsprofilen** Befehl.

1. Wählen Sie dann **erstellen** um ein neues Verbindungsprofil für Ihre SQL Server zu erstellen.

1. Führen Sie die Anweisungen aus, um die Eigenschaften für das neue Verbindungsprofil anzugeben. Wenn Sie jeden Wert angegeben, drücken Sie die **EINGABETASTE** um den Vorgang fortzusetzen.

   | Verbindungseigenschaft | Beschreibung |
   |---|---|
   | **Servername oder die ADO-Verbindungszeichenfolge** | Geben Sie den Namen der SQL Server-Instanz. Verwendung *"localhost"* zur Verbindung mit SQL Server-Instanz auf dem lokalen Computer. Geben Sie zum Verbinden mit einem Remotecomputer mit SQL Server den Namen des Zielcomputers mit SQL Server oder die IP-Adresse ein. Geben Sie die IP-Adresse des Containers-Hostcomputer zum Verbinden mit einem SQL Server-Container. Wenn Sie einen anderen Port angeben möchten, verwenden Sie für die Trennung der Name ein Komma. Geben Sie beispielsweise für einen Server über Port 1401 lauscht, `<servername or IP>,1401`.<br/><br/>Als Alternative können Sie die ADO-Verbindungszeichenfolge für Ihre Datenbank hier eingeben. |
   | **Name der Datenbank** (optional) | Die Datenbank, die Sie verwenden möchten. Zum Verbinden mit der Standarddatenbank Geben Sie keine verwenden zu können, hier einen Datenbanknamen. |
   | **Authentifizierungstyp** | Wählen Sie entweder **integrierte** oder **SQL-Anmeldung**. |
   | **Benutzername** | Wenn Sie ausgewählt haben **SQL-Anmeldung**, geben Sie den Namen eines Benutzers mit Zugriff auf eine Datenbank auf dem Server. |
   | **Kennwort** | Geben Sie das Kennwort für den angegebenen Benutzer ein. |
   | **Kennwort speichern** | Drücken Sie **EINGABETASTE** auszuwählenden **Ja** und das Kennwort zu speichern. Wählen Sie **keine** für das Kennwort jedes Mal aufgefordert werden, wird das Verbindungsprofil verwendet. |
   | **Profilname** (optional) | Geben Sie einen Namen für das Verbindungsprofil, z. B. *"localhost" Profil*. |

   Nachdem Sie alle Werte eingeben, und wählen Sie **EINGABETASTE**, Visual Studio Code erstellt das Verbindungsprofil und eine Verbindung mit SQL Server her.

   > [!TIP]
   > Wenn die Verbindung ein Fehler auftritt, versuchen Sie es zur diagnose des Problems aus der Fehlermeldung in die **Ausgabe** Bereich in Visual Studio Code. Zum Öffnen der **Ausgabe** wählen **Ansicht** > **Ausgabe**. Überprüfen Sie auch die [Empfehlungen zur Verbindungsproblembehandlung](./sql-server-linux-troubleshooting-guide.md#connection).

1. Überprüfen Sie Ihre Verbindung in der unteren Statusleiste angezeigt.

   ![Verbindungsstatus](./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png)

Als Alternative zu den vorherigen Schritten können Sie auch erstellen und Bearbeiten von remoteverbindungsprofilen in der Datei mit den Einstellungen der Benutzer können ( *"Settings.JSON"* ). Wählen Sie zum Öffnen der Einstellungsdatei **Datei** > **Voreinstellungen** > **Einstellungen**. Weitere Informationen finden Sie unter [Verwalten von remoteverbindungsprofilen](https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles).

## <a name="create-a-sql-database"></a>Erstellen Sie eine SQL­Datenbank

1. Geben Sie in der neuen SQL-Datei, die Sie zuvor gestartet, *Sql* zum Anzeigen einer Liste der Codeausschnitte bearbeitet werden. 

   ![SQL-Ausschnitten](./media/sql-server-linux-develop-use-vscode/vscode-sql-snippets.png)

1. Wählen Sie **SqlCreateDatabase**.

1. Geben Sie im Codeausschnitt `TutorialDB` "DatabaseName" zu ersetzen:

   ```sql
   -- Create a new database called 'TutorialDB'
   -- Connect to the 'master' database to run this snippet
   USE master
   GO
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
   CREATE DATABASE [TutorialDB]
   GO
   ```

1. Drücken Sie **STRG**+**UMSCHALT**+**E** zur Ausführung der Transact-SQL-Befehle. Anzeigen der Ergebnisse in das Abfragefenster.

   ![Erstellen von Nachrichten.](./media/sql-server-linux-develop-use-vscode/vscode-create-database-messages.png)

   > [!TIP]
   > Sie können die Tastenkombinationen für die Mssql-Befehlen anpassen. Finden Sie unter [Tastenkombinationen anpassen](https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts).

## <a name="create-a-table"></a>Erstellen einer Tabelle

1. Löschen Sie den Inhalt des Code-Editor-Fensters.

1. Drücken Sie **STRG**+**UMSCHALT**+**P** oder **F1** zum Öffnen der **Befehlspalette**. 

1. Typ *Sql* zum Anzeigen der Mssql-Befehle oder Typ *Sqluse*, und wählen Sie dann die **MS SQL: Verwenden Sie die Datenbank** Befehl.

1. Wählen Sie die neue **"tutorialdb"** Datenbank. 

   ![Verwenden Sie die Datenbank](./media/sql-server-linux-develop-use-vscode/vscode-use-database.png)

1. Geben Sie im Code-Editor, *Sql* wählen Sie zum Anzeigen der Codeausschnitte **SqlCreateTable**, und drücken Sie dann die **EINGABETASTE**.

1. Geben Sie im Codeausschnitt `Employees` für den Tabellennamen an.

1. Drücken Sie **Registerkarte** zum nächsten Feld zu erhalten, und geben Sie dann `dbo` des Schemanamens.

1. Ersetzen Sie die Spaltendefinitionen, durch die folgenden Spalten:

   ```sql
   EmployeesId INT NOT NULL PRIMARY KEY,
   Name [NVARCHAR](50)  NOT NULL,
   Location [NVARCHAR](50)  NOT NULL
   ```

1. Drücken Sie **STRG**+**UMSCHALT**+**E** zum Erstellen der Tabelle.

## <a name="insert-and-query"></a>Einfügen und Abfragen

1. Fügen Sie die folgenden Anweisungen zum Einfügen von vier Zeilen in der **Mitarbeiter** Tabelle.

   ```sql
   -- Insert rows into table 'Employees'
   INSERT INTO Employees
      ([EmployeesId],[Name],[Location])
   VALUES
      ( 1, N'Jared', N'Australia'),
      ( 2, N'Nikita', N'India'),
      ( 3, N'Tom', N'Germany'),
      ( 4, N'Jake', N'United States')
   GO
   -- Query the total count of employees
   SELECT COUNT(*) as EmployeeCount FROM dbo.Employees;
   -- Query all employee information
   SELECT e.EmployeesId, e.Name, e.Location 
   FROM dbo.Employees as e
   GO
   ```

   Während der Eingabe, können T-SQL IntelliSense Sie die Anweisungen ausführen:

   ![T-SQL-IntelliSense](./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png)

   > [!TIP]
   > Die Mssql-Erweiterung verfügt außerdem über Befehle, um INSERT- und SELECT-Anweisungen zu erstellen. Diese wurden im vorherigen Beispiel nicht verwendet.

1. Drücken Sie **STRG**+**UMSCHALT**+**E** die Befehle ausführen. Die beiden führen legt Anzeige in der **Ergebnisse** Fenster. 

   ![Ergebnisse](./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png)

## <a name="view-and-save-the-result"></a>Anzeigen und Speichern des Ergebnisses

1. Wählen Sie **Ansicht** >  **-Editor-Layout** > **kippen Layout** auf einer vertikale oder horizontale Teilung Layout wechseln.

1. Wählen Sie die **Ergebnisse** und **Nachrichten** panel reduzieren und erweitern die Panels-Header.

   ![Ein/aus-Header](./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png)

   > [!TIP]
   > Sie können das Standardverhalten von der Mssql-Erweiterung anpassen. Finden Sie unter [passen Sie die Erweiterung Optionen](https://github.com/Microsoft/vscode-mssql/wiki/customize-options).

1. Wählen Sie das Raster "Maximieren", auf das zweite Ergebnisraster, um zu diesen Ergebnissen zu vergrößern.

   ![Maximieren Sie Raster](./media/sql-server-linux-develop-use-vscode/vscode-maximize-grid.png)

   > [!NOTE]
   > Das Symbol "Maximieren" zeigt an, wenn das T-SQL-Skript mindestens zwei ergebnisrastern erzeugt.

1. Öffnen Sie das Kontextmenü für Raster, indem Sie mit der rechten Maustaste auf das Raster. 

   ![Kontextmenü](./media/sql-server-linux-develop-use-vscode/vscode-grid-context-menu.png)

1. Wählen Sie **wählen Sie alle**.

1. Öffnen Sie das Kontextmenü für Raster erneut, und wählen Sie **als JSON speichern** zum Speichern des Ergebnisses zu einer *JSON* Datei.

1. Geben Sie einen Namen für die JSON-Datei. 

1. Stellen Sie sicher, dass die JSON-Datei gespeichert und wird in Visual Studio Code geöffnet.

   ![im JSON-Format speichern](./media/sql-server-linux-develop-use-vscode/vscode-save-as-json.png)

Bei Bedarf speichern und später ausführen von SQL-Skripts für die Verwaltung oder einen größeren Entwicklungsprojekt hinzu, speichern Sie die Skripts mit einer *.sql* Erweiterung.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie mit T-SQL vertraut sind, finden Sie unter [Lernprogramm: Schreiben von Transact-SQL-Anweisungen](https://docs.microsoft.com/sql/t-sql/tutorial-writing-transact-sql-statements) und [Transact-SQL-Referenz (Datenbankmodul)](https://docs.microsoft.com/sql/t-sql/language-reference).

Weitere Informationen zu verwenden oder die Mitwirkung an der Mssql-Erweiterung, finden Sie unter den [Mssql-Erweiterung Project Wiki](https://github.com/Microsoft/vscode-mssql/wiki).

Weitere Informationen zur Verwendung von Visual Studio Code finden Sie unter den [Dokumentation zu Visual Studio Code](https://code.visualstudio.com/docs).