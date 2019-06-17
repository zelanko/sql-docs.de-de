---
title: 'C in SQL: Zeichen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- character data type [ODBC]
- data conversions from C to SQL types [ODBC], character
- converting data from c to SQL types [ODBC], character
ms.assetid: be66188a-ebdb-4c9e-af72-c379886766fa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0158da62ed360e926cdb5382b89b1491c0723550
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63201624"
---
# <a name="c-to-sql-character"></a>C in SQL: Zeichen
Der Bezeichner für das ODBC-C-Datentyp-Zeichen sind:  
  
 SQL_C_CHAR  
  
 SQL_C_WCHAR  
  
 Die folgende Tabelle zeigt die ODBC-SQL-Datentypen, die in denen C-Zeichendaten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
> [!NOTE]  
>  Wenn C-Zeichendaten in Unicode-SQL-Daten konvertiert werden, muss die Länge des Unicode-Daten eine gerade Zahl sein.  
  
|SQL-Typ-ID|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Die Bytelänge der Daten < = Länge der Spalte.<br /><br /> Die Bytelänge der Daten > Länge der Spalte.|–<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Länge der Daten Zeichen < = Länge der Spalte.<br /><br /> Länge der Daten Zeichen > Länge der Spalte.|–<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER SQL_BIGINT|Daten, die konvertiert werden, ohne Abschneiden<br /><br /> Daten, die mit dem Abschneiden der Dezimalstellen [e] konvertiert<br /><br /> Konvertierung von Daten führt zu Verlust insgesamt (im Gegensatz zu Bruch) Ziffern [e]<br /><br /> Keine *numerischen Literalen*|–<br /><br /> 22001<br /><br /> 22001<br /><br /> 22018|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Daten sind innerhalb des Bereichs des Datentyps, der die Anzahl konvertiert wird<br /><br /> Daten sind außerhalb des Bereichs des Datentyps, der die Anzahl konvertiert wird<br /><br /> Keine *numerischen Literalen*|–<br /><br /> 22003<br /><br /> 22018|  
|SQL_BIT|Daten sind 0 oder 1<br /><br /> Daten ist größer als 0 ist, kleiner als 2, und nicht gleich-1<br /><br /> Daten ist kleiner als 0 oder größer als oder gleich 2<br /><br /> Daten sind keine *numerischen Literalen*|–<br /><br /> 22001<br /><br /> 22003<br /><br /> 22018|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|(Bytelänge der Daten) / 2 < = Spalte-Byte-Länge<br /><br /> (Bytelänge der Daten) / 2 > Spalte-Byte-Länge<br /><br /> Datenwert ist es sich nicht um einen Hexadezimalwert|–<br /><br /> 22001<br /><br /> 22018|  
|SQL_TYPE_DATE|Datenwert ist ein gültiger *ODBC-Datum-Literal*<br /><br /> Datenwert ist ein gültiger *ODBC-Zeitstempel-Literal*; Uhrzeitanteil ist 0 (null)<br /><br /> Datenwert ist ein gültiger *ODBC-Zeitstempel-Literal*; Uhrzeitanteil ist ungleich Null [a]<br /><br /> Wert ist kein gültiger *ODBC-Datum-Literal* oder *ODBC-Zeitstempel-Literal*|–<br /><br /> –<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIME|Datenwert ist ein gültiger *ODBC-Uhrzeit-Literal*<br /><br /> Datenwert ist ein gültiger *ODBC-Zeitstempel-Literal*; Bruchteilen Sekundenteil ist 0 (null) [b]<br /><br /> Datenwert ist ein gültiger *ODBC-Zeitstempel-Literal*; Bruchteilen Sekundenteil ist ungleich Null [b]<br /><br /> Wert ist kein gültiger *ODBC-Uhrzeit-Literal* oder *ODBC-Zeitstempel-Literal*|–<br /><br /> –<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIMESTAMP|Datenwert ist ein gültiger *ODBC-Zeitstempel-Literal*; Bruchteilen Sekundenteil nicht abgeschnitten<br /><br /> Datenwert ist ein gültiger *ODBC-Zeitstempel-Literal*; Sekundenbruchteile abgeschnitten Sekundenteil<br /><br /> Datenwert ist ein gültiger *ODBC-Datum-Literal*[c]<br /><br /> Datenwert ist ein gültiger *ODBC-Uhrzeit-Literal*[d]<br /><br /> Wert ist kein gültiger *ODBC-Datum-Literal*, *ODBC-Uhrzeit-Literal*, oder *ODBC-Zeitstempel-Literal*|–<br /><br /> 22008<br /><br /> –<br /><br /> –<br /><br /> 22018|  
|Alle Typen von SQL-Zeitintervall|Datenwert ist ein gültiger *Intervallwert*; kein Abschneiden erfolgt<br /><br /> Datenwert ist ein gültiger *Intervallwert*; der Wert in einem der Felder wird abgeschnitten.<br /><br /> Der Wert ist kein gültiges Intervall literal.|–<br /><br /> 22015<br /><br /> 22018|  
  
 [a] der Uhrzeitteil des Zeitstempels wird abgeschnitten.  
  
 [b] der Datumsteil des Zeitstempels wird ignoriert.  
  
 [c] der Uhrzeitteil des Zeitstempels ist auf 0 (null) festgelegt.  
  
 [d] der Datumsteil des Zeitstempels wird auf das aktuelle Datum festgelegt.  
  
 [e]-Treibers /-Datenquelle effektiv wartet, bis die gesamte Zeichenfolge empfangen wurden (auch wenn die Zeichendaten in Teilen, durch Aufrufe von gesendet werden **SQLPutData**) bevor Sie versuchen, die die Konvertierung nicht ausgeführt.  
  
 Wenn Zeichendaten C in numerischer, konvertiert Datum, Uhrzeit oder Zeitstempel-SQL-Daten ist, werden führende und nachfolgende Leerzeichen ignoriert.  
  
 Wenn auf binäre Daten, SQL C Zeichendaten konvertiert werden, werden jeweils zwei Byte von Zeichendaten in ein einzelnes Byte (8 Bits) von Binärdaten konvertiert. Eine Zahl im hexadezimalen Format darstellen, jeweils zwei Byte Zeichendaten. Z. B. "01" wird in eine binäre 00000001 konvertiert, und "FF" in eine binäre 11111111 konvertiert wird.  
  
 Der Treiber immer-Paare von hexadezimalen Ziffern auf einzelnen Byte konvertiert und ignoriert das Byte Null-Terminierung vorliegt. Wenn die Länge der Zeichenfolge ungerade ist, ist, wird das letzte Byte der Zeichenfolge (ohne das Byte, das Null-Terminierung vorliegt, sofern vorhanden) aus diesem Grund nicht konvertiert.  
  
> [!NOTE]  
>  Anwendungsentwicklern werden davon abgeraten, aus dem Zeichen C-Daten in einen binären SQL-Datentyp binden. Diese Konvertierung ist in der Regel ineffizient und zeitaufwändig.
