---
title: sp_change_log_shipping_primary_database (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_primary_database
- sp_change_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_primary_database
ms.assetid: 8c9dce6b-d2a3-4ca7-a832-8f59a5adb214
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 02ba9c11d9c74daa6cc88051ada7037edc16f35b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715926"
---
# <a name="sp_change_log_shipping_primary_database-transact-sql"></a>sp_change_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Ändert die Einstellungen primärer Datenbanken.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_change_log_shipping_primary_database [ @database = ] 'database'  
[, [ @backup_directory = ] 'backup_directory']   
[, [ @backup_share = ] 'backup_share']   
[, [ @backup_retention_period = ] 'backup_retention_period']  
[, [ @monitor_server_security_mode = ] 'monitor_server_security_mode']  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @backup_threshold = ] 'backup_threshold']   
[, [ @threshold_alert = ] 'threshold_alert']   
[, [ @threshold_alert_enabled = ] 'threshold_alert_enabled']   
[, [ @history_retention_period = ] 'history_retention_period']  
[, [ @backup_compression = ] backup_compression_option ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @database = ] 'database'`Der Name der Datenbank auf dem primären Server. *primary_database* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
`[ @backup_directory = ] 'backup_directory'`Der Pfad zum Sicherungsordner auf dem primären Server. *backup_directory* ist vom Datentyp **nvarchar (500)** und hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @backup_share = ] 'backup_share'`Der Netzwerkpfad zum Sicherungs Verzeichnis auf dem primären Server. *backup_share* ist vom Datentyp **nvarchar (500)** und hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @backup_retention_period = ] 'backup_retention_period'`Der Zeitraum (in Minuten), in dem die Protokoll Sicherungsdatei im Sicherungs Verzeichnis auf dem primären Server beibehalten werden soll. *backup_retention_period* ist vom Datentyp **int**und hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @monitor_server_security_mode = ] 'monitor_server_security_mode'`Der Sicherheitsmodus, der zum Herstellen der Verbindung mit dem Überwachungs Server verwendet wird.  
  
 1 = Windows-Authentifizierung  
  
 0 = SQL Server-Authentifizierung  
  
 *monitor_server_security_mode* ist vom Datentyp **bit** und darf nicht NULL sein.  
  
`[ @monitor_server_login = ] 'monitor_server_login'`Der Benutzername des Kontos, das für den Zugriff auf den Überwachungs Server verwendet wird.  
  
`[ @monitor_server_password = ] 'monitor_server_password'`Das Kennwort des Kontos, das für den Zugriff auf den Überwachungs Server verwendet wird.  
  
`[ @backup_threshold = ] 'backup_threshold'`Die Zeitspanne (in Minuten) nach der letzten Sicherung, bevor ein *threshold_alert* Fehler ausgelöst wird. *backup_threshold* ist vom Datentyp **int**, der Standardwert ist 60 Minuten.  
  
`[ @threshold_alert = ] 'threshold_alert'`Die Warnung, die ausgelöst werden soll, wenn der Sicherungs Schwellenwert überschritten wird. *threshold_alert* ist vom Datentyp **int** und kann nicht NULL sein.  
  
`[ @threshold_alert_enabled = ] 'threshold_alert_enabled'`Gibt an, ob eine Warnung ausgelöst wird, wenn *backup_threshold* überschritten wird.  
  
 1 = aktiviert.  
  
 0 = deaktiviert.  
  
 *threshold_alert_enabled* ist vom **Bit** und kann nicht NULL sein.  
  
`[ @history_retention_period = ] 'history_retention_period'`Der Zeitraum in Minuten, in dem der Verlauf beibehalten wird. *history_retention_period* ist vom Datentyp **int**. Der Wert 14420 wird verwendet, wenn kein Wert angegeben wird.  
  
`[ @backup_compression = ] backup_compression_option`Gibt an, ob eine Protokoll Versand Konfiguration die [Sicherungs Komprimierung](../../relational-databases/backup-restore/backup-compression-sql-server.md)verwendet. Dieser Parameter wird nur in [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (oder einer höheren Version) unterstützt.  
  
 0 = Deaktiviert. Protokollsicherungen nie komprimieren.  
  
 1 = Aktiviert. Protokollsicherungen immer komprimieren.  
  
 2 = Einstellung der [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)verwenden. Dies ist der Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_change_log_shipping_primary_database** muss von der **Master** -Datenbank auf dem primären Server ausgeführt werden. Diese gespeicherte Prozedur führt folgende Aktionen aus:  
  
1.  Ändert die Einstellungen im **log_shipping_primary_database** Datensatz, falls erforderlich.  
  
2.  Ändert den lokalen Datensatz in **log_shipping_monitor_primary** auf dem primären Server mithilfe der angegebenen Argumente, falls erforderlich.  
  
3.  Wenn der Überwachungs Server nicht mit dem primären Server identisch ist, wird der Änderungs Daten Satz in **log_shipping_monitor_primary** auf dem Überwachungs Server mithilfe der angegebenen Argumente angezeigt, falls erforderlich.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 Dieses Beispiel veranschaulicht die Verwendung von **sp_change_log_shipping_primary_database** , um die Einstellungen zu aktualisieren, die der primären Datenbank zugeordnet sind [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
EXEC master.dbo.sp_change_log_shipping_primary_database   
 @database = N'AdventureWorks'   
, @backup_directory = N'c:\LogShipping'   
, @backup_share = N'\\tribeca\LogShipping'   
, @backup_retention_period = 1440   
, @backup_threshold = 60   
, @threshold_alert = 0   
, @threshold_alert_enabled = 1   
, @history_retention_period = 1440   
,@monitor_server_security_mode = 1  
,@backup_compression = 1;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [log_shipping_primary_databases &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-primary-databases-transact-sql.md)  
  
  
