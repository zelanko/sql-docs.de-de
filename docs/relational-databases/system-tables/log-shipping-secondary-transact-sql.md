---
title: log_shipping_secondary (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_secondary
- log_shipping_secondary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_secondary system table
ms.assetid: 69723419-4544-49c6-a517-adb30ffa5741
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5debab1572bc2f788c0dc13773d0dc140c693108
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82805947"
---
# <a name="log_shipping_secondary-transact-sql"></a>log_shipping_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Speichert einen Datensatz pro sekundärer ID. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**secondary_id**|**uniqueidentifier**|Die ID für den sekundären Server in der Protokollversandkonfiguration.|  
|**primary_server**|**sysname**|Der Name der primären Instanz der SQL Server-Datenbank-Engine in der Protokollversandkonfiguration|  
|**primary_database**|**sysname**|Der Name der primären Datenbank in der Protokollversandkonfiguration|  
|**backup_source_directory**|**nvarchar (500)**|Das Verzeichnis, in dem die Dateien der Transaktionsprotokollsicherung gespeichert werden.|  
|**backup_destination_directory**|**nvarchar (500)**|Das Verzeichnis auf dem sekundären Server, in das Sicherungsdateien kopiert werden|  
|**file_retention_period**|**int**|Gibt an, wie lange (in Minuten) eine Sicherungsdatei auf dem sekundären Server aufbewahrt wird, bevor sie gelöscht wird|  
|**copy_job_id**|**uniqueidentifier**|Die dem Kopierauftrag zugeordnete ID auf dem sekundären Server|  
|**restore_job_id**|**uniqueidentifier**|Die dem Wiederherstellungsauftrag zugeordnete ID auf dem sekundären Server|  
|**monitor_server**|**sysname**|Der Name der Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , die als Überwachungsserver in der Protokollversandkonfiguration verwendet wird.|  
|**monitor_server_security_mode**|**bit**|Der Sicherheitsmodus, der zum Herstellen einer Verbindung mit dem Überwachungsserver verwendet wird.<br /><br /> 1 = Windows-Authentifizierung<br /><br /> 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.|  
|**last_copied_file**|**nvarchar (500)**|Der Dateiname der letzten Sicherungsdatei, die auf den sekundären Server kopiert wurde.|  
|**last_copied_date**|**datetime**|Datum und Uhrzeit des letzten Kopiervorgangs auf den sekundären Server|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn es für eine bestimmte primäre Datenbank mehrere sekundäre Datenbanken auf demselben sekundären Server gibt, nutzen diese einige Einstellungen in der **log_shipping_secondary** -Tabelle gemeinsam. Wenn eine freigegebene Einstellung für eine der Datenbanken geändert wird, ändert sich diese Einstellung für alle Datenbanken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokoll Versand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_secondary_database &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_change_log_shipping_secondary_database &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
