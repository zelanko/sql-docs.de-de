---
title: 'C to SQL: Jahr-Monat-Intervalle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
- data conversions from C to SQL types [ODBC], year-month intervals
ms.assetid: a0eb7b55-9db0-4375-9210-bddec4593880
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d12727f9298eb63fe10b44c48b9d3b7996a839d5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692768"
---
# <a name="c-to-sql-year-month-intervals"></a>C zu SQL: Jahr-Monat-Intervalle
Der Bezeichner für die Jahr-Monat-Intervall ODBC C-Datentypen sind:  
  
 SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR_TO_MONTH  
  
 Die folgende Tabelle zeigt die ODBC-SQL-Datentypen, die Jahr-Monat-C Intervalldaten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typ-ID|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR [a]<br /><br /> SQL_VARCHAR [a]<br /><br /> SQL_LONGVARCHAR [a]|Spalte-Byte-Länge > = Zeichen-Byte-Länge<br /><br /> Byte-Länge der Spalte < Zeichen Länge in Byte [a]<br /><br /> Datenwert ist es sich nicht um ein gültiges Intervall-Literale|–<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR [a]<br /><br /> SQL_WVARCHAR [a]<br /><br /> SQL_WLONGVARCHAR [a]|Spalte Zeichenlänge > = Zeichenlänge der Daten<br /><br /> Spaltenlänge für die Zeichen < Zeichen Länge der Daten [a]<br /><br /> Datenwert ist es sich nicht um ein gültiges Intervall-Literale|–<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b]<br /><br /> SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b]<br /><br /> SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|Konvertierung von einem Intervall von einem einzigen Feld führten nicht Abschneiden von ganzen Zahlen<br /><br /> Konvertierung führte Abschneiden von ganzen Zahlen|–<br /><br /> 22003|  
|SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_YEAR_TO_MONTH|Der Datenwert wurde ohne Abschneiden von Feldern konvertiert.<br /><br /> Ein oder mehrere Felder der Datenwert wurde während der Konvertierung abgeschnitten.|–<br /><br /> 22015|  
  
 [a] alle C-Interval-Datentypen können in einen Zeichendatentyp konvertiert werden.  
  
 [b] ist das Typfeld in die Intervall-Struktur, für die das Intervall ein einzelnes Feld (SQL_YEAR oder SQL_MONTH) entspricht, kann der Intervalltyp C in jedem genauer numerischer Wert (SQL_TINYINT SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL oder SQL_NUMERIC) konvertiert werden.  
  
 Die standardkonvertierung eines Intervalls C-Typ ist für das entsprechende Jahr-Monat-Intervall SQL-Typ.  
  
 Der Treiber ignoriert den Längenindikator /-Wert, bei der Konvertierung von Daten aus dem Intervall C-Datentyp, und es wird davon ausgegangen, dass die Größe des Datenpuffers die Größe des Datentyps Interval C. Der Längenindikator /-Wert übergeben wird die *StrLen_or_Ind* -Argument in **SQLPutData** und in den Puffer, der mit angegebenen die *StrLen_or_IndPtr* -Argument in **SQLBindParameter**. Der Datenpuffer wird angegeben, mit der *DataPtr* -Argument in **SQLPutData** und die *ParameterValuePtr* -Argument in **SQLBindParameter**.
