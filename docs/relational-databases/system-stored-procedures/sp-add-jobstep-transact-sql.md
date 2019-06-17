---
title: Sp_add_jobstep (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_jobstep_TSQL
- sp_add_jobstep
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_jobstep
ms.assetid: 97900032-523d-49d6-9865-2734fba1c755
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 112afe8f7a8eaea87c860264c820c874788cbc7f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66500360"
---
# <a name="spaddjobstep-transact-sql"></a>sp_add_jobstep (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Fügen einem Auftrag einen Schritt (Vorgang) hinzu.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```
sp_add_jobstep [ @job_id = ] job_id | [ @job_name = ] 'job_name'   
     [ , [ @step_id = ] step_id ]   
     { , [ @step_name = ] 'step_name' }   
     [ , [ @subsystem = ] 'subsystem' ]   
     [ , [ @command = ] 'command' ]   
     [ , [ @additional_parameters = ] 'parameters' ]   
          [ , [ @cmdexec_success_code = ] code ]   
     [ , [ @on_success_action = ] success_action ]   
          [ , [ @on_success_step_id = ] success_step_id ]   
          [ , [ @on_fail_action = ] fail_action ]   
          [ , [ @on_fail_step_id = ] fail_step_id ]   
     [ , [ @server = ] 'server' ]   
     [ , [ @database_name = ] 'database' ]   
     [ , [ @database_user_name = ] 'user' ]   
     [ , [ @retry_attempts = ] retry_attempts ]   
     [ , [ @retry_interval = ] retry_interval ]   
     [ , [ @os_run_priority = ] run_priority ]   
     [ , [ @output_file_name = ] 'file_name' ]   
     [ , [ @flags = ] flags ]   
     [ , { [ @proxy_id = ] proxy_id   
         | [ @proxy_name = ] 'proxy_name' } ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id` Die ID des Auftrags, dem den Schritt hinzugefügt werden soll. *Job_id* ist **Uniqueidentifier**, hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags, dem den Schritt hinzugefügt. *Job_name* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Entweder *Job_id* oder *Job_name* muss angegeben werden, aber beide Angaben sind nicht möglich.  
  
`[ @step_id = ] step_id` Die Sequenz-ID für den Auftragsschritt. Schritt-IDs beginnen bei **1** und lückenlos erhöht. Wenn ein Schritt in eine vorhandene Sequenz eingefügt wird, werden die Sequenznummern automatisch angepasst. Ein Wert angegeben wird, wenn *Step_id* nicht angegeben ist. *Step_id* ist **Int**, hat den Standardwert NULL.  
  
`[ @step_name = ] 'step_name'` Der Name des Schritts. *Step_name* ist **Sysname**, hat keinen Standardwert.  
  
`[ @subsystem = ] 'subsystem'` Das Subsystem ein, die die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zum Ausführen *Befehl*. *Subsystem* ist **nvarchar(40)** , und kann einen der folgenden Werte sein.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|"**ACTIVESCRIPTING**"|Active Script<br /><br /> **\*\* Wichtig \*\*** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|  
|"**CMDEXEC**"|Betriebssystembefehl oder ausführbares Programm|  
|"**VERTEILUNG**"|Auftrag des Replikationsverteilungs-Agents|  
|"**MOMENTAUFNAHME**"|Auftrag des Replikationsmomentaufnahme-Agents|  
|"**PROTOKOLLLESER**"|Auftrag des Replikationsprotokolllese-Agents|  
|"**MERGE**"|Auftrag des Replikationsmerge-Agents|  
|'**QueueReader**'|Warteschlangenlese-Agent-Auftrag der Replikation|  
|"**DAS ANALYSISQUERY**"|Analysis Services-Abfrage (MDX, DMX)|  
|"**DAS ANALYSISCOMMAND**"|Analysis Services-Befehl (XMLA)|  
|"**Dts**"|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paketausführung|  
|"**PowerShell**"|PowerShell-Skript|  
|"**TSQL**" (Standard)|[!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung|  
  
`[ @command = ] 'command'` Die Befehle ausgeführt werden soll **SQLServerAgent** -Dienst über *Subsystem*. *Befehl* ist **nvarchar(max)** , hat den Standardwert NULL. Vom SQL Server-Agent wird eine Tokenersetzung bereitgestellt, die Ihnen beim Schreiben von Softwareprogrammen dieselbe Flexibilität wie Variablen bietet.  
  
> [!IMPORTANT]  
>  Damit Auftragsschritte fehlerfrei ausgeführt werden können, müssen alle in Auftragsschritten verwendeten Token von einem Escapemakro begleitet werden. Darüber hinaus müssen Sie Tokennamen nun in runde Klammern einschließen und ein Dollarzeichen (`$`) an den Anfang der Tokensyntax setzen. Zum Beispiel:  
>   
>  `$(ESCAPE_` *Makroname* `(DATE))`  
  
 Weitere Informationen zu diesen Token und Aktualisieren der Auftragsschritte verwenden Sie die neue Tokensyntax finden Sie unter [Verwenden von Token in Auftragsschritten](../../ssms/agent/use-tokens-in-job-steps.md).  
  
> [!IMPORTANT]  
>  Jeder Windows-Benutzer mit Schreibberechtigungen für das Windows-Ereignisprotokoll kann auf Auftragsschritte zugreifen, die durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Warnungen oder WMI-Warnungen aktiviert werden. Zur Vermeidung dieses Sicherheitsrisikos sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Tokens, die in von Warnungen aktivierten Aufträgen verwendet werden können, standardmäßig deaktiviert. Dabei handelt es sich um folgende Token: **A-DBN**, **A-SVR**, **A-ERR**, **A-SEV**, **A-MSG** und **WMI(** _Eigenschaft_ **)** . Beachten Sie, dass in dieser Version die Verwendung von Token auf alle Warnungen ausgeweitet ist.  
>   
>  Wenn Sie diese Token verwenden müssen, stellen Sie zuvor sicher, dass ausschließlich Mitglieder von vertrauenswürdigen Windows-Sicherheitsgruppen, wie der Administratorengruppe, über Schreibberechtigungen für das Ereignisprotokoll des Computers verfügen, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird. Klicken Sie dann zum Aktivieren dieser Token im Objekt-Explorer mit der rechten Maustaste auf **SQL Server-Agent** , wählen Sie **Eigenschaften**, und wählen Sie anschließend auf der Seite **Warnungssystem** die Option **Token für alle Auftragsantworten auf Warnungen ersetzen** aus.  
  
`[ @additional_parameters = ] 'parameters'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *Parameter* ist **Ntext**, hat den Standardwert NULL.  
  
`[ @cmdexec_success_code = ] code` Der Rückgabewert von einer **CmdExec** -Subsystembefehl an, dass *Befehl* erfolgreich ausgeführt wurde. *Code* ist **Int**, hat den Standardwert **0**.  
  
`[ @on_success_action = ] success_action` Die Aktion ausführen, wenn der Schritt erfolgreich ist. *Success_action* ist **Tinyint**, und kann einen der folgenden Werte sein.  
  
|Wert|Beschreibung (Aktion)|  
|-----------|----------------------------|  
|**1** (Standard)|Beenden mit Erfolg|  
|**2**|Beenden mit Fehler|  
|**3**|Zum nächsten Schritt wechseln|  
|**4**|Wechseln Sie zu Schritt *On_success_step_id*|  
  
`[ @on_success_step_id = ] success_step_id` Die ID des Schritts in diesem Auftrag ausgeführt wird, wenn der Schritt erfolgreich ausgeführt wird und *Success_action* ist **4**. *Success_step_id* ist **Int**, hat den Standardwert **0**.  
  
`[ @on_fail_action = ] fail_action` Die Aktion, wenn der Schritt ein Fehler auftritt. *fail_action gleich* ist **Tinyint**, und kann einen der folgenden Werte sein.  
  
|Wert|Beschreibung (Aktion)|  
|-----------|----------------------------|  
|**1**|Beenden mit Erfolg|  
|**2** (Standardwert)|Beenden mit Fehler|  
|**3**|Zum nächsten Schritt wechseln|  
|**4**|Wechseln Sie zu Schritt *On_fail_step_id*|  
  
`[ @on_fail_step_id = ] fail_step_id` Die ID des Schritts in diesem Auftrag ausgeführt wird, wenn der Schritt fehlschlägt und *fail_action gleich* ist **4**. *Fail_step_id* ist **Int**, hat den Standardwert **0**.  
  
`[ @server = ] 'server'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *Server* ist **nvarchar(30)** , hat den Standardwert NULL.  
  
`[ @database_name = ] 'database'` Der Name der Datenbank, in der zum Ausführen einer [!INCLUDE[tsql](../../includes/tsql-md.md)] Schritt. *Datenbank* ist **Sysname**, hat den Standardwert NULL. der Wert in diesem Fall die **master** Datenbank verwendet wird. In eckige Klammern ([ ]) eingeschlossene Namen sind nicht zulässig. Für ein ActiveX-Auftragsschritt der *Datenbank* ist der Name der Skriptsprache, die der Schritt verwendet.  
  
`[ @database_user_name = ] 'user'` Der Name des Benutzerkontos ein, verwenden Sie beim Ausführen einer [!INCLUDE[tsql](../../includes/tsql-md.md)] Schritt. *Benutzer* ist **Sysname**, hat den Standardwert NULL. Wenn *Benutzer* NULL ist, wird die in einem Benutzerkontext des Auftragsbesitzers auf *Datenbank*.  SQL Server-Agent schließt nur diesen Parameter ein, wenn der Auftragsbesitzer ein SQL Server sysadmin ist. In diesem Fall wird der angegebene Transact-SQL-Schritt im Kontext des angegebenen SQL Server-Benutzernamens ausgeführt. Wenn der Besitzer des Auftrags ist kein der Rolle Sysadmin SQL Server, der Transact-SQL-Schritt immer im Kontext der Anmeldung, die diesen Auftrag besitzt ausgeführt und die @database_user_name Parameter wird ignoriert.  
  
`[ @retry_attempts = ] retry_attempts` Die Anzahl der Wiederholungsversuche verwenden, wenn dieser Schritt fehlschlägt. *Retry_attempts* ist **Int**, hat den Standardwert **0**, die keine Wiederholungsversuche.  
  
`[ @retry_interval = ] retry_interval` Die Zeitspanne in Minuten zwischen den Wiederholungsversuchen. *Retry_interval* ist **Int**, hat den Standardwert **0**, womit eine **0**-Minuten-Intervall.  
  
`[ @os_run_priority = ] run_priority` Reserviert.  
  
`[ @output_file_name = ] 'file_name'` Der Name der Datei, in der die Ausgabe dieses Schritts gespeichert wird. *File_name* ist **nvarchar(200)-Datentyp gepackt ist**, hat den Standardwert NULL. *File_name* kann eine oder mehrere der unter aufgeführten Token enthalten *Befehl*. Dieser Parameter gilt nur mit Befehlen, die unter der [!INCLUDE[tsql](../../includes/tsql-md.md)], **CmdExec**, **PowerShell**, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], oder [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Subsysteme.  
  
`[ @flags = ] flags` Ist eine Option, die Verhalten steuert. *Flags* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0** (Standardwert)|Ausgabedatei überschreiben|  
|**2**|An Ausgabedatei anfügen|  
|**4**|Ausgabe des [!INCLUDE[tsql](../../includes/tsql-md.md)]-Auftragsschritts in Schrittverlauf schreiben|  
|**8**|Protokoll in Tabelle schreiben (vorhandenen Verlauf überschreiben)|  
|**16**|Protokoll in Tabelle schreiben (an vorhandenen Verlauf anfügen)|  
|**32**|Schreiben der gesamten Ausgabe in den Auftragsverlauf|  
|**64**|Erstellen eines Windows-Ereignisses, das für den Cmd-Jobstep als Signal als Signal zum Abbruch verwendet werden soll|  
  
`[ @proxy_id = ] proxy_id` Die ID des Proxys, der der Auftragsschritt ausgeführt wird. *Proxy_id* Typ **Int**, hat den Standardwert NULL. Wenn kein *Proxy_id* angegeben ist, kein *Proxy_name* angegeben ist, und es wird kein *User_name* angegeben ist, wird der Auftragsschritt ausgeführt wird, als das Dienstkonto für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
`[ @proxy_name = ] 'proxy_name'` Der Name des Proxys, der der Auftragsschritt ausgeführt wird. *Proxy_name* Typ **Sysname**, hat den Standardwert NULL. Wenn kein *Proxy_id* angegeben ist, kein *Proxy_name* angegeben ist, und es wird kein *User_name* angegeben ist, wird der Auftragsschritt ausgeführt wird, als das Dienstkonto für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 **Sp_add_jobstep** muss ausgeführt werden, aus der **Msdb** Datenbank.  
  
 SQL Server Management Studio bietet eine einfache grafische Möglichkeit zum Verwalten von Aufträgen. Es handelt sich hierbei um die empfohlene Art und Weise zum Erstellen und Verwalten der Auftragsinfrastruktur.  
  
 Ein Auftragsschritt muss ein Proxy angegeben, es sei denn, der Ersteller des Auftragsschritts Mitglied ist die **Sysadmin** festen Sicherheitsrolle.  
  
 Ein Proxy kann identifiziert werden *Proxy_name* oder *Proxy_id*.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Der Ersteller des Auftragsschritts muss Zugriff auf den für den Auftragsschritt verwendeten Proxy haben. Mitglieder der **Sysadmin** -Serverrolle haben Zugriff auf alle Proxys. Anderen Benutzern muss der Zugriff auf einen Proxy explizit erteilt werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Auftragsschritt erstellt, der für die Sales-Datenbank den Schreibschutz aktiviert. Zudem werden in diesem Beispiel 5 Wiederholungsversuche festgelegt, wobei jede Wiederholung nach einer Wartezeit von 5 Minuten auftritt.  
  
> [!NOTE]  
>  In diesem Beispiel wird vorausgesetzt, dass die `Weekly Sales Data Backup` Auftrag ist bereits vorhanden.  
  
```sql
USE msdb;  
GO  
EXEC sp_add_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_name = N'Set database to read only',  
    @subsystem = N'TSQL',  
    @command = N'ALTER DATABASE SALES SET READ_ONLY',
    @retry_attempts = 5,  
    @retry_interval = 5 ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen oder Ändern von Aufträgen](../../ssms/agent/view-or-modify-jobs.md)   
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_update_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
