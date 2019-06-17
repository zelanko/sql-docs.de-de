---
title: Überwachung von SQLServer Managed Backup für Windows Azure | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: cfb9e431-7d4c-457c-b090-6f2528b2f315
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b7b7b6cc8127b339a45a5f651af6db4d0b595b80
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62844580"
---
# <a name="monitor-sql-server-managed-backup-to-windows-azure"></a>Überwachen von SQL Server Managed Backup für Windows Azure
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verfügt über integrierte Measures, um Fehler und Probleme während der Sicherungsvorgänge zu identifizieren und wenn möglich mit Korrekturmaßnahmen zu beheben.  In bestimmten Situationen ist jedoch ein Benutzereingriff erforderlich. In diesem Thema werden die Tools beschrieben, mit denen Sie den Gesamtintegritätsstatus von Sicherungen bestimmen und ggf. zu behebende Fehler ermitteln können.  
  
## <a name="overview-of-includesssmartbackupincludesss-smartbackup-mdmd-built-in-debugging"></a>Übersicht über das in [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] integrierte Debuggen  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] überprüft geplante Sicherungen in regelmäßigen Abständen und versucht, fehlerhafte Sicherungen erneut zu planen. Er fragt das Speicherkonto in regelmäßigen Abständen, um Unterbrechungen in der Protokollkette der Datenbank zu identifizieren und entsprechend neue Sicherungen. Außerdem werden die Windows Azure-Einschränkungsrichtlinien berücksichtigt, und es sind Mechanismen vorhanden, um mehrere Datenbanksicherungen zu verwalten. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verwendet erweiterte Ereignisse, um alle Aktivitäten nachzuverfolgen. Die Kanäle für erweiterte Ereignisse, die vom [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Agent verwendet werden, umfassen Admin, Operational, Analytical und Debug. Ereignisse, die unter die Kategorie Admin fallen, stehen normalerweise im Zusammenhang mit Fehlern, erfordern einen Benutzereingriff und sind standardmäßig aktiviert. Analytical-Ereignisse sind ebenfalls standardmäßig aktiviert, beziehen sich aber normalerweise nicht auf Fehler, die einen Benutzereingriff erfordern. Operational-Ereignisse dienen typischerweise zu Informationszwecken. Operation-Ereignisse umfassen z. B. Planen einer Sicherung, die einen erfolgreichen Abschluss einer Sicherung usw. Debug ist am ausführlichsten und wird intern vom verwendet [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Probleme ermitteln und bei Bedarf zu beheben.  
  
### <a name="configure-monitoring-parameters-for-includesssmartbackupincludesss-smartbackup-mdmd"></a>Konfigurieren von Überwachungsparametern für [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]  
 Die **sp_set_parameter** im System gespeicherten Prozedur ermöglicht Ihnen, überwachungseinstellungen anzugeben. Die folgenden Abschnitte führen Sie durch den Vorgang zum Aktivieren erweiterter Ereignisse und zum Aktivieren von E-Mail-Benachrichtigungen bei Fehlern und Warnungen.  
  
 Die **smart_admin.fn_get_parameter** Funktion kann verwendet werden, um die aktuelle Einstellung für einen bestimmten Parameter oder für alle konfigurierten Parameter abgerufen. Wenn die Parameter nicht konfiguriert wurden, gibt die Funktion keine Werte zurück.  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie dann auf **Ausführen**. Dadurch wird die aktuelle Konfiguration für erweiterte Ereignisse und E-Mail-Benachrichtigungen zurückgegeben.  
  
```  
Use msdb  
Go  
SELECT * FROM smart_admin.fn_get_parameter (NULL)  
GO  
```  
  
 Weitere Informationen finden Sie unter [smart_admin.fn_get_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)  
  
### <a name="extended-events-for-monitoring"></a>Erweiterte Ereignisse für die Überwachung  
 Standardmäßig sind Admin-, Operational- und Analytical-Ereignisse aktiviert. Admin-Ereignisse sind am wichtigsten und hilfreich für die Ermittlung von Fehlern, die zur Behebung des Problems manuelle Eingriffe erfordern. Sie können die Operational- und Debug-Ereignisse aktivieren, Sie sollten aber bedenken, dass diese Ereignisse ausführlich sind und möglicherweise gefiltert werden müssen. Die folgenden Verfahren beschreiben, wie Sie über die erweiterten Ereignisse protokollierte Ereignisse überwachen können.  
  
> [!IMPORTANT]  
>  Im Gegensatz zu erweiterten Ereignissen für SQL Engine unterstützt [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] die Konzepte von Sitzungen für erweiterte Ereignisse nicht. Gespeicherte Systemprozeduren und -funktionen sind die Tools für die Interaktion mit erweiterten Ereignissen. Sie können das Protokoll für erweiterte Ereignisse im Protokollverzeichnis anzeigen.  
  
##### <a name="to-configure-and-view-extended-events"></a>So konfigurieren Sie erweiterte Ereignisse und zeigen sie an  
  
1.  Führen Sie die folgende Abfrage aus, um verfügbare Kanäle für erweiterte Ereignisse und ihren aktuellen Status anzuzeigen:  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     In der Ausgabe dieser Abfrage wird der event_name angezeigt und ob es konfiguriert werden kann und derzeit aktiviert ist.  Weitere Informationen finden Sie unter [smart_admin.fn_get_current_xevent_settings &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql).  
  
2.  Um Debug-Ereignisse zu aktivieren, führen Sie die folgende Abfrage aus:  
  
    ```  
    --  to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
     Weitere Informationen zur gespeicherten Prozedur finden Sie unter [sp_set_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql).  
  
3.  Führen Sie die folgende Abfrage aus, um die protokollierten Ereignisse anzuzeigen:  
  
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
  
### <a name="aggregated-error-countshealth-status"></a>Aggregierte Fehleranzahl/Integritätsstatus  
 Die **smart_admin.fn_get_health_status** Funktionsergebnis ist eine Tabelle mit aggregierten Fehleranzahl für jede Kategorie, die verwendet werden können, zum Überwachen des Integritätsstatus von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Die gleiche Funktion verwendet auch der vom System konfigurierte E-Mail-Benachrichtigungsmechanismus, der weiter unten in diesem Thema beschrieben ist.   
Anhand dieser aggregierten Anzahl kann die Systemintegrität überwacht werden. Wenn beispielsweise die Spalte number_ of_retention_loops 0 in 30 Minuten ist, benötigt die Beibehaltungsverwaltung viel Zeit oder funktioniert nicht korrekt. Spalten mit Werten ungleich 0 können auf Probleme hindeuten. Sie sollten die Protokolle der erweiterten Ereignisse prüfen, um das Problem zu bestimmen. Rufen Sie alternativ **smart_admin.sp_get_backup_diagnostics** gespeicherte Prozedur, um die Details des Fehlers zu finden.  
  
### <a name="using-agent-notification-for-assessing-backup-status-and-health"></a>Verwenden von Agent-Benachrichtigungen zum Bewerten von Sicherungsstatus und -integrität  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verfügt über einen Benachrichtigungsmechanismus, der auf Verwaltungsrichtlinien auf Grundlage von SQL Server-Richtlinien beruht.  
  
 **Voraussetzungen:**  
  
-   Datenbank-E-Mail ist erforderlich, um diese Funktionen verwenden zu können. Weitere Informationen zum Aktivieren von Datenbank-e-Mails für die Instanz von SQL Server finden Sie unter [Konfigurieren von Datenbank-e-Mails](../relational-databases/database-mail/configure-database-mail.md).  
  
-   Die Eigenschaften des SQL Server-Agent-Warnsystems sollten für die Verwendung der Datenbank-E-Mail festgelegt werden.  
  
 **Benachrichtigungsarchitektur:**  
  
-   **Richtlinienbasierte Verwaltung:** Zwei Richtlinien werden zum Überwachen der Sicherungsintegrität festgelegt: **Smart Admin Integritätsrichtlinie**, und die **Smart Admin Integritätsrichtlinie zur Benutzeraktion**. Die Smart Admin-Richtlinie für die Systemintegrität wertet kritische Fehler wie fehlende oder ungültige SQL-Anmeldeinformationen oder Verbindungsfehler aus und meldet die Integrität des Systems. Bei diesen ist normalerweise ein manueller Eingriff erforderlich, um das zugrunde liegende Problem zu beheben. Die Smart Admin-Richtlinie für die Integrität von Benutzeraktionen wertet Warnungen aus, z. B. beschädigte Sicherungen.  Bei diesen ist möglicherweise keine Aktion erforderlich, sondern stellen lediglich eine Warnung zu einem Ereignis dar. Es wird erwartet, dass solche Probleme automatisch vom [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Agent behandelt werden.  
  
-   **SQL Server-Agent** Auftrag: Die Benachrichtigung erfolgt mithilfe eines SQL Server-Agent-Auftrags, das drei Auftragsschritte umfasst. Im ersten Auftragsschritt wird ermittelt, ob [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Datenbank oder eine Instanz konfiguriert ist. Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] aktiviert und konfiguriert vorgefunden wird, wird der zweite Schritt ausgeführt: Es wird ein PowerShell-Cmdlet ausgeführt, das den Integritätsstatus bewertet, indem die Verwaltungsrichtlinien auf Grundlage von SQL Server-Richtlinien ausgewertet werden. Wenn ein Fehler oder Warnung gefunden wird, schlägt fehl, die dann den dritten Schritt ausgelöst: Der dritte Schritt sendet eine e-Mail-Benachrichtigung mit dem Bericht Fehler/Warnung.  Dieser SQL Server-Agent-Auftrag ist jedoch nicht standardmäßig aktiviert. Um den e-Mail-benachrichtigungsauftrag zu aktivieren, verwenden die **smart_admin.sp_set_backup_parameter** gespeicherten Systemprozedur.  Das folgende Verfahren beschreibt diese Schritte ausführlicher:  
  
##### <a name="enabling-email-notification"></a>Aktivieren der E-Mail-Benachrichtigung  
  
1.  Wenn die Datenbank-e-Mails nicht bereits konfiguriert ist, verwenden Sie die Schritte in [Konfigurieren von Datenbank-e-Mails](../relational-databases/database-mail/configure-database-mail.md).  
  
2.  Set-Datenbank als Mailsystem für SQL Server-Warnungssystem: Der rechten Maustaste auf **SQL Server-Agent**Option **Warnungssystem**, überprüfen Sie die **Mailprofil aktivieren** Feld wählen **Database Mail** als die  **E-Mail-System**, und wählen Sie ein zuvor erstelltes e-Mail-Profil.  
  
3.  Führen Sie die folgende Abfrage in einem Abfragefenster aus, und geben Sie die E-Mail-Adresse an, an die die Benachrichtigung gesendet werden soll:  
  
    ```  
    Use msdb  
    Go  
    EXEC smart_admin.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'  
  
    ```  
  
     Dadurch wird ein SQL Server-Agent-Auftrag erstellt, der zum Abrufen des Integritätsstatus und zum Senden von Benachrichtigungen verwendet wird, wenn ein Fehler oder ein Problem mit Sicherungen auftritt.  
  
 Im Folgenden ist ein Beispielskript aufgeführt, mit dem die Datenbank-E-Mail aktiviert und E-Mail-Benachrichtigungen über den SQL Server-Agent-Auftrag eingerichtet werden:  
  
```  
-- Prereq: Make sure that SQL Server service runs in a service account that has  
--  access to SMTP Server   
-- set SQL Server service account as domain account   
  
EXEC sp_configure 'show advanced', 1  
RECONFIGURE  
GO  
  
-- Enable DBMail  
EXEC sp_configure 'Database Mail XPs',1  
GO  
RECONFIGURE  
GO  
  
-- Configure DBMail  
DECLARE @emailid NVARCHAR(255)  
-- Note: change this email to your own email id  
SET @emailid = N'emailalias@mycompany.com'  
  
DECLARE @smtpserver NVARCHAR(255)  
SET @smtpserver = N'smtphost.domainname.com'  
  
DECLARE @mailprofile NVARCHAR(255)  
SET @mailprofile = N'my_profile'  
  
EXEC msdb.dbo.sysmail_add_account_sp @account_name=N'myaccount',  
                @email_address = @emailid,  
                @replyto_address = @emailid,  
                @mailserver_name = @smtpserver,  
                @use_default_credentials = 1  
  
EXEC msdb.dbo.sysmail_add_profile_sp @profile_name=@mailprofile  
EXEC msdb.dbo.sysmail_add_profileaccount_sp @profile_name=@mailprofile, @account_name=N'myaccount', @sequence_number=1  
  
-- Set SQL Agent to use DBMail profile  
EXEC msdb.dbo.sp_set_sqlagent_properties @databasemail_profile = @mailprofile  
  
-- Configure Notifications   
EXEC msdb.smart_admin.sp_set_parameter  
@parameter_name = 'SSMBackup2WANotificationEmailIds',  
@parameter_value = @emailid  
  
-- To test is you are receiving notifications  
-- delete few backup files from your storage container, Wait for 15 minutes & see if you get any email notification  
  
```  
  
### <a name="using-powershell-to-setup-custom-health-monitoring"></a>Einrichten einer benutzerdefinierten Integritätsüberwachung mit PowerShell  
 Die **Test-SqlSmartAdmin** Cmdlet kann verwendet werden, um benutzerdefinierte Integritätsüberwachung erstellen. Beispielsweise kann die im vorhergehenden Abschnitt beschriebene Benachrichtigungsoption auf Instanzebene konfiguriert werden.  Wenn Sie mehrere SQL Server-Instanzen für die Verwendung von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] konfiguriert haben, können Sie mit dem PowerShell-Cmdlet Skripts erstellen, die den Status und die Integrität von Sicherungen für alle Instanzen erfassen.  
  
 Die **Test-SqlSmartAdmin** Cmdlet wertet die Fehler und Warnungen zurückgegeben, durch die Richtlinien von SQL Server-Verwaltung und meldet einen Rollup des Status.  Dieses Cmdlet verwendet standardmäßig die Systemrichtlinien. Mit dem `-AllowUserPolicies`-Parameter können Sie beliebige benutzerdefinierte Richtlinien einschließen.  
  
 Im Folgenden ist ein PowerShell-Beispielskript aufgeführt, das einen Bericht über Fehler und Warnungen auf Grundlage der Systemrichtlinien und ggf. von erstellten Benutzerrichtlinien zurückgibt:  
  
```  
$policyResults = get-sqlsmartadmin | test-sqlsmartadmin -AllowUserPolicies  
$policyResults.PolicyEvaluationDetails | select Name, Category, Expression, Result, Exception | fl  
  
```  
  
 Mit dem folgenden Skript wird ein ausführlicher Bericht der Fehler und Warnungen für die Standardinstanz zurückgegeben:  
  
```  
PS C:\>PS SQLSERVER:\SQL\COMPUTER\DEFAULT> (get-sqlsmartadmin ).EnumHealthStatus()  
```  
  
### <a name="objects-in-msdb-database"></a>Objekte in einer MSDB-Datenbank  
 Einige Objekte werden installiert, um die Funktionalität zu implementieren. Diese Objekte sind für die interne Verwendung reserviert. Eine Systemtabelle kann jedoch bei der Überwachung des Sicherungsstatus von Nutzen sein: smart_backup_files. Die meisten der in dieser Tabelle, die für die Überwachung wie des Typs der Sicherung der Datenbank gespeicherten Informationen, erste und letzte Lsn, Ablaufdaten für Sicherungen werden durch die Systemfunktion verfügbar gemacht [fn_available_backups &#40;Transact-SQL &#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql). Die Statusspalte in der smart_backup_files-Tabelle, die den Status der Sicherungsdatei angibt, ist bei Verwendung der Funktion jedoch nicht verfügbar. Mithilfe der folgenden Beispielabfrage können verschiedene Informationen, u. a. auch der Status, aus der Systemtabelle abgerufen werden:  
  
```  
USE msdb  
GO  
SELECT  
 database_name AS [Database Name]  
,backup_path AS [Backup Destination and File]  
,[Backup Type] =  
CASE backup_type  
WHEN 1 THEN 'FULL'  
WHEN 2 THEN 'LOG'  
END  
,[Backup Status] =  
CASE [status]  
WHEN 'A' THEN 'Available'  
WHEN 'B' THEN 'Copy In Progress'  
WHEN 'C' THEN 'Corrupted'  
WHEN 'D' THEN 'Deleted'  
WHEN 'F' THEN 'Copy Failed'  
WHEN 'U' THEN 'Unknown'  
END  
,first_lsn AS [First LSN]  
,last_lsn AS [Last LSN]  
,backup_start_date AS [Backup Start Time]  
,backup_finish_date AS [Backup Completion Time]  
,expiration_date AS [Backup Expiry Date/Time]  
FROM  
smart_backup_files;  
  
```  
  
 Im Folgenden werden die unterschiedlichen zurückgegebenen Statusangaben ausführlich erläutert:  
  
-   **Verfügbar – A:** Dies ist eine normale Sicherungsdatei. Die Sicherung wurde abgeschlossen und auch daraufhin überprüft, ob sie im Windows Azure-Speicher verfügbar ist.  
  
-   **Kopieren wird ausgeführt-B:** Dieser Status ist speziell für die Datenbanken der Verfügbarkeitsgruppe. Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] eine Unterbrechung in der Sicherungsprotokollkette feststellt, wird zunächst versucht, die Sicherung zu ermitteln, die die Unterbrechung in der Sicherungskette verursacht hat. Falls die Sicherungsdatei gefunden wird, wird sie in den Windows Azure-Speicher kopiert. Dieser Status wird angezeigt, wenn der Kopiervorgang gerade ausgeführt wird.  
  
-   **Fehler beim Kopieren der-F:** Ähnlich wie im Status des Kopiervorgangs, ist dies speziell Availability Group-Datenbanken. Wenn der Kopiervorgang fehlschlägt, lautet der Status F.  
  
-   **Beschädigt: "c:"** Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] wird die Sicherungsdatei im Speicher zu überprüfen, indem Sie Ausführung eines RESTORE HEADER_ONLY-Befehls selbst nach mehreren Versuchen nicht, markiert diese Datei als beschädigt. Damit die beschädigte Datei keine Unterbrechung in der Sicherungskette verursacht, wird von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] eine Sicherung geplant.  
  
-   **Gelöscht: "d:"** Die entsprechende Datei wurde in Windows Azure-Speicher nicht gefunden. Wenn die gelöschte Datei eine Unterbrechung in der Sicherungskette verursacht, wird von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] eine Sicherung geplant.  
  
-   **Unknown (unbekannt) U:** Dieser Status gibt an, die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] wurde noch nicht vorhanden und seine Eigenschaften im Windows Azure-Speicher zu überprüfen. Wenn der Prozess zum nächsten Mal ausgeführt wird, d. h. alle 15 Minuten, wird dieser Status aktualisiert.  
  
  
