---
title: Sp_help_jobserver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_jobserver
- sp_help_jobserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobserver
ms.assetid: 57971787-f9f5-4199-9f64-c2b61a308906
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fdaa9481c51188767834679031b6cdc9084f969d
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393657"
---
# <a name="sphelpjobserver-transact-sql"></a>sp_help_jobserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zum Server für einen bestimmten Auftrag zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_jobserver  
     { [ @job_id = ] job_id   
     | [ @job_name = ] 'job_name' }  
     [ , [ @show_last_run_details = ] show_last_run_details ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@job_id=** ] *job_id*  
 Die ID des Auftrags, zu dem Informationen zurückgegeben werden sollen. *Job_id* ist **Uniqueidentifier**, hat den Standardwert NULL.  
  
 [  **@job_name=** ] **"***Job_name***"**  
 Der Name des Auftrags, für den Informationen zurückgegeben werden sollen. *Job_name* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Entweder *Job_id* oder *Job_name* muss angegeben werden, aber beide Angaben sind nicht möglich.  
  
 [  **@show_last_run_details=** ] *Show_last_run_details*  
 Gibt an, ob die Informationen der letzten Ausführung Teil des Resultsets sind. *Show_last_run_details* ist **Tinyint**, hat den Standardwert **0**. **0** enthält keine Informationen zur letzten Ausführung, und **1** ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ID des Zielservers|  
|**server_name**|**nvarchar(30)**|Computername des Zielservers|  
|**enlist_date**|**datetime**|Datum, an dem der Zielserver auf dem Masterserver eingetragen wurde|  
|**last_poll_date**|**datetime**|Datum, an dem der Zielserver den Masterserver zuletzt abgerufen hat|  
  
 Wenn **Sp_help_jobserver** ausgeführt wird, mit *Show_last_run_details* festgelegt **1**, das Resultset verfügt über diese zusätzlichen Spalten.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**last_run_date**|**int**|Datum, an dem die Ausführung des Auftrags auf diesem Zielserver zuletzt gestartet wurde|  
|**last_run_time**|**int**|Uhrzeit, zu der die Ausführung des Auftrags auf diesem Server zuletzt gestartet wurde|  
|**last_run_duration**|**int**|Dauer des Auftrags bei der letzten Ausführung auf diesem Zielserver (in Sekunden)|  
|**last_outcome_message**|**nvarchar(1024)**|Beschreibt das letzte Ergebnis des Auftrags|  
|**last_run_outcome**|**int**|Ergebnis des Auftrags bei der letzten Ausführung auf diesem Server:<br /><br /> **0** = Fehler<br /><br /> **1** = war erfolgreich<br /><br /> **3** = abgebrochen<br /><br /> **5** = unbekannt|  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Mitglieder der **SQLAgentUserRole** können nur Informationen für ihren eigenen Aufträgen anzeigen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen, einschließlich der Informationen zur letzten Ausführung, zum `NightlyBackups`-Auftrag zurückgegeben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobserver  
    @job_name = N'NightlyBackups',  
    @show_last_run_details = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
