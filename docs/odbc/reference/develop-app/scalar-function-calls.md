---
title: Skalar-Funktionsaufrufe | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function calls
ms.assetid: 10cb4dcf-4cd8-4a56-8725-d080bd3ffe47
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 349599a51b2996f419e6c8656a71bc9e30146542
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304261"
---
# <a name="scalar-function-calls"></a>Aufrufe von Skalarfunktionen
Skalare Funktionen geben einen Wert für jede Zeile zurück. Beispielsweise nimmt die Skalarfunktion des absoluten Wertes eine numerische Spalte als Argument und gibt den absoluten Wert jedes Wertes in der Spalte zurück. Die Escape-Sequenz zum Aufrufen einer Skalarfunktion ist  
  
 **}** **{fn**_scalar-Funktion_    
  
 wobei *die Scalar-Funktion* eine der in [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)aufgeführten Funktionen ist. Weitere Informationen zur Escapesequenz der skalaren Funktion finden Sie unter [Scalar Function Escape Sequence](../../../odbc/reference/appendixes/scalar-function-escape-sequence.md) in Anhang C: SQL Grammar.  
  
 Die folgenden SQL-Anweisungen erstellen z. B. denselben Resultset mit Großbuchstaben-Kundennamen. Die erste Anweisung verwendet die Escape-Sequenz-Syntax. Die zweite Anweisung verwendet die systemeigene Syntax für Ingres für OS/2 und ist nicht interoperabel.  
  
```  
SELECT {fn UCASE(Name)} FROM Customers  
  
SELECT uppercase(Name) FROM Customers  
```  
  
 Eine Anwendung kann Aufrufe von skalaren Funktionen mischen, die native Syntax und Aufrufe von skalaren Funktionen verwenden, die ODBC-Syntax verwenden. Angenommen, Namen in der Tabelle Employee werden als Nachname, Komma und Vorname gespeichert. Die folgende SQL-Anweisung erstellt eine Resultset mit Nachnamen von Mitarbeitern in der Tabelle Employee. Die Anweisung verwendet die ODBC-Skalarfunktion **SUBSTRING** und die SQL Server-Skalarfunktion **CHARINDEX** und wird nur auf SQL Server korrekt ausgeführt.  
  
```  
SELECT {fn SUBSTRING(Name, 1, CHARINDEX(',', Name) - 1)} FROM Customers  
```  
  
 Für maximale Interoperabilität sollten Anwendungen die **scalar-Funktion CONVERT** verwenden, um sicherzustellen, dass die Ausgabe einer Skalarfunktion der erforderliche Typ ist. Die **CONVERT-Funktion** konvertiert Daten von einem SQL-Datentyp in den angegebenen SQL-Datentyp. Die Syntax der **CONVERT-Funktion** ist  
  
 **CONVERT(** _value_exp_ **,** _data_type_**)**  
  
 wobei *value_exp* ein Spaltenname, das Ergebnis einer anderen Skalarfunktion oder ein Literalwert und *data_type* ein Schlüsselwort ist, das mit dem **#define** Namen übereinstimmt, der von einem SQL-Datentypbezeichner verwendet wird, wie in [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md)definiert. Die folgende SQL-Anweisung verwendet **CONVERT** beispielsweise die CONVERT-Funktion, um sicherzustellen, dass die Ausgabe der **CURDATE-Funktion** ein Datum anstelle eines Zeitstempels oder Zeichendaten ist:  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, {fn CONVERT({fn CURDATE()}, SQL_DATE)}, ?, ?)  
```  
  
 Um zu bestimmen, welche Skalarfunktionen von einer Datenquelle unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit den Optionen SQL_CONVERT_FUNCTIONS, SQL_NUMERIC_FUNCTIONS, SQL_STRING_FUNCTIONS, SQL_SYSTEM_FUNCTIONS und SQL_TIMEDATE_FUNCTIONS auf. Um zu bestimmen, welche Konvertierungsvorgänge von der **CONVERT-Funktion** unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit einer der Optionen auf, die mit SQL_CONVERT beginnen.
