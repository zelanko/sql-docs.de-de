---
description: sp_update_jobstep (Transact-SQL)
title: sp_update_jobstep (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_jobstep
- sp_update_jobstep_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_jobstep
ms.assetid: e158802c-c347-4a5d-bf75-c03e5ae56e6b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0a7161fd475b1fdac439e1c14e59034de2d7bbfe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473526"
---
# <a name="sp_update_jobstep-transact-sql"></a>sp_update_jobstep (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ändert die Einstellung für einen Schritt eines Auftrags, mit dem automatische Aktivitäten ausgeführt werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_update_jobstep   
     {   [@job_id =] job_id   
       | [@job_name =] 'job_name' } ,  
     [@step_id =] step_id  
     [ , [@step_name =] 'step_name' ]  
     [ , [@subsystem =] 'subsystem' ]   
     [ , [@command =] 'command' ]  
     [ , [@additional_parameters =] 'parameters' ]  
     [ , [@cmdexec_success_code =] success_code ]  
     [ , [@on_success_action =] success_action ]   
     [ , [@on_success_step_id =] success_step_id ]  
     [ , [@on_fail_action =] fail_action ]   
     [ , [@on_fail_step_id =] fail_step_id ]  
     [ , [@server =] 'server' ]   
     [ , [@database_name =] 'database' ]  
     [ , [@database_user_name =] 'user' ]   
     [ , [@retry_attempts =] retry_attempts ]  
     [ , [@retry_interval =] retry_interval ]   
     [ , [@os_run_priority =] run_priority ]  
     [ , [@output_file_name =] 'file_name' ]   
     [ , [@flags =] flags ]  
     [ ,  {   [ @proxy_id = ] proxy_id   
            | [ @proxy_name = ] 'proxy_name' }   
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id` Die ID des Auftrags, zu dem der Schritt gehört. *job_id*ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL. Es muss entweder *job_id* oder *job_name* angegeben werden, aber beide können nicht angegeben werden.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags, zu dem der Schritt gehört. *job_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Es muss entweder *job_id* oder *job_name* angegeben werden, aber beide können nicht angegeben werden.  
  
`[ @step_id = ] step_id` Die ID des Auftrags Schritts, der geändert werden soll. Diese ID kann nicht geändert werden. *step_id*ist vom Datentyp **int**und hat keinen Standardwert.  
  
`[ @step_name = ] 'step_name'` Ein neuer Name für den Schritt. *step_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @subsystem = ] 'subsystem'` Das Subsystem, das von Microsoft SQL Server-Agent zum Ausführen des *Befehls*verwendet wird. *Subsystem* ist vom Datentyp **nvarchar (40)** und hat den Standardwert NULL.  
  
`[ @command = ] 'command'` Der Befehl (e), der über das *Subsystem*ausgeführt werden soll. der *Befehl* ist vom Datentyp **nvarchar (max)** und hat den Standardwert NULL.  
  
`[ @additional_parameters = ] 'parameters'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @cmdexec_success_code = ] success_code` Der von einem **CmdExec** -Subsystembefehl zurückgegebene Wert, der angibt, dass der *Befehl* erfolgreich ausgeführt wurde. *success_code* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @on_success_action = ] success_action` Die Aktion, die ausgeführt werden soll, wenn der Schritt erfolgreich ist. *success_action* ist vom Datentyp **tinyint**. der Standardwert ist NULL. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung (Aktion)|  
|-----------|----------------------------|  
|**1**|Beenden mit Erfolg|  
|**2**|Beenden mit Fehler|  
|**3**|Gehe zum nächsten Schritt|  
|**4**|Gehen Sie zu Schritt *success_step_id.*|  
  
`[ @on_success_step_id = ] success_step_id` Die ID des Schritts in diesem Auftrag, der ausgeführt werden soll, wenn der Schritt erfolgreich ist und *success_action* **4**ist. *success_step_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @on_fail_action = ] fail_action` Die Aktion, die ausgeführt werden soll, wenn der Schritt fehlschlägt. *fail_action* ist vom Datentyp **tinyint**und hat den Standardwert NULL und kann einen der folgenden Werte aufweisen.  
  
|Wert|Beschreibung (Aktion)|  
|-----------|----------------------------|  
|**1**|Beenden mit Erfolg|  
|**2**|Beenden mit Fehler|  
|**3**|Gehe zum nächsten Schritt|  
|**4**|Gehen Sie zu Schritt *fail_step_id * *.*|  
  
`[ @on_fail_step_id = ] fail_step_id` Die ID des Schritts in diesem Auftrag, der ausgeführt werden soll, wenn der Schritt fehlschlägt und *fail_action* **4**ist. *fail_step_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @server = ] 'server'`[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]der *Server* ist vom Datentyp **nvarchar (128)** und hat den Standardwert NULL.  
  
`[ @database_name = ] 'database'` Der Name der Datenbank, in der ein Schritt ausgeführt werden soll [!INCLUDE[tsql](../../includes/tsql-md.md)] . *Database*ist vom **Datentyp vom Datentyp sysname**. In eckige Klammern ([ ]) eingeschlossene Namen sind nicht zulässig. Der Standardwert ist NULL.  
  
`[ @database_user_name = ] 'user'` Der Name des Benutzerkontos, das beim Ausführen eines Schritts verwendet werden soll [!INCLUDE[tsql](../../includes/tsql-md.md)] . *User*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @retry_attempts = ] retry_attempts` Die Anzahl der zu verwendenden Wiederholungs Versuche, wenn dieser Schritt fehlschlägt. *retry_attempts*ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @retry_interval = ] retry_interval` Die Zeitspanne (in Minuten) zwischen den Wiederholungs versuchen. *retry_interval* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @os_run_priority = ] run_priority` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @output_file_name = ] 'file_name'` Der Name der Datei, in der die Ausgabe dieses Schritts gespeichert wird. *file_name* ist vom Datentyp **nvarchar (200)** und hat den Standardwert NULL. Dieser Parameter ist nur mit Befehlen gültig, die in [!INCLUDE[tsql](../../includes/tsql-md.md)]- oder CmdExec-Subsystemen ausgeführt werden.  
  
 Um output_file_name auf NULL festzulegen, müssen Sie *output_file_name* auf eine leere Zeichenfolge ("") oder auf eine leere Zeichenfolge ("") oder auf eine leere Zeichenfolge festlegen, aber Sie können die **char (32)** -Funktion nicht verwenden. Sie können dieses Argument z. B. wie folgt auf eine leere Zeichenfolge festlegen:  
  
 **@output_file_name = ' '**  
  
`[ @flags = ] flags` Eine Option, die das Verhalten steuert. *Flags* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0** (Standardwert)|Ausgabedatei überschreiben.|  
|**2**|An Ausgabedatei anfügen|  
|**4**|Ausgabe des Transact-SQL-Auftragsschrittes in Schrittverlauf schreiben|  
|**8**|Protokoll in Tabelle schreiben (vorhandenen Verlauf überschreiben)|  
|**16**|Protokoll in Tabelle schreiben (an vorhandenen Verlauf anfügen)|  
  
`[ @proxy_id = ] proxy_id` Die ID-Nummer des Proxys, als der der Auftrags Schritt ausgeführt wird. *proxy_id* ist vom Datentyp **int**und hat den Standardwert NULL. Wenn keine *proxy_id* angegeben wird, kein *proxy_name* angegeben wird und keine *user_name* angegeben ist, wird der Auftrags Schritt als Dienst Konto für den- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ausgeführt.  
  
`[ @proxy_name = ] 'proxy_name'` Der Name des Proxys, als der der Auftrags Schritt ausgeführt wird. *proxy_name* ist vom Datentyp **vom Datentyp sysname**und hat den Standardwert NULL. Wenn keine *proxy_id* angegeben wird, kein *proxy_name* angegeben wird und keine *user_name* angegeben ist, wird der Auftrags Schritt als Dienst Konto für den- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ausgeführt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_update_jobstep** müssen von der **msdb** -Datenbank aus ausgeführt werden.  
  
 Beim Aktualisieren eines Auftragsschrittes wird die Versionsnummer des Auftrags erhöht.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder von **sysadmin** können einen Auftrags Schritt aktualisieren, dessen Besitzer ein anderer Benutzer ist.  
  
 Falls für den Auftragsschritt der Zugriff auf einen Proxy erforderlich ist, muss der Ersteller des Auftragsschrittes Zugriff auf den Proxy für den Auftragsschritt haben. Alle Subsysteme außer Transact-SQL erfordern ein Proxykonto. Mitglieder von **sysadmin** haben Zugriff auf alle Proxys und können das- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienst Konto für den Proxy verwenden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Anzahl der Wiederholungsversuche für den ersten Schritt des `Weekly Sales Data Backup`-Auftrags geändert. Nach Ausführung dieses Beispiels ist die Anzahl der Wiederholungsversuche auf `10` festgelegt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1,  
    @retry_attempts = 10 ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen oder Ändern von Aufträgen](../../ssms/agent/view-or-modify-jobs.md)   
 [sp_delete_jobstep &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
