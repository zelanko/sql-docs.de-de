---
title: SQLServer Managed Backup für Windows Azure - Beibehaltungs- und Speichereinstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: c4aa26ea-5465-40cc-8b83-f50603cb9db1
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6f9f9db58c48e74a91ec85972befb206ed3fb07f
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52534485"
---
# <a name="sql-server-managed-backup-to-windows-azure---retention-and-storage-settings"></a>SQL Server Managed Backup für Windows Azure - Beibehaltungs- und Speichereinstellungen
  In diesem Thema werden die grundlegenden Schritte zum Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Datenbank sowie zum Konfigurieren der Standardeinstellungen für die Instanz beschrieben. Außerdem werden in diesem Thema die zum Anhalten und Fortsetzen der [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Dienste für die Instanz erforderlichen Schritte beschrieben.  
  
 Eine vollständige Exemplarische Vorgehensweise zum Einrichten von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] finden Sie unter [Einrichten von SQL Server Managed Backup für Windows Azure](../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md) und [zum Einrichten von SQL Server Managed Backup für Windows Azure-Verfügbarkeitsgruppen](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
 
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Aktivieren Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] nicht für Datenbanken, die derzeit Wartungspläne oder Protokollversand verwenden. Weitere Informationen zu Interoperabilität und Koexistenz mit anderen SQL Server-Funktionen finden Sie unter [SQL Server Managed Backup für Windows Azure: Interoperabilität und Koexistenz](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Der SQL Server-Agent muss ausgeführt werden.  
  
    > [!WARNING]  
    >  Wenn der SQL Server-Agent einige Zeit nicht ausgeführt und danach neu gestartet wird, können abhängig von der Zeitspanne zwischen der Beendigung und dem Start des SQL-Agents verstärkt Sicherungsaktivitäten auftreten und ein Rückstand von Protokollsicherungen entstehen, die auf die Ausführung warten. Es könnte ratsam sein, den SQL Server-Agent für den automatischen Start beim Systemstart zu konfigurieren.  
  
-   Ein Windows Azure-Speicherkonto und SQL-Anmeldeinformationen, in denen die Authentifizierungsinformationen für das Speicherkonto gespeichert sind, müssen erstellt worden sein, bevor Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]konfigurieren. Weitere Informationen finden Sie unter [Introduction to Key Components and Concepts](../relational-databases/backup-restore/sql-server-backup-to-url.md#intorkeyconcepts) Teil der **SQL Server Backup to URL** Thema und [Lektion 2: Erstellen Sie eine SQL Server-Anmeldeinformation](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] erstellt die notwendigen Container zum Speichern der Sicherungen. Der Name des Containers wird mit "Computer-Instanzenname"-Format erstellt. Bei AlwaysOn-Verfügbarkeitsgruppen wird der Container unter Verwendung der GUID der Verfügbarkeitsgruppe benannt.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Zum Ausführen der gespeicherten Prozeduren, mit denen [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], Sie muss entweder eine `System Administrator` oder Mitglied der **Db_backupoperator** Datenbankrolle mit **ALTER ANY CREDENTIAL** Berechtigungen und `EXECUTE` Berechtigungen für die **Sp_delete_backuphistory**, und `smart_admin.sp_backup_master_switch` gespeicherte Prozeduren.  Gespeicherte Prozeduren und Funktionen zur Überprüfung der vorhandenen Einstellungen erfordern in der Regel `Execute`-Berechtigungen für die gespeicherte Prozedur bzw. `Select`-Berechtigungen für die Funktion.  
  

  
###  <a name="Considerations"></a> Überlegungen zum Aktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für Datenbanken und Instanzen  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] kann separat für einzelne Datenbanken oder für die gesamte Instanz aktiviert werden. Die Optionen hängen von den Wiederherstellbarkeitsanforderungen für die Datenbanken in der Instanz, den Anforderungen für die Verwaltung von mehreren Datenbanken und Instanzen und der strategischen Verwendung des Windows Azure-Speichers ab.  
  
#### <a name="enabling-includesssmartbackupincludesss-smartbackup-mdmd-at-the-database-level"></a>Aktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Datenbankebene  
 Wenn für eine Datenbank bestimmte Anforderungen an den Sicherungszeitraum und die Beibehaltungsdauer (Wiederherstellbarkeits-SLA) bestehen, die sich von denjenigen für andere Datenbanken in der Instanz unterscheiden, konfigurieren Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für diese Datenbank auf Datenbankebene. Datenbankebeneneinstellungen überschreiben Konfigurationseinstellungen der Instanzebenen. Es können jedoch beide Optionen auf derselben Instanz zusammen verwendet werden. Im Folgenden finden Sie eine Liste der Vorteile und Überlegungen beim Aktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Datenbankebene.  
  
-   Präziser: Separate Konfigurationseinstellungen für jede Datenbank. Unterstützung verschiedener Beibehaltungsdauern für einzelne Datenbanken sind möglich.  
  
-   Überschreibt Instanzebeneneinstellungen für die Datenbank.  
  
-   Kann verwendet werden, um die Speicherkosten zu verringern, indem einzelne zu sichernde Datenbanken ausgewählt werden.  
  
-   Erfordert die Verwaltung jeder Datenbank  
  
#### <a name="enabling-includesssmartbackupincludesss-smartbackup-mdmd-at-the-instance-level-with-default-settings"></a>Aktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Instanzebene mit Standardeinstellungen  
 Verwenden Sie diese Einstellung, wenn die meisten Datenbanken in der Instanz die gleichen Anforderungen an die Sicherungs- und Beibehaltungsrichtlinie besitzen oder wenn neue Datenbankinstanzen bei der Erstellung automatisch gesichert werden sollen. Einige Datenbanken, die eine Ausnahme von der Richtlinie darstellen, können dennoch einzeln konfiguriert werden. Im Folgenden sind Vorteile und Überlegungen aufgelistet, die sich auf die Aktivierung von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Instanzebene beziehen.  
  
-   Automatisierung auf Instanzebene: Allgemeine Einstellungen, die automatisch auf später hinzugefügte neue Datenbanken angewendet werden.  
  
-   Neue Datenbanken werden kurz nach ihrer Erstellung auf den Instanzen automatisch gesichert.  
  
-   Eine Anwendung auf Datenbanken mit den gleichen Anforderungen an die Beibehaltungsdauer ist möglich.  
  
-   Sie können trotzdem einzelne Datenbanken konfigurieren, für die eine andere Beibehaltungsdauer erforderlich ist, selbst wenn die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Sicherung auf Instanzebene mit Standardeinstellungen aktiviert ist. Sie können [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für Datenbanken auch deaktivieren, wenn Sie nicht beabsichtigen, Windows Azure-Speicher für die Sicherungen zu verwenden.  
  
##  <a name="DatabaseConfigure"></a> Aktivieren und Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Datenbank  
 Die gespeicherte Systemprozedur `smart_admin.sp_set_db_backup` wird verwendet, um [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine bestimmte Datenbank zu aktivieren. Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] zum ersten Mal in der Datenbank aktiviert wird, müssen zusätzlich zum Aktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]die folgenden Informationen angegeben werden:  
  
-   Der Name der Datenbank.  
  
-   Die Beibehaltungsdauer.  
  
-   SQL-Anmeldeinformationen, die zur Authentifizierung beim Windows Azure-Speicherkonto verwendet werden.  
  
-   Geben Sie entweder nicht für die Verschlüsselung mit *@encryption_algorithm*  =  **NO_ENCRYPTION** , oder geben Sie einen unterstützten Verschlüsselungsalgorithmus. Weitere Informationen zur Verschlüsselung finden Sie unter [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für die Konfiguration auf Datenbankebene wird nur über Transact-SQL unterstützt.  
  
 Nach der Aktivierung von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Datenbank werden diese Informationen gespeichert. Wenn Sie die Konfiguration ändern, sind nur der Datenbankname und die zu ändernde Einstellung erforderlich. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] behält in diesem Fall die vorhandenen Werte für andere Parameter bei, sofern sie nicht angegeben werden.  
  
> [!IMPORTANT]  
>  Vor dem Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Datenbank kann es empfehlenswert sein, vorhandene Konfigurationen ggf. zu prüfen. Der Schritt zum Prüfen der Konfigurationseinstellungen für eine Datenbank wird weiter unten in diesem Abschnitt erläutert.  
  
-   **Mithilfe von Transact-SQL:**  
  
     Wenn Sie aktivieren [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] zum ersten Mal die erforderlichen Parameter sind: *@database_name*, *@credential_name*, *@encryption_algorithm*, *@enable_backup* Die *@storage_url* Parameter ist optional. Wenn Sie keinen Wert für angeben der @storage_url Parameter, der Wert wird abgeleitet, die speicherkontoinformationen aus der SQL-Anmeldeinformationen verwenden. Wenn Sie die Speicher-URL bereitstellen, geben Sie nur die URL für den Stamm des Speicherkontos an; diese muss mit den Informationen in den SQL-Anmeldeinformationen übereinstimmen, die Sie angegeben haben.  
  
    1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
    2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
    3.  Kopieren und fügen Sie im folgenden Beispiel wird in das Abfragefenster, und klicken Sie auf `Execute`. In diesem Beispiel wird [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für die Datenbank "TestDB". Die Beibehaltungsdauer wird auf 30 Tage festgelegt. Im Beispiel wird die Verschlüsselungsoption verwendet, bei der der Verschlüsselungsalgorithmus und die Verschlüsselungsinformationen angegeben werden.  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@enable_backup=1  
                    ,@retention_days =30   
                    ,@credential_name ='MyCredential'  
                    ,@encryption_algorithm ='AES_256'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
    GO  
  
    ```  
  
    > [!IMPORTANT]  
    >  Die Beibehaltungsdauer kann auf einen beliebigen Wert zwischen 1 und 30 Tage festgelegt werden.  
    >   
    >  Weitere Informationen zum Erstellen eines Zertifikats für die Verschlüsselung finden Sie im Schritt Erstellen Sie ein Sicherungszertifikat in [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
     Weitere Informationen zu dieser gespeicherten Prozedur, finden Sie unter [smart_admin.set_db_backup &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)  
  
     Überprüfen Sie die Konfigurationseinstellungen für eine Datenbank mit der folgenden Abfrage:  
  
    ```  
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('TestDB')  
    ```  
  
##  <a name="InstanceConfigure"></a> Deaktivieren und konfigurieren [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Einstellungen für die Instanz  
 Sie können die standardmäßigen [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Einstellungen auf Instanzebene auf zwei Arten aktivieren und konfigurieren:  Mithilfe der gespeicherten Prozedur `smart_backup.set_instance_backup` oder **SQL Server Management Studio**. Die beiden Methoden werden nachfolgend erläutert:  
  
 **smart_backup.set_instance_backup:**. Durch Angabe des Werts **1** für *@enable_backup* -Parameter können Sie die Sicherung aktivieren und die Standardkonfigurationen festlegen. Nachdem diese auf Instanzebene angewendet wurden, werden diese Standardeinstellungen auf alle neuen Datenbanken angewendet, die dieser Instanz hinzugefügt werden.  Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] zum ersten Mal aktiviert wird, müssen zusätzlich zum Aktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für die Instanz die folgenden Informationen angegeben werden:  
  
-   Die Beibehaltungsdauer.  
  
-   SQL-Anmeldeinformationen, die zur Authentifizierung beim Windows Azure-Speicherkonto verwendet werden.  
  
-   Die Verschlüsselungsoption. Geben Sie entweder nicht für die Verschlüsselung mit *@encryption_algorithm*  =  **NO_ENCRYPTION** , oder geben Sie einen unterstützten Verschlüsselungsalgorithmus. Weitere Informationen zur Verschlüsselung finden Sie unter [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).  
  
 Nach der Aktivierung werden diese Einstellungen gespeichert. Wenn Sie die Konfiguration ändern, sind nur der Datenbankname und der Einstellung, die Sie ändern möchten, erforderlich. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] behält die vorhandenen Werte bei, wenn nichts angegeben wird.  
  
> [!IMPORTANT]  
>  Vor dem Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Instanz kann es empfehlenswert sein, vorhandene Konfigurationen ggf. zu prüfen. Der Schritt zum Prüfen der Konfigurationseinstellungen für eine Datenbank wird weiter unten in diesem Abschnitt erläutert.  
  
 **SQL Server Management Studio:** Um diese Aufgabe in SQL Server Management Studio zu auszuführen, navigieren Sie im Objekt-Explorer, erweitern Sie die **Management** Knoten und der rechten Maustaste auf **Managed Backup**. Wählen Sie **Konfigurieren**aus. Das Dialogfeld **Managed Backup** wird geöffnet. Verwenden Sie dieses Dialogfeld, um die Beibehaltungsdauer, SQL-Anmeldeinformationen, die Speicher-URL und Verschlüsselungseinstellungen anzugeben. Spezifische Hilfe zu diesem Dialogfeld finden Sie [Managed Backup konfigurieren &#40;SQL Server Management Studio&#41;](configure-managed-backup-sql-server-management-studio.md).  
  
#### <a name="using-transact-sql"></a>Verwenden von Transact-SQL  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren und fügen Sie im folgenden Beispiel wird in das Abfragefenster, und klicken Sie auf `Execute`.  
  
```  
Use msdb;  
Go  
   EXEC smart_admin.sp_set_instance_backup  
                @retention_days=30   
                ,@credential_name='sqlbackuptoURL'  
                ,@encryption_algorithm ='AES_128'  
                ,@encryptor_type= 'Certificate'  
                ,@encryptor_name='MyBackupCert'  
                ,@enable_backup=1;  
GO  
  
```  
  
> [!IMPORTANT]  
>  Die Beibehaltungsdauer kann auf einen beliebigen Wert zwischen 1 und 30 Tage festgelegt werden.  
>   
>  Weitere Informationen zum Erstellen eines Zertifikats für die Verschlüsselung finden Sie im Schritt Erstellen Sie ein Sicherungszertifikat in [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
 Zeigen Sie die Standardkonfigurationseinstellungen für die Instanz mit der folgenden Abfrage an:  
  
```  
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_instance_config ();  
  
```  
  
#### <a name="using-powershell"></a>PowerShell  
  
1.  Starten Sie eine PowerShell-Instanz.  
  
2.  Führen Sie das folgende Skript aus, nachdem Sie es an Ihre Einstellungen angepasst haben.  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    $encryptionOption = New-SqlBackupEncryptionOption -EncryptionAlgorithm Aes128 -EncryptorType ServerCertificate -EncryptorName "MyBackupCert"  
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -BackupEnabled $True -BackupRetentionPeriodInDays 10 -EncryptionOption $encryptionOption  
    ```  
  
> [!IMPORTANT]  
>  Wenn Sie nach dem Konfigurieren der Standardeinstellungen eine neue Datenbank erstellen, kann es bis zu 15 Minuten dauern, bis die Datenbank mit den Standardeinstellungen konfiguriert ist. Dies gilt auch für Datenbanken, die von **Simple** auf das Wiederherstellungsmodell **Full** oder **Bulk-Logged** geändert werden.  
  
##  <a name="DatabaseDisable"></a> Deaktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Datenbank  
 Sie können die deaktivieren [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Einstellungen mithilfe der `sp_set_db_backup` gespeicherte Systemprozedur. Die *@enableparameter* dient zum Aktivieren und Deaktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Konfigurationen für eine bestimmte Datenbank verwendet, wobei die Konfigurationseinstellungen mit 1 aktiviert und mit 0 deaktiviert.  
  
#### <a name="to-disable-includesssmartbackupincludesss-smartbackup-mdmd-for-a-specific-database"></a>So deaktivieren Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine bestimmte Datenbank  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren und fügen Sie im folgenden Beispiel wird in das Abfragefenster, und klicken Sie auf `Execute`.  
  
```  
Use msdb;  
Go  
EXEC smart_admin.sp_set_db_backup   
                @database_name='TestDB'   
                ,@enable_backup=0;  
GO  
  
```  
  
##  <a name="DatabaseAllDisable"></a> Deaktivieren Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für alle Datenbanken in der Instanz.  
 Mit dem folgenden Verfahren können Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Konfigurationseinstellungen für alle Datenbanken deaktivieren, für die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] momentan für die Instanz aktiviert ist.  Die Konfigurationseinstellungen wie Speicher-URL, Beibehaltung und SQL-Anmeldeinformationen verbleiben in den Metadaten und können verwendet werden, wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] zu einem späteren Zeitpunkt für die Datenbank aktiviert wird. Wenn Sie die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Dienste vorübergehend anhalten möchten, können Sie den in den folgenden Abschnitten weiter unten in diesem Thema erläuterten Hauptschalter verwenden.  
  
#### <a name="to-disable-includesssmartbackupincludesss-smartbackup-mdmdfor-all-the-databases"></a>So deaktivieren Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]für alle Datenbanken  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren und fügen Sie im folgenden Beispiel wird in das Abfragefenster, und klicken Sie auf `Execute`. Im folgenden Beispiel wird ermittelt, ob [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Instanzebene konfiguriert ist und für welche Datenbanken in der Instanz [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] aktiviert ist, und die gespeicherte Systemprozedur `sp_set_db_backup` wird ausgeführt, um [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] zu deaktivieren.  
  
```  
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
  
       smart_admin.fn_backup_db_config (NULL)  
       WHERE is_smart_backup_enabled = 1  
  
       --Select DBName from @DBNames  
  
       select @rowid = min(RowID)  
       FROM @DBNames  
  
       WHILE @rowID IS NOT NULL  
       Begin  
  
             Set @dbname = (Select DBName From @DBNames Where RowID = @rowid)  
             Begin  
             Set @SQL = 'EXEC smart_admin.sp_set_db_backup    
                @database_name= '''+'' + @dbname+ ''+''',   
                @enable_backup=0'  
  
            EXECUTE (@SQL)  
  
             END  
             Select @rowid = min(RowID)  
             From @DBNames Where RowID > @rowid  
  
       END  
  
```  
  
 Prüfen Sie die Konfigurationseinstellungen für alle Datenbanken auf der Instanz mit der folgenden Abfrage:  
  
```  
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_db_config (NULL);  
GO  
  
```  
  
##  <a name="InstanceDisable"></a> Deaktivieren der [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Standardeinstellungen für die Instanz  
 Standardeinstellungen auf Instanzebene gelten für alle neuen Datenbanken, die auf dieser Instanz erstellt werden.  Wenn Sie die Standardeinstellungen nicht mehr benötigen, können Sie diese Konfiguration mit der gespeicherten Systemprozedur **smart_admin.sp_set_instance_backup** deaktivieren. Durch die Deaktivierung werden die anderen Konfigurationseinstellungen wie Speicher-URL, Beibehaltungseinstellung oder der Name der SQL-Anmeldeinformationen nicht entfernt. Diese Einstellungen werden verwendet, wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] zu einem späteren Zeitpunkt für die Instanz aktiviert wird.  
  
#### <a name="to-disable-includesssmartbackupincludesss-smartbackup-mdmd-default-configuration-settings"></a>So deaktivieren Sie die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Standardkonfigurationseinstellungen  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren und fügen Sie im folgenden Beispiel wird in das Abfragefenster, und klicken Sie auf `Execute`.  
  
    ```  
    Use msdb;  
    Go  
    EXEC smart_admin.sp_set_instance_backup  
                    @enable_backup=0;  
    GO  
  
    ```  
  
#### <a name="using-powershell"></a>PowerShell  
  
1.  Starten Sie eine PowerShell-Instanz.  
  
2.  Führen Sie folgendes Skript aus:  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    Set-SqlSmartAdmin -BackupEnabled $False  
    ```  
  
##  <a name="InstancePause"></a> Anhalten von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Instanzebene  
 Zuweilen kann es vorkommen, dass Sie die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Dienste für kurze Zeit vorübergehend anhalten müssen.  Mit der gespeicherten `smart_admin.sp_backup_master_switch`-Systemprozedur können Sie den [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Dienst auf Instanzebene deaktivieren.  Mit der gleichen gespeicherten Prozedur wird [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]fortgesetzt. Mit dem @state-Parameter wird definiert, ob [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] aktiviert oder deaktiviert werden soll.  
  
#### <a name="to-pause-includesssmartbackupincludesss-smartbackup-mdmd-services-using-transact-sql"></a>So halten Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Dienste mit Transact-SQL an  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie und fügen Sie im folgenden Beispiel wird in das Abfragefenster, und klicken Sie dann auf `Execute`  
  
```  
Use msdb;  
GO  
EXEC smart_admin.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
#### <a name="to-pause-includesssmartbackupincludesss-smartbackup-mdmd-using-powershell"></a>So halten Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] mit PowerShell an  
  
1.  Starten Sie eine PowerShell-Instanz.  
  
2.  Führen Sie das folgende Skript aus, nachdem Sie es an Ihre Einstellungen angepasst haben.  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $False  
    ```  
  
#### <a name="to-resume-includesssmartbackupincludesss-smartbackup-mdmd-using-transact-sql"></a>So setzen Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] mit Transact-SQL fort  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren und fügen Sie im folgenden Beispiel wird in das Abfragefenster, und klicken Sie dann auf `Execute`.  
  
```  
Use msdb;  
Go  
EXEC smart_admin. sp_backup_master_switch @new_state=1;  
GO  
  
```  
  
#### <a name="to-resume-includesssmartbackupincludesss-smartbackup-mdmd-using-powershell"></a>So setzen Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] mit PowerShell fort  
  
1.  Starten Sie eine PowerShell-Instanz.  
  
2.  Führen Sie das folgende Skript aus, nachdem Sie es an Ihre Einstellungen angepasst haben.  
  
    ```  
    C:\ PS> cd SQLSERVER:\SQL\Computer\MyInstance   
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $True  
    ```  
  
  
