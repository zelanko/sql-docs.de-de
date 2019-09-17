---
title: sp_add_jobstep (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: b679f34e16b0f22018357f3c6fd6a531d283b2bc
ms.sourcegitcommit: df1f71231f8edbdfe76e8851acf653c25449075e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2019
ms.locfileid: "70810538"
---
# <a name="sp_add_jobstep-transact-sql"></a>sp_add_jobstep (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Fügt einem SQL-Agentauftrag einen Schritt (Vorgang) hinzu.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
  > [!IMPORTANT]  
  > Auf [verwaltete Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)werden die meisten, aber nicht alle SQL Server-Agent Auftrags Typen unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).
  
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
`[ @job_id = ] job_id`Die ID des Auftrags, dem der Schritt hinzugefügt werden soll. *job_id* ist vom Datentyp **uniqueidentifier**. der Standardwert ist NULL.  
  
`[ @job_name = ] 'job_name'`Der Name des Auftrags, dem der Schritt hinzugefügt werden soll. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *job_id* oder *job_name* angegeben werden, aber beide können nicht angegeben werden.  
  
`[ @step_id = ] step_id`Die Sequenz-ID für den Auftrags Schritt. Schritt-IDs beginnen bei **1** und Inkrementen ohne Lücken. Wenn ein Schritt in eine vorhandene Sequenz eingefügt wird, werden die Sequenznummern automatisch angepasst. Wenn *step_id* nicht angegeben ist, wird ein Wert bereitgestellt. *step_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @step_name = ] 'step_name'`Der Name des Schritts. *step_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @subsystem = ] 'subsystem'`Das vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst zum Ausführen des *Befehls*verwendete Subsystem. *Subsystem* ist vom Datentyp **nvarchar (40)** . die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|"**ACTIVESCRIPTING**"|Active Script<br /><br /> **\*\* Wichtig \*\*** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|  
|'**CMDEXEC**'|Betriebssystembefehl oder ausführbares Programm|  
|"**VERTEILUNG**"|Auftrag des Replikationsverteilungs-Agents|  
|"**MOMENTAUFNAHME**"|Auftrag des Replikationsmomentaufnahme-Agents|  
|"PROTOKOLL**LESER**"|Auftrag des Replikationsprotokolllese-Agents|  
|"ZUSAMMEN**FÜHREN**"|Auftrag des Replikationsmerge-Agents|  
|'**Queuereader**'|Warteschlangenlese-Agent-Auftrag der Replikation|  
|'**ANALYSISQUERY**'|Analysis Services-Abfrage (MDX, DMX)|  
|'**ANALYSISCOMMAND**'|Analysis Services-Befehl (XMLA)|  
|'**DTS**'|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paketausführung|  
|"**PowerShell**"|PowerShell-Skript|  
|"**TQL**" (Standard)|[!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung|  
  
`[ @command = ] 'command'`Die Befehle, die vom **SQLServerAgent** -Dienst über das *Subsystem*ausgeführt werden sollen. der *Befehl* ist vom Datentyp **nvarchar (max)** und hat den Standardwert NULL. Vom SQL Server-Agent wird eine Tokenersetzung bereitgestellt, die Ihnen beim Schreiben von Softwareprogrammen dieselbe Flexibilität wie Variablen bietet.  
  
> [!IMPORTANT]  
>  Damit Auftragsschritte fehlerfrei ausgeführt werden können, müssen alle in Auftragsschritten verwendeten Token von einem Escapemakro begleitet werden. Darüber hinaus müssen Sie Tokennamen nun in runde Klammern einschließen und ein Dollarzeichen (`$`) an den Anfang der Tokensyntax setzen. Zum Beispiel:  
>   
>  `$(ESCAPE_`*Makroname*`(DATE))`  
  
 Weitere Informationen zu diesen Token und zum Aktualisieren der Auftrags Schritte, um die neue Tokensyntax zu verwenden, finden Sie unter [Verwenden von Token in Auftrags Schritten](../../ssms/agent/use-tokens-in-job-steps.md).  
  
> [!IMPORTANT]  
>  Jeder Windows-Benutzer mit Schreibberechtigungen für das Windows-Ereignisprotokoll kann auf Auftragsschritte zugreifen, die durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Warnungen oder WMI-Warnungen aktiviert werden. Zur Vermeidung dieses Sicherheitsrisikos sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Tokens, die in von Warnungen aktivierten Aufträgen verwendet werden können, standardmäßig deaktiviert. Dabei handelt es sich um folgende Token: **A-DBN**, **A-SVR**, **A-ERR**, **A-SEV**, **A-MSG** und **WMI(** _Eigenschaft_ **)** . Beachten Sie, dass in dieser Version die Verwendung von Token auf alle Warnungen ausgeweitet ist.  
>   
>  Wenn Sie diese Token verwenden müssen, stellen Sie zuvor sicher, dass ausschließlich Mitglieder von vertrauenswürdigen Windows-Sicherheitsgruppen, wie der Administratorengruppe, über Schreibberechtigungen für das Ereignisprotokoll des Computers verfügen, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird. Klicken Sie dann zum Aktivieren dieser Token im Objekt-Explorer mit der rechten Maustaste auf **SQL Server-Agent** , wählen Sie **Eigenschaften**, und wählen Sie anschließend auf der Seite **Warnungssystem** die Option **Token für alle Auftragsantworten auf Warnungen ersetzen** aus.  
  
`[ @additional_parameters = ] 'parameters'`Parameter ist vom Typ **ntext**und hat den Standardwert NULL. [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @cmdexec_success_code = ] code`Der von einem **CmdExec** -Subsystembefehl zurückgegebene Wert, der angibt, dass der *Befehl* erfolgreich ausgeführt wurde. *Code* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @on_success_action = ] success_action`Die Aktion, die ausgeführt werden soll, wenn der Schritt erfolgreich ist. *success_action* ist vom Datentyp **tinyint**. die folgenden Werte sind möglich.  
  
|Wert|Beschreibung (Aktion)|  
|-----------|----------------------------|  
|**1** (Standard)|Beenden mit Erfolg|  
|**2**|Beenden mit Fehler|  
|**3**|Zum nächsten Schritt wechseln|  
|**4**|Gehen Sie zu Schritt *on_success_step_id*|  
  
`[ @on_success_step_id = ] success_step_id`Die ID des Schritts in diesem Auftrag, der ausgeführt werden soll, wenn der Schritt erfolgreich ausgeführt wurde und *success_action* den Wert **4**hat. *success_step_id* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @on_fail_action = ] fail_action`Die Aktion, die ausgeführt werden soll, wenn der Schritt fehlschlägt. *fail_action* ist vom Datentyp **tinyint**. die folgenden Werte sind möglich.  
  
|Wert|Beschreibung (Aktion)|  
|-----------|----------------------------|  
|**1**|Beenden mit Erfolg|  
|**2** (Standardwert)|Beenden mit Fehler|  
|**3**|Zum nächsten Schritt wechseln|  
|**4**|Gehen Sie zu Schritt *on_fail_step_id*|  
  
`[ @on_fail_step_id = ] fail_step_id`Die ID des Schritts in diesem Auftrag, der ausgeführt werden soll, wenn der Schritt fehlschlägt und *fail_action* **4**ist. *fail_step_id* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @server = ] 'server'`der Server ist vom Datentyp **nvarchar (30)** und hat den Standardwert NULL. [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @database_name = ] 'database'`Der Name der Datenbank, in der ein [!INCLUDE[tsql](../../includes/tsql-md.md)] Schritt ausgeführt werden soll. *Database* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. in diesem Fall wird die **Master** -Datenbank verwendet. In eckige Klammern ([ ]) eingeschlossene Namen sind nicht zulässig. Bei einem ActiveX-Auftrags Schritt ist die *Datenbank* der Name der Skriptsprache, die in diesem Schritt verwendet wird.  
  
`[ @database_user_name = ] 'user'`Der Name des Benutzerkontos, das beim Ausführen eines [!INCLUDE[tsql](../../includes/tsql-md.md)] Schritts verwendet werden soll. *User* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn der *Benutzer* NULL ist, wird der Schritt im Benutzer Kontext des Auftrags Besitzers in der *Datenbank*ausgeführt.  SQL Server-Agent schließt nur diesen Parameter ein, wenn der Auftragsbesitzer ein SQL Server sysadmin ist. In diesem Fall wird der angegebene Transact-SQL-Schritt im Kontext des angegebenen SQL Server-Benutzernamens ausgeführt. Wenn der Besitzer des Auftrags kein SQL Server sysadmin ist, wird der Transact-SQL-Schritt immer im Kontext des-Anmelde namens ausgeführt, der diesen Auftrag besitzt, und der @database_user_name -Parameter wird ignoriert.  
  
`[ @retry_attempts = ] retry_attempts`Die Anzahl der zu verwendenden Wiederholungs Versuche, wenn dieser Schritt fehlschlägt. *retry_attempts* ist vom Datentyp **int**. der Standardwert ist **0**. Dies bedeutet, dass keine Wiederholungs Versuche unternommen werden.  
  
`[ @retry_interval = ] retry_interval`Die Zeitspanne (in Minuten) zwischen den Wiederholungs versuchen. *retry_interval* ist vom Datentyp **int**. der Standardwert ist **0**, was ein Intervall von **0**Minuten angibt.  
  
`[ @os_run_priority = ] run_priority`Bleiben.  
  
`[ @output_file_name = ] 'file_name'`Der Name der Datei, in der die Ausgabe dieses Schritts gespeichert wird. *file_name* ist vom Datentyp **nvarchar (200)** und hat den Standardwert NULL. *file_name* kann eines oder mehrere der unter *Befehl*aufgeführten Token enthalten. Dieser Parameter ist nur mit Befehlen gültig, die auf [!INCLUDE[tsql](../../includes/tsql-md.md)]den-, **CmdExec**-, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **PowerShell**-,-oder [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Subsystemen ausgeführt werden.  
  
`[ @flags = ] flags`Ist eine Option, die das Verhalten steuert. *Flags* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**0** (Standardwert)|Ausgabedatei überschreiben|  
|**2**|An Ausgabedatei anfügen|  
|**4**|Ausgabe des [!INCLUDE[tsql](../../includes/tsql-md.md)]-Auftragsschritts in Schrittverlauf schreiben|  
|**8**|Protokoll in Tabelle schreiben (vorhandenen Verlauf überschreiben)|  
|**16**|Protokoll in Tabelle schreiben (an vorhandenen Verlauf anfügen)|  
|**32**|Schreiben der gesamten Ausgabe in den Auftragsverlauf|  
|**64**|Erstellen eines Windows-Ereignisses, das für den Cmd-Jobstep als Signal als Signal zum Abbruch verwendet werden soll|  
  
`[ @proxy_id = ] proxy_id`Die ID-Nummer des Proxys, als der der Auftrags Schritt ausgeführt wird. *proxy_id* ist vom Datentyp **int**und hat den Standardwert NULL. Wenn *proxy_id* nicht angegeben wird, kein *proxy_name* -Wert angegeben wird und keine *user_name* angegeben ist, wird der Auftrags Schritt als Dienst Konto für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den-Agent ausgeführt.  
  
`[ @proxy_name = ] 'proxy_name'`Der Name des Proxys, als der der Auftrags Schritt ausgeführt wird. *proxy_name* ist vom Datentyp **vom Datentyp sysname**und hat den Standardwert NULL. Wenn *proxy_id* nicht angegeben wird, kein *proxy_name* -Wert angegeben wird und keine *user_name* angegeben ist, wird der Auftrags Schritt als Dienst Konto für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den-Agent ausgeführt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 **sp_add_jobstep** muss von der **msdb** -Datenbank aus ausgeführt werden.  
  
 SQL Server Management Studio bietet eine einfache grafische Möglichkeit zum Verwalten von Aufträgen. Es handelt sich hierbei um die empfohlene Art und Weise zum Erstellen und Verwalten der Auftragsinfrastruktur.  
  
 Ein Auftrags Schritt muss einen Proxy angeben, es sei denn, der Ersteller des Auftrags Schritts ist ein Mitglied der festen Sicherheitsrolle **sysadmin** .  
  
 Ein Proxy kann mit *proxy_name* oder *proxy_id*identifiziert werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Der Ersteller des Auftragsschritts muss Zugriff auf den für den Auftragsschritt verwendeten Proxy haben. Mitglieder der festen Server Rolle **sysadmin** haben Zugriff auf alle Proxys. Anderen Benutzern muss der Zugriff auf einen Proxy explizit erteilt werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Auftragsschritt erstellt, der für die Sales-Datenbank den Schreibschutz aktiviert. Zudem werden in diesem Beispiel 5 Wiederholungsversuche festgelegt, wobei jede Wiederholung nach einer Wartezeit von 5 Minuten auftritt.  
  
> [!NOTE]  
>  In diesem Beispiel wird davon `Weekly Sales Data Backup` ausgegangen, dass der Auftrag bereits vorhanden ist.  
  
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
  
  
