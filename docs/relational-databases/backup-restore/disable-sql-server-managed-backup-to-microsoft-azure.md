---
title: Deaktivieren der verwalteten Sicherung in Azure Blob Storage
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 3e02187f-363f-4e69-a82f-583953592544
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d85df8c4d07a61c75dcb42eadbc9c7cdae4faad6
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75257975"
---
# <a name="disable-sql-server-managed-backup-to-microsoft-azure"></a>Deaktivieren der verwalteten SQL Server-Sicherung in Microsoft Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] sowohl auf Datenbank- als auch auf Instanzebene deaktiviert oder angehalten wird.  
  
##  <a name="DatabaseDisable"></a> Deaktivieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für eine Datenbank  
 Sie können die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]-Einstellungen deaktivieren, indem Sie die gespeicherte Systemprozedur [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md) verwenden. Der Parameter *\@enable_backup* wird zum Aktivieren und Deaktivieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]-Konfigurationen für eine bestimmte Datenbank verwendet, wobei die Konfigurationseinstellungen mit 1 aktiviert und mit 0 deaktiviert werden.  
  
#### <a name="to-disable-includess_smartbackupincludesss-smartbackup-mdmd-for-a-specific-database"></a>So deaktivieren Sie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für eine bestimmte Datenbank  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
```sql
EXEC msdb.managed_backup.sp_backup_config_basic  
                @database_name = 'TestDB'   
                ,@enable_backup = 0;  
GO
```

> [!NOTE]
> Je nach Konfiguration müssen Sie möglicherweise auch den Parameter `@container_url` festlegen.
  
##  <a name="DatabaseAllDisable"></a> Deaktivieren Sie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für alle Datenbanken in der Instanz.  
 Mit dem folgenden Verfahren können Sie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] -Konfigurationseinstellungen für alle Datenbanken deaktivieren, für die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] momentan für die Instanz aktiviert ist.  Die Konfigurationseinstellungen wie Speicher-URL, Beibehaltung und SQL-Anmeldeinformationen verbleiben in den Metadaten und können verwendet werden, wenn [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] zu einem späteren Zeitpunkt für die Datenbank aktiviert wird. Wenn Sie die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] -Dienste vorübergehend anhalten möchten, können Sie den in den folgenden Abschnitten dieses Themas erläuterten Hauptschalter verwenden.  
  
#### <a name="to-disable-includess_smartbackupincludesss-smartbackup-mdmd-for-all-the-databases"></a>So deaktivieren Sie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für alle Datenbanken  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im folgenden Beispiel wird ermittelt, ob [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] auf Instanzebene konfiguriert ist und für welche Datenbanken auf der Instanz [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] aktiviert ist, und die gespeicherte Systemprozedur **sp_backup_config_basic** wird ausgeführt, um [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]zu deaktivieren.  
  
```sql
-- Create a working table to store the database names  
Declare @DBNames TABLE  
  
       (  
             RowID int IDENTITY PRIMARY KEY  
             ,DBName varchar(500)  
  
       )  
-- Define the variables  
DECLARE @rowid int  
DECLARE @dbname varchar(500)  
DECLARE @SQL varchar(2000)  
-- Get the database names from the system function  
  
INSERT INTO @DBNames (DBName)  
  
SELECT db_name  
       FROM   
  
       msdb.managed_backup.fn_backup_db_config (NULL)  
       WHERE is_managed_backup_enabled = 1 
       AND is_dropped = 0
  
       --Select DBName from @DBNames  
  
       select @rowid = min(RowID)  
       FROM @DBNames  
  
       WHILE @rowID IS NOT NULL  
       Begin  
  
             Set @dbname = (Select DBName From @DBNames Where RowID = @rowid)  
             Begin  
             Set @SQL = 'EXEC msdb.managed_backup.sp_backup_config_basic    
                @database_name= '''+'' + @dbname+ ''+''',   
                @enable_backup=0'  
  
            EXECUTE (@SQL)  
  
             END  
             Select @rowid = min(RowID)  
             From @DBNames Where RowID > @rowid  
  
       END  
```  
  
 Prüfen Sie die Konfigurationseinstellungen für alle Datenbanken auf der Instanz mit der folgenden Abfrage:  
  
```sql
Use msdb;  
GO  
SELECT * FROM managed_backup.fn_backup_db_config (NULL);  
GO  
```  
  
##  <a name="InstanceDisable"></a> Deaktivieren der [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] -Standardeinstellungen für die Instanz  
 Standardeinstellungen auf Instanzebene gelten für alle neuen Datenbanken, die auf dieser Instanz erstellt werden.  Wenn Sie die Standardeinstellungen nicht mehr benötigen, können Sie diese Konfiguration mithilfe der gespeicherten Systemprozedur **managed_backup.sp_backup_config_basic** deaktivieren, indem Sie den Parameter *\@database_name* auf NULL setzen. Durch die Deaktivierung werden die anderen Konfigurationseinstellungen wie Speicher-URL, Beibehaltungseinstellung oder der Name der SQL-Anmeldeinformationen nicht entfernt. Diese Einstellungen werden verwendet, wenn [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] zu einem späteren Zeitpunkt für die Instanz aktiviert wird.  
  
#### <a name="to-disable-includess_smartbackupincludesss-smartbackup-mdmd-default-configuration-settings"></a>So deaktivieren Sie die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] -Standardkonfigurationseinstellungen  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```sql
    EXEC msdb.managed_backup.sp_backup_config_basic  
                    @enable_backup = 0;  
    GO
    ```  
  
##  <a name="InstancePause"></a> Anhalten von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] auf Instanzebene  
 Zuweilen kann es vorkommen, dass Sie die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] -Dienste für kurze Zeit vorübergehend anhalten müssen.  Mit der gespeicherten Hauptschalter-Systemprozedur **managed_backup.sp_backup_master_switch** können Sie den [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] -Dienst auf Instanzebene deaktivieren.  Mit der gleichen gespeicherten Prozedur wird [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]fortgesetzt. Mit dem Parameter \@state wird definiert, ob [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] aktiviert oder deaktiviert werden soll.  
  
#### <a name="to-pause-includess_smartbackupincludesss-smartbackup-mdmd-services-using-transact-sql"></a>So halten Sie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] -Dienste mit Transact-SQL an  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie dann auf **Ausführen**.  
  
```sql
Use msdb;  
GO  
EXEC managed_backup.sp_backup_master_switch @new_state=0;  
Go
```  
  
#### <a name="to-resume-includess_smartbackupincludesss-smartbackup-mdmd-using-transact-sql"></a>So setzen Sie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] mit Transact-SQL fort  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie dann auf **Ausführen**.  
  
```sql
Use msdb;  
Go  
EXEC managed_backup.sp_backup_master_switch @new_state=1;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktivieren der verwalteten SQL Server-Sicherung in Microsoft Azure](../../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md)  
  
  
