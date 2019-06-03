---
title: '&lt; (Kleiner als) (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- < (Less Than)
- <_TSQL
- Than
- Less
- <
- Less Than
dev_langs:
- TSQL
helpviewer_keywords:
- less than (<)
- < (less than operator)
ms.assetid: 54f50bdd-bb62-4593-9af9-4c49edecab75
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bad75430d6458ce9927dd9031c5e98294559d03a
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65983194"
---
# <a name="lt-less-than-transact-sql"></a>&lt; (Kleiner als) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Vergleicht zwei Ausdrücke (ein Vergleichsoperator). Beim Vergleichen von Ausdrücken, die ungleich NULL sind, ist das Ergebnis TRUE, wenn der linke Operand einen niedrigeren Wert als der rechte Operand besitzt; andernfalls ist das Ergebnis FALSE. Wenn einer oder beide Operanden NULL sind, finden Sie weitere Informationen unter [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein beliebiger gültiger [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md). Beide Ausdrücke müssen implizit konvertierbare Datentypen besitzen. Die Konvertierung folgt den [Rangfolge der Datentypen](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 **Boolean**  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using--in-a-simple-query"></a>A. Verwenden von < in einer einfachen Abfrage  
 Im folgenden Beispiel werden alle Zeilen in der `HumanResources.Department` -Tabelle zurückgegeben, die in `DepartmentID` über einen Wert kleiner 3 verfügen.  
  
```  
-- Uses AdventureWorks  
  
SELECT DepartmentID, Name  
FROM HumanResources.Department  
WHERE DepartmentID < 3  
ORDER BY DepartmentID;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DepartmentID Name  
------------ --------------------------------------------------  
1            Engineering  
2            Tool Design  
  
(2 row(s) affected)  
  
```  
  
### <a name="b-using--to-compare-two-variables"></a>B. Verwenden von < zum Vergleich von zwei Variablen  
  
```  
DECLARE @a int = 45, @b int = 40;  
SELECT IIF ( @a < @b, 'TRUE', 'FALSE' ) AS Result;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------  
FALSE  
  
(1 row(s) affected)  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IIF &#40;Transact-SQL&#41;](../../t-sql/functions/logical-functions-iif-transact-sql.md)   
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
