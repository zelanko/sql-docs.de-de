---
title: ASCII (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/14/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ASCII_TSQL
- ASCII
dev_langs:
- TSQL
helpviewer_keywords:
- ASCII function
- characters [SQL Server], ASCII
- code [SQL Server], ASCII
- leftmost character of expression
ms.assetid: 45c2044a-0593-4805-8bae-0fad4bde2e6b
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9b982d357668703a54b06124a8bb3edf0c963463
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "74119189"
---
# <a name="ascii-transact-sql"></a>ASCII (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Gibt den ASCII-Codewert des ersten Zeichens eines Zeichenausdrucks zurück.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
ASCII ( character_expression )  
```  
  
## <a name="arguments"></a>Argumente  
*character_expression*  
Ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) des Typs **char** oder **varchar**.
  
## <a name="return-types"></a>Rückgabetypen
 **int**  
  
## <a name="remarks"></a>Bemerkungen
Die Abkürzung ASCII steht für **A**merican **S**tandard **C**ode for **I**nformation **I**nterchange. Es dient als ein Zeichencodierungsstandard für moderne Computer. Eine Liste mit ASCII-Zeichen finden Sie im Abschnitt **Printable characters (Darstellbare Zeichen)** des Artikels [ASCII](https://www.wikipedia.org/wiki/ASCII).

ASCII ist ein 7-Bit-Zeichensatz. Erweiterte oder hohe ASCII sind ein 8-Bit-Zeichensatz, der nicht von der `ASCII`-Funktion behandelt wird. 

## <a name="examples"></a>Beispiele 

### <a name="a-this-example-assumes-an-ascii-character-set-and-returns-the-ascii-value-for-6-characters"></a>A. In diesem Beispiel, in dem von einem ASCII-Zeichensatz ausgegangen wird, wird der Wert `ASCII` für sechs Zeichen zurückgegeben.
  
```sql
SELECT ASCII('A') AS A, ASCII('B') AS B,   
ASCII('a') AS a, ASCII('b') AS b,  
ASCII(1) AS [1], ASCII(2) AS [2];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
A           B           a           b           1           2  
----------- ----------- ----------- ----------- ----------- -----------  
65          66          97          98          49          50  
```  
  
### <a name="b-this-examples-shows-how-a-7-bit-ascii-value-is-returned-correctly-but-an-8-bit-extended-ascii-value-is-not-handled"></a>B. In diesen Beispielen wird gezeigt, wie ein 7-Bit-ASCII-Wert ordnungsgemäß zurückgegeben wird, ein erweiterter 8-Bit-ASCII-Wert jedoch nicht behandelt wird.

```sql
SELECT ASCII('P') AS [ASCII], ASCII('æ') AS [Extended_ASCII];
```

[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```
ASCII       Extended_ASCII
----------- --------------
80          195
```

Verwenden Sie die Ausgabewerte mit der `CHAR`- oder `NCHAR`-Funktion, um zu überprüfen, ob die oben angegebenen Ergebnisse dem richtigen Zeichencodepunkt zugeordnet sind:

```sql
SELECT NCHAR(80) AS [CHARACTER], NCHAR(195) AS [CHARACTER];
```

[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```
CHARACTER CHARACTER
--------- ---------
P         Ã
```

Beachten Sie aus dem vorherigen Ergebnis, dass das Zeichen für den Codepunkt 195 **Ã** und nicht **æ** ist. Das liegt daran, dass die `ASCII`-Funktion zwar den ersten 7-Bit-Stream, aber nicht den zusätzlichen Bit lesen kann. Der korrekte Codepunkt für das Zeichen `æ` kann mit der `UNICODE`-Funktion gefunden werden, die in der Lage ist, den richtigen Zeichencodepunkt zurückzugeben:

```sql
SELECT UNICODE('æ') AS [Extended_ASCII], NCHAR(230) AS [CHARACTER];
```

[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```
Extended_ASCII CHARACTER
-------------- ---------
230            æ
```

## <a name="see-also"></a>Weitere Informationen
 [CHAR &#40;Transact-SQL&#41;](../../t-sql/functions/char-transact-sql.md)  
 [NCHAR &#40;Transact-SQL&#41;](../../t-sql/functions/nchar-transact-sql.md)  
 [UNICODE &#40;Transact-SQL&#41;](../../t-sql/functions/unicode-transact-sql.md)  
 [String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/string-functions-transact-sql.md)
  
