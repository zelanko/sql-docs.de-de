---
title: sp_add_log_shipping_secondary_primary (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_secondary_primary_TSQL
- sp_add_log_shipping_secondary_primary
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_secondary_primary
ms.assetid: bfbbbee2-c255-4a59-a963-47d6e980a8e2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 155f59426e8167d5d888f3890089dd4b2ea3bf7c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "72909687"
---
# <a name="sp_add_log_shipping_secondary_primary-transact-sql"></a>sp_add_log_shipping_secondary_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Richtet die primären Informationen ein, fügt Links zur lokalen und Remoteüberwachung hinzu und erstellt auf dem sekundären Server Kopier- und Wiederherstellungsaufträge für die angegebene primäre Datenbank.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_log_shipping_secondary_primary  
 [ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database',  
[ @backup_source_directory = ] 'backup_source_directory' ,   
[ @backup_destination_directory = ] 'backup_destination_directory'  
[ @copy_job_name = ] 'copy_job_name'  
[ @restore_job_name = ] 'restore_job_name'  
[, [ @file_retention_period = ] 'file_retention_period']  
[, [ @monitor_server = ] 'monitor_server']  
[, [ @monitor_server_security_mode = ] 'monitor_server_security_mode']  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @copy_job_id = ] 'copy_job_id' OUTPUT ]  
[, [ @restore_job_id = ] 'restore_job_id' OUTPUT ]  
[, [ @secondary_id = ] 'secondary_id' OUTPUT]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @primary_server = ] 'primary_server'`Der Name der primären Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in der Protokoll Versand Konfiguration. *primary_server* ist vom **Datentyp vom Datentyp sysname** und darf nicht NULL sein.  
  
`[ @primary_database = ] 'primary_database'`Der Name der Datenbank auf dem primären Server. *primary_database* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @backup_source_directory = ] 'backup_source_directory'`Das Verzeichnis, in dem die Sicherungsdateien des Transaktions Protokolls vom primären Server gespeichert werden. *backup_source_directory* ist vom Datentyp **nvarchar (500)** und darf nicht NULL sein.  
  
`[ @backup_destination_directory = ] 'backup_destination_directory'`Das Verzeichnis auf dem sekundären Server, in das Sicherungsdateien kopiert werden. *backup_destination_directory* ist vom Datentyp **nvarchar (500)** und darf nicht NULL sein.  
  
`[ @copy_job_name = ] 'copy_job_name'`Der Name, der für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellten Agentauftrag zum Kopieren von Transaktionsprotokoll Sicherungen auf den sekundären Server verwendet werden soll. *copy_job_name* ist vom **Datentyp vom Datentyp sysname** und darf nicht NULL sein.  
  
`[ @restore_job_name = ] 'restore_job_name'`Der Name des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agentauftrags auf dem sekundären Server, von dem die Sicherungen in der sekundären Datenbank wieder hergestellt werden. *restore_job_name* ist vom **Datentyp vom Datentyp sysname** und darf nicht NULL sein.  
  
`[ @file_retention_period = ] 'file_retention_period'`Die Zeitspanne in Minuten, die eine Sicherungsdatei auf dem sekundären Server in dem vom- @backup_destination_directory Parameter angegebenen Pfad aufbewahrt wird, bevor Sie gelöscht wird. *history_retention_period* ist vom Datentyp **int**und hat den Standardwert NULL. Der Wert 14420 wird verwendet, falls kein anderer Wert angegeben wird.  
  
`[ @monitor_server = ] 'monitor_server'`Der Name des Überwachungs Servers. *Monitor_server* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @monitor_server_security_mode = ] 'monitor_server_security_mode'`Der Sicherheitsmodus, der zum Herstellen der Verbindung mit dem Überwachungs Server verwendet wird.  
  
 1 = Windows-Authentifizierung  
  
 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung  
  
 *monitor_server_security_mode* ist vom **Bit** und kann nicht NULL sein.  
  
`[ @monitor_server_login = ] 'monitor_server_login'`Der Benutzername des Kontos, das für den Zugriff auf den Überwachungs Server verwendet wird.  
  
`[ @monitor_server_password = ] 'monitor_server_password'`Das Kennwort des Kontos, das für den Zugriff auf den Überwachungs Server verwendet wird.  
  
`[ @copy_job_id = ] 'copy_job_id' OUTPUT`Die ID, die dem Kopierauftrag auf dem sekundären Server zugeordnet ist. *copy_job_id* ist vom Datentyp **uniqueidentifier** und darf nicht NULL sein.  
  
`[ @restore_job_id = ] 'restore_job_id' OUTPUT`Die ID, die dem Wiederherstellungsauftrag auf dem sekundären Server zugeordnet ist. *restore_job_id* ist vom Datentyp **uniqueidentifier** und darf nicht NULL sein.  
  
`[ @secondary_id = ] 'secondary_id' OUTPUT`Die ID für den sekundären Server in der Protokoll Versand Konfiguration. *secondary_id* ist vom Datentyp **uniqueidentifier** und darf nicht NULL sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_add_log_shipping_secondary_primary** muss von der **Master** -Datenbank auf dem sekundären Server ausgeführt werden. Diese gespeicherte Prozedur führt folgende Aktionen aus:  
  
1.  Generiert eine sekundäre ID für den angegebenen primären Server und die primäre Datenbank.  
  
2.  Führt Folgendes aus:  

    1.  Fügt einen Eintrag für die sekundäre ID in **log_shipping_secondary** mit den bereitgestellten Argumenten hinzu.  
  
    2.  Erstellt einen Kopierauftrag für die sekundäre ID, die deaktiviert ist.  
  
    3.  Legt die Kopier Auftrags-ID im **log_shipping_secondary** Eintrag auf die Auftrags-ID des Kopier Auftrags fest.  
  
    4.  Erstellt einen Wiederherstellungsauftrag für die sekundäre ID, die deaktiviert ist.  
  
    5.  Legen Sie die Wiederherstellungs Auftrags-ID im **log_shipping_secondary** Eintrag auf die Auftrags-ID des Wiederherstellungs Auftrags fest.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird die Verwendung der gespeicherten Prozedur **sp_add_log_shipping_secondary_primary** zum Einrichten von Informationen für die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] primäre Datenbank auf dem sekundären Server veranschaulicht.  
  
```  
EXEC master.dbo.sp_add_log_shipping_secondary_primary   
@primary_server = N'TRIBECA'   
,@primary_database = N'AdventureWorks'   
,@backup_source_directory = N'\\tribeca\LogShipping'   
,@backup_destination_directory = N''   
,@copy_job_name = N''   
,@restore_job_name = N''   
,@file_retention_period = 1440   
,@monitor_server = N'ROCKAWAY'   
,@monitor_server_security_mode = 1   
,@copy_job_id = @LS_Secondary__CopyJobId OUTPUT   
,@restore_job_id = @LS_Secondary__RestoreJobId OUTPUT   
,@secondary_id = @LS_Secondary__SecondaryId OUTPUT ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
