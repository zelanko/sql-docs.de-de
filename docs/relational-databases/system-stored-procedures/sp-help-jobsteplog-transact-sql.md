---
title: Sp_help_jobsteplog (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobsteplog_TSQL
- sp_help_jobsteplog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobsteplog
ms.assetid: 1a0be7b1-8f31-4b4c-aadb-586c0e00ed04
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b6480c498914c4ec0bc02ba21552615bbdd28f6e
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535692"
---
# <a name="sphelpjobsteplog-transact-sql"></a>sp_help_jobsteplog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Metadaten zu einem bestimmten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auftragsschrittprotokoll Agent. **Sp_help_jobsteplog** ist nicht das eigentliche Protokoll zurück.  

  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]  
     [ , [ @step_name = ] 'step_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] 'job_id'` Die Auftrags-ID für den Auftragsschritt-Protokollinformationen zurückgegeben werden soll. *Job_id* ist **Int**, hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags. *Job_name* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Entweder *Job_id* oder *Job_name* muss angegeben werden, aber beide Angaben sind nicht möglich.  
  
`[ @step_id = ] step_id` Die ID des Schritts im Auftrag. Wenn diese nicht angegeben wird, sind alle Schritte im Auftrag eingeschlossen. *Step_id* ist **Int**, hat den Standardwert NULL.  
  
`[ @step_name = ] 'step_name'` Der Name des Schritts im Auftrag. *Step_name* ist **Sysname**, hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|Eindeutiger Bezeichner des Auftrags.|  
|**job_name**|**sysname**|Name des Auftrags.|  
|**step_id**|**int**|Bezeichner des Schritts innerhalb des Auftrags. Wenn der Schritt der erste Schritt im Auftrag ist z. B. die *Step_id* ist 1.|  
|**step_name**|**sysname**|Name des Auftragsschritts.|  
|**step_uid**|**uniqueidentifier**|Eindeutiger Bezeichner des Schritts (systemgeneriert) im Auftrag.|  
|**date_created**|**datetime**|Datum, an dem der Schritt erstellt wurde.|  
|**date_modified**|**datetime**|Datum, an dem der Schritt zuletzt geändert wurde.|  
|**log_size**|**float**|Größe des Auftragsschrittprotokolls in MB.|  
|**log**|**nvarchar(max)**|Ausgabe des Auftragsschrittprotokolls.|  
  
## <a name="remarks"></a>Hinweise  
 **Sp_help_jobsteplog** befindet sich in der **Msdb** Datenbank.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Mitglieder der **SQLAgentUserRole** Metadaten des auftragsschrittprotokolls für Auftragsschritte, deren Besitzer, können nur anzeigen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returns-job-step-log-information-for-all-steps-in-a-specific-job"></a>A. Gibt Auftragsschritt-Protokollinformationen für alle Schritte in einem bestimmten Auftrag zurück  
 Im folgenden Beispiel werden alle Auftragsschrittinformationen für den Auftrag namens `Weekly Sales Data Backup` zurückgegeben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobsteplog  
    @job_name = N'Weekly Sales Data Backup' ;  
GO  
```  
  
### <a name="b-return-job-step-log-information-about-a-specific-job-step"></a>B. Zurückgeben von Auftragsschritt-Protokollinformationen zu einem bestimmten Auftragsschritt  
 Im folgenden Beispiel werden Auftragsschrittinformationen zum ersten Auftragsschritt des Auftrags namens `Weekly Sales Data Backup` zurückgegeben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_delete_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)   
 [SQL Server-Agent-gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
