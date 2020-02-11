---
title: sp_update_schedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_schedule
- sp_update_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_schedule
ms.assetid: 97b3119b-e43e-447a-bbfb-0b5499e2fefe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 51e21d189a9302c2dc7b74a013846460e9cb7bc5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67946640"
---
# <a name="sp_update_schedule-transact-sql"></a>sp_update_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Einstellungen für einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Zeitplan.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_update_schedule   
    {   [ @schedule_id = ] schedule_id   
      | [ @name = ] 'schedule_name' }  
    [ , [ @new_name = ] new_name ]  
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
    [ , [ @automatic_post =] automatic_post ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @schedule_id = ] schedule_id`Der Bezeichner des Zeitplans, der geändert werden soll. *schedule_id* ist vom Datentyp **int**und hat keinen Standardwert. Es muss entweder *schedule_id* oder *schedule_name* angegeben werden.  
  
`[ @name = ] 'schedule_name'`Der Name des Zeitplans, der geändert werden soll. *schedule_name*ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Es muss entweder *schedule_id* oder *schedule_name* angegeben werden.  
  
`[ @new_name = ] new_name`Der neue Name für den Zeitplan. *new_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn *new_name* NULL ist, bleibt der Name des Zeitplans unverändert.  
  
`[ @enabled = ] enabled`Gibt den aktuellen Status des Zeitplans an. *aktiviert*ist vom Datentyp **tinyint**. der Standardwert ist **1** (aktiviert). Wenn der Wert **0**ist, ist der Zeitplan nicht aktiviert. Wenn der Zeitplan nicht aktiviert ist, werden über diesen Zeitplan keine Aufträge ausgeführt.  
  
`[ @freq_type = ] freq_type`Ein Wert, der angibt, wann ein Auftrag ausgeführt werden soll. *freq_type*ist vom Datentyp **int**und hat den Standardwert **0**. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Einmalig|  
|**4**|Täglich|  
|**88**|Wöchentlich|  
|**Uhr**|Monatlich|  
|**32**|Monatlich, relativ zum *freq-Intervall*|  
|**64**|Ausführen beim Start des SQLServerAgent-Diensts|  
|**128**|Ausführen, wenn sich der Computer im Leerlauf befindet|  
  
`[ @freq_interval = ] freq_interval`Die Tage, an denen ein Auftrag ausgeführt wird. *freq_interval* ist vom Datentyp **int**und hat den Standardwert **0**. der Wert hängt vom Wert *freq_type*ab.  
  
|Wert *freq_type*|Auswirkung auf *freq_interval*|  
|---------------------------|--------------------------------|  
|**1** (einmal)|*freq_interval* wird nicht verwendet.|  
|**4** (täglich)|Alle *freq_interval* Tage.|  
|**8** (wöchentlich)|*freq_interval* ist eine oder mehrere der folgenden (kombiniert mit einem logischen **or** -Operator):<br /><br /> **1** = Sonntag<br /><br /> **2** = Montag<br /><br /> **4** = Dienstag<br /><br /> **8** = Mittwoch<br /><br /> **16** = Donnerstag<br /><br /> **32** = Freitag<br /><br /> **64** = Samstag|  
|**16** (monatlich)|Am *freq_interval* Tag des Monats.|  
|**32** (monatlich, relativ)|*freq_interval* ist einer der folgenden:<br /><br /> **1** = Sonntag<br /><br /> **2** = Montag<br /><br /> **3** = Dienstag<br /><br /> **4** = Mittwoch<br /><br /> **5** = Donnerstag<br /><br /> **6** = Freitag<br /><br /> **7** = Samstag<br /><br /> **8** = Tag<br /><br /> **9** = Wochentag<br /><br /> **10** = Wochenendtag|  
|**64** (wenn der SQLServerAgent-Dienst gestartet wird)|*freq_interval* wird nicht verwendet.|  
|**128**|*freq_interval* wird nicht verwendet.|  
  
`[ @freq_subday_type = ] freq_subday_type`Gibt die Einheiten für *freq_subday_interval * * an.* *freq_subday_type*ist vom Datentyp **int**und hat den Standardwert **0**. die folgenden Werte sind möglich:  
  
|value|Beschreibung (Einheit)|  
|-----------|--------------------------|  
|**0x1**|Zum angegebenen Zeitpunkt|  
|**0x2**|Sekunden|  
|**0x4**|Minuten|  
|**0x8**|Stunden|  
  
`[ @freq_subday_interval = ] freq_subday_interval`Die Anzahl der *freq_subday_type* Zeiträume zwischen jeder Ausführung eines Auftrags. *freq_subday_interval*ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @freq_relative_interval = ] freq_relative_interval`Das Vorkommen eines Auftrags *freq_interval* in jedem Monat, wenn *freq_interval* **32** (monatlich, relativ) ist. *freq_relative_interval*ist vom Datentyp **int**und hat den Standardwert **0**. die folgenden Werte sind möglich:  
  
|value|Beschreibung (Einheit)|  
|-----------|--------------------------|  
|**1**|First (Erster)|  
|**2**|Sekunde|  
|**4**|Dritter|  
|**88**|Vierter|  
|**Uhr**|Last (Letzter)|  
  
`[ @freq_recurrence_factor = ] freq_recurrence_factor`Die Anzahl der Wochen oder Monate zwischen der geplanten Ausführung eines Auftrags. *freq_recurrence_factor* wird nur verwendet, ** wenn freq_type **8**, **16**oder **32**ist. *freq_recurrence_factor*ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @active_start_date = ] active_start_date`Das Datum, an dem die Ausführung eines Auftrags beginnen kann. *active_start_date*ist vom Datentyp **int**und hat den Standardwert NULL, der das heutige Datum angibt. Das Datum wird als YYYYMMDD formatiert. Wenn *active_start_date* nicht NULL ist, muss das Datum größer oder gleich 19900101 sein.  
  
 Überprüfen Sie nach dem Erstellen des Zeitplans, ob das Startdatum korrekt ist. Weitere Informationen finden Sie im Abschnitt "Planen des Start Datums" unter [Erstellen und Anfügen von Zeitplänen an Aufträge](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
`[ @active_end_date = ] active_end_date`Das Datum, an dem die Ausführung eines Auftrags beendet werden kann. *active_end_date*ist vom Datentyp **int**und hat den Standardwert **99991231**, womit der 31. Dezember 9999 angegeben wird. Im Format JJJJMMTT.  
  
`[ @active_start_time = ] active_start_time`Die Uhrzeit an einem beliebigen Tag zwischen *active_start_date* und *active_end_date* , um die Ausführung eines Auftrags zu beginnen. *active_start_time*ist vom Datentyp **int**und hat den Standardwert 000000, der 12:00:00 Uhr im 24-Stunden-Format an und muss im Format HHMMSS eingegeben werden.  
  
`[ @active_end_time = ] active_end_time`Die Uhrzeit an einem beliebigen Tag zwischen *active_start_date* und *active_end_date* , um die Ausführung eines Auftrags zu beenden. *active_end_time*ist vom Datentyp **int**und hat den Standardwert **235959**, der 11:59:59 Uhr angibt. im 24-Stunden-Format an und muss im Format HHMMSS eingegeben werden.  
  
`[ @owner_login_name = ] 'owner_login_name']`Der Name des Server Prinzipals, der den Zeitplan besitzt. *owner_login_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL, womit angegeben wird, dass der Zeitplan dem Ersteller gehört.  
  
`[ @automatic_post = ] automatic_post`Bleiben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Alle Aufträge, die den Zeitplan verwenden, verwenden sofort die neuen Einstellungen. Zurzeit ausgeführte Aufträge werden durch das Ändern eines Zeitplans jedoch nicht beendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder der **sysadmin** -Rolle können einen Zeitplan ändern, der im Besitz eines anderen Benutzers ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der aktivierte Status des `NightlyJobs`-Zeitplans zu `0` und der Besitzer zu `terrid` geändert.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_schedule  
    @name = 'NightlyJobs',  
    @enabled = 0,  
    @owner_login_name = 'terrid' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen und Anfügen von Zeitplänen an Aufträge](../../ssms/agent/create-and-attach-schedules-to-jobs.md)   
 [Planen eines Auftrags](../../ssms/agent/schedule-a-job.md)   
 [Erstellen eines Zeitplans](../../ssms/agent/create-a-schedule.md)   
 [SQL Server-Agent gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_add_jobschedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
