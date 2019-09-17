---
title: sp_add_schedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_schedule_TSQL
- sp_add_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_schedule
ms.assetid: 9060aae3-3ddd-40a5-83bb-3ea7ab1ffbd7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 21fe2a05c87caf5270967381e9ebeefc1069729f
ms.sourcegitcommit: df1f71231f8edbdfe76e8851acf653c25449075e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2019
ms.locfileid: "70810396"
---
# <a name="sp_add_schedule-transact-sql"></a>sp_add_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Legt einen Zeitplan an, der von einer beliebigen Anzahl von Aufträgen verwendet werden kann.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_schedule [ @schedule_name = ] 'schedule_name'   
    [ , [ @enabled = ] enabled ]  
    [ , [ @freq_type = ] freq_type ]  
    [ , [ @freq_interval = ] freq_interval ]   
    [ , [ @freq_subday_type = ] freq_subday_type ]   
    [ , [ @freq_subday_interval = ] freq_subday_interval ]   
    [ , [ @freq_relative_interval = ] freq_relative_interval ]   
    [ , [ @freq_recurrence_factor = ] freq_recurrence_factor ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @active_start_time = ] active_start_time ]   
    [ , [ @active_end_time = ] active_end_time ]   
    [ , [ @owner_login_name = ] 'owner_login_name' ]  
    [ , [ @schedule_uid = ] schedule_uid OUTPUT ]  
    [ , [ @schedule_id = ] schedule_id OUTPUT ]  
    [ , [ @originating_server = ] server_name ] /* internal */  
```  
  
## <a name="arguments"></a>Argumente  
`[ @schedule_name = ] 'schedule_name'`Der Name des Zeitplans. *schedule_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @enabled = ] enabled`Gibt den aktuellen Status des Zeitplans an. *aktiviert* ist vom Datentyp **tinyint**. der Standardwert ist **1** (aktiviert). Wenn der Wert **0**ist, ist der Zeitplan nicht aktiviert. Wenn der Zeitplan nicht aktiviert ist, werden über diesen Zeitplan keine Aufträge ausgeführt.  
  
`[ @freq_type = ] freq_type`Ein Wert, der angibt, wann ein Auftrag ausgeführt werden soll. *freq_type* ist vom Datentyp **int**und hat den Standardwert **0**. die folgenden Werte sind möglich:  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**4**|Täglich|  
|**8**|Wöchentlicher Zeitplan|  
|**16**|Monatlicher Zeitplan|  
|**32**|Monatlich, relativ zu *freq_interval*|  
|**64**|Beim Starten des SQL Agent-Dienstanbieter ausführen|  
|**128**|Ausführen, wenn sich der Computer im Leerlauf befindet (wird in [verwaltete Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)nicht unterstützt) |  
  
`[ @freq_interval = ] freq_interval`Die Tage, an denen ein Auftrag ausgeführt wird. *freq_interval* ist vom Datentyp **int**. der Standardwert ist **1**, und der Wert hängt vom Wert von *freq_type*ab.  
  
|Wert von *freq_type*|Auswirkung auf *freq_interval*|  
|---------------------------|--------------------------------|  
|**1** (einmal)|*freq_interval* wird nicht verwendet.|  
|**4** (täglich)|Alle *freq_interval* Tage.|  
|**8** (wöchentlich)|*freq_interval* ist eine oder mehrere der folgenden (kombiniert mit einem logischen OR-Operator):<br /><br /> **1** = Sonntag<br /><br /> **2** = Montag<br /><br /> **4** = Dienstag<br /><br /> **8** = Mittwoch<br /><br /> **16** = Donnerstag<br /><br /> **32** = Freitag<br /><br /> **64** = Samstag|  
|**16** (monatlich)|Am *freq_interval* Tag des Monats.|  
|**32** (monatlich, relativ)|*freq_interval* ist einer der folgenden:<br /><br /> **1** = Sonntag<br /><br /> **2** = Montag<br /><br /> **3** = Dienstag<br /><br /> **4** = Mittwoch<br /><br /> **5** = Donnerstag<br /><br /> **6** = Freitag<br /><br /> **7** = Samstag<br /><br /> **8** = Tag<br /><br /> **9** = Wochentag<br /><br /> **10** = Wochenendtag|  
|**64** (wenn der SQLServerAgent-Dienst gestartet wird)|*freq_interval* wird nicht verwendet.|  
|**128**|*freq_interval* wird nicht verwendet.|  
  
`[ @freq_subday_type = ] freq_subday_type`Gibt die Einheiten für *freq_subday_interval*an. *freq_subday_type* ist vom Datentyp **int**und hat den Standardwert **0**. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung (Einheit)|  
|-----------|--------------------------|  
|**0x1**|Zum angegebenen Zeitpunkt|  
|**0x2**|Sekunden|  
|**0x4**|Minuten|  
|**0x8**|Stunden|  
  
`[ @freq_subday_interval = ] freq_subday_interval`Die Anzahl der *freq_subday_type* Zeiträume, die zwischen den einzelnen Ausführungen eines Auftrags auftreten. *freq_subday_interval* ist vom Datentyp **int**und hat den Standardwert **0**. Hinweis: Das Intervall muss länger als 10 Sekunden sein. *freq_subday_interval* wird in den Fällen ignoriert, in denen *freq_subday_type* gleich **1**ist.  
  
`[ @freq_relative_interval = ] freq_relative_interval`Ein Auftrags Vorkommen von *freq_interval* in jedem Monat, wenn *freq_interval* 32 (monatlich, relativ) ist. *freq_relative_interval* ist vom Datentyp **int**und hat den Standardwert **0**. die folgenden Werte sind möglich: *freq_relative_interval* wird in den Fällen ignoriert, in denen *freq_type* nicht gleich 32 ist.  
  
|Wert|Beschreibung (Einheit)|  
|-----------|--------------------------|  
|**1**|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
  
`[ @freq_recurrence_factor = ] freq_recurrence_factor`Die Anzahl der Wochen oder Monate zwischen der geplanten Ausführung eines Auftrags. *freq_recurrence_factor* wird nur verwendet, wenn freq_type **8**, **16**oder **32**ist. *freq_recurrence_factor* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @active_start_date = ] active_start_date`Das Datum, an dem die Ausführung eines Auftrags beginnen kann. *active_start_date* ist vom Datentyp **int**und hat den Standardwert NULL, der das heutige Datum angibt. Das Datum wird als YYYYMMDD formatiert. Wenn *active_start_date* nicht NULL ist, muss das Datum größer oder gleich 19900101 sein.  
  
 Überprüfen Sie nach dem Erstellen des Zeitplans, ob das Startdatum korrekt ist. Weitere Informationen finden Sie im Abschnitt "Planen des Start Datums" unter [Erstellen und Anfügen von Zeitplänen an Aufträge](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
 Bei wöchentlichen oder monatlichen Zeitplänen wird vom Agent nicht berücksichtigt, ob active_start_date in der Vergangenheit liegt, und das aktuelle Datum verwendet. Beim Erstellen eines SQL-Agentzeitplans mithilfe von sp_add_schedule kann der active_start_date-Parameter angegeben werden, der das Startdatum der Auftragsausführung darstellt. Wenn der Zeitplantyp "Wöchentlich" oder "Monatlich" lautet und der active_start_date-Parameter auf ein Datum in der Vergangenheit festgelegt ist, werden der active_start_date-Parameter ignoriert und das aktuelle Datum für active_start_date verwendet.  
  
`[ @active_end_date = ] active_end_date`Das Datum, an dem die Ausführung eines Auftrags beendet werden kann. *active_end_date* ist vom Datentyp **int**und hat den Standardwert **99991231**, womit der 31. Dezember 9999 angegeben wird. Im Format JJJJMMTT.  
  
`[ @active_start_time = ] active_start_time`Die Uhrzeit an einem beliebigen Tag zwischen *active_start_date* und *active_end_date* , mit der die Ausführung eines Auftrags begonnen werden soll. *active_start_time* ist vom Datentyp **int**und hat den Standardwert **000000**, der 12:00:00 Uhr angibt. im 24-Stunden-Format an und muss im Format HHMMSS eingegeben werden.  
  
`[ @active_end_time = ] active_end_time`Die Uhrzeit an einem beliebigen Tag zwischen *active_start_date* und *active_end_date* , um die Ausführung eines Auftrags zu beenden. *active_end_time* ist vom Datentyp **int**und hat den Standardwert **235959**, der 11:59:59 Uhr angibt. im 24-Stunden-Format an und muss im Format HHMMSS eingegeben werden.  
  
`[ @owner_login_name = ] 'owner_login_name'`Der Name des Server Prinzipals, der den Zeitplan besitzt. *owner_login_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL, womit angegeben wird, dass der Zeitplan dem Ersteller gehört.  
  
`[ @schedule_uid = ] _schedule_uidOUTPUT`Ein eindeutiger Bezeichner für den Zeitplan. *schedule_uid* ist eine Variable vom Typ **uniqueidentifier**.  
  
`[ @schedule_id = ] _schedule_idOUTPUT`Ein Bezeichner für den Zeitplan. *schedule_id* ist eine Variable vom Typ **int**.  
  
`[ @originating_server = ] server_name` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] können Aufträge problemlos mithilfe einer grafischen Oberfläche verwaltet werden. Dies ist die empfohlene Vorgehensweise für die Erstellung und Verwaltung der Auftragsinfrastruktur.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-creating-a-schedule"></a>A. Erstellen eines Zeitplans  
 Im folgenden Beispiel wird ein Zeitplan mit dem Namen `RunOnce` erstellt. Der Zeitplan wird einmal um `23:30` Uhr an dem Tag ausgeführt, an dem der Zeitplan erstellt wird.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_schedule  
    @schedule_name = N'RunOnce',  
    @freq_type = 1,  
    @active_start_time = 233000 ;  
  
GO  
```  
  
### <a name="b-creating-a-schedule-attaching-the-schedule-to-multiple-jobs"></a>B. Erstellen eines Zeitplans und Zuweisen des Zeitplans zu mehreren Aufträgen  
 Im folgenden Beispiel wird ein Zeitplan mit dem Namen `NightlyJobs` erstellt. Aufträge, die diesen Zeitplan verwenden, werden jeden Tag zur Serveruhrzeit `01:00` Uhr ausgeführt. Im Beispiel wird der Zeitplan den Aufträgen `BackupDatabase` und `RunReports` angefügt.  
  
> [!NOTE]  
>  Bei diesem Beispiel wird davon ausgegangen, dass die Aufträge `BackupDatabase` und `RunReports` bereits vorhanden sind.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_add_schedule  
    @schedule_name = N'NightlyJobs' ,  
    @freq_type = 4,  
    @freq_interval = 1,  
    @active_start_time = 010000 ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'BackupDatabase',  
   @schedule_name = N'NightlyJobs' ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'RunReports',  
   @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Anfügen von Zeitplänen an Aufträge](../../ssms/agent/create-and-attach-schedules-to-jobs.md)   
 [Planen eines Auftrags](../../ssms/agent/schedule-a-job.md)   
 [Erstellen eines Zeitplans](../../ssms/agent/create-a-schedule.md)   
 [SQL Server-Agent gespeicherter &#40;Prozeduren (Transact-SQL)&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_jobschedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md)   
 [sp_update_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
