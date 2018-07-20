---
title: Sp_execute_remote (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/01/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sp_execute_remote
- sp_execute_remote_TSQL
helpviewer_keywords:
- remote execution
- queries, remote execution
ms.assetid: ca89aa4c-c4c1-4c46-8515-a6754667b3e5
caps.latest.revision: 17
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 319eee940c5f5d90d6cfe9442c66f506670c26a0
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082572"
---
# <a name="spexecuteremote-azure-sql-database"></a>Sp_execute_remote (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Führt eine [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung für eine einzelne Azure SQL-Remotedatenbank oder eine Gruppe von Datenbanken, die als Shards in einem Schema mit horizontaler Partitionierung dient.  
  
 Die gespeicherte Prozedur ist Teil der Features für elastische Abfragen.  Finden Sie unter [Azure SQL-Datenbank Übersicht über elastische datenbankenabfragen](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/) und [Elastischer Datenbankabfragen für Sharding (horizontales partitionieren)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-horizontal-partitioning/).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 [ \@Data_source_name =] *Datasourcename*  
 Gibt die externe Datenquelle, in dem die Anweisung ausgeführt wird. Finden Sie unter [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md). Die externe Datenquelle kann vom Typ "RDBMS" oder "SHARD_MAP_MANAGER" sein.  
  
 [ \@Stmt =] *Anweisung*  
 Ist eine Unicodezeichenfolge mit einem [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung oder einen Batch. \@Stmt muss es sich um eine Unicodekonstante oder eine Unicode-Variable sein. Komplexere Unicodeausdrücke, wie z. B. die Verkettung von zwei Zeichenfolgen mit dem +-Operator, sind nicht zulässig. Zeichenkonstanten sind nicht zulässig. Wenn eine Unicode-Konstante angegeben wird, muss er mit Präfix ein **N**. Beispielsweise die Unicode-Konstante **N 'Sp_who'** gültig ist, die Zeichenkonstante **'Sp_who'** nicht. Die Länge der Zeichenfolge wird nur durch den verfügbaren Arbeitsspeicher des Datenbankservers begrenzt. Auf 64-Bit-Servern, die Größe der Zeichenfolge beträgt 2 GB sind, die maximale Größe der **nvarchar(max)**.  
  
> [!NOTE]  
>  \@Stmt kann Parameter aufweisen, die die gleiche Form wie ein Variablenname aufweisen, z. B. enthalten: `N'SELECT * FROM HumanResources.Employee WHERE EmployeeID = @IDParameter'`  
  
 Für jeden Parameter in \@Stmt ist ein entsprechender Eintrag muss in beiden die \@Definitionsliste für Params-Parameter und den Parameter Werteliste.  
  
 [ \@Params =] N'\@*Parameter_name ** Data_type* [,... *n* ] "  
 Eine Zeichenfolge, die die Definitionen aller Parameter enthält, die eingebetteten \@Stmt. Die Zeichenfolge muss eine Unicode-Konstante oder eine Unicode-Variable sein. Jede Parameterdefinition besteht aus einem Parameternamen und einem Datentyp. *n* ist ein Platzhalter, der zusätzliche Parameterdefinitionen. Jeder Parameter, die im angegebenen \@Stmtmust in definiert werden \@Params. Wenn die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung oder der Batch in \@Stmt enthält keine Parameter \@"Params" ist nicht erforderlich. Der Standardwert für diesen Parameter ist NULL.  
  
 [ \@param1 =] '*value1*"  
 Der Wert für den ersten Parameter, der in der Parameterzeichenfolge definiert ist. Bei diesem Wert kann es sich um eine Unicode-Konstante oder eine Unicode-Variable handeln. Es muss ein Parameterwert angegeben wird, für jeden Parameter in \@Stmt. Die Werte sind nicht erforderlich, wenn die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung oder der Batch in \@Stmt hat keine Parameter.  
  
 *n*  
 Ein Platzhalter für die Werte zusätzlicher Parameter. Werte können nur Konstanten oder Variablen sein. Werte können keine komplexeren Ausdrücke sein, wie z. B. Funktionen oder Ausdrücke, die mithilfe von Operatoren erstellt werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder ungleich 0 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Gibt das Resultset der ersten SQL-Anweisung zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `ALTER ANY EXTERNAL DATA SOURCE`-Berechtigung.  
  
## <a name="remarks"></a>Hinweise  
 `sp_execute_remote` Parameter müssen in der Reihenfolge eingegeben werden, wie im vorherigen Syntaxabschnitt beschrieben. Wenn die Parameter nicht in der vorgegebenen Reihenfolge eingegeben werden, wird eine Fehlermeldung ausgegeben.  
  
 `sp_execute_remote` weist das gleiche Verhalten wie [EXECUTE &#40;Transact-SQL&#41; ](../../t-sql/language-elements/execute-transact-sql.md) im Hinblick auf Batches und der Gültigkeitsbereich von Namen. Die Transact-SQL-Anweisung oder der Batch in die Sp_execute_remote  *\@Stmt* Parameter wird nicht kompiliert werden, bis die Sp_execute_remote-Anweisung ausgeführt wird.  
  
 `sp_execute_remote` das Resultset mit dem Namen "$ShardName" mit dem Namen der Remotedatenbank, die die Zeile erstellt hinzugefügt eine zusätzliche Spalte.  
  
 `sp_execute_remote` kann verwendet werden, ähnlich wie [Sp_executesql &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md).  
  
## <a name="examples"></a>Beispiele  
### <a name="simple-example"></a>Einfaches Beispiel  
 Das folgende Beispiel erstellt und führt eine einfache SELECT-Anweisung in einer Remotedatenbank.  
  
```sql  
EXEC sp_execute_remote  
    N'MyExtSrc',  
    N'SELECT COUNT(w_id) AS Count_id FROM warehouse'   
```  
  
### <a name="example-with-multiple-parameters"></a>Beispiel mit mehreren Parametern  
Erstellen Sie datenbankweit gültige Anmeldeinformationen in einer Benutzerdatenbank, die Anmeldeinformationen des Administrators für die master-Datenbank angeben. Erstellen einer externen Datenquelle, auf die master-Datenbank verweist, und geben Sie die datenbankweit gültigen Anmeldeinformationen an. Dann Folgendes Beispiel in der Benutzerdatenbank und führt die `sp_set_firewall_rule` Prozedur in der master-Datenbank. Die `sp_set_firewall_rule` Verfahren erfordert 3 Parameter, und die `@name` Parameter Unicode.

```
EXEC sp_execute_remote @data_source_name  = N'PointToMaster', 
@stmt = N'sp_set_firewall_rule @name, @start_ip_address, @end_ip_address', 
@params = N'@name nvarchar(128), @start_ip_address varchar(50), @end_ip_address varchar(50)',
@name = N'TempFWRule', @start_ip_address = '0.0.0.2', @end_ip_address = '0.0.0.2';
```

## <a name="see-also"></a>Siehe auch:

[ERSTELLEN SIE DATENBANKBEZOGENE ANMELDEINFORMATIONEN](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)  
[CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)  
    
