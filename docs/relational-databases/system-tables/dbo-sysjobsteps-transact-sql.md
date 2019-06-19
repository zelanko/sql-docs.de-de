---
title: dbo.sysjobsteps (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobsteps
- dbo.sysjobsteps_TSQL
- sysjobsteps
- sysjobsteps_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobsteps system table
ms.assetid: 978b8205-535b-461c-91f3-af9b08eca467
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a9264ed33ffeea224f69b8a880e235753ead1467
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62470745"
---
# <a name="dbosysjobsteps-transact-sql"></a>dbo.sysjobsteps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält die Informationen für jeden Schritt in einem Auftrag, der vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent ausgeführt werden soll. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ID des Auftrags.|  
|**step_id**|**int**|ID des Schritts im Auftrag.|  
|**step_name**|**sysname**|Der Name des Auftragsschritts.|  
|**subsystem**|**nvarchar(40)**|Name des vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent zur Ausführung des Auftragsschritts verwendeten Subsystems.|  
|**Befehl**|**nvarchar(max)**|Der Befehl ausgeführt werden soll **Subsystem**.|  
|**flags**|**int**|Reserviert.|  
|**additional_parameters**|**ntext**|Reserviert.|  
|**cmdexec_success_code**|**int**|Auf der Fehlerebene Rückgabewert **CmdExec** -Subsystemschritten, um den Erfolg mitzuteilen.|  
|**on_success_action**|**tinyint**|Aktion, die nach erfolgreicher Ausführung eines Schritts durchzuführen ist.|  
|**on_success_step_id**|**int**|ID des Schritts, der als Nächstes auszuführen ist, nachdem ein Schritt erfolgreich ausgeführt wurde.|  
|**on_fail_action**|**tinyint**|Aktion, die durchzuführen ist, wenn ein Schritt nicht erfolgreich ausgeführt wurde.|  
|**on_fail_step_id**|**int**|ID des Schritts, der als Nächstes auszuführen ist, wenn ein Schritt nicht erfolgreich ausgeführt wurde.|  
|**server**|**sysname**|Reserviert.|  
|**database_name**|**sysname**|Name der Datenbank, in der **Befehl** wird ausgeführt, wenn **Subsystem** TSQL ist.|  
|**database_user_name**|**sysname**|Name des Datenbankbenutzers, dessen Konto verwendet wird, wenn der Schritt ausgeführt wird.|  
|**retry_attempts**|**int**|Anzahl der Wiederholungsversuche, wenn der Schritt einen Fehler erzeugt.|  
|**retry_interval**|**int**|Zeit, die zwischen Wiederholungsversuchen gewartet wird.|  
|**os_run_priority**|**int**|Reserviert.|  
|**output_file_name**|**nvarchar(200)**|Name der Datei, in dem die Ausgabe des Schritts, gespeichert wird, wenn **Subsystem** Wert TSQL, PowerShell oder **CmdExec** _._|  
|**last_run_outcome**|**int**|Ergebnis der vorherigen Ausführung des Auftragsschritts.<br /><br /> **0** = Fehler<br /><br /> **1** = war erfolgreich<br /><br /> **2** = wiederholen<br /><br /> **3** = abgebrochen<br /><br /> **5** = unbekannt|  
|**last_run_duration**|**int**|Dauer (hhmmss) der letzten Ausführung des Schritts.|  
|**last_run_retries**|**int**|Anzahl der Wiederholungsversuche bei der letzten Ausführung des Auftragsschritts.|  
|**last_run_date**|**int**|Datum (yyymmdd), an dem die Ausführung des Schritts zuletzt gestartet wurde.|  
|**last_run_time**|**int**|Uhrzeit (hhmmss), zu der die Ausführung des Schritts zuletzt gestartet wurde.|  
|**proxy_id**|**int**|Proxy für den Auftragsschritt.|  
|**step_uid**|**uniqueidentifier**|ID für den Auftragsschritt.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Agent-Tabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
