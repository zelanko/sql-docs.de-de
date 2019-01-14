---
title: Verwenden Sie die Visual Studio Code-Mssql-Erweiterung für SQL Server unter Linux | Microsoft-Dokumentation
description: Verwenden Sie die Mssql-Erweiterung für Visual Studio Code zum Bearbeiten und Ausführen von Transact-SQL-Skripts für SQL Server unter Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/18/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 9766ee75-32d3-4045-82a6-4c7968bdbaa6
ms.custom: sql-linux
ms.openlocfilehash: 583c7ac13b49370b333e80568c4b52885b58dcf3
ms.sourcegitcommit: 78e32562f9c1fbf2e50d3be645941d4aa457e31f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54100565"
---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts-on-linux"></a>Verwenden von Visual Studio Code zum Erstellen und Ausführen von Transact-SQL-Skripts unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird gezeigt, wie Sie mit der *Mssql* -Erweiterung für Visual Studio Code zum Entwickeln von SQL Server-Datenbanken unter Linux.

## <a name="install-and-start-visual-studio-code"></a>Installieren Sie und starten Sie Visual Studio Code

Visual Studio Code ist ein grafischer Code-Editor für Linux, MacOS und Windows, der Erweiterungen unterstützt. 

1. [Herunterladen Sie und installieren Sie Visual Studio Code] auf Ihrem Computer.
   
1. Starten Sie Visual Studio Code.
   
   >[!NOTE]
   >Wenn Visual Studio Code nicht gestartet wird, wenn Sie über eine Remotedesktopsitzung von "xrdp" verbunden sind, finden Sie unter [VS Code funktioniert nicht unter Ubuntu, wenn eine Verbindung besteht, mithilfe von "xrdp"](https://github.com/Microsoft/vscode/issues/3451).

## <a name="install-the-mssql-extension"></a>Installieren Sie die Mssql-Erweiterung

Die [Mssql-Erweiterung für Visual Studio Code] ermöglicht die Verbindung mit einer SQL-Server, Abfragen mit Transact-SQL (T-SQL), und die Ergebnisse anzuzeigen.

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
   
Wenn Sie eine vorhandene Datei öffnen, die eine *.sql* -Erweiterung, der Sprachmodus automatisch auf SQL festgelegt.  

## <a name="connect-to-sql-server"></a>Verbindung mit SQL Server herstellen

Um ein Verbindungsprofil erstellen und eine Verbindung mit einer SQL Server, gehen Sie wie folgt vor.

> [!TIP] 
> Sie können auch erstellen und Bearbeiten von remoteverbindungsprofilen in die Datei mit den Benutzer (*"Settings.JSON"*). Wählen Sie zum Öffnen der Einstellungsdatei **Datei** > **Voreinstellungen** > **Einstellungen**. Weitere Informationen finden Sie unter [Verwalten von remoteverbindungsprofilen].
   
1. Drücken Sie **STRG**+**UMSCHALT**+**P** oder **F1** zum Öffnen der **Befehlspalette**. 
   
1. Typ *Sql* zum Anzeigen der Mssql-Befehle oder Typ *Sqlcon*, und wählen Sie dann **MS SQL: Herstellen einer mit** aus der Dropdownliste aus.
   
   ![MSSQL-Befehlen](./media/sql-server-linux-develop-use-vscode/vscode-commands.png)   
   
   >[!NOTE]
   >Eine SQL-Datei, müssen z. B. die leere SQL-Datei, die Sie erstellt haben, die Fokus im Code-Editor, bevor Sie die Mssql-Befehle ausführen können. 

1. Wählen Sie **Create Connection Profile** um ein neues Verbindungsprofil für Ihre SQL Server zu erstellen.
   
1. Führen Sie die Anweisungen aus, um die Eigenschaften für das neue Verbindungsprofil anzugeben. Wenn Sie jeden Wert angegeben, drücken Sie die **EINGABETASTE** um den Vorgang fortzusetzen. 
   
   1. **Servername oder die ADO-Verbindungszeichenfolge**: Geben Sie den Namen der SQL Server-Instanz. Verwendung *"localhost"* zur Verbindung mit SQL Server-Instanz auf dem lokalen Computer. Geben Sie zum Verbinden mit einem Remotecomputer mit SQL Server den Namen des Zielcomputers mit SQL Server oder die IP-Adresse ein. Wenn Sie einen anderen Port angeben möchten, verwenden Sie für die Trennung der Name ein Komma. Geben Sie beispielsweise für einen lokalen Server an Port 1401 *1401 "localhost"*. 
      
      >[!NOTE]
      >Sie können auch die ADO-Verbindungszeichenfolge eingeben, für die Datenbank, drücken Sie **EINGABETASTE**, optional Name das Verbindungsprofil ein, und drücken Sie **EINGABETASTE** erneut aus, um eine Verbindung herstellen und das Profil erstellt. 
      
   1. **Name der Datenbank** (optional): Die Datenbank, die Sie verwenden möchten. Um eine neue Datenbank erstellen zu können, nicht Geben Sie eine Datenbank ein, und drücken Sie **EINGABETASTE** um den Vorgang fortzusetzen. 
      
   1. **Authentifizierungstyp**: Drücken Sie **EINGABETASTE** auszuwählenden **SQL-Anmeldung**. 
      
   1. **Benutzername**: Geben Sie den Namen eines Benutzers mit Zugriff auf eine Datenbank auf dem Server ein.
      
   1. **Kennwort**: Geben Sie das Kennwort für den angegebenen Benutzer ein.
      
   1. **Kennwort speichern**: Drücken Sie **EINGABETASTE** auszuwählenden **Ja** und das Kennwort zu speichern. Wählen Sie **keine** für das Kennwort jedes Mal aufgefordert werden, wird das Verbindungsprofil verwendet. 
      
   1. **Profilname** (optional): Geben Sie einen Namen für das Verbindungsprofil, z. B. *"localhost" Profil*. 
   
   Nach der Auswahl **EINGABETASTE**, Visual Studio Code erstellt das Verbindungsprofil und eine Verbindung mit SQL Server her. 
   
   > [!TIP]
   > Wenn die Verbindung ein Fehler auftritt, versuchen Sie es zur diagnose des Problems aus der Fehlermeldung in die **Ausgabe** Bereich in Visual Studio Code. Zum Öffnen der **Ausgabe** wählen **Ansicht** > **Ausgabe**. Überprüfen Sie auch die [Problembehandlung bei verbindungsempfehlungen].
   
1. Überprüfen Sie Ihre Verbindung in der unteren Statusleiste angezeigt.
   
  ![Verbindungsstatus](./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png)   
   
## <a name="create-a-sql-database"></a>Erstellen Sie eine SQL­Datenbank

1. Geben Sie in der neuen SQL-Datei, die Sie zuvor gestartet, *Sql* zum Anzeigen einer Liste der Codeausschnitte bearbeitet werden. 

  ![SQL-Ausschnitten](./media/sql-server-linux-develop-use-vscode/vscode-sql-snippets.png)   
   
1. Wählen Sie **SqlCreateDatabase**.
   
1. Ersetzen Sie im Codeausschnitt `DatabaseName` mit `TutorialDB`:
   
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
> Sie können die Tastenkombinationen für die Mssql-Befehlen anpassen. Finden Sie unter [Anpassen von Tastenkombinationen].

## <a name="create-a-table"></a>Erstellen einer Tabelle

1. Löschen Sie den Inhalt des Code-Editor-Fensters.
   
1. Drücken Sie **STRG**+**UMSCHALT**+**P** oder **F1** zum Öffnen der **Befehlspalette**. 
   
1. Typ *Sql* zum Anzeigen der Mssql-Befehle oder Typ *Sqluse*, und wählen Sie dann die **MS SQL: Use Database** Befehl.
   
1. Wählen Sie die neue **"tutorialdb"** Datenbank. 
   
   ![Verwenden Sie die Datenbank](./media/sql-server-linux-develop-use-vscode/vscode-use-database.png)   
   
1. Geben Sie im Code-Editor, *Sql* wählen Sie zum Anzeigen der Codeausschnitte **SqlCreateTable**, und drücken Sie dann die **EINGABETASTE**.
   
1. Geben Sie im Codeausschnitt *Mitarbeiter* für den Tabellennamen und *Dbo* des Schemanamens.
   
1. Erstellen Sie die Spalten aus, wie im folgenden Code gezeigt:
   
   ```sql
   -- Create a new table called 'Employees' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Employees', 'U') IS NOT NULL
   DROP TABLE dbo.Employees
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Employees
   (
      EmployeesId        INT    NOT NULL   PRIMARY KEY, -- primary key column
      Name      [NVARCHAR](50)  NOT NULL,
      Location   [NVARCHAR](50)  NOT NULL
   );
   GO
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
   
   > [!TIP]
   > Während der Eingabe, verwenden Sie T-SQL-IntelliSense, können Sie die Anweisungen.
   >![T-SQL-IntelliSense](./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png)   
   
1. Drücken Sie **STRG**+**UMSCHALT**+**E** die Befehle ausführen. Die beiden führen legt Anzeige in der **Ergebnisse** Fenster. 
   
   ![Ergebnisse](./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png)   

## <a name="view-and-save-the-result"></a>Anzeigen und Speichern des Ergebnisses
   
1. Wählen Sie **Ansicht** > **-Editor-Layout** > **kippen Layout** auf einer vertikale oder horizontale Teilung Layout wechseln.
   
1. Wählen Sie die **Ergebnisse** und **Nachrichten** panel reduzieren und erweitern die Panels-Header.
   
   ![Ein/aus-Header](./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png)   
   
   > [!TIP]
   > Sie können das Standardverhalten von der Mssql-Erweiterung anpassen. Finden Sie unter [Passen Sie die Erweiterung-Optionen].
   
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

Wenn Sie mit T-SQL vertraut sind, finden Sie unter [Tutorial: Schreiben von Transact-SQL-Anweisungen] und [Transact-SQL-Referenz (Datenbank-Engine)].

Weitere Informationen zu verwenden oder die Mitwirkung an der Mssql-Erweiterung, finden Sie unter den [Mssql-Erweiterung Project Wiki].

Weitere Informationen zur Verwendung von Visual Studio Code finden Sie unter den [Dokumentation zu Visual Studio Code](https://code.visualstudio.com/docs).

[MSSQL-Erweiterung für Visual Studio Code]:https://aka.ms/mssql-marketplace
[Herunterladen Sie und installieren Sie Visual Studio Code]:https://code.visualstudio.com/Download
[.Net Core instructions]:https://www.microsoft.com/net/core
[Verwalten von remoteverbindungsprofilen]:https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles
[Problembehandlung bei verbindungsempfehlungen]:./sql-server-linux-troubleshooting-guide.md#connection
[Anpassen von Tastenkombinationen]:https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts
[Tutorial: Schreiben von Transact-SQL-Anweisungen]:https://docs.microsoft.com/sql/t-sql/tutorial-writing-transact-sql-statements
[Transact-SQL-Referenz (Datenbank-Engine)]:https://docs.microsoft.com/sql/t-sql/language-reference
[Visual Studio Code documentation]:https://code.visualstudio.com/docs
[Windows 10 Universal C Runtime]:https://github.com/Microsoft/vscode-mssql/wiki/windows10-universal-c-runtime-requirement
[Passen Sie die Erweiterung-Optionen]: https://github.com/Microsoft/vscode-mssql/wiki/customize-options
[MSSQL-Erweiterung Project wiki]: https://github.com/Microsoft/vscode-mssql/wiki
