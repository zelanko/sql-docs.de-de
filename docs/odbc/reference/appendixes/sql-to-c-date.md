---
title: 'SQL zu C: Date | Microsoft-Dokumentation'
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
ms.openlocfilehash: d282798a31ac9059ed3c1901ea01f1f3104f09c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68056881"
---
# <a name="sql-to-c-date"></a>SQL zu C: Datum
Der Bezeichner für den ODBC-SQL-Datentyp "Date" lautet:  
  
 SQL_TYPE_DATE  
  
 In der folgenden Tabelle werden die ODBC-C-Datentypen angezeigt, in die SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typbezeichner|Test|**Targetvalueptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|Länge des *pufflength* -> Zeichens<br /><br /> 11 <= *BufferLength* <= Zeichen Byte Länge<br /><br /> *BufferLength* < 11|Data<br /><br /> Abgeschnittene Daten<br /><br /> Undefined|10<br /><br /> Länge der Daten in Bytes<br /><br /> Undefined|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Länge der *BufferLength* -> Zeichen<br /><br /> 11 <= *BufferLength* <= Zeichen Länge<br /><br /> *BufferLength* < 11|Data<br /><br /> Abgeschnittene Daten<br /><br /> Undefined|10<br /><br /> Länge der Daten in Zeichen<br /><br /> Undefined|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Byte Länge der Daten <= *BufferLength*<br /><br /> Byte Länge der Daten > *BufferLength*|Data<br /><br /> Undefined|Länge der Daten in Bytes<br /><br /> Undefined|–<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Keine [a]|Data|6 [c]|–|  
|SQL_C_TYPE_TIMESTAMP|Keine [a]|Daten [b]|16 [c]|–|  
  
 [a] der Wert von *BufferLength* wird für diese Konvertierung ignoriert. Der Treiber geht davon aus, dass die Größe von **targetvalueptr* die Größe des C-Datentyps ist.  
  
 [b] die Zeitfelder der Zeitstempel Struktur werden auf 0 (null) festgelegt.  
  
 [c] Dies ist die Größe des entsprechenden c-Datentyps.  
  
 Wenn Datums-SQL-Daten in Zeichen-C-Daten konvertiert werden, liegt die resultierende Zeichenfolge im Format "*JJJJ*-*mm*-*DD*". Dieses Format wird von der Einstellung für das Windows-® Land nicht beeinträchtigt.
