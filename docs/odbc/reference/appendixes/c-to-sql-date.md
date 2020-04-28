---
title: 'C zu SQL: Datum | Microsoft-Dokumentation'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fa3df8aaee03472076b3241cb9bb60e2a307e28b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298848"
---
# <a name="c-to-sql-date"></a>C zu SQL: Datum
Der Bezeichner für den ODBC-C-Datentyp "Date" lautet:  
  
 SQL_C_TYPE_DATE  
  
 In der folgenden Tabelle werden die ODBC-SQL-Datentypen angezeigt, in die die Daten von Date C konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Spalten Byte Länge >= 10<br /><br /> Spalten Byte Länge < 10<br /><br /> Der Datenwert ist kein gültiges Datum.|Nicht zutreffend<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Spalten Zeichenlänge >= 10<br /><br /> Spalten Zeichenlänge < 10<br /><br /> Der Datenwert ist kein gültiges Datum.|Nicht zutreffend<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Der Datenwert ist ein gültiges Datum.<br /><br /> Der Datenwert ist kein gültiges Datum.|Nicht zutreffend<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Der Datenwert ist ein gültiges Datum [a]<br /><br /> Der Datenwert ist kein gültiges Datum.|Nicht zutreffend<br /><br /> 22007|  
  
 [a] der Uhrzeit Teil des Zeitstempels wird auf 0 (null) festgelegt.  
  
 Informationen dazu, welche Werte in einer SQL_C_TYPE_DATE Struktur gültig sind, finden Sie unter [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md)weiter oben in diesem Anhang.  
  
 Wenn date C-Daten in Zeichen-SQL-Daten konvertiert werden, liegen die resultierenden Zeichendaten im Format "*JJJJ*-*mm*-*DD*".  
  
 Der Treiber ignoriert den Längen-/indikatorenwert beim Umrechnen von Daten aus dem Datentyp Date c und geht davon aus, dass die Größe des Daten Puffers der Größe des Datentyps date c entspricht. Der Wert für die Länge/den Indikator wird im *StrLen_Or_Ind* -Argument in **SQLPutData** und in dem Puffer übergeben, der mit dem *StrLen_or_IndPtr* -Argument in **SQLBindParameter**angegeben wird. Der Datenpuffer wird mit dem *DataPtr* -Argument in **SQLPutData** und dem *ParameterValuePtr* -Argument in **SQLBindParameter**angegeben.
