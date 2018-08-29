---
title: Sp_add_jobschedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/28/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_jobschedule
- sp_add_jobschedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_jobschedule
ms.assetid: ffce19d9-d1d6-45b4-89fd-ad0f60822ba0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0c60decc6d074208d2149a3597818963d57a50e7
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43021968"
---
# <a name="spaddjobschedule-transact-sql"></a>sp_add_jobschedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt einen Zeitplan für einen Auftrag.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_jobschedule [ @job_id = ] job_id, | [ @job_name = ] 'job_name', [ @name = ] 'name'  
     [ , [ @enabled = ] enabled_flag ]  
     [ , [ @freq_type = ] frequency_type ]  
     [ , [ @freq_interval = ] frequency_interval ]  
     [ , [ @freq_subday_type = ] frequency_subday_type ]  
     [ , [ @freq_subday_interval = ] frequency_subday_interval ]  
     [ , [ @freq_relative_interval = ] frequency_relative_interval ]  
     [ , [ @freq_recurrence_factor = ] frequency_recurrence_factor ]  
     [ , [ @active_start_date = ] active_start_date ]  
     [ , [ @active_end_date = ] active_end_date ]  
     [ , [ @active_start_time = ] active_start_time ]  
     [ , [ @active_end_time = ] active_end_time ]  
     [ , [ @schedule_id = ] schedule_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@job_id=** ] *job_id*  
 Die ID des Auftrags, dem der Zeitplan hinzugefügt wird. *Job_id* ist **Uniqueidentifier**, hat keinen Standardwert.  
  
 [  **@job_name=** ] **"***Job_name***"**  
 Der Name des Auftrags, dem der Zeitplan hinzugefügt wird. *Job_name* ist **vom Datentyp nvarchar(128)**, hat keinen Standardwert.  
  
> [!NOTE]  
>  Entweder *Job_id* oder *Job_name* muss angegeben werden, aber beide Angaben sind nicht möglich.  
  
 [ **@name=** ] **'***name***'**  
 Name des Zeitplans. *Namen* ist **vom Datentyp nvarchar(128)**, hat keinen Standardwert.  
  
 [ **@enabled=** ] *enabled_flag*  
 Gibt den aktuellen Status des Zeitplans an. *Enabled_flag* ist **Tinyint**, hat den Standardwert **1** (aktiviert). Wenn **0**, der Zeitplan ist nicht aktiviert. Wenn der Zeitplan deaktiviert ist, wird der Auftrag nicht ausgeführt.  
  
 [ **@freq_type=** ] *frequency_type*  
 Ein Wert, der angibt, wann der Auftrag ausgeführt werden soll. *Frequency_type* ist **Int**, hat den Standardwert **0**, und kann einen der folgenden Werte:  
  
|value|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**4**|Täglich|  
|**8**|Wöchentlicher Zeitplan|  
|**16**|Monatlicher Zeitplan|  
|**32**|Monatlich, relativ zum *Frequency_interval.*|  
|**64**|Ausführen, wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst gestartet wird.|  
|**128**|Ausführen, wenn sich der Computer im Leerlauf befindet.|  
  
 [ **@freq_interval=** ] *frequency_interval*  
 Der Tag, an dem der Auftrag ausgeführt wird. *Frequency_interval* ist **Int**, hat den Standardwert 0 (null) und hängt vom Wert der *Frequency_type* in der folgenden Tabelle aufgeführt:  
  
|value|Wirkung|  
|-----------|------------|  
|**1** (einmal)|*Frequency_interval* wird nicht verwendet.|  
|**4** (täglich)|Jede *Frequency_interval* Tage.|  
|**8** (wöchentlich)|*Frequency_interval* kann einen oder mehrere der folgenden (zusammen mit logischen OR-Operator):<br /><br /> 1 = Sonntag<br /><br /> 2 = Montag<br /><br /> 4 = Dienstag<br /><br /> 8 = Mittwoch<br /><br /> 16 = Donnerstag<br /><br /> 32 = Freitag<br /><br /> 64 = Samstag|  
|**16** (monatlich)|Auf der *Frequency_interval* Tag des Monats.|  
|**32** (mit relativem Monatsintervall)|*Frequency_interval* ist eine der folgenden:<br /><br /> 1 = Sonntag<br /><br /> 2 = Montag<br /><br /> 3 = Dienstag<br /><br /> 4 = Mittwoch<br /><br /> 5 = Donnerstag<br /><br /> 6 = Freitag<br /><br /> 7 = Samstag<br /><br /> 8 = Tag<br /><br /> 9 = Arbeitstag<br /><br /> 10 = Wochenendtag|  
|**64** (wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -agentdiensts wird)|*Frequency_interval* wird nicht verwendet.|  
|**128**|*Frequency_interval* wird nicht verwendet.|  
  
 [ **@freq_subday_type=** ] *frequency_subday_type*  
 Gibt die Einheiten für *Frequency_subday_interval*. *Frequency_subday_type* ist **Int**und hat keinen Standardwert und kann die folgenden Werte sind möglich:  
  
|value|Beschreibung (Einheit)|  
|-----------|--------------------------|  
|**0x1**|Zum angegebenen Zeitpunkt|  
|**0x4**|Minuten|  
|**0x8**|Stunden|  
  
 [ **@freq_subday_interval=** ] *frequency_subday_interval*  
 Anzahl der *Frequency_subday_type* -Perioden zwischen den Ausführungsinstanzen des Auftrags. *Frequency_subday_interval* ist **Int**, hat den Standardwert 0.  
  
 [ **@freq_relative_interval=** ] *frequency_relative_interval*  
 Weitere definiert die *Frequency_interval* beim *Frequency_type* nastaven NA hodnotu **32** (mit relativem Monatsintervall).  
  
 *Frequency_relative_interval* ist **Int**und hat keinen Standardwert und kann die folgenden Werte sind möglich:  
  
|value|Beschreibung (Einheit)|  
|-----------|--------------------------|  
|**1**|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
  
 *Frequency_relative_interval* zeigt das Auftreten des Intervalls. Z. B. wenn *Frequency_relative_interval* nastaven NA hodnotu **2**, *Frequency_type* nastaven NA hodnotu **32**, und *Frequency_ Intervall* nastaven NA hodnotu **3**, kommt es, der geplante Auftrag am zweiten Dienstag jedes Monats.  
  
 [ **@freq_recurrence_factor=** ] *frequency_recurrence_factor*  
 Die Anzahl der Wochen oder Monate zwischen den geplanten Ausführungen des Auftrags. *Frequency_recurrence_factor* wird nur verwendet, wenn *Frequency_type* nastaven NA hodnotu **8**, **16**, oder **32**. *Frequency_recurrence_factor* ist **Int**, hat den Standardwert 0.  
  
 [ **@active_start_date=** ] *active_start_date*  
 Das Datum, an dem Ausführung des Auftrags beginnen kann. *Active_start_date* ist **Int**, hat keinen Standardwert. Das Datum wird als JJJJMMTT formatiert. Wenn *Active_start_date* festgelegt ist, muss das Datum größer oder gleich 19900101 sein.  
  
 Überprüfen Sie nach dem Erstellen des Zeitplans, ob das Startdatum korrekt ist. Weitere Informationen finden Sie im Abschnitt "Planen von Startdaten" in [erstellen und Zuweisen von Zeitplänen zu Aufträgen](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
 [ **@active_end_date=** ] *active_end_date*  
 Das Datum, an dem die Ausführung des Auftrags beendet werden kann. *Active_end_date* ist **Int**, hat keinen Standardwert. Das Datum wird als JJJJMMTT formatiert.  
  
 [ **@active_start_time=** ] *active_start_time*  
 Auf einem beliebigen Tag zwischen *Active_start_date* und *Active_end_date* zum Starten der auftragsausführung. *Active_start_time* ist **Int**, hat keinen Standardwert. Die Zeit wird auf dem 24-Stunden-Format HHMMSS verwendet.  
  
 [**@active_end_time= *** Active_end_time*  
 Auf einem beliebigen Tag zwischen *Active_start_date* und *Active_end_date* zum Ende der auftragsausführung. *Active_end_time* ist **Int**, hat keinen Standardwert. Die Zeit wird auf dem 24-Stunden-Format HHMMSS verwendet.  
  
 [ **@schedule_id=***schedule_id***OUTPUT**  
 Die Zeitplan-ID, die dem Zeitplan zugewiesen wird, wenn er erfolgreich erstellt wird. *Schedule_id* ist eine Ausgabevariable vom Typ **Int**, hat keinen Standardwert.  
  
 [ **@schedule_uid**=] *Schedule_uid *** Ausgabe**  
 Ein eindeutiger Bezeichner für den Zeitplan. *Wert für schedule_uid an* ist eine Variable vom Typ **Uniqueidentifier**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Auftragszeitpläne können jetzt unabhängig von Aufträgen verwaltet werden. Verwenden Sie zum Hinzufügen eines Zeitplans zu einem Auftrag **Sp_add_schedule** um den Zeitplan zu erstellen und **Sp_attach_schedule** den Zeitplan einem Auftrag angefügt.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
 
 ## <a name="example"></a>Beispiel
 Das folgende Beispiel weist einen Auftragszeitplan `SaturdayReports` die wird jeden Samstag um 2:00 Uhr ausgeführt.
```sql  
EXEC msdb.dbo.sp_add_jobschedule 
        @job_name = N'SaturdayReports', -- Job name
        @name = N'Weekly_Sat_2AM',  -- Schedule name
        @freq_type = 8, -- Weekly
        @freq_interval = 64, -- Saturday
        @freq_recurrence_factor = 1, -- every week
        @active_start_time = 20000 -- 2:00 AM
```
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Zuweisen von Zeitplänen zu Aufträgen](../../ssms/agent/create-and-attach-schedules-to-jobs.md)   
 [Planen eines Auftrags](../../ssms/agent/schedule-a-job.md)   
 [Erstellen Sie einen Zeitplan](../../ssms/agent/create-a-schedule.md)   
 [SQL Server-Agent-gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_update_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
