---
title: POWER (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- POWER_TSQL
- POWER
dev_langs:
- TSQL
helpviewer_keywords:
- POWER function
ms.assetid: 0fd34494-90b9-4559-8011-a8c1b9f40239
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0003102d607cac065a1168e0c5544a8db2163249
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65943323"
---
# <a name="power-transact-sql"></a>POWER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt den Wert des angegebenen Ausdrucks in der angegebenen Potenz zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
POWER ( float_expression , y )  
```  
  
## <a name="arguments"></a>Argumente  
 *float_expression*  
 Ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) vom Typ **float** oder von einem Typ, der implizit in **float** konvertiert werden kann.  
  
 *y*  
 Die Potenz, in die *float_expression* erhoben werden soll. *y* kann ein Ausdruck der genauen numerischen oder ungefähren numerischen Datentypkategorie sein, mit Ausnahme des **bit**-Datentyps.  
  
## <a name="return-types"></a>Rückgabetypen  
 Der Rückgabetyp hängt vom Eingabetyp von *float_expression* ab:
 
|Eingabetyp|Rückgabetyp|  
|----------|-----------|  
|**float**, **real**|**float**|
|**decimal(*p*, *s*)**|**decimal(38, *s*)**|
|**int**, **smallint**, **tinyint**|**ssNoversion**|
|**bigint**|**bigint**|
|**money**, **smallmoney**|**money**|
|**bit**, **char**, **nchar**, **varchar**, **nvarchar**|**float**|
 
Wenn das Ergebnis nicht zum Rückgabetyp passt, wird ein Fehler durch einen arithmetischen Überlauf ausgelöst.
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-power-to-return-the-cube-of-a-number"></a>A. Rückgabe der Kubikwurzel einer Zahl mit POWER  
 Im folgenden Beispiel wird das Potenzieren einer Zahl mit 3 (der Kubikwurzel der Zahl) veranschaulicht.  
  
```  
DECLARE @input1 float;  
DECLARE @input2 float;  
SET @input1= 2;  
SET @input2 = 2.5;  
SELECT POWER(@input1, 3) AS Result1, POWER(@input2, 3) AS Result2;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result1                Result2  
---------------------- ----------------------  
8                      15.625  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-power-to-show-results-of-data-type-conversion"></a>B. Anzeigen der Ergebnisse einer Datentypkonvertierung mit POWER  
 Im folgenden Beispiel wird veranschaulicht, wie der Datentyp von *float_expression* beibehalten wird, was zu unerwarteten Ergebnissen führen kann.  
  
```  
SELECT   
POWER(CAST(2.0 AS float), -100.0) AS FloatResult,  
POWER(2, -100.0) AS IntegerResult,  
POWER(CAST(2.0 AS int), -100.0) AS IntegerResult,  
POWER(2.0, -100.0) AS Decimal1Result,  
POWER(2.00, -100.0) AS Decimal2Result,  
POWER(CAST(2.0 AS decimal(5,2)), -100.0) AS Decimal2Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
FloatResult            IntegerResult IntegerResult Decimal1Result Decimal2Result Decimal2Result  
---------------------- ------------- ------------- -------------- -------------- --------------  
7.88860905221012E-31   0             0             0.0            0.00           0.00  
```  
  
### <a name="c-using-power"></a>C. Verwenden von POWER  
 Das folgende Beispiel gibt `POWER`-Ergebnisse für `2` zurück.  
  
```  
DECLARE @value int, @counter int;  
SET @value = 2;  
SET @counter = 1;  
  
WHILE @counter < 5  
   BEGIN  
      SELECT POWER(@value, @counter)  
      SET NOCOUNT ON  
      SET @counter = @counter + 1  
      SET NOCOUNT OFF  
   END;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------   
2             
  
(1 row(s) affected)  
  
-----------   
4             
  
(1 row(s) affected)  
  
-----------   
8             
  
(1 row(s) affected)  
  
-----------   
16            
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
### <a name="d-using-power-to-return-the-cube-of-a-number"></a>D: Rückgabe der Kubikwurzel einer Zahl mit POWER  
 Im folgenden Beispiel wird die Rückgabe von `POWER`-Ergebnissen für `2.0` an die dritte Potenz dargestellt.  
  
```  
SELECT POWER(2.0, 3);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
------------ 
8.0
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [decimal und numeric &#40;Transact-SQL&#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)   
 [float und real &#40;Transact-SQL&#41;](../../t-sql/data-types/float-and-real-transact-sql.md)   
 [int, bigint, smallint und tinyint &#40;Transact-SQL&#41;](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)   
 [Mathematische Funktionen &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [money und smallmoney &#40;Transact-SQL&#41;](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)  
  
  

