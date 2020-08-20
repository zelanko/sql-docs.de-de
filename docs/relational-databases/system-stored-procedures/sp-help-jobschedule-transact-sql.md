---
description: sp_help_jobschedule (Transact-SQL)
title: sp_help_jobschedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobschedule
- sp_help_jobschedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobschedule
ms.assetid: 2cded902-9272-4667-ac4b-a4f95a9f008e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 002534c38b5060dca0457d0c704194db037b93b2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481273"
---
# <a name="sp_help_jobschedule-transact-sql"></a>sp_help_jobschedule (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen zur Zeitplanung von Aufträgen zurück, mit denen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] automatisierte Aktivitäten ausführt.  
 
 
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_jobschedule { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @schedule_name = ] 'schedule_name' ]  
     [ , [ @schedule_id = ] schedule_id ]  
     [ , [ @include_description = ] include_description ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id` Die Auftrags-ID. *job_id*ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags. *job_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]
> Es muss entweder *job_id* oder *job_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.

`[ @schedule_name = ] 'schedule_name'` Der Name des Zeit Plan Elements für den Auftrag. *schedule_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @schedule_id = ] schedule_id` Die ID des Zeit Plan Elements für den Auftrag. *schedule_id*ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @include_description = ] include_description` Gibt an, ob die Beschreibung des Zeitplans in das Resultset eingeschlossen werden soll. *include_description* ist vom Typ **Bit**. der Standardwert ist **0**. Wenn *include_description* **0**ist, ist die Beschreibung des Zeitplans nicht im Resultset enthalten. Wenn *include_description* **1**ist, wird die Beschreibung des Zeitplans in das Resultset eingeschlossen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|ID des Zeitplans.|  
|**schedule_name**|**sysname**|Name des Zeitplans.|  
|**enabled**|**int**|Gibt an, ob der Zeitplan aktiviert (**1**) oder nicht aktiviert (**0**) ist.|  
|**freq_type**|**int**|Der Wert, der angibt, wann der Auftrag ausgeführt werden soll.<br /><br /> **1** = einmal<br /><br /> **4** = täglich<br /><br /> **8** = wöchentlich<br /><br /> **16** = monatlich<br /><br /> **32** = monatlich, relativ zum **freq_interval**<br /><br /> **64** = ausführen, wenn der **SQLServerAgent** -Dienst gestartet wird.|  
|**freq_interval**|**int**|Tage, an denen der Auftrag ausgeführt wird. Der Wert hängt vom Wert **freq_type**ab. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_subday_type**|**int**|Einheiten für **freq_subday_interval**. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_subday_interval**|**int**|Anzahl der **freq_subday_type** Zeiträume zwischen den einzelnen Ausführungen des Auftrags. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_relative_interval**|**int**|Das Vorkommen des **freq_interval** eines geplanten Auftrags in jedem Monat. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_recurrence_factor**|**int**|Anzahl der Monate zwischen der geplanten Ausführung des Auftrags|  
|**active_start_date**|**int**|Datum, an dem der Zeitplan aktiviert wird.|  
|**active_end_date**|**int**|Enddatum für den Zeitplan.|  
|**active_start_time**|**int**|Uhrzeit, zu der der Zeitplan gestartet wird.|  
|**active_end_time**|**int**|Uhrzeit, zu der der Zeitplan beendet wird.|  
|**date_created**|**datetime**|Datum, an dem der Zeitplan erstellt wird|  
|**schedule_description**|**nvarchar(4000)**|Eine englische Beschreibung des Zeitplans, der von Werten inmsdb.dbo.sysZeit ** Plänen**abgeleitet wird. Wenn *include_description* **0**ist, enthält diese Spalte Text, der besagt, dass die Beschreibung nicht angefordert wurde.|  
|**next_run_date**|**int**|Datum, an dem der Zeitplan die nächste Ausführung des Auftrags bewirken wird|  
|**next_run_time**|**int**|Uhrzeit, zu der der Zeitplan die nächste Ausführung des Auftrags bewirken wird|  
|**schedule_uid**|**uniqueidentifier**|Bezeichner für den Zeitplan.|  
|**job_count**|**int**|Die Anzahl der zurückgegebenen Aufträge.|  
  
> **Hinweis: sp_help_jobschedule** gibt Werte aus den **dbo.sysjobzeitpläne** und **dbo.sysplant** Systemtabellen in **msdb**zurück. **sysjobzeitpläne** werden alle 20 Minuten aktualisiert. Dies kann Auswirkungen auf die Werte haben, die von dieser gespeicherten Prozedur zurückgegeben werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Parameter von **sp_help_jobschedule** können nur in bestimmten Kombinationen verwendet werden. Wenn *schedule_id* angegeben wird, können weder *job_id* noch *job_name* angegeben werden. Andernfalls können die Parameter *job_id* oder *job_name* mit *schedule_name*verwendet werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** . Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Mitglieder von **SQLAgentUserRole** können nur Eigenschaften von Auftrags Zeitplänen anzeigen, deren Besitzer Sie sind.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-the-job-schedule-for-a-specific-job"></a>A. Zurückgeben des Auftragszeitplans für einen bestimmten Auftrag  
 Im folgenden Beispiel werden die Zeitplaninformationen für einen Auftrag namens `BackupDatabase` zurückgegeben  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobschedule  
    @job_name = N'BackupDatabase' ;  
GO  
```  
  
### <a name="b-returning-the-job-schedule-for-a-specific-schedule"></a>B. Zurückgeben des Auftragszeitplans für einen bestimmten Zeitplan  
 Im folgenden Beispiel werden die Informationen für den Zeitplan `NightlyJobs` und den Auftrag `RunReports` zurückgegeben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobschedule   
    @job_name = N'RunReports',  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
### <a name="c-returning-the-job-schedule-and-schedule-description-for-a-specific-schedule"></a>C. Zurückgeben des Auftragszeitplans und der Zeitplanbeschreibung für einen bestimmten Zeitplan  
 Im folgenden Beispiel werden die Informationen für den Zeitplan `NightlyJobs` und den Auftrag `RunReports` zurückgegeben. Das zurückgegebene Resultset schließt eine Beschreibung des Zeitplans ein.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobschedule  
    @job_name = N'RunReports',  
    @schedule_name = N'NightlyJobs',  
    @include_description = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_update_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
