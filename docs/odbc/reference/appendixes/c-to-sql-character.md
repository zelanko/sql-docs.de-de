---
title: 'C zu SQL: Zeichen | Microsoft Docs'
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
ms.openlocfilehash: acde0d2a79492607185d56d3082797c79a100fa2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292031"
---
# <a name="c-to-sql-character"></a>C zu SQL: Zeichen
Die Bezeichner für den Datentyp ODBC C sind:  
  
 SQL_C_CHAR  
  
 SQL_C_WCHAR  
  
 Die folgende Tabelle zeigt die ODBC SQL-Datentypen, in die C-Zeichendaten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
> [!NOTE]  
>  Wenn Zeichen-C-Daten in Unicode SQL-Daten konvertiert werden, muss die Länge der Unicode-Daten eine gerade Zahl sein.  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Bytelänge der Daten <= Spaltenlänge.<br /><br /> Bytelänge der Daten > Spaltenlänge.|–<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Zeichenlänge der Daten <= Spaltenlänge.<br /><br /> Zeichenlänge der Daten > Spaltenlänge.|–<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER SQL_BIGINT|Daten, die ohne Abschneide konvertiert werden<br /><br /> Daten, die mit Abschneiden von Bruchziffern konvertiert werden[e]<br /><br /> Die Konvertierung von Daten würde zu einem Verlust ganzer (im Gegensatz zu bruchstückten) Ziffern führen[e]<br /><br /> Der Datenwert ist kein *numerisches Literal*|–<br /><br /> 22001<br /><br /> 22001<br /><br /> 22018|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Die Daten liegen im Bereich des Datentyps, in den die Nummer konvertiert wird.<br /><br /> Die Daten liegen außerhalb des Bereichs des Datentyps, in den die Nummer konvertiert wird.<br /><br /> Der Datenwert ist kein *numerisches Literal*|–<br /><br /> 22003<br /><br /> 22018|  
|SQL_BIT|Die Daten sind 0 oder 1<br /><br /> Die Daten sind größer als 0, kleiner als 2 und nicht gleich 1<br /><br /> Die Daten sind kleiner als 0 oder größer oder gleich 2<br /><br /> Daten sind kein *numerisches Literal*|–<br /><br /> 22001<br /><br /> 22003<br /><br /> 22018|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|(Byte-Länge der Daten) / 2 <= Spaltenbytelänge<br /><br /> (Byte-Länge der Daten) / 2 > Spaltenbytelänge<br /><br /> Der Datenwert ist kein hexadezimaler Wert|–<br /><br /> 22001<br /><br /> 22018|  
|SQL_TYPE_DATE|Datenwert ist ein gültiges *ODBC-Datumsliteral*<br /><br /> Der Datenwert ist ein gültiges *ODBC-Timestamp-Literal*; Zeitanteil ist Null<br /><br /> Der Datenwert ist ein gültiges *ODBC-Timestamp-Literal*; Zeitanteil ist ungleich Null[a]<br /><br /> Der Datenwert ist kein gültiges *ODBC-Datumsliteral* oder *ODBC-Timestamp-Literal*|–<br /><br /> –<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIME|Der Datenwert ist ein gültiges *ODBC-Zeitliteral*<br /><br /> Der Datenwert ist ein gültiges *ODBC-Timestamp-Literal*; Bruchsekundenanteil ist Null[b]<br /><br /> Der Datenwert ist ein gültiges *ODBC-Timestamp-Literal*; Bruchsekundenanteil ist ungleich Null[b]<br /><br /> Der Datenwert ist kein gültiges *ODBC-Zeitliteral* oder *ODBC-Timestamp-Literal*|–<br /><br /> –<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIMESTAMP|Der Datenwert ist ein gültiges *ODBC-Timestamp-Literal*; Bruchsekundenanteil nicht abgeschnitten<br /><br /> Der Datenwert ist ein gültiges *ODBC-Timestamp-Literal*; Bruchsekunden-Portion abgeschnitten<br /><br /> Datenwert ist ein gültiges *ODBC-Datumsliteral*[c]<br /><br /> Der Datenwert ist ein gültiges *ODBC-Zeitliteral*[d]<br /><br /> Der Datenwert ist kein gültiges *ODBC-Datumsliteral*, *ODBC-time-literal*oder *ODBC-timestamp-literal*|–<br /><br /> 22008<br /><br /> –<br /><br /> –<br /><br /> 22018|  
|Alle SQL-Intervalltypen|Der Datenwert ist ein gültiger *Intervallwert;* es tritt kein Abschneiden auf<br /><br /> Der Datenwert ist ein gültiger *Intervallwert;* Der Wert in einem der Felder wird abgeschnitten<br /><br /> Der Datenwert ist kein gültiges Intervallliteral|–<br /><br /> 22015<br /><br /> 22018|  
  
 [a] Der Zeitteil des Zeitstempels wird abgeschnitten.  
  
 [b] Der Datumsteil des Zeitstempels wird ignoriert.  
  
 [c] Der Zeitteil des Zeitstempels ist auf Null gesetzt.  
  
 [d] Der Datumsteil des Zeitstempels wird auf das aktuelle Datum festgelegt.  
  
 [e] Der Treiber/die Datenquelle wartet effektiv, bis die gesamte Zeichenfolge empfangen wurde (auch wenn die Zeichendaten durch Aufrufe von **SQLPutData**in Teilen gesendet werden), bevor versucht wird, die Konvertierung durchzuführen.  
  
 Wenn Zeichen C-Daten in numerische, Datums-, Uhrzeit- oder Zeitstempel-SQL-Daten konvertiert werden, werden führende und nachfolgende Leerzeichen ignoriert.  
  
 Wenn Zeichen-C-Daten in binäre SQL-Daten konvertiert werden, werden alle zwei Bytes an Zeichendaten in ein einzelnes Byte (8 Bit) binärer Daten konvertiert. Jedes einzelne Byte von Zeichendaten stellt eine Zahl in hexadezimaler Form dar. Beispielsweise wird "01" in eine binäre 00000001 und "FF" in eine binäre 11111111 konvertiert.  
  
 Der Treiber konvertiert immer Paare von hexadezimalen Ziffern in einzelne Bytes und ignoriert das Null-Beendigungsbyte. Aus diesem Grund wird, wenn die Länge der Zeichenfolge ungerade ist, das letzte Byte der Zeichenfolge (mit Ausnahme des Null-Beendigungsbytes, falls vorhanden), nicht konvertiert.  
  
> [!NOTE]  
>  Anwendungsentwickler nafern davon ab, Zeichen-C-Daten an einen binären SQL-Datentyp zu binden. Diese Konvertierung ist in der Regel ineffizient und langsam.
