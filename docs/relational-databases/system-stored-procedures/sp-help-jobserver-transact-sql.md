---
title: sp_help_jobserver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobserver
- sp_help_jobserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobserver
ms.assetid: 57971787-f9f5-4199-9f64-c2b61a308906
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6a1a2ce1208dcf359bb0586c3de1fe294644e3a5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68054878"
---
# <a name="sp_help_jobserver-transact-sql"></a>sp_help_jobserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zum Server für einen bestimmten Auftrag zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_jobserver  
     { [ @job_id = ] job_id   
     | [ @job_name = ] 'job_name' }  
     [ , [ @show_last_run_details = ] show_last_run_details ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id`Die ID des Auftrags, für den Informationen zurückgegeben werden sollen. *job_id* ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'`Der Name des Auftrags, für den Informationen zurückgegeben werden sollen. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *job_id* oder *job_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @show_last_run_details = ] show_last_run_details`Gibt an, ob die Ausführungs Informationen der letzten Ausführung Teil des Resultsets sind. *show_last_run_details* ist vom Datentyp **tinyint**. der Standardwert ist **0**. **0** enthält keine Informationen zur letzten Laufzeit und **1** .  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ID des Zielservers|  
|**server_name**|**nvarchar(30)**|Computername des Zielservers|  
|**enlist_date**|**datetime**|Datum, an dem der Zielserver auf dem Masterserver eingetragen wurde|  
|**last_poll_date**|**datetime**|Datum, an dem der Zielserver den Masterserver zuletzt abgerufen hat|  
  
 Wenn **sp_help_jobserver** ausgeführt wird, wobei *show_last_run_details* auf **1**festgelegt ist, enthält das Resultset diese zusätzlichen Spalten.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**last_run_date**|**int**|Datum, an dem die Ausführung des Auftrags auf diesem Zielserver zuletzt gestartet wurde|  
|**last_run_time**|**int**|Uhrzeit, zu der die Ausführung des Auftrags auf diesem Server zuletzt gestartet wurde|  
|**last_run_duration**|**int**|Dauer des Auftrags bei der letzten Ausführung auf diesem Zielserver (in Sekunden)|  
|**last_outcome_message**|**nvarchar(1024)**|Beschreibt das letzte Ergebnis des Auftrags|  
|**last_run_outcome**|**int**|Ergebnis des Auftrags bei der letzten Ausführung auf diesem Server:<br /><br /> **0** = fehlgeschlagen<br /><br /> **1** = erfolgreich<br /><br /> **3** = abgebrochen<br /><br /> **5** = unbekannt|  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Mitglieder von **SQLAgentUserRole** können nur Informationen für Aufträge anzeigen, deren Besitzer Sie sind.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_jobserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
