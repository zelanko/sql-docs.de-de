---
title: 'Schnellstart: Verbinden und Abfragen von Azure SQL-Datenbank'
titleSuffix: Azure Data Studio
description: In dieser schnellstartanleitung veranschaulicht, wie Azure Data Studio eine Verbindung mit einer SQL-Datenbank, und führen Sie eine Abfrage
ms.custom: seodec18, sqlfreshmay19
ms.date: 05/14/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: a961cd08baab13b87241492df4adef52d5846daf
ms.sourcegitcommit: 553ecea0427e4d2118ea1ee810f4a73275b40741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65620355"
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-azure-sql-database"></a>Schnellstart: Verwendung [!INCLUDE[name-sos](../includes/name-sos-short.md)] zum Verbinden und Abfragen von Azure SQL-Datenbank

In diesem Schnellstart verwenden Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)] für die Verbindung mit einem Azure SQL-Datenbank-Server. Führen Sie anschließend Transact-SQL (T-SQL)-Anweisungen zum Erstellen und Abfragen der Datenbank "tutorialdb", die in anderen dient [!INCLUDE[name-sos](../includes/name-sos-short.md)] Tutorials.

## <a name="prerequisites"></a>Erforderliche Komponenten

Um diesen Schnellstart abzuschließen, müssen Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)], und eine Azure SQL-Datenbank-Server.

- [Installieren Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md)

Wenn Sie nicht über eine Azure SQL-Server verfügen, führen Sie eines der folgenden Schnellstarts für Azure SQL-Datenbank. Beachten Sie den vollqualifizierten Servernamen, und melden Sie sich die Anmeldeinformationen für die Verwendung in späteren Schritten:

- [Erstellen Sie DB - Portal.](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal)
- [Erstellen Sie DB - CLI.](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-cli)
- [Erstellen einer Datenbank – PowerShell](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-powershell)


## <a name="connect-to-your-azure-sql-database-server"></a>Verbindungsherstellung mit Ihrem Azure SQL-Datenbank-server

Verwendung [!INCLUDE[name-sos](../includes/name-sos-short.md)] zum Herstellen einer Verbindung mit Ihrem Azure SQL-Datenbank-Server.

1. Der ersten Ausführung [!INCLUDE[name-sos](../includes/name-sos-short.md)] der **Willkommen** Seite sollte zu öffnen. Wenn Sie nicht sehen die **Willkommen** Seite **Hilfe** > **Willkommen**. Wählen Sie **neue Verbindung** zum Öffnen der **Verbindung** Bereich:
   
   ![Symbol "neue Verbindung"](media/quickstart-sql-database/new-connection-icon.png)

2. In diesem Artikel wird die SQL-Anmeldung verwendet, aber Sie unterstützt auch die Windows-Authentifizierung. Geben Sie die folgenden Felder, die mit der Servername, Benutzername und das Kennwort für Ihre Azure SQL-Server:

   | Einstellung       | Empfohlener Wert | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Servername** | Der vollqualifizierte Servername | Ähnlich: **servername.database.windows.net**. |
   | **Authentifizierung** | SQL-Anmeldung| In diesem Tutorial wird SQL-Authentifizierung verwendet. |
   | **Benutzername** | Die Server Admin-Kontobenutzername | Der Benutzername aus dem Konto verwendet, um den Server zu erstellen. |
   | **Kennwort (SQL-Anmeldung)** | Das Kennwort für das Server-Administratorkonto | Das Kennwort aus dem Konto verwendet, um den Server zu erstellen. |
   | **Kennwort speichern** | Ja oder Nein | Wählen Sie **Ja** , wenn Sie nicht jedes Mal das Kennwort eingeben möchten. |
   | **Datenbankname** | *Leer lassen* | Sie können nur eine Verbindung mit dem Server hier. |
   | **Gruppe "Server"** | Wählen Sie<Default> | Sie können dieses Feld auf eine bestimmte Servergruppe festlegen, die Sie erstellt haben. | 

   ![Symbol "neue Verbindung"](media/quickstart-sql-database/new-connection-screen.png)  

3. Wählen Sie **Verbinden**.

4. Wenn es sich bei Ihrem Server eine Firewallregel mit dem Azure Data Studio eine Verbindung herstellen, sodass keine der **Firewallregel erstellen** -Formular wird geöffnet. Führen Sie das Formular, um eine neue Firewallregel zu erstellen. Weitere Informationen finden Sie unter [Firewallregeln](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure).

   ![Neue Firewallregel](media/quickstart-sql-database/firewall.png)  

Nach der erfolgreichen verbindungsherstellung Ihren Server wird geöffnet, der **Server** Randleiste.

## <a name="create-the-tutorial-database"></a>Erstellen der Tutorial-Datenbank

In den nächsten Abschnitten erstellen Sie die Datenbank "tutorialdb", die verwendet wird, in anderen [!INCLUDE[name-sos](../includes/name-sos-short.md)] Tutorials.

1. Mit der rechten Maustaste auf Ihre Azure SQL-Server in der **Server** Randleiste, und wählen **neue Abfrage**.

1. Fügen Sie diese SQL-Anweisungen in den Abfrage-Editor ein.

   ```sql
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
   CREATE DATABASE [TutorialDB]
   GO

   ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
   GO
   ```

1. Wählen Sie in der Symbolleiste **ausführen**. Benachrichtigungen werden in der **Nachrichten** Bereich zeigt die Abfrage wird ausgeführt.

## <a name="create-a-table"></a>Erstellen einer Tabelle

Mit der Abfrage-Editor verbunden ist die **master** -Datenbank, aber wir möchten eine Tabelle in der **"tutorialdb"** Datenbank. 

1. Herstellen einer Verbindung mit der **"tutorialdb"** Datenbank.

   ![Kontext ändern](media/quickstart-sql-database/change-context2.png)



1. Erstellen Sie eine `Customers` Tabelle. 

   Ersetzen Sie die vorherige Abfrage im Abfrage-Editor durch diese, und wählen Sie **ausführen**.

   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
   DROP TABLE dbo.Customers
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
      CustomerId        INT    NOT NULL   PRIMARY KEY, -- primary key column
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```


## <a name="insert-rows-into-the-table"></a>Einfügen von Zeilen in der Tabelle

Ersetzen Sie die vorherige Abfrage durch diese, und wählen Sie **ausführen**.

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
   VALUES
      ( 1, N'Orlando', N'Australia', N''),
      ( 2, N'Keith', N'India', N'keith0@adventure-works.com'),
      ( 3, N'Donna', N'Germany', N'donna0@adventure-works.com'),
      ( 4, N'Janet', N'United States', N'janet1@adventure-works.com')
   GO
   ```

## <a name="view-the-result"></a>Das Ergebnis anzeigen

Ersetzen Sie die vorherige Abfrage durch diese, und wählen Sie **ausführen**.

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

Die Abfrageergebnisse anzeigen zu können:

   ![Select-Ergebnisse](media/quickstart-sql-database/select-results2.png)


## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Spätere schnellstartartikel baut auf die hier erstellten Ressourcen. Wenn Sie diese Artikel durcharbeiten möchten, achten Sie darauf, dass Sie nicht, um diese Ressourcen zu löschen. Löschen Sie andernfalls im Azure-Portal, die nicht mehr benötigten Ressourcen. Weitere Informationen finden Sie unter [Bereinigen von Ressourcen](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal#clean-up-resources).

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie erfolgreich mit einer Azure SQL-Datenbank und Ausführen einer Abfrage verbunden haben, können Sie die [Code-Editor-Tutorials](tutorial-sql-editor.md).
