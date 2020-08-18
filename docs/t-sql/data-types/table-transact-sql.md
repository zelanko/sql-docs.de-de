---
description: table (Transact-SQL)
title: table (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/27/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- table data type [SQL Server]
- table variables [SQL Server]
ms.assetid: 1ef0b60e-a64c-4e97-847b-67930e3973ef
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ad743fc9864207dedcad050428646abf80fa4f59
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88311446"
---
# <a name="table-transact-sql"></a>table (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Entspricht einem speziellen Datentyp, der zum Speichern eines Resultsets für die Verarbeitung zu einem späteren Zeitpunkt verwendet wird. **table** wird hauptsächlich für die temporäre Speicherung eines Zeilensatzes verwendet, der als Resultset einer Tabellenwertfunktion zurückgegeben wird. Für Funktionen und Variablen kann der Typ **table** angegeben werden. **table**-Variablen können in Funktionen, gespeicherten Prozeduren und Batches verwendet werden. Verwenden Sie zum Deklarieren von Variablen des **table**-Typs die Anweisung [DECLARE @local_variable](../../t-sql/language-elements/declare-local-variable-transact-sql.md).
  

**Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]und höher), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
table_type_definition ::=   
    TABLE ( { <column_definition> | <table_constraint> } [ ,...n ] )   
  
<column_definition> ::=   
    column_name scalar_data_type   
    [ COLLATE <collation_definition> ]   
    [ [ DEFAULT constant_expression ] | IDENTITY [ ( seed , increment ) ] ]   
    [ ROWGUIDCOL ]   
    [ column_constraint ] [ ...n ]   
  
 <column_constraint> ::=   
    { [ NULL | NOT NULL ]   
    | [ PRIMARY KEY | UNIQUE ]   
    | CHECK ( logical_expression )   
    }   
  
<table_constraint> ::=   
     { { PRIMARY KEY | UNIQUE } ( column_name [ ,...n ] )  
     | CHECK ( logical_expression )   
     }   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
*table_type_definition*  
Dieselbe Teilmenge von Informationen, die zum Definieren einer Tabelle in CREATE TABLE verwendet wird. Die Tabellendeklaration schließt Spaltendefinitionen, Namen, Datentypen und Einschränkungen ein. Die einzigen zulässigen Einschränkungstypen sind PRIMARY KEY, UNIQUE KEY und NULL.  
Weitere Informationen zur Syntax finden Sie unter [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md), [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md) und [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md).
  
*collation_definition*  
Die Sortierung einer Spalte, die aus einem [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Gebietsschema und einer Vergleichsart, einem Windows-Gebietsschema und der Binärschreibweise oder einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sortierung besteht. Wenn *collation_definition* nicht angegeben ist, erbt die Spalte die Sortierung der aktuellen Datenbank. Wenn die Spalte als CLR-benutzerdefinierter Typ (Common Language Runtime) definiert ist, erbt die Spalte die Sortierung des benutzerdefinierten Typs.
  
## <a name="remarks"></a>Bemerkungen  
**table** verweist anhand des Namens in der FROM-Klausel eines Batches auf Variablen, wie im folgenden Beispiel gezeigt:
  
```sql
SELECT Employee_ID, Department_ID FROM @MyTableVar;  
```  
  
Außerhalb einer FROM-Klausel muss ein Alias für Verweise auf **table**-Variablen verwendet werden, wie im folgenden Beispiel gezeigt wird:
  
```sql
SELECT EmployeeID, DepartmentID   
FROM @MyTableVar m  
JOIN Employee on (m.EmployeeID =Employee.EmployeeID AND  
   m.DepartmentID = Employee.DepartmentID);  
```  
  
**table**-Variablen bieten die folgenden Vorteile für Abfragen mit kleinerem Umfang, die über Abfragepläne verfügen, die sich nicht ändern (gilt auch für Szenarios mit vorwiegend vorhandenen Neukompilierungsaspekten):
-   Eine **table**-Variable verhält sich wie eine lokale Variable. Sie hat einen fest definierten Bereich. Diese Variable kann in der Funktion, der gespeicherten Prozedur oder dem Batch verwendet werden, in der bzw. dem sie deklariert ist.  
     Innerhalb dieses Bereichs kann eine **table**-Variable wie eine reguläre Tabelle verwendet werden. Sie kann überall angewendet werden, wo eine Tabelle oder ein Tabellenausdruck in SELECT-, INSERT-, UPDATE- und DELETE-Anweisungen verwendet wird. **table** kann jedoch nicht in der folgenden Anweisung verwendet werden:  
  
```sql
SELECT select_list INTO table_variable;
```
  
Für **table**-Variablen wird automatisch am Ende der Funktion, der gespeicherten Prozedur oder des Batches, in der bzw. dem sie definiert sind, ein Cleanup ausgeführt.
  
-   In gespeicherten Prozeduren verwendete **table**-Variablen verursachen weniger Neukompilierungen der gespeicherten Prozeduren als bei Verwendung temporärer Tabellen, wenn keine kostenbasierten Optionen vorhanden sind, welche die Leistung beeinflussen.  
-   Transaktionen, an denen **table**-Variablen beteiligt sind, dauern nur so lange wie das Update der **table**-Variablen. Daher sind für **table**-Variablen weniger Sperr- und Protokollierungsressourcen erforderlich.  
  
## <a name="limitations-and-restrictions"></a>Einschränkungen
**table**-Variablen haben keine Verteilungsstatistiken. Sie lösen keine Neukompilierungen aus. Daher erstellt der Optimierer in vielen Fällen einen Abfrageplan unter der Annahme, dass die „table“-Variable keine Zeilen enthält. Aus diesem Grund sollten Sie Tabellenvariablen mit Vorsicht verwenden, wenn Sie von einer großen Anzahl von Zeilen (mehr als 100) ausgehen. Für solche Fälle sind temporäre Tabellen möglicherweise die bessere Lösung. Verwenden Sie bei Abfragen, die einen Join der Tabelle mit anderen Tabellen ausführen, auch den RECOMPILE-Hinweis. Dieser führt dazu, dass der Optimierer die korrekte Kardinalität für die „table“-Variable verwendet.
  
**table**-Variablen werden im kostenbasierten Ansatzmodell des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Optimierers nicht unterstützt. Daher sollten sie nicht verwendet werden, wenn kostenbasierte Optionen erforderlich sind, um einen effizienten Abfrageplan zu erzielen. Temporäre Tabellen werden bevorzugt, wenn kostenbasierte Optionen erforderlich sind. Dieser Plan schließt in der Regel Abfragen mit Joins, Parallelverarbeitungsentscheidungen und Indexauswahloptionen ein.
  
Abfragen, die **table**-Variablen ändern, generieren keine Pläne für die parallele Abfrageausführung. Die Leistung kann beeinträchtigt sein, wenn große **table**-Variablen oder **table**-Variablen in komplexen Abfragen geändert werden. Erwägen Sie daher in Situationen, in denen **table**-Variablen geändert werden, die Verwendung von temporären Tabellen. Weitere Informationen finden Sie unter [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md). Abfragen, die **table**-Variablen lesen, ohne sie zu ändern, können weiterhin parallelisiert werden.

> [!IMPORTANT]
> Der Datenbank-Kompatibilitätsgrad 150 verbessert die Leistung der Tabellenvariablen mit der Einführung der **verzögerten Kompilierung von Tabellenvariablen**.  Weitere Informationen finden Sie unter [Verzögerte Kompilierung von Tabellenvariablen](../../relational-databases/performance/intelligent-query-processing.md#table-variable-deferred-compilation).
>
  
Die explizite Erstellung von Indizes für **table**-Variablen ist nicht möglich, zudem werden für **table**-Variablen keine Statistiken geführt. Mit [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] wurde eine neue Syntax eingeführt, die es erlaubt, bestimmte Indextypen inline mit der Tabellendefinition zu erstellen.  Mit dieser neuen Syntax können Sie Indizes für **table**-Variablen als Teil der Tabellendefinition erstellen. In einigen Fällen kann die Leistung verbessert werden, indem stattdessen temporäre Tabellen verwendet werden, die eine vollständige Unterstützung für Indizes und Statistiken bieten. Weitere Informationen zu temporären Tabellen und der Inlineerstellung von Indizes finden Sie unter [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).

CHECK-Einschränkungen, DEFAULT-Werte und berechnete Spalten in der **table**-Typdeklaration können keine benutzerdefinierten Funktionen aufrufen.
  
Zuweisungsvorgänge zwischen **table**-Variablen werden nicht unterstützt.
  
Transaktionsrollbacks wirken sich nicht auf **table**-Variablen aus, da diese Variablen einen eingeschränkten Bereich haben und kein Teil der permanenten Datenbank sind.
  
„table“-Variablen können nach ihrer Erstellung nicht mehr geändert werden.
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-declaring-a-variable-of-type-table"></a>A. Deklarieren einer Variablen vom Typ "table"  
Im folgenden Beispiel wird eine `table`-Variable erstellt, die die in der OUTPUT-Klausel der UPDATE-Anweisung angegebenen Werte speichert. Es folgen zwei `SELECT`-Anweisungen, die die Werte in `@MyTableVar` und die Ergebnisse des Updatevorgangs in der `Employee`-Tabelle zurückgeben. Die Ergebnisse in der `INSERTED.ModifiedDate`-Spalte weichen von den Werten in der `ModifiedDate`-Spalte in der `Employee`-Tabelle ab. Der Grund für die Abweichung ist, dass der `AFTER UPDATE`-Trigger, der den Wert von `ModifiedDate` auf das aktuelle Datum aktualisiert, in der `Employee`-Tabelle definiert ist. Die von `OUTPUT` zurückgegebenen Spalten spiegeln jedoch die Daten wider, bevor Trigger ausgelöst werden. Weitere Informationen finden Sie unter [OUTPUT-Klausel &#40;Transact-SQL&#41;](../../t-sql/queries/output-clause-transact-sql.md).
  
```sql
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table(  
    EmpID int NOT NULL,  
    OldVacationHours int,  
    NewVacationHours int,  
    ModifiedDate datetime);  
UPDATE TOP (10) HumanResources.Employee  
SET VacationHours = VacationHours * 1.25   
OUTPUT INSERTED.BusinessEntityID,  
       DELETED.VacationHours,  
       INSERTED.VacationHours,  
       INSERTED.ModifiedDate  
INTO @MyTableVar;  
--Display the result set of the table variable.  
SELECT EmpID, OldVacationHours, NewVacationHours, ModifiedDate  
FROM @MyTableVar;  
GO  
--Display the result set of the table.  
--Note that ModifiedDate reflects the value generated by an  
--AFTER UPDATE trigger.  
SELECT TOP (10) BusinessEntityID, VacationHours, ModifiedDate  
FROM HumanResources.Employee;  
GO  
```  
  
### <a name="b-creating-an-inline-table-valued-function"></a>B. Erstellen einer Inline-Tabellenwertfunktion  
Das folgende Beispiel gibt eine Inline-Tabellenwertfunktion zurück. Die Funktion gibt drei Spalten `ProductID`, `Name` und das Aggregat der gesamten Verkäufe des Jahres (nach Filiale sortiert) als `YTD Total` für jedes Produkt zurück, das an die Filiale verkauft wurde.
  
```sql
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'Sales.ufn_SalesByStore', N'IF') IS NOT NULL  
    DROP FUNCTION Sales.ufn_SalesByStore;  
GO  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
GO  
```  
  
Rufen Sie die Funktion mit dieser Abfrage auf.
  
```sql
SELECT * FROM Sales.ufn_SalesByStore (602);  
```  
  
## <a name="see-also"></a>Weitere Informationen
[COLLATE &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)  
[Benutzerdefinierte Funktionen](../../relational-databases/user-defined-functions/user-defined-functions.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[Verwenden von Tabellenwertparametern &#40;Datenbank-Engine&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)  
[Abfragehinweise &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md)
