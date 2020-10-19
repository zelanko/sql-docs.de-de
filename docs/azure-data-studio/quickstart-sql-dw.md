---
title: Verbinden und Abfragen mit Azure Synapse Analytics
description: In diesem Schnellstart erfahren Sie, wie Sie mithilfe von Azure Data Studio eine Verbindung herstellen, um einen dedizierten SQL-Pool in Azure Synapse Analytics zu verwenden und eine Abfrage auszuführen.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.reviewer: alayu, maghan, sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
ms.custom: seodec18; seo-lt-2019
ms.date: 09/24/2018
ms.openlocfilehash: c2282220dff18a7f054cc5fd01b3670b6fd14d43
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92005483"
---
# <a name="quickstart-use-azure-data-studio-to-connect-and-query-data-using-dedicated-sql-pool-in-azure-synapse-analytics"></a>Schnellstart: Verwenden von Azure Data Studio zum Verbinden mit und Abfragen von Daten mithilfe eines dedizierten SQL-Pools in Azure Synapse Analytics

In diesem Schnellstart erfahren Sie, wie Sie mit Azure Data Studio eine Verbindung mit einem dedizierten SQL-Pool in Azure Synapse Analytics herstellen und anschließend Transact-SQL-Anweisungen verwenden, um Daten zu erstellen, einzufügen und auszuwählen. 

## <a name="prerequisites"></a>Voraussetzungen
Um diesen Schnellstart ausführen zu können, benötigen Sie Azure Data Studio und einen dedizierten SQL-Pool in Azure Synapse Analytics.

- [Installieren Sie Azure Data Studio](./download-azure-data-studio.md?view=sql-server-ver15).

Wenn Sie noch nicht über einen dedizierten SQL-Pool verfügen, lesen Sie [Erstellen eines dedizierten SQL-Pools](/azure/sql-data-warehouse/sql-data-warehouse-get-started-provision).

Merken Sie sich den Servernamen und die Anmeldeinformationen!


## <a name="connect-to-your-dedicated-sql-pool"></a>Herstellen einer Verbindung mit Ihrem dedizierten SQL-Pool

Verwenden Sie Azure Data Studio, um eine Verbindung mit Ihrem Azure Synapse Analytics-Server herzustellen.

1. Wenn Sie Azure Data Studio zum ersten Mal ausführen, sollte die **Verbindungsseite** geöffnet werden. Wird die Seite **Verbindung** nicht angezeigt, klicken Sie auf **Verbindung hinzufügen**, oder klicken Sie in der Randleiste **SERVER** auf das Symbol **Neue Verbindung**:
   
   ![Symbol „Neue Verbindung“](media/quickstart-sql-dw/new-connection-icon.png)

2. In diesem Artikel wird die *SQL-Anmeldung* verwendet, aber auch die *Windows-Authentifizierung* wird unterstützt. Füllen Sie die Felder wie folgt aus, wozu Sie den Servernamen, den Benutzernamen und das Kennwort für *Ihre* Azure SQL Server-Instanz verwenden:

   | Einstellung       | Vorgeschlagener Wert | BESCHREIBUNG |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Servername** | Der vollqualifizierte Servername | Der Name sollte in etwa wie folgt lauten: **sqldwsample.database.windows.net** |
   | **Authentifizierung** | SQL-Anmeldung| In diesem Tutorial wird SQL-Authentifizierung verwendet. |
   | **Benutzername** | Das Serveradministratorkonto | Hierbei handelt es sich um das Konto, das Sie beim Erstellen des Servers angegeben haben. |
   | **Kennwort (SQL-Anmeldung)** | Das Kennwort für das Serveradministratorkonto | Hierbei handelt es sich um das Kennwort, das Sie beim Erstellen des Servers angegeben haben. |
   | **Kennwort speichern** | Ja oder Nein | Wählen Sie „Ja“ aus, wenn Sie Ihr Kennwort nicht jedes Mal eingeben möchten. |
   | **Datenbankname** | *Leer lassen* | Dies ist der Name der Datenbank, mit der eine Verbindung hergestellt werden soll. |
   | **Servergruppe** | <Default> auswählen | Wenn Sie eine Servergruppe erstellt haben, können Sie dieses Feld auf eine bestimmte Servergruppe festlegen. | 

   ![Symbol „Neue Verbindung“](media/quickstart-sql-dw/new-connection-screen.png) 

3. Wenn der Server nicht über eine Firewallregel verfügt, die Azure Data Studio ermöglicht, eine Verbindung herzustellen, wird das Formular **Neue Firewallregel erstellen** geöffnet. Füllen Sie das Formular aus, um eine neue Firewallregel zu erstellen. Weitere Informationen finden Sie unter [Firewallregeln](/azure/sql-database/sql-database-firewall-configure).

   ![Neue Firewallregel](media/quickstart-sql-dw/firewall.png)  

4. Nachdem die Verbindung erfolgreich hergestellt wurde, wird Ihr Server in der Randleiste *SERVER* geöffnet.

## <a name="create-the-tutorial-dedicated-sql-pool"></a>Erstellen des dedizierten SQL-Pools für das Tutorial
1. Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf Ihren Server, und wählen Sie **Neue Abfrage** aus.

1. Fügen Sie den folgenden Codeausschnitt in den Abfrage-Editor ein, und klicken Sie auf **Ausführen**:

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

Der Abfrage-Editor ist immer noch mit der Datenbank *master* verbunden, aber wir möchten eine Tabelle in der Datenbank *TutorialDB* erstellen. 

1. Ändern Sie den Verbindungskontext in **TutorialDB**:

   ![Kontext ändern](media/quickstart-sql-database/change-context.png)


1. Fügen Sie den folgenden Codeausschnitt in den Abfrage-Editor ein, und klicken Sie auf **Ausführen**:

   > [!NOTE]
   > Sie können diesen Codeausschnitt im Editor an die vorherige Abfrage anfügen oder überschreiben. Beachten Sie, dass beim Klicken auf **Ausführen** nur die ausgewählte Abfrage ausgeführt wird. Wenn nichts ausgewählt ist, werden beim Klicken auf **Ausführen** alle Abfragen im Editor ausgeführt.

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

1. Fügen Sie den folgenden Codeausschnitt in den Abfrage-Editor ein, und klicken Sie auf **Ausführen**:

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
      SELECT 1, N'Orlando',N'Australia', N'' UNION ALL
      SELECT 2, N'Keith', N'India', N'keith0@adventure-works.com' UNION ALL
      SELECT 3, N'Donna', N'Germany', N'donna0@adventure-works.com' UNION ALL
      SELECT 4, N'Janet', N'United States', N'janet1@adventure-works.com'
   ```


## <a name="view-the-result"></a>Anzeigen des Ergebnisses
1. Fügen Sie den folgenden Codeausschnitt in den Abfrage-Editor ein, und klicken Sie auf **Ausführen**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Die Abfrageergebnisse werden angezeigt:

   ![Select-Ergebnis](media/quickstart-sql-dw/select-results.png)


## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Andere Artikel in dieser Sammlung bauen auf diesem Schnellstart auf. Wenn Sie die Absicht haben, mit den nachfolgenden Schnellstarts weiterzuarbeiten, sollten Sie die in diesem Schnellstart erstellten Ressourcen nicht bereinigen. Wenn Sie nicht weiterarbeiten möchten, führen Sie im Azure-Portal die folgenden Schritte aus, um die Ressourcen zu löschen, die in diesem Schnellstart erstellt wurden.
Bereinigen Sie die Ressourcen, indem Sie die Ressourcengruppen löschen, die Sie nicht mehr benötigen. Weitere Informationen finden Sie unter [Bereinigen von Ressourcen](/azure/sql-database/sql-database-get-started-portal#clean-up-resources).


## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie erfolgreich eine Verbindung mit Azure Synapse Analytics hergestellt und eine Abfrage ausgeführt haben, wechseln Sie zum [Tutorial zum Code-Editor](tutorial-sql-editor.md).