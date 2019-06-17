---
title: Spaltengröße, Dezimalstellen, Oktettlänge Übertragung, Anzeigegröße | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba21e2a13b755c938c8b1bdc321a5f23bf87c29f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63213304"
---
# <a name="column-size-decimal-digits-transfer-octet-length-and-display-size---odbc"></a>Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße - ODBC
Datentypen sind gekennzeichnet durch ihre Größe Spalte (oder Parameter), Dezimalstellen, Länge und Größe angezeigt. Die folgenden ODBC-Funktionen werden diese Attribute für einen Parameter in einer SQL-Anweisung oder eine SQL-Datentyp in einer Datenquelle zurück. Jede ODBC-Funktion gibt einen anderen Satz von diesen Attributen wie folgt aus:  
  
-   **SQLDescribeCol** gibt die Spalte zurück, Größe und Dezimalstelle Ziffern der Spalten beschrieben.  
  
-   **SQLDescribeParam** Größe und Dezimalstelle Ziffern der Parameter, es wird beschrieben, für den Parameter zurück. **SQLBindParameter** legt den Parameter Größe und Dezimalstelle Ziffern für einen Parameter in einer SQL­Anweisung.  
  
-   Die Katalogfunktionen **SQLColumns**, **SQLProcedureColumns**, und **SQLGetTypeInfo** Attribute für eine Spalte in einer Tabelle, Resultsets oder Parameter einer Prozedur zurückgeben und die Katalogattribute der Datentypen in der Datenquelle. **SQLColumns** gibt, die die Spaltengröße, Dezimalstellen und Länge einer Spalte in angegebenen Tabellen (z. B. die Basistabelle, Sicht oder eine Systemtabelle) zurück. **SQLProcedureColumns** gibt die Spaltengröße, Dezimalstellen und Länge einer Spalte in einer Prozedur. **SQLGetTypeInfo** gibt die maximale Spaltengröße und die minimalen und maximalen Dezimalstellen eines SQL-Datentyps in einer Datenquelle zurück.  
  
 Die Werte, die von diesen Funktionen für die Spalte zurückgegeben oder Parametergröße entsprechen "Precision" als in ODBC 2. definiert. *x*. Allerdings entsprechen die Werte nicht unbedingt auf die Werte in SQL_DESC_PRECISION oder einem anderen einen Deskriptorfeld zurückgegeben. Dies gilt auch für die Dezimalstellen, die "Scale" als definiert, in ODBC 2. entsprechen. *x*. Entspricht nicht notwendigerweise um die Rückgabewerte in SQL_DESC_SCALE oder einem anderen einen Deskriptorfeld, sondern stammen aus verschiedenen deskriptorfelder je nach Datentyp. Weitere Informationen finden Sie unter [Spaltengröße](../../../odbc/reference/appendixes/column-size.md) und [Dezimalstellen](../../../odbc/reference/appendixes/decimal-digits.md).  
  
 Auf ähnliche Weise die Werte für Oktettlänge Übertragung nicht SQL_DESC_LENGTH stammen. Sie stammen aus der SQL_DESC_OCTET_LENGTH eines Felds einen Deskriptor für alle Zeichen- und Binärtypen. Es gibt keine Deskriptorfeld, die diese Informationen für andere Typen enthält.  
  
 Der Anzeigewert für die Größe für alle Datentypen entspricht dem Wert in einem einzelnen Beschreibungsfeld SQL_DESC_DISPLAY_SIZE.  
  
 Deskriptorfelder beschreiben die Merkmale eines Resultsets. Deskriptorfelder enthalten keine gültigen Werte zu den Daten vor dem Ausführen der Anweisung. Die Werte für die Spalte Größe, Dezimalziffern und Anzeigegröße zurückgegebenes **SQLColumns**, **SQLProcedureColumns**, und **SQLGetTypeInfo**, auf der anderen hand, zurückgeben Eigenschaften der Datenbankobjekte, z. B. Spalten und Datentypen, vorhanden sein, in der Datenquelle des Katalogs. Ebenso im Resultset **SQLColAttribute** gibt die Spaltengröße, Dezimalstellen und Oktettlänge Übertragung, der Spalten in der Datenquelle; diese Werte sind nicht unbedingt identisch mit den Werten in der SQL_DESC_PRECISION, SQL_ DESC_SCALE und SQL_DESC_OCTET_LENGTH Descriptor-Felder.  
  
 Weitere Informationen zu diesen deskriptorfelder, finden Sie unter [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Verwandte Themen:  
  
-   [Spaltengröße](../../../odbc/reference/appendixes/column-size.md)  
-   [Dezimalziffern](../../../odbc/reference/appendixes/decimal-digits.md)  
-   [Oktettlänge übertragen](../../../odbc/reference/appendixes/transfer-octet-length.md)  
-   [Anzeigegröße](../../../odbc/reference/appendixes/display-size.md)
