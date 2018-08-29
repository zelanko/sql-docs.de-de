---
title: Einfügen von Daten in eine Tabelle und Aktualisieren der Daten (Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- inserting and updating data
ms.assetid: 514dc87a-b829-43b5-8fc8-1a400a260284
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 051301fc440de5336701438e35fbbaebc68b0b17
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43035504"
---
# <a name="inserting-and-updating-data-in-a-table-tutorial"></a>Einfügen und Aktualisieren von Daten in einer Tabelle (Lernprogramm)
  Nachdem Sie nun die **Products**-Tabelle erstellt haben, können Sie Daten mithilfe der INSERT-Anweisung in die Tabelle einfügen. Nach dem Einfügen der Daten ändern Sie den Inhalt einer Zeile mithilfe einer UPDATE-Anweisung. Mithilfe der WHERE-Klausel der UPDATE-Anweisung schränken Sie das Update auf eine einzelne Zeile ein. Durch die vier Anweisungen werden die folgenden Daten eingegeben.  
  
|ProductID|ProductName|Price|ProductDescription|  
|---------------|-----------------|-----------|------------------------|  
|1|Clamp|12.48|Workbench clamp|  
|50|Screwdriver|3.17|Flat head|  
|75|Tire Bar||Tool for changing tires.|  
|3000|3mm Bracket|.52||  
  
 Die grundlegende Syntax lautet: INSERT, Tabellenname, Spaltenliste, VALUES und dann eine Liste der einzufügenden Werte. Die beiden Bindestriche vor einer Zeile geben an, dass es sich bei der Zeile um einen Kommentar handelt, der vom Compiler ignoriert wird. In diesem Fall wird im Kommentar eine zulässige Variante der Syntax beschrieben.  
  
### <a name="to-insert-data-into-a-table"></a>So fügen Sie Daten in eine Tabelle ein  
  
1.  Führen Sie die folgende Anweisung aus, um eine Zeile in die in der vorhergehenden Aufgabe erstellte `Products` -Tabelle einzufügen. Dies ist die grundlegende Syntax.  
  
    ```  
    -- Standard syntax  
    INSERT dbo.Products (ProductID, ProductName, Price, ProductDescription)  
        VALUES (1, 'Clamp', 12.48, 'Workbench clamp')  
    GO  
  
    ```  
  
2.  In der folgenden Anweisung sehen Sie, wie die Reihenfolge, in der die Parameter bereitgestellt werden, durch Wechseln der Position von `ProductID` und `ProductName` sowohl in der Liste der Felder (in Klammern) als auch in der Liste der Werte geändert werden kann.  
  
    ```  
    -- Changing the order of the columns  
    INSERT dbo.Products (ProductName, ProductID, Price, ProductDescription)  
        VALUES ('Screwdriver', 50, 3.17, 'Flat head')  
    GO  
  
    ```  
  
3.  Die folgende Anweisung veranschaulicht, dass die Namen der Spalten optional sind, solange die Werte in der richtigen Reihenfolge aufgelistet werden. Obwohl diese Syntax gängig ist, wird ihre Verwendung nicht empfohlen, da sie das Verständnis des Codes durch Dritte erschweren könnte. `NULL` wird für die `Price` -Spalte angegeben, da der Preis für dieses Produkt noch nicht bekannt ist.  
  
    ```  
    -- Skipping the column list, but keeping the values in order  
    INSERT dbo.Products  
        VALUES (75, 'Tire Bar', NULL, 'Tool for changing tires.')  
    GO  
  
    ```  
  
4.  Der Schemaname ist optional, solange Sie auf eine Tabelle im Standardschema zugreifen und diese ändern. Da die `ProductDescription` -Spalte NULL-Werte zulässt und kein Wert bereitgestellt wird, können Name und Wert der `ProductDescription` -Spalte vollständig aus der Anweisung gelöscht werden.  
  
    ```  
    -- Dropping the optional dbo and dropping the ProductDescription column  
    INSERT Products (ProductID, ProductName, Price)  
        VALUES (3000, '3mm Bracket', .52)  
    GO  
    ```  
  
### <a name="to-update-the-products-table"></a>So aktualisieren Sie die Products-Tabelle  
  
1.  Geben Sie die folgende `UPDATE` -Anweisung zum Ändern von `ProductName` des zweiten Produkts von `Screwdriver`in `Flat Head Screwdriver`ein, und führen Sie sie aus.  
  
    ```  
    UPDATE dbo.Products  
        SET ProductName = 'Flat Head Screwdriver'  
        WHERE ProductID = 50  
    GO  
    ```  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Lesen der Daten in einer Tabelle &#40;Tutorial&#41;](lesson-1-4-reading-the-data-in-a-table.md)  
  
## <a name="see-also"></a>Siehe auch  
 [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)   
 [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql)  
  
  
