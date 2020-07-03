---
title: sp_change_log_shipping_secondary_primary (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_secondary_primary
- sp_change_log_shipping_secondary_primary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_secondary_primary
ms.assetid: 5bcb4df7-6df3-4f2b-9207-b97b5addf2a6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 94ee2f67f0f496a5dffc515c0145de127e823863
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85872658"
---
# <a name="sp_change_log_shipping_secondary_primary-transact-sql"></a>sp_change_log_shipping_secondary_primary (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ändert Einstellungen sekundärer Datenbanken.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_change_log_shipping_secondary_primary  
[ @primary_server = ] 'primary_server',  
[ @primary_database = ] 'primary_database',  
[, [ @backup_source_directory = ] 'backup_source_directory']  
[, [ @backup_destination_directory = ] 'backup_destination_directory']  
[, [ @file_retention_period = ] file_retention_period]  
[, [ @monitor_server_security_mode = ] monitor_server_security_mode]  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
```  
  
## <a name="arguments"></a>Argumente  
`[ @primary_server = ] 'primary_server'`Der Name der primären Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in der Protokoll Versand Konfiguration. *primary_server* ist vom Datentyp **sysname** und darf nicht NULL sein.  
  
`[ @primary_database = ] 'primary_database'`Der Name der Datenbank auf dem primären Server. *primary_database* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
`[ @backup_source_directory = ] 'backup_source_directory'`Das Verzeichnis, in dem die Sicherungsdateien des Transaktions Protokolls vom primären Server gespeichert werden. *backup_source_directory* ist vom Datentyp **nvarchar(500)** und darf nicht NULL sein.  
  
`[ @backup_destination_directory = ] 'backup_destination_directory'`Das Verzeichnis auf dem sekundären Server, in das Sicherungsdateien kopiert werden. *backup_destination_directory* ist vom Datentyp **nvarchar(500)** und darf nicht NULL sein.  
  
`[ @file_retention_period = ] 'file_retention_period'`Der Zeitraum in Minuten, in dem der Verlauf beibehalten wird. *history_retention_period* ist vom Datentyp **int**. Der Standardwert ist NULL. Der Wert 14420 wird verwendet, falls kein anderer Wert angegeben wird.  
  
`[ @monitor_server_security_mode = ] 'monitor_server_security_mode'`Der Sicherheitsmodus, der zum Herstellen der Verbindung mit dem Überwachungs Server verwendet wird.  
  
 1 = Windows-Authentifizierung;  
  
 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. *monitor_server_security_mode* ist vom Datentyp **bit** und darf nicht NULL sein.  
  
`[ @monitor_server_login = ] 'monitor_server_login'`Der Benutzername des Kontos, das für den Zugriff auf den Überwachungs Server verwendet wird.  
  
`[ @monitor_server_password = ] 'monitor_server_password'`Das Kennwort des Kontos, das für den Zugriff auf den Überwachungs Server verwendet wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_change_log_shipping_secondary_primary** muss von der **master** -Datenbank aus auf dem sekundären Server ausgeführt werden. Diese gespeicherte Prozedur führt folgende Aktionen aus:  
  
1.  Änderung von Einstellungen in den **log_shipping_secondary** -Datensätzen, sofern dies notwendig ist.  
  
2.  Sofern notwendig, eine Änderung des Überwachungsdatensatzes in **log_shipping_monitor_secondary** auf dem Überwachungsserver mithilfe angegebener Parameter, falls der Überwachungsserver nicht mit dem sekundären Server identisch ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
