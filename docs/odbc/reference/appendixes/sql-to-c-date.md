---
title: 'SQL in C: Datum | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], date
- date data type [ODBC]
- data conversions from SQL to C types [ODBC], date
ms.assetid: 703c7960-9cf4-4d7a-9920-53b29c184f97
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fe0c30f0f0fbf0ea695d79387fdec3694a54ebca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63151271"
---
# <a name="sql-to-c-date"></a>SQL in C: date
Der Bezeichner für die Date-ODBC-SQL-Datentyp ist:  
  
 SQL_TYPE_DATE  
  
 Die folgende Tabelle zeigt die ODBC-C-Datentypen, die in denen Datum SQL-Daten konvertiert werden kann. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typ-ID|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > Zeichen Länge in Byte<br /><br /> 11 < = *Pufferlänge* < = Zeichen-Byte-Länge<br /><br /> *BufferLength* < 11|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|10<br /><br /> Länge der Daten in bytes<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > Zeichenlänge<br /><br /> 11 < = *Pufferlänge* < = Länge von Zeichen<br /><br /> *BufferLength* < 11|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|10<br /><br /> Länge der Daten in Zeichen<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Die Bytelänge der Daten < = *Pufferlänge*<br /><br /> Die Bytelänge der Daten > *Pufferlänge*|Daten<br /><br /> Nicht definiert|Länge der Daten in bytes<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Keine [a]|Daten|6[c]|–|  
|SQL_C_TYPE_TIMESTAMP|Keine [a]|Daten [b]|16[c]|–|  
  
 [a] den Wert der *Pufferlänge* für diese Konvertierung ignoriert wird. Der Treiber setzt voraus, dass die Größe des **TargetValuePtr* ist die Größe der C-Datentyp.  
  
 [b] Zeitfelder der Timestamp-Struktur werden auf 0 (null) festgelegt.  
  
 [c] Dies ist die Größe des entsprechenden C-Datentyp.  
  
 Wenn in Zeichendaten C Datum SQL-Daten konvertiert wird, wird die resultierende Zeichenfolge der "*JJJJ*-*mm*-*TT*" Format. Dieses Format wird von der Einstellung für Land Windows® nicht beeinflusst.
