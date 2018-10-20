---
title: 'Schnellstart: Verbinden und Abfragen von Azure SQL-Datenbank mithilfe von Azure Data Studio | Microsoft-Dokumentation'
description: In dieser schnellstartanleitung veranschaulicht, wie Azure Data Studio eine Verbindung mit einer SQL-Datenbank, und führen Sie eine Abfrage
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: a1d39e8ebd3d986825141b1acadd0ebc782083a6
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356041"
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-azure-sql-database"></a>Schnellstart: Verwenden von [!INCLUDE[name-sos](../includes/name-sos-short.md)] zum Verbinden und Abfragen von Azure SQL-Datenbank

Dieser Schnellstart veranschaulicht, wie *[!INCLUDE[name-sos](../includes/name-sos-short.md)]* eine Verbindung mit einer Azure SQL-Datenbank herstellen und anschließend mithilfe von Transact-SQL (T-SQL)-Anweisungen zum Erstellen der *"tutorialdb"* verwendet [!INCLUDE[name-sos](../includes/name-sos-short.md)] Lernprogramme.

## <a name="prerequisites"></a>Erforderliche Komponenten

Um diesen Schnellstart abzuschließen, müssen Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)], und eine Azure SQL-Server.

- [Installieren Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).

Wenn Sie bereits über eine Azure SQL-Server haben, führen Sie eines der folgenden Azure SQL-Datenbank-Schnellstarts (Beachten Sie den Servernamen und Anmeldeinformationen!):

- [Erstellen Sie DB - Portal.](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal)
- [Erstellen Sie DB - CLI.](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-cli)
- [Erstellen einer Datenbank – PowerShell](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-powershell)


## <a name="connect-to-your-azure-sql-database-server"></a>Verbindungsherstellung mit Ihrem Azure SQL-Datenbank-server

Verwendung [!INCLUDE[name-sos](../includes/name-sos-short.md)] zum Herstellen einer Verbindung mit Ihrem Azure SQL-Datenbank-Server.

1. Der ersten Ausführung [!INCLUDE[name-sos](../includes/name-sos-short.md)] der **Verbindung** Seite sollte zu öffnen. Wenn Sie nicht angezeigt wird der **Verbindung** auf **Verbindung hinzufügen**, oder die **neue Verbindung** Symbol in der **Server** Randleiste:
   
   ![Symbol "neue Verbindung"](media/quickstart-sql-database/new-connection-icon.png)

2. In diesem Artikel wird *SQL-Anmeldung*, aber *Windows-Authentifizierung* wird ebenfalls unterstützt. Geben Sie die Felder, die wie folgt mithilfe der Servername, Benutzername und das Kennwort für *Ihre* Azure SQL-Server:

   | Einstellung       | Empfohlener Wert | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Servername** | Der vollqualifizierte Servername | Der Name sollte etwa wie folgt sein: **servername.database.windows.net** |
   | **Authentifizierung** | SQL-Anmeldung| In diesem Tutorial wird SQL-Authentifizierung verwendet. |
   | **Benutzername** | Das Konto des Serveradministrators | Dabei handelt es sich um das Konto, das Sie beim Erstellen des Servers angegeben haben. |
   | **Kennwort (SQL-Anmeldung)** | Das Kennwort für das Konto des Serveradministrators | Dabei handelt es sich um das Kennwort, das Sie beim Erstellen des Servers angegeben haben. |
   | **Kennwort speichern** | Ja oder Nein | Wählen Sie Ja aus, wenn Sie nicht jedes Mal das Kennwort eingeben möchten. |
   | **Datenbankname** | *Leer lassen* | Der Name der Datenbank, die, der Sie herstellen möchten. |
   | **Gruppe "Server"** | Wählen Sie<Default> | Wenn Sie eine Servergruppe erstellt haben, können Sie auf eine bestimmte Servergruppe festlegen. | 

   ![Symbol "neue Verbindung"](media/quickstart-sql-database/new-connection-screen.png)  

3. Wenn es sich bei Ihrem Server eine Firewallregel mit dem Azure Data Studio eine Verbindung herstellen, sodass keine der **Firewallregel erstellen** -Formular wird geöffnet. Führen Sie das Formular, um eine neue Firewallregel zu erstellen. Weitere Informationen finden Sie unter [Firewallregeln](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure).

   ![Neue Firewallregel](media/quickstart-sql-database/firewall.png)  

4. Nach der erfolgreichen Verbindung von Ihrem Server, die in der geöffnet wird die *Server* Randleiste.

## <a name="create-the-tutorial-database"></a>Erstellen der Tutorial-Datenbank

Erstellen Sie in den folgenden Abschnitten der *"tutorialdb"* in mehreren verwendeten [!INCLUDE[name-sos](../includes/name-sos-short.md)] Tutorials.

1. Klicken Sie mit der rechten Maustaste auf Ihre Azure SQL-Server in der Randleiste Server, und wählen Sie **neue Abfrage.**

1. Fügen Sie den folgenden Codeausschnitt in der Abfrage-Editor, und klicken Sie auf **ausführen**:

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



## <a name="create-a-table"></a>Erstellen einer Tabelle

Abfrage-Editor immer noch verbunden ist die *master* -Datenbank, aber wir möchten eine Tabelle in der *"tutorialdb"* Datenbank. 

1. Ändern den Verbindungskontext für **"tutorialdb"**:

   ![Kontext ändern](media/quickstart-sql-database/change-context.png)



1. Fügen Sie den folgenden Codeausschnitt in der Abfrage-Editor, und klicken Sie auf **ausführen**:

   > [!NOTE]
   > Sie können fügen Sie diese Option, um, oder überschreiben die vorherige Abfrage in Editor. Beachten Sie, dass beim Klicken auf **ausführen** führt nur die Abfrage, die ausgewählt ist. Wenn nichts ausgewählt ist, durch Klicken auf **ausführen** alle Abfragen im Editor ausgeführt.

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


## <a name="insert-rows"></a>Einfügen von Zeilen

- Fügen Sie den folgenden Codeausschnitt in der Abfrage-Editor, und klicken Sie auf **ausführen**:

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
1. Fügen Sie den folgenden Codeausschnitt in der Abfrage-Editor, und klicken Sie auf **ausführen**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Die Ergebnisse der Abfrage werden angezeigt:

   ![Select-Ergebnisse](media/quickstart-sql-database/select-results.png)


## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Weitere Artikel in dieser Sammlung bauen auf diesem Schnellstart auf. Wenn Sie auf Weiter mit nachfolgenden Schnellstarts arbeiten möchten, nicht bereinigen die Ressourcen, die in diesem Schnellstart erstellt. Wenn Sie nicht beabsichtigen, um den Vorgang fortzusetzen, verwenden Sie die folgenden Schritte aus, um erstellten Ressourcen dieses Schnellstarts im Azure-Portal löschen.
Bereinigen Sie Ressourcen durch Löschen der Ressourcengruppe, die Sie nicht mehr benötigen. Weitere Informationen finden Sie unter [Bereinigen von Ressourcen](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal#clean-up-resources).

## <a name="next-steps"></a>Nächste Schritte

Nun, Sie erfolgreich eine Verbindung mit einer Azure SQL-Datenbank hergestellt haben und eine Abfrage ausgeführt, probieren Sie die [Code-Editor-Tutorials](tutorial-sql-editor.md).
