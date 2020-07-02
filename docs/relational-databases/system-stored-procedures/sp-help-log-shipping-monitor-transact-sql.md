---
title: sp_help_log_shipping_monitor (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_monitor_TSQL
- sp_help_log_shipping_monitor
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_monitor
ms.assetid: a4e96c45-6dcd-471a-a494-b5c619459855
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bf5b4c74b39c9326382089579e111b118235170
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715851"
---
# <a name="sp_help_log_shipping_monitor-transact-sql"></a>sp_help_log_shipping_monitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt ein Resultset mit Status- und anderen Informationen für registrierte primäre und sekundäre Datenbanken auf einem primären, sekundären oder Überwachungsserver zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_log_shipping_monitor  
```  
  
## <a name="arguments"></a>Argumente  
 Keine.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**status**|**bit**|Gemeinsamer Status der Agents für die Protokollversand-Datenbank:<br /><br /> **0** = fehlerfrei und ohne Agent-Fehler.<br /><br /> **1** = sonstiger Status.|  
|**is_primary**|**bit**|Gibt an, ob diese Zeile für eine primäre Datenbank gilt:<br /><br /> **1** = Die Zeile gilt für eine primäre Datenbank.<br /><br /> **0** = Die Zeile gilt für eine sekundäre Datenbank.|  
|**server**|**sysname**|Der Name des primären oder sekundären Servers, auf dem sich diese Datenbank befindet.|  
|**database_name**|**sysname**|Der Datenbankname.|  
|**time_since_last_backup**|**int**|Die Zeitdauer in Minuten seit der letzten Protokollsicherung.<br /><br /> NULL = Die Informationen sind nicht verfügbar oder nicht von Bedeutung.|  
|**last_backup_file**|**nvarchar (500)**|Der Name der letzten erfolgreich erstellten Protokollsicherungsdatei.<br /><br /> NULL = Die Informationen sind nicht verfügbar oder nicht von Bedeutung.|  
|**backup_threshold**|**int**|Die Zeit (in Minuten) seit der letzten Sicherung, nach der ein threshold_alert-Fehler ausgelöst wird. **backup_threshold** ist **int**, mit einem Standardwert von **60 Minuten**.<br /><br /> NULL = Die Informationen sind nicht verfügbar oder nicht von Bedeutung.<br /><br /> Dieser Wert kann mit [sp_add_log_shipping_primary_database &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md)geändert werden.|  
|**is_backup_alert_enabled**|**bit**|Gibt an, ob eine Warnung ausgelöst wird, wenn **backup_threshold** überschritten wird. Der Standardwert**1**bedeutet, dass die Warnung ausgelöst wird.<br /><br /> NULL = Die Informationen sind nicht verfügbar oder nicht von Bedeutung.<br /><br /> Dieser Wert kann mit [sp_add_log_shipping_primary_database &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md)geändert werden.|  
|**time_since_last_copy**|**int**|Die Zeitdauer in Minuten seit der letzten Kopie der Protokollsicherung.<br /><br /> NULL = Die Informationen sind nicht verfügbar oder nicht von Bedeutung.|  
|**last_copied_file**|**nvarchar (500)**|Der Name der letzten erfolgreich kopierten Protokollsicherungsdatei.<br /><br /> NULL = Die Informationen sind nicht verfügbar oder nicht von Bedeutung.|  
|**time_since_last_restore**|**int**|Die Zeitdauer in Minuten seit der letzten Wiederherstellung der Protokollsicherung.<br /><br /> NULL = Die Informationen sind nicht verfügbar oder nicht von Bedeutung.|  
|**last_restored_file**|**nvarchar (500).**|Der Name der letzten erfolgreich wiederhergestellten Protokollsicherungsdatei.<br /><br /> NULL = Die Informationen sind nicht verfügbar oder nicht von Bedeutung.|  
|**last_restored_latency**|**int**|Die Zeitdauer in Minuten von der Erstellung der letzten Sicherung bis zur Wiederherstellung der Sicherung.<br /><br /> NULL = Die Informationen sind nicht verfügbar oder nicht von Bedeutung.|  
|**restore_threshold**|**int**|Die Anzahl der zulässigen Minuten zwischen Wiederherstellungsvorgängen, bevor eine Warnung generiert wird. **restore_threshold** kann nicht NULL sein.|  
|**is_restore_alert_enabled**|**bit**|Gibt an, ob eine Warnung ausgegeben wird, wenn **restore_threshold** überschritten wird. Der Wert eins (**1**), der Standardwert, bedeutet, dass die Warnung ausgelöst wird.<br /><br /> NULL = Die Informationen sind nicht verfügbar oder nicht von Bedeutung.<br /><br /> Verwenden Sie [sp_add_log_shipping_secondary_database](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md), um die Wiederherstellungsschwelle festzulegen.|  
  
## <a name="remarks"></a>Hinweise  
 **sp_help_log_shipping_monitor** muss in der **master** -Datenbank auf dem Überwachungsserver ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **sysadmin** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
