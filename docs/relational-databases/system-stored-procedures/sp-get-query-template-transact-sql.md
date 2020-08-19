---
description: sp_get_query_template (Transact-SQL)
title: sp_get_query_template (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_get_query_template
- sp_get_query_template_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_get_query_template
ms.assetid: 85e9bef7-2417-41a8-befa-fe75507d9bf2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b6bef227f94188afe6f1eade92c54ff119982902
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447092"
---
# <a name="sp_get_query_template-transact-sql"></a>sp_get_query_template (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt das parametrisierte Format einer Abfrage zurück. Die zurückgegebenen Ergebnisse imitieren das parametrisierte Format einer Abfrage, das aus der Verwendung von erzwungener Parametrisierung resultiert. sp_get_query_template wird hauptsächlich beim Erstellen von Vorlagen Plan Hinweis Listen verwendet.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_get_query_template  
   [ @querytext = ] N'query_text'  
   , @templatetext OUTPUT   
   , @parameters OUTPUT   
```  
  
## <a name="arguments"></a>Argumente  
 "*query_text*"  
 Die Abfrage, für die die parametrisierte Version erzeugt werden soll. '*query_text*' muss in einfache Anführungszeichen eingeschlossen werden, und ihm muss der N-Unicode-Spezifizierer vorangestellt werden. N '*query_text*' ist der Wert, der dem @querytext Parameter zugewiesen ist. Dies ist vom Typ **nvarchar (max)**.  
  
 @templatetext  
 Ist ein Ausgabeparameter vom Typ **nvarchar (max)**, der wie angegeben angegeben wird, um die parametrisierte Form von *query_text* als Zeichenfolgenliteralzeichen zu empfangen.  
  
 @parameters  
 Ist ein Ausgabeparameter vom Typ **nvarchar (max)**, der wie angegeben bereitgestellt wird, um ein Zeichenfolgenliteral der Parameternamen und Datentypen zu empfangen, die in parametrisiert wurden @templatetext .  
  
## <a name="remarks"></a>Bemerkungen  
 Der Parameter sp_get_query_template gibt in folgenden Situationen einen Fehler zurück:  
  
-   In *query_text*werden keine konstanten Literalwerte parametrisiert.  
  
-   *query_text* ist NULL, keine Unicode-Zeichenfolge, syntaktisch ungültig oder kann nicht kompiliert werden.  
  
 Wenn sp_get_query_template einen Fehler zurückgibt, werden die Werte der @templatetext Ausgabeparameter und nicht geändert @parameters .  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der public-Datenbankrolle.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt das parametrisierte Format einer Abfrage zurück, die zwei konstante literale Werte enthält.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @my_templatetext nvarchar(max)  
DECLARE @my_parameters nvarchar(max)  
EXEC sp_get_query_template   
    N'SELECT pi.ProductID, SUM(pi.Quantity) AS Total  
        FROM Production.ProductModel pm   
        INNER JOIN Production.ProductInventory pi  
        ON pm.ProductModelID = pi.ProductID  
        WHERE pi.ProductID = 2  
        GROUP BY pi.ProductID, pi.Quantity  
        HAVING SUM(pi.Quantity) > 400',  
@my_templatetext OUTPUT,  
@my_parameters OUTPUT;  
SELECT @my_templatetext;  
SELECT @my_parameters;  
```  
  
 Im Folgenden sehen Sie die parametrisierten Werte des `@my_templatetext``OUTPUT`-Parameters:  
  
 `select pi . ProductID , SUM ( pi . Quantity ) as Total`  
  
 `from Production . ProductModel pm`  
  
 `inner join Production . ProductInventory pi`  
  
 `on pm . ProductModelID = pi . ProductID`  
  
 `where pi . ProductID = @0`  
  
 `group by pi . ProductID , pi . Quantity`  
  
 `having SUM ( pi . Quantity ) > 400`  
  
 Beachten Sie, dass das erste konstante Literal, `2`, in einen Parameter konvertiert wird. Das zweite Literal, `400`, wird nicht konvertiert, da es sich in einer `HAVING`-Klausel befindet. Die von sp_get_query_template zurückgegebenen Ergebnisse imitieren das parametrisierte Format einer Abfrage, wenn die PARAMETERIZATION-Option von ALTER DATABASE auf FORCED festgelegt wird.  
  
 Im Folgenden sehen Sie die parametrisierten Werte des `@my_parameters OUTPUT`-Parameters:  
  
```  
@0 int  
```  
  
> [!NOTE]  
>  Die Reihenfolge und Benennung von Parametern in der Ausgabe von sp_get_query_template kann sich von einem zum nächsten Quick Fix Engineering, Service Pack und Versionsupgrade für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ändern. Upgrades können auch bewirken, dass eine andere Gruppe mit konstanten Literalen für dieselbe Abfrage parametrisiert und unterschiedliche Abstände auf die Ergebnisse beider Ausgabeparameter angewendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Angeben des Abfrageparametrisierungsverhaltens mithilfe von Planhinweislisten](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md)  
  
  
