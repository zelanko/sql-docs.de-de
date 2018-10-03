---
title: 'SQL zu C: Zeitstempel | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- timestamp data type [ODBC]
- converting data from SQL to C types [ODBC], timestamp
- data conversions from SQL to C types [ODBC], timestamp
ms.assetid: 6a0617cf-d8c0-4316-8bb4-e6ddb45d7bf1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47a0fa22e2d5810faae10ca4ae620bb2a57bb856
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724418"
---
# <a name="sql-to-c-timestamp"></a>SQL zu C: Zeitstempel
Der Bezeichner für den Timestamp ODBC-SQL-Datentyp ist:  
  
 SQL_TYPE_TIMESTAMP  
  
 Die folgende Tabelle zeigt die ODBC-C-Datentypen, die in denen Timestamp-SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typ-ID|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > Zeichen Länge in Byte<br /><br /> 20 < = *Pufferlänge* < = Zeichen-Byte-Länge<br /><br /> *BufferLength* < 20|data<br /><br /> Abgeschnittene Daten [b]<br /><br /> Nicht definiert|Länge der Daten in bytes<br /><br /> Länge der Daten in bytes<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > Zeichenlänge<br /><br /> 20 < = *Pufferlänge* < = Länge von Zeichen<br /><br /> *BufferLength* < 20|data<br /><br /> Abgeschnittene Daten [b]<br /><br /> Nicht definiert|Länge der Daten in Zeichen<br /><br /> Länge der Daten in Zeichen<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Die Bytelänge der Daten < = *Pufferlänge*<br /><br /> Die Bytelänge der Daten > *Pufferlänge*|data<br /><br /> Nicht definiert|Länge der Daten in bytes<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Der Uhrzeitteil des Zeitstempels ist 0 (null) [a]<br /><br /> Der Uhrzeitteil des Zeitstempels ist ungleich Null [a]|data<br /><br /> Abgeschnittene Daten [c]|6 [f]<br /><br /> 6 [f]|–<br /><br /> 01 S 07|  
|SQL_C_TYPE_TIME|Bereich der Sekundenbruchteile von Timestamp ist 0 (null) [a]<br /><br /> Bereich der Sekundenbruchteile von Timestamp ist ungleich Null [a]|Daten [d]<br /><br /> Abgeschnittene Daten [d], [e]|6 [f]<br /><br /> 6 [f]|–<br /><br /> 01 S 07|  
_C_TYPE_TIMESTAMP|Bereich der Sekundenbruchteile von Timestamp wird nicht abgeschnitten, [a]<br /><br /> Bereich der Sekundenbruchteile von Timestamp wird abgeschnitten, [a]|Daten [e]<br /><br /> Abgeschnittene Daten [e]|16 [f]<br /><br /> 16 [f]|–<br /><br /> 01 S 07|  
  
 [a] den Wert der *Pufferlänge* für diese Konvertierung ignoriert wird. Der Treiber setzt voraus, dass die Größe des **TargetValuePtr* ist die Größe der C-Datentyp.  
  
 [b] die Sekundenbruchteile des Zeitstempels werden abgeschnitten.  
  
 [c] der Uhrzeitteil des Zeitstempels wird abgeschnitten.  
  
 [d] der Datumsteil des Zeitstempels wird ignoriert.  
  
 [e] der Bereich der Sekundenbruchteile des Zeitstempels wird abgeschnitten.  
  
 [f] Dies ist die Größe des entsprechenden C-Datentyp.  
  
 Wenn SQL-Zeitstempeldaten in C-Zeichendaten konvertiert werden, wird die resultierende Zeichenfolge der "*JJJJ*-*mm*-*TT* *Hh* :*mm*:*ss*[.*f...*] "-Format, in denen bis zu neun Ziffern für Sekundenbruchteile verwendet werden kann. Dieses Format wird von der Einstellung für Land Windows® nicht beeinflusst. (Mit Ausnahme des Dezimalzeichens und Bruchteilen von Sekunden, muss die gesamte Format, unabhängig von der Genauigkeit von der SQL-Datentyp Timestamp verwendet werden.)
