---
title: 'SQL zu C: Zeitstempel | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2019
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 552bab585e4480fd922c9b9a6b112830f5c11ad9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296350"
---
# <a name="sql-to-c-timestamp"></a>SQL zu C: Zeitstempel

Der Bezeichner für den Datentyp ODBC SQL ist der folgende:

- SQL_TYPE_TIMESTAMP  

Die folgende Tabelle zeigt die ODBC C-Datentypen, in die SQL-Zeitstempeldaten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|C-Typ-Idonid|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > Zeichenbytelänge<br /><br /> 20 <= *BufferLength* <= Zeichenbytelänge<br /><br /> *BufferLength* < 20|Daten<br /><br /> Abgeschnittene Daten[b]<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > Zeichenlänge<br /><br /> 20 <= *BufferLength* <= Zeichenlänge<br /><br /> *BufferLength* < 20|Daten<br /><br /> Abgeschnittene Daten[b]<br /><br /> Nicht definiert|Länge der Daten in Zeichen<br /><br /> Länge der Daten in Zeichen<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Bytelänge der Daten <= *BufferLength*<br /><br /> Byte-Länge der Daten > *BufferLength*|Daten<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Zeitteil des Zeitstempels ist Null[a]<br /><br /> Der Zeitteil des Zeitstempels ist ungleich Null[a]|Daten<br /><br /> Abgeschnittene Daten[c]|6[f]<br /><br /> 6[f]|–<br /><br /> 01S07|  
|SQL_C_TYPE_TIME|Bruchsekundenanteil des Zeitstempels ist Null[a]<br /><br /> Bruchsekundenanteil des Zeitstempels ist ungleich Null[a]|Daten[d]<br /><br /> Abgeschnittene Daten[d], [e]|6[f]<br /><br /> 6[f]|–<br /><br /> 01S07|  
|SQL_C_TYPE_TIMESTAMP|Bruchsekundenanteil des Zeitstempels wird nicht abgeschnitten[a]<br /><br /> Bruchsekundenanteil des Zeitstempels wird abgeschnitten[a]|Daten[e]<br /><br /> Abgeschnittene Daten[e]|16[f]<br /><br /> 16[f]|–<br /><br /> 01S07|  

 [a] Der Wert von *BufferLength* wird für diese Konvertierung ignoriert. Der Treiber geht davon aus, dass die Größe von **TargetValuePtr* die Größe des C-Datentyps ist.  
  
 [b] Die Sekundenbruchteile des Zeitstempels werden abgeschnitten.  
  
 [c] Der Zeitteil des Zeitstempels wird abgeschnitten.  
  
 [d] Der Datumsteil des Zeitstempels wird ignoriert.  
  
 [e] Der Bruchteil der Sekunden des Zeitstempels wird abgeschnitten.  
  
 [f] Dies ist die Größe des entsprechenden C-Datentyps.  

Wenn Timestamp SQL-Daten in Zeichen C-Daten konvertiert werden, befindet sich die resultierende Zeichenfolge im "*yyyy*-*mm*-*dd* *hh*:*mm*:*ss*[.* f...*]" Format, in dem bis zu neun Ziffern für Bruchteilsekunden verwendet werden können. Dieses Format wird von der Windows®-Ländereinstellung nicht beeinflusst. (Mit Ausnahme des Dezimalkommas und der Sekundenbruchteile muss das gesamte Format verwendet werden, unabhängig von der Genauigkeit des SQL-Datentyps mit Zeitstempel.)
