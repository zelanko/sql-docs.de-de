---
title: Aufrufe von Skalarfunktionen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 24b62c2b5cd449b6e7201d413b315e48fbd570f6
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54132575"
---
# <a name="scalar-function-calls"></a>Aufrufe von Skalarfunktionen
Skalarfunktionen geben einen Wert für jede Zeile zurück. Z. B. die Skalarfunktion absoluten Wert eine numerische Spalte als Argument akzeptiert und gibt den absoluten Wert der einzelnen Werte in der Spalte zurück. Die-Escapesequenz zum Aufrufen einer Skalarfunktion ist.  
  
 **{fn** _-Skalarfunktion_ **}**  
  
 wo *-Skalarfunktion* ist eine der Funktionen in [Anhang E: Skalare Funktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md). Weitere Informationen zu den Escapesequenz Skalarfunktion, finden Sie unter [skalare Funktionsescapesequenz](../../../odbc/reference/appendixes/scalar-function-escape-sequence.md) in Anhang C: SQL-Grammatik.  
  
 Z. B. erstellen die folgenden SQL-Anweisungen Sie das gleiche Resultset Großbuchstaben Kunden Namen. Die erste Anweisung verwendet die Syntax der Escapesequenz. Die zweite Anweisung verwendet die systemeigene Syntax für Ingres für OS/2 und ist nicht interoperabel.  
  
```  
SELECT {fn UCASE(Name)} FROM Customers  
  
SELECT uppercase(Name) FROM Customers  
```  
  
 Aufrufe von Skalarfunktionen, die systemeigenen Syntax verwenden und Aufrufe von Skalarfunktionen, die ODBC-Syntax verwenden, kann eine Anwendung kombinieren. Nehmen wir beispielsweise an, dass Namen in der Employee-Tabelle gespeichert werden, als einen Nachnamen ein, ein Komma und einen Vornamen ein. Die folgende SQL-Anweisung erstellt ein Resultset der Nachnamen der Mitarbeiter in der Employee-Tabelle. Die Anweisung verwendet die ODBC-Skalarfunktion **TEILZEICHENFOLGE** und die SQL Server-Skalarfunktion **CHARINDEX** und wird nur für SQL Server ordnungsgemäß ausgeführt.  
  
```  
SELECT {fn SUBSTRING(Name, 1, CHARINDEX(',', Name) - 1)} FROM Customers  
```  
  
 Für eine optimale Interoperabilität sollten Anwendungen verwenden die **konvertieren** skalare Funktion, um sicherzustellen, dass die Ausgabe eine skalare Funktion mit den erforderlichen Typ ist. Die **konvertieren** Funktion konvertiert die Daten von einem SQL-Datentyp, in der angegebenen SQL-Datentyp. Die Syntax der **konvertieren** -Funktion ist  
  
 **KONVERTIEREN (** _Value_exp_ **,** _Data_type_**)**  
  
 in denen *Value_exp* ist, einen Spaltennamen an, das Ergebnis von einem anderen skalaren Funktion oder ein Literalwert, und *Data_type* ist ein Schlüsselwort, das entspricht der **#define** Name, mit dem ein SQL-Datentyp Bezeichner gemäß [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md). Beispielsweise die folgende SQL-Anweisung verwendet die **konvertieren** Funktion, um sicherzustellen, dass die Ausgabe der **CURDATE** -Funktion ist ein Datum ist, anstatt ein Zeitstempel oder Zeichen-Daten:  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, {fn CONVERT({fn CURDATE()}, SQL_DATE)}, ?, ?)  
```  
  
 Um zu bestimmen, welche skalaren Funktionen, die von einer Datenquelle unterstützt werden, eine Anwendung ruft **SQLGetInfo** mit der SQL_CONVERT_FUNCTIONS SQL_NUMERIC_FUNCTIONS, SQL_STRING_FUNCTIONS, SQL_SYSTEM_FUNCTIONS und SQL_TIMEDATE_ Optionen für Funktionen. Um zu bestimmen, welche Konvertierungsvorgänge von Microsoft Intune die **konvertieren** -Funktion, eine Anwendung ruft **SQLGetInfo** mit den Optionen, die mit SQL_CONVERT beginnen.
