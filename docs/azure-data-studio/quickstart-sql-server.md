---
title: 'Schnellstart: Herstellen einer Verbindung mit und Abfragen von SQL Server'
titleSuffix: Azure Data Studio
description: In dieser Schnellstartanleitung erfahren Sie, wie Sie mit Azure Data Studio eine Verbindung mit SQL Server herstellen und eine Abfrage ausführen.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: quickstart
author: yualan
ms.author: alayu
ms.reviewer: alayu; sstein
ms.custom: seodec18, sqlfreshmay19
ms.date: 08/02/2019
ms.openlocfilehash: 7398d918a027b28513b3f12a5101628cf1158e49
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "75884054"
---
# <a name="quickstart-connect-and-query-sql-server-using-name-sos"></a>Schnellstart: Herstellen einer Verbindung mit und Abfragen von SQL Server mit [!INCLUDE[name-sos](../includes/name-sos-short.md)]

In dieser Schnellstartanleitung erfahren Sie, wie Sie mithilfe von [!INCLUDE[name-sos](../includes/name-sos-short.md)] eine Verbindung mit SQL Server herstellen und anschließend Transact-SQL-Anweisungen (T- SQL) verwenden, um die in [!INCLUDE[name-sos](../includes/name-sos-short.md)]-Tutorials verwendete *TutorialDB* zu erstellen.

## <a name="prerequisites"></a>Voraussetzungen

Um diesen Schnellstart abzuschließen, benötigen Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)] und Zugriff auf SQL Server.

- [Installieren Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md).

Wenn Sie nicht auf eine SQL Server-Instanz zugreifen können, wählen Sie Ihre Plattform über einen der folgenden Links aus (hierzu benötigen Sie Ihren SQL-Anmeldenamen und das zugehörige Kennwort):

- [Windows: Herunterladen der SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads)
- [macOS: Herunterladen von SQL Server 2017 für Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)
- [Linux: Herunterladen der SQL Server 2017 Developer Edition](https://docs.microsoft.com/sql/linux/sql-server-linux-overview#install): Sie müssen nur die Schritte zum *Erstellen und Abfragen von Daten* ausführen.

## <a name="connect-to-a-sql-server"></a>Herstellen einer Verbindung mit SQL Server

1. Starten Sie **[!INCLUDE[name-sos](../includes/name-sos-short.md)]** .

2. Wenn Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)] zum ersten Mal ausführen, sollte die **Homepage** geöffnet werden. Wenn die **Homepage** nicht angezeigt wird, wählen Sie **Hilfe** > **Willkommen** aus. Wählen Sie **Neue Verbindung** aus, um den Bereich **Verbindung** zu öffnen:

   ![Symbol „Neue Verbindung“](media/quickstart-sql-server/new-connection-icon.png)

3. In diesem Artikel wird die *SQL-Anmeldung* verwendet, aber auch die *Windows-Authentifizierung* unterstützt. Füllen Sie die Felder wie folgt aus:

- **Servername:** Geben Sie hier den Servernamen ein. Beispiel: localhost.
- **Authentifizierungstyp:** SQL-Anmeldung
- **Benutzername:** Benutzername für die SQL Server-Instanz
- **Kennwort:** Kennwort für die SQL Server-Instanz
- **Datenbankname:** \<Standard\>
- **Servergruppe:** \<Standard\>

   ![Bildschirm „Neue Verbindung“](media/quickstart-sql-server/new-connection-screen.png)

## <a name="create-a-database"></a>Erstellen einer Datenbank

Mit den folgenden Schritten wird eine Datenbank mit dem Namen **TutorialDB** erstellt:

1. Klicken Sie mit der rechten Maustaste auf Ihren Server, **localhost**, und wählen Sie **Neue Abfrage** aus.

2. Fügen Sie den folgenden Codeausschnitt in das Abfragefenster ein, und klicken Sie auf **Ausführen**.

 ```sql
 USE master
 GO
 IF NOT EXISTS (
  SELECT name
  FROM sys.databases
  WHERE name = N'TutorialDB'
 )
  CREATE DATABASE [TutorialDB];
 GO
 IF SERVERPROPERTY('ProductVersion') > '12'
  ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON;
 GO
 ```

Nachdem die Abfrage abgeschlossen ist, wird die neue Datenbank **TutorialDB** in der Datenbankliste angezeigt. Wenn die Datenbank nicht angezeigt wird, klicken Sie zuerst mit der rechten Maustaste auf den Knoten **Datenbanken**, und wählen Sie **Aktualisieren** aus.

   ![Erstellen einer Datenbank](media/quickstart-sql-server/create-database.png)

## <a name="create-a-table"></a>Erstellen einer Tabelle

Der Abfrage-Editor ist immer noch mit der Datenbank *master* verbunden, aber wir möchten eine Tabelle in der Datenbank *TutorialDB* erstellen.

1. Ändern Sie den Verbindungskontext in **TutorialDB**:

   ![Kontext ändern](media/quickstart-sql-server/change-context.png)

2. Fügen Sie den folgenden Codeausschnitt in das Abfragefenster ein, und klicken Sie auf **Ausführen**:

   > [!NOTE]
   > Sie können diesen Codeausschnitt im Editor anfügen oder die vorherige Abfrage überschreiben. Beachten Sie, dass beim Klicken auf **Ausführen** nur die ausgewählte Abfrage ausgeführt wird. Wenn nichts ausgewählt ist, werden beim Klicken auf **Ausführen** alle Abfragen im Editor ausgeführt.

 ```sql
 -- Create a new table called 'Customers' in schema 'dbo'
 -- Drop the table if it already exists
 IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
  DROP TABLE dbo.Customers;
 GO
 -- Create the table in the specified schema
 CREATE TABLE dbo.Customers
 (
  CustomerId int NOT NULL PRIMARY KEY, -- primary key column
  Name nvarchar(50) NOT NULL,
  Location nvarchar(50) NOT NULL,
  Email nvarchar(50) NOT NULL
 );
 GO
 ```

Nachdem die Abfrage abgeschlossen ist, wird die neue Tabelle **Customers** in der Tabellenliste angezeigt. Möglicherweise müssen Sie mit der rechten Maustaste auf den Knoten **TutorialDB > Tables** klicken und **Aktualisieren** auswählen.

## <a name="insert-rows"></a>Einfügen von Zeilen

- Fügen Sie den folgenden Codeausschnitt in das Abfragefenster ein, und klicken Sie auf **Ausführen**:

 ```sql
 -- Insert rows into table 'Customers'
 INSERT INTO dbo.Customers
  ([CustomerId], [Name], [Location], [Email])
 VALUES
  ( 1, N'Orlando', N'Australia', N''),
  ( 2, N'Keith', N'India', N'keith0@adventure-works.com'),
  ( 3, N'Donna', N'Germany', N'donna0@adventure-works.com'),
  ( 4, N'Janet', N'United States', N'janet1@adventure-works.com')
 GO
 ```

## <a name="view-the-data-returned-by-a-query"></a>Anzeigen der von einer Abfrage zurückgegebenen Daten

1. Fügen Sie den folgenden Codeausschnitt in das Abfragefenster ein, und klicken Sie auf **Ausführen**:

 ```sql
 -- Select rows from table 'Customers'
 SELECT * FROM dbo.Customers;
 ```

   ![Select-Ergebnis](media/quickstart-sql-server/select-results.png)

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie erfolgreich eine Verbindung mit SQL Server hergestellt und eine Abfrage ausgeführt haben, probieren Sie das [Tutorial zum Code-Editor](tutorial-sql-editor.md) aus.