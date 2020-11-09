---
title: Verwenden des Transact-SQL-Editors zum Erstellen von Datenbankobjekten
description: In diesem Tutorial erfahren Sie, wie Sie den Transact-SQL-Editor verwenden, um grundlegende Datenbankaufgaben auszuführen, z. B. die Erstellung von und die Suche nach Datenbankobjekten.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18; seo-lt-2019
ms.date: 09/24/2018
ms.openlocfilehash: e2c200bc57bc62a54a9850e85e13b9c9f15c49f0
ms.sourcegitcommit: 80701484b8f404316d934ad2a85fd773e26ca30c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93243379"
---
# <a name="tutorial-use-the-transact-sql-editor-to-create-database-objects---azure-data-studio"></a>Tutorial: Verwenden des Transact-SQL-Editors zum Erstellen von Datenbankobjekten – Azure Data Studio

Das Erstellen und Ausführen von Abfragen, gespeicherten Prozeduren, Skripts usw. sind die Hauptaufgaben von Datenbankexperten. Dieses Tutorial veranschaulicht die wichtigsten Funktionen im T-SQL-Editor zum Erstellen von Datenbankobjekten.

In diesem Tutorial lernen, wie Sie [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] für folgende Vorgänge verwenden:
> [!div class="checklist"]
> * Suchen nach Datenbankobjekten
> * Bearbeiten von Tabellendaten 
> * Verwenden von Codeausschnitten zum schnellen Schreiben von T-SQL-Code
> * Anzeigen von Datenbankobjektdetails mithilfe von *Definition einsehen* und *Gehe zu Definition*


## <a name="prerequisites"></a>Voraussetzungen

Für dieses Tutorial ist die SQL Server- oder Azure SQL-Datenbank *TutorialDB* erforderlich. Um die *TutorialDB* -Datenbank zu erstellen, führen Sie eine der folgenden Schnellstartanleitungen vollständig aus:

- [Herstellen einer Verbindung mit und Abfragen von SQL Server mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Herstellen einer Verbindung mit und Abfragen von Azure SQL-Datenbank mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="quickly-locate-a-database-object-and-perform-a-common-task"></a>Schnelles Auffinden eines Datenbankobjekts und Ausführen einer allgemeinen Aufgabe

[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] bietet ein Suchwidget, mit dem sich Datenbankobjekte schnell finden lassen. Die Ergebnisliste bietet ein Kontextmenü für allgemeine Aufgaben in Bezug auf das ausgewählte Objekt, wie z.B. *Daten bearbeiten* für eine Tabelle.

1. Öffnen Sie die Randleiste SERVER ( **STRG+G** ), erweitern Sie **Datenbanken** , und wählen Sie **TutorialDB** aus. 

1. Öffnen Sie das *TutorialDB-Dashboard* , indem Sie mir der rechten Maustaste auf **TutorialDB** klicken und im Kontextmenü **Verwalten** auswählen:

   ![Kontextmenü – Verwalten](./media/tutorial-sql-editor/insight-open-dashboard.png)

1. Klicken Sie auf dem Dashboard mit der rechten Maustaste auf **dbo.Customers** (im Suchwidget), und wählen Sie **Daten bearbeiten** aus.
   
   > [!TIP]
   > Verwenden Sie bei Datenbanken mit vielen Objekten das Suchwidget, um die gesuchte Tabelle oder Ansicht schnell zu finden.

   ![Widget für die Schnellsuche](./media/tutorial-sql-editor/quick-search-widget.png)

1. Bearbeiten Sie die Spalte **Email** in der ersten Zeile. Geben Sie *orlando0\@adventure-works.com* ein, und drücken Sie die **EINGABETASTE** , um die Änderung zu speichern.

   ![Bearbeiten von Daten](./media/tutorial-sql-editor/edit-data.png)

## <a name="use-t-sql-snippets-to-create-stored-procedures"></a>Verwenden von T-SQL-Codeausschnitten zum Erstellen von gespeicherten Prozeduren

Azure Data Studio bietet viele integrierte T-SQL-Codeausschnitte zum schnellen Erstellen von Anweisungen.


1. Öffnen Sie einen neuen Abfrage-Editor, indem Sie **STRG+N** drücken.

2. Geben Sie im Editor **sql** ein, navigieren Sie mit der NACH-UNTEN-TASTE nach unten zu **sqlCreateStoredProcedure** , und drücken Sie die *TAB-TASTE* (oder die *EINGABETASTE* ), um den Codeausschnitt mit der gespeicherten Prozedur zu laden.

   ![Screenshot: Abfrage-Editor, in dem „sql“ eingegeben wurde, mit hervorgehobener Option sqlCreateStoredProcedure](./media/tutorial-sql-editor/snippet-list.png)

3. Der Codeausschnitt mit der gespeicherten Prozedur verfügt zur schnellen Bearbeitung über zwei Felder: *StoredProcedureName* und *SchemaName*. Wählen Sie *StoredProcedureName* aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Alle Vorkommen ändern** aus. Geben Sie jetzt *getCustomer* ein – alle *StoredProcedureName* -Einträge ändern sich zu *getCustomer*.

   ![Screenshot: Abfrage-Editor mit hervorgehobener Option „Change All Occurrences“ (Alle Vorkommen ändern)](./media/tutorial-sql-editor/snippet.png)

5. Ändern aller Vorkommen von *SchemaName* zu *dbo*. 
6. Der Codeausschnitt enthält Platzhalterparameter und Text, der aktualisiert werden muss. Die *EXECUTE* -Anweisung enthält auch Platzhaltertext, da noch nicht bekannt ist, wie viele Parameter in der Prozedur enthalten sein werden. Aktualisieren Sie den Codeausschnitt für dieses Tutorial so, dass er wie der folgende Code aussieht:

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
    
5. Um die gespeicherte Prozedur zu erstellen und testweise auszuführen, drücken Sie **F5**.

Die gespeicherte Prozedur ist jetzt erstellt, und der Bereich **ERGEBNISSE** zeigt den zurückgegebenen Kunden in JSON-Format an. Um den formatierten JSON-Eintrag anzuzeigen, klicken Sie auf den zurückgegebenen Datensatz. 


## <a name="use-peek-definition"></a>Verwenden von „Definition einsehen“ 

Azure Data Studio bietet die Möglichkeit, mithilfe des Features „Definition einsehen“ eine Objektdefinition anzuzeigen. In diesem Abschnitt wird eine zweite gespeicherte Prozedur erstellt und „Definition einsehen“ verwendet, um anzuzeigen, welche Spalten in einer Tabelle vorliegen, und schnell den Text der gespeicherten Prozedur zu erstellen.

1. Öffnen Sie einen neuen Editor, indem Sie **STRG+N** drücken. 

2. Geben Sie im Editor *sql* ein, navigieren Sie mit der NACH-UNTEN-TASTE nach unten zu *sqlCreateStoredProcedure* , und drücken Sie die *TAB-TASTE* (oder die *EINGABETASTE* ), um den Codeausschnitt mit der gespeicherten Prozedur zu laden.
3. Geben Sie *setCustomer* als *StoredProcedureName* und *dbo* als *SchemaName* ein.

3. Ersetzen Sie die @param-Platzhalter durch die folgende Parameterdefinition:

   ```sql
   @json_val nvarchar(max)
   ```

4. Ersetzen Sie den Text der gespeicherten Prozedur durch den folgenden Code:
   ```sql
   INSERT INTO dbo.Customers
   ```

5. Klicken Sie in der Zeile *INSERT* , die Sie gerade eingefügt haben, mit der rechten Maustaste auf **dbo.Customers** , und wählen Sie **Definition einsehen** aus.

   ![Definition einsehen](./media/tutorial-sql-editor/peek-definition.png)

6. Die Tabellendefinition wird angezeigt, sodass Sie auf einen Blick erkennen können, welche Spalten sich in der Tabelle befinden. Verwenden Sie die Spaltenliste als Referenz, um die Anweisungen für Ihre gespeicherte Prozedur ganz einfach zu erstellen. Schließen Sie die zuvor hinzugefügte INSERT-Anweisung ab, um den Text der gespeicherten Prozedur vollständig anzugeben, und schließen Sie das Fenster „Definition einsehen“:

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
7. Löschen Sie den Befehl *EXECUTE* am Ende der Abfrage, oder kommentieren Sie sie aus.
8. Die gesamte Anweisung sollte wie der folgende Code aussehen:

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

8. Um die gespeicherte Prozedur *setCustomer* zu erstellen, drücken Sie **F5**.

## <a name="use-save-query-results-as-json-to-test-the-setcustomer-stored-procedure"></a>Verwenden von „Abfrageergebnisse als JSON speichern“ zum Testen der gespeicherten Prozedur „setCustomer“

Die im vorherigen Abschnitt erstellte gespeicherte Prozedur *setCustomer* erfordert JSON-Daten für die Übergabe an den *\@json_val* -Parameter. In diesem Abschnitt wird erläutert, wie Sie ordnungsgemäß formatierte JSON-Daten zum Übergeben an den Parameter erhalten, damit Sie die gespeicherte Prozedur testen können.

1. Klicken Sie in der Randleiste **SERVER** mit der rechten Maustaste auf die Tabelle *dbo.Customers* , und klicken Sie auf **SELECT TOP 1000 Rows**.

2. Wählen Sie in der Ergebnisansicht die erste Zeile aus, stellen Sie sicher, dass die gesamte Zeile ausgewählt ist (klicken Sie auf die Nummer 1 in der Spalte ganz links), und wählen Sie **Als JSON speichern** aus.  
3. Ändern Sie den Ordner in einen leicht zu merkenden Speicherort (beispielsweise den Desktop), damit Sie die Datei später löschen können, und klicken Sie auf **Speicherort**. Die JSON-formatierte Datei wird geöffnet.

   ![Speichern als JSON](./media/tutorial-sql-editor/save-as-json.png)

4. Wählen Sie die JSON-Daten im Editor aus, und kopieren Sie sie.
5. Öffnen Sie einen neuen Editor, indem Sie **STRG+N** drücken.
6. Die oben genannten Schritte haben Ihnen gezeigt, wie Sie ganz einfach ordnungsgemäß formatierte Daten erhalten, um den Aufruf der Prozedur *setCustomer* abzuschließen. Wie Sie sehen, verwendet der folgende Code das gleiche JSON-Format, aber mit neuen Kundeninformationen, sodass wir die Prozedur *setCustomer* testen können. Die Anweisung enthält eine Syntax zum Deklarieren des Parameters und Ausführen der neuen get- und set-Prozeduren. Sie können die kopierten Daten aus dem vorherigen Abschnitt einfügen und bearbeiten, sodass sie dem folgenden Beispiel entsprechen. Sie können auch einfach die folgende Anweisung in den Abfrage-Editor einfügen.

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

7. Führen Sie das Skript aus, indem Sie **F5** drücken. Das Skript fügt einen neuen Kunden ein und gibt die neuen Kundeninformationen im JSON-Format zurück. Klicken Sie auf das Ergebnis, um eine formatierte Ansicht zu öffnen.

   ![Testergebnis](./media/tutorial-sql-editor/test-result.png)

## <a name="next-steps"></a>Nächste Schritte
In diesem Tutorial haben Sie Folgendes gelernt:
> [!div class="checklist"]
> * Schnelles Suchen nach Schemaobjekten
> * Bearbeiten von Tabellendaten 
> * Schreiben von T-SQL-Skripts mithilfe von Codeausschnitten
> * Anzeigen von Datenbankobjektdetails mithilfe von „Definition einsehen“ und „Gehe zu Definition“


Um zu erfahren, wie Sie das Widget für die **fünf langsamsten Abfragen** aktivieren, arbeiten Sie das nächste Tutorial durch:

> [!div class="nextstepaction"]
> [Aktivieren des Beispielwidgets für Erkenntnisse zu den langsamsten Abfragen](tutorial-qds-sql-server.md)
