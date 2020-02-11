---
title: Intervall Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- second intervals [ODBC]
- data types [ODBC], interval data types
- interval data type [ODBC]
- day-time intervals [ODBC]
- intervals [ODBC], about intervals
- minute intervals [ODBC]
- day intervals [ODBC]
- year intervals [ODBC]
- month intervals [ODBC]
- interval data type [ODBC], about interval data types
- SQL data types [ODBC], interval
- year-month intervals [ODBC]
- C data types [ODBC], interval
- interval fields [ODBC]
ms.assetid: fba93f65-c1db-44f4-91ba-532f87241cf7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a42c8767228c75d3b7b0da308d739516875cf966
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67947557"
---
# <a name="interval-data-types"></a>Intervalldatentypen
Ein Intervall wird als Differenz zwischen zwei Datums-und Uhrzeiten definiert. Intervalle werden auf eine von zwei Arten ausgedrückt. Eine ist ein *Jahr-Monat-* Intervall, das Intervalle in Bezug auf Jahre und eine ganzzahlige Anzahl von Monaten ausdrückt. Bei der anderen handelt es sich um ein *Zeit* Intervall, das Intervalle in Form von Tagen, Minuten und Sekunden ausdrückt. Diese beiden Arten von Intervallen sind unterschiedlich und können nicht gemischt werden, da Monate eine unterschiedliche Anzahl von Tagen aufweisen können.  
  
 Ein Intervall besteht aus einem Satz von Feldern. Zwischen den Feldern besteht eine implizite Reihenfolge. Beispielsweise wird in einem Jahr-zu-Monat-Intervall zuerst das Jahr gefolgt vom Monat angezeigt. Entsprechend befinden sich die Felder in einem Tag-zu-Minute-Intervall in den Reihenfolge Day, Hour und Minute. Das erste Feld in einem Intervalltyp wird als *führendes* Feld oder das Feld für die *hohe Reihenfolge* bezeichnet. Das letzte Feld wird als *nachfolg* Endes Feld bezeichnet.  
  
 In allen Intervallen wird das führende Feld nicht durch Regeln des gregorianischen Kalenders eingeschränkt. Beispielsweise ist das Stunden Feld in einem Stunden-zu-Minute-Intervall nicht auf einen Wert zwischen 0 und 23 (inklusiv) beschränkt, was normalerweise der Fall ist. Die nachfolgenden Felder, die dem führenden Feld folgen, folgen den üblichen Einschränkungen des gregorianischen Kalenders. Weitere Informationen finden Sie unter [Einschränkungen des gregorianischen Kalenders](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)weiter unten in diesem Anhang.  
  
 Es gibt 13-Intervall-SQL-Datentypen und 13 Interval C-Datentypen. Jeder Datentyp der Interval-C-Datentypen verwendet die gleiche Struktur, SQL_INTERVAL_STRUCT, um die Intervall Daten zu enthalten. (Weitere Informationen finden Sie im nächsten Abschnitt, [C Interval Structure](../../../odbc/reference/appendixes/c-interval-structure.md).) Weitere Informationen zu den SQL-Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md). Weitere Informationen zu den c-Datentypen finden Sie unter [c-Datentypen](../../../odbc/reference/appendixes/c-data-types.md).  
  
|Typbezeichner|Klasse|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|MONTH|Jahr-Monat|Anzahl von Monaten zwischen zwei Datumsangaben.|  
|YEAR|Jahr-Monat|Anzahl von Jahren zwischen zwei Datumsangaben.|  
|YEAR_TO_MONTH|Jahr-Monat|Anzahl von Jahren und Monaten zwischen zwei Datumsangaben.|  
|DAY|Tag-Uhrzeit|Anzahl von Tagen zwischen zwei Datumsangaben.|  
|HOUR|Tag-Uhrzeit|Anzahl der Stunden zwischen zwei Datums-und Uhrzeitangaben.|  
|MINUTE|Tag-Uhrzeit|Anzahl der Minuten zwischen zwei Datums-/Uhrzeitangaben.|  
|SECOND|Tag-Uhrzeit|Anzahl von Sekunden zwischen zwei Datums-/Uhrzeitangaben.|  
|DAY_TO_HOUR|Tag-Uhrzeit|Anzahl der Tage/Stunden zwischen zwei Datums-und Uhrzeitangaben.|  
|DAY_TO_MINUTE|Tag-Uhrzeit|Anzahl der Tage/Stunden/Minuten zwischen zwei Datums-und Uhrzeitangaben.|  
|DAY_TO_SECOND|Tag-Uhrzeit|Anzahl der Tage/Stunden/Minuten/Sekunden zwischen zwei Datums-und Uhrzeitangaben.|  
|HOUR_TO_MINUTE|Tag-Uhrzeit|Anzahl von Stunden/Minuten zwischen zwei Datums-/Uhrzeitangaben.|  
|HOUR_TO_SECOND|Tag-Uhrzeit|Anzahl von Stunden/Minuten/Sekunden zwischen zwei Datums-und Uhrzeitangaben.|  
|MINUTE_TO_SECOND|Tag-Uhrzeit|Anzahl der Minuten/Sekunden zwischen zwei Datums-/Uhrzeitangaben.|  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [C-Intervallstruktur](../../../odbc/reference/appendixes/c-interval-structure.md)  
  
-   [Genauigkeit des Datentyps „Intervall“](../../../odbc/reference/appendixes/interval-data-type-precision.md)  
  
-   [Länge des Datentyps „Intervall“](../../../odbc/reference/appendixes/interval-data-type-length.md)  
  
-   [Intervallliterale](../../../odbc/reference/appendixes/interval-literals.md)  
  
-   [Überschreiben der Standardwerte für die Genauigkeit des führenden Intervallfelds und die Sekundengenauigkeit für Intervalldatentypen](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md)
