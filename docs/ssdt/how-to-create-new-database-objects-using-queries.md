---
title: Erstellen von neuen Datenbankobjekten mithilfe von Abfragen
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: ac983ac7-f9c4-495d-8a99-e1ba370fb271
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 38a7165eb1145c6da08902d06a8483b0e26abf5b
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75241492"
---
# <a name="how-to-create-new-database-objects-using-queries"></a>Gewusst wie: Erstellen von neuen Datenbankobjekten mit Abfragen

Falls Sie es vorziehen, Sichten, gespeicherte Prozeduren, Funktionen, Trigger oder benutzerdefinierte Typen mithilfe von Skripts zu erstellen oder zu bearbeiten, können Sie den Transact\-SQL-Editor verwenden. Der Transact\-SQL-Editor bietet Unterstützung für IntelliSense und andere Sprachen. Weitere Informationen finden Sie unter [Verwenden des Transact-SQL-Editors zum Bearbeiten und Ausführen von Skripts](../ssdt/use-transact-sql-editor-to-edit-and-execute-scripts.md).  
  
Der Transact\-SQL-Editor wird aufgerufen, wenn Sie eine Datenbankentität in einer verbundenen Datenbank oder einem Projekt über das Kontextmenü **Code anzeigen** öffnen. Er wird auch automatisch geöffnet, wenn Sie das Kontextmenü **Neue Abfrage** im SQL Server-Objekt-Explorer aufrufen und wenn Sie einem Datenbankprojekt ein neues Skriptobjekt hinzufügen. Wenn Sie mit keiner Datenbank verbunden sind, aber eine Abfrage für eine Datenbank ausführen möchten, können Sie auch das Dialogfeld **Neue Abfrageverbindung** verwenden, indem Sie im Menü **SQL** das Menü **Transact-SQL-Editor** auswählen, um eine Verbindung mit einer Datenbank herzustellen und den Transact\-SQL-Editor zu starten.  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden die Entitäten verwendet, die in vorherigen Vorgehensweisen im Abschnitt [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) erstellt wurden.  
  
### <a name="to-create-a-new-table-using-a-transact-sql-query"></a>So erstellen Sie mithilfe einer Transact\-SQL-Abfrage eine neue Tabelle  
  
1.  Klicken Sie mit der rechten Maustaste auf den Datenbankknoten **Trade**, und wählen Sie **Neue Abfrage** aus.  
  
2.  Fügen Sie im Skriptbereich folgenden Code ein:  
  
    ```  
  
    CREATE TABLE [dbo].[Fruits] (  
        [Id]         INT NOT NULL,  
        [Perishable] BIT DEFAULT ((1)) NULL,  
        PRIMARY KEY CLUSTERED ([Id] ASC),  
        FOREIGN KEY ([Id]) REFERENCES [dbo].[Products] ([Id])   
    );  
    ```  
  
3.  Klicken Sie auf der Transact\-SQL-Editor-Symbolleiste auf die Schaltfläche **Abfrage ausführen**, um diese Abfrage auszuführen.  
  
4.  Klicken Sie mit der rechten Maustaste auf die Datenbank **Trade** im **SQL Server-Objekt-Explorer**, und klicken Sie auf **Aktualisieren**. Beachten Sie, dass der Datenbank die neue Tabelle **Fruits** hinzugefügt wurde.  
  
### <a name="to-create-a-new-function"></a>So erstellen Sie eine neue Funktion  
  
1.  Ersetzen Sie den Code im aktuellen Transact\-SQL-Editor durch den folgenden Code:  
  
    ```  
  
    CREATE FUNCTION [dbo].GetProductsBySupplier  
    (  
    @SupplierId int  
    )  
    RETURNS @returntable TABLE   
    (  
    [Id] int NOT NULL,   
    [Name] NVARCHAR (128) NOT NULL,  
    [Shelflife] INT NOT NULL,  
    [SupplierId] INT NOT NULL,  
    [CustomerId] INT NOT NULL  
    )  
    AS  
    BEGIN  
    INSERT @returntable  
    SELECT *  from Products p  
    where p.SupplierId = @SupplierId  
    RETURN   
    END  
    ```  
  
    Diese Funktion gibt alle Zeilen in der Tabelle `Products` zurück, deren `SupplierId` gleich dem angegebenen Parameter ist. Klicken Sie auf der Transact\-SQL-Editor-Symbolleiste auf die Schaltfläche **Abfrage ausführen**, um diese Abfrage auszuführen.  
  
2.  Erweitern Sie im SQL Server-Objekt-Explorer unter dem Knoten **Trade** die Knoten **Programmierung** und **Funktionen**. Sie finden die neue Funktion, die Sie soeben erstellt haben, unter **Tabellenwertfunktionen**.  
  
### <a name="to-create-a-new-view"></a>So erstellen Sie eine neue Sicht  
  
1.  Ersetzen Sie den Code im aktuellen Transact\-SQL-Editor durch den folgenden Code: Klicken Sie anschließend über dem Editor auf die Schaltfläche **Abfrage ausführen**, um diese Abfrage auszuführen.  
  
    ```  
    CREATE VIEW [dbo].PerishableFruits   
    AS SELECT p.Id, p.Name FROM dbo.Products p  
    join dbo.Fruits f on f.Id = p.Id  
    where f.Perishable = 1  
    ```  
  
2.  Erweitern Sie im SQL Server-Objekt-Explorer unter dem Knoten **Trade** den Knoten **Sicht**, um die soeben erstellte neue Sicht zu suchen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Verwalten von Tabellen, Beziehungen und Beheben von Fehlern](../ssdt/manage-tables-relationships-and-fix-errors.md)  
[Verwenden des Transact-SQL-Editors zum Bearbeiten und Ausführen von Skripts](../ssdt/use-transact-sql-editor-to-edit-and-execute-scripts.md)  
  
