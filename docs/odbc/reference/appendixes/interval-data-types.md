---
title: Intervalldatentypen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ee4a6e845e0bc0830f514b2e768075dd75bcf6e6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304966"
---
# <a name="interval-data-types"></a>Intervalldatentypen
Ein Intervall ist definiert als die Differenz zwischen zwei Datumsangaben und Uhrzeiten. Intervalle werden auf zwei verschiedene Arten ausgedrückt. Eines davon ist ein *Jahres-Monats-Intervall,* das Intervalle in Jahren und einer integralen Anzahl von Monaten ausdrückt. Das andere ist ein *Tagesintervall,* das Intervalle in Tagen, Minuten und Sekunden ausdrückt. Diese beiden Arten von Intervallen sind unterschiedlich und können nicht gemischt werden, da Monate unterschiedliche Anzahl von Tagen haben können.  
  
 Ein Intervall besteht aus einer Reihe von Feldern. Es gibt eine implizite Reihenfolge unter den Feldern. In einem Intervall von Jahr zu Monat steht beispielsweise das Jahr an erster Stelle, gefolgt vom Monat. Ebenso befinden sich die Felder in einem Täglichen-Minuten-Intervall in der Reihenfolge Tag, Stunde und Minute. Das erste Feld in einem Intervalltyp wird als *führendes* Feld oder als Feld *mit hoher Ordnung* bezeichnet. Das letzte Feld wird als *Nachtrailingfeld* bezeichnet.  
  
 In allen Intervallen ist das führende Feld nicht durch Regeln des Gregorianischen Kalenders eingeschränkt. Beispielsweise ist das Stundenfeld in einem Stunden-zu-Minuten-Intervall nicht darauf beschränkt, zwischen 0 und 23 (inklusive) zu liegen, wie es normalerweise der Fall ist. Die nachfolgenden Felder nach dem führenden Feld folgen den üblichen Einschränkungen des Gregorianischen Kalenders. Weitere Informationen finden Sie unter [Einschränkungen des Gregorianischen Kalenders](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)weiter unten in diesem Anhang.  
  
 Es gibt 13 Intervall-SQL-Datentypen und 13 Intervall-C-Datentypen. Jeder der Intervall-C-Datentypen verwendet dieselbe Struktur, SQL_INTERVAL_STRUCT, um die Intervalldaten zu enthalten. (Weitere Informationen finden Sie im nächsten [Abschnitt, C-Intervallstruktur](../../../odbc/reference/appendixes/c-interval-structure.md).) Weitere Informationen zu den SQL-Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md); Weitere Informationen zu den C-Datentypen finden Sie unter [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md).  
  
|Typbezeichner|Klasse|Beschreibung|  
|---------------------|-----------|-----------------|  
|MONTH|Jahr-Monat|Anzahl der Monate zwischen zwei Datumsangaben.|  
|YEAR|Jahr-Monat|Anzahl der Jahre zwischen zwei Datumsangaben.|  
|YEAR_TO_MONTH|Jahr-Monat|Anzahl der Jahre und Monate zwischen zwei Datumsangaben.|  
|DAY|Tag-Zeit|Anzahl der Tage zwischen zwei Datumsangaben.|  
|HOUR|Tag-Zeit|Anzahl der Stunden zwischen zwei Datums-/Uhrzeiten.|  
|MINUTE|Tag-Zeit|Anzahl der Minuten zwischen zwei Datums-/Uhrzeiten.|  
|SECOND|Tag-Zeit|Anzahl der Sekunden zwischen zwei Datums-/Uhrzeiten.|  
|DAY_TO_HOUR|Tag-Zeit|Anzahl der Tage/Stunden zwischen zwei Datums-/Uhrzeiten.|  
|DAY_TO_MINUTE|Tag-Zeit|Anzahl der Tage/Stunden/Minuten zwischen zwei Datums-/Uhrzeiten.|  
|DAY_TO_SECOND|Tag-Zeit|Anzahl der Tage/Stunden/Minuten/Sekunden zwischen zwei Datums-/Uhrzeiten.|  
|HOUR_TO_MINUTE|Tag-Zeit|Anzahl der Stunden/Minuten zwischen zwei Datums-/Uhrzeiten.|  
|HOUR_TO_SECOND|Tag-Zeit|Anzahl der Stunden/Minuten/Sekunden zwischen zwei Datums-/Uhrzeiten.|  
|MINUTE_TO_SECOND|Tag-Zeit|Anzahl der Minuten/Sekunden zwischen zwei Datums-/Uhrzeiten.|  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [C-Intervall-Struktur](../../../odbc/reference/appendixes/c-interval-structure.md)  
  
-   [Datentypgenauigkeit Intervall](../../../odbc/reference/appendixes/interval-data-type-precision.md)  
  
-   [Datentyplänge Intervall](../../../odbc/reference/appendixes/interval-data-type-length.md)  
  
-   [Intervall-Literale](../../../odbc/reference/appendixes/interval-literals.md)  
  
-   [Overriding Default Leading and Seconds Precision for Interval Data Types (Überschreiben von standardmäßigen anführender Präzision und Genauigkeit in Sekunden für Intervalldatentypen)](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md)
