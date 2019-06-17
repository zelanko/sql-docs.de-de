---
title: 'SQL in C: Zeichen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], character
- character data type [ODBC]
- data conversions from SQL to C types [ODBC], character
ms.assetid: 7fdb7f38-b64d-48f2-bcb4-1ca96b2bbdb6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3a0a7036d67716a3d90bd8953a3c7ba2c575c92
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63259510"
---
# <a name="sql-to-c-character"></a>SQL in C: Zeichen

Der Bezeichner für die ODBC-SQL-Datentypen sind die folgenden:

- SQL_CHAR
- SQL_VARCHAR
- SQL_LONGVARCHAR
- SQL_WCHAR
- SQL_WVARCHAR
- SQL_WLONGVARCHAR

Die folgende Tabelle zeigt die ODBC-C-Datentypen, die in denen SQL-Zeichendaten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|C-Typ-ID|Test|TargetValuePtr|StrLen_or_IndPtr|SQLSTATE|
|:----------------|:---|:-------------|:---------------|:-------|
|SQL_C_CHAR|Die Bytelänge der Daten < *Pufferlänge*<br /><br /> Die Bytelänge der Daten > = *Pufferlänge*|Daten<br /><br /> Abgeschnittene Daten|Länge der Daten in bytes<br /><br /> Länge der Daten in bytes|–<br /><br /> 01004|  
|SQL_C_WCHAR|Länge der Daten Zeichen < *Pufferlänge*<br /><br /> Zeichen Länge > = *Pufferlänge*|Daten<br /><br /> Abgeschnittene Daten|Länge der Daten in Zeichen<br /><br /> Länge der Daten in Zeichen|–<br /><br /> 01004|  
|SQL_C_STINYINT SQL_C_UTINYINT SQL_C_TINYINT SQL_C_SBIGINT SQL_C_UBIGINT SQL_C_SSHORT SQL_C_USHORT SQL_C_SHORT SQL_C_SLONG SQL_C_ULONG SQL_C_LONG SQL_C_NUMERIC|Daten konvertiert werden, ohne Abschneiden [b]<br /><br /> Daten konvertiert werden, mit dem Abschneiden der Dezimalstellen [a]<br /><br /> Konvertierung von Daten führt zu Verlust insgesamt (im Gegensatz zu Bruch) Ziffern [a]<br /><br /> Daten sind keine *numerischen Literalen*[b].|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert<br /><br /> Nicht definiert|Anzahl von Datenbytes der C-Datentyp<br /><br /> Anzahl von Datenbytes der C-Datentyp<br /><br /> Nicht definiert<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_FLOAT SQL_C_DOUBLE|Daten sind innerhalb des Bereichs des Datentyps, der die Zahl konvertiert wird wird [a]<br /><br /> Daten sind außerhalb des Bereichs des Datentyps, der die Zahl konvertiert wird wird [a]<br /><br /> Daten sind keine *numerischen Literalen*[b].|Daten<br /><br /> Nicht definiert<br /><br /> Nicht definiert|Anzahl der C-Datentyp<br /><br /> Nicht definiert<br /><br /> Nicht definiert|–<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BIT|Daten sind 0 oder 1<br /><br /> Daten ist größer als 0 ist, kleiner als 2, und nicht gleich-1<br /><br /> Daten ist kleiner als 0 oder größer als oder gleich 2<br /><br /> Daten sind keine *numerischen Literalen*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert<br /><br /> Nicht definiert|1[b]<br /><br /> 1[b]<br /><br /> Nicht definiert<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BINARY|Die Bytelänge der Daten < = *Pufferlänge*<br /><br /> Die Bytelänge der Daten > *Pufferlänge*|Daten<br /><br /> Abgeschnittene Daten|Länge der Daten in bytes<br /><br /> Länge der Daten|–<br /><br /> 01004|  
|SQL_C_TYPE_DATE|Datenwert ist ein gültiger *Datumswert*[a]<br /><br /> Datenwert ist ein gültiger *Timestamp-Wert*; Uhrzeitanteil ist 0 (null) [a]<br /><br /> Datenwert ist ein gültiger *Timestamp-Wert*; Uhrzeitanteil ist ungleich Null [a], [c]<br /><br /> Wert ist kein gültiger *Datumswert* oder *Timestamp-Wert*[a]|Daten<br /><br /> Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|6[b]<br /><br /> 6[b]<br /><br /> 6[b]<br /><br /> Nicht definiert|–<br /><br /> –<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIME|Datenwert ist ein gültiger *Zeit-Wert und die Sekundenbruchteile, 0 wird*[a]<br /><br /> Datenwert ist ein gültiger *Timestamp-Wert oder ein gültiger Zeitwert*; Bruchteilen Sekundenteil ist 0 (null) [a], [d]<br /><br /> Datenwert ist ein gültiger *Timestamp-Wert*; Bruchteilen Sekundenteil ungleich NULL ist [a], [d], [e]<br /><br /> Wert ist kein gültiger *Zeitwert* oder *Timestamp-Wert*[a]|Daten<br /><br /> Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|6[b]<br /><br /> 6[b]<br /><br /> 6[b]<br /><br /> Nicht definiert|–<br /><br /> –<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIMESTAMP|Datenwert ist ein gültiger *Timestamp-Wert oder ein gültiger Zeitwert*; Bruchteilen Sekundenteil nicht abgeschnitten, [a]<br /><br /> Datenwert ist ein gültiger *Timestamp-Wert oder ein gültiger Zeitwert*; Bruchteilen Sekundenteil abgeschnitten, [a]<br /><br /> Datenwert ist ein gültiger *Datumswert*[a]<br /><br /> Datenwert ist ein gültiger *Zeitwert*[a]<br /><br /> Wert ist kein gültiger *Datumswert*, *Zeitwert*, oder *Timestamp-Wert*[a]|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Daten [f]<br /><br /> Daten [g]<br /><br /> Nicht definiert|16[b]<br /><br /> 16[b]<br /><br /> 16[b]<br /><br /> 16[b]<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> –<br /><br /> –<br /><br /> 22018|  
|Alle C-Intervall-Typen|Datenwert ist ein gültiger *Intervallwert*; kein Abschneiden<br /><br /> Datenwert ist ein gültiger *Intervallwert*; Abschneiden von ein oder mehrere nachfolgende Felder<br /><br /> Daten werden Sie gültige Intervall. Feld erhebliche Genauigkeit für anführenden ist verloren gegangen.<br /><br /> Der Wert ist kein gültiges Intervallwert|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert<br /><br /> Nicht definiert|Länge der Daten in bytes<br /><br /> Länge der Daten in bytes<br /><br /> Nicht definiert<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22015<br /><br /> 22018|  
|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|

 [a] den Wert der *Pufferlänge* für diese Konvertierung ignoriert wird. Der Treiber setzt voraus, dass die Größe des **TargetValuePtr* ist die Größe der C-Datentyp.  
  
 [b] Dies ist die Größe des entsprechenden C-Datentyp.  
  
 [c] der Uhrzeitteil der *Timestamp-Wert* wird abgeschnitten.  
  
 [d] in der Date-Teil der *Timestamp-Wert* wird ignoriert.  
  
 [e] der Bereich der Sekundenbruchteile des Zeitstempels wird abgeschnitten.  
  
 [f] Zeitfelder der Timestamp-Struktur werden auf 0 (null) festgelegt.  
  
 [g] die Datumsfelder der Timestamp-Struktur werden auf das aktuelle Datum festgelegt.  

**Zusätzliche Leerzeichen**

Führende und nachfolgende Leerzeichen werden ignoriert, wenn SQL-Zeichendaten in der folgenden Typen konvertiert werden:

- date
- NUMERIC
- time
- timestamp
- C Intervalldaten
