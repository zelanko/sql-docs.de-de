---
description: '* (Multiplikation) (Transact-SQL)'
title: '* (Multiplikation) (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '*_TSQL'
- '*'
dev_langs:
- TSQL
helpviewer_keywords:
- '* (multiply operator)'
- multiplication [SQL Server]
- multiply operator (*)
ms.assetid: 34beb660-db19-46ca-ac90-2218471457bf
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4265eac0332833e2a3fdae2957e3ef37b7b62707
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88467642"
---
# <a name="-multiplication-transact-sql"></a>* (Multiplikation) (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Multiplikation zweier Ausdrücke (arithmetischer Operator für die Multiplikation).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
expression * expression  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *expression*  
 Ist jeder gültige [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) eines Datentyps der numerischen Datentypkategorie. Dies gilt allerdings nicht für die Datentypen **datetime** und **smalldatetime**.  
  
## <a name="result-types"></a>Ergebnistypen  
 Gibt einen Wert vom Datentyp des Arguments zurück, das in der Rangfolge höher steht. Weitere Informationen finden Sie unter [Rangfolge der Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Produkt-ID, der Name, der Listenpreis und der neue Listenpreis für alle Mountainbikes in der `Product`-Tabelle abgerufen. Mithilfe des arithmetischen Operators `*` wird der neue Listenpreis berechnet (`ListPrice` multipliziert mit `1.15`).  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID, Name, ListPrice, ListPrice * 1.15 AS NewPrice  
FROM Production.Product  
WHERE Name LIKE 'Mountain-%'  
ORDER BY ProductID ASC;  
GO  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel wird der Vor- und der Nachname von Mitarbeitern aus der `dimEmployee`-Tabelle abgerufen und die Bezahlung für jede `VacationHours` für jeden Mitarbeiter berechnet.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, BaseRate * VacationHours AS VacationPay  
FROM DimEmployee  
ORDER BY lastName ASC;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Integrierte Funktionen &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)   
 [&#42;= &#40;Multiplikationszuweisung&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/multiply-equals-transact-sql.md)   
 [Verbundoperatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


