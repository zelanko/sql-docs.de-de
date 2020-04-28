---
title: sp_prepare (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/28/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepare_TSQL
- sp_cursor_prepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepare
ms.assetid: f328c9eb-8211-4863-bafa-347e1bf7bb3f
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: acadb311dac786d9f1c5dbcc86fac9b2609fb959
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68085799"
---
# <a name="sp_prepare-transact-sql"></a>sp_prepare (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

Bereitet eine parametrisierte [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung vor und gibt ein Anweisungs *handle* zur Ausführung zurück.  `sp_prepare`wird aufgerufen, indem ID = 11 in einem Tabular Data Stream-Paket (TDS) angegeben wird.  
  
 ![Artikellinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_prepare handle OUTPUT, params, stmt, options  
```  
  
## <a name="arguments"></a>Argumente  
 *bewältigen*  
 Ist ein SQL Server generierter Bezeichner für den *handle* . *handle* ist ein erforderlicher Parameter mit einem **int** -Rückgabewert.  
  
 *params*  
 Identifiziert parametrisierte Anweisungen. Die *params* -Definition der Variablen wird in der Anweisung an die Stelle der Parametermarkierungen gesetzt. *params* ist ein erforderlicher Parameter, der einen Eingabewert vom Typ **ntext**, **nchar**,oder **nvarchar** erfordert. Geben Sie einen NULL-Wert ein, wenn die Anweisung nicht parametrisiert ist.  
  
 *stmt*  
 Definiert das Resultset des Cursors. Der *stmt* -Parameter ist erforderlich und erfordert einen Eingabe Wert vom Typ **ntext**, **NCHAR**oder **nvarchar** .  
  
 *options*  
 Ein optionaler Parameter, der eine Beschreibung der Spalten im Cursorresultset zurückgibt. die *Optionen* erfordern den folgenden int-Eingabe Wert:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
## <a name="examples"></a>Beispiele  
A. Im folgenden Beispiel wird eine einfache Anweisung vorbereitet und ausgeführt.  
  
```sql  
DECLARE @P1 int;  
EXEC sp_prepare @P1 output,   
    N'@P1 nvarchar(128), @P2 nvarchar(100)',  
    N'SELECT database_id, name FROM sys.databases WHERE name=@P1 AND state_desc = @P2';  
EXEC sp_execute @P1, N'tempdb', N'ONLINE';  
EXEC sp_unprepare @P1;  
```

B. Im folgenden Beispiel wird eine-Anweisung in der AdventureWorks2016-Datenbank vorbereitet und später mit dem Handle ausgeführt.

```sql
-- Prepare query
DECLARE @P1 int;  
EXEC sp_prepare @P1 output,   
    N'@Param int',  
    N'SELECT *
FROM Sales.SalesOrderDetail AS sod
INNER JOIN Production.Product AS p ON sod.ProductID = p.ProductID
WHERE SalesOrderID = @Param
ORDER BY Style DESC;';  

-- Return handle for calling application
SELECT @P1;
GO
```
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```
-----------
1

(1 row affected)
```

Die Anwendung führt die Abfrage dann zweimal mit dem Handle-Wert 1 aus, bevor der vorbereitete Plan verworfen wird.

```sql
EXEC sp_execute 1, 49879;  
GO

EXEC sp_execute 1, 48766;
GO

EXEC sp_unprepare 1; 
GO
```
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  

