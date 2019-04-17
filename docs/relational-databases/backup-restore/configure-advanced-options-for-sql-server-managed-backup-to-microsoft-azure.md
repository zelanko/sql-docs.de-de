---
title: Konfigurieren der erweiterten Optionen für die verwaltete Sicherung von SQL Server zu Microsoft Azure | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/05/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: ffd28159-8de8-4d40-87da-1586bfef3315
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b6bcf893e719a2501fcf2084331b21de6f6a491c
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2019
ms.locfileid: "59241748"
---
# <a name="configure-advanced-options-for-sql-server-managed-backup-to-microsoft-azure"></a>Konfigurieren der erweiterten Optionen für die verwaltete Sicherung von SQL Server zu Microsoft Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das folgende Tutorial beschreibt, wie Sie erweiterte Optionen für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]festlegen. Diese Prozeduren sind nur notwendig, wenn Sie die Funktionen benötigen, die sie bieten. Andernfalls können Sie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] aktivieren und sich auf das Standardverhalten verlassen.  
  
 In jedem Szenario wird die Sicherung mit dem `database_name` -Parameter angegeben. Wenn `database_name` NULL oder * ist, wirken sich die Änderungen auf die Standardeinstellungen auf Instanzebene aus. Instanzebeneneinstellungen wirken sich auch auf neue Datenbanken aus, die nach der Änderung erstellt wurden.  
  
 Nachdem Sie diese Einstellungen angegeben haben, können Sie die verwaltete Sicherung für die Datenbank oder Instanz mithilfe der gespeicherten Systemprozedur [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md) aktivieren. Weitere Informationen finden Sie unter [Aktivieren der verwalteten SQL Server-Sicherung in Microsoft Azure](../../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md).  
  
> [!WARNING]  
>  Bevor Sie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] mit [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md) aktivieren, sollten Sie immer die erweiterten Optionen und benutzerdefinierte Planungsoptionen konfigurieren. Andernfalls kann es sein, dass es im Zeitfenster zwischen der Aktivierung von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] und der Konfiguration dieser Einstellungen zu unerwünschten Sicherungsvorgängen kommt.  
  
## <a name="configure-encryption"></a>Konfigurieren der Verschlüsselung  
 Die folgenden Schritte beschreiben, wie Sie die Einstellungen für die Verschlüsselung mithilfe der gespeicherten Prozedur [managed_backup.sp_backup_config_advanced &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md) angegeben.  

[!INCLUDE[Freshness](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

1.  **Bestimmen Sie den Verschlüsselungsalgorithmus:** Bestimmen Sie zunächst den Namen des zu verwendenden Verschlüsselungsalgorithmus. Wählen Sie einen der folgenden Algorithmen aus:  
  
    -   AES_128  
  
    -   AES_192  
  
    -   AES_256  
  
    -   TRIPLE_DES_3KEY  
  
    -   NO_ENCRYPTION  
  
2.  **Erstellen Sie einen Datenbank-Hauptschlüssel:** Wählen Sie ein Kennwort aus, mit dem die in der Datenbank gespeicherte Kopie des Datenbank-Hauptschlüssels verschlüsselt wird.  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
       CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
    ```  
  
3.  **Erstellen Sie ein Sicherungszertifikat oder einen asymmetrischen Schlüssel:** Sie können ein Zertifikat oder einen asymmetrischen Schlüssel für die Verschlüsselung verwenden. Im folgenden Beispiel wird ein Sicherungszertifikat für die Verschlüsselung erstellt.  
  
    ```sql  
    USE Master;  
    GO  
       CREATE CERTIFICATE MyTestDBBackupEncryptCert  
          WITH SUBJECT = 'MyTestDBBackupEncryptCert';  
    GO  
    ```  
  
4.  **Legen Sie die Verschlüsselung für die verwaltete Sicherung fest:** Rufen Sie die gespeicherte Prozedur **managed_backup.sp_backup_config_advanced** mit den entsprechenden Werten auf. Im folgenden Beispiel wird z.B. die `MyDB` -Datenbank für die Verschlüsselung mit einem Zertifikat namens `MyTestDBBackupEncryptCert` und dem `AES_128` -Verschlüsselungsalgorithmus konfiguriert.  
  
    ```  
    USE msdb;  
    GO  
       EXEC managed_backup.sp_backup_config_advanced  
          @database_name = 'MyDB'                
          ,@encryption_algorithm ='AES_128'  
          ,@encryptor_type = 'CERTIFICATE'  
          ,@encryptor_name = 'MyTestDBBackupEncryptCert';  
    GO  
    ```  
  
    > [!WARNING]  
    >  Wenn `@database_name` im vorherigen Beispiel NULL ist, werden die Einstellungen auf die SQL Server-Instanz angewendet.  
  
## <a name="configure-a-custom-backup-schedule"></a>Konfigurieren eines benutzerdefinierten Sicherungszeitplans  
 Die folgenden Schritte beschreiben, wie Sie einen benutzerdefinierten Zeitplan mithilfe der gespeicherten Prozedur [managed_backup.sp_backup_config_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md) angegeben.  
  
1.  **Ermitteln Sie die Häufigkeit für vollständige Sicherungen:** Bestimmen Sie, wie häufig die Datenbank vollständig gesichert werden soll. Sie können für die vollständigen Sicherungen zwischen den Optionen „Täglich“ und „Wöchentlich“ wählen.  
  
2.  **Ermitteln Sie die Häufigkeit für Protokollsicherungen:** Bestimmen Sie, wie häufig Protokolle gesichert werden sollen. Dieser Wert wird in Minuten oder Stunden angegeben.  
  
3.  **Bestimmen Sie den Wochentag für wöchentliche Sicherungen:** Bei einer wöchentlichen Sicherung wählen Sie einen Wochentag für die vollständige Sicherung aus.  
  
4.  **Bestimmen Sie die Startzeit der Sicherung:** Wählen Sie unter Verwendung des 24-Stunden-Formats eine Startzeit für die Sicherung aus.  
  
5.  **Bestimmen Sie die Dauer der Sicherung:** Hiermit wird die Zeitspanne angegeben, in der eine Sicherung abgeschlossen sein muss.  
  
6.  **Legen Sie den benutzerdefinierten Sicherungszeitplan fest:** Die folgende gespeicherte Prozedur definiert einen benutzerdefinierten Zeitplan für die `MyDB`-Datenbank. Vollständige Sicherungen werden wöchentlich am `Monday` um `17:30`durchgeführt. Protokollsicherungen werden alle `5` Minuten durchgeführt. Sicherungen müssen innerhalb von zwei Stunden abgeschlossen sein.  
  
    ```  
    USE msdb;  
    GO  
    EXEC managed_backup.sp_backup_config_schedule   
         @database_name =  'MyDB'  
        ,@scheduling_option = 'Custom'  
        ,@full_backup_freq_type = 'Weekly'  
        ,@days_of_week = 'Monday'  
        ,@backup_begin_time =  '17:30'  
        ,@backup_duration = '02:00'  
        ,@log_backup_freq = '00:05'  
    GO  
  
    ```  
  
## <a name="next-steps"></a>Nächste Schritte  
 Nach dem Konfigurieren der erweiterten Optionen und der benutzerdefinierten Zeitpläne müssen Sie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] auf der Zieldatenbank oder der SQL Server-Instanz aktivieren. Weitere Informationen finden Sie unter [Aktivieren der verwalteten SQL Server-Sicherung in Microsoft Azure](../../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Managed Backup für Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
