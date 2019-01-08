---
title: Sp_control_plan_guide (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_control_plan_guide
- sp_control_plan_guide_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_control_plan_guide
ms.assetid: c96d43d5-6507-4d66-b3f5-f44c0617cb5c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 29fbce7f3e8fee200384f6162b28576d96593b37
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52502982"
---
# <a name="spcontrolplanguide-transact-sql"></a>sp_control_plan_guide (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht, aktiviert oder deaktiviert eine Planhinweisliste.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_control_plan_guide [ @operation = ] N'<control_option>'  
  [ , [ @name = ] N'plan_guide_name' ]  
  
<control_option>::=  
{   
    DROP   
  | DROP ALL  
  | DISABLE  
  | DISABLE ALL  
  | ENABLE   
  | ENABLE ALL  
}  
```  
  
## <a name="arguments"></a>Argumente  
 **N'** *Plan_guide_name* **"**  
 Gibt die Planhinweisliste an, die gelöscht, aktiviert oder deaktiviert wird. *Plan_guide_name* wird in der aktuellen Datenbank aufgelöst. Wenn nicht angegeben, *Plan_guide_name* der Standardwert ist NULL.  
  
 DROP  
 Löscht die Planhinweisliste, die anhand des *Plan_guide_name*. Nachdem eine Planhinweisliste gelöscht wurde, werden zukünftige Ausführungen einer Abfrage, die zuvor mit der Planhinweisliste übereingestimmt hat, nicht von dieser Liste beeinflusst.  
  
 DROP ALL  
 Löscht alle Planhinweislisten in der aktuellen Datenbank. **N'**_Plan_guide_name_ kann nicht angegeben werden, wenn DROP ALL angegeben wird.  
  
 DISABLE  
 Deaktiviert die Planhinweisliste, die anhand des *Plan_guide_name*. Nachdem eine Planhinweisliste deaktiviert wurde, werden zukünftige Ausführungen einer Abfrage, die zuvor mit der Planhinweisliste übereingestimmt hat, nicht von dieser Liste beeinflusst.  
  
 DISABLE ALL  
 Deaktiviert alle Planhinweislisten in der aktuellen Datenbank. **N'**_Plan_guide_name_ kann nicht angegeben werden, wenn DISABLE ALL angegeben wird.  
  
 ENABLE  
 Ermöglicht die Planhinweisliste, die anhand des *Plan_guide_name*. Eine aktivierte Planhinweisliste kann mit einer geeigneten Abfrage abgeglichen werden. Planhinweislisten werden standardmäßig bei ihrer Erstellung aktiviert.  
  
 ENABLE ALL  
 Aktiviert alle Planhinweislisten in der aktuellen Datenbank. **N'**_Plan_guide_name_**"** kann nicht angegeben werden, wenn ENABLE ALL angegeben wird.  
  
## <a name="remarks"></a>Hinweise  
 Das Löschen oder Ändern einer Funktion, einer gespeicherten Prozedur oder eines DML-Triggers, auf die bzw. den in einer Planhinweisliste verwiesen wird, verursacht einen Fehler.  
  
 Das Deaktivieren einer deaktivierten bzw. das Aktivieren einer aktivierten Planhinweisliste hat keine Auswirkung und kann ausgeführt werden, ohne einen Fehler zu verursachen.  
  
 Planhinweislisten sind nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Editionen und unterstütze Funktionen für den SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md). Sie können jedoch ausführen **Sp_control_plan_guide** mit der Drop- oder DROP ALL-Option in keiner Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="permissions"></a>Berechtigungen  
 Auszuführende **Sp_control_plan_guide** auf eine Planhinweisliste des Typs "OBJECT" (erstellt durch angeben  **@type ='** Objekt **"** ) erfordert die ALTER-Berechtigung für das Objekt, das wird von der Planhinweisliste verwiesen wird. Für alle anderen Planhinweislisten ist die ALTER DATABASE-Berechtigung erforderlich.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-enabling-disabling-and-dropping-a-plan-guide"></a>A. Aktivieren, Deaktivieren und Löschen einer Planhinweisliste  
 In dem folgenden Beispiel wird eine Planhinweisliste erstellt, deaktiviert, aktiviert und gelöscht.  
  
```  
--Create a procedure on which to define the plan guide.  
IF OBJECT_ID(N'Sales.GetSalesOrderByCountry', N'P') IS NOT NULL  
    DROP PROCEDURE Sales.GetSalesOrderByCountry;  
GO  
CREATE PROCEDURE Sales.GetSalesOrderByCountry   
    (@Country nvarchar(60))  
AS  
BEGIN  
    SELECT *  
    FROM Sales.SalesOrderHeader AS h   
    INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
    INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
    WHERE t.CountryRegionCode = @Country;  
END  
GO  
--Create the plan guide.  
EXEC sp_create_plan_guide N'Guide3',  
    N'SELECT *  
    FROM Sales.SalesOrderHeader AS h   
    INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
    INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
    WHERE t.CountryRegionCode = @Country',  
    N'OBJECT',  
    N'Sales.GetSalesOrderByCountry',  
    NULL,  
    N'OPTION (OPTIMIZE FOR (@Country = N''US''))';  
GO  
--Disable the plan guide.  
EXEC sp_control_plan_guide N'DISABLE', N'Guide3';  
GO  
--Enable the plan guide.  
EXEC sp_control_plan_guide N'ENABLE', N'Guide3';  
GO  
--Drop the plan guide.  
EXEC sp_control_plan_guide N'DROP', N'Guide3';  
```  
  
### <a name="b-disabling-all-plan-guides-in-the-current-database"></a>B. Deaktivieren aller Planhinweislisten in der aktuellen Datenbank  
 In dem folgenden Beispiel werden alle Planhinweislisten in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank deaktiviert.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_control_plan_guide N'DISABLE ALL';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sys.plan_guides &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-plan-guides-transact-sql.md)   
 [Planhinweislisten](../../relational-databases/performance/plan-guides.md)  
  
  
