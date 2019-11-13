---
title: sp_server_diagnostics (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_server_diagnostics
- sp_server_diagnostics_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_server_diagnostics
ms.assetid: 62658017-d089-459c-9492-c51e28f60efe
author: stevestein
ms.author: sstein
ms.openlocfilehash: d150d9b027b9a2c4d309ca2055722bb47ba092a4
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "73982118"
---
# <a name="sp_server_diagnostics-transact-sql"></a>sp_server_diagnostics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Erfasst Diagnosedaten und Zustandsinformationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], um potenzielle Fehler zu erkennen. Die Prozedur wird im Wiederholungsmodus ausgeführt und sendet regelmäßig Ergebnisse. Sie kann über eine reguläre oder eine DAC-Verbindung aufgerufen werden.  
  
**Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher).  
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlink (Symbol)") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_server_diagnostics [@repeat_interval =] 'repeat_interval_in_seconds'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @repeat_interval = ] 'repeat_interval_in_seconds'` gibt das Zeitintervall an, in dem die gespeicherte Prozedur wiederholt ausgeführt wird, um Integritäts Informationen zu senden.  
  
 *repeat_interval_in_seconds* ist vom Datentyp **int** und hat den Standardwert 0. Die gültigen Parameterwerte sind 0 sowie alle Werte größer oder gleich 5. Die gespeicherte Prozedur muss mindestens 5 Sekunden lang ausgeführt werden, um vollständige Daten zurückzugeben. Der minimale Wert für die Ausführung der gespeicherten Prozedur im Wiederholungsmodus beträgt 5 Sekunden.  
  
 Wenn dieser Parameter nicht angegeben ist oder der angegebene Wert 0 beträgt, gibt die gespeicherte Prozedur einmal Daten zurück und wird dann beendet.  
  
 Wenn der angegebene Wert kleiner als der minimale Wert ist, wird ein Fehler ausgelöst und kein Wert zurückgegeben.  
  
 Wenn der angegebene Wert größer oder gleich 5 ist, wird die gespeicherte Prozedur wiederholt ausgeführt, um den Zustand zurückzugeben, bis sie manuell abgebrochen wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
**sp_server_diagnostics** gibt die folgenden Informationen zurück.  
  
|Spalte|Datentyp|und Beschreibung|  
|------------|---------------|-----------------|  
|**creation_time**|**datetime**|Gibt den Zeitstempel der Zeilenerstellung an. Jede Zeile in einem einzelnen Rowset weist denselben Zeitstempel auf.|  
|**component_type**|**sysname**|Gibt an, ob die Zeile Informationen für die Komponente der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanzebene oder für eine Always on Verfügbarkeits Gruppe enthält:<br /><br /> Instanz<br /><br /> Always on: availabilitygroup|  
|**component_name**|**sysname**|Gibt den Namen der Komponente oder den Namen der Verfügbarkeitsgruppe an:<br /><br /> System<br /><br /> resource<br /><br /> query_processing<br /><br /> io_subsystem<br /><br /> -Ereignisse<br /><br /> *\<Name der Verfügbarkeits Gruppe >*|  
|**state**|**int**|Gibt den Integritätsstatus der Komponente an:<br /><br /> 0<br /><br /> 1<br /><br /> 2<br /><br /> 3|  
|**state_desc**|**sysname**|Beschreibt die Zustandsspalte. Folgende Beschreibungen entsprechen den Werten in der Statusspalte:<br /><br /> 0: unbekannt<br /><br /> 1: Bereinigen<br /><br /> 2: Warnung<br /><br /> 3: Fehler|  
|**data**|**varchar (max)**|Gibt Daten an, die für die Komponente spezifisch sind.|  
  
 Im Folgenden finden Sie die Beschreibungen der fünf Komponenten:  
  
-   **System**: sammelt Daten aus einer Systemperspektive für Spinlocks, schwerwiegende Verarbeitungsbedingungen, nicht zustellenden Aufgaben, Seiten Fehler und CPU-Auslastung. Diese Informationen ergeben eine allgemeine Empfehlung zum Integritätsstatus.  
  
-   **Ressource**: sammelt Daten aus einer ressourcenperspektive für physischen und virtuellen Arbeitsspeicher, Pufferpools, Seiten, Cache und andere Speicher Objekte. Diese Informationen erzeugen eine allgemeine Integritäts Zustands Empfehlung.  
  
-   **query_processing**: sammelt Daten aus einer Abfrage Verarbeitungs Perspektive für Arbeitsthreads, Tasks, warte Typen, CPU-intensive Sitzungen und blockierende Tasks. Diese Informationen erzeugen eine allgemeine Integritäts Zustands Empfehlung.  
  
-   **io_subsystem**: sammelt Daten über e/a. Zusätzlich zu den Diagnosedaten erzeugt diese Komponente nur für ein EA-Subsystem einen komplett fehlerfreien oder einen Warnzustand.  
  
-   **Ereignisse**: sammelt Daten und über die gespeicherte Prozedur auf den vom Server aufgezeichneten Fehlern und Ereignissen, einschließlich Details zu Ringpuffer Ausnahmen, Ringpuffer Ereignissen zum Speicher Broker, nicht genügend Arbeitsspeicher, Scheduler-Monitor, Pufferpool, Spinlocks, Sicherheit und Konnektivität. Ereignisse zeigen als Status immer 0 an.  
  
-   **\<Name der Verfügbarkeits Gruppe >** : sammelt Daten für die angegebene Verfügbarkeits Gruppe (wenn component_type = "Always on: availabilitygroup").  
  
## <a name="remarks"></a>Remarks  
Die Komponenten system, resource und query_processing werden zur Fehlererkennung aus Fehlerperspektive genutzt, während die Komponenten io_subsystem und events nur zu Diagnosezwecken genutzt werden.  
  
In der folgenden Tabelle sind die Komponenten den jeweils zugeordneten Integritätszuständen zugeordnet.  
  
|-Komponenten|Clean (1)|Warning (2)|Error (3)|Unknowns (0)|  
|----------------|-----------------|-------------------|-----------------|--------------------|  
|System|x|x|x||  
|resource|x|x|x||  
|query_processing|x|x|x||  
|io_subsystem|x|x|||  
|-Ereignisse||||x|  
  
Das (x) in jeder Zeile steht für gültige Zustände für die Komponente. Im Beispiel wird io_subsystem als fehlerfrei oder Warnung angezeigt. Der Fehlerstatus wird nicht angezeigt.  
 
> [!NOTE]
> Die Ausführung sp_server_diagnostics internen Prozedur wird in einem präemptiven Thread mit hoher Priorität implementiert.
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
Es ist empfehlenswert, die Zustandsinformationen in erweiterten Sitzungen aufzuzeichnen und in einer Datei zu speichern, die sich außerhalb von SQL Server befindet. In diesem Fall können Sie auch bei einem Fehler auf diese zugreifen. Im folgenden Beispiel wird die Ausgabe einer Ereignissitzung in einer Datei gespeichert:  
```sql  
CREATE EVENT SESSION [diag]  
ON SERVER  
           ADD EVENT [sp_server_diagnostics_component_result] (set collect_data=1)  
           ADD TARGET [asynchronous_file_target] (set filename='c:\temp\diag.xel');  
GO  
ALTER EVENT SESSION [diag]  
      ON SERVER STATE = start;  
GO  
```  
  
In der unten angegebenen Beispielabfrage wird die Protokolldatei der erweiterten Sitzung gelesen:  
```sql  
SELECT  
    xml_data.value('(/event/@name)[1]','varchar(max)') AS Name  
  , xml_data.value('(/event/@package)[1]', 'varchar(max)') AS Package  
  , xml_data.value('(/event/@timestamp)[1]', 'datetime') AS 'Time'  
  , xml_data.value('(/event/data[@name=''component_type'']/value)[1]','sysname') AS Sysname  
  , xml_data.value('(/event/data[@name=''component_name'']/value)[1]','sysname') AS Component  
  , xml_data.value('(/event/data[@name=''state'']/value)[1]','int') AS State  
  , xml_data.value('(/event/data[@name=''state_desc'']/value)[1]','sysname') AS State_desc  
  , xml_data.query('(/event/data[@name="data"]/value/*)') AS Data  
FROM   
(  
      SELECT  
                        object_name as event  
                        ,CONVERT(xml, event_data) as xml_data  
       FROM    
      sys.fn_xe_file_target_read_file('C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Log\*.xel', NULL, NULL, NULL)  
)   
AS XEventData  
ORDER BY time;  
```  
  
Im folgenden Beispiel wird die Ausgabe von sp_server_diagnostics an eine Tabelle in einem anderen als dem Wiederholungsmodus aufgezeichnet:  
```sql  
CREATE TABLE SpServerDiagnosticsResult  
(  
      create_time DateTime,  
      component_type sysname,  
      component_name sysname,  
      state int,  
      state_desc sysname,  
      data xml  
);  
INSERT INTO SpServerDiagnosticsResult  
EXEC sp_server_diagnostics; 
```  

Die nachstehende Beispielabfrage liest die Zusammenfassungsausgabe aus der Tabelle:  
```sql  
SELECT create_time,
       component_name,
       state_desc 
FROM SpServerDiagnosticsResult;  
``` 

Die nachstehende Beispielabfrage liest einige Bestandteile der ausführlichen Ausgabe aus jeder Komponente in der Tabelle:  
```sql  
-- system
select data.value('(/system/@systemCpuUtilization)[1]','bigint') as 'System_CPU',
   data.value('(/system/@sqlCpuUtilization)[1]','bigint') as 'SQL_CPU',
   data.value('(/system/@nonYieldingTasksReported)[1]','bigint') as 'NonYielding_Tasks',
   data.value('(/system/@pageFaults)[1]','bigint') as 'Page_Faults',
   data.value('(/system/@latchWarnings)[1]','bigint') as 'Latch_Warnings',
   data.value('(/system/@BadPagesDetected)[1]','bigint') as 'BadPages_Detected',
   data.value('(/system/@BadPagesFixed)[1]','bigint') as 'BadPages_Fixed'
from SpServerDiagnosticsResult 
where component_name like 'system'
go

-- Resource Monitor
select data.value('(./Record/ResourceMonitor/Notification)[1]', 'VARCHAR(max)') AS [Notification],
    data.value('(/resource/memoryReport/entry[@description=''Working Set'']/@value)[1]', 'bigint')/1024 AS [SQL_Mem_in_use_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Paging File'']/@value)[1]', 'bigint')/1024 AS [Avail_Pagefile_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Physical Memory'']/@value)[1]', 'bigint')/1024 AS [Avail_Physical_Mem_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Virtual Memory'']/@value)[1]', 'bigint')/1024 AS [Avail_VAS_MB],
    data.value('(/resource/@lastNotification)[1]','varchar(100)') as 'LastNotification',
    data.value('(/resource/@outOfMemoryExceptions)[1]','bigint') as 'OOM_Exceptions'
from SpServerDiagnosticsResult 
where component_name like 'resource'
go

-- Nonpreemptive waits
select waits.evt.value('(@waitType)','varchar(100)') as 'Wait_Type',
   waits.evt.value('(@waits)','bigint') as 'Waits',
   waits.evt.value('(@averageWaitTime)','bigint') as 'Avg_Wait_Time',
   waits.evt.value('(@maxWaitTime)','bigint') as 'Max_Wait_Time'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/queryProcessing/topWaits/nonPreemptive/byDuration/wait') AS waits(evt)
where component_name like 'query_processing'
go

-- Preemptive waits
select waits.evt.value('(@waitType)','varchar(100)') as 'Wait_Type',
   waits.evt.value('(@waits)','bigint') as 'Waits',
   waits.evt.value('(@averageWaitTime)','bigint') as 'Avg_Wait_Time',
   waits.evt.value('(@maxWaitTime)','bigint') as 'Max_Wait_Time'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/queryProcessing/topWaits/preemptive/byDuration/wait') AS waits(evt)
where component_name like 'query_processing'
go

-- CPU intensive requests
select cpureq.evt.value('(@sessionId)','bigint') as 'SessionID',
   cpureq.evt.value('(@command)','varchar(100)') as 'Command',
   cpureq.evt.value('(@cpuUtilization)','bigint') as 'CPU_Utilization',
   cpureq.evt.value('(@cpuTimeMs)','bigint') as 'CPU_Time_ms'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/queryProcessing/cpuIntensiveRequests/request') AS cpureq(evt)
where component_name like 'query_processing'
go

-- Blocked Process Report
select blk.evt.query('.') as 'Blocked_Process_Report_XML'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/queryProcessing/blockingTasks/blocked-process-report') AS blk(evt)
where component_name like 'query_processing'
go

-- IO
select data.value('(/ioSubsystem/@ioLatchTimeouts)[1]','bigint') as 'Latch_Timeouts',
   data.value('(/ioSubsystem/@totalLongIos)[1]','bigint') as 'Total_Long_IOs'
from SpServerDiagnosticsResult 
where component_name like 'io_subsystem'
go

-- Event information
select xevts.evt.value('(@name)','varchar(100)') as 'xEvent_Name',
   xevts.evt.value('(@package)','varchar(100)') as 'Package',
   xevts.evt.value('(@timestamp)','datetime') as 'xEvent_Time',
   xevts.evt.query('.') as 'Event Data'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/events/session/RingBufferTarget/event') AS xevts(evt)
where component_name like 'events'
go  
``` 
  
## <a name="see-also"></a>Siehe auch  
 [Failoverrichtlinie für Failoverclusterinstanzen](../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)  
  
  
