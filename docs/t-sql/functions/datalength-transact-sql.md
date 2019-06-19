---
title: DATALENGTH (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DATALENGTH_TSQL
- DATALENGTH
dev_langs:
- TSQL
helpviewer_keywords:
- number of bytes representing expression
- data types [SQL Server], length
- DATALENGTH function
- expressions [SQL Server], length
- lengths [SQL Server], data
ms.assetid: 00f377f1-cc3e-4eac-be47-b3e3f80267c9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d5f1b4816be53f05dd964f8be0ee9ce52fd11cbb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65943783"
---
# <a name="datalength-transact-sql"></a>DATALENGTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Diese Funktion gibt die Anzahl von Bytes zurück, die zum Darstellen eines Ausdrucks verwendet werden.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
DATALENGTH ( expression )   
```  
  
## <a name="arguments"></a>Argumente  
*expression*  
Ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) mit beliebigem Datentyp.
  
## <a name="return-types"></a>Rückgabetypen
**bigint**, wenn *expression* den Datentyp **nvarchar(max)** , **varbinary(max)** oder **varchar(max)** hat; andernfalls **int**.
  
## <a name="remarks"></a>Remarks  
`DATALENGTH` ist insbesondere nützlich bei Verwendung mit den Datentypen

- **image**
- **ntext**
- **nvarchar**
- **text**
- **varbinary**
- **varchar**

Dies liegt daran, dass mit diesen Datentypen Daten variabler Länge gespeichert werden können.
  
Für einen NULL-Wert gibt `DATALENGTH` NULL zurück.
  
> [!NOTE]  
>  Kompatibilitätsgrade können sich auf Rückgabewerte auswirken. Weitere Informationen zu den Kompatibilitätsgraden finden Sie unter [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="examples"></a>Beispiele  
In diesem Beispiel wird nach der Länge der `Name`-Spalte in der `Product`-Tabelle gesucht:
  
```sql
-- Uses AdventureWorks  
  
SELECT length = DATALENGTH(EnglishProductName), EnglishProductName  
FROM dbo.DimProduct  
ORDER BY EnglishProductName;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch
[LEN &#40;Transact-SQL&#41;](../../t-sql/functions/len-transact-sql.md)  
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)
  
  

