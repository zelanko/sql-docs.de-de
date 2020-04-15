---
title: Ausführen von Batches | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC], executing
- SQL statements [ODBC], batches
ms.assetid: f082c717-4f82-4820-a2fa-ba607d8fd872
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0ce0c043fcfad41a624ad129a757a047d2c87fb6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305731"
---
# <a name="executing-batches"></a>Ausführen von Batches
Bevor eine Anwendung einen Batch von Anweisungen ausführt, sollte sie zunächst überprüfen, ob sie unterstützt werden. Dazu ruft die Anwendung **SQLGetInfo** mit den Optionen SQL_BATCH_SUPPORT, SQL_PARAM_ARRAY_ROW_COUNTS und SQL_PARAM_ARRAY_SELECTS auf. Die erste Option gibt zurück, ob Zeilenanzahlgenerierende und ergebnissatzgenerierende Anweisungen in expliziten Batches und Prozeduren unterstützt werden, während die beiden letztgenannten Optionen Informationen über die Verfügbarkeit von Zeilenanzahlen und Ergebnissätzen in der parametrisierten Ausführung zurückgeben.  
  
 Batches von Anweisungen werden über **SQLExecute** oder **SQLExecDirect**ausgeführt. Der folgende Aufruf führt z. B. einen expliziten Stapel von Anweisungen aus, um einen neuen Auftrag zu öffnen.  
  
```  
SQLCHAR *BatchStmt =  
   "INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)"  
      "VALUES (2002, 1001, {fn CURDATE()}, 'Garcia', 'OPEN');"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 1, 1234, 10);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 2, 987, 8);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 3, 566, 17);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 4, 412, 500)";  
  
SQLExecDirect(hstmt, BatchStmt, SQL_NTS);  
```  
  
 Wenn ein Batch von ergebnisgenerierenden Anweisungen ausgeführt wird, gibt er eine oder mehrere Zeilenanzahlen oder Resultsets zurück. Informationen zum Abrufen dieser Ergebnisse finden Sie unter [Mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Wenn ein Batch von Anweisungen Parametermarkierungen enthält, werden diese in steigender Parameterreihenfolge nummeriert, wie sie in jeder anderen Anweisung enthalten sind. Der folgende Satz von Anweisungen enthält z. B. Parameter, die von 1 bis 21 nummeriert sind. Die in der ersten **INSERT-Anweisung** sind mit 1 bis 5 und die in der letzten **INSERT-Anweisung** mit den Nummern 18 bis 21 nummeriert.  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
```  
  
 Weitere Informationen zu Parametern finden Sie weiter unten in diesem Abschnitt unter [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md).
