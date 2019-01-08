---
title: Sp_detach_schedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_detach_schedule
- sp_detach_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_detach_schedule
ms.assetid: 9a1fc335-1bef-4638-a33a-771c54a5dd19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 409dec92a6dbfe9c4dd2c8cef1d81b2aa7f21d91
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52536377"
---
# <a name="spdetachschedule-transact-sql"></a>sp_detach_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt eine Zuordnung zwischen einem Zeitplan und einem Auftrag.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_detach_schedule   
     { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,  
       { [ @schedule_id = ] schedule_id | [ @schedule_name = ] 'schedule_name' } ,  
     [ @delete_unused_schedule = ] delete_unused_schedule   
```  
  
## <a name="arguments"></a>Argumente  
 [ **@job_id=** ] *job_id*  
 Die ID des Auftrags, aus dem der Zeitplan entfernt werden soll. *Job_id* ist **Uniqueidentifier**, hat den Standardwert NULL.  
  
 [  **@job_name=** ] **"**_Job_name_**"**  
 Der Name des Auftrags, aus dem der Zeitplan entfernt werden soll. *Job_name* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Entweder *Job_id* oder *Job_name* muss angegeben werden, aber beide Angaben sind nicht möglich.  
  
 [  **@schedule_id=** ] *Schedule_id*  
 Die ID des Zeitplans, der aus dem Auftrag entfernt werden soll. *Schedule_id* ist **Int**, hat den Standardwert NULL.  
  
 [  **@schedule_name=** ] **"**_Schedule_name_**"**  
 Der Name des Zeitplans, der aus dem Auftrag entfernt werden soll. *Schedule_name* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Entweder *Schedule_id* oder *Schedule_name* muss angegeben werden, aber beide Angaben sind nicht möglich.  
  
 [  **@delete_unused_schedule=** ] *Delete_unused_schedule*  
 Gibt an, ob nicht verwendete Auftragszeitpläne gelöscht werden sollen. *Delete_unused_schedule* ist **Bit**, hat den Standardwert **0**, d. h. alle Zeitpläne beibehalten werden, auch wenn keine Aufträge, die darauf verweisen. Wenn auf festgelegt **1**, nicht verwendete Auftragszeitpläne gelöscht, wenn keine Aufträge auf sie verweist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Hinweis: Der Auftragsbesitzer kann einem Zeitplan einen Auftrag anfügen oder diesen von ihm trennen, und zwar ohne der Zeitplanbesitzer sein zu müssen. Ein Zeitplan kann jedoch nicht gelöscht werden, wenn durch das Trennen keine Aufträge mehr vorhanden wären, außer der Aufrufer ist der Zeitplanbesitzer.  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überprüft, ob der Benutzer der Besitzer des Zeitplans ist. Nur Mitglieder der **Sysadmin** -Serverrolle kann Zeitpläne von Aufträgen, die im Besitz eines anderen Benutzers trennen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Zuordnung zwischen einem `'NightlyJobs'`-Zeitplan und einem `'BackupDatabase'`-Auftrag entfernt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_detach_schedule  
    @job_name = 'BackupDatabase',  
    @schedule_name = 'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)  
  
  
