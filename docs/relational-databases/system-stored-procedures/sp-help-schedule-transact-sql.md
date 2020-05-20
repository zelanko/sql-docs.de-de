---
title: sp_help_schedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_schedule
- sp_help_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_schedule
ms.assetid: b2fc4ce1-0a8e-44d2-b206-7dc7b258d8c9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ce8c1514a0c62eeb11743d86dd6922cf4995c63c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828403"
---
# <a name="sp_help_schedule-transact-sql"></a>sp_help_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Listet Informationen zu Zeitplänen auf.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_schedule   
     [ @schedule_id = ] id ,  
     [ @schedule_name = ] 'schedule_name'   
     [ , [ @attached_schedules_only = ] attached_schedules_only ]  
     [ , [ @include_description = ] include_description ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @schedule_id = ] id`Der Bezeichner des aufzulistenden Zeitplans. *schedule_name* ist vom Datentyp **int**und hat keinen Standardwert. Es können entweder *schedule_id* oder *schedule_name* angegeben werden.  
  
`[ @schedule_name = ] 'schedule_name'`Der Name des Zeitplans, der aufgelistet werden soll. *schedule_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Es können entweder *schedule_id* oder *schedule_name* angegeben werden.  
  
`[ @attached_schedules_only = ] attached_schedules_only ]`Gibt an, ob nur Zeitpläne angezeigt werden sollen, an die ein Auftrag angefügt ist. *attached_schedules_only* ist vom Typ **Bit**. der Standardwert ist **0**. Wenn *attached_schedules_only* **0**ist, werden alle Zeitpläne angezeigt. Wenn *attached_schedules_only* **1**ist, enthält das Resultset nur Zeitpläne, die an einen Auftrag angefügt sind.  
  
`[ @include_description = ] include_description`Gibt an, ob Beschreibungen in das Resultset eingeschlossen werden sollen. *include_description* ist vom Typ **Bit**. der Standardwert ist **0**. Wenn *include_description* **0**ist, enthält die *schedule_description* Spalte des Resultsets einen Platzhalter. Wenn *include_description* **1**ist, wird die Beschreibung des Zeitplans in das Resultset eingeschlossen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Diese Prozedur gibt das folgende Resultset zurück:  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|ID des Zeitplans.|  
|**schedule_uid**|**uniqueidentifier**|Bezeichner für den Zeitplan.|  
|**schedule_name**|**sysname**|Name des Zeitplans.|  
|**wodurch**|**int**|Gibt an, ob der Zeitplan aktiviert (**1**) oder nicht aktiviert (**0**) ist.|  
|**freq_type**|**int**|Der Wert, der angibt, wann der Auftrag ausgeführt werden soll.<br /><br /> **1** = einmal<br /><br /> **4** = täglich<br /><br /> **8** = wöchentlich<br /><br /> **16** = monatlich<br /><br /> **32** = monatlich, relativ zum **freq_interval**<br /><br /> **64** = ausführen, wenn der SQLServerAgent-Dienst gestartet wird.|  
|**freq_interval**|**int**|Tage, an denen der Auftrag ausgeführt wird. Der Wert hängt vom Wert **freq_type**ab. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_subday_type**|**int**|Einheiten für **freq_subday_interval**. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_subday_interval**|**int**|Anzahl der **freq_subday_type** Zeiträume zwischen den einzelnen Ausführungen des Auftrags. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_relative_interval**|**int**|Das Vorkommen des **freq_interval** eines geplanten Auftrags in jedem Monat. Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_recurrence_factor**|**int**|Anzahl der Monate zwischen der geplanten Ausführung des Auftrags|  
|**active_start_date**|**int**|Datum, an dem der Zeitplan aktiviert wird.|  
|**active_end_date**|**int**|Enddatum für den Zeitplan.|  
|**active_start_time**|**int**|Uhrzeit, zu der der Zeitplan gestartet wird.|  
|**active_end_time**|**int**|Uhrzeit, zu der der Zeitplan beendet wird.|  
|**date_created**|**datetime**|Datum, an dem der Zeitplan erstellt wird|  
|**schedule_description**|**nvarchar(4000)**|Eine Beschreibung des Zeitplans in englischer Sprache (falls angefordert).|  
|**job_count**|**int**|Gibt die Anzahl von Aufträgen zurück, die auf diesen Zeitplan verweisen.|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn keine Parameter angegeben werden, werden in **sp_help_schedule** Informationen zu allen Zeitplänen in der-Instanz aufgelistet.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Mitglieder von **SQLAgentUserRole** können nur die Zeitpläne anzeigen, deren Besitzer Sie sind.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-information-for-all-schedules-in-the-instance"></a>A. Auflisten der Informationen für alle Zeitpläne in der Instanz  
 Im folgenden Beispiel werden die Informationen für alle Zeitpläne in der Instanz aufgelistet.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_schedule ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-schedule"></a>B. Auflisten der Informationen für einen bestimmten Zeitplan  
 Im folgenden Beispiel werden Informationen zum Zeitplan `NightlyJobs` aufgelistet.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_schedule  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
  
