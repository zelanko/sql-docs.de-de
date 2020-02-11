---
title: sp_help_log_shipping_primary_database (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_primary_database_TSQL
- sp_help_log_shipping_primary_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_primary_database
ms.assetid: e711b01c-ef29-4eb6-a016-0e647e337818
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9559a882da12c3e2a7a48a0aaa656a554633aa6f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937916"
---
# <a name="sp_help_log_shipping_primary_database-transact-sql"></a>sp_help_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ruft Einstellungen der primären Datenbank ab.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_log_shipping_primary_database  
[ @database = ] 'database' OR  
[ @primary_id = ] 'primary_id'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @database = ] 'database'`Der Name der primären Datenbank für den Protokoll Versand. *Database* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @primary_id = ] 'primary_id'`Die ID der primären Datenbank für die Protokoll Versand Konfiguration. *primary_id* ist vom Datentyp **uniqueidentifier** und darf nicht NULL sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|BESCHREIBUNG|  
|-----------------|-----------------|  
|**primary_id**|Die ID der primären Datenbank für die Protokollversandkonfiguration.|  
|**primary_database**|Der Name der primären Datenbank in der Protokollversandkonfiguration|  
|**backup_directory**|Das Verzeichnis, in dem die Dateien der Transaktionsprotokollsicherung gespeichert werden.|  
|**backup_share**|Der Netzwerk- oder UNC-Pfad zum Sicherungsverzeichnis.|  
|**backup_retention_period**|Gibt an, wie lange (in Minuten) eine Protokollsicherungsdatei im Sicherungsverzeichnis aufbewahrt wird, bevor sie gelöscht wird.|  
|**backup_compression**|Gibt an, ob die Protokollversandkonfiguration die [Sicherungskomprimierung](../../relational-databases/backup-restore/backup-compression-sql-server.md)verwendet.<br /><br /> **0** = deaktiviert. Protokollsicherungen nie komprimieren.<br /><br /> **1** = aktiviert. Protokollsicherungen immer komprimieren.<br /><br /> **2** = verwenden Sie die Einstellung der [Server Konfigurations Option "Standardeinstellung für die Sicherungs Komprimierung anzeigen oder konfigurieren](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)". Dies ist der Standardwert.<br /><br /> Die Sicherungskomprimierung wird erst ab [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] unterstützt. In allen anderen Versionen ist der Wert immer 2.|  
|**backup_job_id**|Die ID des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Auftrags, die dem Sicherungsauftrag auf dem primären Server zugeordnet ist.|  
|**monitor_server**|Der Name der Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , die als Überwachungsserver in der Protokollversandkonfiguration verwendet wird.|  
|**monitor_server_security_mode**|Der Sicherheitsmodus, der zum Herstellen einer Verbindung mit dem Überwachungsserver verwendet wird.<br /><br /> 1 = [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung<br /><br /> 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.|  
|**backup_threshold**|Die Anzahl von Minuten, die zwischen Sicherungsvorgängen verstreichen darf, bevor eine Warnung generiert wird.|  
|**threshold_alert**|Die Warnung, die bei Überschreiten des Sicherungsschwellenwertes ausgelöst wird.|  
|**threshold_alert_enabled**|Bestimmt, ob Warnungen für Sicherungsschwellenwerte aktiviert sind.<br /><br /> **1** = aktiviert.<br /><br /> **0** = deaktiviert.|  
|**last_backup_file**|Der absolute Pfad der jüngsten Transaktionsprotokollsicherung.|  
|**last_backup_date**|Uhrzeit und Datum des letzten Protokollsicherungsvorgangs.|  
|**last_backup_date_utc**|Die Uhrzeit und das Datum der letzten Transaktionsprotokollsicherung in der primären Datenbank in UTC.|  
|**history_retention_period**|Der Zeitraum in Minuten, den Verlaufsdatensätze des Protokollversands für eine bestimmte primäre Datenbank aufbewahrt werden, ehe sie gelöscht werden.|  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_help_log_shipping_primary_database** muss von der **Master** -Datenbank auf dem primären Server ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird die Verwendung von **sp_help_log_shipping_primary_database** zum Abrufen der Einstellungen der primären Datenbank für die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank erläutert.  
  
```  
EXEC master.dbo.sp_help_log_shipping_primary_database @database=N'AdventureWorks2012';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
