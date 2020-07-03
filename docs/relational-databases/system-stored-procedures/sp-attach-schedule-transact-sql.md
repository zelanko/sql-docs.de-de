---
title: sp_attach_schedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_attach_schedule_TSQL
- sp_attach_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_attach_schedule
ms.assetid: 80c80eaf-cf23-4ed8-b8dd-65fe59830dd1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6bc01db6ae019694cbff4082c394fd8c736b9a5a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85874369"
---
# <a name="sp_attach_schedule-transact-sql"></a>sp_attach_schedule (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Legt einen Zeitplan für einen Auftrag fest.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_attach_schedule  
     { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,   
     { [ @schedule_id = ] schedule_id   
     | [ @schedule_name = ] 'schedule_name' }  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id`Die ID des Auftrags, dem der Zeitplan hinzugefügt wird. *job_id*ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'`Der Name des Auftrags, dem der Zeitplan hinzugefügt wird. *job_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *job_id* oder *job_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @schedule_id = ] schedule_id`Die Zeitplan-ID des Zeitplans, der für den Auftrag festgelegt werden soll. *schedule_id*ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @schedule_name = ] 'schedule_name'`Der Name des Zeitplans, der für den Auftrag festgelegt werden soll. *schedule_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *schedule_id* oder *schedule_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
## <a name="remarks"></a>Hinweise  
 Der Zeitplan und der Auftrag müssen denselben Besitzer aufweisen.  
  
 Ein Zeitplan kann für mehrere Aufträge festgelegt werden. Ein Auftrag kann auf der Basis mehrerer Zeitpläne ausgeführt werden.  
  
 Diese gespeicherte Prozedur muss von der **msdb** -Datenbank aus ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Hinweis: Der Auftragsbesitzer kann einem Zeitplan einen Auftrag anfügen oder diesen von ihm trennen, und zwar ohne der Zeitplanbesitzer sein zu müssen. Ein Zeitplan kann jedoch nicht gelöscht werden, wenn der Trennvorgang keine Aufträge hat, es sei denn, der Aufrufer ist der Zeit Plan Besitzer.  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prüft, ob der Benutzer Besitzer sowohl des Auftrags als auch des Zeitplans ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Zeitplan mit dem Namen `NightlyJobs` erstellt. Aufträge, die diesen Zeitplan verwenden, werden jeden Tag zur Serveruhrzeit `01:00` Uhr ausgeführt. Im Beispiel wird der Zeitplan den Aufträgen `BackupDatabase` und `RunReports` angefügt.  
  
> [!NOTE]  
>  Bei diesem Beispiel wird davon ausgegangen, dass die Aufträge `BackupDatabase` und `RunReports` bereits vorhanden sind.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_add_schedule  
    @schedule_name = N'NightlyJobs' ,  
    @freq_type = 4,  
    @freq_interval = 1,  
    @active_start_time = 010000 ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'BackupDatabase',  
   @schedule_name = N'NightlyJobs' ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'RunReports',  
   @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)  
  
  
