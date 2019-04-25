---
title: dbo.sysjobhistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobhistory_TSQL
- dbo.sysjobhistory
- sysjobhistory
- sysjobhistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobhistory system table
ms.assetid: 1b1fcdbb-2af2-45e6-bf3f-e8279432ce13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1797fb6183863bb0249bd0cda6024d0e95914e82
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62470848"
---
# <a name="dbosysjobhistory-transact-sql"></a>dbo.sysjobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält Informationen zur Ausführung geplanter Aufträge durch den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
> **HINWEIS:** Daten werden aktualisiert, nur, nachdem der Jobstep abgeschlossen wurde.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Eindeutiger Bezeichner für die Zeile.|  
|**job_id**|**uniqueidentifier**|Auftrags-ID.|  
|**step_id**|**int**|ID des Schritts im Auftrag.|  
|**step_name**|**sysname**|Name des Schritts|  
|**sql_message_id**|**int**|ID einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlermeldung, die beim Fehlschlagen des Auftrags zurückgegeben wird.|  
|**sql_severity**|**int**|Schweregrad eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlers.|  
|**Nachricht**|**nvarchar(4000)**|Text (falls vorhanden) eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlers.|  
|**run_status**|**int**|Status der Auftragsausführung:<br /><br /> **0** = Fehler<br /><br /> **1** = war erfolgreich<br /><br /> **2** = wiederholen<br /><br /> **3** = abgebrochen<br /><br /> **4** = wird ausgeführt|  
|**run_date**|**int**|Datum, an dem die Ausführung des Auftrags oder Schrittes gestartet wurde. Bei einem In-Progress-Verlauf ist dies das Datum/die Uhrzeit, an dem bzw. zu der der Verlauf geschrieben wurde.|  
|**run_time**|**int**|Uhrzeit, zu der der Auftrag oder Schritt gestartet wurde.|  
|**run_duration**|**int**|Verstrichene Zeit bei der Ausführung des Auftrags oder Schritts im **HHMMSS** Format.|  
|**operator_id_emailed**|**int**|ID des Operators, der bei Abschluss des Auftrags benachrichtigt wurde.|  
|**operator_id_netsent**|**int**|ID des Operators, der bei Abschluss des Auftrags durch eine Meldung benachrichtigt wurde.|  
|**operator_id_paged**|**int**|ID des Operators, der mithilfe eines Pagers bei Abschluss des Auftrags benachrichtigt wurde.|  
|**retries_attempted**|**int**|Anzahl der Wiederholungsversuche für den Auftrag oder Schritt.|  
|**server**|**sysname**|Name des Servers, auf dem der Auftrag ausgeführt wurde.|  
  
  ## <a name="example"></a>Beispiel
 Die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] Abfrage konvertiert die **Run_time** und **Run_duration** Spalten in einem benutzerfreundlicheren Format.  Führen Sie das Skript in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
 
 ```sql
 SET NOCOUNT ON;
 
 SELECT sj.name,
        sh.run_date,
        sh.step_name,
        STUFF(STUFF(RIGHT(REPLICATE('0', 6) +  CAST(sh.run_time as varchar(6)), 6), 3, 0, ':'), 6, 0, ':') 'run_time',
        STUFF(STUFF(STUFF(RIGHT(REPLICATE('0', 8) + CAST(sh.run_duration as varchar(8)), 8), 3, 0, ':'), 6, 0, ':'), 9, 0, ':') 'run_duration (DD:HH:MM:SS)  '
FROM msdb.dbo.sysjobs sj
JOIN msdb.dbo.sysjobhistory sh
ON sj.job_id = sh.job_id
```
