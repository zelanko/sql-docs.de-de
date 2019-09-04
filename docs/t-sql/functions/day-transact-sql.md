---
title: DAY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DAY_TSQL
- DAY
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], DAY
- dates [SQL Server], functions
- DAY function [SQL Server]
- dates [SQL Server], days
- functions [SQL Server], date and time
- dateparts [SQL Server], day
ms.assetid: 2f4410ea-fd3e-4d69-ac4b-3b0091a084bc
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0f1d58e89e6fd7cdc4d8af85d3d8745e1bc15fa7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119060"
---
# <a name="day-transact-sql"></a>DAY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Diese Funktion gibt eine ganze Zahl zurück, die den Tag (Tag des Monats) des angegebenen *Datums* darstellt.
  
Unter [Datums- und Uhrzeitdatentypen und zugehörige Funktionen &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md) finden Sie eine Übersicht über alle [!INCLUDE[tsql](../../includes/tsql-md.md)] Datums- und Uhrzeitdatentypen und zugehörige Funktionen.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
DAY ( date )  
```  
  
## <a name="arguments"></a>Argumente  
*date*  
Ein Ausdruck, der in einen der folgenden Datentypen aufgelöst werden kann:

+ **date**
+ **datetime**
+ **datetimeoffset**
+ **datetime2** 
+ **smalldatetime**
+ **time**

Bei *date* akzeptiert `DAY` einen Spaltenausdruck, einen Ausdruck, ein Zeichenfolgenliteral oder eine benutzerdefinierte Variable.
  
## <a name="return-type"></a>Rückgabetyp  
**int**
  
## <a name="return-value"></a>Rückgabewert  
DAY gibt den gleichen Wert zurück wie [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**day**, *date*).
  
Wenn *date* nur einen Uhrzeitabschnitt enthält, gibt `DAY` 1 zurück. Hierbei handelt es sich um dem Basistag.
  
## <a name="examples"></a>Beispiele  
Diese Anweisung gibt `30` zurück, was der Zahl des Tags selbst entspricht.
  
```sql
SELECT DAY('2015-04-30 01:01:01.1234567');  
```  
  
Diese Anweisung gibt `1900, 1, 1` zurück. Das Argument *date* verfügt über einen Zahlenwert von `0`. `0` wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als 1. Januar 1900 interpretiert.
  
```sql
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="see-also"></a>Siehe auch
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


