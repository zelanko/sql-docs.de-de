---
title: SQL Server verwaltete Sicherung in Azure-Beibehaltungs-und Speichereinstellungen | Microsoft-Dokumentation
description: In diesem Thema wird beschrieben, wie SQL Server verwaltete Sicherung konfiguriert wird, um für eine-Datenbank zu Microsoft Azure und die Standardeinstellungen für die-Instanz zu konfigurieren.
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: c4aa26ea-5465-40cc-8b83-f50603cb9db1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c2ef4a0546dfced643fb50900e6b56002b617e09
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84928801"
---
# <a name="sql-server-managed-backup-to-azure---retention-and-storage-settings"></a>Verwaltete SQL Server-Sicherung in Azure: Beibehaltungs- und Speichereinstellungen
  In diesem Thema werden die grundlegenden Schritte zum Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Datenbank sowie zum Konfigurieren der Standardeinstellungen für die Instanz beschrieben. Außerdem werden in diesem Thema die zum Anhalten und Fortsetzen der [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Dienste für die Instanz erforderlichen Schritte beschrieben.  
  
 Eine umfassende Exemplarische Vorgehensweise zum Einrichten von finden Sie unter [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] [Einrichten von SQL Server Managed Backup in Azure](../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md) und [Einrichten von SQL Server verwalteten Sicherung in Azure für Verfügbarkeits Gruppen](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Aktivieren Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] nicht für Datenbanken, die derzeit Wartungspläne oder Protokollversand verwenden. Weitere Informationen zur Interoperabilität und Koexistenz mit anderen SQL Server Features finden Sie unter [SQL Server Managed Backup to Azure: Interoperabilität und Koexistenz](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
  
-   Der SQL Server-Agent muss ausgeführt werden.  
  
    > [!WARNING]  
    >  Wenn der SQL Server-Agent einige Zeit nicht ausgeführt und danach neu gestartet wird, können abhängig von der Zeitspanne zwischen der Beendigung und dem Start des SQL-Agents verstärkt Sicherungsaktivitäten auftreten und ein Rückstand von Protokollsicherungen entstehen, die auf die Ausführung warten. Es könnte ratsam sein, den SQL Server-Agent für den automatischen Start beim Systemstart zu konfigurieren.  
  
-   Ein Azure-Speicherkonto und SQL-Anmelde Informationen, in denen die Authentifizierungsinformationen für das Speicherkonto gespeichert werden, sollten vor dem Konfigurieren von erstellt werden [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] . Ausführliche Informationen finden Sie im Thema [SQL Server-URL-Sicherung](../relational-databases/backup-restore/sql-server-backup-to-url.md#intorkeyconcepts) im Abschnitt **Introduction to Key Components and Concepts** und in [Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] erstellt die notwendigen Container zum Speichern der Sicherungen. Der Container Name wird im Format "Computername-Instanzname" erstellt. Bei AlwaysOn-Verfügbarkeitsgruppen wird der Container unter Verwendung der GUID der Verfügbarkeitsgruppe benannt.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Zum Ausführen der gespeicherten Prozeduren, die aktivieren [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] , müssen Sie entweder ein `System Administrator` -oder-Mitglied in der **db_backupoperator** -Daten Bank Rolle mit **ALTER ANY CREDENTIAL** -Berechtigungen und- `EXECUTE` Berechtigungen für die **sp_delete_backuphistory**und `smart_admin.sp_backup_master_switch` gespeicherte Prozeduren sein.  Gespeicherte Prozeduren und Funktionen zur Überprüfung der vorhandenen Einstellungen erfordern in der Regel `Execute`-Berechtigungen für die gespeicherte Prozedur bzw. `Select`-Berechtigungen für die Funktion.  
  

  
###  <a name="considerations-for-enabling-ss_smartbackup-for-databases-and-instances"></a><a name="Considerations"></a>Überlegungen zum Aktivieren [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] von für Datenbanken und Instanzen  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] kann separat für einzelne Datenbanken oder für die gesamte Instanz aktiviert werden. Die Auswahl hängt von den Anforderungen für die Wiederherstellbarkeit der Datenbanken auf der Instanz, den Anforderungen für die Verwaltung mehrerer Datenbanken und Instanzen und der strategischen Verwendung von Azure Storage ab.  
  
#### <a name="enabling-ss_smartbackup-at-the-database-level"></a>Aktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Datenbankebene  
 Wenn für eine Datenbank bestimmte Anforderungen an den Sicherungszeitraum und die Beibehaltungsdauer (Wiederherstellbarkeits-SLA) bestehen, die sich von denjenigen für andere Datenbanken in der Instanz unterscheiden, konfigurieren Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für diese Datenbank auf Datenbankebene. Datenbankebeneneinstellungen überschreiben Konfigurationseinstellungen der Instanzebenen. Es können jedoch beide Optionen auf derselben Instanz zusammen verwendet werden. Im Folgenden finden Sie eine Liste der Vorteile und Überlegungen beim Aktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Datenbankebene.  
  
-   Präziser: Separate Konfigurationseinstellungen für jede Datenbank. Unterstützung verschiedener Beibehaltungsdauern für einzelne Datenbanken sind möglich.  
  
-   Überschreibt Instanzebeneneinstellungen für die Datenbank.  
  
-   Kann verwendet werden, um die Speicherkosten zu verringern, indem einzelne zu sichernde Datenbanken ausgewählt werden.  
  
-   Erfordert die Verwaltung jeder Datenbank  
  
#### <a name="enabling-ss_smartbackup-at-the-instance-level-with-default-settings"></a>Aktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Instanzebene mit Standardeinstellungen  
 Verwenden Sie diese Einstellung, wenn die meisten Datenbanken in der Instanz die gleichen Anforderungen an die Sicherungs- und Beibehaltungsrichtlinie besitzen oder wenn neue Datenbankinstanzen bei der Erstellung automatisch gesichert werden sollen. Einige Datenbanken, die eine Ausnahme von der Richtlinie darstellen, können dennoch einzeln konfiguriert werden. Im Folgenden sind Vorteile und Überlegungen aufgelistet, die sich auf die Aktivierung von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Instanzebene beziehen.  
  
-   Automatisierung auf Instanzebene: Anschließend werden gemeinsame Einstellungen automatisch auf neue Datenbanken angewendet.  
  
-   Neue Datenbanken werden kurz nach ihrer Erstellung auf den Instanzen automatisch gesichert.  
  
-   Eine Anwendung auf Datenbanken mit den gleichen Anforderungen an die Beibehaltungsdauer ist möglich.  
  
-   Sie können trotzdem einzelne Datenbanken konfigurieren, für die eine andere Beibehaltungsdauer erforderlich ist, selbst wenn die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Sicherung auf Instanzebene mit Standardeinstellungen aktiviert ist. Sie können [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für Datenbanken auch deaktivieren, wenn Sie nicht beabsichtigen, den Azure-Speicher für die Sicherungen zu verwenden.  
  
##  <a name="enable-and-configure-ss_smartbackup-for-a-database"></a><a name="DatabaseConfigure"></a>Aktivieren und konfigurieren [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] von für eine Datenbank  
 Die gespeicherte Systemprozedur `smart_admin.sp_set_db_backup` wird verwendet, um [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine bestimmte Datenbank zu aktivieren. Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] zum ersten Mal in der Datenbank aktiviert wird, müssen zusätzlich zum Aktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]die folgenden Informationen angegeben werden:  
  
-   Der Name der Datenbank.  
  
-   Die Beibehaltungsdauer.  
  
-   SQL-Anmelde Informationen, die für die Authentifizierung beim Azure Storage-Konto verwendet werden.  
  
-   Geben Sie an, dass die Verschlüsselung nicht mithilfe * \@ encryption_algorithm*  =  **NO_ENCRYPTION** , oder geben Sie einen unterstützten Verschlüsselungsalgorithmus an. Weitere Informationen zur Verschlüsselung finden Sie unter [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für die Konfiguration auf Datenbankebene wird nur über Transact-SQL unterstützt.  
  
 Nach der Aktivierung von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Datenbank werden diese Informationen gespeichert. Wenn Sie die Konfiguration ändern, sind nur der Datenbankname und die zu ändernde Einstellung erforderlich. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] behält in diesem Fall die vorhandenen Werte für andere Parameter bei, sofern sie nicht angegeben werden.  
  
> [!IMPORTANT]  
>  Vor dem Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Datenbank kann es empfehlenswert sein, vorhandene Konfigurationen ggf. zu prüfen. Der Schritt zum Prüfen der Konfigurationseinstellungen für eine Datenbank wird weiter unten in diesem Abschnitt erläutert.  
  
-   **Verwenden von Transact-SQL:**  
  
     Wenn Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] zum ersten Mal aktivieren, sind die erforderlichen Parameter: * \@ database_name*, * \@ credential_name* * \@ encryption_algorithm*, * \@ enable_backup* der * \@ storage_url* Parameter optional ist. Wenn Sie keinen Wert für den @storage_url Parameter angeben, wird der Wert anhand der Speicherkonto Informationen aus den SQL-Anmelde Informationen abgeleitet. Wenn Sie die Speicher-URL bereitstellen, geben Sie nur die URL für den Stamm des Speicherkontos an; diese muss mit den Informationen in den SQL-Anmeldeinformationen übereinstimmen, die Sie angegeben haben.  
  
    1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
    2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
    3.  Fügen Sie das folgende Beispiel in das Abfragefenster ein, und klicken Sie auf `Execute` . In diesem Beispiel wird [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für die Datenbank "TestDB" aktiviert. Die Beibehaltungsdauer wird auf 30 Tage festgelegt. Im Beispiel wird die Verschlüsselungsoption verwendet, bei der der Verschlüsselungsalgorithmus und die Verschlüsselungsinformationen angegeben werden.  
  
    ```sql
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
  
     Weitere Informationen zu dieser gespeicherten Prozedur finden Sie unter [smart_admin. set_db_backup &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)  
  
     Überprüfen Sie die Konfigurationseinstellungen für eine Datenbank mit der folgenden Abfrage:  
  
    ```sql
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('TestDB')  
    ```  
  
##  <a name="enable-and-configure-default-ss_smartbackup-settings-for-the-instance"></a><a name="InstanceConfigure"></a>Aktivieren und konfigurieren [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] der Standardeinstellungen für die Instanz  
 Sie können die Standard [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Einstellungen auf Instanzebene auf zweierlei Weise aktivieren und konfigurieren: mithilfe der gespeicherten System Prozedur `smart_admin.set_instance_backup` oder **SQL Server Management Studio**. Die beiden Methoden werden nachfolgend erläutert:  
  
 **smart_admin. set_instance_backup:**. Wenn Sie den Wert **1** für * \@ enable_backup* Parameter angeben, können Sie die Sicherung aktivieren und die Standardkonfigurationen festlegen. Nachdem diese auf Instanzebene angewendet wurden, werden diese Standardeinstellungen auf alle neuen Datenbanken angewendet, die dieser Instanz hinzugefügt werden.  Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] zum ersten Mal aktiviert wird, müssen zusätzlich zum Aktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für die Instanz die folgenden Informationen angegeben werden:  
  
-   Die Beibehaltungsdauer.  
  
-   SQL-Anmelde Informationen, die für die Authentifizierung beim Azure Storage-Konto verwendet werden.  
  
-   Die Verschlüsselungsoption. Geben Sie an, dass die Verschlüsselung nicht mithilfe * \@ encryption_algorithm*  =  **NO_ENCRYPTION** , oder geben Sie einen unterstützten Verschlüsselungsalgorithmus an. Weitere Informationen zur Verschlüsselung finden Sie unter [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).  
  
 Nach der Aktivierung werden diese Einstellungen gespeichert. Wenn Sie die Konfiguration ändern, sind nur der Datenbankname und der Einstellung, die Sie ändern möchten, erforderlich. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] behält die vorhandenen Werte bei, wenn nichts angegeben wird.  
  
> [!IMPORTANT]  
>  Vor dem Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Instanz kann es empfehlenswert sein, vorhandene Konfigurationen ggf. zu prüfen. Der Schritt zum Prüfen der Konfigurationseinstellungen für eine Datenbank wird weiter unten in diesem Abschnitt erläutert.  
  
 **SQL Server Management Studio:** Um diese Aufgabe in SQL Server Management Studio auszuführen, erweitern Sie im Objekt-Explorer den Knoten **Verwaltung** und klicken mit der rechten Maustaste auf **Managed Backup**. Wählen Sie **Konfigurieren**aus. Das Dialogfeld **Managed Backup** wird geöffnet. Verwenden Sie dieses Dialogfeld, um die Beibehaltungsdauer, SQL-Anmeldeinformationen, die Speicher-URL und Verschlüsselungseinstellungen anzugeben. Spezifische Hilfe zu diesem Dialogfeld finden Sie unter [configure Managed Backup &#40;SQL Server Management Studio&#41;](configure-managed-backup-sql-server-management-studio.md).  
  
#### <a name="using-transact-sql"></a>Verwenden von Transact-SQL  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Fügen Sie das folgende Beispiel in das Abfragefenster ein, und klicken Sie auf `Execute` .  
  
```sql
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
  
```sql
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_instance_config ();
```  
  
#### <a name="using-powershell"></a>PowerShell  
  
1.  Starten Sie eine PowerShell-Instanz.  
  
2.  Führen Sie das folgende Skript aus, nachdem Sie es an Ihre Einstellungen angepasst haben.  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    $encryptionOption = New-SqlBackupEncryptionOption -EncryptionAlgorithm Aes128 -EncryptorType ServerCertificate -EncryptorName "MyBackupCert"  
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -BackupEnabled $True -BackupRetentionPeriodInDays 10 -EncryptionOption $encryptionOption  
    ```  
  
> [!IMPORTANT]  
>  Wenn Sie nach dem Konfigurieren der Standardeinstellungen eine neue Datenbank erstellen, kann es bis zu 15 Minuten dauern, bis die Datenbank mit den Standardeinstellungen konfiguriert ist. Dies gilt auch für Datenbanken, die von **Simple** auf das Wiederherstellungsmodell **Full** oder **Bulk-Logged** geändert werden.  
  
##  <a name="disable-ss_smartbackup-for-a-database"></a><a name="DatabaseDisable"></a> Deaktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Datenbank  
 Sie können [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Einstellungen mithilfe der `sp_set_db_backup` gespeicherten System Prozedur deaktivieren. Der * \@ enableparameter* wird zum Aktivieren und deaktivieren [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] von Konfigurationen für eine bestimmte Datenbank verwendet, wobei "1" aktiviert und "0" die Konfigurationseinstellungen deaktiviert.  
  
#### <a name="to-disable-ss_smartbackup-for-a-specific-database"></a>So deaktivieren Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine bestimmte Datenbank  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Fügen Sie das folgende Beispiel in das Abfragefenster ein, und klicken Sie auf `Execute` .  
  
```sql
Use msdb;  
Go  
EXEC smart_admin.sp_set_db_backup   
                @database_name='TestDB'   
                ,@enable_backup=0;  
GO
```  
  
##  <a name="disable-ss_smartbackup-for-all-the-databases-on-the-instance"></a><a name="DatabaseAllDisable"></a> Deaktivieren Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für alle Datenbanken in der Instanz.  
 Mit dem folgenden Verfahren können Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Konfigurationseinstellungen für alle Datenbanken deaktivieren, für die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] momentan für die Instanz aktiviert ist.  Die Konfigurationseinstellungen wie Speicher-URL, Beibehaltung und SQL-Anmeldeinformationen verbleiben in den Metadaten und können verwendet werden, wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] zu einem späteren Zeitpunkt für die Datenbank aktiviert wird. Wenn Sie die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Dienste vorübergehend anhalten möchten, können Sie den in den folgenden Abschnitten weiter unten in diesem Thema erläuterten Hauptschalter verwenden.  
  
#### <a name="to-disable-ss_smartbackupfor-all-the-databases"></a>So deaktivieren Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]für alle Datenbanken  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Fügen Sie das folgende Beispiel in das Abfragefenster ein, und klicken Sie auf `Execute` . Im folgenden Beispiel wird ermittelt, ob [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Instanzebene konfiguriert ist und für welche Datenbanken in der Instanz [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] aktiviert ist, und die gespeicherte Systemprozedur `sp_set_db_backup` wird ausgeführt, um [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] zu deaktivieren.  
  
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
  
       smart_admin.fn_backup_db_config (NULL)  
       WHERE is_smart_backup_enabled = 1  
  
       --Select DBName from @DBNames 
       select @rowid = min(RowID) FROM @DBNames  
  
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
  
```sql
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_db_config (NULL);  
GO
```  
  
##  <a name="disable-default-ss_smartbackup-settings-for-the-instance"></a><a name="InstanceDisable"></a> Deaktivieren der [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Standardeinstellungen für die Instanz  
 Standardeinstellungen auf Instanzebene gelten für alle neuen Datenbanken, die auf dieser Instanz erstellt werden.  Wenn Sie die Standardeinstellungen nicht mehr benötigen, können Sie diese Konfiguration mit der gespeicherten Systemprozedur **smart_admin.sp_set_instance_backup** deaktivieren. Durch die Deaktivierung werden die anderen Konfigurationseinstellungen wie Speicher-URL, Beibehaltungseinstellung oder der Name der SQL-Anmeldeinformationen nicht entfernt. Diese Einstellungen werden verwendet, wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] zu einem späteren Zeitpunkt für die Instanz aktiviert wird.  
  
#### <a name="to-disable-ss_smartbackup-default-configuration-settings"></a>So deaktivieren Sie die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Standardkonfigurationseinstellungen  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Fügen Sie das folgende Beispiel in das Abfragefenster ein, und klicken Sie auf `Execute` .  
  
    ```sql
    Use msdb;  
    Go  
    EXEC smart_admin.sp_set_instance_backup  
                    @enable_backup=0;  
    GO
    ```  
  
#### <a name="using-powershell"></a>PowerShell  
  
1.  Starten Sie eine PowerShell-Instanz.  
  
2.  Führen Sie folgendes Skript aus:  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Set-SqlSmartAdmin -BackupEnabled $False  
    ```  
  
##  <a name="pause-ss_smartbackup-at-the-instance-level"></a><a name="InstancePause"></a> Anhalten von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Instanzebene  
 Zuweilen kann es vorkommen, dass Sie die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Dienste für kurze Zeit vorübergehend anhalten müssen.  Mit der gespeicherten `smart_admin.sp_backup_master_switch`-Systemprozedur können Sie den [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Dienst auf Instanzebene deaktivieren.  Mit der gleichen gespeicherten Prozedur wird [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]fortgesetzt. Mit dem @state-Parameter wird definiert, ob [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] aktiviert oder deaktiviert werden soll.  
  
#### <a name="to-pause-ss_smartbackup-services-using-transact-sql"></a>So halten Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] -Dienste mit Transact-SQL an  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf`Execute`  
  
```sql
Use msdb;  
GO  
EXEC smart_admin.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
#### <a name="to-pause-ss_smartbackup-using-powershell"></a>So halten Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] mit PowerShell an  
  
1.  Starten Sie eine PowerShell-Instanz.  
  
2.  Führen Sie das folgende Skript aus, nachdem Sie es an Ihre Einstellungen angepasst haben.  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $False  
    ```  
  
#### <a name="to-resume-ss_smartbackup-using-transact-sql"></a>So setzen Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] mit Transact-SQL fort  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf `Execute` .  
  
```sql
Use msdb;  
Go  
EXEC smart_admin. sp_backup_master_switch @new_state=1;  
GO
```  
  
#### <a name="to-resume-ss_smartbackup-using-powershell"></a>So setzen Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] mit PowerShell fort  
  
1.  Starten Sie eine PowerShell-Instanz.  
  
2.  Führen Sie das folgende Skript aus, nachdem Sie es an Ihre Einstellungen angepasst haben.  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $True  
    ```  
