---
title: Sp_delete_job (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_job
- sp_delete_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_job
ms.assetid: b85db6e4-623c-41f1-9643-07e5ea38db09
author: stevestein
ms.author: sstein
ms.openlocfilehash: 94b77b30d96b5361967398a35335f6aa96587f1b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085330"
---
# <a name="spdeletejob-transact-sql"></a>sp_delete_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht einen Auftrag.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_job { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,  
     [ , [ @originating_server = ] 'server' ]   
     [ , [ @delete_history = ] delete_history ]  
     [ , [ @delete_unused_schedule = ] delete_unused_schedule ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id` Ist die ID des Auftrags, der gelöscht werden. *Job_id* ist **Uniqueidentifier**, hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'` Ist der Name des Auftrags, der gelöscht werden. *Job_name* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Entweder *Job_id* oder *Job_name*muss angegeben werden; können nicht gleichzeitig angegeben werden.  
  
`[ @originating_server = ] 'server'` Zur internen Verwendung.  
  
`[ @delete_history = ] delete_history` Gibt an, ob der Verlauf für den Auftrag zu löschen. *Delete_history* ist **Bit**, hat den Standardwert **1**. Wenn *Delete_history* ist **1**, wird der Auftragsverlauf für den Auftrag gelöscht. Wenn *Delete_history* ist **0**, der Auftragsverlauf nicht gelöscht.  
  
 Beachten Sie, dass wenn ein Auftrag gelöscht, und der Verlauf wird nicht gelöscht, die Verlaufsinformationen für den Auftrag nicht in angezeigt wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Auftragsverlauf der Agents grafische Benutzeroberfläche, aber die Informationen noch befindet sich in der **Sysjobhistory**-Tabelle in der **Msdb** Datenbank.  
  
`[ @delete_unused_schedule = ] delete_unused_schedule` Gibt an, ob die Zeitpläne löschen, die diesem Auftrag angefügt werden, wenn sie nicht an einen anderen Auftrag angefügt sind. *Delete_unused_schedule* ist **Bit**, hat den Standardwert **1**. Wenn *Delete_unused_schedule* ist **1**, diesen Auftrag angefügten Zeitpläne werden gelöscht, wenn keine anderen Aufträge mit Verweisen auf den Zeitplan. Wenn *Delete_unused_schedule* ist **0**, die Zeitpläne werden nicht gelöscht.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Die **@originating_server** Argument ist für die interne Verwendung reserviert.  
  
 Die **@delete_unused_schedule** Argument bietet Abwärtskompatibilität mit früheren Versionen von SQL Server von Zeitplänen, die nicht an einen beliebigen Auftrag angefügt sind, automatisch entfernt werden. Beachten Sie, dass dieser Parameter standardmäßig das Verhalten der Abwärtskompatibilität bietet. Zum Beibehalten der Zeitpläne, die nicht mit einem Auftrag angefügt sind, geben Sie den Wert **0** als die **@delete_unused_schedule** Argument.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] können Aufträge problemlos mithilfe einer grafischen Oberfläche verwaltet werden. Dies ist die empfohlene Vorgehensweise für die Erstellung und Verwaltung der Auftragsinfrastruktur.  
  
 Mit dieser gespeicherten Prozedur können keine Wartungspläne oder Aufträge, die Teil von Wartungsplänen sind, gelöscht werden. Zum Löschen von Wartungsplänen müssen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwenden.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder der festen Serverrolle **sysadmin** können **sp_delete_job** ausführen, um einen beliebigen Auftrag zu löschen. Ein Benutzer, der kein Mitglied der festen Serverrolle **sysadmin** ist, kann nur Aufträge löschen, deren Besitzer er ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Auftrag `NightlyBackups` gelöscht.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_delete_job  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
