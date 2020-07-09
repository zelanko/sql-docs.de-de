---
title: YEAR (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- YEAR
- YEAR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- dates [SQL Server], years
- date and time [SQL Server], YEAR
- functions [SQL Server], date and time
- YEAR function [SQL Server]
- dateparts [SQL Server], year
ms.assetid: 74aa7ccc-8575-4018-80cf-14aeca379687
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b48d0a768bae5a058c2868ae3b30f3f48f06ef40
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "85991437"
---
# <a name="year-transact-sql"></a>YEAR (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt einen Integer zurück, der das Jahr des angegebenen Datums (*date*) darstellt.  
  
 Eine Übersicht über alle Datums- und Uhrzeitdatentypen und zugehörige Funktionen für [!INCLUDE[tsql](../../includes/tsql-md.md)] finden Sie unter [Date and Time Data Types and Functions &#40;Transact-SQL&#41; (Datums- und Uhrzeitdatentypen und zugehörige Funktionen)](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
YEAR ( date )  
```  
  
## <a name="arguments"></a>Argumente  
 *date*  
 Ein Ausdruck, der in einen der folgenden Werte aufgelöst werden kann: **time**, **date**, **smalldatetime**, **datetime**, **datetime2** oder **datetimeoffset**. Bei dem *date*-Argument kann es sich um einen Ausdruck, einen Spaltenausdruck, eine benutzerdefinierte Variable oder ein Zeichenfolgenliteral handeln.  
  
## <a name="return-types"></a>Rückgabetypen  
 **int**  
  
## <a name="return-value"></a>Rückgabewert  
 YEAR gibt den gleichen Wert zurück wie [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**year**, *date*).  
  
 Wenn *date* nur einen Uhrzeitteil enthält, lautet der Rückgabewert 1900. Hierbei handelt es sich um das Basisjahr.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Anweisung gibt `2010` zurück. Dies ist das Jahr.  
  
```  
SELECT YEAR('2010-04-30T01:01:01.1234567-07:00');  
```  
  
 Die folgende Anweisung gibt `1900, 1, 1` zurück. Das Argument für *date* ist die Zahl `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird von `0` als 1. Januar 1900 interpretiert.  
  
```  
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Die folgende Anweisung gibt `1900, 1, 1` zurück. Das Argument für *date* ist die Zahl `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird von `0` als 1. Januar 1900 interpretiert.  
  
```  
SELECT TOP 1 YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  

