---
title: Verwenden Sie die Visual Studio Code-Mssql-Erweiterung für SQL Server | Microsoft-Dokumentation
description: In diesem Tutorial zeigt, wie Sie mit der Mssql-Erweiterung für Visual Studio Code. Diese Erweiterung ermöglicht das Bearbeiten und Ausführen von Transact-SQL-Skripts in Visual Studio Code.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 9766ee75-32d3-4045-82a6-4c7968bdbaa6
ms.custom: sql-linux
ms.openlocfilehash: b1ae9056ecbaf158b275798d69d691ae64e6ef06
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033627"
---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts-for-sql-server"></a>Verwenden von Visual Studio Code zum Erstellen und Ausführen von Transact-SQL-Skripts für SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird gezeigt, wie Sie mit der **Mssql** -Erweiterung für Visual Studio Code (VS Code), um SQL Server-Datenbanken zu entwickeln.

Visual Studio Code ist ein grafischer Code-Editor für Linux, MacOS und Windows, der Erweiterungen unterstützt. Die [**Mssql** -Erweiterung für Visual Studio Code] ermöglicht es Ihnen, eine Verbindung mit SQL Server, Abfrage mit Transact-SQL (T-SQL) und die Ergebnisse anzuzeigen.

## <a name="install-vs-code"></a>Installieren von VS Code
1. Wenn Sie Visual Studio-Code nicht bereits installiert haben [herunterladen und Installieren von VS Code] auf Ihrem Computer.

2. Starten Sie VS Code.

## <a name="install-the-mssql-extension"></a>Installieren Sie die Mssql-Erweiterung
Die folgenden Schritte erläutern, wie Sie die Mssql-Erweiterung zu installieren. 

1. Drücken Sie **STRG + UMSCHALT + P** (oder **F1**) in Visual Studio Code die Befehlspalette zu öffnen. 

2. Wählen Sie **Erweiterung installieren** und **Mssql**.
   > [!TIP] 
   > Für MacOS die **CMD** Schlüssel entspricht dem **STRG** Schlüssel für Linux- und Windows.

2. Klicken Sie auf Installieren **Mssql**. 
   
   <img src="./media/sql-server-linux-develop-use-vscode/vscode-extension.png" alt="Install the extension" style="width: 600px;"/>

3. Die **Mssql** Erweiterung dauert bis zu eine Minute zu installieren. Warten Sie, bis die Eingabeaufforderung, die Ihnen mitteilt, dass er erfolgreich installiert.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-install-success-notification.png" alt="Installation success notification" style="width: 600px;"/>

   > [!NOTE]
   > Für Mac OS müssen Sie OpenSSL installieren. Dies ist eine Voraussetzung für.NET Core, die von der Mssql-Erweiterung verwendet. Führen Sie die **Voraussetzung installieren** Schritte in der [.NET Core Anweisungen]. Oder Sie können die folgenden Befehle in MacOS-Terminal ausführen.
   >
   >   ```bash
   >   brew update
   >   brew install openssl
   >   ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
   >   ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
   >   ```
   
   > [!NOTE]
   > Für Windows 8.1, Windows Server 2012 oder frühere Versionen müssen Sie herunterladen und installieren Sie die [Windows 10 Universal C Runtime]. Laden Sie und öffnen Sie die Zip-Datei. Führen Sie das Installationsprogramm (MSU-Datei) für die aktuelle Konfiguration des Betriebssystems an.

## <a name="create-or-open-a-sql-file"></a>Erstellen Sie oder öffnen Sie eine SQL-Datei

Die **Mssql** Erweiterung Mssql-Befehlen und T-SQL IntelliSense bei der Language-Modus, um festgelegt ist im Editor ermöglicht **SQL**.

1. Drücken Sie **STRG + N**. Visual Studio Code öffnet eine neue Datei mit "Nur-Text" in der Standardeinstellung. 

2. Drücken Sie **STRG + K, M** , und ändern Sie den Sprachmodus auf **SQL**. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-language-mode.png" alt="SQL language mode" style="width: 500px;" />

3. Alternativ öffnen Sie eine vorhandene Datei mit der Dateierweiterung SQL aufweisen. Der Sprachmodus wird automatisch **SQL** für Dateien, die die SQL-Erweiterung aufweisen.  

## <a name="connect-to-sql-server"></a>Verbindung mit SQL Server herstellen

Die folgenden Schritte zeigen, wie Sie die Verbindung mit SQL Server mit Visual Studio Code.

1. Drücken Sie in VS Code **STRG+UMSCHALT+P** (oder **F1**), um die Befehlspalette zu öffnen.

2. Typ **Sql** Mssql-Befehle angezeigt.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-commands.png" alt="mssql commands" style="width: 500px;" />
   

3. Wählen Sie die **MS SQL: Connect** Befehl. Sie können einfach eingeben **Sqlcon** , und drücken Sie **EINGABETASTE**.

4. Wählen Sie **Verbindungsprofil erstellen**. Dadurch wird ein Verbindungsprofil für Ihre SQL Server-Instanz erstellt.

5. Befolgen Sie die Anweisungen, um die Verbindungseigenschaften für das neue Verbindungsprofil anzugeben. Nachdem Sie sämtliche Werte angegeben haben, drücken Sie die **EINGABETASTE**, um fortzufahren. 

   In der folgende Tabelle werden die verbindungsprofileigenschaften beschrieben.

   | Einstellung | Description |
   |-----|-----|
   | **Servername** | Der Name des SQL Server-Instanz. Verwenden Sie für dieses Tutorial **"localhost"** für die Verbindung mit der lokalen SQL Server-Instanz auf Ihrem Computer. Wenn auf einem Remotecomputer mit SQL Server zu verbinden, geben Sie den Namen der Zielcomputer für die SQL Server oder die IP-Adresse. Wenn Sie einen Port für Ihre SQL Server-Instanz angeben müssen, verwenden Sie für die Trennung der Name ein Komma. Z. B. bei einem lokalen Server an Port 1401 Geben Sie **"localhost" 1401**. |
   | **[Optional] Name der Datenbank** | Die Datenbank, die Sie verwenden möchten. Für dieses Lernprogramm nicht angeben, eine Datenbank, und drücken Sie **EINGABETASTE** um den Vorgang fortzusetzen. |
   | **Benutzername** | Geben Sie den Namen eines Benutzers mit Zugriff auf eine Datenbank auf dem Server ein. In diesem Tutorial verwenden Sie die Standardeinstellung **SA** Konto während des SQL Server-Setups erstellt wurde. |
   | **Kennwort (SQL-Anmeldung)** | Geben Sie das Kennwort für den angegebenen Benutzer ein. | 
   | **Kennwort speichern** | Typ **Ja** zum Speichern des Kennworts. Geben Sie andernfalls **keine** für das Kennwort jedes Mal aufgefordert werden, wird das Profil für die Verbindung verwendet. |
   | **[Optional] Geben Sie einen Namen für dieses Profil** | Der Name des Elements. Angenommen, nennen Sie das Profil **"localhost" Profil**. 

   > [!Tip] 
   > Sie können erstellen und Bearbeiten von remoteverbindungsprofilen in User Settings-Datei ("Settings.JSON"). Öffnen Sie die Datei mit den Einstellungen dazu **Einstellung** und dann **Benutzereinstellungen** im VS Code. Weitere Informationen finden Sie unter [Verwalten von remoteverbindungsprofilen].

6. Drücken Sie die **ESC**-Taste, um die Meldung zu schließen, in der Sie darüber informiert werden, dass das Profil erstellt und eine Verbindung hergestellt wurde.

   > [!TIP]
   > Wenn Sie einen Verbindungsfehler erhalten, versuchen zunächst, die diagnose des Problems aus der Fehlermeldung in die **Ausgabe** Panel in Visual Studio Code (Wählen Sie **Ausgabe** auf die **Ansicht** Menü). Überprüfen Sie anschließend die [Problembehandlung bei verbindungsempfehlungen].

7. Überprüfen Sie Ihre Verbindung in der Statusleiste.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png" alt="Connection status" style="width: 500px;" />

## <a name="create-a-database"></a>Erstellen einer Datenbank

1. Geben Sie im Editor **Sql** , um eine Liste der bearbeitbaren Codeausschnitte anzuzeigen. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-sql-snippets.png" alt="SQL snippets" style="width: 500px;" />

2. Wählen Sie **SqlCreateDatabase**.

3. Geben Sie im Codeausschnitt **"tutorialdb"** für den Datenbanknamen an.

   ```sql
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
   
4. Drücken Sie **STRG + UMSCHALT + E** zur Ausführung der Transact-SQL-Befehle. Anzeigen der Ergebnisse in das Abfragefenster.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-create-database-messages.png" alt="create database messages" style="width: 500px;" />

   > [!TIP]
   > Sie können die Verknüpfung tastenzuordnungen für die Mssql-Erweiterungsbefehle anpassen. Finden Sie unter [Anpassen von Tastenkombinationen].

## <a name="create-a-table"></a>Erstellen einer Tabelle

1. Entfernt den Inhalt des Editor-Fensters.

2. Drücken Sie **F1** um die Befehlspalette anzuzeigen.

3. Typ **Sql** in der Befehlspalette den Befehl zum Anzeigen der SQL-Befehlen oder Typ **Sqluse** für **MS SQL: Use Database** Befehl.

4. Klicken Sie auf **MS SQL: Use Database**, und wählen Sie die **"tutorialdb"** Datenbank. Dies ändert den Kontext, in die neue Datenbank, die im vorherigen Abschnitt erstellt haben.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-use-database.png" alt="use database" style="width: 500px;" />

3. Geben Sie im Editor **Sql** auf die Codeausschnitte anzeigen lassen, und wählen Sie dann **SqlCreateTable** , und drücken Sie **geben**.

4. Geben Sie im Codeausschnitt **Mitarbeiter** für den Tabellennamen an.

5. Drücken Sie **Registerkarte**, und geben Sie dann **Dbo** des Schemanamens.

   > [!NOTE]
   > Nachdem der Ausschnitt hinzugefügt haben, müssen Sie die Namen der Tabelle und Schema eingeben, ohne den Fokus von VS Code-Editor.

6. Ändern Sie den Spaltennamen für **Column1** zu **Namen** und **Column2** zu **Speicherort**.

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

7. Drücken Sie **STRG + UMSCHALT + E** zum Erstellen der Tabelle.

## <a name="insert-and-query"></a>Einfügen und Abfragen

1. Fügen Sie die folgenden Anweisungen zum Einfügen von vier Zeilen in der **Mitarbeiter** Tabelle. Wählen Sie dann alle Zeilen aus.

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
   > Während der Eingabe, verwenden Sie die Unterstützung des T-SQL IntelliSense.
   >   <img src="./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png" alt="TSQL IntelliSense" style="width: 500px;" />

2. Drücken Sie **STRG + UMSCHALT + E** die Befehle ausführen. Die beiden führen legt Anzeige in der **Ergebnisse** Fenster. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png" alt="Results" style="width: 300px;" />

## <a name="view-and-save-the-result"></a>Anzeigen und Speichern des Ergebnisses

1. Auf der **Ansicht** , wählen Sie im Menü **Layout für ein/aus-Editor** vertikale oder horizontale Teilung Layout wechseln.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-split.png" alt="Vertical split" style="width: 500px;" />

2. Klicken Sie auf die **Ergebnisse** und **Nachrichten** Panel-Header zu reduzieren und erweitern im Bereich.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png" alt="Toggle Messages" style="width: 500px;" />

   > [!TIP]
   > Sie können das Standardverhalten von der Mssql-Erweiterung anpassen. Finden Sie unter [Passen Sie die Erweiterung-Optionen].

2. Klicken Sie auf das Symbol "Raster maximieren", auf das zweite Ergebnisraster zum Verkleinern die Tasten.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-maximize-grid.png" alt="Maximize grid" style="width: 500px;" />

   > [!NOTE]
   > Das Symbol "Maximieren" zeigt an, wenn das T-SQL-Skript ergebnisrastern von zwei oder mehr hat.

3. Öffnen Sie das Kontextmenü für Raster mit der rechten Maustaste in einem Raster an. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-grid-context-menu.png" alt="Context menu" style="width: 500px;" />

4. Wählen Sie **wählen Sie alle**.

5. Öffnen Sie das Kontextmenü für Raster, und wählen **als JSON speichern** um das Ergebnis in eine JSON-Datei zu speichern.

6. Geben Sie einen Namen für die JSON-Datei. Geben Sie für dieses Tutorial **employees.json**.

7. Stellen Sie sicher, dass die JSON-Datei gespeichert und in Visual Studio Code geöffnet ist.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-save-as-json.png" alt="Save as Json" style="width: 500px;" />

## <a name="next-steps"></a>Nächste Schritte

In einem realen Szenario können Sie ein Skript, die Sie benötigen, speichern und Ausführen erstellen höher (für die Verwaltung oder als Teil eines größeren Entwicklungsprojekts). In diesem Fall können Sie speichern Sie das Skript mit einem **.sql** Erweiterung.

Unter [Lernprogramm: Schreiben von Transact-SQL-Anweisungen] und [Transact-SQL-Referenz (Datenbank-Engine)] finden Sie weitere Informationen, wenn Sie noch nicht mit T-SQL vertraut sind.

Weitere Informationen zu verwenden oder die Mitwirkung an der Mssql-Erweiterung, finden Sie unter [der Mssql-Erweiterung Project wiki].

Weitere Informationen zur Verwendung von Visual Studio Code finden Sie unter den [Dokumentation zu Visual Studio Code](https://code.visualstudio.com/docs).

[**Mssql** -Erweiterung für Visual Studio Code]:https://aka.ms/mssql-marketplace
[Herunterladen und Installieren von VS Code]:https://code.visualstudio.com/Download
[.NET Core Anweisungen]:https://www.microsoft.com/net/core
[Verwalten von remoteverbindungsprofilen]:https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles
[Problembehandlung bei verbindungsempfehlungen]:./sql-server-linux-troubleshooting-guide.md#connection
[Anpassen von Tastenkombinationen]:https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts
[Lernprogramm: Schreiben von Transact-SQL-Anweisungen]:https://msdn.microsoft.com/library/ms365303.aspx
[Transact-SQL-Referenz (Datenbank-Engine)]:https://msdn.microsoft.com/library/bb510741.aspx
[Visual Studio Code documentation]:https://code.visualstudio.com/docs
[Windows 10 Universal C Runtime]:https://github.com/Microsoft/vscode-mssql/wiki/windows10-universal-c-runtime-requirement
[Passen Sie die Erweiterung-Optionen]: https://github.com/Microsoft/vscode-mssql/wiki/customize-options
[der Mssql-Erweiterung Project wiki]: https://github.com/Microsoft/vscode-mssql/wiki
