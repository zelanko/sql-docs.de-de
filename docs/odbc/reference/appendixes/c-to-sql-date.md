---
title: 'C in SQL: Datum | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date data type [ODBC]
- converting data from c to SQL types [ODBC], date
- data conversions from C to SQL types [ODBC], date
ms.assetid: bea087d3-911f-418b-b483-d2b5b334da19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8edb075be1bf64dad8f4ef18924a6396b7c64e80
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63294372"
---
# <a name="c-to-sql-date"></a>C in SQL: date
Der Bezeichner für die Date-ODBC-C-Datentyp ist:  
  
 SQL_C_TYPE_DATE  
  
 Die folgende Tabelle zeigt die ODBC-SQL-Datentypen, die in denen Datum C-Daten konvertiert werden kann. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typ-ID|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Spalte-Byte-Länge > = 10<br /><br /> Spalte Byte Länge < 10<br /><br /> Datenwert ist kein gültiges Datum|–<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Spalte Zeichenlänge > = 10<br /><br /> Spalte Zeichen Länge < 10<br /><br /> Datenwert ist kein gültiges Datum|–<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Datenwert ist ein gültiges Datum<br /><br /> Datenwert ist kein gültiges Datum|–<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Datenwert ist ein gültiges Datum [a]<br /><br /> Datenwert ist kein gültiges Datum|–<br /><br /> 22007|  
  
 [a] der Uhrzeitteil des Zeitstempels auf 0 (null) festgelegt ist.  
  
 Weitere Informationen dazu, welche Werte in einer Struktur SQL_C_TYPE_DATE gültig sind, finden Sie unter [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md)weiter oben in diesem Anhang.  
  
 Wenn C Daten in SQL-Zeichendaten konvertiert werden, werden die resultierende Zeichendaten die "*JJJJ*-*mm*-*TT*" Format.  
  
 Der Treiber ignoriert die Längenindikator /-Wert, bei der Konvertierung von Daten von der C-Date-Datentyp, und es wird davon ausgegangen, dass die Größe des Datenpuffers die Größe des Datentyps Date C. Der Längenindikator /-Wert übergeben wird die *StrLen_or_Ind* -Argument in **SQLPutData** und in den Puffer, der mit angegebenen die *StrLen_or_IndPtr* -Argument in **SQLBindParameter**. Der Datenpuffer wird angegeben, mit der *DataPtr* -Argument in **SQLPutData** und die *ParameterValuePtr* -Argument in **SQLBindParameter**.
