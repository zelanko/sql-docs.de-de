---
title: 'C zu SQL: Numerisch | Microsoft Docs'
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304731"
---
# <a name="c-to-sql-numeric"></a>C zu SQL: numerisch
Die Bezeichner für die numerischen ODBC C-Datentypen sind:  
  
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
  
 Die folgende Tabelle zeigt die ODBC SQL-Datentypen, in die numerische C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Anzahl der Ziffern <= Spaltenbytelänge<br /><br /> Anzahl der Ziffern > Spaltenbytelänge|–<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Anzahl der Zeichen <= Spaltenzeichenlänge<br /><br /> Anzahl der Zeichen > Spaltenzeichenlänge|–<br /><br /> 22001|  
|SQL_DECIMAL[b]<br /><br /> SQL_NUMERIC[b]<br /><br /> SQL_TINYINT[b]<br /><br /> SQL_SMALLINT[b]<br /><br /> SQL_INTEGER[b]<br /><br /> SQL_BIGINT[b]|Daten, die ohne Abschneiden oder mit abgeschnittenen Bruchziffern konvertiert werden<br /><br /> Daten, die mit Abschneiden ganzer Ziffern konvertiert wurden|–<br /><br /> 22003|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Die Daten liegen im Bereich des Datentyps, in den die Nummer konvertiert wird.<br /><br /> Die Daten liegen außerhalb des Bereichs des Datentyps, in den die Nummer konvertiert wird.|–<br /><br /> 22003|  
|SQL_BIT|Die Daten sind 0 oder 1<br /><br /> Die Daten sind größer als 0, kleiner als 2 und nicht gleich 1<br /><br /> Die Daten sind kleiner als 0 oder größer oder gleich 2|–<br /><br /> 22001<br /><br /> 22003|  
|SQL_INTERVAL_YEAR[a]<br /><br /> SQL_INTERVAL_MONTH[a]<br /><br /> SQL_INTERVAL_DAY[a]<br /><br /> SQL_INTERVAL_HOUR[a]<br /><br /> SQL_INTERVAL_MINUTE[a]<br /><br /> SQL_INTERVAL_SECOND[a]|Daten wurden nicht abgeschnitten.<br /><br /> Daten abgeschnitten.|–<br /><br /> 22015|  
  
 [a] Diese Konvertierungen werden nur für die genauen numerischen Datentypen (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_SSHORT, SQL_C_USHORT, SQL_C_SLONG, SQL_C_ULONG oder SQL_C_NUMERIC) unterstützt. Sie werden für die ungefähren numerischen Datentypen (SQL_C_FLOAT oder SQL_C_DOUBLE) nicht unterstützt. Exakte numerische C-Datentypen können nicht in einen Intervall-SQL-Typ konvertiert werden, dessen Intervallgenauigkeit kein einzelnes Feld ist.  
  
 [b] Für den Fall "n/a" kann ein Treiber optional SQL_SUCCESS_WITH_INFO und 01S07 zurückgeben, wenn es eine fraktionierte Kürzung gibt.  
  
 Der Treiber ignoriert den Längen-/Indikatorwert beim Konvertieren von Daten aus den numerischen C-Datentypen und geht davon aus, dass die Größe des Datenpuffers die Größe des numerischen C-Datentyps ist. Der Längen-/Indikatorwert wird im *Argument StrLen_or_Ind* in **SQLPutData** und im Puffer übergeben, der mit dem *Argument StrLen_or_IndPtr* in **SQLBindParameter**angegeben ist. Der Datenpuffer wird mit dem *DataPtr-Argument* in **SQLPutData** und dem *ParameterValuePtr-Argument* in **SQLBindParameter**angegeben.
