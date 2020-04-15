---
title: Spaltengröße | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07b6151c723cb5e05189791100338e9e343c28aa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306581"
---
# <a name="column-size"></a>Spaltengröße
Die Spaltengröße (oder der Parameter) numerischer Datentypen ist definiert als die maximale Anzahl von Ziffern, die vom Datentyp der Spalte oder des Parameters verwendet werden, oder die Genauigkeit der Daten. Bei Zeichentypen ist dies die Länge in Den Zeichen der Daten. Bei binären Datentypen ist die Spaltengröße als Länge in Bytes der Daten definiert. Für die Zeit, den Zeitstempel und alle Intervalldatentypen ist dies die Anzahl der Zeichen in der Zeichendarstellung dieser Daten. Die für jeden kurzen SQL-Datentyp definierte Spaltengröße wird in der folgenden Tabelle angezeigt.  
  
|SQL-Typbezeichner|Spaltengröße|  
|-------------------------|-----------------|  
|Alle Zeichentypen[a],[b]|Die definierte oder maximale Spaltengröße in Zeichen der Spalte oder des Parameters (wie im SQL_DESC_LENGTH Deskriptorfeld enthalten). Beispielsweise ist die Spaltengröße einer Einbyte-Zeichenspalte, die als CHAR(10) definiert ist, 10.|  
|SQL_DECIMAL SQL_NUMERIC|Die definierte Anzahl von Ziffern. Beispielsweise beträgt die Genauigkeit einer Spalte, die als NUMERIC(10,3) definiert ist, 10.|  
|SQL_BIT[c]|1|  
|SQL_TINYINT[c]|3|  
|SQL_SMALLINT[c]|5|  
|SQL_INTEGER[c]|10|  
|SQL_BIGINT[c]|19 (falls unterschrieben) oder 20 (falls nicht unterschrieben)|  
|SQL_REAL[c]|7|  
|SQL_FLOAT[c]|15|  
|SQL_DOUBLE[c]|15|  
|Alle binären Typen[a],[b]|Die definierte oder maximale Länge in Bytes der Spalte oder des Parameters. Beispielsweise beträgt die Länge einer Spalte, die als BINARY(10) definiert ist, 10.|  
|SQL_TYPE_DATE[c]|10 (die Anzahl der Zeichen im *yyyy-mm-dd-Format).*|  
|SQL_TYPE_TIME[c]|8 (die Anzahl der Zeichen im *format hh-mm-ss)* oder 9 + *s* (die Anzahl der Zeichen im *Format hh:mm:ss*[.fff...], wobei *s* die Sekundengenauigkeit ist).|  
|SQL_TYPE_TIMESTAMP|16 (die Anzahl der Zeichen im *Format yyyy-mm-dd hh:mm)*<br /><br /> 19 (die Anzahl der Zeichen im *Yyyy-mm-dd* *hh:mm:ss-Format)*<br /><br /> oder<br /><br /> 20 + *s* (die Anzahl der Zeichen im *Format yyyy-mm-dd hh:mm:ss*[.fff...], wobei *s* die Sekundengenauigkeit ist).|  
|SQL_INTERVAL_SECOND|Wobei *p* das Intervall ist, das die Genauigkeit führt, und *s* die Sekundengenauigkeit, *p* (wenn *s*=0) oder *p*+*s*+1 (wenn *s*>0) ist. [d]|  
|SQL_INTERVAL_DAY_TO_SECOND|Wobei *p* die Intervallführungsgenauigkeit und *s* die Sekundengenauigkeit, 9+*p* (wenn *s*=0) oder 10+*p*+*s* (wenn *s*>0) ist. [d]|  
|SQL_INTERVAL_HOUR_TO_SECOND|Wobei *p* die Intervallführungsgenauigkeit und *s* die Sekundengenauigkeit, 6+*p* (wenn *s*=0) oder 7+*p*+*s* (wenn *s*>0) ist. [d]|  
|SQL_INTERVAL_MINUTE_TO_SECOND|Wobei *p* die Intervallführungsgenauigkeit und *s* die Sekundengenauigkeit, 3+*p* (wenn *s*=0) oder 4+*p*+*s* (wenn *s*>0) ist. [d]|  
|SQL_INTERVAL_YEAR SQL_INTERVAL_MONTH SQL_INTERVAL_DAY SQL_INTERVAL_HOUR SQL_INTERVAL_MINUTE|*p*, wobei *p* die Intervallführungsgenauigkeit ist. [d]|  
|SQL_INTERVAL_YEAR_TO_MONTH SQL_INTERVAL_DAY_TO_HOUR|3+*p*, wobei *p* die Intervall-führende Genauigkeit ist. [d]|  
|SQL_INTERVAL_DAY_TO_MINUTE|6+*p*, wobei *p* die Intervall-führende Genauigkeit ist. [d]|  
|SQL_INTERVAL_HOUR_TO_MINUTE|3+*p*, wobei *p* die Intervall-führende Genauigkeit ist. [d]|  
|SQL_GUID|36 (die Anzahl der Zeichen im *Aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeeeeeeeee)*|  
  
 [a] Für eine ODBC 1.0-Anwendung, die **SQLSetParam** in einem ODBC 2.0-Treiber aufruft, und für eine \*ODBC 2.0-Anwendung, die SQLBindParameter in einem ODBC 1.0-Treiber **aufruft,** muss *ColumnSize* auf die Gesamtlänge der zu sendenden Daten und nicht auf die in dieser Tabelle definierte Genauigkeit festgelegt werden, wenn *StrLen_or_IndPtr* für einen SQL_LONGVARCHAR- oder SQL_LONGVARBINARY-Typ SQL_DATA_AT_EXEC wird.  
  
 [b] Wenn der Treiber die Spalten- oder Parameterlänge für einen Variablentyp nicht bestimmen kann, gibt er SQL_NO_TOTAL zurück.  
  
 [c] Das *ColumnSize-Argument* von **SQLBindParameter** wird für diesen Datentyp ignoriert.  
  
 [d] Allgemeine Regeln zur Spaltenlänge in Intervalldatentypen finden Sie unter [Intervalldatentyplänge](../../../odbc/reference/appendixes/interval-data-type-length.md)weiter oben in diesem Anhang.  
  
 Die für die Spaltengröße (oder Parameter) zurückgegebenen Werte entsprechen nicht den Werten in einem Deskriptorfeld. Die Werte können je nach Datentyp entweder aus dem SQL_DESC_PRECISION oder dem SQL_DESC_LENGTH-Feld stammen, wie in der folgenden Tabelle dargestellt.  
  
|SQL-Typ|Deskriptorfeld entsprechend<br /><br /> Spalten- oder Parametergröße|  
|--------------|--------------------------------------------------------------------|  
|Alle Zeichen- und Binärtypen|LENGTH|  
|Alle numerischen Typen|PRECISION|  
|Alle Datums- und Intervalltypen|LENGTH|  
|SQL_BIT|LENGTH|
