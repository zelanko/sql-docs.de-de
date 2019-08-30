---
title: Einrichten SQL Server Managed Backup in Azure | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/04/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 68ebb53e-d5ad-4622-af68-1e150b94516e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b69439226b55965e37f24f2131c77340ae833590
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154725"
---
# <a name="setting-up-sql-server-managed-backup-to-azure"></a>Einrichten SQL Server verwalteten Sicherung in Azure
  Dieses Thema umfasst zwei Lernprogramme:  
  
 Einrichten von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] auf Datenbankebene, Aktivieren der E-Mail-Benachrichtigung und Überwachen der Sicherungsaktivität  
  
 Einrichten von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] auf Instanzebene, Aktivieren der E-Mail-Benachrichtigung und Überwachen der Sicherungsaktivität  
  
 Ein Tutorial zum Einrichten [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] von für Verfügbarkeits Gruppen finden Sie unter [Einrichten SQL Server verwalteten Sicherung für die Microsoft Azure von Verfügbarkeits Gruppen](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
## <a name="setting-up-includess_smartbackupincludesss-smartbackup-mdmd"></a>Einrichten von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
  
### <a name="enable-and-configure-includess_smartbackupincludesss-smartbackup-mdmd-for-a-database"></a>Aktivieren und Konfigurieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für eine Datenbank  
 In diesem Lernprogramm werden die notwendigen Schritte zum Aktivieren und Konfigurieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für eine Datenbank (TestDB) beschrieben, gefolgt von den Schritten, mit denen die Überwachung des "[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]"-Integritätsstatus aktiviert wird.  
  
 **Berechtigungen:**  
  
-   Erfordert die Mitgliedschaft in der Daten Bank Rolle **db_backupoperator** mit **ALTER ANY CREDENTIAL** - `EXECUTE` Berechtigungen und Berechtigungen für die gespeicherte Prozedur **sp_delete_backuphistory**.  
  
-   Erfordert **Select** -Berechtigungen für die **smart_admin. fn_get_current_xevent_settings**-Funktion.  
  
-   Erfordert `EXECUTE` Berechtigungen für die gespeicherte Prozedur **smart_admin. sp_get_backup_diagnostics** . Außerdem sind `VIEW SERVER STATE`-Berechtigungen erforderlich, da andere Systemobjekte, die diese Berechtigung erfordern, intern aufgerufen werden.  
  
-   Erfordert `EXECUTE` Berechtigungen für die `smart_admin.sp_set_instance_backup` gespeicherten `smart_admin.sp_backup_master_switch` Prozeduren und.  


1.  **Erstellen Sie ein Microsoft Azure Speicherkonto:** Die Sicherungen werden im Microsoft Azure Speicher Dienstanbieter gespeichert. Sie müssen zunächst ein Microsoft Azure Speicherkonto erstellen, wenn Sie noch nicht über ein Konto verfügen.
    - In SQL Server 2014 werden seitenblobs verwendet, die sich von Block-und anfügeblobs unterscheiden. Daher müssen Sie ein allgemeines Konto erstellen und kein BLOB-Konto. Weitere Informationen finden Sie unter Informationen [zu Azure Storage-Konten](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).
    - Notieren Sie den Speicherkontonamen und die Zugriffsschlüssel. Aus dem Speicherkontonamen und den Zugriffsschlüsseln werden SQL-Anmeldeinformationen erstellt. Die SQL-Anmeldeinformationen werden zur Authentifizierung beim Speicherkonto verwendet.  
 
2.  **Erstellen Sie SQL-Anmelde Informationen:** Erstellen Sie SQL-Anmelde Informationen, indem Sie den Namen des Speicher Kontos als Identität und den Speicherzugriffs Schlüssel als Kennwort verwenden.  
  
3.  **Sicherstellen, dass der SQL Server-Agent-Dienst ausgeführt wird:**  Starten Sie den SQL Server-Agent, wenn er nicht ausgeführt wird.  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] benötigt einen laufenden SQL Server-Agent auf der Instanz, um Sicherungsvorgänge durchführen zu können.  Sie können den Starttyp des SQL Server-Agents auf "Automatisch" festlegen, um zu gewährleisten, dass regelmäßige Sicherungsvorgänge durchgeführt werden können.  
  
4.  **Bestimmen des Aufbewahrungszeitraums:** Bestimmen Sie die Beibehaltungsdauer für die Sicherungsdateien. Die Beibehaltungsdauer wird in Tagen angegeben und kann zwischen 1 und 30 Tagen liegen.  
  
5.  **Aktivieren und Konfigurieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]:** Starten SQL Server Management Studio, und stellen Sie eine Verbindung mit der Instanz her, auf der die Datenbank installiert ist Führen Sie im Abfragefenster folgende Anweisung aus, nachdem Sie die Werte für Datenbankname, SQL-Anmeldeinformationen, Beibehaltungsdauer und Verschlüsselungsoptionen Ihren Anforderungen entsprechend angepasst haben:  
  
     Weitere Informationen zum Erstellen eines Zertifikats für die Verschlüsselung finden Sie im Schritt **Erstellen eines Sicherungs Zertifikats** unter [Erstellen einer verschlüsselten Sicherung](create-an-encrypted-backup.md).  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ist damit für die angegebene Datenbank aktiviert. Es kann bis zu 15 Minuten dauern, bis die Sicherungsvorgänge für die Datenbank gestartet werden.  
  
6.  **Überprüfen der Standardkonfiguration für erweiterte Ereignisse:** Überprüfen Sie die Einstellungen für erweiterte Ereignisse, indem Sie die folgende Transact-SQL-Anweisung ausführen.  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     Stellen Sie sicher, dass Ereignisse der Kanäle Admin, Operational und Analytical standardmäßig aktiviert sind und nicht deaktiviert werden können. Dies sollte ausreichen, um alle Ereignisse zu überwachen, die ein manuelles Eingreifen erfordern.  Sie können die Debugereignisse ebenfalls aktivieren. Diese Kanäle enthalten jedoch auch Informations- und Debugereignisse, die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] intern zur Erkennung und Behebung von Fehlern verwendet. Weitere Informationen finden Sie unter [überwachen SQL Server verwalteten Sicherung in Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
7.  **Aktivieren und Konfigurieren der Benachrichtigung für den Integritätsstatus:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] verfügt über eine gespeicherte Prozedur, die einen Agent-Auftrag erstellt, um E-Mail-Benachrichtigungen mit Fehlern oder Warnungen zu senden, die möglicherweise ein Eingreifen erfordern. In den folgenden Schritten wird der Prozess zum Aktivieren und Konfigurieren der E-Mail-Benachrichtigungen beschrieben:  
  
    1.  Richten Sie Datenbank-E-Mail ein, falls diese Funktion auf der Instanz noch nicht aktiviert wurde. Weitere Informationen finden Sie unter [Configure Database Mail](../database-mail/configure-database-mail.md).  
  
    2.  Konfigurieren Sie SQL Server-Agent-Benachrichtigungen für die Verwendung von Datenbank-E-Mail. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server-Agent-Mail zum Verwenden von Datenbank-E-Mails](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Aktivieren der E-mail-Benachrichtigungen für den Empfang von Sicherungsfehlern und Warnungen:** Führen Sie im Abfragefenster die folgenden Transact-SQL-Anweisungen aus:  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email1;email2>'  
  
        ```  
  
         Weitere Informationen und ein vollständiges Beispielskript finden [Sie unter Überwachen SQL Server verwaltete Sicherung in Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
8.  **Anzeigen von Sicherungsdateien im Microsoft Azure Storage-Konto:** Stellen Sie eine Verbindung mit dem Speicherkonto von SQL Server Management Studio oder dem Azure-Verwaltungsportal her. Es wird ein Container für die Instanz von SQL Server angezeigt, die die Datenbank hostet, die Sie für die Verwendung von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] konfiguriert haben. Innerhalb der ersten 15 Minuten nach dem Aktivieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für die Datenbank können außerdem eine Datenbank- und eine Protokollsicherung angezeigt werden.  
  
9. **Überwachen des Integritätsstatus:**  Sie können die zuvor konfigurierten E-Mail-Benachrichtigungen verwenden oder die protokollierten Ereignisse manuell überwachen. Die folgenden Beispiele zeigen einige Transact-SQL-Anweisungen, mit denen die Ereignisse angezeigt werden können:  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    -- to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 Die in diesem Abschnitt beschriebenen Schritte sind speziell für die erste Konfiguration von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für die Datenbank vorgesehen. Sie können die vorhandenen Konfigurationen mithilfe derselben gespeicherten System Prozedur **smart_admin. sp_set_db_backup** ändern und die neuen Werte bereitstellen. Weitere Informationen finden Sie unter [SQL Server Managed Backup to Microsoft Azure Beibehaltungs-und Speichereinstellungen](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).  
  
### <a name="enable-includess_smartbackupincludesss-smartbackup-mdmd-for-the-instance-with-default-settings"></a>Aktivieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] mit Standardeinstellungen für die Instanz  
 In diesem Tutorial werden die Schritte zum Aktivieren und [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] Konfigurieren von für die Instanz "MyInstance\\" beschrieben. Es umfasst Schritte, um das Überwachen des [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]-Integritätsstatus zu aktivieren.  
  
 **Berechtigungen:**  
  
-   Erfordert die Mitgliedschaft in der Daten Bank Rolle **db_backupoperator** mit **ALTER ANY CREDENTIAL** - `EXECUTE` Berechtigungen und Berechtigungen für die gespeicherte Prozedur **sp_delete_backuphistory**.  
  
-   Erfordert **Select** -Berechtigungen für die **smart_admin. fn_get_current_xevent_settings**-Funktion.  
  
-   Erfordert `EXECUTE` Berechtigungen für die gespeicherte Prozedur **smart_admin. sp_get_backup_diagnostics** . Außerdem sind `VIEW SERVER STATE`-Berechtigungen erforderlich, da andere Systemobjekte, die diese Berechtigung erfordern, intern aufgerufen werden.  


1.  **Erstellen Sie ein Microsoft Azure Speicherkonto:** Die Sicherungen werden im Microsoft Azure Speicher Dienstanbieter gespeichert. Sie müssen zunächst ein Microsoft Azure Speicherkonto erstellen, wenn Sie noch nicht über ein Konto verfügen.
    - In SQL Server 2014 werden seitenblobs verwendet, die sich von Block-und anfügeblobs unterscheiden. Daher müssen Sie ein allgemeines Konto erstellen und kein BLOB-Konto. Weitere Informationen finden Sie unter Informationen [zu Azure Storage-Konten](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).
    - Notieren Sie den Speicherkontonamen und die Zugriffsschlüssel. Aus dem Speicherkontonamen und den Zugriffsschlüsseln werden SQL-Anmeldeinformationen erstellt. Die SQL-Anmeldeinformationen werden zur Authentifizierung beim Speicherkonto verwendet.  
  
2.  **Erstellen Sie SQL-Anmelde Informationen:** Erstellen Sie SQL-Anmelde Informationen, indem Sie den Namen des Speicher Kontos als Identität und den Speicherzugriffs Schlüssel als Kennwort verwenden.  
  
3.  **Sicherstellen, dass der SQL Server-Agent-Dienst ausgeführt wird:** Starten Sie den SQL Server-Agent, wenn er nicht ausgeführt wird. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] benötigt einen laufenden SQL Server-Agent auf der Instanz, um Sicherungsvorgänge durchführen zu können.  Sie können den Starttyp des SQL Server-Agents auf "Automatisch" festlegen, um zu gewährleisten, dass regelmäßige Sicherungsvorgänge durchgeführt werden können.  
  
4.  **Bestimmen des Aufbewahrungszeitraums:** Bestimmen Sie die Beibehaltungsdauer für die Sicherungsdateien. Die Beibehaltungsdauer wird in Tagen angegeben und kann zwischen 1 und 30 Tagen liegen. Sobald [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] auf Instanzebene mit Standardwerten aktiviert wurde, erben die neuen Datenbanken, die anschließend erstellt werden, die Einstellungen. Es werden nur Datenbanken unterstützt und automatisch konfiguriert, für die eine vollständige oder massenprotokollierte Wiederherstellung festgelegt wurde. Sie können [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] jederzeit für eine bestimmte Datenbank deaktivieren, wenn [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für diese Datenbank nicht verwendet werden soll. Außerdem können Sie die Konfiguration für eine bestimmte Datenbank ändern, indem Sie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] auf Datenbankebene konfigurieren.  
  
5.  **Aktivieren und Konfigurieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]:** Starten Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit der Instanz SQL Server her. Führen Sie im Abfragefenster folgende Anweisung aus, nachdem Sie die Werte für Datenbankname, SQL-Anmeldeinformationen, Beibehaltungsdauer und Verschlüsselungsoptionen Ihren Anforderungen entsprechend angepasst haben:  
  
     Weitere Informationen zum Erstellen eines Zertifikats für die Verschlüsselung finden Sie im Schritt **Erstellen eines Sicherungs Zertifikats** unter [Erstellen einer verschlüsselten Sicherung](create-an-encrypted-backup.md).  
  
    ```  
    Use msdb;  
    Go  
       EXEC smart_admin.sp_set_instance_backup  
                     @enable_backup=1  
                    ,@retention_days=30   
                    ,@credential_name='sqlbackuptoURL'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert';  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ist nun für diese Instanz aktiviert.  
  
6.  Überprüfen Sie die Konfigurationseinstellungen, indem Sie folgende Transact-SQL-Anweisung ausführen:  
  
    ```  
    Use msdb;  
    GO  
    SELECT * FROM smart_admin.fn_backup_instance_config ();  
  
    ```  
  
7.  Erstellen Sie eine neue Datenbank für die Instanz. Führen Sie die folgende Transact-SQL-Anweisung aus, um die Konfigurationseinstellungen von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für die Datenbank anzuzeigen:  
  
    ```  
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('NewDB')  
    ```  
  
     Es kann bis zu 15 Minuten dauern, bis die Einstellungen angezeigt und die Sicherungsvorgänge für die Datenbank gestartet werden.  
  
8.  **Aktivieren und Konfigurieren der Benachrichtigung für den Integritätsstatus:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] verfügt über eine gespeicherte Prozedur, die einen Agent-Auftrag erstellt, um E-Mail-Benachrichtigungen mit Fehlern oder Warnungen zu senden, die möglicherweise ein Eingreifen erfordern.  Wenn Sie diese E-Mail-Benachrichtigungen erhalten möchten, müssen Sie das Ausführen der gespeicherten Prozedur aktivieren, durch die ein SQL Server-Agentauftrag erstellt wird. In den folgenden Schritten wird der Prozess zum Aktivieren und Konfigurieren der E-Mail-Benachrichtigungen beschrieben:  
  
    1.  Richten Sie Datenbank-E-Mail ein, falls diese Funktion auf der Instanz noch nicht aktiviert wurde. Weitere Informationen finden Sie unter [Configure Database Mail](../database-mail/configure-database-mail.md).  
  
    2.  Konfigurieren Sie SQL Server-Agent-Benachrichtigungen für die Verwendung von Datenbank-E-Mail. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server-Agent-Mail zum Verwenden von Datenbank-E-Mails](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Aktivieren der E-mail-Benachrichtigungen für den Empfang von Sicherungsfehlern und Warnungen:** Führen Sie im Abfragefenster die folgenden Transact-SQL-Anweisungen aus:  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email address>'  
  
        ```  
  
         Weitere Informationen zum Überwachen und ein vollständiges Beispielskript finden [Sie unter Überwachen SQL Server verwalteten Sicherung in Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
9. **Anzeigen von Sicherungsdateien im Microsoft Azure Storage-Konto:** Stellen Sie eine Verbindung mit dem Speicherkonto von SQL Server Management Studio oder dem Azure-Verwaltungsportal her. Es wird ein Container für die Instanz von SQL Server angezeigt, die die Datenbank hostet, die Sie für die Verwendung von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] konfiguriert haben. Innerhalb der ersten 15 Minuten nach dem Erstellen einer neuen Datenbank sollten außerdem eine Datenbank- und eine Protokollsicherung angezeigt werden.  
  
10. **Überwachen des Integritätsstatus:**  Sie können die zuvor konfigurierten E-Mail-Benachrichtigungen verwenden oder die protokollierten Ereignisse manuell überwachen. Die folgenden Beispiele zeigen einige Transact-SQL-Anweisungen, mit denen die Ereignisse angezeigt werden können:  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    --  to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 Die Standardeinstellungen von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] können für eine bestimmte Datenbank überschrieben werden, indem die Einstellungen auf Datenbankebene konfiguriert werden. Außerdem können Sie den "[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]"-Dienst zeitweise anhalten und wieder fortsetzen. Weitere Informationen finden Sie unter [SQL Server Managed Backup to Microsoft Azure Beibehaltungs-und Speichereinstellungen](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md) .  
  
  
