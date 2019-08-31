---
title: Einrichten SQL Server verwalteten Sicherung in Azure für Verfügbarkeits Gruppen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 0c4553cd-d8e4-4691-963a-4e414cc0f1ba
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aa2cbce81827c9085f87112b366d532077915f58
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176101"
---
# <a name="setting-up-sql-server-managed-backup-to-azure-for-availability-groups"></a>Einrichten der verwalteten SQL Server-Sicherung in Azure für Verfügbarkeitsgruppen
  Dieses Thema ist ein Lernprogramm zum Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für Datenbanken, die an AlwaysOn-Verfügbarkeitsgruppen teilnehmen.  
  
## <a name="availability-group-configurations"></a>Verfügbarkeitsgruppenkonfigurationen  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]wird für Datenbanken der Verfügbarkeits Gruppe unterstützt, unabhängig davon, ob die Replikate lokal oder vollständig in Azure konfiguriert sind oder eine Hybrid Implementierung zwischen lokalen Systemen und einem oder mehreren virtuellen Azure-Computern. Allerdings müssen bei einigen Implementierungen u. U. folgende Aspekte berücksichtigt werden:  
  
-   Häufigkeit der Protokoll Sicherung: Die Häufigkeit der Protokoll Sicherung ist sowohl Zeit-als auch Protokoll Vergrößerung. Beispielsweise wird alle zwei Stunden eine Protokollsicherung ausgeführt, es sei denn, der innerhalb des zweistündigen Zeitraums belegte Protokollspeicherplatz wächst auf fünf oder mehr MB an. Dies gilt ausnahmslos für lokale, cloudbasierte und Hybridimplementierungen.  
  
-   Netzwerkbandbreite: Dies gilt für Implementierungen, bei denen sich die Replikate an unterschiedlichen physischen Standorten befinden, wie z. b. in einem Hybrid Cloud oder über verschiedene Azure-Regionen in einer reinen cloudkonfiguration. Die Netzwerkbandbreite kann die Latenz der sekundären Replikate beeinflussen, und wenn für die sekundären Replikate die synchrone Replikation festgelegt ist, kann das Protokoll auf dem primären Replikat anwachsen. Wenn für die sekundären Replikate die synchrone Replikation festgelegt wurde, können sie aufgrund der Netzwerklatenz u. U. nicht mehr Schritt halten, was bei einem Failover auf das sekundäre Replikat zu Datenverlusten führen kann.  
  
### <a name="configuring-includess_smartbackupincludesss-smartbackup-mdmd-for-availability-databases"></a>Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für Verfügbarkeitsdatenbanken.  
 **Berechtigungen:**  
  
-   Erfordert die Mitgliedschaft in der Daten Bank Rolle **db_backupoperator** mit **ALTER ANY CREDENTIAL** - `EXECUTE` Berechtigungen und Berechtigungen für die gespeicherte Prozedur **sp_delete_backuphistory**.  
  
-   Erfordert **Select** -Berechtigungen für die **smart_admin. fn_get_current_xevent_settings**-Funktion.  
  
-   Erfordert `EXECUTE` Berechtigungen für die gespeicherte Prozedur **smart_admin. sp_get_backup_diagnostics** . Außerdem sind `VIEW SERVER STATE`-Berechtigungen erforderlich, da andere Systemobjekte, die diese Berechtigung erfordern, intern aufgerufen werden.  
  
-   Erfordert `EXECUTE` Berechtigungen für die `smart_admin.sp_set_instance_backup` gespeicherten `smart_admin.sp_backup_master_switch` Prozeduren und.  
  
 Die folgenden allgemeinen Schritte sind zum Einrichten einer AlwaysOn-Verfügbarkeitsgruppe mit [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] erforderlich. Ein ausführliches schrittweises Lernprogramm wird weiter unten in diesem Thema beschrieben.  
  
1.  Konfigurieren Sie nach dem Erstellen der Verfügbarkeitsgruppe das bevorzugte Sicherungsreplikat. Diese Einstellung der Verfügbarkeitsgruppe wird auch von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verwendet, um festzustellen, welches Replikat für die Sicherung verwendet werden soll. Schritt-für-Schritt-Anleitungen zum Einrichten der Sicherungs Einstellungen finden Sie unter [Konfigurieren der Sicherung auf &#40;Verfügbarkeits&#41;Replikaten SQL Server](availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).  Wenn Sie eine neue AlwaysOn-Verfügbarkeits Gruppe erstellen, lesen Sie die Informationen unter [Getting Started with &#40;AlwaysOn-Verfügbarkeitsgruppen SQL Server&#41;](availability-groups/windows/getting-started-with-always-on-availability-groups-sql-server.md).  
  
2.  Konfigurieren Sie den schreibgeschützten Verbindungszugriff auf sekundäre Replikate. Schritt-für-Schritt-Anleitungen zum Konfigurieren des schreibgeschützten Zugriffs finden Sie unter [Konfigurieren des schreibgeschützten Zugriffs auf ein &#40;Verfügbarkeits Replikat SQL Server&#41; ](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
3.  Geben Sie das Sicherungsreplikat an. Die Einstellung für das bevorzugte Sicherungsreplikat wird von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verwendet, um festzustellen, welche Datenbank für die Planung von Sicherungen verwendet werden soll.  Verwenden Sie die [sys. fn_hadr_backup_is_preferred_replica &#40;-Transact-SQL&#41; ](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) -Funktion, um zu bestimmen, ob das aktuelle Replikat das bevorzugte Sicherungs Replikat ist.  
  
4.  Führen [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Sie auf jedem Replikat die Konfiguration für die Datenbank mithilfe der gespeicherten Prozedur " **Smart-admin. sp_set_db_backup** " aus.  
  
     [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]  **Verhalten[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] nach einem Failover:** funktioniert nach einem failoverereignis weiterhin und behält Sicherungskopien und die Wiederherstellbarkeit bei. Nach einem Failover sind keine speziellen Aktionen erforderlich.  
  
#### <a name="considerations-and-requirements"></a>Überlegungen und Anforderungen:  
 Bei der Konfiguration von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für Datenbanken, die Teil einer AlwaysOn-Verfügbarkeitsgruppe sind, müssen bestimmte Überlegungen und Anforderungen berücksichtigt werden. In der folgenden Liste werden Überlegungen und Anforderungen aufgeführt:  
  
-   Die Konfigurationseinstellungen für [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] müssen für alle Datenbanken auf allen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Knoten einer Verfügbarkeitsgruppe gleich sein. Dies erreichen Sie, indem Sie entweder für die primäre Datenbank und für alle Replikate auf der Datenbankebene dieselbe Konfiguration für [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] festlegen, oder indem Sie dieselben Standardeinstellungen für [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf allen Knoten festlegen, die Teil der Verfügbarkeitsgruppen sind. Es wird empfohlen, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für die Datenbank festzulegen, da durch die Konfiguration von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Datenbankebene die Einstellungen auf die Datenbanken begrenzt bleiben und Änderungen an den Standardeinstellungen alle anderen Datenbanken auf den Instanzen betreffen.  
  
-   Geben Sie das Sicherungsreplikat an. Die bevorzugte Sicherungsreplikateinstellung wird von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verwendet, um die Sicherungen zu planen. Verwenden Sie die [sys. fn_hadr_backup_is_preferred_replica &#40;-Transact-SQL&#41; ](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) -Funktion, um zu bestimmen, ob das aktuelle Replikat das bevorzugte Sicherungs Replikat ist.  
  
-   Wenn das sekundäre Replikat als bevorzugtes Replikat konfiguriert ist, muss für dieses Replikat mindestens ein schreibgeschützter Verbindungszugriff konfiguriert werden. Verfügbarkeitsgruppen, die keinen Verbindungszugriff auf sekundäre Datenbanken haben, werden nicht unterstützt.  Weitere Informationen finden Sie unter [Konfigurieren des schreibgeschützten Zugriffs auf ein Verfügbarkeitsreplikat &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md).  
  
-   Wenn Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] konfigurieren, nachdem Sie die Verfügbarkeitsgruppe konfiguriert haben, versucht [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], alle vorhandenen Sicherungen in den Speichercontainer zu kopieren.  Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] keine vorhandenen Sicherungen findet bzw. nicht auf diese zugreifen kann, wird eine vollständige Datenbanksicherung geplant. Dieser Schritt dient speziell der Optimierung von Sicherungsvorgängen für Datenbanken in einer Verfügbarkeitsgruppe.  
  
-   Möglicherweise möchten Sie die Einstellungen auf Instanzebene deaktivieren, wenn Sie eine neue Verfügbarkeits Datenbank erstellen, und Sie beabsichtigen nicht, die Einstellungen auf Instanzebene auf die Datenbank anzuwenden.  
  
-   Bei Verwendung der Verschlüsselung verwenden Sie dasselbe Zertifikat auf allen Replikaten. Auf diese Weise ist gewährleistet, dass Sicherungsvorgänge im Falle eines Failovers oder einer Wiederherstellung auf einem anderen Replikat kontinuierlich und unterbrechungsfrei verlaufen.  
  
#### <a name="enable-and-configure-includess_smartbackupincludesss-smartbackup-mdmd-for-an-availability-database"></a>Aktivieren und Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Verfügbarkeitsdatenbank  
 In diesem Lernprogramm werden die Schritte zum Aktivieren und Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Datenbank (AGTestDB) auf den Computern Node1 und Node2 beschrieben, gefolgt von den Schritten, mit denen die Überwachung des Integritätsstatus von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] aktiviert wird.  
  
1.  **Erstellen eines Azure-Speicherkontos:** Die Sicherungen werden im Azure-BLOB-Speicherdienst gespeichert. Sie müssen zunächst ein Azure-Speicherkonto erstellen, falls Sie noch nicht über ein Konto verfügen. Weitere Informationen finden Sie unter [Erstellen eines Azure Storage Kontos](http://www.windowsazure.com/manage/services/storage/how-to-create-a-storage-account/). Notieren Sie sich den Namen und die URL des Speicherkontos sowie die Zugriffsschlüssel. Aus dem Speicherkontonamen und den Zugriffsschlüsseln werden SQL-Anmeldeinformationen erstellt. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verwendet die SQL-Anmeldeinformationen während Sicherungsvorgängen, um sich beim Speicherkonto zu authentifizieren.  
  
2.  **Erstellen Sie SQL-Anmelde Informationen:** Erstellen Sie SQL-Anmelde Informationen, indem Sie den Namen des Speicher Kontos als Identität und den Speicherzugriffs Schlüssel als Kennwort verwenden.  
  
3.  **Sicherstellen, dass der SQL Server-Agent-Dienst ausgeführt wird:** Starten Sie den SQL Server-Agent, wenn er nicht ausgeführt wird. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] benötigt einen laufenden SQL Server-Agent auf der Instanz, um Sicherungsvorgänge durchführen zu können.  Sie können den SQL-Agent automatisch ausführen lassen, um zu gewährleisten, dass regelmäßig Sicherungen ausgeführt werden können.  
  
4.  **Bestimmen des Aufbewahrungszeitraums:** Bestimmen Sie die Beibehaltungs Dauer für die Sicherungsdateien. Die Beibehaltungsdauer wird in Tagen angegeben und kann zwischen 1 und 30 Tagen liegen. Die Beibehaltungsdauer bestimmt den Zeitraum für die Wiederherstellbarkeit der Datenbank.  
  
5.  **Erstellen Sie ein Zertifikat oder einen asymmetrischen Schlüssel für die Verschlüsselung während der Wiederherstellung:** Erstellen Sie das Zertifikat auf dem ersten Knoten Node1, und exportieren Sie es dann in eine Datei mit dem [Sicherungs Zertifikat &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql). Erstellen Sie auf Node2 mithilfe der von Node1 exportierten Datei ein Zertifikat. Weitere Informationen zum Erstellen eines Zertifikats aus einer Datei finden Sie im Beispiel unter [Create Certificate &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).  
  
6.  **Aktivieren und konfigurieren [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] von für agtestdb auf Node1:** Starten Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit der Instanz auf Node1 her, wo die Verfügbarkeits Datenbank installiert ist Führen Sie im Abfragefenster folgende Anweisung aus, nachdem Sie die Werte für Datenbankname, Speicher-URL, SQL-Anmeldeinformationen und Beibehaltungsdauer Ihren Anforderungen entsprechend angepasst haben:  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='AGTestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     Weitere Informationen zum Erstellen eines Zertifikats für die Verschlüsselung finden Sie im Schritt **Erstellen eines Sicherungs Zertifikats** unter [Erstellen einer verschlüsselten Sicherung](../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
7.  **Aktivieren und konfigurieren [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] von für agtestdb auf Node2:** Starten Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit der Instanz auf Node2 her, wo die Verfügbarkeits Datenbank installiert ist Führen Sie im Abfragefenster folgende Anweisung aus, nachdem Sie die Werte für Datenbankname, Speicher-URL, SQL-Anmeldeinformationen und Beibehaltungsdauer Ihren Anforderungen entsprechend angepasst haben:  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='AGTestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ist damit für die angegebene Datenbank aktiviert. Es kann bis zu 15 Minuten dauern, bis die Sicherungsvorgänge für die Datenbank gestartet werden. Die Sicherung wird auf dem bevorzugten Sicherungsreplikat durchgeführt.  
  
8.  **Überprüfen der Standardkonfiguration für erweiterte Ereignisse:**  Überprüfen Sie die Konfiguration für erweiterte Ereignisse, indem Sie die folgende Transact-SQL- [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Anweisung auf dem Replikat ausführen, das von zum Planen der Sicherungen verwendet wird. Dies ist i. d. R. die Einstellung für das bevorzugte Sicherungsreplikat der Verfügbarkeitsgruppe, zu der die Datenbank gehört.  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     Stellen Sie sicher, dass Ereignisse der Kanäle Admin, Operational und Analytical standardmäßig aktiviert sind und nicht deaktiviert werden können. Dies sollte ausreichen, um alle Ereignisse zu überwachen, die ein manuelles Eingreifen erfordern.  Sie können die Debugereignisse aktivieren. Diese Kanäle enthalten jedoch Informations- und Debugereignisse, die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] zur Erkennung und Behebung von Fehlern verwendet. Weitere Informationen finden Sie unter [überwachen SQL Server verwalteten Sicherung in Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
9. **Aktivieren und Konfigurieren der Benachrichtigung für den Integritätsstatus:** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verfügt über eine gespeicherte Prozedur, die einen Agent-Auftrag erstellt, um E-Mail-Benachrichtigungen mit Fehlern oder Warnungen zu senden, die möglicherweise ein Eingreifen erfordern.  Wenn Sie diese E-Mail-Benachrichtigungen erhalten möchten, müssen Sie das Ausführen der gespeicherten Prozedur aktivieren, durch die ein SQL Server-Agentauftrag erstellt wird. In den folgenden Schritten wird der Prozess zum Aktivieren und Konfigurieren der E-Mail-Benachrichtigungen beschrieben:  
  
    1.  Richten Sie Datenbank-E-Mail ein, falls diese Funktion auf der Instanz noch nicht aktiviert wurde. Weitere Informationen finden Sie unter [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).  
  
    2.  Konfigurieren Sie SQL Server-Agent-Benachrichtigungen für die Verwendung von Datenbank-E-Mail. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server-Agent-Mail zum Verwenden von Datenbank-E-Mails](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Aktivieren der E-mail-Benachrichtigungen für den Empfang von Sicherungsfehlern und Warnungen:** Führen Sie im Abfragefenster die folgenden Transact-SQL-Anweisungen aus:  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email>'  
  
        ```  
  
         Weitere Informationen und ein vollständiges Beispielskript finden [Sie unter Überwachen SQL Server verwalteten Sicherung in Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
10. **Anzeigen von Sicherungsdateien im Azure Storage Konto:** Stellen Sie eine Verbindung mit dem Speicherkonto von SQL Server Management Studio oder dem Azure-Verwaltungsportal her. Es wird ein Container für die Instanz von SQL Server angezeigt, die die Datenbank hostet, die Sie für die Verwendung von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] konfiguriert haben. Innerhalb der ersten 15 Minuten nach dem Aktivieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für die Datenbank können außerdem eine Datenbank- und eine Protokollsicherung angezeigt werden.  
  
11. **Überwachen des Integritätsstatus:**  Sie können die zuvor konfigurierten E-Mail-Benachrichtigungen verwenden oder die protokollierten Ereignisse manuell überwachen. Die folgenden Beispiele zeigen einige Transact-SQL-Anweisungen, mit denen die Ereignisse angezeigt werden können:  
  
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
    event varchar (512),  
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
  
 Die in diesem Abschnitt beschriebenen Schritte sind speziell für die erste Konfiguration von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für die Datenbank vorgesehen. Sie können die vorhandenen Konfigurationen mithilfe derselben gespeicherten System Prozedur **smart_admin. sp_set_db_backup** ändern und die neuen Werte bereitstellen. Weitere Informationen finden Sie unter [SQL Server verwaltete Sicherung in Azure-Beibehaltungs-und Speichereinstellungen](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).  
  
### <a name="considerations-when-removing-a-database-from-alwayson-availability-group-configuration"></a>Überlegungen zum Entfernen einer Datenbank aus der Konfiguration für eine AlwaysOn-Verfügbarkeitsgruppe  
 Wenn eine Datenbank aus der Konfiguration der AlwaysOn-Verfügbarkeits Gruppe entfernt wird und jetzt eine eigenständige Datenbank ist, empfiehlt es sich, eine Sicherung mithilfe von [smart_admin &#40;.&#41;sp_backup_on_demand Transact-SQL](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql)durchgeführt werden. Wenn Sie auf diese Weise eine Datenbanksicherung erstellen, entsteht eine neue Sicherungskette, und die Datei wird im instanzspezifischen Container anstatt im Verfügbarkeitscontainer abgelegt, in dem die Sicherungen gespeichert wurden, als die Datenbank Teil der Verfügbarkeitsgruppe war.  
  
> [!WARNING]  
>  Die Wiederherstellbarkeit der Datenbank in diesem Szenario aus Sicherungen, die vor der Änderung des Verfügbarkeitsgruppenstatus durchgeführt wurden, ist nicht gewährleistet.  
  
  
