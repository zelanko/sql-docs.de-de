---
title: sp_update_job (Transact-SQL) | Microsoft Docs
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c12e078505c8049511e59973c26d6a1417c7eae0
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537852"
---
# <a name="spupdatejob-transact-sql"></a>sp_update_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Attribute eines Auftrags.  
  

  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @job_id = ] job_id` Die ID des Auftrags, der aktualisiert werden. *Job_id*ist **Uniqueidentifier**.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags. *Job_name* ist **vom Datentyp nvarchar(128)**.  
  
> **HINWEIS:** Entweder *Job_id* oder *Job_name* muss angegeben werden, aber beide Angaben sind nicht möglich.  
  
`[ @new_name = ] 'new_name'` Der neue Name für den Auftrag. *New_name* ist **vom Datentyp nvarchar(128)**.  
  
`[ @enabled = ] enabled` Gibt an, ob der Auftrag aktiviert ist (**1**) oder nicht aktiviert ist (**0**). *aktiviert* ist **Tinyint**.  
  
`[ @description = ] 'description'` Die Beschreibung des Auftrags. *Beschreibung* ist **nvarchar(512)**.  
  
`[ @start_step_id = ] step_id` Die ID des ersten Schritts zum Ausführen des Auftrags. *Step_id* ist **Int**.  
  
`[ @category_name = ] 'category'` Die Kategorie des Auftrags. *Kategorie* ist **vom Datentyp nvarchar(128)**.  
  
`[ @owner_login_name = ] 'login'` Der Name der Anmeldung, die den Auftrag besitzt. *Anmeldung* ist **vom Datentyp nvarchar(128)** nur Mitglieder der der **Sysadmin** Serverrolle kann den Auftragsbesitz ändern.  
  
`[ @notify_level_eventlog = ] eventlog_level` Gibt an, wann einen Eintrag im Microsoft Windows-Anwendungsprotokoll für diesen Auftrag erfolgen. *ist NULL*ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Beschreibung (Aktion)|  
|-----------|----------------------------|  
|**0**|Never|  
|**1**|Bei Erfolg|  
|**2**|Bei einem Fehler|  
|**3**|Always|  
  
`[ @notify_level_email = ] email_level` Gibt an, wann nach Abschluss dieses Auftrags eine E-mail gesendet. *Email_level*ist **Int**. *Email_level*verwendet die gleichen Werte wie *ist NULL*.  
  
`[ @notify_level_netsend = ] netsend_level` Gibt an, wann eine Netzwerknachricht nach dem Abschluss des Auftrags gesendet. *Netsend_level*ist **Int**. *Netsend_level*verwendet die gleichen Werte wie *ist NULL*.  
  
`[ @notify_level_page = ] page_level` Gibt an, wann eine Seite nach dem Abschluss des Auftrags gesendet. *Page_level* ist **Int**. *Page_level*verwendet die gleichen Werte wie *ist NULL*.  
  
`[ @notify_email_operator_name = ] 'operator_name'` Der Name des Operators, an die e-Mail-Nachricht, wenn gesendet wird *Email_level* erreicht ist. *e-Mail-Name* ist **vom Datentyp nvarchar(128)**.  
  
`[ @notify_netsend_operator_name = ] 'netsend_operator'` Der Name des Operators, an den die Netzwerknachricht gesendet wird. *Netsend_operator* ist **vom Datentyp nvarchar(128)**.  
  
`[ @notify_page_operator_name = ] 'page_operator'` Der Name des Operators, an eine Seite gesendet wird. *Page_operator* ist **vom Datentyp nvarchar(128)**.  
  
`[ @delete_level = ] delete_level` Gibt an, wann den Auftrag gelöscht. *delete_level*ist **Int**. *Auftrag nie gelöscht*verwendet die gleichen Werte wie *ist NULL*.  
  
`[ @automatic_post = ] automatic_post` Reserviert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_update_job** muss ausgeführt werden, aus der **Msdb** Datenbank.  
  
 **Sp_update_job** ändert nur die Einstellungen, die für die Parameterwerte angegeben werden. Wird ein Parameter nicht angegeben, wird die aktuelle Einstellung beibehalten.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder der **Sysadmin** können diese gespeicherte Prozedur verwenden, um Attribute von Aufträgen zu bearbeiten, die von anderen Benutzern gehören.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
