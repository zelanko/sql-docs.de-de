---
title: 'C zu SQL: Jahres-Monatsintervalle | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2ec7bfda0015883c8470dd453c7ae5de9bfd6cec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306611"
---
# <a name="c-to-sql-year-month-intervals"></a>C zu SQL: Jahr-Monat-Intervalle
Die Bezeichner für das Jahresmonatsintervall ODBC C-Datentypen sind:  
  
 SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR_TO_MONTH  
  
 Die folgende Tabelle zeigt die ODBC SQL-Datentypen, in die Jahresintervall C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR[a]<br /><br /> SQL_VARCHAR[a]<br /><br /> SQL_LONGVARCHAR[a]|Spaltenbytelänge >= Zeichenbytelänge<br /><br /> Spaltenbytelänge < Zeichenbytelänge[a]<br /><br /> Der Datenwert ist kein gültiges Intervallliteral|–<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR[a]<br /><br /> SQL_WVARCHAR[a]<br /><br /> SQL_WLONGVARCHAR[a]|Spaltenzeichenlänge >= Zeichenlänge der Daten<br /><br /> Spaltenzeichenlänge < Zeichenlänge der Daten[a]<br /><br /> Der Datenwert ist kein gültiges Intervallliteral|–<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT[b]<br /><br /> SQL_SMALLINT[b]<br /><br /> SQL_INTEGER[b]<br /><br /> SQL_BIGINT[b]<br /><br /> SQL_NUMERIC[b]<br /><br /> SQL_DECIMAL[b]|Die Konvertierung eines Einfeldintervalls hat nicht dazu geführt, dass ganze Ziffern abgeschnitten wurden.<br /><br /> Konvertierung führte zum Abschneiden ganzer Ziffern|–<br /><br /> 22003|  
|SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_YEAR_TO_MONTH|Der Datenwert wurde ohne Abschneiden von Feldern konvertiert.<br /><br /> Mindestens ein Datenwertfeld wurde während der Konvertierung abgeschnitten|–<br /><br /> 22015|  
  
 [a] Alle C-Intervalldatentypen können in einen Zeichendatentyp konvertiert werden.  
  
 [b] Wenn das Typfeld in der Intervallstruktur so ist, dass das Intervall ein einzelnes Feld ist (SQL_YEAR oder SQL_MONTH), kann der Intervall-C-Typ in eine beliebige exakte Numerische (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL oder SQL_NUMERIC) konvertiert werden.  
  
 Die Standardkonvertierung eines Intervall-C-Typs ist der entsprechende Jahres-Monats-Intervall-SQL-Typ.  
  
 Der Treiber ignoriert den Längen-/Indikatorwert beim Konvertieren von Daten aus dem Intervall-C-Datentyp und geht davon aus, dass die Größe des Datenpuffers die Größe des Intervall-C-Datentyps ist. Der Längen-/Indikatorwert wird im *Argument StrLen_or_Ind* in **SQLPutData** und im Puffer übergeben, der mit dem *Argument StrLen_or_IndPtr* in **SQLBindParameter**angegeben ist. Der Datenpuffer wird mit dem *DataPtr-Argument* in **SQLPutData** und dem *ParameterValuePtr-Argument* in **SQLBindParameter**angegeben.
