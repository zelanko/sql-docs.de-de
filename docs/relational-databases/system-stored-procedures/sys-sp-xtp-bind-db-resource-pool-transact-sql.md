---
description: sys.sp_xtp_bind_db_resource_pool (Transact-SQL)
title: sys. sp_xtp_bind_db_resource_pool (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_xtp_bind_db_resource_pool_TSQL
- sp_xtp_bind_db_resource_pool
- sys.sp_xtp_bind_db_resource_pool_TSQL
- sys.sp_xtp_bind_db_resource_pool
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xtp_bind_db_resource_pool
- sys.sp_xtp_bind_db_resource_pool
ms.assetid: c2a78073-626b-4159-996e-1808f6bfb6d2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 17b73b2acd00e7ea299c1d9e64bbac270485c678
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473467"
---
# <a name="syssp_xtp_bind_db_resource_pool-transact-sql"></a>sys.sp_xtp_bind_db_resource_pool (Transact-SQL)
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]

  Bindet die angegebene [!INCLUDE[hek_2](../../includes/hek-2-md.md)]-Datenbank an den angegebenen Ressourcenpool. Vor der Ausführung von `sys.sp_xtp_bind_db_resource_pool` müssen die Datenbank und der Ressourcenpool vorhanden sein.  
  
 Diese Systemprozedur erstellt eine Bindung zwischen dem durch resource_pool_name angegebenen Ressourcenkontrollenpool und der durch database_name angegebenen Datenbank. Es ist nicht erforderlich, dass die Datenbank zur Zeit der Bindung speicheroptimierte Objekte enthält. Falls keine speicheroptimierten Objekte vorhanden sind, wird kein Arbeitsspeicher aus dem Ressourcenpool belegt. Diese Bindung wird von der Ressourcenkontrolle verwendet, um den durch [!INCLUDE[hek_2](../../includes/hek-2-md.md)]-Zuordnungen belegten Arbeitsspeicher zu verwalten, wie nachfolgend beschrieben.  
  
 Wenn für eine bestimmte Datenbank bereits eine Bindung besteht, gibt die Prozedur einen Fehler zurück.  Eine Datenbank darf immer nur über eine aktive Bindung verfügen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
  
## <a name="syntax"></a>Syntax  
  
```sql  
sys.sp_xtp_bind_db_resource_pool 'database_name', 'resource_pool_name'  
```  
  
## <a name="arguments"></a>Argumente  
 database_name  
 Der Name einer vorhandenen [!INCLUDE[hek_2](../../includes/hek-2-md.md)] -aktivierten Datenbank.  
  
 resource_pool_name  
 Der Name eines vorhandenen Ressourcenpools.  
  
## <a name="messages"></a>Meldungen  
 Bei einem Fehler gibt `sp_xtp_bind_db_resource_pool` eine der folgenden Meldungen zurück.  
  
 **Die Datenbank ist nicht vorhanden.**  
 'Database_name' muss auf eine vorhandene Datenbank verweisen. Wenn keine Datenbank mit der angegebenen ID vorhanden ist, wird die folgende Meldung zurückgegeben:   
*Die Datenbank mit der ID% d ist nicht vorhanden.  Verwenden Sie eine gültige Datenbank-ID für diese Bindung.*  
  
```  
Msg 911, Level 16, State 18, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Database 'Hekaton_DB213' does not exist. Make sure that the name is entered correctly.  
```  
  
**Die Datenbank ist eine Systemdatenbank.**  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)]-Tabellen können nicht in Systemdatenbanken erstellt werden.  Daher ist es nicht zulässig, [!INCLUDE[hek_2](../../includes/hek-2-md.md)]-Arbeitsspeicher für eine derartige Datenbank zu binden.  Der folgende Fehler wird zurückgegeben:  
*Database_name% s verweist auf eine Systemdatenbank.  Ressourcenpools können nur an eine Benutzerdatenbank gebunden werden.*  
  
```  
Msg 41371, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Binding to a resource pool is not supported for system database 'master'. This operation can only be performed on a user database.  
```  
  
**Der Ressourcenpool ist nicht vorhanden.**  
 Der durch resource_pool_name angegebene Ressourcenpool muss vorhanden sein, bevor `sp_xtp_bind_db_resource_pool` ausgeführt wird.  Wenn kein Pool mit der angegebenen ID vorhanden ist, wird folgender Fehler zurückgegeben:  
*Der Ressourcen Pool '% s ' ist nicht vorhanden.  Geben Sie einen gültigen Namen für den Ressourcenpool ein.*  
  
```  
Msg 41370, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Resource pool 'Pool_Hekaton' does not exist or resource governor has not been reconfigured.  
```  
  
**'Pool_name' verweist auf einen reservierten Systempool.**  
 Die Poolnamen "Internal" und "Default" sind für System Pools reserviert.  Es ist nicht zulässig, eine Datenbank explizit an einen der beiden zu binden.  Bei Eingabe eines Systempoolnamens wird der folgende Fehler zurückgegeben:  
*Der Ressourcenpool "% s" ist ein Systemressourcen Pool.  System Ressourcenpools können mithilfe dieses Verfahrens nicht explizit an eine Datenbank gebunden werden.*  
  
```  
Msg 41373, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Database 'Hekaton_DB' cannot be explicitly bound to the resource pool 'internal'. A database can only be bound only to a user resource pool.  
```  
  
**Die Datenbank ist bereits an einen anderen Ressourcenpool gebunden.**  
 Eine Datenbank kann jeweils nur an einen Ressourcenpool gebunden werden. Datenbankbindungen an Ressourcenpools müssen explizit entfernt werden, bevor eine Bindung an einen anderen Pool erfolgen kann. Weitere Informationen finden Sie unter [sys. sp_xtp_unbind_db_resource_pool &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql.md).  
*Die% s-Datenbank ist bereits an den Ressourcenpool '% s ' gebunden.  Sie müssen die Bindung aufheben, bevor Sie eine neue Bindung erstellen können.*  
  
```  
Msg 41372, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 54  
Database 'Hekaton_DB' is currently bound to a resource pool. A database must be unbound before creating a new binding.  
```  
  
 Bei erfolgreicher Ausführung gibt `sp_xtp_bind_db_resource_pool` die folgende Meldung zurück.  
  
**Erfolgreiche Bindung**  
 Bei erfolgreicher Ausführung gibt die Funktion die folgende Erfolgsmeldung zurück, die in SQL ERRORLOG protokolliert wird.  
*Zwischen der Datenbank mit der ID %d und dem Ressourcenpool mit der ID %d wurde erfolgreich eine Ressourcenbindung erstellt.*  
  
## <a name="examples"></a>Beispiele  
A.  Im folgenden Codebeispiel wird die Hekaton_DB-Datenbank an den Pool_Hekaton-Ressourcenpool gebunden.  
  
```sql  
sys.sp_xtp_bind_db_resource_pool N'Hekaton_DB', N'Pool_Hekaton'  
```  
 
 Die Bindung wird wirksam, wenn die Datenbank das nächste Mal online geschaltet wird.  
 
 B. Erweitertes Beispiel für das obige Beispiel, das einige grundlegende Überprüfungen enthält.  Führen Sie Folgendes [!INCLUDE[tsql](../../includes/tsql-md.md)] in aus. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]\:
 
```sql
DECLARE @resourcePool sysname = N'Pool_Hekaton';
DECLARE @database sysname = N'Hekaton_DB';

-- Check whether resource pool exists
IF NOT EXISTS (
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = @resourcePool
    )
BEGIN
    SELECT N'Resource pool "' + @resourcePool + N'" does not exist or resource governor has not been reconfigured.';
END
-- Check whether database is already bound to a resource pool
ELSE IF EXISTS (
    SELECT p.name
    FROM sys.databases d
    JOIN sys.resource_governor_resource_pools p
    ON d.resource_pool_id = p.pool_id
    WHERE d.name = @database
    )
BEGIN
    SELECT N'Database "' + @database + N'" is currently bound to resource pool "' + @resourcePool  + N'". A database must be unbound before creating a new binding.';
END
-- Bind resource pool to database.
ELSE BEGIN
    EXEC sp_xtp_bind_db_resource_pool @database, @resourcePool; 
END 
``` 
  
## <a name="requirements"></a>Anforderungen  
  
-   Sowohl die durch `database_name` angegebene Datenbank als auch der durch `resource_pool_name` angegebene Ressourcenpool müssen vor dem Binden vorhanden sein.  
  
-   Erfordert die CONTROL SERVER-Berechtigung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Binden einer Datenbank mit speicheroptimierten Tabellen an einen Ressourcenpool](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [sys.sp_xtp_unbind_db_resource_pool &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql.md)  
  
  
