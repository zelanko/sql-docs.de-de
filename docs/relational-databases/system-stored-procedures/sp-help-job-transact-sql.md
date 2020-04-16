---
title: sp_help_job (Transact-SQL) | Microsoft Docs
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 29870a0ffb3d2c3b1872acbb40266aef0d16b62c
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "75546564"
---
# <a name="sp_help_job-transact-sql"></a>sp_help_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
`[ @job_id = ] job_id`Die Projekt-Identifikationsnummer. *job_id* ist **uniqueidentifier**, mit dem Standardwert NULL.  
  
`[ @job_name = ] 'job_name'`Der Name des Auftrags. *job_name* ist **sysname**, mit dem Standardwert NULL.  
  
> [!NOTE]  
>  Um einen bestimmten Auftrag anzuzeigen, müssen *entweder job_id* oder *job_name* angegeben werden.  Lassen Sie sowohl *job_id als* auch *job_name,* um Informationen über alle Aufträge zurückzugeben.
  
`[ @job_aspect = ] 'job_aspect'`Das anzuzeigende auftragsattribut. *job_aspect* ist **varchar(9)**, mit dem Standardwert NULL, und kann einer dieser Werte sein.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Alle**|Auftragsaspektinformationen|  
|**Job**|Auftragsinformationen|  
|**Zeitpläne**|Zeitplaninformationen|  
|**Schritte**|Auftragsschrittinformationen|  
|**Ziele**|Zielinformationen|  
  
`[ @job_type = ] 'job_type'`Die Art der Einzelvorgänge, die in den Bericht aufgenommen werden sollen. *job_type* ist **varchar(12)**, mit dem Standardwert NULL. *job_type* können **LOCAL** oder **MULTI-SERVER**sein.  
  
`[ @owner_login_name = ] 'login_name'`Der Anmeldename des Besitzers des Auftrags. *login_name* ist **sysname**, mit dem Standardwert NULL.  
  
`[ @subsystem = ] 'subsystem'`Der Name des Subsystems. *subsystem* ist **nvarchar(40)**, mit dem Standardwert NULL.  
  
`[ @category_name = ] 'category'`Der Name der Kategorie. *Kategorie* ist **sysname**, mit dem Standardwert NULL.  
  
`[ @enabled = ] enabled`Eine Zahl, die angibt, ob Informationen für aktivierte oder deaktivierte Aufträge angezeigt werden. *aktiviert* ist **tinyint**mit dem Standardwert NULL. **1** gibt aktivierte Aufträge an, und **0** gibt deaktivierte Aufträge an.  
  
`[ @execution_status = ] status`Der Ausführungsstatus für die Aufträge. *status* ist **int**, mit dem Standardwert NULL, und kann einer dieser Werte sein.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**0**|Nur die Aufträge werden zurückgegeben, die sich nicht im Leerlauf befinden oder unterbrochen sind.|  
|**1**|Ausführen.|  
|**2**|Wartet auf Thread|  
|**3**|Zwischen Wiederholungen|  
|**4**|Im Leerlauf.|  
|**5**|Unterbrochen|  
|**7**|Abschlussaktionen werden ausgeführt|  
  
`[ @date_comparator = ] 'date_comparison'`Der Vergleichsoperator, der in Vergleichen von *date_created* und *date_modified*verwendet werden soll. *date_comparison* ist **char(1)** und kann \<=, oder > sein.  
  
`[ @date_created = ] date_created`Das Datum, an dem der Einzelvorgang erstellt wurde. *date_created*ist **datetime**, mit dem Standardwert NULL.  
  
`[ @date_last_modified = ] date_modified`Das Datum, an dem der Einzelvorgang zuletzt geändert wurde. *date_modified* ist **datetime**, mit dem Standardwert NULL.  
  
`[ @description = ] 'description_pattern'`Die Beschreibung des Auftrags. *description_pattern* ist **nvarchar(512)**, mit dem Standardwert NULL. *description_pattern* können die SQL Server-Platzhalterzeichen für den Musterabgleich enthalten.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn keine Argumente angegeben werden, **gibt sp_help_job** dieses Resultset zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Job_id**|**UNIQUEIDENTIFIER**|Eindeutige ID des Auftrags.|  
|**originating_server**|**nvarchar(30)**|Name des Servers, von dem der Auftrag stammt|  
|**name**|**Sysname**|Der Name des Auftrags.|  
|**Aktiviert**|**TINYINT**|Zeigt an, ob der Auftrag für die Ausführung aktiviert ist.|  
|**Beschreibung**|**nvarchar(512)**|Die Beschreibung des Auftrags.|  
|**start_step_id**|**int**|ID des Schrittes in dem Auftrag, bei dem die Ausführung beginnen soll.|  
|**category**|**Sysname**|Auftragskategorie|  
|**Besitzer**|**Sysname**|Auftragsbesitzer|  
|**notify_level_eventlog**|**int**|**Bitmaske,** die angibt, unter welchen Umständen ein Benachrichtigungsereignis im Microsoft Windows-Anwendungsprotokoll protokolliert werden soll. Einer der folgenden Werte ist möglich:<br /><br /> **0** = Nie<br /><br /> **1** = Wenn ein Auftrag erfolgreich ist<br /><br /> **2** = Bei Fehlschlagen des Auftrags<br /><br /> **3** = Immer, wenn der Auftrag abgeschlossen ist (unabhängig vom Ergebnis des Auftrags)|  
|**notify_level_email**|**int**|**Bitmaske,** die angibt, unter welchen Umständen eine Benachrichtigungs-E-Mail gesendet werden soll, wenn ein Auftrag abgeschlossen ist. Mögliche Werte sind die gleichen wie für **notify_level_eventlog**.|  
|**notify_level_netsend**|**int**|**Bitmaske,** die angibt, unter welchen Umständen eine Netzwerknachricht gesendet werden soll, wenn ein Auftrag abgeschlossen ist. Mögliche Werte sind die gleichen wie für **notify_level_eventlog**.|  
|**notify_level_page**|**int**|**Bitmaske,** die angibt, unter welchen Umständen eine Seite gesendet werden soll, wenn ein Auftrag abgeschlossen ist. Mögliche Werte sind die gleichen wie für **notify_level_eventlog**.|  
|**notify_email_operator**|**Sysname**|E-Mail-Name des Operators, der benachrichtigt werden soll.|  
|**notify_netsend_operator**|**Sysname**|Name des Computers oder Benutzers, der beim Senden von Netzwerkmeldungen verwendet wird|  
|**notify_page_operator**|**Sysname**|Name des Computers oder Benutzers, der beim Senden einer Pagerbenachrichtigung verwendet wird|  
|**delete_level**|**int**|**Bitmaske,** die angibt, unter welchen Umständen der Auftrag gelöscht werden soll, wenn ein Auftrag abgeschlossen wird. Mögliche Werte sind die gleichen wie für **notify_level_eventlog**.|  
|**date_created**|**datetime**|Datum, an dem der Auftrag erstellt wurde.|  
|**date_modified**|**datetime**|Datum, an dem der Auftrag zuletzt geändert wurde.|  
|**version_number**|**int**|Version des Auftrags (wird automatisch jedes Mal aktualisiert, wenn der Auftrag geändert wird)|  
|**last_run_date**|**int**|Datum, an dem die Ausführung des Auftrags zuletzt gestartet wurde|  
|**last_run_time**|**int**|Uhrzeit, zu der die Ausführung des Auftrags zuletzt gestartet wurde|  
|**last_run_outcome**|**int**|Ergebnis des Auftrags beim letzten Liefer:<br /><br /> **0** = Fehlgeschlagen<br /><br /> **1** = Erfolgreich<br /><br /> **3** = Abgebrochen<br /><br /> **5** = Unbekannt|  
|**next_run_date**|**int**|Datum, für das die nächste Ausführung des Auftrags geplant ist|  
|**next_run_time**|**int**|Uhrzeit, zu der die nächste Ausführung des Auftrags geplant ist|  
|**next_run_schedule_id**|**int**|Zeitplan-ID für nächste Ausführung|  
|**current_execution_status**|**int**|Aktueller Ausführungsstatus:<br /><br /> **1** = Ausführen<br /><br /> **2** = Warten auf Gewinde<br /><br /> **3** = Zwischen Wiederholungen<br /><br /> **4** = Leerlauf<br /><br /> **5** = Ausgesetzt<br /><br /> **6** = Veraltet<br /><br /> **7** = Durchführen von Vervollständigungsaktionen|  
|**current_execution_step**|**Sysname**|Aktueller Ausführungsschritt des Auftrags|  
|**current_retry_attempt**|**int**|Wenn der Auftrag ausgeführt wird und der Schritt wiederholt wurde, ist dies der aktuelle Wiederholungsversuch|  
|**has_step**|**int**|Anzahl der Auftragsschritte des Auftrags|  
|**has_schedule**|**int**|Anzahl der Auftragszeitpläne des Auftrags|  
|**has_target**|**int**|Die Anzahl der Zielserver des Auftrags.|  
|**type**|**int**|Auftragstyp:<br /><br /> 1 = Lokaler Auftrag<br /><br /> **2** = Multiserver-Auftrag.<br /><br /> **0** = Auftrag hat keine Zielserver.|  
  
 Wenn *job_id* oder *job_name* angegeben ist, **gibt sp_help_job** diese zusätzlichen Ergebnissätze für Auftragsschritte, Auftragszeitpläne und Auftragszielserver zurück.  
  
 Im Folgenden wird das Resultset für Auftragsschritte aufgeführt.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**step_id**|**int**|Eindeutiger Bezeichner (für diesen Auftrag) für den Schritt|  
|**step_name**|**Sysname**|Name des Schritts|  
|**Subsystem**|**nvarchar(40)**|Subsystem, in dem der Schrittbefehl ausgeführt werden soll|  
|**Befehl**|**nvarchar(3200)**|Auszuführender Befehl|  
|**Flaggen**|**nvarchar(4000)**|**Bitmaske** von Werten, die das Schrittverhalten steuern.|  
|**cmdexec_success_code**|**int**|Bei einem **CmdExec-Schritt** ist dies der Prozess-Exit-Code eines erfolgreichen Befehls.|  
|**on_success_action**|**nvarchar(4000)**|Mögliche Aktionen, wenn der Schritt erfolgreich durchgeführt wird:<br /><br /> **1** = Beenden Sie mit Erfolg.<br /><br /> **2** = Beenden mit Einem Fehler.<br /><br /> **3** = Gehen Sie zum nächsten Schritt.<br /><br /> **4** = Gehen Sie zu Schritt.|  
|**on_success_step_id**|**int**|Wenn **on_success_action** **4**ist, gibt dies den nächsten auszuführenden Schritt an.|  
|**on_fail_action**|**nvarchar(4000)**|Auszuführende Aktion, wenn der Schritt einen Fehler erzeugt. Die Werte sind die gleichen wie für **on_success_action**.|  
|**on_fail_step_id**|**int**|Wenn **on_fail_action** **4**ist, gibt dies den nächsten auszuführenden Schritt an.|  
|**Server**|**Sysname**|Reserviert.|  
|**database_name**|**Sysname**|Für [!INCLUDE[tsql](../../includes/tsql-md.md)] einen Schritt ist dies die Datenbank, in der der Befehl ausgeführt wird.|  
|**database_user_name**|**Sysname**|Für einen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Schritt ist dies der Datenbank-Benutzerkontext, in dem der Befehl ausgeführt wird.|  
|**retry_attempts**|**int**|Die maximale Anzahl von Wiederholungsversuchen für den Befehl (falls er nicht erfolgreich ist), bevor der Schritt als fehlgeschlagen angesehen wird|  
|**retry_interval**|**int**|Das Intervall (in Minuten) zwischen den Wiederholungsversuchen|  
|**os_run_priority**|**varchar(4000)**|Reserviert.|  
|**output_file_name**|**varchar(200)**|Datei, in die die[!INCLUDE[tsql](../../includes/tsql-md.md)] Befehlsausgabe geschrieben werden soll (und **nur CmdExec-Schritte).**|  
|**last_run_outcome**|**int**|Ergebnis der letzten Ausführung des Schritts:<br /><br /> **0** = Fehlgeschlagen<br /><br /> **1** = Erfolgreich<br /><br /> **3** = Abgebrochen<br /><br /> **5** = Unbekannt|  
|**last_run_duration**|**int**|Die Ausführungsdauer (in Sekunden) des Schritts bei der letzten Ausführung.|  
|**last_run_retries**|**int**|Anzahl der Wiederholungsversuche für den Befehl bei der letzten Ausführung des Schritts|  
|**last_run_date**|**int**|Datum, an dem die Ausführung des Schritts zuletzt gestartet wurde|  
|**last_run_time**|**int**|Uhrzeit, zu der die Ausführung des Schritts zuletzt gestartet wurde|  
|**proxy_id**|**int**|Proxy für den Auftragsschritt.|  
  
 Im Folgenden wird das Resultset für Auftragszeitpläne aufgeführt.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|Bezeichner des Zeitplans (eindeutig für alle Aufträge)|  
|**schedule_name**|**Sysname**|Name des Zeitplans (eindeutig nur für diesen Auftrag)|  
|**Aktiviert**|**int**|Ob der Zeitplan aktiv ist (**1**) oder nicht (**0**).|  
|**freq_type**|**int**|Zeigt an, wann der Auftrag ausgeführt werden soll:<br /><br /> **1** = Einmal<br /><br /> **4** = Täglich<br /><br /> **8** = Wöchentlich<br /><br /> **16** = Monatlich<br /><br /> **32** = Monatlich, bezogen auf die **freq_interval**<br /><br /> **64** = Ausführen, wenn der **SQLServerAgent-Dienst** gestartet wird.|  
|**freq_interval**|**int**|Tage, an denen der Auftrag ausgeführt wird. Der Wert hängt vom Wert **von freq_type ab.** Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_type**|**Int**|Einheiten für **freq_subday_interval**. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_interval**|**int**|Anzahl der **freq_subday_type** Zeiträume zwischen jeder Ausführung des Auftrags. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_relative_interval**|**int**|Geplantes Auftreten des **freq_interval** in jedem Monat. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_recurrence_factor**|**int**|Anzahl der Monate zwischen der geplanten Ausführung des Auftrags|  
|**active_start_date**|**int**|Datum, an dem die Ausführung des Auftrags beginnen soll|  
|**active_end_date**|**int**|Datum, an dem die Ausführung des Auftrags beendet werden soll|  
|**active_start_time**|**int**|Zeit, mit der Ausführung des Auftrags auf active_start_date zu **beginnen.**|  
|**active_end_time**|**int**|Zeit, um die Ausführung des Auftrags auf **active_end_date**zu beenden.|  
|**date_created**|**datetime**|Datum, an dem der Zeitplan erstellt wird|  
|**schedule_description**|**nvarchar(4000)**|Eine Beschreibung des Zeitplans in englischer Sprache (falls angefordert).|  
|**next_run_date**|**int**|Datum, an dem der Zeitplan die nächste Ausführung des Auftrags bewirken wird|  
|**next_run_time**|**int**|Uhrzeit, zu der der Zeitplan die nächste Ausführung des Auftrags bewirken wird|  
|**schedule_uid**|**UNIQUEIDENTIFIER**|Bezeichner für den Zeitplan.|  
|**job_count**|**int**|Gibt die Anzahl Aufträge zurück, die auf diesen Zeitplan verweisen|  
  
 Im Folgenden wird das Resultset für Auftragszielserver aufgeführt.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Bezeichner des Zielservers|  
|**Server_name**|**nvarchar(30)**|Computername des Zielservers|  
|**enlist_date**|**datetime**|Datum, an dem der Zielserver auf dem Masterserver eingetragen wurde|  
|**last_poll_date**|**datetime**|Datum, an dem der Zielserver den Masterserver zuletzt abgerufen hat|  
|**last_run_date**|**int**|Datum, an dem die Ausführung des Auftrags auf diesem Zielserver zuletzt gestartet wurde|  
|**last_run_time**|**int**|Uhrzeit, zu der die Ausführung des Auftrags auf diesem Zielserver zuletzt gestartet wurde|  
|**last_run_duration**|**int**|Dauer des Auftrags bei der letzten Ausführung auf diesem Zielserver|  
|**last_run_outcome**|**TINYINT**|Ergebnis des Auftrags bei der letzten Ausführung auf diesem Server:<br /><br /> **0** = Fehlgeschlagen<br /><br /> **1** = Erfolgreich<br /><br /> **3** = Abgebrochen<br /><br /> **5** = Unbekannt|  
|**last_outcome_message**|**nvarchar(1024)**|Ergebnismeldung des Auftrags bei der letzten Ausführung auf diesem Zielserver|  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der **sysadmin** Fixed Server-Rolle diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Mitglieder von **SQLAgentUserRole** können nur Aufträge anzeigen, die sie besitzen. Member von **sysadmin**, **SQLAgentReaderRole**und **SQLAgentOperatorRole** können alle lokalen und Multiserveraufträge anzeigen.  
  
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
 [sp_add_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
