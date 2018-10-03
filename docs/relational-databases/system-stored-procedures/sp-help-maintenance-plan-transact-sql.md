---
title: Sp_help_maintenance_plan (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_maintenance_plan_TSQL
- sp_help_maintenance_plan
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_maintenance_plan
ms.assetid: e972a510-960e-41d6-93c5-c71cd581a585
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 665d4de0f1ee61942e4f1af431889672bcc313bb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47757418"
---
# <a name="sphelpmaintenanceplan-transact-sql"></a>sp_help_maintenance_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zum angegebenen Wartungsplan zurück. Wenn kein Plan angegeben ist, gibt die gespeicherte Prozedur Informationen zu allen Wartungsplänen zurück.  
  
> **Hinweis:** diese gespeicherte Prozedur wird mit Datenbankwartungsplänen verwendet. Diese Funktion wurde durch Wartungspläne ersetzt, die nicht diese gespeicherte Prozedur verwenden. Verwenden Sie diese Prozedur, um Datenbankwartungspläne für Installationen bereitzustellen, die von einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisiert wurden.  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_maintenance_plan [ [ @plan_id = ] 'plan_id' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@plan_id =**] **'***plan_id***'**  
 Gibt die Plan-ID des Wartungsplans an. *Plan_id* ist **UNIQUEIDENTIFIER**. Die Standardeinstellung ist NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 None  
  
## <a name="result-sets"></a>Resultsets  
 Wenn *Plan_id* angegeben wird, **Sp_help_maintenance_plan** drei Tabellen zurück: Plan, Datenbank und Auftrag.  
  
### <a name="plan-table"></a>Plan-Tabelle  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|ID des Wartungsplans.|  
|**plan_name**|**sysname**|Name des Wartungsplans.|  
|**date_created**|**datetime**|Erstellungsdatum des Wartungsplans.|  
|**Besitzer**|**sysname**|Besitzer des Wartungsplans.|  
|**max_history_rows**|**int**|Maximale Anzahl von Zeilen, die für das Aufzeichnen des Wartungsplanverlaufs in der Systemtabelle zugeordnet werden.|  
|**remote_history_server**|**int**|Der Name des Remoteservers, zu dem der Verlaufsbericht geschrieben werden konnte.|  
|**max_remote_history_rows**|**int**|Maximale Anzahl von Zeilen, die in der Systemtabelle auf einem Remoteserver zugeordnet wurden und in die der Verlaufsbericht geschrieben werden konnte.|  
|**user_defined_1**|**int**|Der Standardwert ist NULL.|  
|**user_defined_2**|**nvarchar(100)**|Der Standardwert ist NULL.|  
|**user_defined_3**|**datetime**|Der Standardwert ist NULL.|  
|**user_defined_4**|**uniqueidentifier**|Der Standardwert ist NULL.|  
  
### <a name="database-table"></a>Database-Tabelle  
  
|Spaltenname|Description|  
|-----------------|-----------------|  
|**database_name**|Der Name jeder Datenbank, die dem Wartungsplan zugeordnet ist. *database_name* ist **sysname**|  
  
### <a name="job-table"></a>Job-Tabelle  
  
|Spaltenname|Description|  
|-----------------|-----------------|  
|**job_id**|Die ID jedes Auftrags, der dem Wartungsplan zugeordnet ist. *Job_id* ist **Uniqueidentifier**.|  
  
## <a name="remarks"></a>Hinweise  
 **Sp_help_maintenance_plan** befindet sich in der **Msdb** Datenbank.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_help_maintenance_plan**.  
  
## <a name="examples"></a>Beispiele  
 Dieses Beispiel enthält beschreibende Informationen zum Wartungsplan FAD6F2AB-3571-11D3-9D4A-00C04FB925FC.  
  
```  
EXECUTE   sp_help_maintenance_plan   
   N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Wartungspläne](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Datenbank-Wartungsplans gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
