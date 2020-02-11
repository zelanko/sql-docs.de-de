---
title: sp_add_log_shipping_primary_database (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 5af11c14c7b0bf3b8e32d503c4b77e59623ce9ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68140446"
---
# <a name="sp_add_log_shipping_primary_database-transact-sql"></a>sp_add_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Richtet die primäre Datenbank, einschließlich des Sicherungsauftrags sowie des lokalen und Remoteüberwachungseintrags, für eine Protokollversandkonfiguration ein.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @database = ] 'database'`Der Name der primären Datenbank für den Protokoll Versand. *Database* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @backup_directory = ] 'backup_directory'`Der Pfad zum Sicherungsordner auf dem primären Server. *backup_directory* ist vom Datentyp **nvarchar (500)** und hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @backup_share = ] 'backup_share'`Der Netzwerkpfad zum Sicherungs Verzeichnis auf dem primären Server. *backup_share* ist vom Datentyp **nvarchar (500)** und hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @backup_job_name = ] 'backup_job_name'`Der Name des SQL Server-Agent Auftrags auf dem primären Server, der die Sicherung in den Sicherungsordner kopiert. *backup_job_name* ist vom **Datentyp vom Datentyp sysname** und darf nicht NULL sein.  
  
`[ @backup_retention_period = ] backup_retention_period`Der Zeitraum (in Minuten), in dem die Protokoll Sicherungsdatei im Sicherungs Verzeichnis auf dem primären Server beibehalten werden soll. *backup_retention_period* ist vom Datentyp **int**und hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @monitor_server = ] 'monitor_server'`Der Name des Überwachungs Servers. *Monitor_server* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @monitor_server_security_mode = ] monitor_server_security_mode`Der Sicherheitsmodus, der zum Herstellen der Verbindung mit dem Überwachungs Server verwendet wird.  
  
 1 = Windows-Authentifizierung  
  
 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. *monitor_server_security_mode* ist vom **Bit** und kann nicht NULL sein.  
  
`[ @monitor_server_login = ] 'monitor_server_login'`Der Benutzername des Kontos, das für den Zugriff auf den Überwachungs Server verwendet wird.  
  
`[ @monitor_server_password = ] 'monitor_server_password'`Das Kennwort des Kontos, das für den Zugriff auf den Überwachungs Server verwendet wird.  
  
`[ @backup_threshold = ] backup_threshold`Die Zeitspanne (in Minuten) nach der letzten Sicherung, bevor ein *threshold_alert* Fehler ausgelöst wird. *backup_threshold* ist vom Datentyp **int**, der Standardwert ist 60 Minuten.  
  
`[ @threshold_alert = ] threshold_alert`Die Warnung, die ausgelöst werden soll, wenn der Sicherungs Schwellenwert überschritten wird. *threshold_alert* ist vom Datentyp **int**und hat den Standardwert 14.420.  
  
`[ @threshold_alert_enabled = ] threshold_alert_enabled`Gibt an, ob eine Warnung ausgelöst wird, wenn *backup_threshold* überschritten wird. Der Standardwert null (0) bedeutet, dass die Warnung deaktiviert ist und nicht ausgelöst wird. *threshold_alert_enabled* ist **Bit**.  
  
`[ @history_retention_period = ] history_retention_period`Der Zeitraum in Minuten, in dem der Verlauf beibehalten wird. *history_retention_period* ist vom Datentyp **int**und hat den Standardwert NULL. Der Wert 14420 wird verwendet, falls kein anderer Wert angegeben wird.  
  
`[ @backup_job_id = ] backup_job_id OUTPUT`Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Auftrags-ID, die dem Sicherungsauftrag auf dem primären Server zugeordnet ist. *backup_job_id* ist vom Datentyp **uniqueidentifier** und darf nicht NULL sein.  
  
`[ @primary_id = ] primary_id OUTPUT`Die ID der primären Datenbank für die Protokoll Versand Konfiguration. *primary_id* ist vom Datentyp **uniqueidentifier** und darf nicht NULL sein.  
  
`[ @backup_compression = ] backup_compression_option`Gibt an, ob eine Protokoll Versand Konfiguration die [Sicherungs Komprimierung](../../relational-databases/backup-restore/backup-compression-sql-server.md)verwendet. Dieser Parameter wird nur in [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (oder einer höheren Version) unterstützt.  
  
 0 = Deaktiviert. Protokollsicherungen nie komprimieren.  
  
 1 = Aktiviert. Protokollsicherungen immer komprimieren.  
  
 2 = verwenden Sie die Einstellung der [Server Konfigurations Option "Standardeinstellung für die Sicherungs Komprimierung anzeigen oder konfigurieren](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)". Dies ist der Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_add_log_shipping_primary_database** muss von der **Master** -Datenbank auf dem primären Server ausgeführt werden. Diese gespeicherte Prozedur führt die folgenden Aktionen aus:  
  
1.  Generiert eine primäre ID und fügt einen Eintrag für die primäre Datenbank in der Tabelle **log_shipping_primary_databases** mit den bereitgestellten Argumenten hinzu.  
  
2.  Erstellen eines Sicherungsauftrags für die primäre Datenbank, die deaktiviert ist.  
  
3.  Legt die Sicherungsauftrags-ID im **log_shipping_primary_databases** Eintrag auf die Auftrags-ID des Sicherungsauftrags fest.  
  
4.  Fügt einen lokalen Überwachungsdaten Satz in der Tabelle **log_shipping_monitor_primary** auf dem primären Server mithilfe der angegebenen Argumente hinzu.  
  
5.  Wenn der Überwachungs Server nicht mit dem primären Server identisch ist, wird in **log_shipping_monitor_primary** auf dem Überwachungs Server ein Überwachungsdaten Satz mithilfe der angegebenen Argumente hinzugefügt.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
