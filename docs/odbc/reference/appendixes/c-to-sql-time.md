---
title: 'C zu SQL: Zeit | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], time
- time data type [ODBC]
- converting data from c to SQL types [ODBC], time
ms.assetid: a8da43c9-d9a5-45e5-bd9a-1dd633db2ee0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 264ce7751072b79163923f0c141542680f7b02bb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304762"
---
# <a name="c-to-sql-time"></a>C zu SQL: Uhrzeit
Der Bezeichner für den Datentyp ODBC C lautet:  
  
 SQL_C_TYPE_TIME  
  
 Die folgende Tabelle zeigt die ODBC SQL-Datentypen, in die C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Spaltenbytelänge >= 8<br /><br /> Spaltenbytelänge < 8<br /><br /> Der Datenwert ist keine gültige Zeit|–<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Spaltenzeichenlänge >= 8<br /><br /> Spaltenzeichenlänge < 8<br /><br /> Der Datenwert ist keine gültige Zeit|–<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_TIME|Datenwert ist eine gültige Zeit<br /><br /> Der Datenwert ist keine gültige Zeit|–<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Der Datenwert ist eine gültige Zeit[a]<br /><br /> Der Datenwert ist keine gültige Zeit|–<br /><br /> 22007|  
  
 [a] Der Datumsteil des Zeitstempels wird auf das aktuelle Datum und der Teil der Sekunden bruchteil des Zeitstempels auf Null gesetzt.  
  
 Informationen darüber, welche Werte in einer SQL_C_TYPE_TIME-Struktur gültig sind, finden Sie weiter oben in diesem Anhang unter [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md).  
  
 Wenn Zeit-C-Daten in SQL-Zeichendaten konvertiert werden, sind die resultierenden Zeichendaten im Format "*hh*:*mm*:*ss*" enthalten.  
  
 Der Treiber ignoriert den Längen-/Indikatorwert beim Konvertieren von Daten aus dem Datentyp Zeit C und geht davon aus, dass die Größe des Datenpuffers die Größe des Zeit-C-Datentyps ist. Der Längen-/Indikatorwert wird im *Argument StrLen_or_Ind* in **SQLPutData** und im Puffer übergeben, der mit dem *Argument StrLen_or_IndPtr* in **SQLBindParameter**angegeben ist. Der Datenpuffer wird mit dem *DataPtr-Argument* in **SQLPutData** und dem *ParameterValuePtr-Argument* in **SQLBindParameter**angegeben.
