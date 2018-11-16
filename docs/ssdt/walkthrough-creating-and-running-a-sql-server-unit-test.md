---
title: 'Exemplarische Vorgehensweise: Erstellen und Ausführen eines SQL Server-Komponententests | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 992c1d8e-3729-438b-9ef4-cd103e28f145
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 86f54b31eb9bab93b6a4a3be918e1011f023ab5b
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51666519"
---
# <a name="walkthrough-creating-and-running-a-sql-server-unit-test"></a>Exemplarische Vorgehensweise: Erstellen und Ausführen eines SQL Server-Komponententests
In dieser exemplarischen Vorgehensweise erstellen Sie einen SQL Server-Komponententest, mit dem das Verhalten mehrerer gespeicherter Prozeduren überprüft wird. Mithilfe von SQL Server-Komponententests können Codefehler, die u.U. ein fehlerhaftes Anwendungsverhalten verursachen, leichter identifiziert werden. SQL Server-Komponententests und -Anwendungstests können im Rahmen einer automatisierten Testreihe ausgeführt werden.  
  
In dieser exemplarischen Vorgehensweise führen Sie folgende Aufgaben aus:  
  
-   [Erstellen eines Skripts, das ein Datenbankschema enthält](#CreateScript)  
  
-   [Erstellen eines Datenbankprojekts und Importieren des Schemas](#CreateProjectAndImport)  
  
-   [Bereitstellen des Datenbankprojekts in einer isolierten Entwicklungsumgebung](#DeployDBProj)  
  
-   [Erstellen von SQL Server-Komponententests](#CreateDBUnitTests)  
  
-   [Definieren einer Testlogik](#DefineTestLogic)  
  
-   [Ausführen von SQL Server-Komponententests](#RunTests)  
  
-   [Hinzufügen eines negativen Komponententests](#NegativeTest)  
  
Nachdem durch einen der Komponententests ein Fehler in einer gespeicherten Prozedur erkannt wurde, beheben Sie den Fehler und führen den Test erneut aus.  
  
## <a name="prerequisites"></a>Voraussetzungen  
Zum Durchführen dieser exemplarischen Vorgehensweise müssen Sie in der Lage sein, eine Verbindung mit einem Datenbankserver (bzw. LocalDB-Datenbank) herzustellen, auf dem bzw. der Sie über Berechtigungen zum Erstellen und Bereitstellen einer Datenbank verfügen. Weitere Informationen finden Sie unter [Erforderliche Berechtigungen für Datenbankfunktionen von Visual Studio](https://msdn.microsoft.com/library/aa833413(VS.100).aspx).  
  
## <a name="CreateScript"></a>Erstellen eines Skripts, das ein Datenbankschema enthält  
  
#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>So erstellen Sie ein Skript, aus dem ein Schema importiert werden kann  
  
1.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Datei**.  
  
    Das Dialogfeld **Neue Datei** wird angezeigt.  
  
2.  Klicken Sie in der Liste **Kategorien** auf **Allgemein** , falls die Option noch nicht hervorgehoben ist.  
  
3.  Klicken Sie in der Liste **Vorlagen** auf **SQL-Datei**, und klicken Sie dann auf **Öffnen**.  
  
    Der Transact\-SQL-Editor wird geöffnet.  
  
4.  Kopieren Sie den folgenden Transact\-SQL-Code, und fügen Sie ihn in den Transact\-SQL-Editor ein.  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40)  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SELECT SCOPE_IDENTITY()  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5.  Speichern Sie die Datei. Notieren Sie sich den Speicherort, da dieses Skript im nächsten Verfahren benötigt wird.  
  
6.  Klicken Sie im Menü **Datei** auf **Projektmappe schließen**.  
  
    Als Nächstes erstellen Sie ein Datenbankprojekt und importieren das Schema aus dem erstellten Skript.  
  
## <a name="CreateProjectAndImport"></a>Erstellen eines Datenbankprojekts und Importieren eines Schemas  
  
#### <a name="to-create-a-database-project"></a>So erstellen Sie ein Datenbankprojekt  
  
1.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie auf **Projekt**.  
  
    Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Wählen Sie unter **Installierte Vorlagen** den Knoten **SQL Server** und dann **SQL Server-Datenbankprojekt** aus.  
  
3.  Geben Sie im Feld **Name**den Namen **SimpleUnitTestDB**ein.  
  
4.  Aktivieren Sie das Kontrollkästchen **Projektmappenverzeichnis erstellen** , falls es noch nicht aktiviert ist.  
  
5.  Deaktivieren Sie das Kontrollkästchen **Zur Quellcodeverwaltung hinzufügen** , wenn es noch nicht deaktiviert ist, und klicken Sie auf **OK**.  
  
    Das Datenbankprojekt wird erstellt und im **Projektmappen-Explorer**angezeigt. Als Nächstes importieren Sie das Datenbankschema aus einem Skript.  
  
#### <a name="to-import-a-database-schema-from-a-script"></a>So importieren Sie ein Datenbankschema aus einem Skript  
  
1.  Klicken Sie im Menü **Projekt** auf **Importieren** und dann auf **Skript (\*.sql)**.  
  
2.  Klicken Sie auf **Weiter** , nachdem Sie die Informationen auf der Willkommensseite gelesen haben.  
  
3.  Klicken Sie auf **Durchsuchen**, und wechseln Sie zu dem Verzeichnis, in dem Sie die SQL-Datei gespeichert haben.  
  
4.  Doppelklicken Sie auf die SQL-Datei, und klicken Sie auf **Fertig stellen**.  
  
    Das Skript wird importiert, und die im Skript definierten Objekte werden dem Datenbankprojekt hinzugefügt.  
  
5.  Überprüfen Sie die Zusammenfassung, und klicken Sie dann auf **Fertig stellen** , um den Vorgang abzuschließen.  
  
    > [!NOTE]  
    > In die Prozedur Sales.uspFillOrder wurde absichtlich ein Codefehler eingefügt, den Sie im weiteren Verlauf dieses Verfahrens ermitteln und beheben werden.  
  
#### <a name="to-examine-the-resulting-project"></a>So überprüfen Sie das resultierende Projekt  
  
1.  Untersuchen Sie im **Projektmappen-Explorer**die Skriptdateien, die in das Projekt importiert wurden.  
  
2.  Suchen Sie im **SQL Server-Objekt-Explorer** die Datenbank unter dem Knoten „Projekte“.  
  
## <a name="DeployDBProj"></a>Bereitstellen in LocalDB  
Wenn Sie F5 drücken, wird die Datenbank standardmäßig auf einer LocalDB-Datenbank bereitgestellt (bzw. veröffentlicht). Sie können den Datenbankpfad ändern, indem Sie auf der Eigenschaftenseite des Projekts die Registerkarte „Debuggen“ öffnen und die Verbindungszeichenfolge ändern.  
  
## <a name="CreateDBUnitTests"></a>Erstellen von SQL Server-Komponententests  
  
#### <a name="to-create-a-sql-server-unit-test-for-the-stored-procedures"></a>So erstellen Sie einen SQL Server-Komponententest für die gespeicherten Prozeduren  
  
1.  Erweitern Sie im **SQL Server-Objekt-Explorer** den Projektknoten für **SimpleUnitTestDB** und dann den Knoten **Programmierbarkeit** und **Gespeicherte Prozeduren**.  
  
2.  Klicken Sie mit der rechten Maustaste auf eine der gespeicherten Prozeduren und dann auf **Komponententests erstellen**, um das Dialogfeld **Komponententests erstellen** anzuzeigen.  
  
3.  Aktivieren Sie die Kontrollkästchen für alle fünf gespeicherten Prozeduren: **Sales.uspCancelOrder**, **Sales.uspFillOrder**, **Sales.uspNewCustomer**, **Sales.uspPlaceNewOrder**und **Sales.uspShowOrderDetails**.  
  
4.  Wählen Sie in der Dropdownliste **Projekt** die Option **Neues Visual C#-Testprojekt erstellen** aus.  
  
5.  Akzeptieren Sie die standardmäßigen Projekt- und Klassennamen, und klicken Sie auf **OK**.  
  
6.  Geben Sie im Dialogfeld „Testkonfiguration“ unter **Komponententests unter Verwendung folgender Datenverbindung ausführen**eine Verbindung mit der Datenbank an, die Sie zuvor in dieser exemplarischen Vorgehensweise bereitgestellt haben. Wenn Sie beispielsweise den Standardbereitstellungsspeicherort, d.h. LocalDB, verwendet haben, würden Sie auf **Neue Verbindung** klicken und **(LocalDB)\Projects** angeben. Wählen Sie anschließend den Namen der Datenbank aus. Klicken Sie dann auf „OK“, um das Dialogfeld **Verbindungseigenschaften** zu schließen.  
  
    > [!NOTE]  
    > Zum Testen von Sichten oder gespeicherte Prozeduren mit eingeschränkten Berechtigungen würden Sie in diesem Schritt normalerweise diese Verbindung angeben. Anschließend würden Sie die sekundäre Verbindung mit ausgedehnteren Berechtigungen angeben, um den Test zu überprüfen. Falls Sie über eine sekundäre Verbindung verfügen, sollten Sie diesen Benutzer dem Datenbankprojekt hinzufügen und im Skript vor der Bereitstellung einen Anmeldenamen für den Benutzer erstellen.  
  
7.  Aktivieren Sie im Dialogfeld „Testkonfiguration“ im Abschnitt **Bereitstellung** das Kontrollkästchen **Datenbankprojekt automatisch vor dem Ausführen von Komponententests bereitstellen** .  
  
8.  Klicken Sie unter **Datenbankprojekt**auf **SimpleUnitTestDB.sqlproj**.  
  
9. Klicken Sie unter **Bereitstellungskonfiguration**auf **Debuggen**.  
  
    Sie können im Rahmen der SQL Server-Komponententests auch Testdaten generieren. In dieser exemplarischen Vorgehensweise überspringen Sie diesen Schritt, da durch die Tests eigene Daten erstellt werden.  
  
10. Klicken Sie auf **OK**.  
  
    Das Testprojekt wird erstellt, und der SQL Server-Komponententest-Designer wird angezeigt. Als Nächstes aktualisieren Sie die Testlogik im Transact\-SQL-Skript der Komponententests.  
  
## <a name="DefineTestLogic"></a>Definieren einer Testlogik  
Die sehr einfache Datenbank enthält die beiden Tabellen „Customer“ und „Order“. Sie aktualisieren die Datenbank mithilfe der folgenden gespeicherten Prozeduren:  
  
-   uspNewCustomer: Diese gespeicherte Prozedur fügt der Tabelle „Customer“ einen Datensatz hinzu, durch den die Spalten „YTDOrders“ und „YTDSales“ des Kunden auf 0 (null) festgelegt werden.  
  
-   uspPlaceNewOrder: Diese gespeicherte Prozedur fügt der Tabelle „Orders“ für den angegebenen Kunden einen Datensatz hinzu und aktualisiert den Wert von „YTDOrders“ im entsprechenden Datensatz der Tabelle „Customer“.  
  
-   uspFillOrder: Diese gespeicherte Prozedur aktualisiert einen Datensatz in der Tabelle „Orders“, indem der Status von „O“ in „F“ geändert wird, und erhöht den Betrag für „YTDSales“ im entsprechenden Datensatz der Tabelle „Customer“.  
  
-   uspCancelOrder: Diese gespeicherte Prozedur aktualisiert einen Datensatz in der Tabelle „Orders“, indem der Status von „O“ in „X“ geändert wird, und verringert den Betrag für „YTDOrders“ im entsprechenden Datensatz der Tabelle „Customer“.  
  
-   uspShowOrderDetails: Diese gespeicherte Prozedur verknüpft die Tabelle Orders mit der Tabelle Customer und zeigt die Datensätze für einen bestimmten Kunden an.  
  
> [!NOTE]  
> In diesem Beispiel wird die Erstellung eines einfachen SQL Server-Komponententests veranschaulicht. In einer realen Datenbank könnten Sie die Gesamtmenge aller Bestellungen mit dem Status "O" oder "F" für einen bestimmten Kunden summieren. Die Prozeduren in dieser exemplarischen Vorgehensweise verzichten auch auf eine Fehlerbehandlung. Beispielsweise wird nicht verhindert, dass „uspFillOrder“ für eine Bestellung aufgerufen wird, die bereits ausgeführt wurde.  
  
Zu Testbeginn wird davon ausgegangen, dass die Datenbank einen fehlerfreien Zustand aufweist. Mit den von Ihnen erstellten Tests werden folgende Bedingungen überprüft:  
  
-   uspNewCustomer: Überprüft, ob die Tabelle „Customer“ nach Ausführung der gespeicherten Prozedur eine Zeile enthält.  
  
-   uspPlaceNewOrder: Geben Sie für den Kunden mit „CustomerID“ 1 eine Bestellung im Wert von 100 US-Dollar auf. Vergewissern Sie sich, dass der Betrag für „YTDOrders“ für diesen Kunden „100“ und dass der Betrag für „YTDSales“ 0 (null) beträgt.  
  
-   uspFillOrder: Geben Sie für den Kunden mit „CustomerID“ 1 eine Bestellung im Wert von 50 US-Dollar auf. Führen Sie die Bestellung aus. Vergewissern Sie sich, dass die Beträge für „YTDOrders“ und „YTDSales“ beide „50“ lauten.  
  
-   uspShowOrderDetails: Geben Sie für den Kunden mit „CustomerID“ 1 Bestellungen im Wert von 100, 50 und 5 US-Dollar auf. Vergewissern Sie sich, dass von uspShowOrderDetails die richtige Anzahl von Spalten zurückgegeben wird und dass das Resultset die erwartete Prüfsumme aufweist.  
  
> [!NOTE]  
> Bei einer vollständigen Gruppe von SQL Server-Komponententests überprüfen Sie in der Regel, ob die anderen Spalten korrekt festgelegt wurden. Da diese exemplarische Vorgehensweise überschaubar bleiben soll, wird nicht beschrieben, wie das Verhalten von uspCancelOrder überprüft wird.  
  
#### <a name="to-write-the-sql-server-unit-test-for-uspnewcustomer"></a>So schreiben Sie den SQL Server-Komponententest für uspNewCustomer  
  
1.  Klicken Sie auf der Navigationsleiste des SQL Server-Komponententest-Designers auf **Sales_uspNewCustomerTest**, und achten Sie darauf, dass **Test** in der nebenstehenden Liste markiert ist.  
  
    Nachdem Sie den vorherigen Schritt ausgeführt haben, können Sie das Testskript für die Testaktion im Komponententest erstellen.  
  
2.  Aktualisieren Sie die Transact\-SQL-Anweisungen im Transact\-SQL-Editor, damit sie folgenden Anweisungen entsprechen:  
  
    ```  
    -- ssNoVersion unit test for Sales.uspNewCustomer  
    DECLARE @RC AS INT, @CustomerName AS NVARCHAR (40);  
  
    SELECT @RC = 0,  
           @CustomerName = 'Fictitious Customer';  
  
    EXECUTE @RC = [Sales].[uspNewCustomer] @CustomerName;  
  
    SELECT * FROM [Sales].[Customer];  
    ```  
  
3.  Klicken Sie im Bereich **Testbedingungen** erst auf die Testbedingung „Nicht eindeutig“ und dann auf das Symbol **Testbedingung löschen** (das rote „X“).  
  
4.  Klicken Sie im Bereich **Testbedingungen** in der Liste auf **Zeilenanzahl**, und klicken Sie dann auf **Testbedingung hinzufügen** (das grüne „+“).  
  
5.  Öffnen Sie das Fenster **Eigenschaften** (wählen Sie die Testbedingung aus, und drücken Sie F4), und legen Sie die Eigenschaft **Zeilenanzahl** auf „1“ fest.  
  
6.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
    Als Nächstes definieren Sie die Logik des Komponententests für uspPlaceNewOrder.  
  
#### <a name="to-write-the-sql-server-unit-test-for-uspplaceneworder"></a>So schreiben Sie den SQL Server-Komponententest für uspPlaceNewOrder  
  
1.  Klicken Sie auf der Navigationsleiste des SQL Server-Komponententest-Designers auf **Sales_uspPlaceNewOrderTest**, und achten Sie darauf, dass **Test** in der nebenstehenden Liste markiert ist.  
  
    Nachdem Sie diesen Schritt ausgeführt haben, können Sie das Testskript für die Testaktion im Komponententest erstellen.  
  
2.  Aktualisieren Sie die Transact\-SQL-Anweisungen im Transact\-SQL-Editor, damit sie folgenden Anweisungen entsprechen:  
  
    ```  
    -- ssNoVersion unit test for Sales.uspPlaceNewOrder  
    DECLARE @RC AS INT, @CustomerID AS INT, @Amount AS INT, @OrderDate AS DATETIME, @Status AS CHAR (1);  
    DECLARE @CustomerName AS NVARCHAR(40);  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @Amount = 100,  
           @OrderDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- place an order for that customer  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, @Amount, @OrderDate, @Status;  
  
    -- verify that the YTDOrders value is correct.  
    SELECT @RC = [YTDOrders] FROM [Sales].[Customer] WHERE [CustomerID] = @CustomerID  
  
    SELECT @RC AS RC  
    ```  
  
3.  Klicken Sie im Bereich **Testbedingungen** erst auf die Testbedingung „Nicht eindeutig“ und dann auf **Testbedingung löschen**.  
  
4.  Klicken Sie im Bereich **Testbedingungen** in der Liste auf **Skalarwert** , und klicken Sie dann auf **Testbedingung hinzufügen**.  
  
5.  Legen Sie im **Eigenschaftenfenster** die Eigenschaft **Erwarteter Wert** auf „100“ fest.  
  
6.  Klicken Sie auf der Navigationsleiste des SQL Server-Komponententest-Designers auf **Sales_uspPlaceNewOrderTest**, und achten Sie darauf, dass **Vortest** in der nebenstehenden Liste markiert ist.  
  
    Nach diesem Schritt können Sie die Daten mithilfe der erforderlichen Anweisungen für die Ausführung des Tests vorbereiten. Zur Verwendung dieses Beispiels müssen Sie den Datensatz „Customer“ erstellen, bevor Sie eine Bestellung aufgeben können.  
  
7.  Klicken Sie auf **Zum Erstellen hierauf klicken**, um ein Vortestskript zu erstellen.  
  
8.  Aktualisieren Sie die Transact\-SQL-Anweisungen im Transact\-SQL-Editor, damit sie folgenden Anweisungen entsprechen:  
  
    ```  
    /*  
    Add Transact-SQL statements here that you want to run before  
    the test script is run.  
    */  
    -- Add a customer for this test with the name 'Fictitious Customer'  
    DECLARE @NewCustomerID AS INT, @CustomerID AS INT, @RC AS INT, @CustomerName AS NVARCHAR (40);  
  
    SELECT @RC = 0,  
           @NewCustomerID = 0,  
       @CustomerID = 0,  
           @CustomerName = N'Fictitious Customer';  
  
    IF NOT EXISTS(SELECT * FROM [Sales].[Customer] WHERE CustomerName = @CustomerName)  
    BEGIN  
    EXECUTE @NewCustomerID = [Sales].[uspNewCustomer] @CustomerName;  
    END  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- delete any old records in the Orders table and clear out the YTD Sales/Orders fields  
    DELETE from [Sales].[Orders] WHERE [CustomerID] = @CustomerID;  
    UPDATE [Sales].[Customer] SET YTDOrders = 0, YTDSales = 0 WHERE [CustomerID] = @CustomerID;  
    ```  
  
9. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
    Als Nächstes erstellen Sie den Komponententest für uspFillOrder.  
  
#### <a name="to-write-the-sql-server-unit-test-for-uspfillorder"></a>So schreiben Sie den SQL Server-Komponententest für uspFillOrder  
  
1.  Klicken Sie auf der Navigationsleiste des SQL Server-Komponententest-Designers auf **Sales_uspFillOrderTest**, und achten Sie darauf, dass **Test** in der nebenstehenden Liste markiert ist.  
  
    Nachdem Sie diesen Schritt ausgeführt haben, können Sie das Testskript für die Testaktion im Komponententest erstellen.  
  
2.  Aktualisieren Sie die Transact\-SQL-Anweisungen im Transact\-SQL-Editor, damit sie folgenden Anweisungen entsprechen:  
  
    ```  
    -- ssNoVersion unit test for Sales.uspFillOrder  
    DECLARE @RC AS INT, @CustomerID AS INT, @Amount AS INT, @FilledDate AS DATETIME, @Status AS CHAR (1);  
    DECLARE @CustomerName AS NVARCHAR(40), @OrderID AS INT;  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @OrderID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @Amount = 100,  
           @FilledDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
    -- Get the most recently added order.  
    SELECT @OrderID = MAX([OrderID]) FROM [Sales].[Orders] WHERE [CustomerID] = @CustomerID;  
  
    -- fill an order for that customer  
    EXECUTE @RC = [Sales].[uspFillOrder] @OrderID, @FilledDate;  
  
    -- verify that the YTDOrders value is correct.  
    SELECT @RC = [YTDSales] FROM [Sales].[Customer] WHERE [CustomerID] = @CustomerID  
  
    SELECT @RC AS RC;  
    ```  
  
3.  Klicken Sie im Bereich **Testbedingungen** erst auf die Testbedingung „Nicht eindeutig“ und dann auf **Testbedingung löschen**.  
  
4.  Klicken Sie im Bereich **Testbedingungen** in der Liste auf **Skalarwert** , und klicken Sie dann auf **Testbedingung hinzufügen**.  
  
5.  Legen Sie im **Eigenschaftenfenster** die Eigenschaft **Erwarteter Wert** auf „100“ fest.  
  
6.  Klicken Sie auf der Navigationsleiste des SQL Server-Komponententest-Designers auf **Sales_uspFillOrderTest**, und achten Sie darauf, dass **Vortest** in der nebenstehenden Liste markiert ist. Nach diesem Schritt können Sie die Daten mithilfe der erforderlichen Anweisungen für die Ausführung des Tests vorbereiten. Zur Verwendung dieses Beispiels müssen Sie den Datensatz „Customer“ erstellen, bevor Sie eine Bestellung aufgeben können.  
  
7.  Klicken Sie auf **Zum Erstellen hierauf klicken**, um ein Vortestskript zu erstellen.  
  
8.  Aktualisieren Sie die Transact\-SQL-Anweisungen im Transact\-SQL-Editor, damit sie folgenden Anweisungen entsprechen:  
  
    ```  
    /*  
    Add Transact-SQL statements here that you want to run before  
    the test script is run.  
    */  
    BEGIN TRANSACTION  
  
    -- Add a customer for this test with the name 'CustomerB'  
    DECLARE @NewCustomerID AS INT, @RC AS INT, @CustomerName AS NVARCHAR (40);  
  
    SELECT @RC = 0,  
           @NewCustomerID = 0,  
           @CustomerName = N'Fictitious Customer';  
  
    IF NOT EXISTS(SELECT * FROM [Sales].[Customer] WHERE CustomerName = @CustomerName)  
    BEGIN  
    EXECUTE @NewCustomerID = [Sales].[uspNewCustomer] @CustomerName;  
    END  
  
    DECLARE @CustomerID AS INT, @Amount AS INT, @OrderDate AS DATETIME, @Status AS CHAR (1);  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @Amount = 100,  
           @OrderDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- delete any old records in the Orders table and clear out the YTD Sales/Orders fields  
    DELETE from [Sales].[Orders] WHERE [CustomerID] = @CustomerID;  
    UPDATE [Sales].[Customer] SET YTDOrders = 0, YTDSales = 0 WHERE [CustomerID] = @CustomerID;  
  
    -- place an order for that customer  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, @Amount, @OrderDate, @Status;  
  
    COMMIT TRANSACTION  
    ```  
  
9. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
#### <a name="to-write-the-sql-server-unit-test-for-uspshoworderdetails"></a>So schreiben Sie den SQL Server-Komponententest für uspShowOrderDetails  
  
1.  Klicken Sie auf der Navigationsleiste des SQL Server-Komponententest-Designers auf **Sales_uspShowOrderDetailsTest**, und achten Sie darauf, dass **Test** in der nebenstehenden Liste markiert ist.  
  
    Nachdem Sie diesen Schritt ausgeführt haben, können Sie das Testskript für die Testaktion im Komponententest erstellen.  
  
2.  Aktualisieren Sie die Transact\-SQL-Anweisungen im Transact\-SQL-Editor, damit sie folgenden Anweisungen entsprechen:  
  
    ```  
    -- ssNoVersion unit test for Sales.uspFillOrder  
    DECLARE @RC AS INT, @CustomerID AS INT, @Amount AS INT, @FilledDate AS DATETIME, @Status AS CHAR (1);  
    DECLARE @CustomerName AS NVARCHAR(40), @OrderID AS INT;  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @OrderID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @Amount = 100,  
           @FilledDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- fill an order for that customer  
    EXECUTE @RC = [Sales].[uspShowOrderDetails] @CustomerID;  
  
    SELECT @RC AS RC;  
    ```  
  
3.  Klicken Sie im Bereich **Testbedingungen** erst auf die Testbedingung „Nicht eindeutig“ und dann auf **Testbedingung löschen**.  
  
4.  Klicken Sie im Bereich **Testbedingungen** in der Liste auf **Erwartetes Schema** , und klicken Sie dann auf **Testbedingung hinzufügen**.  
  
5.  Klicken Sie im Fenster **Eigenschaften** in der Eigenschaft **Konfiguration** auf die Schaltfläche zum Durchsuchen („**…**“).  
  
6.  Geben Sie im Dialogfeld **Konfiguration für expectedSchemaCondition1** eine Verbindung mit der Datenbank an. Wenn Sie beispielsweise den Standardbereitstellungsspeicherort, d.h. LocalDB, verwendet haben, würden Sie auf **Neue Verbindung** klicken und **(LocalDB)\Projects** angeben. Wählen Sie anschließend den Namen der Datenbank aus.  
  
7.  Klicken Sie auf **Abrufen**. (Falls erforderlich, klicken Sie auf **Abrufen**, bis Daten angezeigt werden.)  
  
    Der Transact\-SQL-Text des Komponententests wird ausgeführt, und das resultierende Schema wird im Dialogfeld angezeigt. Da kein Code für den Vortest ausgeführt wurde, werden keine Daten zurückgegeben. Dies ist in Ordnung, da Sie lediglich das Schema und nicht die Daten überprüfen.  
  
8.  Klicken Sie auf **OK**.  
  
    Das erwartete Schema wird mit der Testbedingung gespeichert.  
  
9. Klicken Sie auf der Navigationsleiste des SQL Server-Komponententest-Designers auf **Sales_uspShowOrderDetailsTest**, und achten Sie darauf, dass **Vortest** in der nebenstehenden Liste markiert ist. Nach diesem Schritt können Sie die Daten mithilfe der erforderlichen Anweisungen für die Ausführung des Tests vorbereiten. Zur Verwendung dieses Beispiels müssen Sie den Datensatz „Customer“ erstellen, bevor Sie eine Bestellung aufgeben können.  
  
10. Klicken Sie auf **Zum Erstellen hierauf klicken**, um ein Vortestskript zu erstellen.  
  
11. Aktualisieren Sie die Transact\-SQL-Anweisungen im Transact\-SQL-Editor, damit sie folgenden Anweisungen entsprechen:  
  
    ```  
    /*  
    Add Transact-SQL statements here to run before the test script is run.  
    */  
    BEGIN TRANSACTION  
  
    -- Add a customer for this test with the name 'FictitiousCustomer'  
    DECLARE @NewCustomerID AS INT, @RC AS INT, @CustomerName AS NVARCHAR (40);  
  
    SELECT @RC = 0,  
           @NewCustomerID = 0,  
           @CustomerName = N'Fictitious Customer';  
  
    IF NOT EXISTS(SELECT * FROM [Sales].[Customer] WHERE CustomerName = @CustomerName)  
    BEGIN  
    EXECUTE @NewCustomerID = [Sales].[uspNewCustomer] @CustomerName;  
    END  
  
    DECLARE @CustomerID AS INT, @Amount AS INT, @OrderDate AS DATETIME, @Status AS CHAR (1);  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @OrderDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- delete any old records in the Orders table and clear out the YTD Sales/Orders fields  
    DELETE from [Sales].[Orders] WHERE [CustomerID] = @CustomerID;  
    UPDATE [Sales].[Customer] SET YTDOrders = 0, YTDSales = 0 WHERE [CustomerID] = @CustomerID;  
  
    -- place 3 orders for that customer  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, 100, @OrderDate, @Status;  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, 50, @OrderDate, @Status;  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, 5, @OrderDate, @Status;  
  
    COMMIT TRANSACTION  
    ```  
  
12. Klicken Sie auf der Navigationsleiste des SQL Server-Komponententest-Designers auf **Sales_uspShowOrderDetailsTest**, und klicken Sie in der nebenstehenden Liste auf **Test**.  
  
    Dieser Schritt ist erforderlich, weil Sie die Prüfsummenbedingung auf den Test und nicht auf den Vortest anwenden möchten.  
  
13. Klicken Sie im Bereich **Testbedingungen** in der Liste auf **Datenprüfsumme** , und klicken Sie dann auf **Testbedingung hinzufügen**.  
  
14. Klicken Sie im Fenster **Eigenschaften** in der Eigenschaft **Konfiguration** auf die Schaltfläche zum Durchsuchen („**…**“).  
  
15. Geben Sie im Dialogfeld **Konfiguration für checksumCondition1** eine Verbindung mit der Datenbank an.  
  
16. Ersetzen Sie Transact\-SQL im Dialogfeld (unterhalb der Schaltfläche **Verbindung bearbeiten**) durch folgenden Code:  
  
    ```  
    BEGIN TRANSACTION  
  
    -- Add a customer for this test with the name 'CustomerB'  
    DECLARE @NewCustomerID AS INT, @RC AS INT, @CustomerName AS NVARCHAR (40);  
  
    SELECT @RC = 0,  
           @NewCustomerID = 0,  
           @CustomerName = N'Fictitious Customer';  
  
    IF NOT EXISTS(SELECT * FROM [Sales].[Customer] WHERE CustomerName = @CustomerName)  
    BEGIN  
    EXECUTE @NewCustomerID = [Sales].[uspNewCustomer] @CustomerName;  
    END  
  
    DECLARE @CustomerID AS INT, @Amount AS INT, @OrderDate AS DATETIME, @Status AS CHAR (1);  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @OrderDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- delete any old records in the Orders table and clear out the YTD Sales/Orders fields  
    DELETE from [Sales].[Orders] WHERE [CustomerID] = @CustomerID;  
    UPDATE [Sales].[Customer] SET YTDOrders = 0, YTDSales = 0 WHERE [CustomerID] = @CustomerID;  
  
    -- place 3 orders for that customer  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, 100, @OrderDate, @Status;  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, 50, @OrderDate, @Status;  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, 5, @OrderDate, @Status;  
  
    COMMIT TRANSACTION  
  
    -- ssNoVersion unit test for Sales.uspFillOrder  
    DECLARE @FilledDate AS DATETIME;  
    DECLARE @OrderID AS INT;  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @OrderID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @Amount = 100,  
           @FilledDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- fill an order for that customer  
    EXECUTE @RC = [Sales].[uspShowOrderDetails] @CustomerID;  
  
    SELECT @RC AS RC;  
    ```  
  
    In diesem Code wird der Transact\-SQL-Code aus dem Vortest mit dem Transact\-SQL-Code aus dem Haupttest kombiniert. Sie benötigen beide, wenn dieselben Ergebnisse wie beim Ausführen des Tests zurückgegeben werden sollen.  
  
17. Klicken Sie auf **Abrufen**. (Falls erforderlich, klicken Sie auf **Abrufen**, bis Daten angezeigt werden.)  
  
    Der angegebene Transact\-SQL-Code wird ausgeführt, und für die zurückgegebenen Daten wird eine Prüfsumme berechnet.  
  
18. Klicken Sie auf **OK**.  
  
    Die berechnete Prüfsumme wird mit der Testbedingung gespeichert. Die erwartete Prüfsumme wird in der Spalte „Wert“ der Testbedingung „Datenprüfsumme“ angezeigt.  
  
19. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
    Nun können Sie die Tests ausführen.  
  
## <a name="RunTests"></a>Ausführen von SQL Server-Komponententests  
  
#### <a name="to-run-the-sql-server-unit-tests"></a>So führen Sie SQL Server-Komponententests aus  
  
1.  Zeigen Sie im Menü **Test** auf **Fenster**, und klicken Sie dann in Visual Studio 2010 auf **Testansicht** oder in Visual Studio 2012 auf **Test-Explorer**.  
  
2.  Klicken Sie im Fenster **Testansicht** (Visual Studio 2010) auf der Symbolleiste auf **Aktualisieren**, um die Liste der Tests zu aktualisieren. Um die Liste der Tests im **Test-Explorer** (Visual Studio 2012) anzuzeigen, erstellen Sie die Projektmappe.  
  
    Im Fenster **Testansicht** oder **Test-Explorer** werden die Tests aufgelistet, die Sie zuvor in dieser exemplarischen Vorgehensweise erstellt und denen Sie Transact\-SQL-Anweisungen und Testbedingungen hinzugefügt haben. Der Test mit dem Namen "TestMethod1" ist leer und wird in dieser exemplarischen Vorgehensweise nicht verwendet.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Sales_uspNewCustomerTest**, und klicken Sie auf **Auswahl ausführen**.  
  
    Visual Studio verwendet den angegebenen privilegierten Kontext, den Sie beim Herstellen einer Verbindung mit der Datenbank und beim Anwenden des Datengenerierungsplans angegeben haben. Visual Studio wechselt dann zum Ausführungskontext, bevor das Transact\-SQL-Skript im Test ausgeführt wird. Zum Schluss werden die Ergebnisse des Transact\-SQL-Skripts in Visual Studio anhand der in der Testbedingung angegebenen Ergebnisse ausgewertet und im Fenster **Testergebnisse** eine erfolgreiche oder fehlerhafte Testausführung gemeldet.  
  
4.  Überprüfen Sie das Ergebnis im Fenster **Testergebnisse** .  
  
    Der Test verläuft erfolgreich, da bei der Ausführung der **SELECT** -Anweisung eine Zeile zurückgegeben wird.  
  
5.  Wiederholen Sie Schritt 3 für die Tests „Sales_uspPlaceNewOrderTest“, „Sales_uspFillOrderTest“ und „Sales_uspShowOrderDetailsTest“. Die Ergebnisse sollten wie folgt lauten:  
  
    |Test|Erwartete Ergebnisse|  
    |--------|-------------------|  
    |Sales_uspPlaceNewOrderTest|Erfolgreich|  
    |Sales_uspShowOrderDetailsTest|Erfolgreich|  
    |Sales_uspFillOrderTest|Verursacht folgenden Fehler: "ScalarValueCondition-Bedingung (scalarValueCondition2) Fehler: ResultSet 1 Zeile 1 Spalte 1: Werte stimmen nicht überein, tatsächlich '-100' erwartet '100'." Dieser Fehler tritt auf, weil die Definition der gespeicherten Prozedur einen geringfügigen Fehler enthält.|  
  
    Im nächsten Schritt berichtigen Sie den Fehler und führen den Text erneut aus.  
  
#### <a name="to-correct-the-error-in-salesuspfillorder"></a>So berichtigen Sie den Fehler in "Sales.uspFillOrder"  
  
1.  Doppelklicken Sie im **SQL Server-Objekt-Explorer** unter dem Knoten „Projekte“ der Datenbank auf die gespeicherte Prozedur **uspFillOrder**, um deren Definition im Transact\-SQL-Editor zu öffnen.  
  
2.  Suchen Sie in der Definition folgende Transact\-SQL-Anweisung:  
  
    ```  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales - @Delta  
        WHERE [CustomerID] = @CustomerID  
    ```  
  
3.  Ändern Sie die SET-Klausel in der Anweisung in folgende Anweisung:  
  
    ```  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    ```  
  
4.  Klicken Sie im Menü **Datei** auf **uspFillOrder.sql speichern**.  
  
5.  Klicken Sie in der **Testansicht** mit der rechten Maustaste auf **Sales_uspFillOrderTest**, und klicken Sie auf **Auswahl ausführen**.  
  
    Der Test verläuft erfolgreich.  
  
## <a name="NegativeTest"></a>Hinzufügen eines negativen Komponententests  
Sie können einen negativen Komponententest erstellen, um zu überprüfen, ob ein Test fehlschlägt, wenn er fehlschlagen sollte. Beispiel: Wenn Sie versuchen, eine bereits ausgeführte Bestellung zu stornieren, sollte dieser Test fehlschlagen. In diesem Teil der exemplarischen Vorgehensweise erstellen Sie einen negativen Komponententest für die gespeicherte Prozedur „Sales.uspCancelOrder“.  
  
Zum Erstellen und Überprüfen eines negativen Tests führen Sie folgende Aufgaben aus:  
  
-   Aktualisieren der gespeicherten Prozedur, um auf Fehlerbedingungen zu testen  
  
-   Definieren eines neuen Komponententests  
  
-   Ändern des Codes für den Komponententest, um anzugeben, dass der Test fehlschlagen soll  
  
-   Ausführen des Komponententests  
  
#### <a name="to-update-the-stored-procedure"></a>So aktualisieren Sie die gespeicherte Prozedur  
  
1.  Erweitern Sie im **SQL Server-Objekt-Explorer** unter dem Knoten „Projekte“ der Datenbank „SimpleUnitTestDB“ erst den Knoten „Programmierbarkeit“ und dann den Knoten „Gespeicherte Prozeduren“, und doppelklicken Sie auf „uspCancelOrder“.  
  
2.  Aktualisieren Sie im Transact\-SQL-Editor die Prozedurdefinition entsprechend folgendem Code:  
  
    ```  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
        DECLARE @Delta INT, @CustomerID INT, @PriorStatus CHAR(1)  
        BEGIN TRANSACTION  
            BEGIN TRY  
                IF (NOT EXISTS(SELECT [CustomerID] from [Sales].[Orders] WHERE [OrderID] = @OrderID))  
                BEGIN  
                    -- Specify WITH LOG option so that the error is  
                    -- written to the application log.  
                    RAISERROR( 'That order does not exist.', -- Message text  
                               16, -- severity  
                                1 -- state  
                            ) WITH LOG;  
                END  
  
                SELECT @Delta = [Amount], @CustomerID = [CustomerID], @PriorStatus = [Status]  
                 FROM [Sales].[Orders] WHERE [OrderID] = @OrderID  
  
                IF @PriorStatus <> 'O'   
                BEGIN  
                    -- Specify WITH LOG option so that the error is  
                    -- written to the application log.  
                    RAISERROR ( 'You can only cancel open orders.', -- Message text  
                                16, -- Severity  
                                1 -- State  
                                ) WITH LOG;  
                END  
                ELSE  
                BEGIN  
                    -- If we make it to here, then we can cancel the order. Update the status to 'X' first...  
                    UPDATE [Sales].[Orders]  
                       SET [Status] = 'X'  
                    WHERE [OrderID] = @OrderID  
                    -- and then remove the amount from the YTDOrders for the customer  
                    UPDATE [Sales].[Customer]  
                           SET  
                               YTDOrders = YTDOrders - @Delta  
                    WHERE [CustomerID] = @CustomerID  
                    COMMIT TRANSACTION  
                    RETURN 1; -- indicate success  
                END  
            END TRY  
            BEGIN CATCH  
                DECLARE @ErrorMessage NVARCHAR(4000);  
                DECLARE @ErrorSeverity INT;  
                DECLARE @ErrorState INT;  
  
                SELECT @ErrorMessage = ERROR_MESSAGE(),  
                       @ErrorSeverity = ERROR_SEVERITY(),  
                       @ErrorState = ERROR_STATE();  
  
                ROLLBACK TRANSACTION  
                -- Use RAISERROR inside the CATCH block to return  
                -- error information about the original error that  
                -- caused execution to jump to the CATCH block.  
                RAISERROR (@ErrorMessage, -- Mesasge text  
                           @ErrorSeverity, -- Severity  
                           @ErrorState -- State  
                          );  
                RETURN 0; -- indicate failure  
            END CATCH;  
    END  
    ```  
  
3.  Klicken Sie im Menü **Datei** auf **uspCancelOrder.sql speichern**.  
  
4.  Drücken Sie F5, um **SimpleUnitTestDB**bereitzustellen.  
  
    Sie stellen die Updates für die gespeicherte Prozedur uspCancelOrder bereit. Da Sie keine anderen Objekte geändert haben, wird nur diese gespeicherte Prozedur aktualisiert.  
  
    Als Nächstes definieren Sie den Komponententest für diese Prozedur.  
  
#### <a name="to-write-the-sql-server-unit-test-for-uspcancelorder"></a>So schreiben Sie den SQL Server-Komponententest für uspCancelOrder  
  
1.  Klicken Sie auf der Navigationsleiste des SQL Server-Komponententest-Designers auf **Sales_uspCancelOrderTest**, und achten Sie darauf, dass **Test** in der nebenstehenden Liste markiert ist.  
  
    Nachdem Sie diesen Schritt ausgeführt haben, können Sie das Testskript für die Testaktion im Komponententest erstellen.  
  
2.  Aktualisieren Sie die Transact\-SQL-Anweisungen im Transact\-SQL-Editor, damit sie folgenden Anweisungen entsprechen:  
  
    ```  
    -- ssNoVersion unit test for Sales.uspFillOrder  
    DECLARE @RC AS INT, @CustomerID AS INT, @Amount AS INT, @FilledDate AS DATETIME, @Status AS CHAR (1);  
    DECLARE @CustomerName AS NVARCHAR(40), @OrderID AS INT;  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @OrderID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @Amount = 100,  
           @FilledDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
    -- Get the most recently added order.  
    SELECT @OrderID = MAX([OrderID]) FROM [Sales].[Orders] WHERE [CustomerID] = @CustomerID;  
  
    -- try to cancel an order for that customer that has already been filled  
    EXECUTE @RC = [Sales].[uspCancelOrder] @OrderID;  
  
    SELECT @RC AS RC;  
    ```  
  
3.  Klicken Sie im Bereich **Testbedingungen** erst auf die Testbedingung „Nicht eindeutig“ und dann auf das Symbol **Testbedingung löschen** .  
  
4.  Klicken Sie im Bereich **Testbedingungen** in der Liste auf **Skalarwert** , und klicken Sie dann auf das Symbol **Testbedingung hinzufügen** .  
  
5.  Legen Sie im Eigenschaftenfenster die Eigenschaft **Erwarteter Wert** auf **0** fest.  
  
6.  Klicken Sie auf der Navigationsleiste des SQL Server-Komponententest-Designers auf **Sales_uspCancelOrderTest**, und achten Sie darauf, dass **Vortest** in der nebenstehenden Liste markiert ist. Nach diesem Schritt können Sie die Daten mithilfe der erforderlichen Anweisungen für die Ausführung des Tests vorbereiten. Zur Verwendung dieses Beispiels müssen Sie den Datensatz „Customer“ erstellen, bevor Sie eine Bestellung aufgeben können.  
  
7.  Klicken Sie auf **Zum Erstellen hierauf klicken**, um ein Vortestskript zu erstellen.  
  
8.  Aktualisieren Sie die Transact\-SQL-Anweisungen im Transact\-SQL-Editor, damit sie folgenden Anweisungen entsprechen:  
  
    ```  
    /*  
    Add Transact-SQL statements here to run before the test script is run.  
    */  
    BEGIN TRANSACTION  
  
    -- Add a customer for this test with the name 'CustomerB'  
    DECLARE @NewCustomerID AS INT, @RC AS INT, @CustomerName AS NVARCHAR (40);  
  
    SELECT @RC = 0,  
           @NewCustomerID = 0,  
           @CustomerName = N'Fictitious Customer';  
  
    IF NOT EXISTS(SELECT * FROM [Sales].[Customer] WHERE CustomerName = @CustomerName)  
    BEGIN  
    EXECUTE @NewCustomerID = [Sales].[uspNewCustomer] @CustomerName;  
    END  
  
    DECLARE @CustomerID AS INT, @Amount AS INT, @OrderDate AS DATETIME, @FilledDate AS DATETIME, @Status AS CHAR (1), @OrderID AS INT;  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
       @OrderID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @Amount = 100,  
           @OrderDate = getdate(),  
       @FilledDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- delete any old records in the Orders table and clear out the YTD Sales/Orders fields  
    DELETE from [Sales].[Orders] WHERE [CustomerID] = @CustomerID;  
    UPDATE [Sales].[Customer] SET YTDOrders = 0, YTDSales = 0 WHERE [CustomerID] = @CustomerID;  
  
    -- place an order for that customer  
    EXECUTE @OrderID = [Sales].[uspPlaceNewOrder] @CustomerID, @Amount, @OrderDate, @Status;  
  
    -- fill the order for that customer  
    EXECUTE @RC = [Sales].[uspFillOrder] @OrderID, @FilledDate;  
  
    COMMIT TRANSACTION  
    ```  
  
9. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
    Nun können Sie die Tests ausführen.  
  
#### <a name="to-run-the-sql-server-unit-tests"></a>So führen Sie SQL Server-Komponententests aus  
  
1.  Klicken Sie in der **Testansicht** mit der rechten Maustaste auf **Sales_uspCancelOrderTest**, und klicken Sie auf **Auswahl ausführen**.  
  
2.  Überprüfen Sie das Ergebnis im Fenster **Testergebnisse** .  
  
    Der Test schlägt mit folgender Fehlermeldung fehl:  
  
    **Die Testmethode „TestProject1.SqlServerUnitTests1.Sales_uspCancelOrderTest“ hat eine Ausnahme ausgelöst: System.Data.SqlClient.SqlException: Sie können nur offene Aufträge abbrechen.**  
  
    Im nächsten Schritt ändern Sie den Code, um anzugeben, dass die Ausnahme erwartet wird.  
  
#### <a name="to-modify-the-code-for-the-unit-test"></a>So ändern Sie den Code für den Komponententest  
  
1.  Erweitern Sie im **Projektmappen-Explorer** die Option **TestProject1**, klicken Sie mit der rechten Maustaste auf **SqlServerUnitTests1.cs**, und klicken Sie auf **Code anzeigen**.  
  
2.  Navigieren Sie im Code-Editor zur Sales_uspCancelOrderTest-Methode. Ändern Sie die Attribute der Methode entsprechend folgendem Code:  
  
    ```  
    [TestMethod(), ExpectedSqlException(Severity=16, MatchFirstError=false, State=1)]  
    public void Sales_uspCancelOrderTest()  
    ```  
  
    Sie geben an, dass Sie eine bestimmte Ausnahme erwarten. Optional können Sie eine bestimmte Fehlernummer angeben. Wenn Sie dieses Attribut nicht hinzufügen, schlägt der Komponententest fehl, und im Fenster "Testergebnisse" wird eine Meldung angezeigt.  
  
    > [!IMPORTANT]  
    > Derzeit wird das ExpectedSqlException-Attribut in Visual Studio 2012 nicht unterstützt. Wie Sie dieses Problem umgehen können, erfahren Sie unter [Datenbankkomponententest "Erwarteter Fehler" kann nicht ausgeführt werden](https://social.msdn.microsoft.com/Forums/en-US/ssdt/thread/e74e06ad-e3c9-4cb0-97ad-a6f235a52345)(möglicherweise nur in englischer Sprache).  
  
3.  Klicken Sie im Menü „Datei“ auf „SqlServerUnitTests1.cs“ speichern.  
  
    Als Nächstes führen Sie den Komponententest erneut aus, um sicherzustellen, dass er wie erwartet fehlschlägt.  
  
#### <a name="to-re-run-the-sql-server-unit-tests"></a>So führen Sie erneut SQL Server-Komponententests aus  
  
1.  Klicken Sie in der **Testansicht** mit der rechten Maustaste auf **Sales_uspCancelOrderTest**, und klicken Sie auf **Auswahl ausführen**.  
  
2.  Überprüfen Sie das Ergebnis im Fenster **Testergebnisse** .  
  
    Der Test verläuft erfolgreich. Dies bedeutet, dass die Prozedur, von der angenommen wurde, dass sie fehlschlägt, tatsächlich einen Fehler verursacht hat.  
  
## <a name="next-steps"></a>Next Steps  
In einem typischen Projekt würden Sie zusätzliche Komponententests definieren, um alle wichtigen Datenbankobjekte auf ihre ordnungsgemäße Funktionsweise zu überprüfen. Nach Abschluss der Tests checken Sie diese in die Versionskontrolle ein, um sie dem Team zur Verfügung zu stellen.  
  
Nachdem Sie eine Basis geschaffen haben, können Sie Datenbankobjekte erstellen, anpassen und anschließend geeignete Tests erstellen, um festzustellen, ob sich eine Änderung auf das erwartete Verhalten auswirken würde.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Erstellen und Definieren von SQL Server-Komponententests](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[Überprüfen des Datenbankcodes mithilfe von SQL Server-Komponententests](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
[Gewusst wie: Erstellen eines leeren SQL Server-Komponententests](../ssdt/how-to-create-an-empty-sql-server-unit-test.md)  
[Gewusst wie: Konfigurieren der Ausführung von SQL Server-Komponententests](../ssdt/how-to-configure-sql-server-unit-test-execution.md)  
  
