---
title: Löschen oder Deaktivieren von DML-Triggern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, disabling
- removing DML triggers
- disabling DML triggers
- dropping DML triggers
- deleting DML triggers
- DML triggers, removing
ms.assetid: 0f97f953-33c5-4b26-afeb-db2a26ce38b4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1195d1b15ed845728cd254032fc7187b3f355f8f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68196531"
---
# <a name="delete-or-disable-dml-triggers"></a>Löschen oder Deaktivieren von DML-Triggern
  In diesem Thema wird beschrieben, wie Sie einen DML-Trigger in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]löschen oder deaktivieren.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Empfehlungen](#Recommendations)  
  
     [Sicherheit](#Security)  
  
-   **Löschen oder Deaktivieren eines DML-Triggers mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Wenn ein Trigger gelöscht wird, wird er aus der aktuellen Datenbank entfernt. Dies hat jedoch keine Auswirkung auf die Tabelle und Daten, auf denen der Trigger basiert. Durch das Löschen einer Tabelle werden automatisch alle Trigger für die Tabelle gelöscht.  
  
-   Ein Trigger wird standardmäßig aktiviert, wenn er erstellt wird.  
  
-   Durch das Deaktivieren wird ein Trigger nicht gelöscht. Der Trigger ist weiterhin als Objekt in der aktuellen Datenbank vorhanden. Ein deaktivierter Trigger wird jedoch nicht ausgelöst, wenn eine INSERT-, UPDATE- oder DELETE-Anweisung ausgeführt wird, für die er programmiert war. Deaktivierte Trigger können erneut aktiviert werden. Durch das Aktivieren eines Triggers wird dieser nicht neu erstellt. Der Trigger wird auf die gleiche Weise ausgelöst wie bei seiner ursprünglichen Erstellung.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Zum Löschen eines DML-Triggers ist die ALTER-Berechtigung für die Tabelle oder Sicht erforderlich, in der der Trigger definiert ist.  
  
 Zum Deaktivieren oder Aktivieren eines DML-Triggers muss ein Benutzer mindestens die ALTER-Berechtigung für die Tabelle oder Sicht besitzen, für die der Trigger erstellt wurde.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-delete-a-dml-trigger"></a>So löschen Sie einen DML-Trigger  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie die gewünschte Datenbank, **Tabellen**und dann die Tabelle, die den zu löschenden Trigger enthält.  
  
3.  Erweitern Sie **Trigger**, klicken Sie mit der rechten Maustaste auf den zu löschenden Trigger, und klicken Sie anschließend auf **Löschen**.  
  
4.  Überprüfen Sie im Dialogfeld **Objekt löschen** , ob der richtige Trigger ausgewählt ist, und klicken Sie dann auf **OK**.  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a>So deaktivieren und aktivieren Sie einen DML-Trigger  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie die gewünschte Datenbank, **Tabellen**und dann die Tabelle, die den zu deaktivierenden Trigger enthält.  
  
3.  Erweitern Sie **Trigger**, klicken Sie mit der rechten Maustaste auf den zu deaktivierenden Trigger, und klicken Sie anschließend auf **Deaktivieren**.  
  
4.  Um den Trigger zu aktivieren, klicken Sie auf **Aktivieren**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-a-dml-trigger"></a>So löschen Sie einen DML-Trigger  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie die folgenden Beispiele, und fügen Sie sie in das Abfrage-Fenster ein. Führen Sie die [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) -Anweisung aus, um den `Sales.bonus_reminder` -Trigger zu erstellen. Führen Sie die [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) -Anweisung aus, um den Trigger zu löschen.  
  
```sql  
--Create the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```sql  
--Delete the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('Sales.bonus_reminder', 'TR') IS NOT NULL  
   DROP TRIGGER Sales.bonus_reminder;  
GO  
  
```  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a>So deaktivieren und aktivieren Sie einen DML-Trigger  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie die folgenden Beispiele, und fügen Sie sie in das Abfrage-Fenster ein. Führen Sie die [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) -Anweisung aus, um den `Sales.bonus_reminder` -Trigger zu erstellen. Führen Sie die [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) - und [die ENABLE TRIGGER](/sql/t-sql/statements/enable-trigger-transact-sql) -Anweisungen aus, um den Trigger zu deaktivieren und zu aktivieren.  
  
```sql  
--Create the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```sql  
--Disable the trigger.  
USE AdventureWorks2012;  
GO  
DISABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
  
```  
  
```sql  
--Enable the trigger.  
USE AdventureWorks2012;  
GO  
ENABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql)   
 [ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql)   
 [DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql)   
 [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql)   
 [Abrufen von Informationen zu DML-Triggern](dml-triggers.md)   
 [sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql)   
 [sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql)   
 [sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql)   
 [sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql)   
 [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)   
 [sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)   
 [sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)   
 [sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql)   
 [sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql)   
 [sys.server_assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
  
