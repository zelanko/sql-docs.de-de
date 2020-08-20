---
description: 'C zu SQL: Zeichen'
title: 'C zu SQL: Zeichen | Microsoft-Dokumentation'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0ab8f1c0471c6e079f792aa40119f13cb31ca9ed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500023"
---
# <a name="c-to-sql-character"></a>C zu SQL: Zeichen
Die Bezeichner für den ODBC-C-Datentyp der Zeichenfolge lauten:  
  
 SQL_C_CHAR  
  
 SQL_C_WCHAR  
  
 In der folgenden Tabelle werden die ODBC-SQL-Datentypen angezeigt, in die C-Zeichendaten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
> [!NOTE]  
>  Wenn Zeichen-C-Daten in Unicode-SQL-Daten konvertiert werden, muss die Länge der Unicode-Daten eine gerade Zahl sein.  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Byte Länge der Daten <= Spaltenlänge.<br /><br /> Byte Länge der Daten > Spaltenlänge.|–<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Zeichen Länge der Daten <= Spaltenlänge.<br /><br /> Die Zeichen Länge der Daten > Spaltenlänge.|–<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER SQL_BIGINT|Daten wurden ohne Abschneiden konvertiert.<br /><br /> Mit Abschneiden von Bruch Ziffern konvertierte Daten [e]<br /><br /> Die Konvertierung von Daten würde zu einem Verlust ganzer (im Gegensatz zu Bruch Ziffern) Ziffern führen. [e]<br /><br /> Der Datenwert ist kein *numerisches Literalzeichen* .|–<br /><br /> 22001<br /><br /> 22001<br /><br /> 22018|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Die Daten befinden sich innerhalb des Bereichs des Datentyps, in den die Zahl konvertiert wird.<br /><br /> Die Daten liegen außerhalb des Bereichs des Datentyps, in den die Zahl konvertiert wird.<br /><br /> Der Datenwert ist kein *numerisches Literalzeichen* .|–<br /><br /> 22003<br /><br /> 22018|  
|SQL_BIT|Die Daten sind 0 oder 1.<br /><br /> Die Daten sind größer als 0 (null), kleiner als 2, nicht gleich 1.<br /><br /> Daten sind kleiner als 0 (null) oder größer oder gleich 2.<br /><br /> Daten sind kein *numerisches Literalzeichen* .|–<br /><br /> 22001<br /><br /> 22003<br /><br /> 22018|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|(Byte Länge der Daten)/2 <= Spalten Byte Länge<br /><br /> (Byte Länge der Daten)/2 > Spalten Byte Länge<br /><br /> Der Datenwert ist kein hexadezimaler Wert.|–<br /><br /> 22001<br /><br /> 22018|  
|SQL_TYPE_DATE|Der Datenwert ist ein gültiges *ODBC-Date-Literal.*<br /><br /> Der Datenwert ist ein gültiger *ODBC-Timestamp-Literalwert*. Der Uhrzeitteil ist NULL.<br /><br /> Der Datenwert ist ein gültiger *ODBC-Timestamp-Literalwert*. Der Zeitanteil ist ungleich 0 (null) [a]<br /><br /> Der Datenwert ist kein gültiger *ODBC-Date-Literal* -oder *ODBC-Timestamp-Literalwert* .|–<br /><br /> –<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIME|Der Datenwert ist ein gültiges *ODBC-Time-Literale* .<br /><br /> Der Datenwert ist ein gültiger *ODBC-Timestamp-Literalwert*. der Teil der Sekundenbruchteile ist 0 (null) [b]<br /><br /> Der Datenwert ist ein gültiger *ODBC-Timestamp-Literalwert*. der Teil für die Sekundenbruchteile ist nicht NULL [b]<br /><br /> Der Datenwert ist kein gültiges *ODBC-Time-Literale* -oder *ODBC-Timestamp-Literalzeichen* .|–<br /><br /> –<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIMESTAMP|Der Datenwert ist ein gültiger *ODBC-Timestamp-Literalwert*. Teil der Sekundenbruchteile nicht abgeschnitten<br /><br /> Der Datenwert ist ein gültiger *ODBC-Timestamp-Literalwert*. Teil Bruchteile abgeschnitten<br /><br /> Der Datenwert ist ein gültiger *ODBC-Date-Literale*[c]<br /><br /> Der Datenwert ist ein gültiger *ODBC-Time-Literale*[d]<br /><br /> Der Datenwert ist keine gültige *ODBC-Date-Literale*, *ODBC-Time-Literale*oder *ODBC-Timestamp-Literale* .|–<br /><br /> 22008<br /><br /> –<br /><br /> –<br /><br /> 22018|  
|Alle SQL-Intervall Typen|Der Datenwert ist ein gültiger *Intervall Wert*. keine Kürzung erfolgt<br /><br /> Der Datenwert ist ein gültiger *Intervall Wert*. der Wert in einem der Felder wird abgeschnitten.<br /><br /> Der Datenwert ist kein gültiges intervallliterale.|–<br /><br /> 22015<br /><br /> 22018|  
  
 [a] der Uhrzeit Teil des Zeitstempels wird abgeschnitten.  
  
 [b] der Datums Teil des Zeitstempels wird ignoriert.  
  
 [c] der Uhrzeit Teil des Zeitstempels wird auf 0 (null) festgelegt.  
  
 [d] der Date-Teil des Zeitstempels wird auf das aktuelle Datum festgelegt.  
  
 [e] der Treiber bzw. die Datenquelle wartet effektiv, bis die gesamte Zeichenfolge empfangen wurde (auch wenn die Zeichendaten in Teilen durch Aufrufe von **SQLPutData**gesendet werden), bevor versucht wird, die Konvertierung auszuführen.  
  
 Wenn Zeichen-C-Daten in numerische Daten, Datums-, Uhrzeit-oder Zeitstempel-SQL-Daten konvertiert werden, werden führende und nachfolgende Leerzeichen ignoriert.  
  
 Wenn Zeichen-C-Daten in binäre SQL-Daten konvertiert werden, werden alle zwei Bytes von Zeichendaten in ein einzelnes Byte (8 Bits) Binärdaten konvertiert. Alle zwei Bytes von Zeichendaten stellen eine Zahl in hexadezimaler Form dar. Beispielsweise wird "01" in ein binäres 00000001-Format konvertiert, und "FF" wird in eine binäre 11111111-Datei konvertiert.  
  
 Der Treiber konvertiert Paare von hexadezimalen Ziffern immer in einzelne Bytes und ignoriert das NULL-Terminierungs Byte. Wenn die Länge der Zeichenfolge ungerade ist, wird das letzte Byte der Zeichenfolge (mit Ausnahme des NULL-Terminierungs Byte, sofern vorhanden) nicht konvertiert.  
  
> [!NOTE]  
>  Anwendungsentwickler werden davon abgeraten, Zeichen-C-Daten an einen binären SQL-Datentyp zu binden. Diese Konvertierung ist in der Regel ineffizient und langsam.
