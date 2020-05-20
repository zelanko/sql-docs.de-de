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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4ccb6e35354629391aecddbdfaa968adf743645b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830381"
---
# <a name="managed_backupsp_backup_config_advanced-transact-sql"></a>managed_backup. sp_backup_config_advanced (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Konfiguriert Erweiterte Einstellungen für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] .  
  
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
  
##  <a name="arguments"></a><a name="Arguments"></a>Argumentation  
 @database_name  
 Der Datenbankname für die Aktivierung der verwalteten Sicherung für eine bestimmte Datenbank. Wenn NULL oder * ist, gilt diese verwaltete Sicherung für alle Datenbanken auf dem Server.  
  
 @encryption_algorithm  
 Der Name des Verschlüsselungsalgorithmus, der bei der Sicherung zum Verschlüsseln der Sicherungsdatei verwendet wird. @encryption_algorithmIst vom **Datentyp sysname**. Dies ist ein erforderlicher Parameter, wenn [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] erstmalig für die Datenbank konfiguriert wird. Geben Sie **NO_ENCRYPTION** an, wenn die Sicherungsdatei nicht verschlüsselt werden soll. Wenn Sie die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] Konfigurationseinstellungen ändern, ist dieser Parameter optional. wenn der-Parameter nicht angegeben wird, werden die vorhandenen Konfigurationswerte beibehalten. Zulässige Werte für diesen Parameter:  
  
-   AES_128  
  
-   AES_192  
  
-   AES_256  
  
-   TRIPLE_DES_3KEY  
  
-   NO_ENCRYPTION  
  
 Weitere Informationen zur Verschlüsselung von Algorithmen finden Sie unter [Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md).  
  
 @encryptor_type  
 Der Verschlüsselungstyp, bei dem es sich entweder um ' Certificate ' oder ' ASYMMETRIC_KEY ' handeln kann. Ist vom Datentyp @encryptor_type **nvarchar (32)**. Dieser Parameter ist optional, wenn Sie NO_ENCRYPTION für den @encryption_algorithm Parameter angeben.  
  
 @encryptor_name  
 Der Name eines vorhandenen Zertifikats oder asymmetrischen Schlüssels, mit dem die Sicherung verschlüsselt wird. @encryptor_nameIst vom **Datentyp sysname**. Bei Verwendung eines asymmetrischen Schlüssels muss die Konfiguration mit der erweiterten Schlüsselverwaltung (Extensible Key Management, EKM) erfolgen. Dieser Parameter ist optional, wenn Sie NO_ENCRYPTION für den @encryption_algorithm Parameter angeben.  
  
 Weitere Informationen über die erweiterbare Schlüsselverwaltung finden Sie unter [Erweiterbare Schlüsselverwaltung &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
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
 [managed_backup.sp_backup_config_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  
