---
title: 'Lernprogramm: Verwenden Sie den Transact-SQL-Editor zum Erstellen von Datenbankobjekten'
titleSuffix: Azure Data Studio
description: Dieses Tutorial veranschaulicht die wichtigsten Features in Azure Data Studio, die die Arbeit mit T-SQL zu vereinfachen.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: tutorial
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 04e6e366d1fd0a5d710296353d6326022f716199
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030454"
---
# <a name="tutorial-use-the-transact-sql-editor-to-create-database-objects---includename-sosincludesname-sos-shortmd"></a>Lernprogramm: Verwendung der Transact-SQL-Editor, um Datenbankobjekte zu erstellen: [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Erstellen und Ausführen von Abfragen, werden gespeicherte Prozeduren, Skripts usw. Datenbankexperten die zentralen Aufgaben. Dieses Tutorial veranschaulicht die wichtigsten Funktionen der T-SQL-Editor, um Datenbankobjekte zu erstellen.

In diesem Tutorial erfahren Sie, wie Sie mit [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] auf:
> [!div class="checklist"]
> * Die Datenbankobjekte suchen
> * Bearbeiten Sie Tabellendaten 
> * Verwenden Sie Codeausschnitte schnell Schreiben von T-SQL
> * View Database Details zum Objekt mit *"Definition einsehen"* und *Gehe zu Definition*


## <a name="prerequisites"></a>Erforderliche Komponenten

In diesem Lernprogramm der SQL Server- oder Azure SQL-Datenbank *"tutorialdb"*. Zum Erstellen der *"tutorialdb"* Datenbank, führen Sie eine der folgenden schnellstartanleitungen:

- [Verbinden und Abfragen von SQL Server verwenden [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Verbinden und Abfragen von Azure SQL-Datenbank [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="quickly-locate-a-database-object-and-perform-a-common-task"></a>Schnell suchen Sie ein Datenbankobjekt zu, und führen Sie eine gängige Aufgabe

[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] bietet eine Such-Widget-Datenbankobjekte schnell zu finden. Die Ergebnisliste enthält ein Kontextmenü für allgemeine Aufgaben, die relevant für das ausgewählte Objekt wie z. B. *Daten bearbeiten* für eine Tabelle.

1. Öffnen Sie die Server-Randleiste (**STRG + G**), erweitern Sie **Datenbanken**, und wählen Sie **"tutorialdb"**. 

1. Öffnen der *"tutorialdb" Dashboard* mit der rechten Maustaste **"tutorialdb"** und **verwalten** aus dem Kontextmenü:

   ![Kontextmenü – verwalten](./media/tutorial-sql-editor/insight-open-dashboard.png)

1. Klicken Sie auf dem Dashboard mit der Maustaste **Dbo. Kunden** (in der Such-Widget), und wählen Sie **Daten bearbeiten**.
   
   > [!TIP]
   > Verwenden Sie das Such-Widget für Datenbanken mit vielen Objekten um schnell zu finden, die Tabelle, Sicht usw., die Sie suchen.

   ![Schnellsuche-widget](./media/tutorial-sql-editor/quick-search-widget.png)

1. Bearbeiten der **-e-Mail** -Spalte in der ersten Zeile Typ *orlando0@adventure-works.com*, und drücken Sie **EINGABETASTE** um die Änderung zu speichern.

   ![Bearbeiten von Daten](./media/tutorial-sql-editor/edit-data.png)

## <a name="use-t-sql-snippets-to-create-stored-procedures"></a>Verwenden Sie T-SQL-Ausschnitten, um gespeicherte Prozeduren erstellen

[!INCLUDE[name-sos](../includes/name-sos-short.md)] stellt viele integrierte T-SQL-Ausschnitte für das schnelle Erstellen von Anweisungen bereit.


1. Öffnen Sie einen neues Abfrage-Editor, indem Sie mit **STRG + N**.

2. Typ **Sql** im Editor, Pfeil nach unten bis zum **SqlCreateStoredProcedure**, und drücken Sie die *Registerkarte* Schlüssel (oder *EINGABETASTE*) beim Laden des gespeicherten erstellen Ausschnitt einer Prozedur.

   ![Codeausschnitt-Liste](./media/tutorial-sql-editor/snippet-list.png)

3. Der Codeausschnitt der erstellen-gespeicherte Prozedur enthält zwei Felder, die richten Sie für schnelle Bearbeitung *StoredProcedureName* und *SchemaName*. Wählen Sie *StoredProcedureName*, mit der rechten Maustaste, und wählen **ändern alle Vorkommen**. Geben Sie nun *GetCustomer* und alle *StoredProcedureName* Einträge zu ändern, um *GetCustomer*.

   ![Codeausschnitt](./media/tutorial-sql-editor/snippet.png)

5. Ändern Sie alle Vorkommen von *SchemaName* zu *Dbo*. 
6. Der Ausschnitt enthält für Platzhalterparameter und Textkörper, die benötigt wird aktualisiert. Die *EXECUTE* -Anweisung enthält ebenfalls Platzhaltertext, da die Prozedur verfügt über wie viele Parameter unbekannt ist. Für dieses Tutorial aktualisieren Sie den Ausschnitt es sieht so wie im folgenden Code:

    ```sql
    -- Create a new stored procedure called 'getCustomer' in schema 'dbo'
    -- Drop the stored procedure if it already exists
    IF EXISTS (
    SELECT *
    FROM INFORMATION_SCHEMA.ROUTINES
    WHERE SPECIFIC_SCHEMA = N'dbo'
    AND SPECIFIC_NAME = N'getCustomer'
    )
    DROP PROCEDURE dbo.getCustomer
    GO
    -- Create the stored procedure in the specified schema
    CREATE PROCEDURE dbo.getCustomer
    @ID int
    -- add more stored procedure parameters here
    AS
    -- body of the stored procedure
    SELECT  c.CustomerId, 
    c.Name, 
    c.Location, 
    c.Email
    FROM dbo.Customers c
    WHERE c.CustomerId = @ID
    FOR JSON PATH

    GO
    -- example to execute the stored procedure we just created
    EXECUTE dbo.getCustomer 1
    GO
    ```
    
5. Erstellen die gespeicherte Prozedur, und geben sie einen Testlauf, drücken Sie die **F5**.

Die gespeicherte Prozedur wird jetzt erstellt, und die **Ergebnisse** Bereich zeigt den zurückgegebenen Kunden im JSON-Format. Um formatierten JSON anzuzeigen, klicken Sie auf die zurückgegebenen Datensätze. 


## <a name="use-peek-definition"></a>Verwenden von "Definition einsehen" 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] bietet die Möglichkeit, eine Objekte Definition mithilfe der Funktion der Peek-Definition anzuzeigen. In diesem Abschnitt wird eine zweite gespeicherte Prozedur erstellt und "Definition einsehen" verwendet, um festzustellen, welche Spalten in einer Tabelle, um schnell den Text der gespeicherten Prozedur zu erstellen sind.

1. Öffnen Sie einen neuen Editor, indem Sie mit **STRG + N**. 

2. Typ *Sql* im Editor, Pfeil nach unten bis zum *SqlCreateStoredProcedure*, und drücken Sie die *Registerkarte* Schlüssel (oder *EINGABETASTE*) beim Laden des gespeicherten erstellen Ausschnitt einer Prozedur.
3. Geben Sie in *SetCustomer* für *StoredProcedureName* und *Dbo* für *SchemaName*

3. Ersetzen Sie die @param -Platzhalter durch den folgenden Parameterdefinition:

   ```sql
   @json_val nvarchar(max)
   ```

4. Ersetzen Sie den Text der gespeicherten Prozedur, durch den folgenden Code:
   ```sql
   INSERT INTO dbo.Customers
   ```

5. In der *einfügen* Zeile Sie gerade hinzugefügt, mit der rechten Maustaste **Dbo. Kunden** , und wählen Sie **"Definition einsehen"**.

   !["Definition einsehen"](./media/tutorial-sql-editor/peek-definition.png)

6. Die Definition der Tabelle angezeigt, damit Sie schnell sehen welche Spalten in der Tabelle enthalten sind. Finden Sie in der Liste der Spalten auf einfache Weise die Anweisungen für die gespeicherte Prozedur abschließen. Beenden Sie die INSERT-Anweisung, die Sie zuvor hinzugefügt haben, führen den Text der gespeicherten Prozedur, und Schließen des Peek-definitionsfensters erstellen:

   ```sql
   INSERT INTO dbo.Customers (CustomerId, Name, Location, Email)
       SELECT CustomerId, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerId int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
    )
   ```
7. Kommentieren Sie (oder löschen) den *EXECUTE* Befehl am Ende der Abfrage.
8. Die gesamte Anweisung sollte wie im folgenden Code aussehen:

   ```sql
   -- Create a new stored procedure called 'setCustomer' in schema 'dbo'
   -- Drop the stored procedure if it already exists
   IF EXISTS (
   SELECT *
       FROM INFORMATION_SCHEMA.ROUTINES
       WHERE SPECIFIC_SCHEMA = N'dbo'
       AND SPECIFIC_NAME = N'setCustomer'
   )
   DROP PROCEDURE dbo.setCustomer
   GO
   -- Create the stored procedure in the specified schema
   CREATE PROCEDURE dbo.setCustomer
       @json_val nvarchar(max) 
   AS
       -- body of the stored procedure
       INSERT INTO dbo.Customers (CustomerId, Name, Location, Email)
       SELECT CustomerId, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerId int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
       )
   GO
   ```

8. Zum Erstellen der *SetCustomer* gespeicherte Prozedur, drücken Sie **F5**.

## <a name="use-save-query-results-as-json-to-test-the-setcustomer-stored-procedure"></a>Verwenden Sie Abfrageergebnissen als JSON-Code zum Testen der SetCustomer, die gespeicherte Prozedur speichern

Die *SetCustomer* gespeicherte Prozedur, die im vorherigen Abschnitt erstellten erfordert JSON Daten übergeben werden, in der *@json_val* Parameter. Dieser Abschnitt beschreibt die abzurufenden etwas ordnungsgemäß formatierter JSON-Code für den Parameter übergeben, damit Sie die gespeicherte Prozedur testen können.

1. In der **Server** mit der rechten Maustaste der Randleiste die *Dbo. Kunden* Tabelle, und klicken Sie auf **oberste 1000 Zeilen auswählen**.

2. Wählen Sie die erste Zeile in der Ergebnisansicht, stellen Sie sicher, dass die gesamte Zeile ausgewählt ist (klicken Sie auf die Zahl 1 in der Spalte ganz links), und wählen Sie **als JSON speichern**.  
3. Ändern Sie den Ordner an einem Speicherort, die Sie erinnern sich, löschen Sie die Datei später (für Beispiel-Desktop) und klicken Sie auf **speichern**. Die JSON formatierte Datei wird geöffnet.

   ![im JSON-Format speichern](./media/tutorial-sql-editor/save-as-json.png)

4. Wählen Sie die JSON-Daten im Editor, und kopieren Sie ihn.
5. Öffnen Sie einen neuen Editor, indem Sie mit **STRG + N**.
6. Die vorherigen Schritte zeigen, wie Sie die ordnungsgemäß formatierten Daten den Aufruf abgeschlossen problemlos abrufen können die *SetCustomer* Verfahren. Sie sehen, dass der folgende Code verwendet das gleiche JSON-Format mit neuen Details für Kunden, damit wir testen, können die *SetCustomer* Verfahren. Die Anweisung enthält Syntax zum Deklarieren Sie den Parameter, und führen Sie die neue Get und set-Prozeduren. Sie können fügen Sie die kopierten Daten aus dem vorherigen Abschnitt und bearbeiten sie daher das gleiche wie im folgenden Beispiel wird, oder fügen Sie einfach die folgende Anweisung in der Abfrage-Editor.

   ```sql
   -- example to execute the stored procedure we just created
   declare @json nvarchar(max) =
   N'[
       {
           "CustomerId": 5,
           "Name": "Lucy",
           "Location": "Canada",
           "Email": "lucy0@adventure-works.com"
       }
   ]'

   EXECUTE dbo.setCustomer @json_val = @json
   GO

   EXECUTE dbo.getCustomer @ID = 5
   ```

7. Führen Sie das Skript durch Drücken von **F5**. Das Skript fügt einen neuen Kunden und die neuen Informationen des Kunden im JSON-Format zurückgibt. Klicken Sie auf das Ergebnis, um eine formatierte Ansicht zu öffnen.

   ![Testergebnis](./media/tutorial-sql-editor/test-result.png)

## <a name="next-steps"></a>Nächste Schritte
In diesem Tutorial haben Sie gelernt, wie die folgenden Aufgaben ausgeführt werden:
> [!div class="checklist"]
> * Schnellsuche Schemaobjekte
> * Bearbeiten Sie Tabellendaten 
> * Schreiben von T-SQL-Skript mithilfe von Codeausschnitten
> * Erfahren Sie mehr über die Details der Datenbank-Objekt mithilfe von "Definition einsehen" und Gehe zu Definition


Informationen zum Aktivieren der **fünf langsamsten Abfragen** -Widget erstellen, führen Sie im nächste Tutorial:

> [!div class="nextstepaction"]
> [Aktivieren Sie das langsame Abfragen Beispiel Insight-widget](tutorial-qds-sql-server.md)
