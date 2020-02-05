---
title: Verbundoperatoren (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators
- compound operators, described
ms.assetid: 5072fe91-02d3-42a7-831f-756eff714a17
author: rothja
ms.author: jroth
ms.openlocfilehash: e81ef89165b3af5af0f8c48ca0338086c5c934a9
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "67929535"
---
# <a name="compound-operators-transact-sql"></a>Verbundoperatoren (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Verbundoperatoren führen einen Vorgang aus und legen einen ursprünglichen Wert auf das Ergebnis des Vorgangs fest. Beispiel: Wenn eine Variable @x gleich 35 ist, übernimmt @x += 2 den ursprünglichen Wert von @x, addiert 2 und legt @x auf diesen neuen Wert (37) fest.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] stellt die folgenden Verbundoperatoren bereit:  
  
|Operator|Link zu weiteren Informationen|Action|  
|--------------|------------------------------|------------|  
|+=|[+= &#40;Add Assignment&#41; &#40;Transact-SQL&#41; (+= (Additionszuweisung) (Transact-SQL))](../../t-sql/language-elements/add-equals-transact-sql.md)|Addiert etwas zum ursprünglichen Wert und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|-=|[-= &#40;Subtract Assignment&#41; &#40;Transact-SQL&#41; (-= (Subtraktionszuweisung) (Transact-SQL))](../../t-sql/language-elements/subtract-equals-transact-sql.md)|Subtrahiert etwas vom ursprünglichen Wert und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|*=|[&#42;= &#40;Multiply Assignment&#41; &#40;Transact-SQL&#41; (*= (Multiplikationszuweisung) (Transact-SQL))](../../t-sql/language-elements/multiply-equals-transact-sql.md)|Multipliziert mit einem Betrag und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|/=|[&#40;Divide Assignment&#41; &#40;Transact-SQL&#41; (Divisionszuweisung) (Transact-SQL)](../../t-sql/language-elements/divide-equals-transact-sql.md)|Dividiert durch einen Betrag und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|%=|[Modulus Assignment &#40;Transact-SQL&#41; (Modulozuweisung (Transact-SQL))](../../t-sql/language-elements/modulo-equals-transact-sql.md)|Dividiert durch einen Betrag und legt den ursprünglichen Wert auf den Modulo fest.|  
|&=|[&= &#40;Bitwise AND Assignment&#41; &#40;Transact-SQL&#41; (&= (Bitweises UND und Zuweisung) (Transact-SQL))](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)|Führt eine bitweise AND-Operation aus und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|^=|[^= &#40;Bitwise Exclusive OR Assignment&#41; &#40;Transact-SQL&#41; (^= (bitweises exklusives ODER mit Zuweisung) (Transact-SQL))](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)|Führt eine bitweise exklusive OR-Operation aus und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|&#124;=|[&#124;= &#40;Bitwise OR Assignment&#41; &#40;Transact-SQL&#41; (|= (bitweises ODER mit Zuweisung) (Transact-SQL))](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)|Führt eine bitweise OR-Operation aus und legt den ursprünglichen Wert auf das Ergebnis fest.|  
  
## <a name="syntax"></a>Syntax  
  
```  
  
expression operator expression  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein gültiger [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) eines Datentyps der numerischen Kategorie.  
  
## <a name="result-types"></a>Ergebnistypen  
 Gibt einen Wert vom Datentyp des Arguments zurück, das in der Rangfolge höher steht. Weitere Informationen finden Sie unter [Rangfolge der Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Bemerkungen  
 Weitere Informationen finden Sie in den Themen zu jedem Operator.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen sind Verbundoperationen dargestellt.  
  
```  
DECLARE @x1 int = 27;  
SET @x1 += 2 ;  
SELECT @x1 AS Added_2;  
  
DECLARE @x2 int = 27;  
SET @x2 -= 2 ;  
SELECT @x2 AS Subtracted_2;  
  
DECLARE @x3 int = 27;  
SET @x3 *= 2 ;  
SELECT @x3 AS Multiplied_by_2;  
  
DECLARE @x4 int = 27;  
SET @x4 /= 2 ;  
SELECT @x4 AS Divided_by_2;  
  
DECLARE @x5 int = 27;  
SET @x5 %= 2 ;  
SELECT @x5 AS Modulo_of_27_divided_by_2;  
  
DECLARE @x6 int = 9;  
SET @x6 &= 13 ;  
SELECT @x6 AS Bitwise_AND;  
  
DECLARE @x7 int = 27;  
SET @x7 ^= 2 ;  
SELECT @x7 AS Bitwise_Exclusive_OR;  
  
DECLARE @x8 int = 27;  
SET @x8 |= 2 ;  
SELECT @x8 AS Bitwise_OR;  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Bitweise Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  
