---
title: 'Gewusst wie: Verwenden von Microsoft SQL Server 2012-Objekten in einem Projekt | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 9baf122f-cf22-4860-98db-ef782cd972fc
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e3175f523a0cc6b91fd1d5bd955e6872a5cf0064
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65098406"
---
# <a name="how-to-use-microsoft-sql-server-2012-objects-in-your-project"></a>Gewusst wie: Verwenden von Microsoft SQL Server 2012-Objekten im Projekt
In diesem Beispiel fügen Sie einem Datenbankprojekt, das auf Microsoft SQL Server 2012 zeigt, ein Sequenzobjekt hinzu.  
  
In Microsoft SQL Server 2012 werden Sequenzen eingeführt. Als Sequenz wird ein benutzerdefiniertes schemagebundenes Objekt bezeichnet, das eine Sequenz numerischer Werte anhand der Spezifikation generiert, mit der die Sequenz erstellt wurde. Die Sequenz von numerischen Werten wird in aufsteigender oder absteigender Reihenfolge in einem definierten Intervall generiert, und je nach Anforderung wird ein Zyklus (Wiederholungen) ausgeführt.  Weitere Informationen zu Sequenzobjekten finden Sie unter [Sequenznummern](htttp://msdn.microsoft.com/library/ff878058(SQL.110).aspx). Informationen zu Neuerungen in Microsoft SQL Server 2012 finden Sie unter [What's New in SQL Server 2012 (Neuigkeiten zu SQL Server 2012)](https://msdn.microsoft.com/library/bb500435(SQL.110).aspx).  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden Entitäten verwendet, die in vorherigen Vorgehensweisen in den Abschnitten [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) und [Projektorientierte Entwicklung von Offlinedatenbanken](../ssdt/project-oriented-offline-database-development.md) erstellt wurden.  
  
### <a name="to-add-a-new-sequence-object-to-your-project"></a>So fügen Sie einem Projekt ein neues Sequenzobjekt hinzu  
  
1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Datenbankprojekt **TradeDev**, wählen Sie **Hinzufügen** aus, und klicken Sie auf **Neues Element**.  
  
2.  Klicken Sie im linken Bereich auf **Programmierung**, und wählen Sie **Sequenz** aus. Klicken Sie auf **Hinzufügen**, um dem Projekt das neue Objekt hinzuzufügen.  
  
3.  Ersetzen Sie den Standardcode durch folgenden Code.  
  
    ```  
    CREATE SEQUENCE [dbo].[Seq1]  
    AS INT  
    START WITH 1  
    INCREMENT BY 1  
    MAXVALUE 1000  
    NO CYCLE  
    CACHE 10  
    ```  
  
4.  Wenn die Zielplattform des Projekts nicht auf Microsoft SQL Server 2012 festgelegt ist, wird in der **Fehlerliste** ein Syntaxfehler für die `CREATE SEQUENCE`-Anweisung angezeigt. Wenn Sie diesen Fehler beheben möchten, führen Sie die unter [Vorgehensweise: Ändern der Zielplattform und Veröffentlichen eines Datenbankprojekts](../ssdt/how-to-change-target-platform-and-publish-a-database-project.md) beschriebenen Schritte aus, um die Zielplattform entsprechend zu ändern.  
  
5.  Führen Sie die unter [Vorgehensweise: Ändern der Zielplattform und Veröffentlichen eines Datenbankprojekts](../ssdt/how-to-change-target-platform-and-publish-a-database-project.md) beschriebenen Schritte aus, um das Projekt in einer Datenbank in Ihrer verbundenen Microsoft SQL Server 2012-Instanz zu veröffentlichen.  
  
### <a name="to-use-the-new-sequence-object"></a>So verwenden Sie das neue Sequenzobjekt  
  
1.  Klicken Sie im SQL Server-Objekt-Explorer mit der rechten Maustaste auf die Datenbank, in der Sie das Projekt in der vorherigen Prozedur veröffentlicht haben, und wählen Sie die Option **Neue Abfrage** aus.  
  
2.  Fügen Sie im Abfragefenster den folgenden Code ein:  
  
    ```  
    DECLARE @counter INT  
    SET @counter=0  
    WHILE @counter<10  
    BEGIN  
        SET @counter = @counter +1  
         INSERT dbo.Products (Id, Name, CustomerId) VALUES (NEXT VALUE FOR dbo.Seq1, 'ProductItem'+cast(@counter as varchar), 1)  
    END   
    GO  
    ```  
  
3.  Klicken Sie auf die Schaltfläche **Abfrage ausführen**.  
  
4.  Navigieren Sie im **SQL Server-Objekt-Explorer** zur Tabelle **Products** in der Datenbank. Klicken Sie mit der rechten Maustaste, und wählen Sie **Daten anzeigen** aus, um die neu hinzugefügten Zeilen zu untersuchen.  
  
