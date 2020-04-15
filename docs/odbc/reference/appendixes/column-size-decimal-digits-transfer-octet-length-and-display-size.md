---
title: Spaltengröße, Dezimalstellen, Übertragen von Oktettlänge, Displaygröße | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- display size of data types [ODBC]
- data types [ODBC], column size
- transfer octet length of data types [ODBC]
- size of data types [ODBC]
- data types [ODBC], display size
- decimal digits of data types [ODBC]
- data types [ODBC], decimal digits
- SQL data types [ODBC], column characteristics
- column size of data types [ODBC]
- data types [ODBC], transfer octet length
ms.assetid: 723107a1-be08-4ea3-a8c0-b2c45d38d1aa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55b8e9dd305764a89601e9ffd5a337e42a8d8db3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306571"
---
# <a name="column-size-decimal-digits-transfer-octet-length-and-display-size---odbc"></a>Spaltengröße, Dezimalziffern, Oktettlänge und Anzeigegröße übertragen - ODBC
Datentypen zeichnen sich durch Spaltengröße (oder Parameter) aus, Dezimalstellen, Länge und Anzeigegröße. Die folgenden ODBC-Funktionen geben diese Attribute für einen Parameter in einer SQL-Anweisung oder für einen SQL-Datentyp in einer Datenquelle zurück. Jede ODBC-Funktion gibt einen anderen Satz dieser Attribute wie folgt zurück:  
  
-   **SQLDescribeCol** gibt die Spaltengröße und die Dezimalstellen der beschriebenen Spalten zurück.  
  
-   **SQLDescribeParam** gibt die Parametergröße und Dezimalstellen der beschriebenen Parameter zurück. **SQLBindParameter** legt die Parametergröße und Dezimalstellen für einen Parameter in einer SQL-Anweisung fest.  
  
-   Die Katalogfunktionen **SQLColumns**, **SQLProcedureColumns**und **SQLGetTypeInfo** geben Attribute für eine Spalte in einer Tabelle, einem Resultset oder einem Prozedurparameter und die Katalogattribute der Datentypen in der Datenquelle zurück. **SQLColumns** gibt die Spaltengröße, Dezimalstellen und Länge einer Spalte in angegebenen Tabellen (z. B. Basistabelle, Ansicht oder Systemtabelle) zurück. **SQLProcedureColumns** gibt die Spaltengröße, Dezimalstellen und die Länge einer Spalte in einer Prozedur zurück. **SQLGetTypeInfo** gibt die maximale Spaltengröße und die minimalen und maximalen Dezimalstellen eines SQL-Datentyps in einer Datenquelle zurück.  
  
 Die von diesen Funktionen für die Spalten- oder Parametergröße zurückgegebenen Werte entsprechen der "Genauigkeit" gemäß ODBC 2. *x*. Die Werte entsprechen jedoch nicht unbedingt den Werten, die in SQL_DESC_PRECISION oder einem anderen Deskriptorfeld zurückgegeben werden. Dasselbe gilt für Dezimalstellen, die "skala" entsprechen, wie in ODBC 2 definiert. *x*. Sie entspricht nicht unbedingt den Werten, die in SQL_DESC_SCALE oder einem anderen Deskriptorfeld zurückgegeben werden, sondern kommt je nach Datentyp aus unterschiedlichen Deskriptorfeldern. Weitere Informationen finden Sie unter [Spaltengröße](../../../odbc/reference/appendixes/column-size.md) und [Dezimalziffern](../../../odbc/reference/appendixes/decimal-digits.md).  
  
 Ebenso stammen die Werte für die Übertragungsoktettlänge nicht von SQL_DESC_LENGTH. Sie stammen aus dem SQL_DESC_OCTET_LENGTH eines Deskriptorfeldes für alle Zeichen- und Binärtypen. Es gibt kein Deskriptorfeld, das diese Informationen für andere Typen enthält.  
  
 Der Anzeigegrößenwert für alle Datentypen entspricht dem Wert in einem einzelnen Deskriptorfeld, SQL_DESC_DISPLAY_SIZE.  
  
 Deskriptorfelder beschreiben die Merkmale eines Resultsets. Deskriptorfelder enthalten keine gültigen Werte für Daten vor der Anweisungsausführung. Die Werte für Spaltengröße, Dezimalstellen und Anzeigegröße, die von **SQLColumns**, **SQLProcedureColumns**und **SQLGetTypeInfo**zurückgegeben werden, geben hingegen Merkmale von Datenbankobjekten, z. B. Tabellenspalten und Datentypen, zurück, die im Katalog der Datenquelle vorhanden sind. Ebenso gibt **SQLColAttribute** in seinem Resultset die Spaltengröße, Dezimalstellen und die Oktettlänge von Spalten in der Datenquelle zurück. Diese Werte sind nicht unbedingt identisch mit den Werten in den Feldern SQL_DESC_PRECISION, SQL_DESC_SCALE und SQL_DESC_OCTET_LENGTH.  
  
 Weitere Informationen zu diesen Deskriptorfeldern finden Sie unter [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Verwandte Themen:  
  
-   [Spaltengröße](../../../odbc/reference/appendixes/column-size.md)  
-   [Dezimalziffern](../../../odbc/reference/appendixes/decimal-digits.md)  
-   [Oktettlänge übertragen](../../../odbc/reference/appendixes/transfer-octet-length.md)  
-   [Anzeigegröße](../../../odbc/reference/appendixes/display-size.md)
