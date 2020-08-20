---
description: sp_help_jobstep (Transact-SQL)
title: sp_help_jobstep (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobstep_TSQL
- sp_help_jobstep
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobstep
ms.assetid: 4a13b804-45f2-4f82-987f-42d9a57dd6db
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5ef8fab59553fd203129852961ac33d59498467d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464270"
---
# <a name="sp_help_jobstep-transact-sql"></a>sp_help_jobstep (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen zu den Schritten eines Auftrags zurück, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst verwendet, um automatisierte Aktivitäten auszuführen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_jobstep { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]   
     [ , [ @step_name = ] 'step_name' ]   
     [ , [ @suffix = ] suffix ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] 'job_id'` Die ID des Auftrags, für den Auftrags Informationen zurückgegeben werden sollen. *job_id* ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *job_id* oder *job_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @step_id = ] step_id` Die ID des Auftrags Schritts. Wenn diese nicht angegeben wird, sind alle Schritte im Auftrag eingeschlossen. *step_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @step_name = ] 'step_name'` Der Name des Schritts im Auftrag. *step_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @suffix = ] suffix` Ein Flag, das angibt, ob eine Textbeschreibung an die **Flags** -Spalte in der Ausgabe angehängt wird. *Suffix*ist vom Typ **Bit**und hat den Standardwert **0**. Wenn *Suffix* **1**ist, wird eine Beschreibung angehängt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**step_id**|**int**|Eindeutiger Bezeichner für den Schritt.|  
|**step_name**|**sysname**|Name des Auftragsschritts.|  
|**System**|**nvarchar(40)**|Subsystem, in dem der Schrittbefehl ausgeführt werden soll|  
|**command**|**nvarchar(max)**|Befehl, der in dem Schritt ausgeführt wird.|  
|**flags**|**int**|Bitmaske der Werte, die das Schrittverhalten steuern.|  
|**cmdexec_success_code**|**int**|Bei einem **CmdExec** -Schritt ist dies der Prozessexitcode eines erfolgreichen Befehls.|  
|**on_success_action**|**tinyint**|Auszuführende Aktion, wenn der Schritt erfolgreich ist:<br /><br /> **1** = Beenden der Auftrags Erfolgsmeldung.<br /><br /> **2** = beenden Sie den Fehler bei der Auftrags Berichterstattung.<br /><br /> **3** = fahren Sie mit dem nächsten Schritt fort.<br /><br /> **4** = gehe zu Schritt.|  
|**on_success_step_id**|**int**|Wenn **on_success_action** 4 ist, gibt dies den nächsten Schritt an, der ausgeführt werden soll.|  
|**on_fail_action**|**tinyint**|Was Sie tun sollten, wenn der Schritt fehlschlägt. Werte sind identisch mit **on_success_action**.|  
|**on_fail_step_id**|**int**|Wenn **on_fail_action** 4 ist, gibt dies den nächsten Schritt an, der ausgeführt werden soll.|  
|**server**|**sysname**|Reserviert.|  
|**database_name**|**sysname**|Für einen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Schritt ist dies die Datenbank, in der der Befehl ausgeführt wird.|  
|**database_user_name**|**sysname**|Für einen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Schritt ist dies der Datenbank-Benutzerkontext, in dem der Befehl ausgeführt wird.|  
|**retry_attempts**|**int**|Die maximale Anzahl von Wiederholungsversuchen für den Befehl (falls er nicht erfolgreich ist).|  
|**retry_interval**|**int**|Das Intervall (in Minuten) zwischen den Wiederholungsversuchen.|  
|**os_run_priority**|**int**|Reserviert.|  
|**output_file_name**|**nvarchar(200)**|Die Datei, in die die Befehlsausgabe geschrieben werden soll ( [!INCLUDE[tsql](../../includes/tsql-md.md)] nur, **CmdExec**und **PowerShell** -Schritte).|  
|**last_run_outcome**|**int**|Ergebnis der letzten Ausführung des Schritts:<br /><br /> **0** = fehlgeschlagen<br /><br /> **1** = erfolgreich<br /><br /> **2** = Wiederholung<br /><br /> **3** = abgebrochen<br /><br /> **5** = unbekannt|  
|**last_run_duration**|**int**|Dauer (hhmmss) der letzten Ausführung des Schritts.|  
|**last_run_retries**|**int**|Anzahl der Wiederholungsversuche für den Befehl bei der letzten Ausführung des Schritts|  
|**last_run_date**|**int**|Datum, an dem die Ausführung des Schritts zuletzt gestartet wurde|  
|**last_run_time**|**int**|Uhrzeit, zu der die Ausführung des Schritts zuletzt gestartet wurde|  
|**proxy_id**|**int**|Proxy für den Auftragsschritt.|  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_help_jobstep** in der **msdb** -Datenbank.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Mitglieder von **SQLAgentUserRole** können nur Auftrags Schritte für Aufträge anzeigen, deren Besitzer Sie sind.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-return-information-for-all-steps-in-a-specific-job"></a>A. Zurückgeben von Informationen für alle Schritte in einem bestimmten Auftrag  
 Im folgenden Beispiel werden alle Auftragsschritte für den Auftrag `Weekly Sales Data Backup` zurückgegeben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobstep  
    @job_name = N'Weekly Sales Data Backup' ;  
GO  
```  
  
### <a name="b-return-information-about-a-specific-job-step"></a>B. Zurückgeben von Informationen zu einem bestimmten Auftragsschritt  
 Im folgenden Beispiel werden Informationen zum ersten Auftragsschritt des Auftrags `Weekly Sales Data Backup` zurückgegeben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_jobstep &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_update_jobstep &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
