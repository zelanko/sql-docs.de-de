---
title: sp_backup_config_advanced (Transact-SQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 86db5a13ab1bdac2b35c6d5128ba1b2234bc24b7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62860953"
---
# <a name="managedbackupspbackupconfigadvanced-transact-sql"></a>managed_backup.sp_backup_config_advanced (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Konfiguriert die erweiterten Einstellungen für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```vb  
EXEC managed_backup.sp_backup_config_advanced   
    [@database_name = ] 'database_name'  
    ,[@encryption_algorithm = ] 'name of the encryption algorithm'  
    ,[@encryptor_type = ] {'CERTIFICATE' | 'ASYMMETRIC_KEY'}  
    ,[@encryptor_name = ] 'name of the certificate or asymmetric key'  
    ,[@local_cache_path = ] 'NOT AVAILABLE'  
```  
  
##  <a name="Arguments"></a> Argumente  
 @database_name  
 Der Name der Datenbank, für die verwaltete Sicherung in einer bestimmten Datenbank aktiviert werden soll. Wenn der Wert NULL oder *, und klicken Sie dann diese verwaltete Sicherung für alle Datenbanken auf dem Server gilt.  
  
 @encryption_algorithm  
 Der Name des Verschlüsselungsalgorithmus, der bei der Sicherung zum Verschlüsseln der Sicherungsdatei verwendet wird. Die @encryption_algorithm ist **SYSNAME**. Dies ist ein erforderlicher Parameter, wenn [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] erstmalig für die Datenbank konfiguriert wird. Geben Sie **NO_ENCRYPTION** , wenn Sie nicht, um die Sicherungsdatei zu verschlüsseln möchten. Beim Ändern der [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] Konfigurationseinstellungen, dieser Parameter ist optional: Wenn der Parameter nicht angegeben ist, und klicken Sie dann die vorhandenen Konfigurationswerte beibehalten werden. Zulässige Werte für diesen Parameter:  
  
-   AES_128  
  
-   AES_192  
  
-   AES_256  
  
-   TRIPLE_DES_3KEY  
  
-   NO_ENCRYPTION  
  
 Weitere Informationen zur Verschlüsselung von Algorithmen finden Sie unter [Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md).  
  
 @encryptor_type  
 Verschlüsselungstyp, der entweder "Zertifikat" sein kann oder "ASYMMETRIC_KEY". Die @encryptor_type ist **nvarchar(32)**. Dieser Parameter ist optional, wenn Sie NO_ENCRYPTION für angeben der @encryption_algorithm Parameter.  
  
 @encryptor_name  
 Der Name eines vorhandenen Zertifikats oder asymmetrischen Schlüssels, mit dem die Sicherung verschlüsselt wird. Die @encryptor_name ist **SYSNAME**. Bei Verwendung eines asymmetrischen Schlüssels muss die Konfiguration mit der erweiterten Schlüsselverwaltung (Extensible Key Management, EKM) erfolgen. Dieser Parameter ist optional, wenn Sie NO_ENCRYPTION für angeben der @encryption_algorithm Parameter.  
  
 Weitere Informationen über die erweiterbare Schlüsselverwaltung finden Sie unter [Erweiterbare Schlüsselverwaltung &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
 @local_cache_path  
 Dieser Parameter wird noch nicht unterstützt.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in **Db_backupoperator** -Datenbankrolle mit **ALTER ANY CREDENTIAL** Berechtigungen und **EXECUTE** Berechtigungen für **Sp_delete_ Backuphistory** gespeicherte Prozedur.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die erweiterte Konfigurationsoptionen für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für die Instanz von SQL Server.  
  
```  
Use msdb;  
Go  
   EXEC managed_backup.sp_backup_config_advanced  
                @encryption_algorithm ='AES_128'  
                ,@encryptor_type = 'CERTIFICATE'  
                ,@encryptor_name = 'MyTestDBBackupEncryptCert'  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup.sp_backup_config_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  
