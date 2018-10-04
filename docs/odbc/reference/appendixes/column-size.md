---
title: Spaltengröße | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], column size
- size of data types [ODBC]
- SQL data types [ODBC], column characteristics
- column size of data types [ODBC]
ms.assetid: 541b83ab-b16d-4714-bcb2-3c3daa9a963b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22271cd37069123d0e11a3d0ab660134c61e283b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47665538"
---
# <a name="column-size"></a>Spaltengröße
Die Spalte (oder Parameter) die Größe der numerischen Datentypen wird als die maximale Anzahl von Ziffern durch den Datentyp der Spalte oder Parameter oder die Genauigkeit der Daten definiert. Für Zeichentypen handelt ist dies die Länge in Zeichen, der Daten; für binäre Datentypen wird die Spaltengröße als die Länge in Bytes der Daten definiert. Für die Zeit, Timestamp und alle Interval-Datentypen ist dies die Anzahl der Zeichen in die Darstellung dieser Daten. Die Größe der Spalte für jeden präzise SQL-Datentyp definiert, wird in der folgenden Tabelle angezeigt.  
  
|SQL-Typ-ID|Spaltengröße|  
|-------------------------|-----------------|  
|Alle Typen mit Zeichen [a] [b].|Die definierten oder maximale Spaltenlänge Größe in Zeichen der Spalte oder des Parameters (wie in das Deskriptorfeld SQL_DESC_LENGTH enthalten). Die Spaltengröße einer Single-Byte-Zeichen-Spalte, die als CHAR(10) definiert ist z. B. 10.|  
|SQL_DECIMAL SQL_NUMERIC|Die festgelegte Anzahl von Ziffern. Die Genauigkeit einer Spalte, die als NUMERIC(10,3) definiert ist z. B. 10.|  
|SQL_BIT [c]|1|  
|SQL_TINYINT [c]|3|  
|SQL_SMALLINT [c]|5|  
|SQL_INTEGER [c]|10|  
|SQL_BIGINT [c]|19 (falls mit Vorzeichen) oder 20 (falls ohne Vorzeichen)|  
|SQL_REAL [c]|7|  
|SQL_FLOAT [c]|15|  
|SQL_DOUBLE [c]|15|  
|Alle binären Typen [a] [b].|Die definiert oder maximale Länge in Bytes der Spalte oder des Parameters. Die Länge einer Spalte, die als Binary(10)-Wert definiert ist z. B. 10.|  
|SQL_TYPE_DATE [c]|10 (die Anzahl der Zeichen in der *jjjj-mm-tt* Format).|  
|SQL_TYPE_TIME [c]|8 (die Anzahl der Zeichen in der *Hh-mm-ss* Format), oder 9 + *s* (die Anzahl der Zeichen in der *hh: mm:*[: ss. fff...]-Format, in denen *s*ist die Genauigkeit, Sekunden).|  
|SQL_TYPE_TIMESTAMP|16 (die Anzahl der Zeichen in der *jjjj-mm-tt hh: mm* Format)<br /><br /> 19 (die Anzahl der Zeichen in der *jjjj-mm-tt* *hh: mm:* Format)<br /><br /> oder<br /><br /> 20 + *s* (die Anzahl der Zeichen in der *jjjj-mm-tt hh: mm:*[: ss. fff...]-Format, in denen *s* ist die Genauigkeit, Sekunden).|  
|SQL_INTERVAL_SECOND|Wo *p* ist die Genauigkeit für anführenden Intervallwert und *s* ist die Genauigkeit, *p* (Wenn *s*= 0) oder *p* + *s*+ 1 (Wenn *s*> 0). [ d]|  
|SQL_INTERVAL_DAY_TO_SECOND|In denen *p* ist die Genauigkeit für anführenden Intervallwert und *s* ist die Genauigkeit, 9 +*p* (Wenn *s*= 0) oder 10 +*p* + *s* (Wenn *s*> 0). [ d]|  
|SQL_INTERVAL_HOUR_TO_SECOND|In denen *p* ist die Genauigkeit für anführenden Intervallwert und *s* ist die Genauigkeit, 6 +*p* (Wenn *s*= 0) oder 7 +*p* + *s* (Wenn *s*> 0). [ d]|  
|SQL_INTERVAL_MINUTE_TO_SECOND|Wo *p* ist die Genauigkeit für anführenden Intervallwert und *s* ist die Genauigkeit, 3 und höher*p* (Wenn *s*= 0) oder 4 +*p* + *s* (Wenn *s*> 0). [ d]|  
|SQL_INTERVAL_YEAR SQL_INTERVAL_MONTH SQL_INTERVAL_DAY SQL_INTERVAL_HOUR SQL_INTERVAL_MINUTE|*p*, wobei *p* ist die Genauigkeit für anführenden Intervallwert. [ d]|  
|SQL_INTERVAL_YEAR_TO_MONTH SQL_INTERVAL_DAY_TO_HOUR|3 +*p*, wobei *p* ist die Genauigkeit für anführenden Intervallwert. [ d]|  
|SQL_INTERVAL_DAY_TO_MINUTE|6 +*p*, wobei *p* ist die Genauigkeit für anführenden Intervallwert. [ d]|  
|SQL_INTERVAL_HOUR_TO_MINUTE|3 +*p*, wobei *p* ist die Genauigkeit für anführenden Intervallwert. [ d]|  
|SQL_GUID|36 (die Anzahl der Zeichen in der *Aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee* Format)|  
  
 [a] für eine ODBC-1.0-Anwendung aufrufen **SQLSetParam** in ODBC 2.0-Treiber und für einen Aufruf der ODBC 2.0-Anwendung **SQLBindParameter** in einer ODBC-1.0-Treiber beim \*  *StrLen_or_IndPtr* SQL_DATA_AT_EXEC für einen Typ SQL_LONGVARCHAR oder SQL_LONGVARBINARY wird *ColumnSize* muss auf die gesamte Länge der Daten festgelegt werden, gesendet werden soll, nicht die Genauigkeit wie in dieser Tabelle definiert.  
  
 [b] Wenn der Treiber die Länge eines Variablentyps Spalte oder des Parameters nicht ermitteln kann, gibt es SQL_NO_TOTAL zurück.  
  
 [c] die *ColumnSize* Argument **SQLBindParameter** wird für diesen Datentyp ignoriert.  
  
 [d] allgemeiner Regeln für die Länge der Spalte in der Interval-Datentypen, finden Sie unter [Datentyplänge Intervall](../../../odbc/reference/appendixes/interval-data-type-length.md)weiter oben in diesem Anhang.  
  
 Die zurückgegebenen Werte für die Größe der Spalte (oder Parameter) entsprechen nicht den Werten in jeder ein Deskriptorfeld. Die Werte können entweder die SQL_DESC_PRECISION oder Feld SQL_DESC_LENGTH je nach Art der Daten stammen, wie in der folgenden Tabelle gezeigt.  
  
|SQL-Typ|Für Deskriptorfeld<br /><br /> Spalte oder des Parameters-Größe|  
|--------------|--------------------------------------------------------------------|  
|Alle Zeichen- und Binärtypen|LENGTH|  
|Alle numerischen Typen|PRECISION|  
|Alle Datetime "und" Interval-Typen|LENGTH|  
|SQL_BIT|LENGTH|
