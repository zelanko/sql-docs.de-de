---
description: POWER (Transact-SQL)
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
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 857ad909b2f471edaebf661ccab4cca0077bc099
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88417316"
---
# <a name="power-transact-sql"></a>POWER (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt den Wert des angegebenen Ausdrucks gemäß der angegebenen Potenz zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
POWER ( float_expression , y )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

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
|**int**, **smallint**, **tinyint**|**int**|
|**bigint**|**bigint**|
|**money**, **smallmoney**|**money**|
|**bit**, **char**, **nchar**, **varchar**, **nvarchar**|**float**|
 
Wenn das Ergebnis nicht zum Rückgabetyp passt, wird ein Fehler durch einen arithmetischen Überlauf ausgelöst.
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-power-to-return-the-cube-of-a-number"></a>A. Rückgabe der Kubikwurzel einer Zahl mit POWER  
 Im folgenden Beispiel wird das Potenzieren einer Zahl mit 3 (der Kubikwurzel der Zahl) veranschaulicht.  
  
```  
DECLARE @input1 FLOAT;  
DECLARE @input2 FLOAT;  
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
POWER(CAST(2.0 AS FLOAT), -100.0) AS FloatResult,  
POWER(2, -100.0) AS IntegerResult,  
POWER(CAST(2.0 AS INT), -100.0) AS IntegerResult,  
POWER(2.0, -100.0) AS Decimal1Result,  
POWER(2.00, -100.0) AS Decimal2Result,  
POWER(CAST(2.0 AS DECIMAL(5,2)), -100.0) AS Decimal2Result;  
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
DECLARE @value INT, @counter INT;  
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
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-power-to-return-the-cube-of-a-number"></a>D: Rückgabe des Cubes einer Zahl mit POWER  
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
  
  

