---
description: Ausführen von Batches
title: Ausführen von Batches | Microsoft-Dokumentation
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
ms.openlocfilehash: b3bb923f95dfcfb731d472aad8ead7ff35053171
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424642"
---
# <a name="executing-batches"></a>Ausführen von Batches
Bevor eine Anwendung einen Batch von-Anweisungen ausführt, sollte Sie zuerst überprüfen, ob Sie unterstützt werden. Hierzu ruft die Anwendung **SQLGetInfo** mit den Optionen SQL_BATCH_SUPPORT, SQL_PARAM_ARRAY_ROW_COUNTS und SQL_PARAM_ARRAY_SELECTS auf. Die erste Option gibt an, ob die Zeilen Anzahl-Generierungs-und Resultset-Generierungs Anweisungen in expliziten Batches und Prozeduren unterstützt werden, während die beiden beiden Optionen Informationen zur Verfügbarkeit von Zeilen-und Resultsets in parametrisierter Ausführung zurückgeben.  
  
 Batches von Anweisungen werden über **SQLExecute** oder **SQLExecDirect**ausgeführt. Der folgende-Befehl führt z. b. einen expliziten Batch von-Anweisungen zum Öffnen eines neuen Verkaufs Auftrags aus.  
  
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
  
 Wenn ein Batch von Ergebnis Generierungs Anweisungen ausgeführt wird, gibt er mindestens eine Zeilen Anzahl oder Resultsets zurück. Informationen dazu, wie Sie diese abrufen, finden Sie unter [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Wenn ein Batch von-Anweisungen Parameter Markierungen enthält, werden diese in einer zunehmenden Parameterreihenfolge nummeriert, wie Sie in jeder anderen-Anweisung enthalten sind. Der folgende Batch von-Anweisungen hat z. b. Parameter, die von 1 bis 21 nummeriert sind. die in der ersten **Insert** -Anweisung nummerierten 1 bis 5, und die in der letzten **Insert** -Anweisung sind von 18 bis 21 nummeriert.  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
```  
  
 Weitere Informationen zu Parametern finden Sie unter [Anweisungs Parameter](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.
