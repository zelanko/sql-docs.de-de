---
description: LEN (Transact-SQL)
title: LEN (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/03/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- LEN
- LEN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- LEN function
- characters [SQL Server], number of
- number of characters
ms.assetid: fa20fee4-884d-4301-891a-c03e901345ae
author: pmasl
ms.author: pelopes
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e73132566ae66f05da30e250e50f7e8367b9bac1
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97472081"
---
# <a name="len-transact-sql"></a>LEN (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Gibt die Anzahl von Zeichen im angegebenen Zeichenfolgenausdruck zurück, wobei nachstehende Leerzeichen ausgeschlossen werden.  
  
> [!NOTE]  
> Verwenden Sie die [DATALENGTH](../../t-sql/functions/datalength-transact-sql.md)-Funktion, um die Anzahl von Bytes zurückzugeben, die zur Darstellung eines Ausdrucks verwendet werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
LEN ( string_expression )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *string_expression*  
 Ist der auszuwertende [Zeichenfolgenausdruck](../../t-sql/language-elements/expressions-transact-sql.md). *string_expression* kann eine Konstante, Variable oder Spalte mit Zeichen- oder Binärdaten darstellen.  
  
## <a name="return-types"></a>Rückgabetypen  
 **bigint**, wenn *expression* vom Datentyp **varchar(max)** , **nvarchar(max)** oder **varbinary(max)** ist; andernfalls **int**.  
  
 Wenn Sie SC-Sortierungen verwenden, betrachtet der zurückgegebene ganzzahlige Wert UTF-16-Ersatzpaare als einzelne Zeichen. Weitere Informationen finden Sie unter [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="remarks"></a>Bemerkungen  
Durch LEN werden nachstehende Leerzeichen ausgeschlossen. Wenn dies ein Problem darstellt, erwägen Sie die Verwendung der Funktion [DATALENGTH &#40;Transact-SQL&#41;](../../t-sql/functions/datalength-transact-sql.md), die die Zeichenfolge nicht abtrennt. Wenn eine Unicode-Zeichenfolge verarbeitet wird, gibt DATALENGTH eine Zahl zurück, die möglicherweise nicht der Anzahl von Zeichen entspricht. Im folgenden Beispiel werden LEN und DATALENGTH mit nachfolgenden Leerräumen veranschaulicht.  
  
```sql  
  DECLARE @v1 VARCHAR(40),  
    @v2 NVARCHAR(40);  
SELECT   
@v1 = 'Test of 22 characters ',   
@v2 = 'Test of 22 characters ';  
SELECT LEN(@v1) AS [VARCHAR LEN] , DATALENGTH(@v1) AS [VARCHAR DATALENGTH];  
SELECT LEN(@v2) AS [NVARCHAR LEN], DATALENGTH(@v2) AS [NVARCHAR DATALENGTH];  
```  

> [!NOTE]
> Verwenden Sie [LEN](../../t-sql/functions/len-transact-sql.md), um die Anzahl von Zeichen zurückzugeben, die in einem angegebenen Zeichenfolgenausdruck codiert sind. Mit [DATALENGTH](../../t-sql/functions/datalength-transact-sql.md) geben Sie die Größe in Byte für einen angegebenen Zeichenfolgenausdruck zurück. Diese Ausgaben können sich unterscheiden, je nachdem, welcher Datentyp und welche Art von Codierung in der Spalte verwendet werden. Weitere Informationen zu Speicherunterschieden zwischen verschiedenen Codierungstypen finden Sie unter [Sortierung und Unicode-Unterstützung](../../relational-databases/collations/collation-and-unicode-support.md).

## <a name="examples"></a>Beispiele  
 Das folgende Beispiel wählt die Anzahl von Zeichen und die Daten in `FirstName` für Personen in `Australia` aus. In diesem Beispiel wird die AdventureWorks-Datenbank verwendet.  
  
```sql  
SELECT LEN(FirstName) AS Length, FirstName, LastName   
FROM Sales.vIndividualCustomer  
WHERE CountryRegionName = 'Australia';  
GO  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel wird die Anzahl von Zeichen in der Spalte `FirstName` zurückgegeben, und die Vor- und Nachnamen der Mitarbeiter werden in `Australia` zurückgegeben.  
  
```sql  
USE AdventureWorks2016  
GO  
SELECT DISTINCT LEN(FirstName) AS FNameLength, FirstName, LastName   
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.DimGeography AS g   
    ON e.SalesTerritoryKey = g.SalesTerritoryKey   
WHERE EnglishCountryRegionName = 'Australia';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
FNameLength  FirstName  LastName  
-----------  ---------  ---------------  
4            Lynn       Tsoflias
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [DATALENGTH &#40;Transact-SQL&#41;](../../t-sql/functions/datalength-transact-sql.md)   
 [CHARINDEX &#40;Transact-SQL&#41;](../../t-sql/functions/charindex-transact-sql.md)  
 [PATINDEX &#40;Transact-SQL&#41;](../../t-sql/functions/patindex-transact-sql.md)  
 [LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)   
 [RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)  
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/string-functions-transact-sql.md)   
  
  
