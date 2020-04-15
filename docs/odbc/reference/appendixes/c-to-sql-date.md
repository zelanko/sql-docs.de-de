---
title: 'C zu SQL: Datum | Microsoft Docs'
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298848"
---
# <a name="c-to-sql-date"></a>C zu SQL: Datum
Der Bezeichner für den Datentyp ODBC C lautet:  
  
 SQL_C_TYPE_DATE  
  
 Die folgende Tabelle zeigt die ODBC SQL-Datentypen, in die C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Spaltenbytelänge >= 10<br /><br /> Säulenbytelänge < 10<br /><br /> Datenwert ist kein gültiges Datum|–<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Spaltenzeichenlänge >= 10<br /><br /> Spaltenzeichenlänge < 10<br /><br /> Datenwert ist kein gültiges Datum|–<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Datenwert ist ein gültiges Datum<br /><br /> Datenwert ist kein gültiges Datum|–<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Datenwert ist ein gültiges Datum[a]<br /><br /> Datenwert ist kein gültiges Datum|–<br /><br /> 22007|  
  
 [a] Der Zeitteil des Zeitstempels ist auf Null gesetzt.  
  
 Informationen darüber, welche Werte in einer SQL_C_TYPE_DATE-Struktur gültig sind, finden Sie weiter oben in diesem Anhang unter [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md).  
  
 Wenn Datum C-Daten in SQL-Zeichendaten konvertiert werden, werden die resultierenden Zeichendaten im Format "*yyyy*-*mm*-*dd*" angezeigt.  
  
 Der Treiber ignoriert den Längen-/Indikatorwert beim Konvertieren von Daten aus dem Datentyp Datum C und geht davon aus, dass die Größe des Datenpuffers die Größe des Datentyps Datum C beträgt. Der Längen-/Indikatorwert wird im *Argument StrLen_or_Ind* in **SQLPutData** und im Puffer übergeben, der mit dem *Argument StrLen_or_IndPtr* in **SQLBindParameter**angegeben ist. Der Datenpuffer wird mit dem *DataPtr-Argument* in **SQLPutData** und dem *ParameterValuePtr-Argument* in **SQLBindParameter**angegeben.
