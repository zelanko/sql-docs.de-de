---
description: Verbundoperatoren (Transact-SQL)
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
ms.openlocfilehash: e42ce0876a6354056ae13daea43878a231bd5306
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88361806"
---
# <a name="compound-operators-transact-sql"></a>Verbundoperatoren (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Verbundoperatoren führen einen Vorgang aus und legen einen ursprünglichen Wert auf das Ergebnis des Vorgangs fest. Beispiel: Wenn eine Variable @x gleich 35 ist, übernimmt @x += 2 den ursprünglichen Wert von @x, addiert 2 und legt @x auf diesen neuen Wert (37) fest.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] stellt die folgenden Verbundoperatoren bereit:  
  
|Operator|Link zu weiteren Informationen|Aktion|  
|--------------|------------------------------|------------|  
|+=|[+= &#40;Add Assignment&#41; &#40;Transact-SQL&#41; (+= (Additionszuweisung) (Transact-SQL))](../../t-sql/language-elements/add-equals-transact-sql.md)|Addiert etwas zum ursprünglichen Wert und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|-=|[-= &#40;Subtract Assignment&#41; &#40;Transact-SQL&#41; (-= (Subtraktionszuweisung) (Transact-SQL))](../../t-sql/language-elements/subtract-equals-transact-sql.md)|Subtrahiert etwas vom ursprünglichen Wert und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|*=|[&#42;= &#40;Multiply Assignment&#41; &#40;Transact-SQL&#41; (*= (Multiplikationszuweisung) (Transact-SQL))](../../t-sql/language-elements/multiply-equals-transact-sql.md)|Multipliziert mit einem Betrag und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|/=|[&#40;Divide Assignment&#41; &#40;Transact-SQL&#41; (Divisionszuweisung) (Transact-SQL)](../../t-sql/language-elements/divide-equals-transact-sql.md)|Dividiert durch einen Betrag und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|%=|[Modulus Assignment &#40;Transact-SQL&#41; (Modulozuweisung (Transact-SQL))](../../t-sql/language-elements/modulo-equals-transact-sql.md)|Dividiert durch einen Betrag und legt den ursprünglichen Wert auf den Modulo fest.|  
|&=|[&= &#40;Bitwise AND Assignment&#41; &#40;Transact-SQL&#41; (&= (Bitweises UND und Zuweisung) &#40;Transact-SQL&#41;)](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)|Führt eine bitweise AND-Operation aus und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|^=|[^= &#40;Bitwise Exclusive OR Assignment&#41; &#40;Transact-SQL&#41; (^= (Zuweisung mit bitweisem exklusiven OR (Transact-SQL))](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)|Führt eine bitweise exklusive OR-Operation aus und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|&#124;=|[&#124;= &#40;Bitwise OR Assignment&#41; &#40;Transact-SQL&#41; (Zuweisung mit bitweisem OR (Transact-SQL))](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)|Führt eine bitweise OR-Operation aus und legt den ursprünglichen Wert auf das Ergebnis fest.|  
  
## <a name="syntax"></a>Syntax  
  
```  
  
expression operator expression  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *expression*  
 Ein gültiger [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) eines Datentyps der numerischen Kategorie.  
  
## <a name="result-types"></a>Ergebnistypen  
 Gibt einen Wert vom Datentyp des Arguments zurück, das in der Rangfolge höher steht. Weitere Informationen finden Sie unter [Rangfolge der Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Hinweise  
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
  
## <a name="see-also"></a>Siehe auch  
 [Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Bitweise Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  
