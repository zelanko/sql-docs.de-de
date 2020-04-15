---
title: 'C zu SQL: Zeitstempel | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], timestamp
- timestamp data type [ODBC]
- converting data from c to SQL types [ODBC], timestamp
ms.assetid: 0e08bfff-68f9-4648-9558-09b57fea08ad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3102e5043527a1aa9463980c9dd546839cb92f37
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283750"
---
# <a name="c-to-sql-timestamp"></a>C zu SQL: Zeitstempel
Der Bezeichner für den Datentyp ODBC C ist:  
  
 SQL_C_TYPE_TIMESTAMP  
  
 Die folgende Tabelle zeigt die ODBC SQL-Datentypen, in die Zeitstempel-C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Spaltenbytelänge >= Zeichenbytelänge<br /><br /> 19 <= Spaltenbytelänge < Zeichenbytelänge<br /><br /> Säulenbytelänge < 19<br /><br /> Der Datenwert ist kein gültiger Zeitstempel|–<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Spaltenzeichenlänge >= Zeichenlänge der Daten<br /><br /> 19 <= Spaltenzeichenlänge < Zeichenlänge der Daten<br /><br /> Spaltenzeichenlänge < 19<br /><br /> Der Datenwert ist kein gültiger Zeitstempel|–<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Zeitfelder sind Null<br /><br /> Zeitfelder sind ungleich Null<br /><br /> Datenwert enthält kein gültiges Datum|–<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIME|Bruchsekundenfelder sind Null[a]<br /><br /> Bruchsekundenfelder sind ungleich Null[a]<br /><br /> Datenwert enthält keine gültige Zeit|–<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Fractional Seconds-Felder werden nicht abgeschnitten<br /><br /> Bruchsekundenfelder werden abgeschnitten<br /><br /> Der Datenwert ist kein gültiger Zeitstempel|–<br /><br /> 22008<br /><br /> 22007|  
  
 [a] Die Datumsfelder der Zeitstempelstruktur werden ignoriert.  
  
 Informationen darüber, welche Werte in einer SQL_C_TIMESTAMP-Struktur gültig sind, finden Sie weiter oben in diesem Anhang unter [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md).  
  
 Wenn Zeitstempel-C-Daten in SQL-Zeichendaten konvertiert werden, sind die resultierenden Zeichendaten im "*yyyy*-*mm*-*dd* *hh*:*mm*:*ss*[.* f...*]" Format.  
  
 Der Treiber ignoriert den Längen-/Indikatorwert beim Konvertieren von Daten aus dem Datentyp Zeitstempel C und geht davon aus, dass die Größe des Datenpuffers die Größe des Datentyps Zeitstempel C hat. Der Längen-/Indikatorwert wird im *Argument StrLen_or_Ind* in **SQLPutData** und im Puffer übergeben, der mit dem *Argument StrLen_or_IndPtr* in **SQLBindParameter**angegeben ist. Der Datenpuffer wird mit dem *DataPtr-Argument* in **SQLPutData** und dem *ParameterValuePtr-Argument* in **SQLBindParameter**angegeben.
