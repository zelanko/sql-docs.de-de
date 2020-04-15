---
title: 'SQL zu C: Zeichen | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3486c0fcf5cefc39c4b85af814d7d3c1d609b4e3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296670"
---
# <a name="sql-to-c-character"></a>SQL zu C: Zeichen

Die Bezeichner für den Charakter ODBC SQL-Datentypen lauten wie folgt:

- SQL_CHAR
- SQL_VARCHAR
- SQL_LONGVARCHAR
- SQL_WCHAR
- SQL_WVARCHAR
- SQL_WLONGVARCHAR

Die folgende Tabelle zeigt die ODBC C-Datentypen, in die SQL-Zeichen konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|C-Typ-Idonid|Test|TargetValuePtr|StrLen_or_IndPtr|SQLSTATE|
|:----------------|:---|:-------------|:---------------|:-------|
|SQL_C_CHAR|Byte-Länge der Daten < *BufferLength*<br /><br /> Bytelänge der Daten >= *BufferLength*|Daten<br /><br /> Abgeschnittene Daten|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes|–<br /><br /> 01004|  
|SQL_C_WCHAR|Zeichenlänge der Daten < *BufferLength*<br /><br /> Zeichenlänge der Daten >= *BufferLength*|Daten<br /><br /> Abgeschnittene Daten|Länge der Daten in Zeichen<br /><br /> Länge der Daten in Zeichen|–<br /><br /> 01004|  
|SQL_C_STINYINT SQL_C_UTINYINT SQL_C_TINYINT SQL_C_SBIGINT SQL_C_UBIGINT SQL_C_SSHORT SQL_C_USHORT SQL_C_SHORT SQL_C_SLONG SQL_C_ULONG SQL_C_LONG SQL_C_NUMERIC|Daten, die ohne Abschneide konvertiert werden[b]<br /><br /> Daten, die mit Abschneiden von Bruchziffern konvertiert werden[a]<br /><br /> Die Konvertierung von Daten würde zu einem Verlust ganzer (im Gegensatz zu fraktionierten) Ziffern führen[a]<br /><br /> Daten sind kein *numerisches Literal*[b]|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert<br /><br /> Nicht definiert|Anzahl der Bytes des C-Datentyps<br /><br /> Anzahl der Bytes des C-Datentyps<br /><br /> Nicht definiert<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_FLOAT SQL_C_DOUBLE|Die Daten liegen im Bereich des Datentyps, in den die Nummer konvertiert wird[a]<br /><br /> Die Daten liegen außerhalb des Bereichs des Datentyps, in den die Nummer konvertiert wird[a]<br /><br /> Daten sind kein *numerisches Literal*[b]|Daten<br /><br /> Nicht definiert<br /><br /> Nicht definiert|Größe des Datentyps C<br /><br /> Nicht definiert<br /><br /> Nicht definiert|–<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BIT|Die Daten sind 0 oder 1<br /><br /> Die Daten sind größer als 0, kleiner als 2 und nicht gleich 1<br /><br /> Die Daten sind kleiner als 0 oder größer oder gleich 2<br /><br /> Daten sind kein *numerisches Literal*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert<br /><br /> Nicht definiert|1[b]<br /><br /> 1[b]<br /><br /> Nicht definiert<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BINARY|Bytelänge der Daten <= *BufferLength*<br /><br /> Byte-Länge der Daten > *BufferLength*|Daten<br /><br /> Abgeschnittene Daten|Länge der Daten in Bytes<br /><br /> Länge der Daten|–<br /><br /> 01004|  
|SQL_C_TYPE_DATE|Datenwert ist ein gültiger *Datumswert*[a]<br /><br /> Der Datenwert ist ein gültiger *Zeitstempelwert*; Zeitanteil ist Null[a]<br /><br /> Der Datenwert ist ein gültiger *Zeitstempelwert*; Zeitabschnitt ist ungleich Null[a],[c]<br /><br /> Der Datenwert ist kein gültiger *Datums-* oder *Zeitstempelwert*[a]|Daten<br /><br /> Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|6[b]<br /><br /> 6[b]<br /><br /> 6[b]<br /><br /> Nicht definiert|–<br /><br /> –<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIME|Der Datenwert ist ein gültiger *Zeitwert, und der Wert für Bruchsekunden ist 0*[a]<br /><br /> Der Datenwert ist ein gültiger *Zeitstempelwert oder ein gültiger Zeitwert;* Bruchsekundenanteil ist Null[a],[d]<br /><br /> Der Datenwert ist ein gültiger *Zeitstempelwert*; Bruchsekundenanteil ist ungleich Null[a],[d],[e]<br /><br /> Der Datenwert ist kein gültiger *Zeit-* oder *Zeitstempelwert*[a]|Daten<br /><br /> Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|6[b]<br /><br /> 6[b]<br /><br /> 6[b]<br /><br /> Nicht definiert|–<br /><br /> –<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIMESTAMP|Der Datenwert ist ein gültiger *Zeitstempelwert oder ein gültiger Zeitwert;* Bruchsekundenanteil nicht abgeschnitten[a]<br /><br /> Der Datenwert ist ein gültiger *Zeitstempelwert oder ein gültiger Zeitwert;* Bruchsekunden-Anteil abgeschnitten[a]<br /><br /> Datenwert ist ein gültiger *Datumswert*[a]<br /><br /> Datenwert ist ein gültiger *Zeitwert*[a]<br /><br /> Der Datenwert ist kein gültiger *Datums-,* *Zeit-Wert-* oder *Zeitstempelwert*[a]|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Daten[f]<br /><br /> Daten[g]<br /><br /> Nicht definiert|16[b]<br /><br /> 16[b]<br /><br /> 16[b]<br /><br /> 16[b]<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> –<br /><br /> –<br /><br /> 22018|  
|Alle C-Intervalltypen|Der Datenwert ist ein gültiger *Intervallwert;* keine Kürzung<br /><br /> Der Datenwert ist ein gültiger *Intervallwert;* Abschneiden eines oder mehrerer nachgestellter Felder<br /><br /> Daten sind gültige Intervalle; Vorderfeld erhebliche Präzision verloren<br /><br /> Der Datenwert ist kein gültiger Intervallwert.|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes<br /><br /> Nicht definiert<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22015<br /><br /> 22018|  
|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|

 [a] Der Wert von *BufferLength* wird für diese Konvertierung ignoriert. Der Treiber geht davon aus, dass die Größe von **TargetValuePtr* die Größe des C-Datentyps ist.  
  
 [b] Dies ist die Größe des entsprechenden C-Datentyps.  
  
 [c] Der Zeitteil des *Zeitstempelwertes* wird abgeschnitten.  
  
 [d] Der Datumsteil des *Zeitstempelwertes* wird ignoriert.  
  
 [e] Der Bruchteil der Sekunden des Zeitstempels wird abgeschnitten.  
  
 [f] Die Zeitfelder der Zeitstempelstruktur werden auf Null gesetzt.  
  
 [g] Die Datumsfelder der Zeitstempelstruktur werden auf das aktuelle Datum festgelegt.  

**Zusätzliche Räume**

Führende und nachfolgende Leerzeichen werden ignoriert, wenn SQL-Zeichendaten in einen der folgenden Typen konvertiert werden:

- date
- NUMERIC
- time
- timestamp
- Intervall C-Daten
