---
title: 'SQL zu C: Zeit | Microsoft-Dokumentation'
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296380"
---
# <a name="sql-to-c-time"></a>SQL zu C: Uhrzeit
Der Bezeichner für den ODBC-SQL-Datentyp "Time" lautet:  
  
 SQL_TYPE_TIME  
  
 In der folgenden Tabelle werden die ODBC-C-Datentypen angezeigt, in die SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typbezeichner|Test|**Targetvalueptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|Länge des *pufflength* -> Zeichens<br /><br /> *9* <= *BufferLength* <= Zeichen Byte Länge<br /><br /> *BufferLength* < 9|Daten<br /><br /> Abgeschnittene Daten [a]<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes<br /><br /> Nicht definiert|Nicht zutreffend<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Länge der *BufferLength* -> Zeichen<br /><br /> *9* <= *BufferLength* <= Zeichen Länge<br /><br /> *BufferLength* < 9|Daten<br /><br /> Abgeschnittene Daten [a]<br /><br /> Nicht definiert|Länge der Daten in Zeichen<br /><br /> Länge der Daten in Zeichen<br /><br /> Nicht definiert|Nicht zutreffend<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Byte Länge der Daten <= *BufferLength*<br /><br /> Byte Länge der Daten > *BufferLength*|Daten<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Nicht definiert|Nicht zutreffend<br /><br /> 22003|  
|SQL_C_TYPE_TIME|Keine [b]|Daten|6 [d]|Nicht zutreffend|  
|SQL_C_TYPE_TIMESTAMP|Keine [b]|Daten [c]|16 [d]|Nicht zutreffend|  
  
 [a] die Sekundenbruchteile der Zeit werden abgeschnitten.  
  
 [b] der Wert von *BufferLength* wird für diese Konvertierung ignoriert. Der Treiber geht davon aus, dass die Größe von **targetvalueptr* die Größe des C-Datentyps ist.  
  
 [c] die Datumsfelder der Zeitstempel Struktur werden auf das aktuelle Datum festgelegt, und das Feld für die Sekundenbruchteile der Zeitstempel Struktur wird auf 0 (null) festgelegt.  
  
 [d] Dies ist die Größe des entsprechenden C-Datentyps.  
  
 Wenn SQL-Daten in Zeichen-C-Daten konvertiert werden, befindet sich die resultierende Zeichenfolge im Format "*HH*:*mm*:*SS*". Dieses Format wird von der Einstellung für das Windows-® Land nicht beeinträchtigt.
