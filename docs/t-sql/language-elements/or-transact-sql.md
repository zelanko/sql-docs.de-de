---
description: OR (Transact-SQL)
title: OR (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- OR_TSQL
- OR
dev_langs:
- TSQL
helpviewer_keywords:
- conditions [SQL Server], combining
- combining conditions
- OR operator
ms.assetid: b730a256-4a63-4880-9906-65b05cd9caf2
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 11dbf45f7376a1a5557331dbd0466443bbd92739
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422494"
---
# <a name="or-transact-sql"></a>OR (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Kombiniert zwei Bedingungen. Werden in einem Ausdruck mehrere logische Operatoren verwendet, werden OR-Operatoren nach AND-Operatoren ausgewertet. Sie können jedoch die Reihenfolge der Auswertung ändern, indem Sie Klammern verwenden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
boolean_expression OR boolean_expression  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *boolean_expression*  
 Ein gültiger [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md), der TRUE, FALSE oder UNKNOWN zurückgibt.  
  
## <a name="result-types"></a>Ergebnistypen  
 **Boolescher Wert**  
  
## <a name="result-value"></a>Ergebniswert  
 OR gibt TRUE zurück, falls der Wert für mindestens eine der Bedingungen TRUE ist.  
  
## <a name="remarks"></a>Hinweise  
 Die folgende Tabelle zeigt das Ergebnis des OR-Operators.  
  
||true|false|UNKNOWN|  
|------|----------|-----------|-------------|  
|**TRUE**|TRUE|TRUE|TRUE|  
|**FALSE**|true|false|UNKNOWN|  
|**UNKNOWN**|true|UNKNOWN|UNKNOWN|  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden mithilfe der `vEmployeeDepartmentHistory`-Sicht die Namen der `Quality Assurance`-Mitarbeiter abgerufen, die in der Abend- oder Nachtschicht arbeiten. Ohne die Angabe der Klammern gibt die Abfrage `Quality Assurance`-Mitarbeiter zurück, die in der Abendschicht arbeiten, und alle Mitarbeiter, die in der Nachtschicht arbeiten.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, Shift   
FROM HumanResources.vEmployeeDepartmentHistory  
WHERE Department = 'Quality Assurance'  
   AND (Shift = 'Evening' OR Shift = 'Night');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 FirstName    LastName         Shift 
 ------------ ---------------- ------- 
 Andreas      Berglund         Evening 
 Sootha       Charncherngkha   Night
 ```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel werden die Namen aller Mitarbeiter abgerufen, deren `BaseRate`-Verdienst entweder kleiner als 20 ist oder deren `HireDate`-Datumswert auf den 1. Januar 2001 oder einen späteren Tag fällt.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, BaseRate, HireDate   
FROM DimEmployee  
WHERE BaseRate < 10 OR HireDate >= '2001-01-01';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Integrierte Funktionen &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
  
  


