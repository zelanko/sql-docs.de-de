---
title: MONTH (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- MONTH_TSQL
- MONTH
dev_langs:
- TSQL
helpviewer_keywords:
- values [SQL Server], date and time
- dates [SQL Server], functions
- month of year [SQL Server]
- date and time [SQL Server], MONTH
- dateparts [SQL Server], month
- functions [SQL Server], date and time
- dates [SQL Server], MONTH
- MONTH function [SQL Server]
ms.assetid: 9dd8aff7-b0fc-45df-b316-ead14ee9b8b7
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d9fc2c8718fd643e5838172831858c51aea6fd47
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68130226"
---
# <a name="month-transact-sql"></a>MONTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt einen Integer zurück, der den Monat des angegebenen *Datums* darstellt.  
  
 Eine Übersicht über alle Datums- und Uhrzeitdatentypen und zugehörige Funktionen für [!INCLUDE[tsql](../../includes/tsql-md.md)] finden Sie unter [Date and Time Data Types and Functions &#40;Transact-SQL&#41; (Datums- und Uhrzeitdatentypen und zugehörige Funktionen (Transact-SQL))](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
MONTH ( date )  
```  
  
## <a name="arguments"></a>Argumente  
 *date*  
 Ein Ausdruck, der in einen der folgenden Werte aufgelöst werden kann: **time**, **date**, **smalldatetime**, **datetime**, **datetime2** oder **datetimeoffset**. Bei dem *date*-Argument kann es sich um einen Ausdruck, einen Spaltenausdruck, eine benutzerdefinierte Variable oder ein Zeichenfolgenliteral handeln.  
  
## <a name="return-type"></a>Rückgabetyp  
 **int**  
  
## <a name="return-value"></a>Rückgabewert  
 MONTH gibt den gleichen Wert wie [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**month**, *date*) zurück.  
  
 Wenn *date* nur einen Uhrzeitteil enthält, lautet der Rückgabewert 1. Hierbei handelt es sich um den Basismonat.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Anweisung gibt `4` zurück. Dies ist die Monatszahl.  
  
```  
SELECT MONTH('2007-04-30T01:01:01.1234567 -07:00');  
```  
  
 Die folgende Anweisung gibt `1900, 1, 1` zurück. Das Argument für *date* ist die Zahl `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird von `0` als 1. Januar 1900 interpretiert.  
  
```  
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel wird `4` zurückgegeben. Dies ist die Monatszahl.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP 1 MONTH('2007-04-30T01:01:01.1234')   
FROM dbo.DimCustomer;  
```  
  
 Im folgenden Beispiel wird `1900, 1, 1` zurückgegeben. Das Argument für *date* ist die Zahl `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird von `0` als 1. Januar 1900 interpretiert.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP 1 YEAR(0), MONTH(0), DAY(0) FROM dbo.DimCustomer;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  

