---
title: Sp_change_log_shipping_primary_database (Transact-SQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: f361039f611a6b7a383649fb18a4af155a0c2b28
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47710608"
---
# <a name="spchangelogshippingprimarydatabase-transact-sql"></a>sp_change_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Einstellungen primärer Datenbanken.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 [  **@database =** ] '*Datenbank*"  
 Der Name der Datenbank auf dem primären Server. *primary_database* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
 [  **@backup_directory =** ] '*Backup_directory*"  
 Der Pfad zum Sicherungsordner auf dem primären Server. *Backup_directory* ist **nvarchar(500)**, hat keinen Standardwert und darf nicht NULL sein.  
  
 [  **@backup_share =** ] '*Backup_share*"  
 Der Netzwerkpfad zum Sicherungsverzeichnis auf dem primären Server. *Backup_share* ist **nvarchar(500)**, hat keinen Standardwert und darf nicht NULL sein.  
  
 [  **@backup_retention_period =** ] '*Backup_retention_period*"  
 Die Zeitdauer (in Minuten), für die die Protokollsicherungsdatei im Sicherungsverzeichnis auf dem primären Server gespeichert wird. *Backup_retention_period* ist **Int**, hat keinen Standardwert und darf nicht NULL sein.  
  
 [  **@monitor_server_security_mode =** ] '*Monitor_server_security_mode*"  
 Der Sicherheitsmodus, der zum Herstellen einer Verbindung mit dem Überwachungsserver verwendet wird.  
  
 1 = Windows-Authentifizierung  
  
 0 = SQL Server-Authentifizierung  
  
 *monitor_server_security_mode* ist vom Datentyp **bit** und darf nicht NULL sein.  
  
 [  **@monitor_server_login =** ] '*Monitor_server_login*"  
 Der Benutzername für das Konto, das zum Zugreifen auf den Überwachungsserver verwendet wird.  
  
 [  **@monitor_server_password =** ] '*Monitor_server_password*"  
 Das Kennwort des Kontos, das zum Zugreifen auf den Überwachungsserver verwendet wird.  
  
 [  **@backup_threshold =** ] '*Backup_threshold*"  
 Die Länge der Zeit in Minuten, nach der letzten Sicherung, bevor eine *Threshold_alert* Fehler ausgelöst. *Backup_threshold* ist **Int**, hat den Standardwert von 60 Minuten.  
  
 [  **@threshold_alert =** ] '*Threshold_alert*"  
 Die Warnung, die bei Überschreiten des Sicherungsschwellenwertes ausgelöst wird. *Threshold_alert* ist **Int** und darf nicht NULL sein.  
  
 [  **@threshold_alert_enabled =** ] '*Threshold_alert_enabled*"  
 Gibt an, ob eine Warnung ausgelöst wird, wenn *Backup_threshold* überschritten wird.  
  
 1 = aktiviert.  
  
 0 = deaktiviert.  
  
 *Threshold_alert_enabled* ist **Bit** und darf nicht NULL sein.  
  
 [  **@history_retention_period =** ] '*History_retention_period*"  
 Die Zeitdauer (in Minuten), für die der Verlauf beibehalten wird. *History_retention_period* ist **Int**. Falls nichts angegeben wird, wird ein Wert von 14420 verwendet.  
  
 [ **@backup_compression**=] *Backup_compression_option*  
 Gibt an, ob eine Protokollversandkonfiguration verwendet [sicherungskomprimierung](../../relational-databases/backup-restore/backup-compression-sql-server.md). Dieser Parameter wird nur in [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (oder einer höheren Version) unterstützt.  
  
 0 = Deaktiviert. Protokollsicherungen nie komprimieren.  
  
 1 = Aktiviert. Protokollsicherungen immer komprimieren.  
  
 2 = Einstellung der der [anzeigen oder Konfigurieren der backup Compression Default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md). Dies ist der Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 **Sp_change_log_shipping_primary_database** muss ausgeführt werden, aus der **master** Datenbank auf dem primären Server. Diese gespeicherte Prozedur führt folgende Aktionen aus:  
  
1.  Ändert die Einstellungen in der **Log_shipping_primary_database** aufzuzeichnen, falls erforderlich.  
  
2.  Ändert den lokalen Datensatz in **Log_shipping_monitor_primary** auf dem primären Server mithilfe bereitgestellter Argumente, falls erforderlich.  
  
3.  Wenn der Überwachungsserver vom primären Server übereinstimmt, notieren Sie Änderungen in **Log_shipping_monitor_primary** auf dem Überwachungsserver mithilfe angegebener Parameter, falls erforderlich.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 Dieses Beispiel veranschaulicht die Verwendung von **Sp_change_log_shipping_primary_database** aktualisieren Sie die Einstellungen im Zusammenhang mit der primären Datenbank [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Über den Protokollversand &#40;SQLServer&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Log_shipping_primary_databases &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-primary-databases-transact-sql.md)  
  
  
