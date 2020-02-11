---
title: 'SQL zu C: Bit | Microsoft-Dokumentation'
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68056904"
---
# <a name="sql-to-c-bit"></a>SQL zu C: Bit
Der Bezeichner für den bitodbc-SQL-Datentyp lautet:  
  
 SQL_BIT  
  
 In der folgenden Tabelle werden die ODBC-C-Datentypen angezeigt, in die bitsql-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typbezeichner|Test|**Targetvalueptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR<br /><br /> SQL_C_WCHAR|*BufferLength* > 1<br /><br /> *BufferLength* <= 1|Data<br /><br /> Undefined|1<br /><br /> Undefined|–<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE<br /><br /> SQL_C_NUMERIC|Keine [a]|Data|Größe des C-Datentyps|–|  
|SQL_C_BIT|Keine [a]|Data|1 [b]|–|  
|SQL_C_BINARY|*BufferLength* >= 1<br /><br /> *BufferLength* < 1|Data<br /><br /> Undefined|1<br /><br /> Undefined|–<br /><br /> 22003|  
  
 [a] der Wert von *BufferLength* wird für diese Konvertierung ignoriert. Der Treiber geht davon aus, dass die Größe von **targetvalueptr* die Größe des C-Datentyps ist.  
  
 [b] Dies ist die Größe des entsprechenden C-Datentyps.  
  
 Wenn bitsql-Daten in Zeichen-C-Daten konvertiert werden, sind die möglichen Werte "0" und "1".
