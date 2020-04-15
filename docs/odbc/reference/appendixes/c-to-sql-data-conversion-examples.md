---
title: C-zu-SQL-Datenkonvertierungsbeispiele | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291990"
---
# <a name="c-to-sql-data-conversion-examples"></a>Beispiele für die Datenkonvertierung von C zu SQL
Die folgenden Beispiele veranschaulichen, wie der Treiber C-Daten in SQL-Daten konvertiert:  
  
|C-Typ-Idonid|C-Datenwert|SQL-Typ<br /><br /> Bezeichner|Column<br /><br /> length|SQL data<br /><br /> value|SQLSTATE|  
|-----------------------|------------------|-----------------------------|-----------------------|------------------------|--------------|  
|SQL_C_CHAR|abcdef-0[a]|SQL_CHAR|6|abcdef|–|  
|SQL_C_CHAR|abcdef-0[a]|SQL_CHAR|5|Abcde|22001|  
|SQL_C_CHAR|1234.56-0[a]|SQL_DECIMAL|8[b]|1234.56|–|  
|SQL_C_CHAR|1234.56-0[a]|SQL_DECIMAL|7[b]|1234.5|22001|  
|SQL_C_CHAR|1234.56-0[a]|SQL_DECIMAL|4|----|22003|  
|SQL_C_FLOAT|1234.56|SQL_FLOAT|–|1234.56|–|  
|SQL_C_FLOAT|1234.56|SQL_INTEGER|–|1234|22001|  
|SQL_C_FLOAT|1234.56|SQL_TINYINT|–|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31[c]|SQL_CHAR|10|1992-12-31|–|  
|SQL_C_TYPE_DATE|1992,12,31[c]|SQL_CHAR|9|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31[c]|SQL_TIMESTAMP|–|1992-12-31 00:00:00.0|–|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000[d]|SQL_CHAR|22|1992-12-31 23:45:55.12|–|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000[d]|SQL_CHAR|21|1992-12-31 23:45:55.1|22001|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000[d]|SQL_CHAR|18|----|22003|  
  
 [a] "-0" stellt ein Null-Beendigungs-Byte dar. Das Null-Beendigungs-Byte ist nur erforderlich, wenn die Länge der Daten SQL_NTS ist.  
  
 [b] Zusätzlich zu Bytes für Zahlen ist ein Byte für ein Zeichen und ein weiteres Byte für das Dezimalkomma erforderlich.  
  
 [c] Die Zahlen in dieser Liste sind die Zahlen, die in den Feldern der SQL_DATE_STRUCT-Struktur gespeichert sind.  
  
 [d] Die Zahlen in dieser Liste sind die Zahlen, die in den Feldern der SQL_TIMESTAMP_STRUCT-Struktur gespeichert sind.
