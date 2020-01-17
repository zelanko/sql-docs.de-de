---
title: +=-Zeichenfolgenverkettung
description: Verkettet zwei Zeichenfolgen und legt die Zeichenfolge auf das Ergebnis des Vorgangs fest
titleSuffix: SQL Server (Transact-SQL)
ms.custom: seo-lt-2019
ms.date: 12/07/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- concatenate strings
- string concatenation
- += (concatenate operator)
ms.assetid: 4aaeaab7-9b2b-48e0-8487-04ed672ebcb1
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dd21fb221076470d0c39194ea4c38d96af0f1056
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75257051"
---
# <a name="-string-concatenation-assignment-transact-sql"></a>+= (Zeichenfolgenverkettungszuweisung) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Verkettet zwei Zeichenfolgen und legt die Zeichenfolge auf das Ergebnis des Vorgangs fest. Wenn beispielsweise eine Variable @x gleich 'Adventure' ist, dann übernimmt @x += 'Works' den ursprünglichen Wert von @x, fügt 'Works' der Zeichenfolge hinzu und legt @x auf den neuen Wert 'AdventureWorks' fest.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
expression += expression  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein gültiger [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) eines beliebigen Zeichendatentyps.  
  
## <a name="result-types"></a>Ergebnistypen  
 Gibt den Datentyp zurück, der für die Variable definiert wird.  
  
## <a name="remarks"></a>Bemerkungen  
 SET @v1 += 'Ausdruck' entspricht SET @v1 = @v1 + ('Ausdruck'). SET @v1 = @v2 + @v3 + @v4 entspricht auch SET @v1 = (@v2 + @v3) + @v4.  
  
 Der Operator += kann nicht ohne eine Variable verwendet werden. So verursacht z. B. der folgende Code einen Fehler:  
  
```  
SELECT 'Adventure' += 'Works'  
```  
  
## <a name="examples"></a>Beispiele  
### <a name="a-concatenation-using--operator"></a>A. Verkettung mit +=-Operator
 Im folgenden Beispiel wird mithilfe des `+=`-Operators verkettet.  
  
```  
DECLARE @v1 varchar(40);  
SET @v1 = 'This is the original.';  
SET @v1 += ' More text.';  
PRINT @v1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `This is the original. More text.`  
  
### <a name="b-order-of-evaluation-while-concatenating-using--operator"></a>B. Reihenfolge der Auswertung beim Verketten mit dem +=-Operator
Im folgenden Beispiel werden mehrere Zeichenfolgen zu einer langen Zeichenfolge verkettet. Anschließend wird versucht, die Länge der endgültigen Zeichenfolge zu berechnen. Dieses Beispiel zeigt die Auswertungsreihenfolge und Kürzungsregeln bei Verwendung des concatenation-Operators. 

```
DECLARE @x varchar(4000) = replicate('x', 4000)
DECLARE @z varchar(8000) = replicate('z',8000)
DECLARE @y varchar(max);
 
SET @y = '';
SET @y += @x + @z;
SELECT LEN(@y) AS Y; -- 8000
 
SET @y = '';
SET @y = @y + @x + @z;
SELECT LEN(@y) AS Y; -- 12000
 
SET @y = '';
SET @y = @y +(@x + @z);
SELECT LEN(@y) AS Y; -- 8000
-- or
SET @y = '';
SET @y = @x + @z + @y;
SELECT LEN(@y) AS Y; -- 8000
GO
```
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Y       
 ------- 
 8000 
  
 (1 row(s) affected) 
  
    
 Y       
 ------- 
 12000 
  
 (1 row(s) affected) 

 Y       
 ------- 
 8000 
  
 (1 row(s) affected) 
  
 Y       
 ------- 
 8000 
  
 (1 row(s) affected)
  ```   
   
## <a name="see-also"></a>Weitere Informationen  
 [Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [+= &#40;Additionszuweisung&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/add-equals-transact-sql.md)   
 [+ &#40;Verketten von Zeichenfolgen&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
  
  
