---
title: Operatorrangfolge (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], precedence
- operator precedence [Transact-SQL]
- order of operator execution [Transact-SQL]
- precedence [SQL Server], operators
ms.assetid: f04d2439-6fff-4e4c-801f-cc62faef510a
author: rothja
ms.author: jroth
ms.openlocfilehash: 37c1bac44b4dff2be7735f89243b6e273eca0775
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68121924"
---
# <a name="operator-precedence-transact-sql"></a>Operatorrangfolge (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Besitzt ein komplexer Ausdruck mehrere Operatoren, bestimmt die Operatorenrangfolge die Reihenfolge der Vorgänge. Die Ausführungsreihenfolge kann sich entscheidend auf das Ergebnis auswirken.  
  
 Operatoren besitzen die in der folgenden Tabelle dargestellte Rangfolge. Ein Operator, der höher in der Rangfolge steht, wird vor einem Operator niedrigeren Ranges ausgewertet. In der folgenden Tabelle entspricht 1 dem höchsten Rang, und 8 entspricht dem niedrigsten Rang.
  
|Ebene|Operatoren|  
|-----------|---------------|  
|1|~ (Bitweises NOT)|  
|2|* (Multiplikation) / (Division), % (Modulo)|  
|3|+ (Positiv), - (Negativ), + (Addition), + (Verkettung), - (Subtraktion), & (bitweises UND), ^ (bitweises exklusives ODER), &#124; (bitweises ODER)|  
|4|=, >, \<, >=, <=, <>, !=, !>, !< (Vergleichsoperatoren)|  
|5|NICHT|  
|6|AND|  
|7|ALL, ANY, BETWEEN, IN, LIKE, OR, SOME|  
|8|= (Zuweisung)|  
  
 Wenn zwei Operatoren die gleiche Position in der Rangfolge belegen, werden sie anhand ihrer Position im Ausdruck von links nach rechts ausgewertet. So wird in dem Ausdruck, der in der folgenden `SET`-Anweisung verwendet wird, der Subtraktionsoperator vor dem Additionsoperator ausgewertet.  
  
```sql  
DECLARE @MyNumber int;  
SET @MyNumber = 4 - 2 + 27;  
-- Evaluates to 2 + 27 which yields an expression result of 29.  
SELECT @MyNumber;  
```  
  
 Mit Klammern kann die definierte Rangfolge von Operatoren in einem Ausdruck überschrieben werden. Der Inhalt der Klammern wird in einen einzelnen Wert ausgewertet. Dieser Wert kann von jedem Operator außerhalb dieser Klammern verwendet werden.  
  
 In dem Ausdruck, der in der folgenden `SET`-Anweisung verwendet wird, besitzt der Multiplikationsoperator Vorrang vor dem Additionsoperator. Der Multiplikationsvorgang wird zuerst ausgewertet. Das Ergebnis des Ausdrucks lautet `13`.  
  
```sql  
DECLARE @MyNumber int;  
SET @MyNumber = 2 * 4 + 5;  
-- Evaluates to 8 + 5 which yields an expression result of 13.  
SELECT @MyNumber;  
```  
  
 In dem Ausdruck, der in der folgenden `SET`-Anweisung verwendet wird, bewirken die Klammern, dass die Addition zuerst ausgewertet wird. Das Ergebnis des Ausdrucks lautet `18`.  
  
```sql  
DECLARE @MyNumber int;  
SET @MyNumber = 2 * (4 + 5);  
-- Evaluates to 2 * 9 which yields an expression result of 18.  
SELECT @MyNumber;  
```  
  
 In einem Ausdruck mit geschachtelten Klammern wird der Ausdruck der höchsten Schachtelungstiefe zuerst ausgewertet. Das folgende Beispiel enthält geschachtelte Klammern, und der Ausdruck `5 - 3` ist der Ausdruck mit der höchsten Schachtelungstiefe. Dieser Ausdruck ergibt den Wert `2`. Danach wird mit dem Additionsoperator (`+`) dieses Ergebnis zu `4` addiert, was den Wert `6` ergibt. Schließlich wird `6` mit `2` multipliziert, sodass sich als Ergebnis des Ausdrucks `12` ergibt.  
  
```sql  
DECLARE @MyNumber int;  
SET @MyNumber = 2 * (4 + (5 - 3) );  
-- Evaluates to 2 * (4 + 2) which then evaluates to 2 * 6, and   
-- yields an expression result of 12.  
SELECT @MyNumber;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Logische Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/logical-operators-transact-sql.md)   
 [Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Integrierte Funktionen &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
