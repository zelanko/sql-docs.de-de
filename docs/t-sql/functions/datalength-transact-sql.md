---
description: DATALENGTH (Transact-SQL)
title: DATALENGTH (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/20/2019
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
author: pmasl
ms.author: pelopes
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 438f44cb3c77abc704509dc5801b43cd6fa0a815
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97468231"
---
# <a name="datalength-transact-sql"></a>DATALENGTH (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Diese Funktion gibt die Anzahl von Bytes zurück, die zum Darstellen eines Ausdrucks verwendet werden.

> [!NOTE]
> Um die Anzahl von Zeichen in einem Zeichenfolgenausdruck zurückzugeben, verwenden Sie die [LEN](../../t-sql/functions/len-transact-sql.md)-Funktion.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
DATALENGTH ( expression )   
```  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
*expression*  
Ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) mit beliebigem Datentyp.
  
## <a name="return-types"></a>Rückgabetypen
**bigint**, wenn *expression* den Datentyp **nvarchar(max)**, **varbinary(max)** oder **varchar(max)** hat; andernfalls **int**.
  
## <a name="remarks"></a>Hinweise  
`DATALENGTH` ist besonders beim Einsatz mit Datentypen nützlich, die Daten variabler Länge speichern können, z. B.:
- **image**
- **ntext**
- **nvarchar**
- **text**
- **varbinary**
- **varchar**
  
Für einen NULL-Wert gibt `DATALENGTH` NULL zurück.
  
> [!NOTE]  
> Kompatibilitätsgrade können sich auf Rückgabewerte auswirken. Weitere Informationen zu den Kompatibilitätsgraden finden Sie unter [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  

> [!NOTE]
> Verwenden Sie [LEN](../../t-sql/functions/len-transact-sql.md), um die Anzahl von Zeichen zurückzugeben, die in einem angegebenen Zeichenfolgenausdruck codiert sind. Mit [DATALENGTH](../../t-sql/functions/datalength-transact-sql.md) geben Sie die Größe in Byte für einen angegebenen Zeichenfolgenausdruck zurück. Diese Ausgaben können sich unterscheiden, je nachdem, welcher Datentyp und welche Art von Codierung in der Spalte verwendet werden. Weitere Informationen zu Speicherunterschieden zwischen verschiedenen Codierungstypen finden Sie unter [Sortierung und Unicode-Unterstützung](../../relational-databases/collations/collation-and-unicode-support.md).

## <a name="examples"></a>Beispiele  
In diesem Beispiel wird nach der Länge der `Name`-Spalte in der `Product`-Tabelle gesucht:
  
```sql
USE AdventureWorks2016  
GO
SELECT length = DATALENGTH(EnglishProductName), EnglishProductName  
FROM dbo.DimProduct  
ORDER BY EnglishProductName;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen
[LEN &#40;Transact-SQL&#41;](../../t-sql/functions/len-transact-sql.md)  
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)
