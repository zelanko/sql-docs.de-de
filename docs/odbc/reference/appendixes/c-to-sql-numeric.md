---
title: 'C in SQL: Numerische | Microsoft-Dokumentation'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 816394bb8469148504c1b2b416e77fec814bef8f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63191737"
---
# <a name="c-to-sql-numeric"></a>C in SQL: Numerisch
Der Bezeichner für die numerische ODBC-C-Datentypen sind:  
  
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
  
 Die folgende Tabelle zeigt die ODBC-SQL-Datentypen, die in denen numerische C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typ-ID|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Anzahl der Ziffern < = Spalte-Byte-Länge<br /><br /> Anzahl der Ziffern > Spalte-Byte-Länge|–<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Anzahl der Zeichen < Zeichen Spaltenlänge =<br /><br /> Anzahl von Zeichen > Zeichen Spaltenlänge|–<br /><br /> 22001|  
|SQL_DECIMAL[b]<br /><br /> SQL_NUMERIC[b]<br /><br /> SQL_TINYINT[b]<br /><br /> SQL_SMALLINT[b]<br /><br /> SQL_INTEGER[b]<br /><br /> SQL_BIGINT[b]|Daten ohne Abschneiden konvertiert oder der Dezimalstellen gekürzt<br /><br /> Daten, die mit Abschneiden von ganzen Zahlen konvertiert|–<br /><br /> 22003|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Daten sind innerhalb des Bereichs des Datentyps, der die Anzahl konvertiert wird<br /><br /> Daten sind außerhalb des Bereichs des Datentyps, der die Anzahl konvertiert wird|–<br /><br /> 22003|  
|SQL_BIT|Daten sind 0 oder 1<br /><br /> Daten ist größer als 0 ist, kleiner als 2, und nicht gleich-1<br /><br /> Daten ist kleiner als 0 oder größer als oder gleich 2|–<br /><br /> 22001<br /><br /> 22003|  
|SQL_INTERVAL_YEAR[a]<br /><br /> SQL_INTERVAL_MONTH[a]<br /><br /> SQL_INTERVAL_DAY[a]<br /><br /> SQL_INTERVAL_HOUR[a]<br /><br /> SQL_INTERVAL_MINUTE[a]<br /><br /> SQL_INTERVAL_SECOND[a]|Die Daten nicht abgeschnitten.<br /><br /> Daten wurden abgeschnitten.|–<br /><br /> 22015|  
  
 [a] diese Konvertierungen werden nur für die genaue numerische Datentypen (SQL_C_STINYINT SQL_C_UTINYINT, SQL_C_SSHORT, SQL_C_USHORT, SQL_C_SLONG, SQL_C_ULONG oder SQL_C_NUMERIC) unterstützt. Sie sind nicht für die ungefähre numerische Datentypen (SQL_C_FLOAT oder SQL_C_DOUBLE) unterstützt. Genaue numerische C-Datentypen können nicht auf ein Intervall von SQL-Typ konvertiert werden, deren Genauigkeit Intervall kein einzelnes Feld handelt.  
  
 [b] für den Fall "n/v" möglicherweise ein Treiber optional zurückgeben SQL_SUCCESS_WITH_INFO und 01 s 07 bei einem Teilbereiche wurden abgeschnitten.  
  
 Der Treiber ignoriert den Längenindikator /-Wert, beim Konvertieren von Daten aus der numerischen C-Datentypen, und es wird davon ausgegangen, dass die Größe des Datenpuffers die Größe des numerischen Datentyps C. Der Längenindikator /-Wert übergeben wird die *StrLen_or_Ind* -Argument in **SQLPutData** und in den Puffer, der mit angegebenen die *StrLen_or_IndPtr* -Argument in **SQLBindParameter**. Der Datenpuffer wird angegeben, mit der *DataPtr* -Argument in **SQLPutData** und die *ParameterValuePtr* -Argument in **SQLBindParameter**.
