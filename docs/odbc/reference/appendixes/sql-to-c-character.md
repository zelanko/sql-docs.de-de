---
title: 'SQL zu C: Zeichen | Microsoft-Dokumentation'
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
ms.openlocfilehash: 8a649e1ec27261551b7a64e09310ce99b6140a15
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68056926"
---
# <a name="sql-to-c-character"></a>SQL zu C: Zeichen

Die Bezeichner für die ODBC-SQL-Datentypen der Zeichen folgen lauten wie folgt:

- SQL_CHAR
- SQL_VARCHAR
- SQL_LONGVARCHAR
- SQL_WCHAR
- SQL_WVARCHAR
- SQL_WLONGVARCHAR

In der folgenden Tabelle werden die ODBC-C-Datentypen angezeigt, in die SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|C-Typbezeichner|Test|Targetvalueptr|StrLen_or_IndPtr|SQLSTATE|
|:----------------|:---|:-------------|:---------------|:-------|
|SQL_C_CHAR|Byte Länge der Daten < *BufferLength*<br /><br /> Byte Länge der Daten >= *BufferLength*|Data<br /><br /> Abgeschnittene Daten|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes|–<br /><br /> 01004|  
|SQL_C_WCHAR|Zeichen Länge der Daten < *BufferLength*<br /><br /> Zeichen Länge der Daten >= *BufferLength*|Data<br /><br /> Abgeschnittene Daten|Länge der Daten in Zeichen<br /><br /> Länge der Daten in Zeichen|–<br /><br /> 01004|  
|SQL_C_STINYINT SQL_C_UTINYINT SQL_C_TINYINT SQL_C_SBIGINT SQL_C_UBIGINT SQL_C_SSHORT SQL_C_USHORT SQL_C_SHORT SQL_C_SLONG SQL_C_ULONG SQL_C_LONG SQL_C_NUMERIC|Konvertierte Daten ohne Abschneiden [b]<br /><br /> Mit Abschneiden von Bruch Ziffern konvertierte Daten [a]<br /><br /> Die Konvertierung von Daten würde zu einem Verlust ganzer (im Gegensatz zu Bruch Ziffern) Ziffern führen. [a]<br /><br /> Daten sind keine *numerischen Literale*[b]|Data<br /><br /> Abgeschnittene Daten<br /><br /> Undefined<br /><br /> Undefined|Anzahl von Bytes des C-Datentyps<br /><br /> Anzahl von Bytes des C-Datentyps<br /><br /> Undefined<br /><br /> Undefined|–<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_FLOAT SQL_C_DOUBLE|Die Daten befinden sich innerhalb des Bereichs des Datentyps, in den die Zahl konvertiert wird [a]<br /><br /> Die Daten liegen außerhalb des Bereichs des Datentyps, in den die Zahl konvertiert wird [a]<br /><br /> Daten sind keine *numerischen Literale*[b]|Data<br /><br /> Undefined<br /><br /> Undefined|Größe des C-Datentyps<br /><br /> Undefined<br /><br /> Undefined|–<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BIT|Die Daten sind 0 oder 1.<br /><br /> Die Daten sind größer als 0 (null), kleiner als 2, nicht gleich 1.<br /><br /> Daten sind kleiner als 0 (null) oder größer oder gleich 2.<br /><br /> Daten sind kein *numerisches Literalzeichen* .|Data<br /><br /> Abgeschnittene Daten<br /><br /> Undefined<br /><br /> Undefined|1 [b]<br /><br /> 1 [b]<br /><br /> Undefined<br /><br /> Undefined|–<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BINARY|Byte Länge der Daten <= *BufferLength*<br /><br /> Byte Länge der Daten > *BufferLength*|Data<br /><br /> Abgeschnittene Daten|Länge der Daten in Bytes<br /><br /> Länge der Daten|–<br /><br /> 01004|  
|SQL_C_TYPE_DATE|Der Datenwert ist ein gültiger *Datumswert*[a].<br /><br /> Der Datenwert ist ein gültiger *timestamp-Wert*. Der Uhrzeitteil ist 0 (null) [a]<br /><br /> Der Datenwert ist ein gültiger *timestamp-Wert*. Der Uhrzeitteil ist ungleich 0 (null) [a], [c]<br /><br /> Der Datenwert ist kein gültiger *Datums-* */Uhrzeitwert-oder timestamp-Wert*[a]|Data<br /><br /> Data<br /><br /> Abgeschnittene Daten<br /><br /> Undefined|6 [b]<br /><br /> 6 [b]<br /><br /> 6 [b]<br /><br /> Undefined|–<br /><br /> –<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIME|Der Datenwert ist ein gültiger *Zeitwert, und der Wert für die Sekundenbruchteile ist 0*(null).<br /><br /> Der Datenwert ist ein gültiger *timestamp-Wert oder ein gültiger Zeitwert*. der Teil der Sekundenbruchteile ist 0 (null) [a], [d]<br /><br /> Der Datenwert ist ein gültiger *timestamp-Wert*. der Teil für die Sekundenbruchteile ist ungleich 0 (null) [a], [d], [e]<br /><br /> Der Datenwert ist kein gültiger *Zeitwert* oder *timestamp-Wert*[a].|Data<br /><br /> Data<br /><br /> Abgeschnittene Daten<br /><br /> Undefined|6 [b]<br /><br /> 6 [b]<br /><br /> 6 [b]<br /><br /> Undefined|–<br /><br /> –<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIMESTAMP|Der Datenwert ist ein gültiger *timestamp-Wert oder ein gültiger Zeitwert*. Teil Sekundenbruchteile nicht abgeschnitten [a]<br /><br /> Der Datenwert ist ein gültiger *timestamp-Wert oder ein gültiger Zeitwert*. Teil Bruchteile abgeschnitten [a]<br /><br /> Der Datenwert ist ein gültiger *Datumswert*[a].<br /><br /> Der Datenwert ist ein gültiger *Zeitwert*[a].<br /><br /> Der Datenwert ist kein gültiger *Datums-* */Uhrzeitwert-oder timestamp-Wert*[a] **|Data<br /><br /> Abgeschnittene Daten<br /><br /> Daten [f]<br /><br /> Daten [g]<br /><br /> Undefined|16 [b]<br /><br /> 16 [b]<br /><br /> 16 [b]<br /><br /> 16 [b]<br /><br /> Undefined|–<br /><br /> 01S07<br /><br /> –<br /><br /> –<br /><br /> 22018|  
|Alle C-Intervall Typen|Der Datenwert ist ein gültiger *Intervall Wert*. keine abkürzen<br /><br /> Der Datenwert ist ein gültiger *Intervall Wert*. Abschneiden von mindestens einem nachfolgenden Feld<br /><br /> Daten sind gültiges Intervall. die signifikante Genauigkeit des führenden Felds ist verloren gegangen.<br /><br /> Der Datenwert ist kein gültiger Intervall Wert.|Data<br /><br /> Abgeschnittene Daten<br /><br /> Undefined<br /><br /> Undefined|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes<br /><br /> Undefined<br /><br /> Undefined|–<br /><br /> 01S07<br /><br /> 22015<br /><br /> 22018|  
|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|

 [a] der Wert von *BufferLength* wird für diese Konvertierung ignoriert. Der Treiber geht davon aus, dass die Größe von **targetvalueptr* die Größe des C-Datentyps ist.  
  
 [b] Dies ist die Größe des entsprechenden C-Datentyps.  
  
 [c] der Uhrzeit Teil des *timestamp-Werts* ist abgeschnitten.  
  
 [d] der Datums Teil des *timestamp-Werts* wird ignoriert.  
  
 [e] der Teil der Sekundenbruchteile des Zeitstempels wird abgeschnitten.  
  
 [f] die Zeitfelder der Zeitstempel Struktur werden auf 0 (null) festgelegt.  
  
 [g] die Datumsfelder der Zeitstempel Struktur werden auf das aktuelle Datum festgelegt.  

**Zusätzliche Leerzeichen**

Führende und nachfolgende Leerzeichen werden ignoriert, wenn SQL-Zeichendaten in einen der folgenden Typen konvertiert werden:

- date
- NUMERIC
- time
- timestamp
- Intervall-C-Daten
