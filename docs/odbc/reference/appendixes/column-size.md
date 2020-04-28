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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07b6151c723cb5e05189791100338e9e343c28aa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306581"
---
# <a name="column-size"></a>Spaltengröße
Die Größe der Spalte (oder des Parameters) numerischer Datentypen wird als maximale Anzahl von Ziffern definiert, die vom Datentyp der Spalte oder des Parameters oder der Genauigkeit der Daten verwendet werden. Bei Zeichen Typen ist dies die Länge der Daten in Zeichen. für binäre Datentypen wird die Spaltengröße als die Länge der Daten in Byte definiert. Bei den Datentypen Time, timestamp und all Interval ist dies die Anzahl der Zeichen in der Zeichen Darstellung dieser Daten. Die Spaltengröße, die für jeden präzisen SQL-Datentyp definiert ist, ist in der folgenden Tabelle dargestellt.  
  
|SQL-Typbezeichner|Spaltengröße|  
|-------------------------|-----------------|  
|Alle Zeichen Typen [a], [b]|Die definierte oder maximale Spaltengröße in Zeichen der Spalte oder des Parameters (wie im Feld SQL_DESC_LENGTH Deskriptor enthalten). Beispielsweise ist die Spaltengröße einer Einzel Byte-Zeichenspalte, die als char (10) definiert ist, 10.|  
|SQL_DECIMAL SQL_NUMERIC|Die definierte Anzahl von Ziffern. Beispielsweise ist die Genauigkeit einer Spalte, die als numerisch (10, 3) definiert ist, 10.|  
|SQL_BIT [c]|1|  
|SQL_TINYINT [c]|3|  
|SQL_SMALLINT [c]|5|  
|SQL_INTEGER [c]|10|  
|SQL_BIGINT [c]|19 (falls signiert) oder 20 (wenn nicht signiert)|  
|SQL_REAL [c]|7|  
|SQL_FLOAT [c]|15|  
|SQL_DOUBLE [c]|15|  
|Alle binären Typen [a], [b]|Die definierte oder maximale Länge der Spalte oder des Parameters in Byte. Beispielsweise ist die Länge einer Spalte, die als "Binary (10)" definiert ist, 10.|  
|SQL_TYPE_DATE [c]|10 (die Anzahl der Zeichen im Format *yyyy-mm-dd* ).|  
|SQL_TYPE_TIME [c]|8 (die Anzahl der Zeichen im Format *hh-mm-SS* ) oder 9 + *s* (die Anzahl der Zeichen im Format *hh: mm: SS*[. fff...], wobei *s* die Genauigkeit von Sekunden ist).|  
|SQL_TYPE_TIMESTAMP|16 (die Anzahl der Zeichen im Format *yyyy-mm-dd hh: mm* )<br /><br /> 19 (die Anzahl der Zeichen im Format *yyyy-mm-dd* *hh: mm: SS* )<br /><br /> oder<br /><br /> 20 + *s* (die Anzahl der Zeichen im Format *yyyy-mm-dd hh: mm: SS*[. fff...], wobei *s* die Genauigkeit von Sekunden ist).|  
|SQL_INTERVAL_SECOND|Dabei *steht p* für die angegebene Intervall Genauigkeit und *s* für die Sekunden Genauigkeit, *p* (wenn *s*= 0) oder *p*+*s*+ 1 (wenn *s*>0). d|  
|SQL_INTERVAL_DAY_TO_SECOND|Dabei steht *p* für das Intervall mit der führenden Genauigkeit und *s* für die Sekunden Genauigkeit, 9 +*p* (wenn *s*= 0) oder 10 +*p*+*s* (wenn *s*>0). d|  
|SQL_INTERVAL_HOUR_TO_SECOND|Dabei ist *p* das Intervall, das die Genauigkeit angibt, und *s* ist die Sekunden Genauigkeit, 6 +*p* (wenn *s*= 0) oder 7 +*p*+*s* (wenn *s*>0). d|  
|SQL_INTERVAL_MINUTE_TO_SECOND|Dabei steht *p* für das Intervall mit der führenden Genauigkeit und *s* für die Sekunden Genauigkeit, 3 +*p* (wenn *s*= 0) oder 4 +*p*+*s* (wenn *s*>0). d|  
|SQL_INTERVAL_YEAR SQL_INTERVAL_MONTH SQL_INTERVAL_DAY SQL_INTERVAL_HOUR SQL_INTERVAL_MINUTE|*p*, wobei *p* die für das Intervall führende Genauigkeit ist. d|  
|SQL_INTERVAL_YEAR_TO_MONTH SQL_INTERVAL_DAY_TO_HOUR|3 +*p*, wobei *p* die für das Intervall führende Genauigkeit ist. d|  
|SQL_INTERVAL_DAY_TO_MINUTE|6 +*p*, wobei *p* die für das Intervall führende Genauigkeit ist. d|  
|SQL_INTERVAL_HOUR_TO_MINUTE|3 +*p*, wobei *p* die für das Intervall führende Genauigkeit ist. d|  
|SQL_GUID|36 (die Anzahl der Zeichen im *aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee* -Format)|  
  
 [a] für eine ODBC 1,0-Anwendung, die **SQLSetParam** in einem ODBC 2,0-Treiber aufruft, und für eine ODBC 2,0-Anwendung, die **SQLBindParameter** in einem \*ODBC-1,0-Treiber aufruft, wenn *StrLen_or_IndPtr* für einen SQL_LONGVARCHAR oder SQL_LONGVARBINARY Typ SQL_DATA_AT_EXEC wird, muss *ColumnSize* auf die Gesamtlänge der zu sendenden Daten festgelegt werden, nicht auf  
  
 [b] Wenn der Treiber die Spalten-oder Parameter Länge für einen Variablentyp nicht bestimmen kann, wird SQL_NO_TOTAL zurückgegeben.  
  
 [c] das *ColumnSize* -Argument von **SQLBindParameter** wird für diesen Datentyp ignoriert.  
  
 [d] allgemeine Regeln zur Spaltenlänge in den Intervall Datentypen finden Sie unter [Intervall Datentyp Länge](../../../odbc/reference/appendixes/interval-data-type-length.md)weiter oben in diesem Anhang.  
  
 Die Werte, die für die Spaltengröße (oder Parameter) zurückgegeben werden, entsprechen nicht den Werten in einem Deskriptorfeld. Die Werte können je nach Datentyp entweder aus dem SQL_DESC_PRECISION oder dem Feld SQL_DESC_LENGTH stammen, wie in der folgenden Tabelle dargestellt.  
  
|SQL-Typ|Deskriptorfeld, das entspricht<br /><br /> Spalten-oder Parameter Größe|  
|--------------|--------------------------------------------------------------------|  
|Alle Zeichen-und Binär Typen|LENGTH|  
|Alle numerischen Typen|PRECISION|  
|Alle DateTime-und Interval-Typen|LENGTH|  
|SQL_BIT|LENGTH|
