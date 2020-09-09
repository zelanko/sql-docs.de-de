---
description: sp_settriggerorder (Transact-SQL)
title: sp_settriggerorder (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_settriggerorder
- sp_settriggerorder_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_settriggerorder
ms.assetid: 8b75c906-7315-486c-bc59-293ef12078e8
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: da6cb44163370332968c32324086b27f673b3f69
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543057"
---
# <a name="sp_settriggerorder-transact-sql"></a>sp_settriggerorder (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt die AFTER-Trigger an, die zuerst oder zuletzt ausgelöst werden. Die AFTER-Trigger, die zwischen dem ersten und letzten Trigger ausgelöst werden, werden in einer nicht definierten Reihenfolge ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_settriggerorder [ @triggername = ] '[ triggerschema. ] triggername'   
    , [ @order = ] 'value'   
    , [ @stmttype = ] 'statement_type'   
    [ , [ @namespace = ] { 'DATABASE' | 'SERVER' | NULL } ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @triggername = ] '[ _triggerschema.] _triggername'` Der Name des Auslösers und des Schemas, zu dem es gehört, falls zutreffend, dessen Reihenfolge festgelegt oder geändert werden soll. [_triggerschema_**.**] *Triggername* ist vom Datentyp **vom Datentyp sysname**. Wenn der Name keinem Trigger entspricht oder wenn der Name dem INSTEAD OF-Trigger entspricht, gibt die Prozedur einen Fehler zurück. *triggerschema* kann nicht für DDL-oder LOGON-Trigger angegeben werden.  
  
`[ @order = ] 'value'` Die Einstellung für die neue Reihenfolge des Auslösers. der *Wert* ist " **varchar (10)** ", und es kann sich um einen der folgenden Werte handeln:  
  
> [!IMPORTANT]  
>  Der **erste** und der **Letzte** Trigger müssen zwei unterschiedliche Trigger sein.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**First**|Trigger wird zuerst ausgelöst|  
|**Last**|Trigger wird zuletzt ausgelöst|  
|**Keine**|Trigger wird in nicht definierter Reihenfolge ausgelöst|  
  
`[ @stmttype = ] 'statement_type'` Gibt die SQL-Anweisung an, die den-Triggern auslöst. *statement_type* ist vom Datentyp **varchar (50)** und kann Einfüge-, Aktualisierungs-, Lösch-, Anmelde-oder beliebige [!INCLUDE[tsql](../../includes/tsql-md.md)] in [DDL-Ereignissen](../../relational-databases/triggers/ddl-events.md)aufgeführte Anweisungs Ereignisse sein Ereignisgruppen können nicht angegeben werden.  
  
 Ein-Auslösers kann als **erster** oder **Letzter** -für einen Anweisungstyp festgelegt werden, nachdem dieser als ein-auslösertyp definiert wurde. Beispielsweise kann der **TR1** Auslösewert TR1 **zuerst** für INSERT in der Tabelle **T1** festgelegt werden, wenn **TR1** als INSERT-Vorgang definiert ist. [!INCLUDE[ssDE](../../includes/ssde-md.md)]Gibt einen Fehler zurück, wenn **TR1**, der nur als INSERT-Vorgang definiert wurde, als **First**-oder **Last**-Wert für eine Update-Anweisung festgelegt wird. Weitere Informationen finden Sie im Abschnitt "Hinweise".  
  
 ** \@ Namespace =** { **' Database '**  |  **' Server '** | Normal  
 Wenn *Triggername* ein DDL-Trigger ist, gibt der ** \@ Namespace** an, ob *Triggername* mit dem Daten Bankbereich oder dem Serverbereich erstellt wurde. Wenn *Triggername* ein LOGON-Trigger ist, muss der Server angegeben werden. Weitere Informationen zum DDL-Triggerbereich finden Sie unter [DDL-Trigger](../../relational-databases/triggers/ddl-triggers.md). Wenn nicht angegeben, oder wenn NULL angegeben wird, ist *Triggername* ein DML-Trigger.  
  
* Server gilt für: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher.
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="dml-triggers"></a>DML-Trigger  
 Für jede Anweisung in einer einzelnen Tabelle können nur ein **erster** und ein **Letzter** Auslösung vorhanden sein.  
  
 Wenn für die Tabelle, die Datenbank oder den Server bereits ein neuer-Auslösung definiert ist, können **Sie für dieselbe** *statement_type*keinen neuen- **Auslösers** für dieselbe Tabelle, Datenbank oder denselben Server festlegen. Diese Einschränkung wendet auch die **letzten** Trigger an.  
  
 Die Replikation generiert automatisch einen ersten Trigger für alle Tabellen, die in einem Abonnement mit sofortigem Update oder verzögertem Update über eine Warteschlange enthalten sind. Für die Replikation gilt, dass ihr Trigger der erste Trigger sein muss. Die Replikation meldet einen Fehler, wenn Sie versuchen, eine Tabelle, die einen ersten Trigger aufweist, in ein Abonnement mit sofortigem Update bzw. verzögertem Update über eine Warteschlange einzufügen. Wenn Sie versuchen, einen Trigger zum ersten Trigger zu erklären, nachdem eine Tabelle in ein Abonnement aufgenommen wurde, gibt **sp_settriggerorder** einen Fehler zurück. Wenn Sie Alter-Triggern für den Replikations **-oder den** Replikations triggerbefehl verwenden, oder wenn Sie **sp_settriggerorder** verwenden, um den Replikations **-und den** Replikations Triggern in einen  
  
## <a name="ddl-triggers"></a>DDL-Trigger  
 Wenn ein DDL-Trigger mit Daten Bankbereich und ein DDL-Trigger mit Serverbereich für dasselbe Ereignis vorhanden sind, können Sie angeben, dass beide Trigger ein **erster** Trigger oder ein **Letzter** Trigger sind. Trigger mit einem Serverbereich werden jedoch immer zuerst ausgelöst. Im Allgemeinen ist die Reihenfolge der Auslösung von DDL-Triggern für das gleiche Ereignis Folgende:  
  
1.  Der **zuerst**markierte Server auf Serverebene.  
  
2.  Weitere Trigger auf Serverebene  
  
3.  Der **zuletzt**markierte Server auf Serverebene.  
  
4.  Der **zuerst**markierte auf Datenbankebene.  
  
5.  Weitere Trigger auf Datenbankebene  
  
6.  Der **zuletzt**markierte auf Datenbankebene.  
  
## <a name="general-trigger-considerations"></a>Allgemeine Überlegungen zu Triggern  
 Wenn eine Alter-auslöseranweisung den ersten oder letzten-Befehl ändert, wird das **erste** oder **Letzte** Attribut, das ursprünglich für den-Befehl festgelegt wurde, gelöscht, und der Wert wird durch **None**ersetzt. Der Bestellwert muss mithilfe **sp_settriggerorder**zurückgesetzt werden.  
  
 Wenn derselbe-Befehl für mehr als einen Anweisungstyp als erste oder Letzte Reihenfolge festgelegt werden muss, muss **sp_settriggerorder** für jeden Anweisungs Typ ausgeführt werden. Außerdem muss der Trigger zuerst für einen Anweisungstyp definiert werden, bevor er als **erster** oder **Letzter** Trigger für diesen Anweisungstyp gekennzeichnet werden kann.  
  
## <a name="permissions"></a>Berechtigungen  
 Um die Reihenfolge eines DDL-Triggers mit Serverbereich (erstellt ON ALL SERVER) oder eines LOGON-Triggers festzulegen, ist die CONTROL SERVER-Berechtigung auf dem Server erforderlich.  
  
 Um die Reihenfolge eines DDL-Triggers mit Datenbankbereich (erstellt ON DATABASE) festzulegen, benötigen Sie die Berechtigung ALTER ANY DATABASE DDL TRIGGER.  
  
 Um die Reihenfolge eines DML-Triggers festzulegen, benötigen Sie die ALTER-Berechtigung für die Tabelle oder Sicht, in der der Trigger definiert wurde.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-setting-the-firing-order-for-a-dml-trigger"></a>A. Festlegen der Auslösungsreihenfolge für einen DML-Trigger  
 Im folgenden Beispiel wird angegeben, dass Trigger `uSalesOrderHeader` der erste Trigger ist, der nach Abschluss eines `UPDATE`-Vorgangs in der `Sales.SalesOrderHeader`-Tabelle ausgelöst wird.  
  
```  
USE AdventureWorks2012;  
GO  
sp_settriggerorder @triggername= 'Sales.uSalesOrderHeader', @order='First', @stmttype = 'UPDATE';  
```  
  
### <a name="b-setting-the-firing-order-for-a-ddl-trigger"></a>B. Festlegen der Auslösungsreihenfolge für einen DDL-Trigger  
 Im folgenden Beispiel wird angegeben, dass Trigger `ddlDatabaseTriggerLog` der erste Trigger ist, der nach einem `ALTER_TABLE`-Ereignis in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank ausgelöst wird.  
  
```  
USE AdventureWorks2012;  
GO  
sp_settriggerorder @triggername= 'ddlDatabaseTriggerLog', @order='First', @stmttype = 'ALTER_TABLE', @namespace = 'DATABASE';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)  
  
  
