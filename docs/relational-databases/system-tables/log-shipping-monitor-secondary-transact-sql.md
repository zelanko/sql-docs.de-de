---
title: log_shipping_monitor_secondary (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_secondary_TSQL
- log_shipping_monitor_secondary
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_secondary system table
ms.assetid: afbe1bb7-89a7-4020-9408-0af64a043c2e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dd35759cfc37f504adc7adcccdbc863525bfa175
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82813290"
---
# <a name="log_shipping_monitor_secondary-transact-sql"></a>log_shipping_monitor_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Speichert einen Überwachungsdatensatz pro sekundärer Datenbank in einer Protokollversandkonfiguration. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
 Die verlaufs- und überwachungsverbundenen Tabellen werden auch auf dem primären und dem sekundären Server verwendet.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**secondary_server**|**sysname**|Der Name der sekundären Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in der Protokoll Versand Konfiguration.|  
|**secondary_database**|**sysname**|Der Name der sekundären Datenbank in der Protokollversandkonfiguration.|  
|**secondary_id**|**uniqueidentifier**|Die ID für den sekundären Server in der Protokollversandkonfiguration.|  
|**primary_server**|**sysname**|Der Name der primären Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in der Protokollversandkonfiguration.|  
|**primary_database**|**sysname**|Der Name der primären Datenbank in der Protokollversandkonfiguration|  
|**restore_threshold**|**int**|Die Anzahl der zulässigen Minuten zwischen Wiederherstellungsvorgängen, bevor eine Warnung generiert wird.|  
|**threshold_alert**|**int**|Die Warnung, die ausgelöst wird, wenn die Wiederherstellungsschwelle überschritten wird.|  
|**threshold_alert_enabled**|**bit**|Legt fest, ob Warnungen für Wiederherstellungsschwellen aktiviert sind. 1 = Aktiviert.<br /><br /> 0 = Deaktiviert.|  
|**last_copied_file**|**nvarchar (500)**|Der Dateiname der letzten Sicherungsdatei, die auf den sekundären Server kopiert wurde.|  
|**last_copied_date**|**datetime**|Datum und Uhrzeit des letzten Kopiervorgangs auf den sekundären Server|  
|**last_copied_date_utc**|**datetime**|Datum und Uhrzeit des letzten Kopiervorgangs auf den sekundären Server in UTC (Coordinated Universal Time).|  
|**last_restored_file**|**nvarchar (500)**|Der Dateiname der letzten Sicherungsdatei, die in der sekundären Datenbank wiederhergestellt wurde.|  
|**last_restored_date**|**datetime**|Datum und Uhrzeit des letzten Wiederherstellungsvorgangs für die sekundäre Datenbank.|  
|**last_restored_date_utc**|**datetime**|Datum und Uhrzeit des letzten Wiederherstellungsvorgangs auf dem sekundären Server in UTC (Coordinated Universal Time).|  
|**last_restored_latency**|**int**|Der Zeitraum in Minuten zwischen dem Erstellen der Protokollsicherung auf dem primären Server und dem Wiederherstellen auf dem sekundären Server.<br /><br /> Der Anfangswert ist NULL.|  
|**history_retention_period**|**int**|Die Zeitdauer in Minuten, die Verlaufsdatensätze des Protokollversands für eine bestimmte sekundäre Datenbank vor dem Löschen aufbewahrt werden.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die mit einem sekundären Server verbundenen Informationen werden sowohl auf dem Remoteüberwachungsserver als auch auf dem sekundären Server in der **log_shipping_monitor_secondary** -Tabelle gespeichert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokoll Versand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [sp_add_log_shipping_secondary_database &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_change_log_shipping_secondary_database &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_monitor_secondary &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
