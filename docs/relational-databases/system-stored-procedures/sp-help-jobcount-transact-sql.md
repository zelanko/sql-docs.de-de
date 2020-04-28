---
title: sp_help_jobcount (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobcount
- sp_help_jobcount_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobcount
ms.assetid: ae8ef851-646c-4889-bc11-c8ec78762572
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f874aa26001b7d595f319a59d5c116907aa096e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68054960"
---
# <a name="sp_help_jobcount-transact-sql"></a>sp_help_jobcount (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Anzahl von Aufträgen an, an die ein Zeitplan angefügt ist.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_jobcount   
     [ @schedule_name = ] 'schedule_name' ,  
     [ @schedule_id = ] schedule_id   
```  
  
## <a name="arguments"></a>Argumente  
`[ @schedule_id = ] schedule_id`Der Bezeichner des aufzulistenden Zeitplans. *schedule_id* ist vom Datentyp **int**und hat keinen Standardwert. Es können entweder *schedule_id* oder *schedule_name* angegeben werden.  
  
`[ @schedule_name = ] 'schedule_name'`Der Name des Zeitplans, der aufgelistet werden soll. *schedule_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Es können entweder *schedule_id* oder *schedule_name* angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Gibt das folgende Resultset zurück:  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**JOBCOUNT**|**int**|Anzahl von Aufträgen für den angegebenen Zeitplan.|  
  
## <a name="remarks"></a>Bemerkungen  
 In dieser Prozedur wird die Anzahl von Aufträgen aufgelistet, die an den angegebenen Zeitplan angefügt sind.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder von **sysadmin** können die Anzahl von Aufträgen anzeigen, die sich im Besitz anderer Personen befinden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Anzahl der dem Zeitplan `NightlyJobs` angefügten Aufträge aufgelistet.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_jobcount  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
  
