---
title: 'Schnellstart: Verbinden Sie und Fragen Sie einer Azure SQL Data Warehouse ab'
titleSuffix: Azure Data Studio
description: Dieser schnellstartanleitung erfahren Sie, wie mit Azure Data Studio eine Verbindung mit einer Azure SQL Data Warehouse, und führen Sie eine Abfrage
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
ms.openlocfilehash: 810d03ab97fd584e1ddaab45e06a21377b81685d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959406"
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-data-in-azure-sql-data-warehouse"></a>Schnellstart: Verwendung [!INCLUDE[name-sos](../includes/name-sos-short.md)] zum Verbinden und Abfragen von Daten in Azure SQL Data Warehouse

Dieser Schnellstart veranschaulicht, wie [!INCLUDE[name-sos](../includes/name-sos-short.md)] zum Verbinden mit Azure SQL Datawarehouse, und anschließend mithilfe von Transact-SQL-Anweisungen erstellen, einfügen, und wählen Sie Daten aus. 

## <a name="prerequisites"></a>Erforderliche Komponenten
Um diesen Schnellstart abzuschließen, müssen Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)], und eine Azure SQL Datawarehouse.

- [Installieren Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).

Wenn Sie eine SQL Datawarehouse noch nicht, finden Sie unter [Erstellen eines SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-get-started-provision).

Denken Sie daran, den Servernamen und Anmeldeinformationen!


## <a name="connect-to-your-data-warehouse"></a>Verbinden Sie mit Ihrer Datawarehouse

Verwendung [!INCLUDE[name-sos](../includes/name-sos-short.md)] zum Herstellen einer Verbindung mit Ihrem Azure SQL Data Warehouse-Server.

1. Der ersten Ausführung [!INCLUDE[name-sos](../includes/name-sos-short.md)] der **Verbindung** Seite sollte zu öffnen. Wenn Sie nicht angezeigt wird der **Verbindung** auf **Verbindung hinzufügen**, oder die **neue Verbindung** Symbol in der **Server** Randleiste:
   
   ![Symbol "neue Verbindung"](media/quickstart-sql-dw/new-connection-icon.png)

2. In diesem Artikel wird *SQL-Anmeldung*, aber *Windows-Authentifizierung* wird ebenfalls unterstützt. Geben Sie die Felder, die wie folgt mithilfe der Servername, Benutzername und das Kennwort für *Ihre* Azure SQL-Server:

   | Einstellung       | Empfohlener Wert | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Servername** | Der vollqualifizierte Servername | Der Name sollte etwa wie folgt sein: **sqldwsample.database.windows.net** |
   | **Authentifizierung** | SQL-Anmeldung| In diesem Tutorial wird SQL-Authentifizierung verwendet. |
   | **Benutzername** | Das Konto des Serveradministrators | Dabei handelt es sich um das Konto, das Sie beim Erstellen des Servers angegeben haben. |
   | **Kennwort (SQL-Anmeldung)** | Das Kennwort für das Konto des Serveradministrators | Dabei handelt es sich um das Kennwort, das Sie beim Erstellen des Servers angegeben haben. |
   | **Kennwort speichern** | Ja oder Nein | Wählen Sie Ja aus, wenn Sie nicht jedes Mal das Kennwort eingeben möchten. |
   | **Datenbankname** | *Leer lassen* | Dies ist der Name der Datenbank, mit der eine Verbindung hergestellt werden soll. |
   | **Gruppe "Server"** | Wählen Sie<Default> | Wenn Sie eine Servergruppe erstellt haben, können Sie auf eine bestimmte Servergruppe festlegen. | 

   ![Symbol "neue Verbindung"](media/quickstart-sql-dw/new-connection-screen.png) 

3. Wenn es sich bei Ihrem Server eine Firewallregel mit dem Azure Data Studio eine Verbindung herstellen, sodass keine der **Firewallregel erstellen** -Formular wird geöffnet. Führen Sie das Formular, um eine neue Firewallregel zu erstellen. Weitere Informationen finden Sie unter [Firewallregeln](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure).

   ![Neue Firewallregel](media/quickstart-sql-dw/firewall.png)  

4. Nach der erfolgreichen Verbindung von Ihrem Server, die in der geöffnet wird die *Server* Randleiste.

## <a name="create-the-tutorial-data-warehouse"></a>Erstellen Sie das Tutorial Datawarehouse
1. Klicken Sie mit der rechten Maustaste auf Ihrem Server, in dem Objekt-Explorer, und wählen Sie **neue Abfrage.**

1. Fügen Sie den folgenden Codeausschnitt in der Abfrage-Editor, und klicken Sie auf **ausführen**:

   ```sql
    IF NOT EXISTS (
       SELECT name
       FROM sys.databases
       WHERE name = N'TutorialDB'
    )
    CREATE DATABASE [TutorialDB] (EDITION = 'datawarehouse', SERVICE_OBJECTIVE='DW100');
    GO  
    
    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
   ```


## <a name="create-a-table"></a>Erstellen einer Tabelle

Abfrage-Editor immer noch verbunden ist die *master* -Datenbank, aber wir möchten eine Tabelle in der *"tutorialdb"* Datenbank. 

1. Ändern den Verbindungskontext für **"tutorialdb"** :

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
      CustomerId        INT     NOT NULL,
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```


## <a name="insert-rows"></a>Einfügen von Zeilen

1. Fügen Sie den folgenden Codeausschnitt in der Abfrage-Editor, und klicken Sie auf **ausführen**:

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
      SELECT 1, N'Orlando',N'Australia', N'' UNION ALL
      SELECT 2, N'Keith', N'India', N'keith0@adventure-works.com' UNION ALL
      SELECT 3, N'Donna', N'Germany', N'donna0@adventure-works.com' UNION ALL
      SELECT 4, N'Janet', N'United States', N'janet1@adventure-works.com'
   ```


## <a name="view-the-result"></a>Das Ergebnis anzeigen
1. Fügen Sie den folgenden Codeausschnitt in der Abfrage-Editor, und klicken Sie auf **ausführen**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Die Ergebnisse der Abfrage werden angezeigt:

   ![Select-Ergebnisse](media/quickstart-sql-dw/select-results.png)


## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Weitere Artikel in dieser Sammlung bauen auf diesem Schnellstart auf. Wenn Sie auf Weiter mit nachfolgenden Schnellstarts arbeiten möchten, nicht bereinigen die Ressourcen, die in diesem Schnellstart erstellt. Wenn Sie nicht beabsichtigen, um den Vorgang fortzusetzen, verwenden Sie die folgenden Schritte aus, um erstellten Ressourcen dieses Schnellstarts im Azure-Portal löschen.
Bereinigen Sie Ressourcen durch Löschen der Ressourcengruppe, die Sie nicht mehr benötigen. Weitere Informationen finden Sie unter [Bereinigen von Ressourcen](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal#clean-up-resources).


## <a name="next-steps"></a>Nächste Schritte

Nun, dass Sie erfolgreich eine Verbindung ein Azure SQL Datawarehouse hergestellt haben und eine Abfrage ausgeführt haben, probieren Sie die [Code-Editor-Tutorials](tutorial-sql-editor.md).
