---
title: 'SQL zu C: Zeit | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ebd146abf650861099a40bf91b2641df768b343d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296380"
---
# <a name="sql-to-c-time"></a>SQL zu C: Uhrzeit
Der Bezeichner für den OdBC SQL-Datentyp lautet:  
  
 SQL_TYPE_TIME  
  
 Die folgende Tabelle zeigt die ODBC C-Datentypen, in die SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typ-Idonid|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > Zeichenbytelänge<br /><br /> *9* <= *BufferLength* <= Zeichenbytelänge<br /><br /> *BufferLength* < 9|Daten<br /><br /> Abgeschnittene Daten[a]<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > Zeichenlänge<br /><br /> *9* <= *BufferLength* <= Zeichenlänge<br /><br /> *BufferLength* < 9|Daten<br /><br /> Abgeschnittene Daten[a]<br /><br /> Nicht definiert|Länge der Daten in Zeichen<br /><br /> Länge der Daten in Zeichen<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Bytelänge der Daten <= *BufferLength*<br /><br /> Byte-Länge der Daten > *BufferLength*|Daten<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_TYPE_TIME|Keine[b]|Daten|6[d]|–|  
|SQL_C_TYPE_TIMESTAMP|Keine[b]|Daten[c]|16[d]|–|  
  
 [a] Die Bruchteilsekunden der Zeit werden abgeschnitten.  
  
 [b] Der Wert von *BufferLength* wird für diese Konvertierung ignoriert. Der Treiber geht davon aus, dass die Größe von **TargetValuePtr* die Größe des C-Datentyps ist.  
  
 [c] Die Datumsfelder der Zeitstempelstruktur werden auf das aktuelle Datum und das Sekundenbruchteilfeld der Zeitstempelstruktur auf Null gesetzt.  
  
 [d] Dies ist die Größe des entsprechenden C-Datentyps.  
  
 Wenn SQL-Daten der Zeit in Zeichen-C-Daten konvertiert werden, befindet sich die resultierende Zeichenfolge im Format "*hh*:*mm*:*ss*". Dieses Format wird von der Windows®-Ländereinstellung nicht beeinflusst.
