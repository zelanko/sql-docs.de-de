---
title: SQLGetTypeInfo (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5f25e20b-a4ef-42da-aeb6-00e0510fb1cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05cc6dc2647b5297b8d7176cd4bc70261b78cb71
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733058"
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: vollständige  
  
 ODBC-API-Übereinstimmung: Ebene 1  
  
 Gibt Informationen zu den Datentypen unterstützt, die von einer Datenquelle zurück. Der Treiber zurückgegeben die Informationen in einer SQL-Resultset. Die folgende Tabelle enthält die ODBC-Datentypen und den entsprechenden Visual FoxPro-Datentyp.  
  
|ODBC-Typ|Visual FoxPro-Typ|  
|---------------|------------------------|  
|SQL_BIGINT|Wird nicht unterstützt. Es gibt keine 64-Bit-Visual FoxPro-Typ.|  
|SQL_BIT|Logische Operatoren|  
|SQL_CHAR|Zeichen|  
|SQL_DATE|date|  
|SQL_DECIMAL|Numerisch|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Integer|  
|SQL_LONGVARBINARY|Memo (binär)|  
|SQL_LONGVARCHAR|Memo|  
|SQL_NUMERIC|Numerische *, Währung, "float"|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Integer|  
|SQL_TIME|Wird nicht unterstützt. Es ist kein Visual FoxPro *Zeit* Typ.|  
|SQL_TIMESTAMP|datetime|  
|SQL_TINYINT|Integer|  
|SQL_VARBINARY|Memo (binär) *, Allgemein|  
|SQL_VARCHAR|Zeichen|  
  
 * Standard-Typ  
  
 Weitere Informationen zu Visual FoxPro-Datentypen, finden Sie unter [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md). Weitere Informationen zu dieser Funktion finden Sie unter [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md) in die *ODBC Programmer's Reference*.
