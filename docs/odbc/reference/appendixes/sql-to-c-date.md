---
title: 'SQL zu C: Datum | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe9656c0c02c0ff5a10029525da3d38280530cc3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296530"
---
# <a name="sql-to-c-date"></a>SQL zu C: Datum
Der Bezeichner für den ODBC SQL-Datentyp lautet:  
  
 SQL_TYPE_DATE  
  
 Die folgende Tabelle zeigt die ODBC C-Datentypen, in die SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typ-Idonid|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > Zeichenbytelänge<br /><br /> 11 <= *BufferLength* <= Zeichenbytelänge<br /><br /> *BufferLength* < 11|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|10<br /><br /> Länge der Daten in Bytes<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > Zeichenlänge<br /><br /> 11 <= *BufferLength* <= Zeichenlänge<br /><br /> *BufferLength* < 11|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|10<br /><br /> Länge der Daten in Zeichen<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Bytelänge der Daten <= *BufferLength*<br /><br /> Byte-Länge der Daten > *BufferLength*|Daten<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Keine[a]|Daten|6[c]|–|  
|SQL_C_TYPE_TIMESTAMP|Keine[a]|Daten[b]|16[c]|–|  
  
 [a] Der Wert von *BufferLength* wird für diese Konvertierung ignoriert. Der Treiber geht davon aus, dass die Größe von **TargetValuePtr* die Größe des C-Datentyps ist.  
  
 [b] Die Zeitfelder der Zeitstempelstruktur werden auf Null gesetzt.  
  
 [c] Dies ist die Größe des entsprechenden C-Datentyps.  
  
 Wenn SQL-Daten in Zeichen-C-Daten konvertiert werden, befindet sich die resultierende Zeichenfolge im Format "*yyyy*-*mm*-*dd*". Dieses Format wird von der Windows®-Ländereinstellung nicht beeinflusst.
