---
title: Bearbeiten einer vorhandenen Tabelle mithilfe von Abfragen
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: 58f4de8e-97b4-4bcb-953f-f3d428432491
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 56411bfffbaebeb07adf23b456a20523342db21d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75241406"
---
# <a name="how-to-edit-an-existing-table-using-queries"></a>Vorgehensweise: Bearbeiten einer vorhandenen Tabelle mit Abfragen

Sie können die Definition einer Tabelle oder ihre Daten bearbeiten, indem Sie eine Transact\-SQL-Abfrage schreiben. Verwenden Sie zum Anzeigen oder visuellen Eingeben von Daten in einer Tabelle den Daten-Editor, wie unter [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) beschrieben wird.  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden die Entitäten verwendet, die in vorherigen Vorgehensweisen im Abschnitt [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) erstellt wurden.  
  
### <a name="to-edit-the-definition-of-an-existing-table"></a>So bearbeiten Sie die Definition einer vorhandenen Tabelle  
  
1.  Erweitern Sie im **SQL Server-Objekt-Explorer** den Knoten **Tabellen** der Datenbank **Trade**, und klicken Sie mit der rechten Maustaste auf **dbo.Suppliers**.  
  
2.  Wählen Sie **Sicht-Designer** aus, um das Tabellenschema im Tabellen-Designer anzuzeigen.  
  
3.  Überprüfen Sie das Feld **NULL-Werte zulassen** für die Spalte **Address**. Beachten Sie, dass der entsprechende Code im Skriptbereich sofort in `NULL` geändert wird.  
  
4.  Aktualisieren Sie die Datenbank gemäß den Schritten im Thema [Gewusst wie: Aktualisieren einer verbundenen Datenbank mit Power Buffer](../ssdt/how-to-update-a-connected-database-with-power-buffer.md) an.  
  
### <a name="to-populate-data-in-new-tables-using-a-transact-sql-query"></a>So füllen Sie mit einer Transact\-SQL-Abfrage neue Tabellen mit Daten auf  
  
1.  Klicken Sie mit der rechten Maustaste auf den Datenbankknoten **Trade**, und wählen Sie **Neue Abfrage** aus.  
  
2.  Fügen Sie im Skriptbereich folgenden Code ein.  
  
    ```  
    insert into dbo.Suppliers values  
    (1, 'NorthWind Traders', 'Seattle, WA'),  
    (2, 'Contoso', 'Tacoma, WA')  
    GO  
  
    insert dbo.Customer values  
    (1, 'Fourth Coffee')  
    GO  
  
    insert dbo.Products values  
    (1, 'Apples', 0, 1, 1),  
    (2, 'Instant Coffee', 1, 2, 1)  
    GO  
    ```  
  
3.  Klicken Sie auf die Schaltfläche **Abfrage ausführen**, um diese Abfrage auszuführen. Die folgenden Meldungen im Bereich **Meldung** geben an, dass den Tabellen die Zeilen erfolgreich hinzugefügt wurden.  
  
**(2 Zeile(n) betroffen)(1 Zeile(n) betroffen)(2 Zeile(n) betroffen)**  
  
4.  Ersetzen Sie den Code im Skriptbereich durch den folgenden Code, und führen Sie die Abfrage aus. Hierdurch wird versucht, der Tabelle `Products` eine neue Zeile mit dem `ShelfLife`-Wert 6 hinzuzufügen.  
  
    ```  
    insert dbo.Products values  
    (3, 'Potato Chips', 6, 1, 1)  
    GO  
    ```  
  
5.  Im Bereich **Meldung** wird angegeben, dass die `INSERT`-Anweisung einen Konflikt mit der vorhandenen CHECK-Einschränkung verursacht, die `ShelfLife` auf einen niedrigeren Wert als 5 begrenzt. Die Tabelle "Products" wird nicht aktualisiert, da die Anweisung eine vorhandene Einschränkung nicht erfüllt.  
  
6.  Ändern Sie den Code wie folgt, und führen Sie die Abfrage erneut aus. Beachten Sie, dass die Zeile jetzt erfolgreich aktualisiert wird.  
  
    ```  
    insert dbo.Products values  
    (3, 'Potato Chips', 2, 1, 1)  
    GO  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
[Verwalten von Tabellen, Beziehungen und Beheben von Fehlern](../ssdt/manage-tables-relationships-and-fix-errors.md)  
[Verwenden des Transact-SQL-Editors zum Bearbeiten und Ausführen von Skripts](../ssdt/use-transact-sql-editor-to-edit-and-execute-scripts.md)  
  
