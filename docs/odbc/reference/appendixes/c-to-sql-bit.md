---
title: 'C in SQL: Bit | Microsoft-Dokumentation'
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
ms.openlocfilehash: 8cc5e26b30816d0989dca90566a1a5de008b71c7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019419"
---
# <a name="c-to-sql-bit"></a>C in SQL: bit
Der Bezeichner für den Bit-ODBC-C-Datentyp ist:  
  
 SQL_C_BIT  
  
 Die folgende Tabelle zeigt die ODBC-SQL-Datentypen, die in den Bit-C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typ-ID|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR, SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR<br /><br /> SQL_WCHAR SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|None|n/v|  
|SQL_DECIMAL SQL_NUMERIC<br /><br /> SQL_TINYINT SQL_SMALLINT<br /><br /> SQL_INTEGER SQL_BIGINT<br /><br /> SQL_REAL SQL_FLOAT<br /><br /> SQL_DOUBLE|None|n/v|  
|SQL_BIT|None|n/v|  
  
 Der Treiber ignoriert die Längenindikator /-Wert, bei der Konvertierung von Daten von der C-Bit-Datentyp, und es wird davon ausgegangen, dass die Größe des Datenpuffers die Größe des C-Bit-Datentyps. Der Längenindikator /-Wert übergeben wird die *StrLen_or_Ind* -Argument in **SQLPutData** und in den Puffer, der mit angegebenen die *StrLen_or_IndPtr* -Argument in **SQLBindParameter**. Der Datenpuffer wird angegeben, mit der *DataPtr* -Argument in **SQLPutData** und die *ParameterValuePtr* -Argument in **SQLBindParameter**.
