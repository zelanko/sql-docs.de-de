---
title: 'C zu SQL: numerisch | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], converting
- data conversions from C to SQL types [ODBC], numeric
- converting data from c to SQL types [ODBC], numeric
ms.assetid: af4095ff-06c3-4b04-83bf-19f9ee098dc2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbc0a994ef95f2deca29c8a4cbb06f3167b0433f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304731"
---
# <a name="c-to-sql-numeric"></a>C zu SQL: numerisch
Die Bezeichner für die numerischen ODBC-C-Datentypen lauten wie folgt:  
  
 SQL_C_STINYINT  
  
 SQL_C_SLONG  
  
 SQL_C_UTINYINT  
  
 SQL_C_ULONG  
  
 SQL_C_TINYINT  
  
 SQL_C_LONG  
  
 SQL_C_SSHORT  
  
 SQL_C_FLOAT  
  
 SQL_C_USHORT  
  
 SQL_C_DOUBLE  
  
 SQL_C_SHORT  
  
 SQL_C_NUMERIC  
  
 SQL_C_SBIGINT  
  
 SQL_C_UBIGINT  
  
 In der folgenden Tabelle werden die ODBC-SQL-Datentypen angezeigt, in die numerische C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Anzahl der Ziffern <= Spalten Byte Länge<br /><br /> Anzahl von Ziffern > Spalten Byte Länge|Nicht zutreffend<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Anzahl von Zeichen <= Länge von Spalten Zeichen<br /><br /> Anzahl von Zeichen > Spalten Zeichenlänge|Nicht zutreffend<br /><br /> 22001|  
|SQL_DECIMAL [b]<br /><br /> SQL_NUMERIC [b]<br /><br /> SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b]<br /><br /> SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b]|Daten, die ohne abschneiden oder durch Abschneiden von Bruch Ziffern konvertiert werden<br /><br /> Mit abschneiden ganzer Ziffern konvertierte Daten|Nicht zutreffend<br /><br /> 22003|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Die Daten befinden sich innerhalb des Bereichs des Datentyps, in den die Zahl konvertiert wird.<br /><br /> Die Daten liegen außerhalb des Bereichs des Datentyps, in den die Zahl konvertiert wird.|Nicht zutreffend<br /><br /> 22003|  
|SQL_BIT|Die Daten sind 0 oder 1.<br /><br /> Die Daten sind größer als 0 (null), kleiner als 2, nicht gleich 1.<br /><br /> Daten sind kleiner als 0 (null) oder größer oder gleich 2.|Nicht zutreffend<br /><br /> 22001<br /><br /> 22003|  
|SQL_INTERVAL_YEAR [a]<br /><br /> SQL_INTERVAL_MONTH [a]<br /><br /> SQL_INTERVAL_DAY [a]<br /><br /> SQL_INTERVAL_HOUR [a]<br /><br /> SQL_INTERVAL_MINUTE [a]<br /><br /> SQL_INTERVAL_SECOND [a]|Daten werden nicht abgeschnitten.<br /><br /> Die Daten wurden abgeschnitten.|Nicht zutreffend<br /><br /> 22015|  
  
 [a] Diese Konvertierungen werden nur für die genauen numerischen Datentypen (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_SSHORT, SQL_C_USHORT, SQL_C_SLONG, SQL_C_ULONG oder SQL_C_NUMERIC) unterstützt. Sie werden für die ungefähren numerischen Datentypen (SQL_C_FLOAT oder SQL_C_DOUBLE) nicht unterstützt. Exakte numerische C-Datentypen können nicht in einen SQL-Intervalltyp konvertiert werden, dessen Intervall Genauigkeit kein einzelnes Feld ist.  
  
 [b] für den "n/a"-Fall kann ein Treiber optional SQL_SUCCESS_WITH_INFO und 01s07 zurückgeben, wenn ein Abschneiden in Sekundenbruchteilen vorliegt.  
  
 Der Treiber ignoriert den Längen-/indikatorenwert beim Umrechnen von Daten aus den numerischen c-Datentypen und geht davon aus, dass die Größe des Daten Puffers die Größe des numerischen c-Datentyps ist. Der Wert für die Länge/den Indikator wird im *StrLen_Or_Ind* -Argument in **SQLPutData** und in dem Puffer übergeben, der mit dem *StrLen_or_IndPtr* -Argument in **SQLBindParameter**angegeben wird. Der Datenpuffer wird mit dem *DataPtr* -Argument in **SQLPutData** und dem *ParameterValuePtr* -Argument in **SQLBindParameter**angegeben.
