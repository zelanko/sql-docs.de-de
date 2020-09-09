---
description: sp_update_job (Transact-SQL)
title: sp_update_job (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_job
- sp_update_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_job
ms.assetid: cbdfea38-9e42-47f3-8fc8-5978b82e2623
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 494e284bb9df06094116d075979673bf2b033dea
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551192"
---
# <a name="sp_update_job-transact-sql"></a>sp_update_job (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ändert die Attribute eines Auftrags.  
  

  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_update_job [ @job_id =] job_id | [@job_name =] 'job_name'  
     [, [@new_name =] 'new_name' ]   
     [, [@enabled =] enabled ]  
     [, [@description =] 'description' ]   
     [, [@start_step_id =] step_id ]  
     [, [@category_name =] 'category' ]   
     [, [@owner_login_name =] 'login' ]  
     [, [@notify_level_eventlog =] eventlog_level ]  
     [, [@notify_level_email =] email_level ]  
     [, [@notify_level_netsend =] netsend_level ]  
     [, [@notify_level_page =] page_level ]  
     [, [@notify_email_operator_name =] 'operator_name' ]  
     [, [@notify_netsend_operator_name =] 'netsend_operator' ]  
     [, [@notify_page_operator_name =] 'page_operator' ]  
     [, [@delete_level =] delete_level ]   
     [, [@automatic_post =] automatic_post ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id` Die ID des Auftrags, der aktualisiert werden soll. *job_id*ist vom Datentyp **uniqueidentifier**.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags. *job_name* ist vom Datentyp **nvarchar (128)**.  
  
> **Hinweis:** Es muss entweder *job_id* oder *job_name* angegeben werden, aber beide können nicht angegeben werden.  
  
`[ @new_name = ] 'new_name'` Der neue Name für den Auftrag. *new_name* ist vom Datentyp **nvarchar (128)**.  
  
`[ @enabled = ] enabled` Gibt an, ob der Auftrag aktiviert (**1**) oder nicht aktiviert (**0**) ist. *aktiviert* ist **tinyint**.  
  
`[ @description = ] 'description'` Die Beschreibung des Auftrags. die *Beschreibung* ist **nvarchar (512)**.  
  
`[ @start_step_id = ] step_id` Die ID des ersten Schritts, der für den Auftrag ausgeführt werden soll. *step_id* ist vom Datentyp **int**.  
  
`[ @category_name = ] 'category'` Die Kategorie des Auftrags. *Category* ist vom Datentyp **nvarchar (128)**.  
  
`[ @owner_login_name = ] 'login'` Der Name der Anmeldung, die den Auftrag besitzt. *Login* ist vom Datentyp **nvarchar (128)** . nur Mitglieder der festen Server Rolle **sysadmin** können den Auftrags Besitz ändern.  
  
`[ @notify_level_eventlog = ] eventlog_level` Gibt an, wann für diesen Auftrag ein Eintrag in das Microsoft Windows-Anwendungsprotokoll platziert werden soll. *eventlog_level*ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung (Aktion)|  
|-----------|----------------------------|  
|**0**|Nie|  
|**1**|Bei Erfolg|  
|**2**|Bei Fehler|  
|**3**|Always|  
  
`[ @notify_level_email = ] email_level` Gibt an, wann nach Abschluss dieses Auftrags eine e-Mail gesendet werden soll. *email_level*ist vom Datentyp **int**. *email_level*verwendet die gleichen Werte wie *eventlog_level*.  
  
`[ @notify_level_netsend = ] netsend_level` Gibt an, wann nach Abschluss dieses Auftrags eine Netzwerk Nachricht gesendet werden soll. *netsend_level*ist vom Datentyp **int**. *netsend_level*verwendet die gleichen Werte wie *eventlog_level*.  
  
`[ @notify_level_page = ] page_level` Gibt an, wann nach dem Abschluss dieses Auftrags eine Seite gesendet werden soll. *page_level* ist vom Datentyp **int**. *page_level*verwendet die gleichen Werte wie *eventlog_level*.  
  
`[ @notify_email_operator_name = ] 'operator_name'` Der Name des Operators, an den die e-Mail-Nachricht gesendet wird, wenn *email_level* erreicht wird. *email_name* ist vom Datentyp **nvarchar (128)**.  
  
`[ @notify_netsend_operator_name = ] 'netsend_operator'` Der Name des Operators, an den die Netzwerk Nachricht gesendet wird. *netsend_operator* ist vom Datentyp **nvarchar (128)**.  
  
`[ @notify_page_operator_name = ] 'page_operator'` Der Name des Operators, an den eine Seite gesendet wird. *page_operator* ist vom Datentyp **nvarchar (128)**.  
  
`[ @delete_level = ] delete_level` Gibt an, wann der Auftrag gelöscht werden soll. *delete_value*ist vom Datentyp **int**. *delete_level*verwendet die gleichen Werte wie *eventlog_level*.  
  
`[ @automatic_post = ] automatic_post` Bleiben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_update_job** müssen von der **msdb** -Datenbank aus ausgeführt werden.  
  
 **sp_update_job** ändert nur die Einstellungen, für die Parameterwerte angegeben werden. Wird ein Parameter nicht angegeben, wird die aktuelle Einstellung beibehalten.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder der **sysadmin** -Rolle können diese gespeicherte Prozedur verwenden, um die Attribute von Aufträgen zu bearbeiten, die sich im Besitz anderer Benutzer befinden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden der Name, die Beschreibung und der aktivierte Status des Auftrags `NightlyBackups` geändert.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_job  
    @job_name = N'NightlyBackups',  
    @new_name = N'NightlyBackups -- Disabled',  
    @description = N'Nightly backups disabled during server migration.',  
    @enabled = 0 ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
