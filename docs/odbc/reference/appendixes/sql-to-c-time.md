---
title: 'SQL in C: Zeit | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], time
- time data type [ODBC]
- data conversions from SQL to C types [ODBC], time
ms.assetid: 6dc59973-7bb5-40f1-87c8-5bf68b3bf2ee
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e028502bd7bc6ac1a81006d340b6ce606a0ae337
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63259595"
---
# <a name="sql-to-c-time"></a>SQL in C: Uhrzeit
Der Bezeichner für die Zeit, die ODBC-SQL-Datentyp ist:  
  
 SQL_TYPE_TIME  
  
 Die folgende Tabelle zeigt die ODBC-C-Datentypen, die auf die Zeit SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typ-ID|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > Zeichen Länge in Byte<br /><br /> *9* <= *Pufferlänge* < = Zeichen-Byte-Länge<br /><br /> *BufferLength* < 9|Daten<br /><br /> [A] abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten in bytes<br /><br /> Länge der Daten in bytes<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > Zeichenlänge<br /><br /> *9* <= *Pufferlänge* < = Länge von Zeichen<br /><br /> *BufferLength* < 9|Daten<br /><br /> [A] abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten in Zeichen<br /><br /> Länge der Daten in Zeichen<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Die Bytelänge der Daten < = *Pufferlänge*<br /><br /> Die Bytelänge der Daten > *Pufferlänge*|Daten<br /><br /> Nicht definiert|Länge der Daten in bytes<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_TYPE_TIME|Keine [b]|Daten|6 [d]|–|  
|SQL_C_TYPE_TIMESTAMP|Keine [b]|Daten [c]|16 [d]|–|  
  
 [a] die Sekundenbruchteile der Zeit werden abgeschnitten.  
  
 [b] den Wert der *Pufferlänge* für diese Konvertierung ignoriert wird. Der Treiber setzt voraus, dass die Größe des **TargetValuePtr* ist die Größe der C-Datentyp.  
  
 [c] die Datumsfelder der Timestamp-Struktur werden auf das aktuelle Datum festgelegt, und das Feld Sekundenbruchteile von Timestamp-Struktur auf 0 (null) festgelegt ist.  
  
 [d] Dies ist die Größe des entsprechenden C-Datentyp.  
  
 Wenn SQL Zeitdaten in Zeichendaten C konvertiert werden, wird die resultierende Zeichenfolge der "*Hh*:*mm*:*ss*" Format. Dieses Format wird von der Einstellung für Land Windows® nicht beeinflusst.
