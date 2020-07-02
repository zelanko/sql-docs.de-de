---
title: sp_execute_remote (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/01/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sp_execute_remote
- sp_execute_remote_TSQL
helpviewer_keywords:
- remote execution
- queries, remote execution
ms.assetid: ca89aa4c-c4c1-4c46-8515-a6754667b3e5
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 9d257f5b52c6dfea82868b69570f2655675bb7ca
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85720284"
---
# <a name="sp_execute_remote-azure-sql-database"></a>sp_execute_remote (Azure SQL-Datenbank)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  Führt eine- [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung für eine einzelne Azure SQL-Remote Datenbank oder eine Gruppe von Datenbanken aus, die als Shards in einem horizontalen Partitionierungsschema fungieren.  
  
 Die gespeicherte Prozedur ist Teil des Features für elastische Abfragen.  Informationen finden Sie unter [Übersicht über elastische Datenbankabfragen in Azure SQL](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/) -Datenbank und [elastische Datenbankabfragen für Sharding (Horizontale Partitionierung)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-horizontal-partitioning/)  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_execute_remote [ @data_source_name = ] datasourcename  
[ , @stmt = ] statement  
[   
  { , [ @params = ] N'@parameter_name data_type [,...n ]' }   
     { , [ @param1 = ] 'value1' [ ,...n ] }  
]  
```  
  
## <a name="arguments"></a>Argumente  
 [ \@ data_source_name =] *DataSourceName*  
 Identifiziert die externe Datenquelle, in der die Anweisung ausgeführt wird. Weitere Informationen finden Sie unter [Erstellen einer externen Datenquelle &#40;Transact-SQL-&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md). Die externe Datenquelle kann vom Typ "RDBMS" oder "SHARD_MAP_MANAGER" sein.  
  
 [ \@ stmt =]- *Anweisung*  
 Eine Unicode-Zeichenfolge, die eine- [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung oder einen-Batch enthält. \@stmt muss entweder eine Unicode-Konstante oder eine Unicode-Variable sein. Komplexere Unicodeausdrücke, wie z. B. die Verkettung von zwei Zeichenfolgen mit dem +-Operator, sind nicht zulässig. Zeichenkonstanten sind nicht zulässig. Wenn eine Unicode-Konstante angegeben wird, muss Ihr ein **N**vorangestellt werden. Beispielsweise ist die Unicode-Konstante **N ' sp_who '** gültig, aber die Zeichen Konstante **' sp_who '** ist nicht. Die Länge der Zeichenfolge wird nur durch den verfügbaren Arbeitsspeicher des Datenbankservers begrenzt. Auf 64-Bit-Servern ist die Größe der Zeichenfolge auf 2 GB beschränkt, die maximale Größe von **nvarchar (max)**.  
  
> [!NOTE]  
>  \@stmt kann Parameter enthalten, die dieselbe Form wie ein Variablenname aufweisen, z. b.:`N'SELECT * FROM HumanResources.Employee WHERE EmployeeID = @IDParameter'`  
  
 Jeder in \@ stmt enthaltene Parameter muss über einen entsprechenden Eintrag in der \@ Parameter Definitionsliste params und in der Parameterwerte Liste verfügen.  
  
 [Parameter \@ =] N ' \@ *parameter_name * * data_type* [,... *n* ] '  
 Ist eine Zeichenfolge, die die Definitionen aller in stmt eingebetteten Parameter enthält \@ . Die Zeichenfolge muss entweder eine Unicode-Konstante oder eine Unicode-Variable sein. Jede Parameterdefinition besteht aus einem Parameternamen und einem Datentyp. *n* ist ein Platzhalter, der zusätzliche Parameter Definitionen angibt. Jeder in " \@ stmt" angegebene Parameter muss in "Parameters" definiert werden \@ . Wenn die [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung oder der Batch in \@ stmt keine Parameter enthält, \@ ist kein Parameter erforderlich. Der Standardwert für diesen Parameter ist NULL.  
  
 [ \@ param1 =] '*value1*'  
 Der Wert für den ersten Parameter, der in der Parameterzeichenfolge definiert ist. Bei diesem Wert kann es sich um eine Unicode-Konstante oder eine Unicode-Variable handeln. Für jeden Parameter, der in stmt enthalten ist, muss ein Parameterwert angegeben werden \@ . Die Werte sind nicht erforderlich, wenn die [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung oder der Batch in \@ stmt keine Parameter enthält.  
  
 *n*  
 Ein Platzhalter für die Werte zusätzlicher Parameter. Werte können nur Konstanten oder Variablen sein. Werte können keine komplexeren Ausdrücke sein, wie z. B. Funktionen oder Ausdrücke, die mithilfe von Operatoren erstellt werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder ungleich 0 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Gibt das Resultset aus der ersten SQL-Anweisung zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `ALTER ANY EXTERNAL DATA SOURCE`-Berechtigung.  
  
## <a name="remarks"></a>Hinweise  
 `sp_execute_remote`Parameter müssen in der spezifischen Reihenfolge eingegeben werden, wie im obigen Abschnitt Syntax beschrieben. Wenn die Parameter nicht in der vorgegebenen Reihenfolge eingegeben werden, wird eine Fehlermeldung ausgegeben.  
  
 `sp_execute_remote`hat das gleiche Verhalten wie [Execute &#40;Transact-SQL-&#41;](../../t-sql/language-elements/execute-transact-sql.md) in Bezug auf Batches und den Umfang der Namen. Die Transact-SQL-Anweisung oder der Batch im sp_execute_remote * \@ stmt* -Parameter wird erst kompiliert, wenn die sp_execute_remote-Anweisung ausgeführt wird.  
  
 `sp_execute_remote`Fügt dem Resultset mit dem Namen "$ShardName" eine zusätzliche Spalte hinzu, die den Namen der Remote Datenbank enthält, die die Zeile erzeugt hat.  
  
 `sp_execute_remote`kann ähnlich wie [sp_executesql &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md)verwendet werden.  
  
## <a name="examples"></a>Beispiele  
### <a name="simple-example"></a>Einfaches Beispiel  
 Im folgenden Beispiel wird eine einfache SELECT-Anweisung für eine Remote Datenbank erstellt und ausgeführt.  
  
```sql  
EXEC sp_execute_remote  
    N'MyExtSrc',  
    N'SELECT COUNT(w_id) AS Count_id FROM warehouse'   
```  
  
### <a name="example-with-multiple-parameters"></a>Beispiel mit mehreren Parametern  
Erstellen Sie Daten Bank weit gültige Anmelde Informationen in einer Benutzerdatenbank, und geben Sie die Administrator Anmelde Informationen für die Master-Datenbank an. Erstellen Sie eine externe Datenquelle, die auf die Master-Datenbank verweist, und geben Sie die Daten Bank weit gültigen Anmelde Informationen an. Im folgenden Beispiel in der Benutzerdatenbank wird die `sp_set_firewall_rule` Prozedur in der Master-Datenbank ausgeführt. Die `sp_set_firewall_rule` Prozedur erfordert 3 Parameter und erfordert, `@name` dass der Parameter Unicode ist.

```
EXEC sp_execute_remote @data_source_name  = N'PointToMaster', 
@stmt = N'sp_set_firewall_rule @name, @start_ip_address, @end_ip_address', 
@params = N'@name nvarchar(128), @start_ip_address varchar(50), @end_ip_address varchar(50)',
@name = N'TempFWRule', @start_ip_address = '0.0.0.2', @end_ip_address = '0.0.0.2';
```

## <a name="see-also"></a>Siehe auch:

[CREATE DATABASE SCOPED CREDENTIAL](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)  
[CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)  
    
