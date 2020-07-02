---
title: sp_detach_schedule (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b183a121981cc32ca7cdd3857c4e9ee10fa7f83e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717342"
---
# <a name="sp_detach_schedule-transact-sql"></a>sp_detach_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Entfernt eine Zuordnung zwischen einem Zeitplan und einem Auftrag.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_detach_schedule   
     { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,  
       { [ @schedule_id = ] schedule_id | [ @schedule_name = ] 'schedule_name' } ,  
     [ @delete_unused_schedule = ] delete_unused_schedule   
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id`Die ID des Auftrags, aus dem der Zeitplan entfernt werden soll. *job_id* ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'`Der Name des Auftrags, aus dem der Zeitplan entfernt werden soll. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *job_id* oder *job_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @schedule_id = ] schedule_id`Die Zeitplan-ID des Zeitplans, der aus dem Auftrag entfernt werden soll. *schedule_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @schedule_name = ] 'schedule_name'`Der Name des Zeitplans, der aus dem Auftrag entfernt werden soll. *schedule_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *schedule_id* oder *schedule_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @delete_unused_schedule = ] delete_unused_schedule`Gibt an, ob nicht verwendete Auftrags Zeitpläne gelöscht werden sollen. *delete_unused_schedule* ist vom Typ **Bit**. der Standardwert ist **0**. Dies bedeutet, dass alle Zeitpläne beibehalten werden, auch wenn keine Aufträge auf Sie verweisen. Wenn der Wert auf **1**festgelegt ist, werden nicht verwendete Auftrags Zeitpläne gelöscht, wenn keine Aufträge darauf verweisen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Hinweis: Der Auftragsbesitzer kann einem Zeitplan einen Auftrag anfügen oder diesen von ihm trennen, und zwar ohne der Zeitplanbesitzer sein zu müssen. Ein Zeitplan kann jedoch nicht gelöscht werden, wenn durch das Trennen keine Aufträge mehr vorhanden wären, außer der Aufrufer ist der Zeitplanbesitzer.  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überprüft, ob der Benutzer der Besitzer des Zeitplans ist. Nur Mitglieder der festen Server Rolle **sysadmin** können Zeitpläne von Aufträgen trennen, die sich im Besitz eines anderen Benutzers befinden.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)  
  
  
