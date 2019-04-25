---
title: Batches von SQL-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC]
- SQL statements [ODBC], batches
- batches [ODBC], about batches
ms.assetid: 766488cc-450c-434c-9c88-467f6c57e17c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 09805ab73af76bc55890222fc1ffd0e1857d0f33
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62447388"
---
# <a name="batches-of-sql-statements"></a>Batches von SQL-Anweisungen
Ein Batch von SQL-Anweisungen ist eine Gruppe von zwei oder mehr SQL-Anweisungen oder eine SQL-Anweisung, die die gleiche Auswirkung wie eine Gruppe von zwei oder mehr SQL-Anweisungen. In einigen Implementierungen wird die gesamte Batch-Anweisung ausgeführt, bevor alle Ergebnisse verfügbar sind. Dies ist häufig effizienter als das Senden getrennter, Anweisungen, da der Netzwerkdatenverkehr dadurch meist reduziert, und die Datenquelle kann die Ausführung eines Batches von SQL-Anweisungen manchmal optimieren. In anderen Implementierungen Aufrufen **SQLMoreResults** die Ausführung der nächsten Anweisung im Batch. ODBC unterstützt die folgenden Arten von Batches:  
  
-   **Explizite Batches** ein *explizite Batch* mindestens zwei SQL-Anweisungen, die durch Semikolons (;) getrennt ist. Beispielsweise wird der folgende Batch von SQL-Anweisungen einen neuen Verkaufsauftrag geöffnet. Dies erfordert das Einfügen von Zeilen in der Bestellungen und der Zeilen. Beachten Sie, dass kein Semikolon nach der letzten Anweisung.  
  
    ```  
    INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
       VALUES (2002, 1001, {fn CURDATE()}, 'Garcia', 'OPEN');  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 1, 1234, 10);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 2, 987, 8);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 3, 566, 17);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 4, 412, 500)  
    ```  
  
-   **Prozeduren** , wenn eine Prozedur mehr als eine SQL-Anweisung enthält, gilt dies ein Batch von SQL-Anweisungen ausgeführt werden. Die folgende SQL Server-spezifische-Anweisung erstellt z. B. eine Prozedur, die ein Resultset mit Informationen zu einem Kunden und Auflisten von alle offenen Aufträge dieses Kunden ein Resultset zurückgibt:  
  
    ```  
    CREATE PROCEDURE GetCustInfo (@CustomerID INT) AS  
       SELECT * FROM Customers WHERE CustID = @CustomerID  
       SELECT OrderID FROM Orders  
          WHERE CustID = @CustomerID AND Status = 'OPEN'  
    ```  
  
     Die **CREATE PROCEDURE** -Anweisung selbst ist keines Batches von SQL-Anweisungen. Die Prozedur erstellt wird, ist jedoch ein Batch von SQL-Anweisungen. Keine Semikolons trennen die beiden **wählen** Anweisungen da die **CREATE PROCEDURE** Anweisung bezieht sich auf SQL Server und SQL Server erfordert keine Semikolons, um mehrere Anweisungen in einem  **CREATE PROCEDURE** Anweisung.  
  
-   **Von Parameterarrays** von Parameterarrays mit einer parametrisierten SQL­Anweisung als eine effektive Möglichkeit zum Ausführen von Massenvorgängen verwendet werden können. Beispielsweise können Arrays von Parametern verwendet werden, durch den folgenden **einfügen** Anweisung mehrere Zeilen in der Tabelle Zeilen eingefügt werden, während der Ausführung nur einer einzelnen SQL­Anweisung:  
  
    ```  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (?, ?, ?, ?)  
    ```  
  
     Wenn eine Datenquelle von Parameterarrays nicht unterstützt, kann der Treiber diese emulieren, durch Ausführen der SQL-Anweisung einmal für jeden Parameter. Weitere Informationen finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md) und [Arrays von Parameterwerten](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)weiter unten in diesem Abschnitt.  
  
 Die verschiedenen Arten von Batches können nicht auf interoperable Weise kombiniert werden. Also wie eine Anwendung bestimmt das Ergebnis der Ausführung eines expliziten Batches, das Prozedur enthält aufruft, einen explizite Batch, der Arrays von Parametern, verwendet und ein Prozeduraufruf an, der Arrays von Parametern verwendet ist treiberspezifisch.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Anweisungen mit generiertem Ergebnis und ohne Ergebnis](../../../odbc/reference/develop-app/result-generating-and-result-free-statements.md)  
  
-   [Ausführen von Batches](../../../odbc/reference/develop-app/executing-batches.md)  
  
-   [Fehler und Batches](../../../odbc/reference/develop-app/errors-and-batches.md)
