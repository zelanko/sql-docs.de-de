---
title: Spaltengröße, Dezimalstellen, Oktettlänge übertragen, Anzeige Größe | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306571"
---
# <a name="column-size-decimal-digits-transfer-octet-length-and-display-size---odbc"></a>Spaltengröße, Dezimalstellen, Oktettlänge übertragen und Anzeige Größe-ODBC
Datentypen werden durch ihre Spaltengröße (oder Parameter Größe), Dezimalziffern, Länge und Anzeige Größe gekennzeichnet. Die folgenden ODBC-Funktionen geben diese Attribute für einen Parameter in einer SQL-Anweisung oder für einen SQL-Datentyp in einer Datenquelle zurück. Jede ODBC-Funktion gibt einen anderen Satz dieser Attribute zurück, wie im folgenden dargestellt:  
  
-   **SQLDescribeCol** gibt die Spaltengröße und die Dezimalstellen der Spalten zurück, die Sie beschreibt.  
  
-   **SQLDescribeParam** gibt die Parameter Größe und die Dezimalstellen der beschriebenen Parameter zurück. **SQLBindParameter** legt die Parameter Größe und Dezimalstellen für einen Parameter in einer SQL-Anweisung fest.  
  
-   Die Katalog Funktionen **SQLColumns**, **sqlprocedurecolrens**und **SQLGetTypeInfo** geben Attribute für eine Spalte in einer Tabelle, einem Resultset oder einem Prozedur Parameter sowie die Katalog Attribute der Datentypen in der Datenquelle zurück. **SQLColumns** gibt die Spaltengröße, Dezimalstellen und Länge einer Spalte in angegebenen Tabellen zurück (z. b. die Basistabelle, die Sicht oder eine Systemtabelle). **Sqlprocedurecolrens** gibt die Spaltengröße, Dezimalziffern und die Länge einer Spalte in einer Prozedur zurück. **SQLGetTypeInfo** gibt die maximale Spaltengröße und die minimalen und maximalen Dezimalstellen eines SQL-Datentyps in einer Datenquelle zurück.  
  
 Die Werte, die von diesen Funktionen für die Spalten-oder Parameter Größe zurückgegeben werden, entsprechen "Precision" gemäß der Definition in ODBC 2. *x*. Die Werte entsprechen jedoch nicht notwendigerweise den Werten, die in SQL_DESC_PRECISION oder einem anderen Deskriptorfeld zurückgegeben werden. Das gleiche gilt für Dezimalstellen, die "Skalierung" entsprechen, wie in ODBC 2 definiert. *x*. Sie entspricht nicht notwendigerweise den Werten, die in SQL_DESC_SCALE oder einem anderen Deskriptorfeld zurückgegeben werden, sondern ist aus unterschiedlichen Deskriptorfeldern abhängig vom Datentyp. Weitere Informationen finden Sie unter [Spaltengröße](../../../odbc/reference/appendixes/column-size.md) und [Dezimalziffern](../../../odbc/reference/appendixes/decimal-digits.md).  
  
 Entsprechend werden die Werte für die Länge der Oktette übertragen nicht von SQL_DESC_LENGTH. Sie stammen aus dem SQL_DESC_OCTET_LENGTH eines Felds eines Deskriptors für alle Zeichen-und Binär Typen. Es gibt kein Deskriptorfeld, das diese Informationen für andere Typen enthält.  
  
 Der Wert für die Anzeige Größe für alle Datentypen entspricht dem Wert in einem einzelnen Deskriptorfeld, SQL_DESC_DISPLAY_SIZE.  
  
 Deskriptorfelder beschreiben die Merkmale eines Resultsets. Deskriptorfelder enthalten keine gültigen Werte zu Daten vor der Anweisungs Ausführung. Die Werte für Spaltengröße, Dezimalstellen und Anzeige Größe, die von **SQLColumns**, **sqlprocedurecolumschlag**und **SQLGetTypeInfo**zurückgegeben werden, geben hingegen Merkmale von Datenbankobjekten (z. b. Tabellen Spalten und Datentypen) zurück, die im Katalog der Datenquelle vorhanden sind. Entsprechend gibt **SQLColAttribute** im Resultset die Spaltengröße, die Dezimalstellen und die Länge von Übertragungs Oktett der Spalten an der Datenquelle zurück. Diese Werte sind nicht notwendigerweise identisch mit den Werten in den Feldern SQL_DESC_PRECISION, SQL_DESC_SCALE und SQL_DESC_OCTET_LENGTH Deskriptor.  
  
 Weitere Informationen zu diesen Deskriptorfeldern finden Sie unter [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Verwandte Themen:  
  
-   [Spaltengröße](../../../odbc/reference/appendixes/column-size.md)  
-   [Dezimalziffern](../../../odbc/reference/appendixes/decimal-digits.md)  
-   [Oktettlänge übertragen](../../../odbc/reference/appendixes/transfer-octet-length.md)  
-   [Anzeigegröße](../../../odbc/reference/appendixes/display-size.md)
