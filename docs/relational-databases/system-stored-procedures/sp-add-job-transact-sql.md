---
title: sp_add_job (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_job_TSQL
- sp_add_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_job
ms.assetid: 6ca8fe2c-7b1c-4b59-b4c7-e3b7485df274
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7752b8fcb453f545c357c529774d570e41201ed1
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381909"
---
# <a name="sp_add_job-transact-sql"></a>sp_add_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Fügt einen neuen Auftrag hinzu, der vom SQL Agent-Dienst ausgeführt wird.  
  
 ![Themen Link Symbol](../../database-engine/configure-windows/media/topic-link.gif "Link Symbol "Thema"") [Transact-SQL-Syntax Konventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
 
 > [!IMPORTANT]  
 > In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).
 
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_job [ @job_name = ] 'job_name'  
     [ , [ @enabled = ] enabled ]   
     [ , [ @description = ] 'description' ]   
     [ , [ @start_step_id = ] step_id ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @category_id = ] category_id ]   
     [ , [ @owner_login_name = ] 'login' ]   
     [ , [ @notify_level_eventlog = ] eventlog_level ]   
     [ , [ @notify_level_email = ] email_level ]   
     [ , [ @notify_level_netsend = ] netsend_level ]   
     [ , [ @notify_level_page = ] page_level ]   
     [ , [ @notify_email_operator_name = ] 'email_name' ]   
          [ , [ @notify_netsend_operator_name = ] 'netsend_name' ]   
     [ , [ @notify_page_operator_name = ] 'page_name' ]   
     [ , [ @delete_level = ] delete_level ]   
     [ , [ @job_id = ] job_id OUTPUT ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_name = ] 'job_name'` den Namen des Auftrags. Der Name muss eindeutig sein und darf kein Prozentzeichen ( **%** ) enthalten. *job_name*ist vom Datentyp **nvarchar (128)** und hat keinen Standardwert.  
  
`[ @enabled = ] enabled` gibt den Status des hinzugefügten Auftrags an. *aktiviert*ist vom Datentyp **tinyint**. der Standardwert ist 1 (aktiviert). Wenn der Wert **0**ist, ist der Auftrag nicht aktiviert und wird nicht gemäß dem Zeitplan ausgeführt. Sie kann jedoch manuell ausgeführt werden.  
  
`[ @description = ] 'description'` die Beschreibung des Auftrags. die *Beschreibung* ist vom Datentyp **nvarchar (512)** und hat den Standardwert NULL. Wenn *Description* weggelassen wird, wird "keine Beschreibung verfügbar" verwendet.  
  
`[ @start_step_id = ] step_id` die ID des ersten Schritts, der für den Auftrag ausgeführt werden soll. *step_id*ist vom Datentyp **int**und hat den Standardwert 1.  
  
`[ @category_name = ] 'category'` die Kategorie für den Auftrag. *Category*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @category_id = ] category_id` ein sprachunabhängiger Mechanismus zum Angeben einer Auftrags Kategorie. *category_id*ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @owner_login_name = ] 'login'` der Name der Anmeldung, die den Auftrag besitzt. *Login*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL, der als aktueller Anmelde Name interpretiert wird. Nur Mitglieder der festen Server Rolle **sysadmin** können den Wert für **\@owner_login_name**festlegen oder ändern. Wenn Benutzer, die keine Mitglieder der **sysadmin** -Rolle sind, den Wert **\@owner_login_name**festlegen oder ändern, schlägt die Ausführung dieser gespeicherten Prozedur fehl, und es wird ein Fehler zurückgegeben.  
  
`[ @notify_level_eventlog = ] eventlog_level` ein Wert, der angibt, wann für diesen Auftrag ein Eintrag in das Microsoft Windows-Anwendungsprotokoll platziert werden soll. *eventlog_level*ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|value|Description|  
|-----------|-----------------|  
|**0**|Never|  
|**1**|Bei Erfolg|  
|**2** (Standardwert)|Bei Fehler|  
|**3**|Always|  
  
`[ @notify_level_email = ] email_level` ein Wert, der angibt, wann nach Abschluss dieses Auftrags eine e-Mail gesendet werden soll. *email_level*ist vom Datentyp **int**. der Standardwert ist **0**, was bedeutet, dass nie. *email_level*verwendet die gleichen Werte wie *eventlog_level*.  
  
`[ @notify_level_netsend = ] netsend_level` ein Wert, der angibt, wann nach Abschluss dieses Auftrags eine Netzwerk Nachricht gesendet werden soll. *netsend_level*ist vom Datentyp **int**. der Standardwert ist **0**, was bedeutet, dass nie. *netsend_level* verwendet die gleichen Werte wie *eventlog_level*.  
  
`[ @notify_level_page = ] page_level` ein Wert, der angibt, wann nach dem Abschluss dieses Auftrags eine Seite gesendet werden soll. *page_level*ist vom Datentyp **int**. der Standardwert ist **0**, was bedeutet, dass nie. *page_level*verwendet die gleichen Werte wie *eventlog_level*.  
  
`[ @notify_email_operator_name = ] 'email_name'` der e-Mail-Name der Person, an die eine e-Mail gesendet werden soll, wenn *email_level* erreicht wird. *aufweisen:* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @notify_netsend_operator_name = ] 'netsend_name'` den Namen des Operators, an den die Netzwerk Nachricht gesendet wird, wenn dieser Auftrag abgeschlossen ist. *netsend_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @notify_page_operator_name = ] 'page_name'` den Namen der Person, die nach dem Abschluss dieses Auftrags angezeigt werden soll. *page_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @delete_level = ] delete_level` ein Wert, der angibt, wann der Auftrag gelöscht werden soll. *delete_value*ist vom Datentyp **int**. der Standardwert ist 0. Dies bedeutet nie. *delete_level*verwendet die gleichen Werte wie *eventlog_level*.  
  
> [!NOTE]  
>  Wenn *delete_level* gleich **3**ist, wird der Auftrag nur einmal ausgeführt, unabhängig von den für den Auftrag definierten Zeitplänen. Darüber hinaus wird, wenn sich ein Auftrag selbst löscht, auch der gesamte Verlauf für diesen Auftrag gelöscht.  
  
`[ @job_id = ] _job_idOUTPUT` die Auftrags-ID, die dem Auftrag zugewiesen wird, wenn er erfolgreich erstellt wurde. *job_id*ist eine Ausgabevariable vom Typ **uniqueidentifier**. der Standardwert ist NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 InclusionThresholdSetting  
  
## <a name="remarks"></a>Bemerkungen  
 **@no__t 1originating_server** ist in **sp_add_job vorhanden,** wird aber nicht unter Argumente aufgeführt. **\@originating_server** ist für die interne Verwendung reserviert.  
  
 Nachdem **sp_add_job** zum Hinzufügen eines Auftrags ausgeführt wurde, kann **sp_add_jobstep** verwendet werden, um Schritte hinzuzufügen, die die Aktivitäten für den Auftrag ausführen. **sp_add_jobschedule** kann verwendet werden, um den Zeitplan zu erstellen, den der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst zum Ausführen des Auftrags verwendet. Legen Sie mit **sp_add_jobserver** die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz fest, in der der Auftrag ausgeführt wird, und **sp_delete_jobserver** , um den Auftrag aus der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz zu entfernen.  
  
 Wenn der Auftrag auf einem oder mehreren Ziel Servern in einer Multiserverumgebung ausgeführt wird, verwenden Sie **sp_apply_job_to_targets** , um die Zielserver oder Zielserver Gruppen für den Auftrag festzulegen. Verwenden Sie **sp_remove_job_from_targets**, um Aufträge von Ziel Servern oder Zielserver Gruppen zu entfernen.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] können Aufträge problemlos mithilfe einer grafischen Oberfläche verwaltet werden. Dies ist die empfohlene Vorgehensweise für die Erstellung und Verwaltung der Auftragsinfrastruktur.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieser gespeicherten Prozedur müssen Benutzer ein Mitglied der festen Server Rolle **sysadmin** sein oder eine der folgenden festen Daten bankrollen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent erhalten, die sich in der **msdb** -Datenbank befinden:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Informationen zu den einzelnen Berechtigungen, die den einzelnen festgelegten Daten bankrollen zugeordnet sind, finden Sie unter [SQL Server-Agent fester Daten bankrollen](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder der festen Server Rolle **sysadmin** können den Wert für **\@owner_login_name**festlegen oder ändern. Wenn Benutzer, die keine Mitglieder der **sysadmin** -Rolle sind, den Wert **\@owner_login_name**festlegen oder ändern, schlägt die Ausführung dieser gespeicherten Prozedur fehl, und es wird ein Fehler zurückgegeben.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-adding-a-job"></a>A. Hinzufügen eines Auftrags  
 Im folgenden Beispiel wird ein neuer Auftrag mit dem Namen `NightlyBackups` hinzugefügt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_job  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-adding-a-job-with-pager-e-mail-and-net-send-information"></a>B. Hinzufügen eines Auftrags mit Pager-, E-Mail- und NET SEND-Informationen  
 Im folgenden Beispiel wird der Auftrag `Ad hoc Sales Data Backup` erstellt, mit dem `François Ajenstat` (per Pager, E-Mail oder Netzwerk-Popupnachricht) benachrichtigt wird, falls der Auftrag einen Fehler erzeugt. Wenn der Auftrag erfolgreich ausgeführt wurde, wird er gelöscht.  
  
> [!NOTE]  
>  Im Rahmen dieses Beispiels wird davon ausgegangen, dass der Operator `François Ajenstat` und der Anmeldename `françoisa` bereits vorhanden sind.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_job  
    @job_name = N'Ad hoc Sales Data Backup',   
    @enabled = 1,  
    @description = N'Ad hoc backup of sales data',  
    @owner_login_name = N'françoisa',  
    @notify_level_eventlog = 2,  
    @notify_level_email = 2,  
    @notify_level_netsend = 2,  
    @notify_level_page = 2,  
    @notify_email_operator_name = N'François Ajenstat',  
    @notify_netsend_operator_name = N'François Ajenstat',   
    @notify_page_operator_name = N'François Ajenstat',  
    @delete_level = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_apply_job_to_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_remove_job_from_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remove-job-from-targets-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
