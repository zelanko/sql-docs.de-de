---
title: ROUND (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ROUND_TSQL
- ROUND
dev_langs:
- TSQL
helpviewer_keywords:
- rounding expressions
- ROUND function [Transact-SQL]
ms.assetid: 23921ed6-dd6a-4c9e-8c32-91c0d44fe4b7
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9224ae75d28a9373cf3c039d0f0d2642bf4d1b28
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86003702"
---
# <a name="round-transact-sql"></a>ROUND (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Gibt einen numerischen Wert zurück, der auf die angegebene Länge oder Genauigkeit gerundet wurde.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ROUND ( numeric_expression , length [ ,function ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) der genauen numerischen oder ungefähren numerischen Datentypkategorie, mit Ausnahme des **bit**-Datentyps.  
  
 *length*  
 Dies entspricht der Genauigkeit, auf die *numeric_expression* gerundet werden soll. *length* muss ein Ausdruck vom Typ **tinyint**, **smallint** oder **int** sein. Wenn *length* eine positive Zahl ist, wird *numeric_expression* auf die Anzahl der durch *length* angegebenen Dezimalstellen gerundet. Wenn *length* eine negative Zahl ist, wird *numeric_expression* wie durch *length*angegeben auf der linken Seite des Dezimaltrennzeichens gerundet.  
  
 *Funktion*  
 Die Art der auszuführenden Operation. *function* muss vom Typ **tinyint**, **smallint** oder **int** sein. Wenn *function* fehlt oder den Wert 0 (Standard) hat, wird *numeric_expression* gerundet. Wird nicht der Wert 0 angegeben, wird *numeric_expression* abgeschnitten.  
  
## <a name="return-types"></a>Rückgabetypen  
 Gibt die folgenden Datentypen zurück.  
  
|Ausdrucksergebnis|Rückgabetyp|  
|-----------------------|-----------------|  
|**tinyint**|**int**|  
|**smallint**|**int**|  
|**int**|**int**|  
|**bigint**|**bigint**|  
|**decimal**- und **numeric**-Kategorie (p, s)|**decimal(p, s)**|  
|**money**- und **smallmoney**-Kategorie|**money**|  
|**float**- und **real**-Kategorie|**float**|  
  
## <a name="remarks"></a>Bemerkungen  
 ROUND gibt immer einen Wert zurück. Ist *length* negativ und der Wert größer als die Anzahl der Stellen vor dem Dezimaltrennzeichen, gibt ROUND den Wert 0 zurück.  
  
|Beispiel|Ergebnis|  
|-------------|------------|  
|ROUND(748,58, –4)|0|  
  
 Unabhängig vom Datentyp gibt ROUND *numeric_expression* gerundet zurück, wenn *length* eine negative Zahl ist.  
  
|Beispiele|Ergebnis|  
|--------------|------------|  
|ROUND(748,58, –1)|750,00|  
|ROUND(748,58, –2)|700,00|  
|ROUND(748.58, -3)|Verursacht einen arithmetischen Überlauffehler, da 748.58 standardmäßig zu decimal(5,2) wird und eine Rückgabe von 1000.00 nicht möglich ist.|  
|Um bis auf 4 Stellen aufzurunden, ändern Sie den Datentyp für die Eingabe. Beispiel:<br /><br /> `SELECT ROUND(CAST (748.58 AS decimal (6,2)),-3);`|1\.000,00|  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-round-and-estimates"></a>A. Verwenden von ROUND und Schätzwerten  
 Im folgenden Beispiel werden zwei Ausdrücke gezeigt, die veranschaulichen, dass mit `ROUND` die letzte Ziffer immer ein Näherungswert ist.  
  
```  
SELECT ROUND(123.9994, 3), ROUND(123.9995, 3);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------- -----------  
123.9990    124.0000      
```  
  
### <a name="b-using-round-and-rounding-approximations"></a>B. Verwenden von ROUND und gerundeten Näherungswerten  
 Das folgende Beispiel zeigt das Runden und die Näherungsberechnung von Werten.  
  
```  
SELECT ROUND(123.4545, 2), ROUND(123.45, -2);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

 ```
----------  ----------
123.4500    100.00
```
  
### <a name="c-using-round-to-truncate"></a>C. Verwenden von ROUND zum Kürzen  
 Das folgende Beispiel verwendet zwei `SELECT`-Anweisungen, um den Unterschied zwischen dem Runden und dem Kürzen zu verdeutlichen. Die erste Anweisung rundet das Ergebnis. Die zweite Anweisung kürzt das Ergebnis.  
  
```  
SELECT ROUND(150.75, 0);  
GO  
SELECT ROUND(150.75, 0, 1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------  
151.00  
  
(1 row(s) affected)  
  
--------  
150.00  
  
(1 row(s) affected)  
```
  
## <a name="see-also"></a>Weitere Informationen  
 [CEILING &#40;Transact-SQL&#41;](../../t-sql/functions/ceiling-transact-sql.md)   
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [FLOOR &#40;Transact-SQL&#41;](../../t-sql/functions/floor-transact-sql.md)   
 [Mathematische Funktionen &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)
