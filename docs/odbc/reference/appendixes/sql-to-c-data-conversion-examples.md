---
title: SQL to C Data Konvertierung Beispielen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from SQL to C types [ODBC], examples
- converting data from SQL to C types [ODBC], examples
ms.assetid: 0190c76c-7f9b-42f4-be9d-cef7284840fd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 84161501d3d705ef60559340502ee702e7c28437
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056892"
---
# <a name="sql-to-c-data-conversion-examples"></a>Beispiele für die Datenkonvertierung von SQL zu C

Die Beispiele in der folgenden Tabelle veranschaulichen, wie der Treiber SQL-Daten in C-Daten konvertiert:  
  
|SQL-Typ<br /><br /> Bezeichner (identifier)|SQL data<br /><br /> Wert|C-Typ<br /><br /> Bezeichner (identifier)|Puffer<br /><br /> Länge|**TargetValuePtr*|SQLSTATE|  
|-----------------------------|------------------------|---------------------------|-----------------------|------------------------|--------------|  
|SQL_CHAR|abcdef|SQL_C_CHAR|7|abcdef\0 [a]|n/v|  
|SQL_CHAR|abcdef|SQL_C_CHAR|6|abcde\0 [a]|01004|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|8|1234.56\0 [a]|n/v|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|5|1234\0 [a]|01004|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|4|----|22003|  
|SQL_DECIMAL|1234.56|SQL_C_FLOAT|wird ignoriert.|1234.56|n/v|  
|SQL_DECIMAL|1234.56|SQL_C_SSHORT|wird ignoriert.|1234|01S07|  
|SQL_DECIMAL|1234.56|SQL_C_STINYINT|wird ignoriert.|----|22003|  
|SQL_DOUBLE|1.2345678|SQL_C_DOUBLE|wird ignoriert.|1.2345678|n/v|  
|SQL_DOUBLE|1.2345678|SQL_C_FLOAT|wird ignoriert.|1.234567|n/v|  
|SQL_DOUBLE|1.2345678|SQL_C_STINYINT|wird ignoriert.|1|n/v|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|11|1992-12-31\0 [a]|n/v|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|10|-----|22003|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_TIMESTAMP|wird ignoriert.|1992,12,31, 0,0,0,0[b]|n/v|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|23|1992-12-31 23:45:55.12\0[a]|n/v|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|22|1992-12-31 23:45:55.1\0[a]|01004|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|18|----|22003|  
  
 [a] "\0" stellt einen Null-Terminierung Byte dar. Der Treiber terminiert Null-immer SQL_C_CHAR-Daten.  
  
 [b] die Zahlen in dieser Liste sind die Zahlen in den Feldern der TIMESTAMP_STRUCT Struktur gespeichert.
