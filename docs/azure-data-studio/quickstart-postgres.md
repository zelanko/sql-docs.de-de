---
title: 'Schnellstart: Verbinden und Abfragen von PostgreSQL'
titleSuffix: Azure Data Studio
description: In dieser schnellstartanleitung veranschaulicht, wie Azure Data Studio eine Verbindung mit PostgreSQL herstellen und eine Abfrage ausführen
ms.custom: seodec18
ms.date: 03/19/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: rachel-msft
ms.author: raagyema
manager: jroth
ms.openlocfilehash: be8683ae563e4e0676f53203cb40386cf8aa4840
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66778330"
---
# <a name="quickstart-connect-and-query-postgresql-using-includename-sosincludesname-sos-shortmd"></a>Schnellstart: Eine Verbindung herzustellen und Abfragen mit PostgreSQL [!INCLUDE[name-sos](../includes/name-sos-short.md)]
Dieser Schnellstart veranschaulicht, wie [!INCLUDE[name-sos](../includes/name-sos-short.md)] Postgres herstellen, und klicken Sie dann mithilfe von SQL-Anweisungen zum Erstellen der Datenbank *"tutorialdb"* und diese abzufragen.

## <a name="prerequisites"></a>Erforderliche Komponenten

Um diesen Schnellstart abzuschließen, müssen Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)], die PostgreSQL-Erweiterung für [!INCLUDE[Name-sos](../includes/name-sos-short.md), und den Zugriff auf einen PostgreSQL-Server.

- [Installieren Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).
- [Installieren Sie die PostgreSQL-Erweiterung für Azure Data Studio](postgres-extension.md).
- [Installieren von PostgreSQL](https://www.postgresql.org/download/). (Alternativ können Sie eine Postgres-Datenbank erstellen, in der Cloud mit [az Postgres einrichten](https://docs.microsoft.com/azure/postgresql/quickstart-create-server-up-azure-cli)). 

## <a name="connect-to-postgresql"></a>Verbindung mit PostgreSQL

1. Starten Sie **[!INCLUDE[name-sos](../includes/name-sos-short.md)]** .

2. Beim ersten Start [!INCLUDE[name-sos](../includes/name-sos-short.md)] der **Verbindung** Dialogfeld wird geöffnet. Wenn die **Verbindung** Dialogfeld nicht geöffnet werden, klicken Sie auf die **neue Verbindung** Symbol in der **Server** Seite:

   ![Symbol "neue Verbindung"](media/quickstart-postgresql/new-connection-icon.png)

3. Wechseln Sie in das Formular, das wird angezeigt, zu **Verbindungstyp** , und wählen Sie **PostgreSQL** aus der Dropdownliste aus.


4. Geben Sie die verbleibenden Felder mithilfe der Servername, Benutzername und das Kennwort für den PostgreSQL-Server. 

   ![Neuen Bildschirm "Flowverbindung"](media/quickstart-postgresql/new-connection-screen.png)  

   | Einstellung       | Beispielwert | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Servername** | localhost | Der vollqualifizierte Servername |
   | **Benutzername** | postgres | Der Benutzername, die für die Anmeldung verwendet werden sollen. |
   | **Kennwort (SQL-Anmeldung)** | *password* | Das Kennwort für das Konto, dem Sie sich mit anmelden. |
   | **Kennwort** | *Check* | Aktivieren Sie dieses Kontrollkästchen, wenn Sie nicht jedes Mal das Kennwort eingeben, die Sie eine Verbindung herstellen möchten. |
   | **Datenbankname** | \<Default\> | Füllen Sie dieses aus, wenn Sie die Verbindung mit eine Datenbank angeben möchten. |
   | **Servergruppe** | \<Default\> | Dieser Option können Sie diese Verbindung mit einer bestimmten Servergruppe zuweisen, die Sie erstellen. | 
   | **Name (optional)** | *Leer lassen* | Dieser Option können Sie einen Anzeigenamen für den Server angeben. | 

5. Wählen Sie **Verbinden**. 

Nach der erfolgreichen verbindungsherstellung Ihren Server wird geöffnet, der **Server** Randleiste.


## <a name="create-a-database"></a>Erstellen einer Datenbank

Die folgenden Schritte erstellen Sie eine Datenbank, die mit dem Namen **"tutorialdb"** :

1. Mit der rechten Maustaste auf Ihrem PostgreSQL-Server in der **Server** Randleiste, und wählen **neue Abfrage**.

2. Fügen Sie die folgende SQL-Anweisung in der Abfrage-Editor, der geöffnet wird.

   ```sql
   CREATE DATABASE tutorialdb;
   ```

3. Wählen Sie auf der Symbolleiste **ausführen** zum Ausführen der Abfrage. Benachrichtigungen werden in der **Nachrichten** Bereich, um den Fortschritt der Abfrage anzuzeigen.

>[!TIP]
> Sie können **F5** auf der Tastatur zum Ausführen der Anweisung anstelle von **ausführen**.

Nach Abschluss die Abfrage, mit der rechten Maustaste **Datenbanken** , und wählen Sie **aktualisieren** , finden Sie unter **"tutorialdb"** in der Liste unter der **Datenbanken** Knoten .


## <a name="create-a-table"></a>Erstellen einer Tabelle

 Die folgenden Schritte erstellen Sie eine Tabelle in der **"tutorialdb"** :

1. Ändern den Verbindungskontext für **"tutorialdb"** mithilfe der Dropdownliste im Abfrage-Editor. 

   ![Kontext ändern](media/quickstart-postgresql/change-context.png)

2. Fügen Sie folgende SQL-Anweisung in der Abfrage-Editor, und klicken Sie auf **ausführen**. 

   > [!NOTE]
   > Sie können fügen Sie Sie oder die vorhandene Abfrage im Editor überschreiben. Auf **ausführen** führt nur die Abfrage, die hervorgehoben ist. Wenn nichts hervorgehoben ist, durch Klicken auf **ausführen** alle Abfragen im Editor ausgeführt.

   ```sql
   -- Drop the table if it already exists
   DROP TABLE IF EXISTS customers;
   -- Create a new table called 'customers'
   CREATE TABLE customers(
       customer_id SERIAL PRIMARY KEY,
       name VARCHAR (50) NOT NULL,
       location VARCHAR (50) NOT NULL,
       email VARCHAR (50) NOT NULL
   );
   ```

## <a name="insert-rows"></a>Einfügen von Zeilen

Fügen Sie den folgenden Codeausschnitt in das Abfragefenster ein, und klicken Sie auf **ausführen**:

   ```sql
   -- Insert rows into table 'customers'
   INSERT INTO customers
       (customer_id, name, location, email)
    VALUES
      ( 1, 'Orlando', 'Australia', ''),
      ( 2, 'Keith', 'India', 'keith0@adventure-works.com'),
      ( 3, 'Donna', 'Germany', 'donna0@adventure-works.com'),
      ( 4, 'Janet', 'United States','janet1@adventure-works.com');
   ```

## <a name="query-the-data"></a>Abfragen der Daten

1. Fügen Sie den folgenden Codeausschnitt in der Abfrage-Editor, und klicken Sie auf **ausführen**:
   
   ```sql
   -- Select rows from table 'customers'
   SELECT * FROM customers; 
   ```

2. Die Ergebnisse der Abfrage werden angezeigt:

   ![Anzeigen der Ergebnisse](media/quickstart-postgresql/view-results.png)

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über die [für Postgres in Azure Data Studio verfügbaren Szenarien](postgres-extension.md). 