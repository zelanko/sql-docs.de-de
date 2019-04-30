---
title: 'C in SQL: Zeitstempel | Microsoft-Dokumentation'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a738712a8fb1b032ef8244f579b10fdcc22becee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63241428"
---
# <a name="c-to-sql-timestamp"></a>C in SQL: Timestamp
Der Bezeichner für den Timestamp ODBC C-Datentyp ist:  
  
 SQL_C_TYPE_TIMESTAMP  
  
 Die folgende Tabelle zeigt die ODBC-SQL-Datentypen, die in die Timestamp-C-Datentyp konvertiert werden kann. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typ-ID|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Spalte-Byte-Länge > = Zeichen-Byte-Länge<br /><br /> 19 < Byte Spaltenlänge = < Zeichen Länge in Byte<br /><br /> Spalte Byte Länge < 19<br /><br /> Wert ist kein gültiger timestamp|–<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Spalte Zeichenlänge > = Zeichenlänge der Daten<br /><br /> 19 < = Spaltenlänge für die Zeichen < Zeichen Länge der Daten<br /><br /> Spalte Zeichen Länge < 19<br /><br /> Wert ist kein gültiger timestamp|–<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Time-Felder sind 0 (null)<br /><br /> Time-Felder sind ungleich NULL.<br /><br /> Datenwert enthält kein gültiges Datum|–<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIME|Felder für Sekundenbruchteile sind 0 (null) [a]<br /><br /> Felder für Sekundenbruchteile werden ungleich Null [a]<br /><br /> Datenwert enthält keine gültige Uhrzeit|–<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Felder für Sekundenbruchteile werden nicht abgeschnitten.<br /><br /> Felder für Sekundenbruchteile werden abgeschnitten.<br /><br /> Wert ist kein gültiger timestamp|–<br /><br /> 22008<br /><br /> 22007|  
  
 [a] das Datum, die Felder der Struktur Zeitstempel ignoriert werden.  
  
 Weitere Informationen dazu, welche Werte in einer Struktur SQL_C_TIMESTAMP gültig sind, finden Sie unter [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md)weiter oben in diesem Anhang.  
  
 Wenn C-Zeitstempel-Daten in SQL-Zeichendaten konvertiert werden, werden die resultierende Zeichendaten die "*JJJJ*-*mm*-*TT* *Hh*:*mm*:*ss*[.*f...*] "Format.  
  
 Der Treiber ignoriert den Längenindikator /-Wert, bei der Konvertierung von Daten von der C-Timestamp-Datentyp, und es wird davon ausgegangen, dass die Größe des Datenpuffers die Größe der C-Timestamp-Datentyp ist. Der Längenindikator /-Wert übergeben wird die *StrLen_or_Ind* -Argument in **SQLPutData** und in den Puffer, der mit angegebenen die *StrLen_or_IndPtr* -Argument in **SQLBindParameter**. Der Datenpuffer wird angegeben, mit der *DataPtr* -Argument in **SQLPutData** und die *ParameterValuePtr* -Argument in **SQLBindParameter**.
