---
title: Erstellen von Sichten und gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- creating views and stored procedures
ms.assetid: 53a0426d-07d8-4b7c-aa21-22632753bad8
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 20f16e9deeb9e07d2c63090c92100871331e0443
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211183"
---
# <a name="creating-views-and-stored-procedures"></a>Erstellen von Sichten und gespeicherten Prozeduren
  Da Mary nun auf die **testdata** -Datenbank zugreifen kann, möchten Sie möglicherweise einige Datenbankobjekte erstellen, z. b. eine Sicht und eine gespeicherte Prozedur, und Mary dann Zugriff auf diese Datenbanken gewähren. Bei einer Sicht handelt es sich um eine gespeicherte SELECT-Anweisung, und eine gespeicherte Prozedur setzt sich aus einer oder mehreren [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen zusammen, die als Batch ausgeführt werden.  
  
 Sichten werden wie Tabellen abgefragt und nehmen keine Parameter an. Gespeicherte Prozeduren sind komplexer als Sichten. Gespeicherte Prozeduren können sowohl Eingabe- als auch Ausgabeparameter aufweisen und Anweisungen enthalten, die den Ablauf des Codes steuern, wie z. B. IF- und WHILE-Anweisungen. Als eine der Grundregeln guter Programmierung gilt die Verwendung gespeicherter Prozeduren für alle Aktionen, die sich in der Datenbank wiederholen.  
  
 In diesem Beispiel erstellen Sie mithilfe von CREATE VIEW eine Sicht, die nur zwei der Spalten in der **Products** -Tabelle auswählt. Sie erstellen dann mithilfe von CREATE PROCEDURE eine gespeicherte Prozedur, die einen Parameter für den Preis akzeptiert und nur die Produkte zurückgibt, deren Preis unter dem angegebenen Parameterwert liegt.  
  
### <a name="to-create-a-view"></a>So erstellen Sie eine Sicht  
  
1.  Führen Sie die folgende Anweisung aus, um eine sehr einfache Sicht zu erstellen, die eine SELECT-Anweisung ausführt und die Namen und Preise der Produkte an den Benutzer zurückgibt.  
  
    ```  
    CREATE VIEW vw_Names  
       AS  
       SELECT ProductName, Price FROM Products;  
    GO  
  
    ```  
  
### <a name="test-the-view"></a>Testen der Sicht  
  
1.  Sichten werden genau wie Tabellen behandelt. Greifen Sie mithilfe einer `SELECT` -Anweisung auf eine Sicht zu.  
  
    ```  
    SELECT * FROM vw_Names;  
    GO  
  
    ```  
  
### <a name="to-create-a-stored-procedure"></a>So erstellen Sie eine gespeicherte Prozedur  
  
1.  Die folgende Anweisung erstellt eine gespeicherte Prozedur namens `pr_Names`, die einen Eingabeparameter mit der Bezeichnung `@VarPrice` vom Datentyp `money`akzeptiert. Die gespeicherte Prozedur druckt die mit dem Eingabeparameter verkettete `Products less than` -Anweisung. Dieser Parameter wird vom `money` -Datentyp in den `varchar(10)` -Zeichendatentyp geändert. Dann führt die Prozedur eine `SELECT` -Anweisung für die Sicht aus und übergibt dabei den Eingabeparameter als Teil der `WHERE` -Klausel. Dadurch werden alle Produkte zurückgegeben, deren Preis unter dem Wert des Eingabeparameters liegt.  
  
    ```  
    CREATE PROCEDURE pr_Names @VarPrice money  
       AS  
       BEGIN  
          -- The print statement returns text to the user  
          PRINT 'Products less than ' + CAST(@VarPrice AS varchar(10));  
          -- A second statement starts here  
          SELECT ProductName, Price FROM vw_Names  
                WHERE Price < @varPrice;  
       END  
    GO  
  
    ```  
  
### <a name="test-the-stored-procedure"></a>Testen der gespeicherten Prozedur.  
  
1.  Wenn Sie die gespeicherte Prozedur testen möchten, geben Sie die folgende Anweisung ein, und führen Sie sie aus. Die Prozedur sollte die Namen der beiden Produkte zurückgeben, die Sie in Lektion 1 mit einem Preis unter `Products` in die `10.00`-Tabelle eingegeben haben.  
  
    ```  
    EXECUTE pr_Names 10.00;  
    GO  
  
    ```  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Erteilen des Zugriffs auf ein Datenbankobjekt](lesson-2-4-granting-access-to-a-database-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE VIEW &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-view-transact-sql)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
