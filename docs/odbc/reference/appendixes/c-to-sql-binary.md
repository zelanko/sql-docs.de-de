---
title: 'C zu SQL: binär | | Microsoft-Dokumentation'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 818de0086ce3996cc1f6194311d2a2bb80c9f564
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292116"
---
# <a name="c-to-sql-binary"></a>C zu SQL: Binärdaten
Der Bezeichner für den binären ODBC-C-Datentyp lautet:  
  
 SQL_C_BINARY  
  
 In der folgenden Tabelle werden die ODBC-SQL-Datentypen angezeigt, in die binäre C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Byte Länge der Daten <= Spalten Byte Länge<br /><br /> Byte Länge der Daten > Spalte Byte Länge|Nicht zutreffend<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Zeichen Länge der Daten <= Spalten Zeichenlänge<br /><br /> Zeichen Länge der Daten > Spalten Zeichenlänge|Nicht zutreffend<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER<br /><br /> SQL_BIGINT<br /><br /> SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE<br /><br /> SQL_BIT SQL_TYPE_DATE<br /><br /> SQL_TYPE_TIME<br /><br /> SQL_TYPE_TIMESTAMP|Byte Länge der Daten = SQL-Daten Länge<br /><br /> Byte Länge der Daten <> SQL-Daten Länge|Nicht zutreffend<br /><br /> 22003|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|Länge der Daten <= Spaltenlänge<br /><br /> Länge der Daten > Spaltenlänge|Nicht zutreffend<br /><br /> 22001|
