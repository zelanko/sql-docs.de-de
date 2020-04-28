---
title: Beispiele für die SQL-zu-C-Datenkonvertierung | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96b10dd93c807aaa49a7e10e198f789fb47ccdeb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296650"
---
# <a name="sql-to-c-data-conversion-examples"></a>Beispiele für die Datenkonvertierung von SQL zu C

Die in der folgenden Tabelle gezeigten Beispiele veranschaulichen, wie der Treiber SQL-Daten in C-Daten konvertiert:  
  
|SQL-Typ<br /><br /> Bezeichner|SQL data<br /><br /> value|C-Typ<br /><br /> Bezeichner|Buffer<br /><br /> length|**Targetvalueptr*|SQLSTATE|  
|-----------------------------|------------------------|---------------------------|-----------------------|------------------------|--------------|  
|SQL_CHAR|abcdef|SQL_C_CHAR|7|abcdef\0 [a]|Nicht zutreffend|  
|SQL_CHAR|abcdef|SQL_C_CHAR|6|abcde\0 [a]|01004|  
|SQL_DECIMAL|1234,56|SQL_C_CHAR|8|1234.56 \ 0 [a]|Nicht zutreffend|  
|SQL_DECIMAL|1234,56|SQL_C_CHAR|5|1234 \ 0 [a]|01004|  
|SQL_DECIMAL|1234,56|SQL_C_CHAR|4|----|22003|  
|SQL_DECIMAL|1234,56|SQL_C_FLOAT|wird ignoriert.|1234,56|Nicht zutreffend|  
|SQL_DECIMAL|1234,56|SQL_C_SSHORT|wird ignoriert.|1234|01S07|  
|SQL_DECIMAL|1234,56|SQL_C_STINYINT|wird ignoriert.|----|22003|  
|SQL_DOUBLE|1,2345678|SQL_C_DOUBLE|wird ignoriert.|1,2345678|Nicht zutreffend|  
|SQL_DOUBLE|1,2345678|SQL_C_FLOAT|wird ignoriert.|1,234567|Nicht zutreffend|  
|SQL_DOUBLE|1,2345678|SQL_C_STINYINT|wird ignoriert.|1|Nicht zutreffend|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|11|1992-12-31 \ 0 [a]|Nicht zutreffend|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|10|-----|22003|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_TIMESTAMP|wird ignoriert.|1992, 12, 31, 0, 0, 0, 0 [b]|Nicht zutreffend|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|23|1992-12-31 23:45:55.12 \ 0 [a]|Nicht zutreffend|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|22|1992-12-31 23:45:55,1 \ 0 [a]|01004|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|18|----|22003|  
  
 [a] "\ 0" stellt ein Byte mit NULL-Terminierung dar. Der Treiber beendet SQL_C_CHAR Daten immer NULL.  
  
 [b] die Zahlen in dieser Liste sind die Zahlen, die in den Feldern der TIMESTAMP_STRUCT Struktur gespeichert werden.
