---
title: 'C in SQL: Zeit | Microsoft-Dokumentation'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ea11803847505698ea42d13727b6177f3a24bda
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63316531"
---
# <a name="c-to-sql-time"></a>C in SQL: Uhrzeit
Der Bezeichner für den Zeitpunkt ODBC C-Datentyp ist:  
  
 SQL_C_TYPE_TIME  
  
 Die folgende Tabelle zeigt die ODBC-SQL-Datentypen, die in denen C Zeitdaten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typ-ID|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Spalte-Byte-Länge > = 8<br /><br /> Spalte Byte Länge < 8<br /><br /> Wert ist nicht gültig|–<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Spalte Zeichenlänge > = 8<br /><br /> Spalte Zeichen Länge < 8<br /><br /> Wert ist nicht gültig|–<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_TIME|Datenwert ist gültig<br /><br /> Wert ist nicht gültig|–<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Datenwert ist gültig [a]<br /><br /> Wert ist nicht gültig|–<br /><br /> 22007|  
  
 [a] das Datum, die Teil des Zeitstempels festgelegt ist, um das aktuelle Datum und die Sekundenbruchteile, die Teil der Zeitstempel auf 0 (null) festgelegt ist.  
  
 Weitere Informationen dazu, welche Werte in einer Struktur SQL_C_TYPE_TIME gültig sind, finden Sie unter [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md)weiter oben in diesem Anhang.  
  
 Wenn C Zeitdaten in SQL-Zeichendaten konvertiert werden, werden die resultierende Zeichendaten die "*Hh*:*mm*:*ss*" Format.  
  
 Der Treiber ignoriert den Längenindikator /-Wert, wenn Daten ab dem Zeitpunkt, zu konvertieren, C-Datentyp ist, und setzt voraus, dass die Größe des Datenpuffers die Größe der Zeit C-Datentyp ist. Der Längenindikator /-Wert übergeben wird die *StrLen_or_Ind* -Argument in **SQLPutData** und in den Puffer, der mit angegebenen die *StrLen_or_IndPtr* -Argument in **SQLBindParameter**. Der Datenpuffer wird angegeben, mit der *DataPtr* -Argument in **SQLPutData** und die *ParameterValuePtr* -Argument in **SQLBindParameter**.
