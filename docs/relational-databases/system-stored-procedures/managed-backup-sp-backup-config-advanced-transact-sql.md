---
title: managed_backup. sp_backup_config_advanced (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_backup_config_optional
- sp_backup_config_optional_TSQL
- managed_backup.sp_backup_config_optional_TSQL
- managed_backup.sp_backup_config_optional
dev_langs:
- TSQL
helpviewer_keywords:
- sp_backup_config_optional
- managed_backup.sp_backup_config_optional
ms.assetid: 4fae8193-1f88-48fd-a94a-4786efe8d6af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0178d4df6a5941b8896e6ff530802fd4c6bc6909
ms.sourcegitcommit: 64e96ad1ce6c88c814e3789f0fa6e60185ec479c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652949"
---
# <a name="managed_backupsp_backup_config_advanced-transact-sql"></a>managed_backup. sp_backup_config_advanced (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Konfiguriert Erweiterte Einstellungen für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
EXEC managed_backup.sp_backup_config_advanced   
    [@database_name = ] 'database_name'  
    ,[@encryption_algorithm = ] 'name of the encryption algorithm'  
    ,[@encryptor_type = ] {'CERTIFICATE' | 'ASYMMETRIC_KEY'}  
    ,[@encryptor_name = ] 'name of the certificate or asymmetric key'  
    ,[@local_cache_path = ] 'NOT AVAILABLE'  
```  
  
##  <a name="Arguments"></a>Argumente  
 @database_name  
 Der Datenbankname für die Aktivierung der verwalteten Sicherung für eine bestimmte Datenbank. Wenn NULL oder * ist, gilt diese verwaltete Sicherung für alle Datenbanken auf dem Server.  
  
 @encryption_algorithm  
 Der Name des Verschlüsselungsalgorithmus, der bei der Sicherung zum Verschlüsseln der Sicherungsdatei verwendet wird. Ist @encryption_algorithm vom **Datentyp sysname**. Dies ist ein erforderlicher Parameter, wenn [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] erstmalig für die Datenbank konfiguriert wird. Geben Sie **NO_ENCRYPTION** an, wenn die Sicherungsdatei nicht verschlüsselt werden soll. Wenn Sie die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] Konfigurationseinstellungen ändern, ist dieser Parameter optional. wenn der-Parameter nicht angegeben wird, werden die vorhandenen Konfigurationswerte beibehalten. Zulässige Werte für diesen Parameter:  
  
-   AES_128  
  
-   AES_192  
  
-   AES_256  
  
-   TRIPLE_DES_3KEY  
  
-   NO_ENCRYPTION  
  
 Weitere Informationen zur Verschlüsselung von Algorithmen finden Sie unter [Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md).  
  
 @encryptor_type  
 Der Verschlüsselungstyp, bei dem es sich entweder um ' Certificate ' oder ' ASYMMETRIC_KEY ' handeln kann. Ist @encryptor_type vom Datentyp **nvarchar (32)**. Dieser Parameter ist optional, wenn Sie NO_ENCRYPTION für den @encryption_algorithm Parameter angeben.  
  
 @encryptor_name  
 Der Name eines vorhandenen Zertifikats oder asymmetrischen Schlüssels, mit dem die Sicherung verschlüsselt wird. Ist @encryptor_name vom **Datentyp sysname**. Bei Verwendung eines asymmetrischen Schlüssels muss die Konfiguration mit der erweiterten Schlüsselverwaltung (Extensible Key Management, EKM) erfolgen. Dieser Parameter ist optional, wenn Sie NO_ENCRYPTION für den @encryption_algorithm Parameter angeben.  
  
 Weitere Informationen finden Sie unter [erweiterbare Schlüsselverwaltung &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
 @local_cache_path  
 Dieser Parameter wird noch nicht unterstützt.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in **db_backupoperator** Daten Bank Rolle mit **ALTER ANY CREDENTIAL** -Berechtigungen und **Execute** -Berechtigungen für die gespeicherte Prozedur **sp_delete_backuphistory** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Erweiterte Konfigurationsoptionen für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] die-Instanz SQL Server festgelegt.  
  
```sql
Use msdb;  
Go  
   EXEC managed_backup.sp_backup_config_advanced  
                @encryption_algorithm ='AES_128'  
                ,@encryptor_type = 'CERTIFICATE'  
                ,@encryptor_name = 'MyTestDBBackupEncryptCert'  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [managed_backup. sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup. sp_backup_config_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  
