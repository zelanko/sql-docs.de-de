---
title: 'C to SQL: Bit | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], bit
- bit data type [ODBC]
- data conversions from C to SQL types [ODBC], bit
ms.assetid: 267c9fa9-599e-4ee6-b51b-0cae43f09183
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9eeeaeaa3bb4af7a244697e992e79e8c66c2a660
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47709708"
---
# <a name="c-to-sql-bit"></a>C zu SQL: Bit
Der Bezeichner für den Bit-ODBC-C-Datentyp ist:  
  
 SQL_C_BIT  
  
 Die folgende Tabelle zeigt die ODBC-SQL-Datentypen, die in den Bit-C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typ-ID|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR, SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR<br /><br /> SQL_WCHAR, SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|None|–|  
|SQL_DECIMAL SQL_NUMERIC<br /><br /> SQL_TINYINT SQL_SMALLINT<br /><br /> SQL_INTEGER SQL_BIGINT<br /><br /> SQL_REAL SQL_FLOAT<br /><br /> SQL_DOUBLE|None|–|  
|SQL_BIT|None|–|  
  
 Der Treiber ignoriert die Längenindikator /-Wert, bei der Konvertierung von Daten von der C-Bit-Datentyp, und es wird davon ausgegangen, dass die Größe des Datenpuffers die Größe des C-Bit-Datentyps. Der Längenindikator /-Wert übergeben wird die *StrLen_or_Ind* -Argument in **SQLPutData** und in den Puffer, der mit angegebenen die *StrLen_or_IndPtr* -Argument in **SQLBindParameter**. Der Datenpuffer wird angegeben, mit der *DataPtr* -Argument in **SQLPutData** und die *ParameterValuePtr* -Argument in **SQLBindParameter**.
