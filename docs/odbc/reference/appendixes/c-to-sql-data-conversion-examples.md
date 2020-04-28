---
title: Beispiele für die C-zu-SQL-Datenkonvertierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], examples
- data conversions from C to SQL types [ODBC], examples
ms.assetid: 9f390afc-d8b8-4286-b559-98b3b8781f3d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0e21654f183946675c63cee10a3c08754e1508f5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81291990"
---
# <a name="c-to-sql-data-conversion-examples"></a>Beispiele für die Datenkonvertierung von C zu SQL
In den folgenden Beispielen wird veranschaulicht, wie der Treiber C-Daten in SQL-Daten konvertiert:  
  
|C-Typbezeichner|C-Datenwert|SQL-Typ<br /><br /> Bezeichner|Column<br /><br /> length|SQL data<br /><br /> value|SQLSTATE|  
|-----------------------|------------------|-----------------------------|-----------------------|------------------------|--------------|  
|SQL_C_CHAR|abcdef\0 [a]|SQL_CHAR|6|abcdef|Nicht zutreffend|  
|SQL_C_CHAR|abcdef\0 [a]|SQL_CHAR|5|abcde|22001|  
|SQL_C_CHAR|1234.56 \ 0 [a]|SQL_DECIMAL|8 [b]|1234,56|Nicht zutreffend|  
|SQL_C_CHAR|1234.56 \ 0 [a]|SQL_DECIMAL|7 [b]|1234,5|22001|  
|SQL_C_CHAR|1234.56 \ 0 [a]|SQL_DECIMAL|4|----|22003|  
|SQL_C_FLOAT|1234,56|SQL_FLOAT|Nicht zutreffend|1234,56|Nicht zutreffend|  
|SQL_C_FLOAT|1234,56|SQL_INTEGER|Nicht zutreffend|1234|22001|  
|SQL_C_FLOAT|1234,56|SQL_TINYINT|Nicht zutreffend|----|22003|  
|SQL_C_TYPE_DATE|1992, 12, 31 [c]|SQL_CHAR|10|1992-12-31|Nicht zutreffend|  
|SQL_C_TYPE_DATE|1992, 12, 31 [c]|SQL_CHAR|9|----|22003|  
|SQL_C_TYPE_DATE|1992, 12, 31 [c]|SQL_TIMESTAMP|Nicht zutreffend|1992-12-31 00:00:00.0|Nicht zutreffend|  
|SQL_C_TYPE_TIMESTAMP|1992, 12, 31, 23, 45, 55, 120000000 [d]|SQL_CHAR|22|1992-12-31 23:45:55.12|Nicht zutreffend|  
|SQL_C_TYPE_TIMESTAMP|1992, 12, 31, 23, 45, 55, 120000000 [d]|SQL_CHAR|21|1992-12-31 23:45:55,1|22001|  
|SQL_C_TYPE_TIMESTAMP|1992, 12, 31, 23, 45, 55, 120000000 [d]|SQL_CHAR|18|----|22003|  
  
 [a] "\ 0" stellt ein Byte mit NULL-Terminierung dar. Das NULL-Terminierungs Byte ist nur erforderlich, wenn die Länge der Daten SQL_NTS ist.  
  
 [b] zusätzlich zu Bytes für Zahlen ist ein Byte für ein Vorzeichen erforderlich, und für den Dezimaltrennzeichen ist ein anderes Byte erforderlich.  
  
 [c] die Zahlen in dieser Liste sind die Zahlen, die in den Feldern der SQL_DATE_STRUCT Struktur gespeichert werden.  
  
 [d] die Zahlen in dieser Liste sind die Zahlen, die in den Feldern der SQL_TIMESTAMP_STRUCT Struktur gespeichert werden.
