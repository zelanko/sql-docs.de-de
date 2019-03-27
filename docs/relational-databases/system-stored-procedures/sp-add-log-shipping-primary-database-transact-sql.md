---
title: Sp_add_log_shipping_primary_database (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_primary_database
- sp_add_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_primary_database
ms.assetid: 69531611-113f-46b5-81a6-7bf496d0353c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 854edf82c32058c45df4ab4f71803933f59f2582
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494102"
---
# <a name="spaddlogshippingprimarydatabase-transact-sql"></a>sp_add_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Richtet die primäre Datenbank, einschließlich des Sicherungsauftrags sowie des lokalen und Remoteüberwachungseintrags, für eine Protokollversandkonfiguration ein.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_log_shipping_primary_database [ @database = ] 'database',   
[ @backup_directory = ] 'backup_directory',   
[ @backup_share = ] 'backup_share',   
[ @backup_job_name = ] 'backup_job_name',   
[, [ @backup_retention_period = ] backup_retention_period]  
[, [ @monitor_server = ] 'monitor_server']  
[, [ @monitor_server_security_mode = ] monitor_server_security_mode]  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @backup_threshold = ] backup_threshold ]   
[, [ @threshold_alert = ] threshold_alert ]   
[, [ @threshold_alert_enabled = ] threshold_alert_enabled ]   
[, [ @history_retention_period = ] history_retention_period ]  
[, [ @backup_job_id = ] backup_job_id OUTPUT ]  
[, [ @primary_id = ] primary_id OUTPUT]  
[, [ @backup_compression = ] backup_compression_option ]  
  
```  
  
## <a name="arguments"></a>Argumente  
`[ @database = ] 'database'` Ist der Name der Protokolldatei Protokollversand primären Datenbank. *database* ist vom Datentyp **sysname**, hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @backup_directory = ] 'backup_directory'` Ist der Pfad zum Sicherungsordner auf dem primären Server. *Backup_directory* ist **nvarchar(500)**, hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @backup_share = ] 'backup_share'` Ist Sie der Netzwerkpfad zum Sicherungsverzeichnis auf dem primären Server. *Backup_share* ist **nvarchar(500)**, hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @backup_job_name = ] 'backup_job_name'` Ist der Name des SQL Server-Agent-Auftrags auf dem primären Server, der die Sicherung in den Sicherungsordner kopiert. *Backup_job_name* ist **Sysname** und darf nicht NULL sein.  
  
`[ @backup_retention_period = ] backup_retention_period` Ist die Zeitdauer in Minuten, die Protokollsicherungsdatei im Sicherungsverzeichnis auf dem primären Server beibehalten werden sollen. *Backup_retention_period* ist **Int**, hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @monitor_server = ] 'monitor_server'` Ist der Name des Überwachungsservers. *Monitor_server* ist **Sysname**, hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @monitor_server_security_mode = ] monitor_server_security_mode` Der Sicherheitsmodus, der für die Verbindung mit dem Überwachungsserver verwendet wird.  
  
 1 = Windows-Authentifizierung  
  
 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. *monitor_server_security_mode* ist vom Datentyp **bit** und darf nicht NULL sein.  
  
`[ @monitor_server_login = ] 'monitor_server_login'` Ist der Benutzername des Kontos, auf dem Überwachungsserver verwendet.  
  
`[ @monitor_server_password = ] 'monitor_server_password'` Ist das Kennwort des Kontos, auf dem Überwachungsserver verwendet.  
  
`[ @backup_threshold = ] backup_threshold` Die Länge der Zeit in Minuten, nach der letzten Sicherung, bevor eine *Threshold_alert* Fehler ausgelöst. *Backup_threshold* ist **Int**, hat den Standardwert von 60 Minuten.  
  
`[ @threshold_alert = ] threshold_alert` Ist die Warnung, die bei Überschreitung des sicherungsschwellenwerts ausgelöst werden. *Threshold_alert* ist **Int**, hat den Standardwert 14,420.  
  
`[ @threshold_alert_enabled = ] threshold_alert_enabled` Gibt an, ob eine Warnung wird ausgelöst, wenn *Backup_threshold* überschritten wird. Der Standardwert null (0) bedeutet, dass die Warnung deaktiviert ist und nicht ausgelöst wird. *Threshold_alert_enabled* ist **Bit**.  
  
`[ @history_retention_period = ] history_retention_period` Ist die Zeitdauer in Minuten, die in denen der Verlauf beibehalten werden. *history_retention_period* ist vom Datentyp **int**. Der Standardwert ist NULL. Der Wert 14420 wird verwendet, falls kein anderer Wert angegeben wird.  
  
`[ @backup_job_id = ] backup_job_id OUTPUT` Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -agentauftrags-ID von der Sicherungsauftrag auf dem primären Server zugeordnet. *Backup_job_id* ist **Uniqueidentifier** und darf nicht NULL sein.  
  
`[ @primary_id = ] primary_id OUTPUT` Die ID der primären Datenbank in der Protokollversandkonfiguration. *primary_id* ist vom Datentyp **uniqueidentifier** und darf nicht NULL sein.  
  
`[ @backup_compression = ] backup_compression_option` Gibt an, ob eine Protokollversandkonfiguration verwendet [sicherungskomprimierung](../../relational-databases/backup-restore/backup-compression-sql-server.md). Dieser Parameter wird nur in [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (oder einer höheren Version) unterstützt.  
  
 0 = Deaktiviert. Protokollsicherungen nie komprimieren.  
  
 1 = Aktiviert. Protokollsicherungen immer komprimieren.  
  
 2 = Einstellung der der [anzeigen oder Konfigurieren der backup Compression Default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md). Dies ist der Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 **Sp_add_log_shipping_primary_database** muss ausgeführt werden, aus der **master** Datenbank auf dem primären Server. Diese gespeicherte Prozedur führt die folgenden Aktionen aus:  
  
1.  Generieren einer primären ID und fügt Sie einen Eintrag für die primäre Datenbank in der Tabelle **Log_shipping_primary_databases** unter Verwendung der angegebenen Argumente.  
  
2.  Erstellen eines Sicherungsauftrags für die primäre Datenbank, die deaktiviert ist.  
  
3.  Festlegen der Sicherungsauftrags-ID in der **Log_shipping_primary_databases** Eintrags, der die Auftrags-ID des Sicherungsauftrags.  
  
4.  Fügt einen lokalen Überwachungsdatensatz in der Tabelle **Log_shipping_monitor_primary** auf dem primären Server mithilfe bereitgestellter Argumente.  
  
5.  Falls der Überwachungsserver vom primären Server übereinstimmt, fügt ein Überwachungsdatensatzes **Log_shipping_monitor_primary** auf dem Überwachungsserver mithilfe angegebener Parameter.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank als primäre Datenbank in einer Protokollversandkonfiguration hinzugefügt.  
  
```  
DECLARE @LS_BackupJobId AS uniqueidentifier ;  
DECLARE @LS_PrimaryId AS uniqueidentifier ;  
  
EXEC master.dbo.sp_add_log_shipping_primary_database   
@database = N'AdventureWorks'   
,@backup_directory = N'c:\lsbackup'   
,@backup_share = N'\\tribeca\lsbackup'   
,@backup_job_name = N'LSBackup_AdventureWorks'   
,@backup_retention_period = 1440  
,@monitor_server = N'rockaway'   
,@monitor_server_security_mode = 1   
,@backup_threshold = 60   
,@threshold_alert = 0   
,@threshold_alert_enabled = 0   
,@history_retention_period = 1440   
,@backup_job_id = @LS_BackupJobId OUTPUT   
,@primary_id = @LS_PrimaryId OUTPUT   
,@overwrite = 1   
,@backup_compression = 0;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Über den Protokollversand &#40;SQLServer&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
