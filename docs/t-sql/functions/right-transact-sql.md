---
title: RIGHT (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- RIGHT_TSQL
- RIGHT
dev_langs:
- TSQL
helpviewer_keywords:
- rightmost character of expression
- RIGHT function
- character strings [SQL Server], RIGHT
ms.assetid: 43f1fe1f-aa18-47e3-ba20-e03e32254a6d
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ef9dfcd1c958088e49221efc23e7101fac9fec0a
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87110329"
---
# <a name="right-transact-sql"></a>RIGHT (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt den rechten Teil einer Zeichenfolge mit der angegebenen Anzahl von Zeichen zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
RIGHT ( character_expression , integer_expression )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *character_expression*  
 Ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) aus Zeichen- oder Binärdaten. *character_expression* kann eine Konstante, Variable oder Spalte sein. *character_expression* kann von einem beliebigen Datentyp sein, ausschließlich **text** oder **ntext**, der implizit in **varchar** oder **nvarchar** konvertiert werden kann. Verwenden Sie in allen anderen Fällen die [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md)-Funktion zur expliziten Konvertierung von *character_expression*.  
   
> [!NOTE]  
> Wenn *string_expression* den Typ **binary** oder **varbinary** aufweist, führt RIGHT eine implizite Konvertierung in **varchar** aus und behält daher die binäre Eingabe nicht bei.  
  
 *integer_expression*  
 Ein positiver Integer, der angibt, wie viele Zeichen von *character_expression* zurückgegeben werden. Wenn *integer_expression* negativ ist, wird ein Fehler zurückgegeben. Wenn *integer_expression* vom Typ **bigint** ist und einen hohen Wert hat, muss *character_expression* von einem umfangreicheren Datentyp wie z.B. **varchar(max)** sein.  
  
## <a name="return-types"></a>Rückgabetypen  
 Gibt **varchar** zurück, wenn es sich bei *character_expression* um einen Zeichendatentyp handelt, der Unicode nicht unterstützt.  
  
 Gibt **nvarchar** zurück, wenn es sich bei *character_expression* um einen Zeichendatentyp handelt, der Unicode nicht unterstützt.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Ergänzende Zeichen (Ersatzpaare)  
 Bei Verwendung von SC-Sortierungen zählt die RIGHT-Funktion ein UTF-16-Ersatzpaar als einzelnes Zeichen. Weitere Informationen finden Sie unter [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-right-with-a-column"></a>A: Verwenden von RIGHT mit einer Spalte  
 Im folgenden Beispiel werden die fünf am weitesten rechts stehenden Zeichen des Vornamens jeder Person in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank zurückgegeben.  
  
```  
SELECT RIGHT(FirstName, 5) AS 'First Name'  
FROM Person.Person  
WHERE BusinessEntityID < 5  
ORDER BY FirstName;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
First Name  
----------  
Ken  
Terri  
berto  
Rob  
  
(4 row(s) affected)  
  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-using-right-with-a-column"></a>B. Verwenden von RIGHT mit einer Spalte  
 Im folgenden Beispiel werden die fünf am weitesten rechts stehenden Zeichen jedes Nachnamens in der `DimEmployee`-Tabelle zurückgegeben.  
  
```  
-- Uses AdventureWorks  
  
SELECT RIGHT(LastName, 5) AS Name  
FROM dbo.DimEmployee  
ORDER BY EmployeeKey;  
```  
  
 Dies ist ein Auszug aus dem Resultset.  
  
 ```
Name
-----
lbert
Brown
rello
lters
 ```  
  
### <a name="c-using-right-with-a-character-string"></a>C. Verwenden von RIGHT mit einer Zeichenfolge  
 Im folgenden Beispiel wird `RIGHT` zur Rückgabe der beiden am weitesten rechts stehenden Zeichen der Zeichenfolge `abcdefg` verwendet.  
  
```  
SELECT RIGHT('abcdefg', 2); 
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
-------  
fg
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)  
 [LTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/ltrim-transact-sql.md)  
 [RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40;Transact-SQL&#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)  
 [TRIM &#40;Transact-SQL&#41;](../../t-sql/functions/trim-transact-sql.md)  
 [CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

