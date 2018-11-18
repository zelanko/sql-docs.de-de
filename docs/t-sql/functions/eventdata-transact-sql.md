---
title: EVENTDATA (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- EVENTDATA
- fn_event_data
- EVENTDATA_TSQL
- fn_event_data_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server instance event data [SQL Server]
- event notifications [SQL Server], event status
- events [SQL Server], status infromation
- EVENTDATA function
- status information [SQL Server], events
- DDL triggers, returning event data
ms.assetid: 03a80e63-6f37-4b49-bf13-dc35cfe46c44
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 953a4d79d128d2295b5365653f0f7b62647f6069
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51701328"
---
# <a name="eventdata-transact-sql"></a>EVENTDATA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Diese Funktion gibt Informationen zu Server- oder Datenbankereignissen zurück. Beim Auslösen einer Ereignisbenachrichtigung und, wenn der angegebene Service Broker die Ergebnisse empfängt, wird `EVENTDATA` aufgerufen. Ein DDL- oder LOGON-Trigger unterstützt auch die interne Verwendung von `EVENTDATA`.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
EVENTDATA( )  
```  
  
## <a name="remarks"></a>Remarks  
`EVENTDATA` gibt nur Daten zurück, wenn ein direkter Verweis innerhalb eines DDL- oder LOGON-Triggers vorliegt. `EVENTDATA` gibt beim Aufruf durch andere Routinen NULL zurück, selbst wenn diese Routinen durch einen DDL- oder LOGON-Trigger aufgerufen werden.
  
Von `EVENTDATA` zurückgegebene Daten sind ungültig, nachdem eine Transaktion

+ `EVENTDATA` explizit aufruft
+ `EVENTDATA` implizit aufruft
+ einen Commit ausführt
+ durch ein Rollback rückgängig gemacht wurde  
  
> [!CAUTION]  
>  `EVENTDATA` gibt XML-Daten zurück, die als Unicode an den Client gesendet werden; dabei werden 2 Bytes für jedes Zeichen verwendet. `EVENTDATA` gibt XML-Daten zurück, die diese Unicode-Codeendpunkte darstellen können:  
>   
>  `0x0009`  
>   
>  `0x000A`  
>   
>  `0x000D`  
>   
>  `>= 0x0020 && <= 0xD7FF`  
>   
>  `>= 0xE000 && <= 0xFFFD`  
>   
>  In XML können und werden einige Zeichen, die in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Bezeichnern und -Daten vorkommen können, nicht ausgedrückt bzw. zugelassen. Zeichen oder Daten mit Codeelementen, die in der vorhergehenden Liste nicht enthalten sind, weisen ein Fragezeichen auf (?).  
  
Kennwörter werden nicht angezeigt, wenn `CREATE LOGIN`- oder `ALTER LOGIN`-Anweisungen ausgeführt werden. Dies dient dem Schutz der Anmeldeinformationen.  
  
## <a name="schemas-returned"></a>Zurückgegebene Schemas  
EVENTDATA gibt einen Wert vom Datentyp **xml** zurück. Standardmäßig wird die Schemadefinition für alle Ereignisse in diesem Verzeichnis installiert: [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd.  
  
Auf der Webseite [Microsoft SQL Server: XML-Schemas](https://go.microsoft.com/fwlink/?LinkID=31850) ist ebenfalls das Ereignisschema veröffentlicht.  
  
Um das Schema für ein besonderes Ereignis zu extrahieren, durchsuchen Sie das Schema nach dem komplexen Typ `EVENT_INSTANCE_<event_type>`. Zum Beispiel können Sie das Schema für das `DROP_TABLE`-Ereignis extrahieren, indem Sie das Schema nach `EVENT_INSTANCE_DROP_TABLE` durchsuchen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-querying-event-data-in-a-ddl-trigger"></a>A. Abfragen von Ereignisdaten in einem DDL-Trigger  
In diesem Beispiel wird ein DDL-Trigger erstellt, der die Erstellung neuer Datenbanktabellen verhindert. Durch die Verwendung von XQuery für die von `EVENTDATA` generierten XML-Daten wird die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung erfasst, die den Trigger auslöst. Weitere Informationen finden Sie unter [XQuery-Sprachreferenz &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md).  
  
> [!NOTE]  
>  Wenn Sie mithilfe von **Ergebnisse in Raster** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] das `<TSQLCommand>`-Element abfragen, werden keine Zeilenumbrüche im Befehlstext angezeigt. Verwenden Sie stattdessen **Ergebnisse in Text**.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER safety   
ON DATABASE   
FOR CREATE_TABLE   
AS   
    PRINT 'CREATE TABLE Issued.'  
    SELECT EVENTDATA().value  
        ('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
   RAISERROR ('New tables cannot be created in this database.', 16, 1)   
   ROLLBACK  
;  
GO  
--Test the trigger.  
CREATE TABLE NewTable (Column1 int);  
GO  
--Drop the trigger.  
DROP TRIGGER safety  
ON DATABASE;  
GO  
```  
  
> [!NOTE]  
>  Zum Zurückgeben von Ereignisdaten verwenden Sie die XQuery-Methode **value()** anstelle der Methode **query()**. Bei der **query()**-Methode werden XML-Daten und durch das kaufmännische Und-Zeichen geschützte CR/LF-Instanzen in der Ausgabe zurückgegeben, während bei der **value()**-Methode CR/LF-Instanzen zurückgegeben werden, die in der Ausgabe nicht sichtbar sind.  
  
### <a name="b-creating-a-log-table-with-event-data-in-a-ddl-trigger"></a>B. Erstellen einer Protokolltabelle mit Ereignisdaten in einem DDL-Trigger  
In diesem Beispiel wird eine Tabelle zum Speichern von Informationen zu Ereignissen auf allen Datenbankebenen erstellt und die Tabelle mit einem DDL-Trigger aufgefüllt. Durch die Verwendung von XQuery für die von `EVENTDATA` generierten XML-Daten wird der Ereignistyp und die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung erfasst.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE ddl_log (PostTime datetime, DB_User nvarchar(100), Event nvarchar(100), TSQL nvarchar(2000));  
GO  
CREATE TRIGGER log   
ON DATABASE   
FOR DDL_DATABASE_LEVEL_EVENTS   
AS  
DECLARE @data XML  
SET @data = EVENTDATA()  
INSERT ddl_log   
   (PostTime, DB_User, Event, TSQL)   
   VALUES   
   (GETDATE(),   
   CONVERT(nvarchar(100), CURRENT_USER),   
   @data.value('(/EVENT_INSTANCE/EventType)[1]', 'nvarchar(100)'),   
   @data.value('(/EVENT_INSTANCE/TSQLCommand)[1]', 'nvarchar(2000)') ) ;  
GO  
--Test the trigger.  
CREATE TABLE TestTable (a int);  
DROP TABLE TestTable ;  
GO  
SELECT * FROM ddl_log ;  
GO  
--Drop the trigger.  
DROP TRIGGER log  
ON DATABASE;  
GO  
--Drop table ddl_log.  
DROP TABLE ddl_log;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwenden der EVENTDATA-Funktion](../../relational-databases/triggers/use-the-eventdata-function.md)   
 [DDL-Trigger](../../relational-databases/triggers/ddl-triggers.md)   
 [Ereignisbenachrichtigungen](../../relational-databases/service-broker/event-notifications.md)   
 [Logon-Trigger](../../relational-databases/triggers/logon-triggers.md)  
  
  
