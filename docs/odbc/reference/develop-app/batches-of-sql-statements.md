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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d68ea1c13655ca7c57ba076823f461a4b2e22055
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283510"
---
# <a name="batches-of-sql-statements"></a>Batches von SQL-Anweisungen
Bei einem Batch von SQL-Anweisungen handelt es sich um eine Gruppe von zwei oder mehr SQL-Anweisungen oder eine einzelne SQL-Anweisung, die denselben Effekt wie eine Gruppe von zwei oder mehr SQL-Anweisungen hat. In einigen Implementierungen wird die gesamte Batch-Anweisung ausgeführt, bevor Ergebnisse verfügbar sind. Dies ist oft effizienter als das getrennte Senden von Anweisungen, da der Netzwerk Datenverkehr häufig reduziert werden kann und die Datenquelle die Ausführung eines Batches von SQL-Anweisungen manchmal optimieren kann. In anderen Implementierungen löst der Aufruf von **SQLMoreResults** die Ausführung der nächsten Anweisung im Batch aus. ODBC unterstützt die folgenden Typen von Batches:  
  
-   **Explizite Batches** Ein *expliziter Batch* besteht aus zwei oder mehr SQL-Anweisungen, die durch Semikolons (;) getrennt sind. Der folgende Batch von SQL-Anweisungen öffnet z. b. einen neuen Verkaufsauftrag. Dies erfordert, dass Zeilen in die Tabellen Orders und Lines eingefügt werden. Beachten Sie, dass nach der letzten Anweisung kein Semikolon vorhanden ist.  
  
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
  
-   **Prozeduren** Wenn eine Prozedur mehr als eine SQL-Anweisung enthält, wird Sie als Batch von SQL-Anweisungen betrachtet. Beispielsweise wird mit der folgenden SQL Server-spezifischen Anweisung eine Prozedur erstellt, die ein Resultset mit Informationen zu einem Kunden und ein Resultset mit allen offenen Verkaufsaufträgen für den Kunden zurückgibt:  
  
    ```  
    CREATE PROCEDURE GetCustInfo (@CustomerID INT) AS  
       SELECT * FROM Customers WHERE CustID = @CustomerID  
       SELECT OrderID FROM Orders  
          WHERE CustID = @CustomerID AND Status = 'OPEN'  
    ```  
  
     Die **CREATE PROCEDURE** -Anweisung selbst ist kein Batch von SQL-Anweisungen. Dabei handelt es sich jedoch um einen Batch von SQL-Anweisungen. Die beiden **Select** -Anweisungen werden von keinem Semikolon getrennt, da die **CREATE PROCEDURE** -Anweisung für SQL Server spezifisch ist und SQL Server keine Semikolons zum Trennen mehrerer Anweisungen in einer **CREATE PROCEDURE** -Anweisung erfordert.  
  
-   **Arrays von Parametern** Arrays von Parametern können mit einer parametrisierten SQL-Anweisung als effektive Methode zum Ausführen von Massen Vorgängen verwendet werden. Beispielsweise können Arrays von Parametern mit der folgenden **Insert** -Anweisung verwendet werden, um mehrere Zeilen in die Zeilen Tabelle einzufügen, während nur eine einzelne SQL-Anweisung ausgeführt wird:  
  
    ```  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (?, ?, ?, ?)  
    ```  
  
     Wenn eine Datenquelle keine Arrays von Parametern unterstützt, kann der Treiber Sie emulieren, indem er die SQL-Anweisung einmal für jeden Parametersatz ausführt. Weitere Informationen finden Sie unter [Anweisungs Parameter](../../../odbc/reference/develop-app/statement-parameters.md) und [Arrays von Parameter Werten](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)weiter unten in diesem Abschnitt.  
  
 Die unterschiedlichen Typen von Batches können nicht interoperabel gemischt werden. Das heißt, wie eine Anwendung das Ergebnis der Ausführung eines expliziten Batches bestimmt, der Prozedur Aufrufe enthält, ein expliziter Batch, der Parameter Arrays verwendet, und ein Prozedur Aufruf, der Parameter Arrays verwendet, ist Treiber spezifisch.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Anweisungen mit generiertem Ergebnis und ohne Ergebnis](../../../odbc/reference/develop-app/result-generating-and-result-free-statements.md)  
  
-   [Ausführen von Batches](../../../odbc/reference/develop-app/executing-batches.md)  
  
-   [Fehler und Batches](../../../odbc/reference/develop-app/errors-and-batches.md)
