---
title: Daten in einer Tabelle lesen (Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- reading data in a table
ms.assetid: 532232c9-3d41-45cd-9150-de67a1cbfcf5
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 0649e167ebaa90267422594ccd193ba468838e6f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "68187289"
---
# <a name="reading-the-data-in-a-table-tutorial"></a>Lesen der Daten in einer Tabelle (Lernprogramm)
  Daten in einer Tabelle können mithilfe der SELECT-Anweisung gelesen werden. Die SELECT-Anweisung gehört zu den wichtigsten [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen. Ihre Syntax zeichnet sich durch unzählige Variationen aus. In diesem Lernprogramm arbeiten Sie mit fünf einfachen Versionen.  
  
### <a name="to-read-the-data-in-a-table"></a>So lesen Sie die Daten in einer Tabelle  
  
1.  Geben Sie die folgenden Anweisungen zum Lesen der Daten in der `Products` -Tabelle ein, und führen Sie sie aus.  
  
    ```  
    -- The basic syntax for reading data from a single table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
    GO  
  
    ```  
  
2.  Sie können alle Spalten in der Tabelle mithilfe eines Sternchens auswählen. Dies wird häufig bei Ad-hoc-Abfragen verwendet. Sie sollten die Spaltenliste im dauerhaften Code bereitstellen, sodass die Anweisung die vorhergesagten Spalten zurückgibt, selbst wenn der Tabelle später eine neue Spalte hinzugefügt wird.  
  
    ```  
    -- Returns all columns in the table  
    -- Does not use the optional schema, dbo  
    SELECT * FROM Products  
    GO  
  
    ```  
  
3.  Sie können Spalten auslassen, die nicht zurückgegeben werden sollen. Die Spalten werden in der Reihenfolge zurückgegeben, in der sie aufgelistet sind.  
  
    ```  
    -- Returns only two of the columns from the table  
    SELECT ProductName, Price  
        FROM dbo.Products  
    GO  
  
    ```  
  
4.  Mithilfe einer `WHERE` -Klausel können Sie die an den Benutzer zurückgegebenen Zeilen beschränken.  
  
    ```  
    -- Returns only two of the records in the table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
        WHERE ProductID < 60  
    GO  
  
    ```  
  
5.  Sie können die Werte in den Spalten direkt nach ihrer Rückgabe bearbeiten. Im folgenden Beispiel wird eine mathematische Operation für die `Price` -Spalte ausgeführt. Spalten, die auf diese Weise geändert wurden, weisen keinen Namen auf, es sei denn, Sie geben einen Namen mithilfe des `AS` -Schlüsselworts an.  
  
    ```  
    -- Returns ProductName and the Price including a 7% tax  
    -- Provides the name CustomerPays for the calculated column  
    SELECT ProductName, Price * 1.07 AS CustomerPays  
        FROM dbo.Products  
    GO  
    ```  
  
## <a name="functions-that-are-useful-in-a-select-statement"></a>Funktionen, die in einer SELECT-Anweisung nützlich sind  
 Weitere Informationen zu bestimmten Funktionen, die zum Bearbeiten von Daten in SELECT-Anweisungen verwendet werden können, finden Sie in den folgenden Themen:  
  
|||  
|-|-|  
|[String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen &#40;Transact-SQL&#41;)](/sql/t-sql/functions/string-functions-transact-sql)|[Date and Time Data Types and Functions &#40;Transact-SQL&#41; (Datums- und Uhrzeitdatentypen und zugehörige Funktionen (Transact-SQL))](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|  
|[Mathematische Funktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/mathematical-functions-transact-sql)|[Text- und Bildfunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/text-and-image-functions-textptr-transact-sql)|  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Zusammenfassung: Erstellen von Datenbankobjekten](lesson-1-5-summary-creating-database-objects.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)  
  
  
