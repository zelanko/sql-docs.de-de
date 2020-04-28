---
title: dbo. cdc_jobs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc_jobs
- cdc_jobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dbo.cdc_jobs
ms.assetid: 85e2d580-1c54-4b81-b7e6-2e12997199fd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0c9668c234728dc34952a7095889fe6ba5cfd06a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68084704"
---
# <a name="dbocdc_jobs-transact-sql"></a>dbo.cdc_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Speichert die Change Data Capture-Konfigurationsparameter für Aufzeichnungs- und Cleanupaufträge. Diese Tabelle wird in **msdb**gespeichert.  
  
 
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID der Datenbank, in der der Auftrag ausgeführt wird.|  
|**job_type**|**nvarchar (20)**|Typ des Auftrags, entweder 'capture' oder 'cleanup'.|  
|**job_id**|**uniqueidentifier**|Dem Auftrag zugeordnete eindeutige ID.|  
|**maxtrans**|**int**|Die maximale Anzahl von Transaktionen, die in jedem Scanvorgang verarbeitet werden sollen.<br /><br /> **maxtrans** ist nur für Aufzeichnungs Aufträge gültig.|  
|**maxscans**|**int**|Die maximale Anzahl der Scan Zyklen, die ausgeführt werden müssen, um alle Zeilen aus dem Protokoll zu extrahieren.<br /><br /> **maxscans** ist nur für Aufzeichnungs Aufträge gültig.|  
|**Continuous**|**bit**|Flag, das angibt, ob der Aufzeichnungsauftrag fortlaufend (1) oder einmalig (0) ausgeführt werden soll. Weitere Informationen finden Sie unter [sys. sp_cdc_add_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md).<br /><br /> **Continuous** ist nur für Aufzeichnungs Aufträge gültig.|  
|**PollingInterval**|**bigint**|Anzahl der Sekunden zwischen Protokollscanzyklen.<br /><br /> **PollingInterval** ist nur für Aufzeichnungs Aufträge gültig.|  
|**zurück**|**bigint**|Anzahl der Minuten, die Änderungszeilen in Änderungstabellen beibehalten werden sollen.<br /><br /> die **Beibehaltung** ist nur für Cleanupaufträge gültig.|  
|**Mindest**|**bigint**|Die maximale Anzahl von Einträgen für Löschvorgänge, die mit einer einzelnen Anweisung beim Cleanup gelöscht werden können.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. sp_cdc_add_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)   
 [sys. sp_cdc_change_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md)   
 [sys. sp_cdc_help_jobs &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)   
 [sys. sp_cdc_drop_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-drop-job-transact-sql.md)  
  
  
