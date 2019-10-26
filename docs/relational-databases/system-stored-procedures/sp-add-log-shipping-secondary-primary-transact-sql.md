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
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909687"
---
# <a name="sp_add_log_shipping_secondary_primary-transact-sql"></a>sp_add_log_shipping_secondary_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Richtet die primären Informationen ein, fügt Links zur lokalen und Remoteüberwachung hinzu und erstellt auf dem sekundären Server Kopier- und Wiederherstellungsaufträge für die angegebene primäre Datenbank.  
  
 ![Themen Link Symbol](../../database-engine/configure-windows/media/topic-link.gif "Link Symbol "Thema"") [Transact-SQL-Syntax Konventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @primary_server = ] 'primary_server'` den Namen der primären Instanz des [!INCLUDE[msCoName](../../includes/msconame-md.md)] in der Protokoll Versand Konfiguration [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. *primary_server* ist vom Datentyp **sysname** und darf nicht NULL sein.  
  
`[ @primary_database = ] 'primary_database'` ist der Name der Datenbank auf dem primären Server. *primary_database* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
`[ @backup_source_directory = ] 'backup_source_directory'` das Verzeichnis, in dem die Sicherungsdateien des Transaktions Protokolls vom primären Server gespeichert werden. *backup_source_directory* ist vom Datentyp **nvarchar(500)** und darf nicht NULL sein.  
  
`[ @backup_destination_directory = ] 'backup_destination_directory'` das Verzeichnis auf dem sekundären Server, in das Sicherungsdateien kopiert werden. *backup_destination_directory* ist vom Datentyp **nvarchar(500)** und darf nicht NULL sein.  
  
`[ @copy_job_name = ] 'copy_job_name'` den Namen, der für den erstellten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agentauftrag verwendet werden soll, um Transaktionsprotokoll Sicherungen auf den sekundären Server zu kopieren. *copy_job_name* ist vom **Datentyp vom Datentyp sysname** und darf nicht NULL sein.  
  
`[ @restore_job_name = ] 'restore_job_name'` ist der Name des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agentauftrags auf dem sekundären Server, der die Sicherungen in der sekundären Datenbank wiederherstellt. *restore_job_name* ist vom **Datentyp vom Datentyp sysname** und darf nicht NULL sein.  
  
`[ @file_retention_period = ] 'file_retention_period'` die Zeitspanne in Minuten, die eine Sicherungsdatei auf dem sekundären Server in dem Pfad aufbewahrt wird, der durch den @backup_destination_directory-Parameter vor dem Löschen angegeben wird. *history_retention_period* ist vom Datentyp **int**. Der Standardwert ist NULL. Der Wert 14420 wird verwendet, falls kein anderer Wert angegeben wird.  
  
`[ @monitor_server = ] 'monitor_server'` ist der Name des Überwachungs Servers. *Monitor_server* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert und darf nicht NULL sein.  
  
`[ @monitor_server_security_mode = ] 'monitor_server_security_mode'` den Sicherheitsmodus, der zum Herstellen der Verbindung mit dem Überwachungs Server verwendet wird.  
  
 1 = Windows-Authentifizierung  
  
 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung  
  
 *monitor_server_security_mode* ist vom Datentyp **bit** und darf nicht NULL sein.  
  
`[ @monitor_server_login = ] 'monitor_server_login'` ist der Benutzername des Kontos, das für den Zugriff auf den Überwachungs Server verwendet wird.  
  
`[ @monitor_server_password = ] 'monitor_server_password'` ist das Kennwort des Kontos, das für den Zugriff auf den Überwachungs Server verwendet wird.  
  
`[ @copy_job_id = ] 'copy_job_id' OUTPUT` die ID ab, die dem Kopierauftrag auf dem sekundären Server zugeordnet ist. *copy_job_id* ist vom Datentyp **uniqueidentifier** und darf nicht NULL sein.  
  
`[ @restore_job_id = ] 'restore_job_id' OUTPUT` die ID ab, die dem Wiederherstellungsauftrag auf dem sekundären Server zugeordnet ist. *restore_job_id* ist vom Datentyp **uniqueidentifier** und darf nicht NULL sein.  
  
`[ @secondary_id = ] 'secondary_id' OUTPUT` die ID für den sekundären Server in der Protokoll Versand Konfiguration. *secondary_id* ist vom Datentyp **uniqueidentifier** und darf nicht NULL sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 InclusionThresholdSetting  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_add_log_shipping_secondary_primary** muss von der **Master** -Datenbank auf dem sekundären Server ausgeführt werden. Diese gespeicherte Prozedur führt folgende Aktionen aus:  
  
1.  Generiert eine sekundäre ID für den angegebenen primären Server und die primäre Datenbank.  
  
2.  Führt Folgendes aus:  

    1.  Fügt einen Eintrag für die sekundäre ID in **log_shipping_secondary** mit den bereitgestellten Argumenten hinzu.  
  
    2.  Erstellt einen Kopierauftrag für die sekundäre ID, die deaktiviert ist.  
  
    3.  Legt die Kopier Auftrags-ID im **log_shipping_secondary** -Eintrag auf die Auftrags-ID des Kopier Auftrags fest.  
  
    4.  Erstellt einen Wiederherstellungsauftrag für die sekundäre ID, die deaktiviert ist.  
  
    5.  Legen Sie die Wiederherstellungs Auftrags-ID im **log_shipping_secondary** -Eintrag auf die Auftrags-ID des Wiederherstellungs Auftrags fest.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 Dieses Beispiel veranschaulicht die Verwendung der gespeicherten Prozedur **sp_add_log_shipping_secondary_primary** , um Informationen für die primäre Datenbank [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] auf dem sekundären Server einzurichten.  
  
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
