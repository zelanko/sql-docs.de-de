---
title: HAVING (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/21/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HAVING
- HAVING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restricting conditions for result set
- search conditions [SQL Server], HAVING clause
- HAVING clause
- HAVING clause, about HAVING clause
ms.assetid: 55650709-001e-42f4-902f-ead09a3c34af
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2a574e3f7348c4641665b067193c54604145386c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "76315610"
---
# <a name="select---having-transact-sql"></a>SELECT – HAVING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Suchbedingung für eine Gruppe oder ein Aggregat an. HAVING kann nur mit der SELECT-Anweisung verwendet werden. HAVING wird in der Regel mit einer GROUP BY-Klausel verwendet. Wenn GROUP BY nicht verwendet wird, gibt es eine implizite einzelne, aggregierte Gruppe.   
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
[ HAVING <search condition> ]  
```  
  
## <a name="arguments"></a>Argumente  
\<search_condition> gibt ein oder mehrere Prädikate für Gruppen und Aggregate an, die erfüllt werden müssen. Weitere Informationen zu Suchbedingungen und Prädikaten finden Sie unter [Suchbedingung &#40;Transact-SQL&#41;](../../t-sql/queries/search-condition-transact-sql.md).  
  
 Die Datentypen **text**, **image** und **ntext** können in einer HAVING-Klausel nicht verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel, in dem eine einfache `HAVING`-Klausel verwendet wird, werden die Gesamtsummen für `SalesOrderID` aus der `SalesOrderDetail`-Tabelle abgerufen, die `$100000.00` überschreiten.  
  
```sql
USE AdventureWorks2012 ;  
GO  
SELECT SalesOrderID, SUM(LineTotal) AS SubTotal  
FROM Sales.SalesOrderDetail  
GROUP BY SalesOrderID  
HAVING SUM(LineTotal) > 100000.00  
ORDER BY SalesOrderID ;  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel wird eine `HAVING`-Klausel zum Abrufen der Summe von `SalesAmount` verwendet, die `80000` für alle `OrderDateKey`-Werte aus der `FactInternetSales`-Tabelle überschreiten.  
  
```sql
-- Uses AdventureWorks  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSales  
GROUP BY OrderDateKey   
HAVING SUM(SalesAmount) > 80000  
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [GROUP BY &#40;Transact-SQL&#41;](../../t-sql/queries/select-group-by-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
  
  

