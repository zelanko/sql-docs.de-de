---
title: 'SQL in C: Bit | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], bit
- bit data type [ODBC]
- data conversions from SQL to C types [ODBC], bit
ms.assetid: 0eeaab8b-ad82-4a36-b464-9a1211d5f72c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8d00a3c26d842b196e20861da6d8ae3e818d4cbe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056904"
---
# <a name="sql-to-c-bit"></a>SQL in C: bit
Der Bezeichner für den Bit-ODBC-SQL-Datentyp ist:  
  
 SQL_BIT  
  
 Die folgende Tabelle zeigt die ODBC-C-Datentypen, die in den Bit-SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typ-ID|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR<br /><br /> SQL_C_WCHAR|*BufferLength* > 1<br /><br /> *BufferLength* < = 1|Daten<br /><br /> Nicht definiert|1<br /><br /> Nicht definiert|n/v<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE<br /><br /> SQL_C_NUMERIC|Keine [a]|Daten|Anzahl der C-Datentyp|n/v|  
|SQL_C_BIT|Keine [a]|Daten|1[b]|n/v|  
|SQL_C_BINARY|*BufferLength* > = 1<br /><br /> *BufferLength* < 1|Daten<br /><br /> Nicht definiert|1<br /><br /> Nicht definiert|n/v<br /><br /> 22003|  
  
 [a] den Wert der *Pufferlänge* für diese Konvertierung ignoriert wird. Der Treiber setzt voraus, dass die Größe des **TargetValuePtr* ist die Größe der C-Datentyp.  
  
 [b] Dies ist die Größe des entsprechenden C-Datentyp.  
  
 Wenn in Zeichendaten C Bit-SQL-Daten konvertiert werden, sind die möglichen Werte "0" und "1".
