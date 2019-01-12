---
title: 'Schnellstart: Verbinden und Abfragen von SQL Server'
titleSuffix: Azure Data Studio
description: In dieser schnellstartanleitung veranschaulicht, wie Azure Data Studio eine Verbindung mit SQL Server, und führen Sie eine Abfrage
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 9e25008836b72ac8860953c5a1f98c13d7540d92
ms.sourcegitcommit: dd794633466b1da8ead9889f5e633bdf4b3389cd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54143450"
---
# <a name="quickstart-connect-and-query-sql-server-using-includename-sosincludesname-sos-shortmd"></a>Schnellstart: Verbinden und Abfragen von SQL Server verwenden [!INCLUDE[name-sos](../includes/name-sos-short.md)]
Dieser Schnellstart veranschaulicht, wie [!INCLUDE[name-sos](../includes/name-sos-short.md)] zum Verbinden mit SQL Server, und klicken Sie dann mithilfe von Transact-SQL (T-SQL)-Anweisungen zum Erstellen der *"tutorialdb"* verwendet [!INCLUDE[name-sos](../includes/name-sos-short.md)] Tutorials.

## <a name="prerequisites"></a>Erforderliche Komponenten

Um diesen Schnellstart abzuschließen, müssen Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)], und den Zugriff auf eine SQL Server.

- [Installieren Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).

Wenn Sie keinen Zugriff auf einen SQL Server haben, wählen Sie Ihre Plattform aus den folgenden Links (Stellen Sie sicher, dass Sie denken Sie daran, Ihren SQL-Anmeldung und das Kennwort!):
- [Windows: Herunterladen der SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads)
- [macOS: Herunterladen von SQL Server 2017 für Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)
- [Linux - Download SQL Server 2017 Developer Edition](https://docs.microsoft.com/sql/linux/sql-server-linux-overview#install) -müssen Sie nur die Schritte bis zu *erstellen und Abfragen von Daten*.


## <a name="connect-to-a-sql-server"></a>Herstellen einer Verbindung mit SQL Server

   
1. Starten Sie **[!INCLUDE[name-sos](../includes/name-sos-short.md)]**.
1. Der ersten Ausführung *[!INCLUDE[name-sos](../includes/name-sos-short.md)]* der **Verbindung** Dialogfeld wird geöffnet. Wenn die **Verbindung** Dialogfeld nicht geöffnet werden, klicken Sie auf die **neue Verbindung** Symbol in der **Server** Seite:
   
   ![Symbol "neue Verbindung"](media/quickstart-sql-server/new-connection-icon.png)

1. In diesem Artikel wird *SQL-Anmeldung*, aber *Windows-Authentifizierung* wird unterstützt. Füllen Sie die Felder wie folgt aus:
 
    - **Name des Servers:** "localhost"
    - **Authentifizierungstyp:** SQL-Anmeldung  
    - **Benutzername:** Benutzername für den SQL Server  
    - **Kennwort:** Kennwort für den SQLServer  
    - **Datenbankname:** dieses Feld leer lassen 
    - **Server-Gruppe:** \<Default\>  

   ![Neuen Bildschirm "Flowverbindung"](media/quickstart-sql-server/new-connection-screen.png)



## <a name="create-a-database"></a>Erstellen einer Datenbank

Die folgenden Schritte erstellen Sie eine Datenbank, die mit dem Namen **"tutorialdb"**:

1. Klicken Sie mit der rechten Maustaste auf, auf dem Server **"localhost"**, und wählen Sie **neue Abfrage.**
1. Fügen Sie den folgenden Codeausschnitt in das Abfragefenster ein: 

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

   ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
   GO
   ```
1. Um die Abfrage auszuführen, klicken Sie auf **ausführen** .

Nach Abschluss die Abfrage, die neue **"tutorialdb"** wird in der Liste der Datenbanken angezeigt. Wenn Sie nicht angezeigt wird, mit der rechten Maustaste die **Datenbanken** Knoten, und wählen **aktualisieren**.


## <a name="create-a-table"></a>Erstellen einer Tabelle

Abfrage-Editor immer noch verbunden ist die *master* -Datenbank, aber wir möchten eine Tabelle in der *"tutorialdb"* Datenbank. 

1. Ändern den Verbindungskontext für **"tutorialdb"**:

   ![Kontext ändern](media/quickstart-sql-server/change-context.png)



1. Fügen Sie den folgenden Codeausschnitt in das Abfragefenster ein, und klicken Sie auf **ausführen**:

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

Nach Abschluss die Abfrage, die neue **Kunden** Tabelle in der Liste der Tabellen angezeigt wird. Möglicherweise müssen Sie mit der rechten Maustaste die **TutorialDB > Tabellen** Knoten, und wählen **aktualisieren**.

## <a name="insert-rows"></a>Einfügen von Zeilen

- Fügen Sie den folgenden Codeausschnitt in das Abfragefenster ein, und klicken Sie auf **ausführen**:

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



## <a name="view-the-data-returned-by-a-query"></a>Zeigen Sie die von einer Abfrage zurückgegebenen Daten an
1. Fügen Sie den folgenden Codeausschnitt in das Abfragefenster ein, und klicken Sie auf **ausführen**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Die Ergebnisse der Abfrage werden angezeigt:

   ![Select-Ergebnisse](media/quickstart-sql-server/select-results.png)


## <a name="next-steps"></a>Nächste Schritte
Nun, da Sie mit SQL Server und Ausführen einer Abfrage verbunden haben, probieren Sie die [Code-Editor-Tutorials](tutorial-sql-editor.md).


