---
description: sp_help_job (Transact-SQL)
title: sp_help_job (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_job_TSQL
- sp_help_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_job
ms.assetid: 8a8b6104-e0e4-4d07-a2c3-f4243ee0d6fa
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5c0b2f0845c98f4b5fa403bd98b87718afd0fb26
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89549691"
---
# <a name="sp_help_job-transact-sql"></a>sp_help_job (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen zu Aufträgen zurück, mit denen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent automatisierte Aktivitäten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausführt.  
  
 
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_job { [ @job_id = ] job_id  
[ @job_name = ] 'job_name' }   
     [ , [ @job_aspect = ] 'job_aspect' ]   
     [ , [ @job_type = ] 'job_type' ]   
     [ , [ @owner_login_name = ] 'login_name' ]   
     [ , [ @subsystem = ] 'subsystem' ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @enabled = ] enabled ]   
     [ , [ @execution_status = ] status ]   
     [ , [ @date_comparator = ] 'date_comparison' ]   
     [ , [ @date_created = ] date_created ]   
     [ , [ @date_last_modified = ] date_modified ]   
     [ , [ @description = ] 'description_pattern' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id` Die Auftrags-ID. *job_id* ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Zum Anzeigen eines bestimmten Auftrags muss entweder *job_id* oder *job_name* angegeben werden.  Lassen Sie sowohl *job_id* als auch *job_name* aus, um Informationen zu allen Aufträgen zurückzugeben.
  
`[ @job_aspect = ] 'job_aspect'` Das anzuzeigende Auftrags Attribut. *job_aspect* ist vom Datentyp **varchar (9)** und hat den Standardwert NULL. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**ALL**|Auftragsaspektinformationen|  
|**Auftrag**|Auftragsinformationen|  
|**Prüf**|Zeitplaninformationen|  
|**Nehmen**|Auftragsschrittinformationen|  
|**Lern**|Zielinformationen|  
  
`[ @job_type = ] 'job_type'` Der Typ der Aufträge, die in den Bericht eingeschlossen werden sollen. *job_type* ist vom Datentyp **varchar (12)** und hat den Standardwert NULL. *job_type* kann " **local** " oder " **MultiServer**" sein.  
  
`[ @owner_login_name = ] 'login_name'` Der Anmelde Name des Besitzers des Auftrags. *login_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @subsystem = ] 'subsystem'` Der Name des Subsystems. *Subsystem* ist vom Datentyp **nvarchar (40)** und hat den Standardwert NULL.  
  
`[ @category_name = ] 'category'` Der Name der Kategorie. *Category* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @enabled = ] enabled` Eine Zahl, die angibt, ob Informationen für aktivierte oder deaktivierte Aufträge angezeigt werden. *aktiviert* ist vom Datentyp **tinyint**. der Standardwert ist NULL. **1** gibt aktivierte Aufträge an, und **0** gibt deaktivierte Aufträge an.  
  
`[ @execution_status = ] status` Der Ausführungs Status für die Aufträge. der *Status* ist vom Datentyp **int**und hat den Standardwert NULL. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|Nur die Aufträge werden zurückgegeben, die sich nicht im Leerlauf befinden oder unterbrochen sind.|  
|**1**|Ausführ.|  
|**2**|Wartet auf Thread|  
|**3**|Zwischen Wiederholungen|  
|**4**|Im Leerlauf.|  
|**5**|Unterbrochen|  
|**7**|Abschlussaktionen werden ausgeführt|  
  
`[ @date_comparator = ] 'date_comparison'` Der Vergleichs Operator, der in Vergleichen von *Date_Created* und *date_modified*verwendet werden soll. *date_comparison* ist vom Typ **char (1)** und kann =, sein \<, or > .  
  
`[ @date_created = ] date_created` Das Datum, an dem der Auftrag erstellt wurde. *Date_Created*ist vom **Datentyp DateTime**und hat den Standardwert NULL.  
  
`[ @date_last_modified = ] date_modified` Das Datum, an dem der Auftrag zuletzt geändert wurde. *date_modified* ist vom **Datentyp DateTime**und hat den Standardwert NULL.  
  
`[ @description = ] 'description_pattern'` Die Beschreibung des Auftrags. *description_pattern* ist vom Datentyp **nvarchar (512)** und hat den Standardwert NULL. *description_pattern* können die SQL Server Platzhalter Zeichen für den Musterabgleich einschließen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn keine Argumente angegeben werden, gibt **sp_help_job** dieses Resultset zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|Eindeutige ID des Auftrags.|  
|**originating_server**|**nvarchar(30)**|Name des Servers, von dem der Auftrag stammt|  
|**name**|**sysname**|Der Name des Auftrags.|  
|**enabled**|**tinyint**|Zeigt an, ob der Auftrag für die Ausführung aktiviert ist.|  
|**description**|**nvarchar(512)**|Die Beschreibung des Auftrags.|  
|**start_step_id**|**int**|ID des Schrittes in dem Auftrag, bei dem die Ausführung beginnen soll.|  
|**category**|**sysname**|Auftragskategorie|  
|**Eigentor**|**sysname**|Auftragsbesitzer|  
|**notify_level_eventlog**|**int**|**Bitmaske** , die anzeigt, unter welchen Umständen ein Benachrichtigungs Ereignis im Microsoft Windows-Anwendungsprotokoll protokolliert werden soll. Einer der folgenden Werte ist möglich:<br /><br /> **0** = Nie<br /><br /> **1** = bei erfolgreicher Auftragsausführung<br /><br /> **2** = Bei Fehlschlagen des Auftrags<br /><br /> **3** = Immer, wenn der Auftrag abgeschlossen ist (unabhängig vom Ergebnis des Auftrags)|  
|**notify_level_email**|**int**|**Bitmaske** , die anzeigt, unter welchen Umständen bei Abschluss eines Auftrags eine Benachrichtigungs-e-Mail gesendet werden soll Mögliche Werte sind die gleichen wie für **notify_level_eventlog**.|  
|**notify_level_netsend**|**int**|**Bitmaske** , die anzeigt, unter welchen Umständen bei Abschluss eines Auftrags eine Netzwerk Meldung gesendet werden soll. Mögliche Werte sind die gleichen wie für **notify_level_eventlog**.|  
|**notify_level_page**|**int**|**Bitmaske** , die anzeigt, unter welchen Umständen eine Seite gesendet werden soll, wenn ein Auftrag abgeschlossen ist. Mögliche Werte sind die gleichen wie für **notify_level_eventlog**.|  
|**notify_email_operator**|**sysname**|E-Mail-Name des Operators, der benachrichtigt werden soll.|  
|**notify_netsend_operator**|**sysname**|Name des Computers oder Benutzers, der beim Senden von Netzwerkmeldungen verwendet wird|  
|**notify_page_operator**|**sysname**|Name des Computers oder Benutzers, der beim Senden einer Pagerbenachrichtigung verwendet wird|  
|**delete_level**|**int**|**Bitmaske** , die anzeigt, unter welchen Umständen der Auftrag beim Abschließen eines Auftrags gelöscht werden soll. Mögliche Werte sind die gleichen wie für **notify_level_eventlog**.|  
|**date_created**|**datetime**|Datum, an dem der Auftrag erstellt wurde.|  
|**date_modified**|**datetime**|Datum, an dem der Auftrag zuletzt geändert wurde.|  
|**version_number**|**int**|Version des Auftrags (wird automatisch jedes Mal aktualisiert, wenn der Auftrag geändert wird)|  
|**last_run_date**|**int**|Datum, an dem die Ausführung des Auftrags zuletzt gestartet wurde|  
|**last_run_time**|**int**|Uhrzeit, zu der die Ausführung des Auftrags zuletzt gestartet wurde|  
|**last_run_outcome**|**int**|Ergebnis des Auftrags beim letzten ausführen:<br /><br /> **0** = fehlgeschlagen<br /><br /> **1** = erfolgreich<br /><br /> **3** = abgebrochen<br /><br /> **5** = unbekannt|  
|**next_run_date**|**int**|Datum, für das die nächste Ausführung des Auftrags geplant ist|  
|**next_run_time**|**int**|Uhrzeit, zu der die nächste Ausführung des Auftrags geplant ist|  
|**next_run_schedule_id**|**int**|Zeitplan-ID für nächste Ausführung|  
|**current_execution_status**|**int**|Aktueller Ausführungs Status:<br /><br /> **1** = wird ausgeführt<br /><br /> **2** = warten auf Thread<br /><br /> **3** = zwischen Wiederholungen<br /><br /> **4** = im Leerlauf<br /><br /> **5** = angehalten<br /><br /> **6** = veraltet<br /><br /> **7** = performingcompletionactions|  
|**current_execution_step**|**sysname**|Aktueller Ausführungsschritt des Auftrags|  
|**current_retry_attempt**|**int**|Wenn der Auftrag ausgeführt wird und der Schritt wiederholt wurde, ist dies der aktuelle Wiederholungsversuch|  
|**has_step**|**int**|Anzahl der Auftragsschritte des Auftrags|  
|**has_schedule**|**int**|Anzahl der Auftragszeitpläne des Auftrags|  
|**has_target**|**int**|Die Anzahl der Zielserver des Auftrags.|  
|**type**|**int**|Auftragstyp:<br /><br /> 1 = Lokaler Auftrag<br /><br /> **2** = Multiserverauftrag.<br /><br /> **0** = Auftrag hat keine Zielserver.|  
  
 Wenn *job_id* oder *job_name* angegeben ist, gibt **sp_help_job** diese zusätzlichen Resultsets für Auftrags Schritte, Auftrags Zeitpläne und Auftrags Zielserver zurück.  
  
 Im Folgenden wird das Resultset für Auftragsschritte aufgeführt.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**step_id**|**int**|Eindeutiger Bezeichner (für diesen Auftrag) für den Schritt|  
|**step_name**|**sysname**|Name des Schritts|  
|**System**|**nvarchar(40)**|Subsystem, in dem der Schrittbefehl ausgeführt werden soll|  
|**command**|**nvarchar (3200)**|Auszuführender Befehl|  
|**flags**|**nvarchar(4000)**|**Bitmaske** der Werte, die das Schritt Verhalten steuern.|  
|**cmdexec_success_code**|**int**|Bei einem **CmdExec** -Schritt ist dies der Prozessexitcode eines erfolgreichen Befehls.|  
|**on_success_action**|**nvarchar(4000)**|Mögliche Aktionen, wenn der Schritt erfolgreich durchgeführt wird:<br /><br /> **1** = beenden mit Erfolg.<br /><br /> **2** = beenden mit Fehler.<br /><br /> **3** = fahren Sie mit dem nächsten Schritt fort.<br /><br /> **4** = gehe zu Schritt.|  
|**on_success_step_id**|**int**|Wenn **on_success_action** **4**ist, gibt dies den nächsten Schritt an, der ausgeführt werden soll.|  
|**on_fail_action**|**nvarchar(4000)**|Auszuführende Aktion, wenn der Schritt einen Fehler erzeugt. Werte sind identisch mit denen für **on_success_action**.|  
|**on_fail_step_id**|**int**|Wenn **on_fail_action** **4**ist, gibt dies den nächsten Schritt an, der ausgeführt werden soll.|  
|**server**|**sysname**|Reserviert.|  
|**database_name**|**sysname**|Für einen [!INCLUDE[tsql](../../includes/tsql-md.md)] Schritt ist dies die Datenbank, in der der Befehl ausgeführt wird.|  
|**database_user_name**|**sysname**|Für einen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Schritt ist dies der Datenbank-Benutzerkontext, in dem der Befehl ausgeführt wird.|  
|**retry_attempts**|**int**|Die maximale Anzahl von Wiederholungsversuchen für den Befehl (falls er nicht erfolgreich ist), bevor der Schritt als fehlgeschlagen angesehen wird|  
|**retry_interval**|**int**|Das Intervall (in Minuten) zwischen den Wiederholungsversuchen|  
|**os_run_priority**|**varchar (4000)**|Reserviert.|  
|**output_file_name**|**varchar (200)**|Die Datei, in die die Befehlsausgabe geschrieben werden soll ( [!INCLUDE[tsql](../../includes/tsql-md.md)] nur die **CmdExec** -Schritte).|  
|**last_run_outcome**|**int**|Ergebnis der letzten Ausführung des Schritts:<br /><br /> **0** = fehlgeschlagen<br /><br /> **1** = erfolgreich<br /><br /> **3** = abgebrochen<br /><br /> **5** = unbekannt|  
|**last_run_duration**|**int**|Die Ausführungsdauer (in Sekunden) des Schritts bei der letzten Ausführung.|  
|**last_run_retries**|**int**|Anzahl der Wiederholungsversuche für den Befehl bei der letzten Ausführung des Schritts|  
|**last_run_date**|**int**|Datum, an dem die Ausführung des Schritts zuletzt gestartet wurde|  
|**last_run_time**|**int**|Uhrzeit, zu der die Ausführung des Schritts zuletzt gestartet wurde|  
|**proxy_id**|**int**|Proxy für den Auftragsschritt.|  
  
 Im Folgenden wird das Resultset für Auftragszeitpläne aufgeführt.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|Bezeichner des Zeitplans (eindeutig für alle Aufträge)|  
|**schedule_name**|**sysname**|Name des Zeitplans (eindeutig nur für diesen Auftrag)|  
|**enabled**|**int**|Gibt an, ob der Zeitplan aktiv (**1**) oder nicht (**0**) ist.|  
|**freq_type**|**int**|Zeigt an, wann der Auftrag ausgeführt werden soll:<br /><br /> **1** = einmal<br /><br /> **4** = täglich<br /><br /> **8** = wöchentlich<br /><br /> **16** = monatlich<br /><br /> **32** = monatlich, relativ zum **freq_interval**<br /><br /> **64** = ausführen, wenn der **SQLServerAgent** -Dienst gestartet wird.|  
|**freq_interval**|**int**|Tage, an denen der Auftrag ausgeführt wird. Der Wert hängt vom Wert **freq_type**ab. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_type**|**Int**|Einheiten für **freq_subday_interval**. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_interval**|**int**|Anzahl der **freq_subday_type** Zeiträume zwischen den einzelnen Ausführungen des Auftrags. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_relative_interval**|**int**|Das Vorkommen des **freq_interval** eines geplanten Auftrags in jedem Monat. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_recurrence_factor**|**int**|Anzahl der Monate zwischen der geplanten Ausführung des Auftrags|  
|**active_start_date**|**int**|Datum, an dem die Ausführung des Auftrags beginnen soll|  
|**active_end_date**|**int**|Datum, an dem die Ausführung des Auftrags beendet werden soll|  
|**active_start_time**|**int**|Uhrzeit, zu der die Ausführung des Auftrags auf **active_start_date** gestartet werden soll.|  
|**active_end_time**|**int**|Die Zeit bis zum Ende der Auftragsausführung auf **active_end_date**.|  
|**date_created**|**datetime**|Datum, an dem der Zeitplan erstellt wird|  
|**schedule_description**|**nvarchar(4000)**|Eine Beschreibung des Zeitplans in englischer Sprache (falls angefordert).|  
|**next_run_date**|**int**|Datum, an dem der Zeitplan die nächste Ausführung des Auftrags bewirken wird|  
|**next_run_time**|**int**|Uhrzeit, zu der der Zeitplan die nächste Ausführung des Auftrags bewirken wird|  
|**schedule_uid**|**uniqueidentifier**|Bezeichner für den Zeitplan.|  
|**job_count**|**int**|Gibt die Anzahl Aufträge zurück, die auf diesen Zeitplan verweisen|  
  
 Im Folgenden wird das Resultset für Auftragszielserver aufgeführt.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Bezeichner des Zielservers|  
|**server_name**|**nvarchar(30)**|Computername des Zielservers|  
|**enlist_date**|**datetime**|Datum, an dem der Zielserver auf dem Masterserver eingetragen wurde|  
|**last_poll_date**|**datetime**|Datum, an dem der Zielserver den Masterserver zuletzt abgerufen hat|  
|**last_run_date**|**int**|Datum, an dem die Ausführung des Auftrags auf diesem Zielserver zuletzt gestartet wurde|  
|**last_run_time**|**int**|Uhrzeit, zu der die Ausführung des Auftrags auf diesem Zielserver zuletzt gestartet wurde|  
|**last_run_duration**|**int**|Dauer des Auftrags bei der letzten Ausführung auf diesem Zielserver|  
|**last_run_outcome**|**tinyint**|Ergebnis des Auftrags bei der letzten Ausführung auf diesem Server:<br /><br /> **0** = fehlgeschlagen<br /><br /> **1** = erfolgreich<br /><br /> **3** = abgebrochen<br /><br /> **5** = unbekannt|  
|**last_outcome_message**|**nvarchar(1024)**|Ergebnismeldung des Auftrags bei der letzten Ausführung auf diesem Zielserver|  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Mitglieder von **SQLAgentUserRole** können nur Aufträge anzeigen, deren Besitzer Sie sind. Mitglieder von **sysadmin**, **SQLAgentReaderRole**und **SQLAgentOperatorRole** können alle lokalen und Multiserveraufträge anzeigen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-list-information-for-all-jobs"></a>A. Auflisten von Informationen für alle Aufträge  
 Das folgende Beispiel führt die `sp_help_job`-Prozedur ohne Parameter aus, um Informationen für alle aktuell in der `msdb`-Datenbank definierten Aufträge zurückzugeben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job ;  
GO  
```  
  
### <a name="b-listing-information-for-jobs-matching-a-specific-criteria"></a>B. Auflisten von Informationen für Aufträge, die ein bestimmtes Kriterium erfüllen  
 Im folgenden Beispiel werden Auftragsinformationen für die Multiserveraufträge im Besitz von `françoisa` aufgelistet, wenn der Auftrag aktiviert und ausgeführt wird.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job   
   @job_type = N'MULTI-SERVER',  
   @owner_login_name = N'françoisa',  
   @enabled = 1,  
   @execution_status = 1 ;  
GO  
```  
  
### <a name="c-listing-all-aspects-of-information-for-a-job"></a>C. Auflisten aller Aspekte der Informationen für einen Auftrag  
 Im folgenden Beispiel werden alle Aspekte der Informationen für den Auftrag `NightlyBackups` aufgelistet.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job  
    @job_name = N'NightlyBackups',  
    @job_aspect = N'ALL' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
