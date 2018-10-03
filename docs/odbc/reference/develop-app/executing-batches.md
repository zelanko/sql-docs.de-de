---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 46b224e8167587c4e4860f171b132d23539143e8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47695032"
---
# <a name="executing-batches"></a>Ausführen von Batches
Bevor eine Anwendung einen Batch von Anweisungen ausführt, wird zunächst überprüft, ob diese unterstützt werden. Ruft die Anwendung dazu **SQLGetInfo** mit den Optionen SQL_BATCH_SUPPORT SQL_PARAM_ARRAY_ROW_COUNTS und SQL_PARAM_ARRAY_SELECTS. Die erste Option gibt, ob Count – Generieren von Zeile und Ergebnis-Gruppe – Generieren von Anweisungen unterstützt in explizite Batches und Prozeduren, während die letzten beiden Optionen, die Informationen über die Verfügbarkeit der Zeilenanzahl und das Ergebnis zurück, legt in fest parametrisiert die Ausführung.  
  
 Batches von Anweisungen werden ausgeführt, über **SQLExecute** oder **SQLExecDirect**. Der folgende Aufruf führt z. B. eine explizite Batches von Anweisungen, um einen neuen Verkaufsauftrag zu öffnen.  
  
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
  
 Wenn ein Batch von generiertem Anweisungen ausgeführt wird, gibt einen oder mehrere Zeilenanzahl oder Ergebnis festgelegt. Informationen dazu, wie Sie diese abrufen, finden Sie unter [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Wenn Sie ein Batch von Anweisungen Parametermarker enthält, werden diese nummeriert, in aufsteigender Reihenfolge der Parameter, wie sie in eine andere Anweisung sind. Der folgende Batch von Anweisungen ist z. B. von 1 bis 21 nummerierte Parameter; die in der ersten **einfügen** Anweisung sind nummerierten 1 bis 5 und die in den letzten **einfügen** Anweisung sind nummerierten 18 bis 21.  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
```  
  
 Weitere Informationen zu Parametern finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.
