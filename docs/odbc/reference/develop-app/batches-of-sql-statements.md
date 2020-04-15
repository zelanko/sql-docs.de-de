---
title: Batches von SQL-Anweisungen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283510"
---
# <a name="batches-of-sql-statements"></a>Batches von SQL-Anweisungen
Ein Batch von SQL-Anweisungen ist eine Gruppe von zwei oder mehr SQL-Anweisungen oder eine einzelne SQL-Anweisung, die denselben Effekt wie eine Gruppe von zwei oder mehr SQL-Anweisungen hat. In einigen Implementierungen wird die gesamte Batchanweisung ausgeführt, bevor Ergebnisse verfügbar sind. Dies ist oft effizienter als das separate Übermitteln von Anweisungen, da der Netzwerkverkehr häufig reduziert werden kann und die Datenquelle manchmal die Ausführung eines Batches von SQL-Anweisungen optimieren kann. In anderen Implementierungen löst der Aufruf von **SQLMoreResults** die Ausführung der nächsten Anweisung im Batch aus. ODBC unterstützt die folgenden Batchtypen:  
  
-   **Explizite Batches** Ein *expliziter Batch* besteht aus zwei oder mehr SQL-Anweisungen, die durch Semikolons (;) getrennt sind. Der folgende Stapel von SQL-Anweisungen öffnet z. B. einen neuen Auftrag. Dazu müssen Zeilen sowohl in die Tabellen Orders als auch Lines eingefügt werden. Beachten Sie, dass nach der letzten Anweisung kein Semikolon vorhanden ist.  
  
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
  
-   **Verfahren** Wenn eine Prozedur mehr als eine SQL-Anweisung enthält, wird sie als batch von SQL-Anweisungen betrachtet. Die folgende SQL Server-spezifische Anweisung erstellt z. B. eine Prozedur, die ein Resultset mit Informationen über einen Debitor und ein Resultset mit allen offenen Aufträgen für diesen Debitor zurückgibt:  
  
    ```  
    CREATE PROCEDURE GetCustInfo (@CustomerID INT) AS  
       SELECT * FROM Customers WHERE CustID = @CustomerID  
       SELECT OrderID FROM Orders  
          WHERE CustID = @CustomerID AND Status = 'OPEN'  
    ```  
  
     Die **CREATE PROCEDURE-Anweisung** selbst ist kein Batch von SQL-Anweisungen. Die prozedur, die sie erstellt, ist jedoch ein Batch von SQL-Anweisungen. Keine Semikolons **SELECT** trennen die beiden SELECT-Anweisungen, da die **CREATE PROCEDURE-Anweisung** für SQL Server spezifisch ist und SQL Server keine Semikolons erfordert, um mehrere Anweisungen in einer **CREATE PROCEDURE-Anweisung** zu trennen.  
  
-   **Arrays von Parametern** Arrays von Parametern können mit einer parametrisierten SQL-Anweisung als effektive Möglichkeit zum Ausführen von Massenvorgängen verwendet werden. Beispielsweise können Arrays von Parametern mit der folgenden **INSERT-Anweisung** verwendet werden, um mehrere Zeilen in die Lines-Tabelle einzufügen, während nur eine einzelne SQL-Anweisung ausgeführt wird:  
  
    ```  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (?, ?, ?, ?)  
    ```  
  
     Wenn eine Datenquelle keine Arrays von Parametern unterstützt, kann der Treiber diese emulieren, indem er die SQL-Anweisung einmal für jeden Parametersatz ausführt. Weitere Informationen finden Sie weiter unten in diesem Abschnitt unter [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md) und [Arrays von Parameterwerten](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Die verschiedenen Chargentypen können nicht interoperabel gemischt werden. Das heißt, wie eine Anwendung das Ergebnis der Ausführung eines expliziten Batches bestimmt, der Prozeduraufrufe, einen expliziten Batch, der Arrays von Parametern verwendet, und einen Prozeduraufruf, der Arrays von Parametern verwendet, treiberspezifisch ist.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Anweisungen mit generiertem Ergebnis und ohne Ergebnis](../../../odbc/reference/develop-app/result-generating-and-result-free-statements.md)  
  
-   [Ausführen von Batches](../../../odbc/reference/develop-app/executing-batches.md)  
  
-   [Fehler und Batches](../../../odbc/reference/develop-app/errors-and-batches.md)
