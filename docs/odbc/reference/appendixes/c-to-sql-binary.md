---
title: 'C in SQL: Binäre | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- binary data type [ODBC]
- data conversions from C to SQL types [ODBC], binary
- binary data transfers [ODBC]
- converting data from c to SQL types [ODBC], binary
ms.assetid: 3e9083f3-357b-41aa-833c-2c8aac2226cd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7220497bfac2b74e933595cb7debfd35b98fc07b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68037730"
---
# <a name="c-to-sql-binary"></a>C in SQL: Binär
Der Bezeichner für den binären ODBC C-Datentyp ist:  
  
 SQL_C_BINARY  
  
 Die folgende Tabelle zeigt die ODBC-SQL-Datentypen, die in denen C-Binärdaten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typ-ID|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Die Bytelänge der Daten < = Spalte-Byte-Länge<br /><br /> Die Bytelänge der Daten > Spalte-Byte-Länge|n/v<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Länge der Daten Zeichen < Zeichen Spaltenlänge =<br /><br /> Länge der Daten Zeichen > Zeichen Spaltenlänge|n/v<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER<br /><br /> SQL_BIGINT<br /><br /> SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE<br /><br /> SQL_BIT SQL_TYPE_DATE<br /><br /> SQL_TYPE_TIME<br /><br /> SQL_TYPE_TIMESTAMP|Die Bytelänge der Daten = SQL-Länge<br /><br /> Die Bytelänge der Daten <> SQL-Länge|n/v<br /><br /> 22003|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|Länge von < = Länge der Spalte<br /><br /> Länge der Daten > Spaltenlänge|n/v<br /><br /> 22001|
