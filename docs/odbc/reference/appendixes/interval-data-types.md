---
title: Interval-Datentypen | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 930a848ea01d128cb248c7929408ce7510937ad9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622218"
---
# <a name="interval-data-types"></a>Intervalldatentypen
Ein Intervall wird als die Differenz zwischen zwei Datumsangaben und Uhrzeiten definiert. Intervalle werden in zwei unterschiedliche Arten ausgedrückt werden. Eine ist ein *Jahr-Monat* Intervall, die Intervalle in Jahren und eine ganzzahlige Anzahl von Monaten ausdrückt. Die andere ist eine *Day-Time-* Intervall, die Intervalle in Tagen, Minuten und Sekunden ausdrückt. Diese beiden Arten von Intervallen zielteilmengen verschieden und können nicht kombiniert werden, da Monate unterschiedliche Anzahl von Tagen haben können.  
  
 Ein Intervall besteht aus einem Satz von Feldern. Es gibt eine implizite Reihenfolge der Felder. Beispielsweise wird in einem Jahr-auf-Monats-Intervall, das Jahr zuerst angegeben, gefolgt von den Monat. Auf ähnliche Weise werden die Felder in eine Tag-zu-Minuten-Intervall, in die Reihenfolge Tag, Stunde und Minute. Das erste Feld in einem Intervalltyp wird aufgerufen, die *führende* Feld oder die *höherwertigen* Feld. Wird aufgerufen, das letzte Feld der *nachfolgende* Feld.  
  
 In alle Intervalle ist das führende Feld durch Regeln des gregorianischen Kalenders nicht eingeschränkt. Beispielsweise wird in einer Stunde-zu-Minuten-Intervall, dem Stundenfeld nicht eingeschränkt, zwischen 0 und 23 (inklusiv), werden, da es normalerweise der Fall ist. Die nachfolgende Felder nach Feld führende führen Sie die üblichen Einschränkungen des gregorianischen Kalenders. Weitere Informationen finden Sie unter [Einschränkungen des gregorianischen Kalenders](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)weiter unten in diesem Anhang.  
  
 Es gibt 13 Interval SQL-Datentypen und 13 Interval C-Datentypen. Jede der Intervalldatentypen C verwendet die gleiche Struktur SQL_INTERVAL_STRUCT, die Intervalldaten enthalten. (Weitere Informationen finden Sie im nächsten Abschnitt [C-Intervall-Struktur](../../../odbc/reference/appendixes/c-interval-structure.md).) Weitere Informationen zu den SQL-Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md); Weitere Informationen zu den C-Datentypen finden Sie unter [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md).  
  
|Typ-ID|Class|Description|  
|---------------------|-----------|-----------------|  
|MONTH|Jahr-Monat|Anzahl der Monate zwischen zwei Datumsangaben.|  
|YEAR|Jahr-Monat|Anzahl der Jahre zwischen zwei Datumsangaben.|  
|YEAR_TO_MONTH|Jahr-Monat|Anzahl von Jahren und Monaten zwischen zwei Datumsangaben.|  
|DAY|Day-Time|Anzahl von Tagen zwischen zwei Datumsangaben.|  
|HOUR|Day-Time|Anzahl der Stunden zwischen zwei Datumsangaben und Uhrzeiten.|  
|MINUTE|Day-Time|Anzahl der Minuten zwischen zwei Datumsangaben und Uhrzeiten.|  
|SECOND|Day-Time|Anzahl der Sekunden zwischen zwei Datumsangaben und Uhrzeiten.|  
|DAY_TO_HOUR|Day-Time|Anzahl der datenbanktage/-Stunden zwischen zwei Datumsangaben und Uhrzeiten.|  
|DAY_TO_MINUTE|Day-Time|Anzahl der Tage/Stunden/Minuten zwischen zwei Datumsangaben und Uhrzeiten.|  
|DAY_TO_SECOND|Day-Time|Anzahl von Tagen Stunden/Minuten/Sekunden zwischen zwei Datumsangaben und Uhrzeiten.|  
|HOUR_TO_MINUTE|Day-Time|Anzahl der Stunden/Minuten zwischen zwei Datumsangaben und Uhrzeiten.|  
|HOUR_TO_SECOND|Day-Time|Anzahl der Stunden/Minuten/Sekunden zwischen zwei Datumsangaben und Uhrzeiten.|  
|MINUTE_TO_SECOND|Day-Time|Anzahl von Minuten/Sekunden zwischen zwei Datumsangaben und Uhrzeiten.|  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [C-Intervall-Struktur](../../../odbc/reference/appendixes/c-interval-structure.md)  
  
-   [Datentypgenauigkeit Intervall](../../../odbc/reference/appendixes/interval-data-type-precision.md)  
  
-   [Datentyplänge Intervall](../../../odbc/reference/appendixes/interval-data-type-length.md)  
  
-   [Intervall-Literale](../../../odbc/reference/appendixes/interval-literals.md)  
  
-   [Overriding Default Leading and Seconds Precision for Interval Data Types (Überschreiben von standardmäßigen anführender Präzision und Genauigkeit in Sekunden für Intervalldatentypen)](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md)
