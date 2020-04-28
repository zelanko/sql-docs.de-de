---
title: sp_help_maintenance_plan (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 42a98fe7af16c4e8aab22d6ace02f359dfe02c54
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68096203"
---
# <a name="sp_help_maintenance_plan-transact-sql"></a>sp_help_maintenance_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zum angegebenen Wartungsplan zurück. Wenn kein Plan angegeben ist, gibt die gespeicherte Prozedur Informationen zu allen Wartungsplänen zurück.  
  
> **Hinweis:** Diese gespeicherte Prozedur wird mit Daten Bank Wartungsplänen verwendet. Diese Funktion wurde durch Wartungspläne ersetzt, die nicht diese gespeicherte Prozedur verwenden. Verwenden Sie diese Prozedur, um Datenbankwartungspläne für Installationen bereitzustellen, die von einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aktualisiert wurden.  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_maintenance_plan [ [ @plan_id = ] 'plan_id' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @plan_id = ] 'plan\_id'`Gibt die Plan-ID des Wartungsplans an. *plan_id* ist vom Datentyp **uniqueidentifier**. Die Standardeinstellung ist NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
 Wenn *plan_id* angegeben wird, werden von **sp_help_maintenance_plan** drei Tabellen zurückgegeben: Plan, Datenbank und Job.  
  
### <a name="plan-table"></a>Plan-Tabelle  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|ID des Wartungsplans.|  
|**plan_name**|**sysname**|Name des Wartungsplans.|  
|**date_created**|**datetime**|Erstellungsdatum des Wartungsplans.|  
|**Eigentor**|**sysname**|Besitzer des Wartungsplans.|  
|**max_history_rows**|**int**|Maximale Anzahl von Zeilen, die für das Aufzeichnen des Wartungsplanverlaufs in der Systemtabelle zugeordnet werden.|  
|**remote_history_server**|**int**|Der Name des Remote Servers, auf den der Verlaufs Bericht geschrieben werden konnte.|  
|**max_remote_history_rows**|**int**|Maximale Anzahl von Zeilen, die in der Systemtabelle auf einem Remoteserver zugeordnet wurden und in die der Verlaufsbericht geschrieben werden konnte.|  
|**user_defined_1**|**int**|Der Standardwert ist NULL.|  
|**user_defined_2**|**nvarchar (100)**|Der Standardwert ist NULL.|  
|**user_defined_3**|**datetime**|Der Standardwert ist NULL.|  
|**user_defined_4**|**uniqueidentifier**|Der Standardwert ist NULL.|  
  
### <a name="database-table"></a>Database-Tabelle  
  
|Spaltenname|BESCHREIBUNG|  
|-----------------|-----------------|  
|**database_name**|Der Name jeder Datenbank, die dem Wartungsplan zugeordnet ist. *database_name* ist **sysname**|  
  
### <a name="job-table"></a>Job-Tabelle  
  
|Spaltenname|BESCHREIBUNG|  
|-----------------|-----------------|  
|**job_id**|Die ID jedes Auftrags, der dem Wartungsplan zugeordnet ist. *job_id* ist vom Datentyp **uniqueidentifier**.|  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_help_maintenance_plan** in der **msdb** -Datenbank.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_help_maintenance_plan**ausführen.  
  
## <a name="examples"></a>Beispiele  
 Dieses Beispiel enthält beschreibende Informationen zum Wartungsplan FAD6F2AB-3571-11D3-9D4A-00C04FB925FC.  
  
```  
EXECUTE   sp_help_maintenance_plan   
   N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wartungspläne](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Gespeicherte Prozeduren für Datenbank-Wartungspläne &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
