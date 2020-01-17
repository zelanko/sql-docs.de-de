---
title: Aliase
description: Aliase in Azure SQL Data Warehouse und Parallel Data Warehouse.
titleSuffix: Azure SQL Data Warehouse
ms.custom: seo-lt-2019
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
ms.assetid: 7b3a5c74-05cf-4385-8ee6-6176d003cb8a
author: shkale-msft
ms.author: shkale
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 3b548dd789bc7e234eb527ffe5766f433a06d77e
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75244764"
---
# <a name="aliasing-azure-sql-data-warehouse-parallel-data-warehouse"></a>Aliasing (Azure SQL Data Warehouse, Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Aliasing ermöglicht das temporäre Ersetzen eines Tabellen- oder Spaltennamens in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]- oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)][!INCLUDE[DWsql](../../includes/dwsql-md.md)]-Abfragen durch eine kurze und leicht zu merkenden Zeichenfolge. Tabellenaliase werden häufig in JOIN-Abfragen verwendet, da die JOIN-Syntax vollqualifizierte Objektnamen erfordert, wenn sie auf Spalten verweist.  
  
 Aliase müssen einzelne Wörter sein, die die Objektbenennungsregeln erfüllen. Weitere Informationen finden Sie unter „Object Naming Rules“ (Objektbenennungsregeln) in [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]. Aliase dürfen keine Leerzeichen enthalten und nicht in einfache oder doppelte Anführungszeichen gesetzt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
object_source [ AS ] alias  
```  
  
## <a name="arguments"></a>Argumente  
 *object_source*  
 Der Name der Quelltabelle oder -spalte.  
  
 AS  
 Eine optionale Aliaspräposition. Beim Aliasing von Bereichsvariablen ist das Schlüsselwort AS nicht zulässig.  
  
 *alias*  
 Der gewünschte temporäre Verweisname für die Tabelle oder Spalte. Alle gültigen Objektnamen können verwendet werden. Weitere Informationen finden Sie unter „Object Naming Rules“ (Objektbenennungsregeln) in [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Das folgende Beispiel zeigt eine Abfrage mit mehreren Joins. In diesem Beispiel wird das Aliasing sowohl von Tabellen als auch von Spalten veranschaulicht.  
  
-   Spaltenaliasing: In diesem Beispiel wird sowohl Spalten als auch Ausdrücken, die Spalten in der ausgewählten Liste haben, ein Alias zugeordnet. `SalesTerritoryRegion AS SalesTR` stellt einen einfachen Spaltenalias dar. `Sum(SalesAmountQuota) AS TotalSales` veranschaulicht  
  
-   Tabellenaliasing: `dbo.DimSalesTerritory AS st` zeigt die Erstellung des `st`-Alias für die `dbo.DimSalesTerritory`-Tabelle.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) AS TotalSales, SalesTerritoryRegion AS SalesTR,  
    RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) AS RankResult  
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory AS st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
  
```  
  
 Das AS-Schlüsselwort kann wie unten dargestellt ausgeschlossen werden, wird aber häufig aus Gründen der Lesbarkeit verwendet.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) TotalSales, SalesTerritoryRegion SalesTR,  
RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) RankResult  
FROM dbo.DimEmployee e  
INNER JOIN dbo.FactSalesQuota sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  
  
  
