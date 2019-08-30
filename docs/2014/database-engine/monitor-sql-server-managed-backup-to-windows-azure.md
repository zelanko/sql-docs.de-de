---
title: Überwachen SQL Server verwalteten Sicherung in Azure | Microsoft-Dokumentation
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
ms.openlocfilehash: 761e2e6ee0da9597433c0f0805aa1d8caf42fbac
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154093"
---
# <a name="monitor-sql-server-managed-backup-to-azure"></a>Überwachen SQL Server verwalteten Sicherung in Azure
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verfügt über integrierte Measures, um Fehler und Probleme während der Sicherungsvorgänge zu identifizieren und wenn möglich mit Korrekturmaßnahmen zu beheben.  In bestimmten Situationen ist jedoch ein Benutzereingriff erforderlich. In diesem Thema werden die Tools beschrieben, mit denen Sie den Gesamtintegritätsstatus von Sicherungen bestimmen und ggf. zu behebende Fehler ermitteln können.  
  
## <a name="overview-of-includess_smartbackupincludesss-smartbackup-mdmd-built-in-debugging"></a>Übersicht über das in [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] integrierte Debuggen  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] überprüft geplante Sicherungen in regelmäßigen Abständen und versucht, fehlerhafte Sicherungen erneut zu planen. Das Speicherkonto wird regelmäßig abgefragt, um Unterbrechungen in Protokoll Ketten zu identifizieren, die sich auf die Wiederherstellbarkeit der Datenbank auswirken, und neue Sicherungen entsprechend Außerdem werden die Richtlinien für die Azure-Drosselung berücksichtigt, und es gelten Mechanismen für die Verwaltung mehrerer Datenbanksicherungen. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verwendet erweiterte Ereignisse, um alle Aktivitäten nachzuverfolgen. Die Kanäle für erweiterte Ereignisse, die vom [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Agent verwendet werden, umfassen Admin, Operational, Analytical und Debug. Ereignisse, die unter die Kategorie Admin fallen, stehen normalerweise im Zusammenhang mit Fehlern, erfordern einen Benutzereingriff und sind standardmäßig aktiviert. Analytical-Ereignisse sind ebenfalls standardmäßig aktiviert, beziehen sich aber normalerweise nicht auf Fehler, die einen Benutzereingriff erfordern. Operational-Ereignisse dienen typischerweise zu Informationszwecken. Zu den Betriebs Ereignissen zählen beispielsweise das Planen einer Sicherung, der erfolgreiche Abschluss der Sicherung usw. Das Debuggen ist die ausführlichste und wird intern von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verwendet, um Probleme zu ermitteln und ggf. zu korrigieren.  
  
### <a name="configure-monitoring-parameters-for-includess_smartbackupincludesss-smartbackup-mdmd"></a>Konfigurieren von Überwachungsparametern für [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]  
 Mit der gespeicherten System Prozedur **smart_admin. sp_set_parameter** können Sie die Überwachungs Einstellungen angeben. Die folgenden Abschnitte führen Sie durch den Vorgang zum Aktivieren erweiterter Ereignisse und zum Aktivieren von E-Mail-Benachrichtigungen bei Fehlern und Warnungen.  
  
 Die **smart_admin. fn_get_parameter** -Funktion kann verwendet werden, um die aktuelle Einstellung für einen bestimmten Parameter oder alle konfigurierten Parameter zu erhalten. Wenn die Parameter nicht konfiguriert wurden, gibt die Funktion keine Werte zurück.  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie dann auf **Ausführen**. Dadurch wird die aktuelle Konfiguration für erweiterte Ereignisse und E-Mail-Benachrichtigungen zurückgegeben.  
  
```  
Use msdb  
Go  
SELECT * FROM smart_admin.fn_get_parameter (NULL)  
GO  
```  
  
 Weitere Informationen finden Sie unter [smart_admin. fn_get_parameter &#40;Transact-SQL&#41; ](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)  
  
### <a name="extended-events-for-monitoring"></a>Erweiterte Ereignisse für die Überwachung  
 Standardmäßig sind Admin-, Operational- und Analytical-Ereignisse aktiviert. Admin-Ereignisse sind am wichtigsten und hilfreich für die Ermittlung von Fehlern, die zur Behebung des Problems manuelle Eingriffe erfordern. Sie können die Operational- und Debug-Ereignisse aktivieren, Sie sollten aber bedenken, dass diese Ereignisse ausführlich sind und möglicherweise gefiltert werden müssen. Die folgenden Verfahren beschreiben, wie Sie über die erweiterten Ereignisse protokollierte Ereignisse überwachen können.  
  
> [!IMPORTANT]  
>  Im Gegensatz zu erweiterten Ereignissen für SQL Engine unterstützt [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] die Konzepte von Sitzungen für erweiterte Ereignisse nicht. Gespeicherte Systemprozeduren und -funktionen sind die Tools für die Interaktion mit erweiterten Ereignissen. Sie können das Protokoll für erweiterte Ereignisse im Protokollverzeichnis anzeigen.  
  
##### <a name="to-configure-and-view-extended-events"></a>So konfigurieren Sie erweiterte Ereignisse und zeigen sie an  
  
1.  Führen Sie die folgende Abfrage aus, um verfügbare Kanäle für erweiterte Ereignisse und ihren aktuellen Status anzuzeigen:  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     In der Ausgabe dieser Abfrage wird der event_name angezeigt und ob es konfiguriert werden kann und derzeit aktiviert ist.  Weitere Informationen finden Sie unter [smart_admin. fn_get_current_xevent_settings &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql).  
  
2.  Um Debug-Ereignisse zu aktivieren, führen Sie die folgende Abfrage aus:  
  
    ```  
    --  to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
     Weitere Informationen zur gespeicherten Prozedur finden Sie unter [smart_admin. sp_set_parameter &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql).  
  
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
 Die **smart_admin. fn_get_health_status** -Funktion gibt eine Tabelle mit aggregierten Fehler Zählungen für jede Kategorie zurück, die zum Überwachen des Integritäts Status von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]verwendet werden kann. Die gleiche Funktion verwendet auch der vom System konfigurierte E-Mail-Benachrichtigungsmechanismus, der weiter unten in diesem Thema beschrieben ist.   
Anhand dieser aggregierten Anzahl kann die Systemintegrität überwacht werden. Wenn beispielsweise die Spalte number_ of_retention_loops 0 in 30 Minuten ist, benötigt die Beibehaltungsverwaltung viel Zeit oder funktioniert nicht korrekt. Spalten mit Werten ungleich 0 können auf Probleme hindeuten. Sie sollten die Protokolle der erweiterten Ereignisse prüfen, um das Problem zu bestimmen. Rufen Sie alternativ die gespeicherte Prozedur **smart_admin. sp_get_backup_diagnostics** auf, um die Details des Fehlers zu ermitteln.  
  
### <a name="using-agent-notification-for-assessing-backup-status-and-health"></a>Verwenden von Agent-Benachrichtigungen zum Bewerten von Sicherungsstatus und -integrität  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verfügt über einen Benachrichtigungsmechanismus, der auf Verwaltungsrichtlinien auf Grundlage von SQL Server-Richtlinien beruht.  
  
 **Voraussetzungen:**  
  
-   Datenbank-E-Mail ist erforderlich, um diese Funktionen verwenden zu können. Weitere Informationen zum Aktivieren von DB-e-Mail für die Instanz von SQL Server finden Sie unter [configure Datenbank-E-Mail](../relational-databases/database-mail/configure-database-mail.md).  
  
-   Die Eigenschaften des SQL Server-Agent-Warnsystems sollten für die Verwendung der Datenbank-E-Mail festgelegt werden.  
  
 **Benachrichtigungs Architektur:**  
  
-   **Richtlinien basierte Verwaltung:** Zwei Richtlinien werden zum Überwachen der Sicherungs Integrität festgelegt: **System Integritätsrichtlinie für intelligente Administratoren**und die Integritäts **Richtlinie "Smart Admin User Action**". Die Smart Admin-Richtlinie für die Systemintegrität wertet kritische Fehler wie fehlende oder ungültige SQL-Anmeldeinformationen oder Verbindungsfehler aus und meldet die Integrität des Systems. Bei diesen ist normalerweise ein manueller Eingriff erforderlich, um das zugrunde liegende Problem zu beheben. Die Smart Admin-Richtlinie für die Integrität von Benutzeraktionen wertet Warnungen aus, z. B. beschädigte Sicherungen.  Bei diesen ist möglicherweise keine Aktion erforderlich, sondern stellen lediglich eine Warnung zu einem Ereignis dar. Es wird erwartet, dass solche Probleme automatisch vom [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Agent behandelt werden.  
  
-   **SQL Server-Agent** Auftrag Die Benachrichtigung wird mithilfe eines SQL Server-Agent Auftrags ausgeführt, der drei Auftrags Schritte umfasst. Im ersten Auftragsschritt wird ermittelt, ob [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Datenbank oder eine Instanz konfiguriert ist. Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] aktiviert und konfiguriert vorgefunden wird, wird der zweite Schritt ausgeführt: Es wird ein PowerShell-Cmdlet ausgeführt, das den Integritätsstatus bewertet, indem die Verwaltungsrichtlinien auf Grundlage von SQL Server-Richtlinien ausgewertet werden. Wenn ein Fehler oder eine Warnung gefunden wird, tritt ein Fehler auf, der den dritten Schritt auslöst: Im dritten Schritt wird eine e-Mail-Benachrichtigung mit dem Fehler-/Warnungs-Bericht gesendet.  Dieser SQL Server-Agent-Auftrag ist jedoch nicht standardmäßig aktiviert. Verwenden Sie die gespeicherte System Prozedur **smart_admin. sp_set_backup_parameter** , um den e-Mail-Benachrichtigungs Auftrag zu aktivieren.  Das folgende Verfahren beschreibt diese Schritte ausführlicher:  
  
##### <a name="enabling-email-notification"></a>Aktivieren der E-Mail-Benachrichtigung  
  
1.  Wenn Datenbank-E-Mail nicht bereits konfiguriert ist, befolgen Sie die Schritte unter [Konfigurieren von Datenbank-E-Mail](../relational-databases/database-mail/configure-database-mail.md).  
  
2.  Datenbank als e-Mail-System für SQL Server Warnungs System festlegen: Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, wählen Sie Warnungs **System**aus, aktivieren Sie das Kontrollkästchen **Mail Profil aktivieren** , wählen Sie **Datenbank-E-Mail** als e- **Mail-System**aus, und wählen Sie ein zuvor  
  
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
 Das **Test-sqlsmartadmin-** Cmdlet kann zum Erstellen einer benutzerdefinierten Integritäts Überwachung verwendet werden. Beispielsweise kann die im vorhergehenden Abschnitt beschriebene Benachrichtigungsoption auf Instanzebene konfiguriert werden.  Wenn Sie mehrere SQL Server-Instanzen für die Verwendung von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] konfiguriert haben, können Sie mit dem PowerShell-Cmdlet Skripts erstellen, die den Status und die Integrität von Sicherungen für alle Instanzen erfassen.  
  
 Das **Test-sqlsmartadmin** -Cmdlet bewertet die Fehler und Warnungen, die von den SQL Server Richtlinien basierten Verwaltungsrichtlinien zurückgegeben werden, und meldet einen rollupstatus.  Dieses Cmdlet verwendet standardmäßig die Systemrichtlinien. Mit dem `-AllowUserPolicies`-Parameter können Sie beliebige benutzerdefinierte Richtlinien einschließen.  
  
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
 Einige Objekte werden installiert, um die Funktionalität zu implementieren. Diese Objekte sind für die interne Verwendung reserviert. Eine Systemtabelle kann jedoch bei der Überwachung des Sicherungsstatus von Nutzen sein: smart_backup_files. Die meisten der in dieser Tabelle gespeicherten Informationen, die sich auf die Überwachung wie den Sicherungstyp, den Datenbanknamen, die erste und die letzte LSN und die Daten der Sicherung beziehen, werden über die Systemfunktion [smart_admin. fn_available_backups &#40;&#41; Transact-SQL verfügbar gemacht. ](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql). Die Statusspalte in der smart_backup_files-Tabelle, die den Status der Sicherungsdatei angibt, ist bei Verwendung der Funktion jedoch nicht verfügbar. Mithilfe der folgenden Beispielabfrage können verschiedene Informationen, u. a. auch der Status, aus der Systemtabelle abgerufen werden:  
  
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
  
-   **Verfügbar-A:** Dies ist eine normale Sicherungsdatei. Die Sicherung wurde abgeschlossen und außerdem überprüft, ob Sie im Azure-Speicher verfügbar ist.  
  
-   **Kopieren in Bearbeitung: B:** Dieser Status gilt speziell für Verfügbarkeits Gruppen Datenbanken. Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] eine Unterbrechung in der Sicherungsprotokollkette feststellt, wird zunächst versucht, die Sicherung zu ermitteln, die die Unterbrechung in der Sicherungskette verursacht hat. Beim Suchen der Sicherungsdatei wird versucht, die Datei in Azure Storage zu kopieren. Dieser Status wird angezeigt, wenn der Kopiervorgang gerade ausgeführt wird.  
  
-   **Fehler beim Kopieren: F:** Ähnlich wie bei der laufenden Kopie handelt es sich hierbei um bestimmte t-Verfügbarkeits Gruppen Datenbanken. Wenn der Kopiervorgang fehlschlägt, lautet der Status F.  
  
-   **Beschädigt-C:** Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] die Sicherungsdatei im Speicher durch Ausführen eines Restore HEADER_ONLY-Befehls nicht überprüfen kann, selbst nach mehreren versuchen, wird diese Datei als beschädigt markiert. Damit die beschädigte Datei keine Unterbrechung in der Sicherungskette verursacht, wird von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] eine Sicherung geplant.  
  
-   **Gelöscht-D:** Die entsprechende Datei wurde im Azure-Speicher nicht gefunden. Wenn die gelöschte Datei eine Unterbrechung in der Sicherungskette verursacht, wird von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] eine Sicherung geplant.  
  
-   **Unbekannt-U:** Dieser Status gibt an [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] , dass noch nicht in der Lage war, das vorhanden sein von Dateien und deren Eigenschaften im Azure-Speicher zu überprüfen. Wenn der Prozess zum nächsten Mal ausgeführt wird, d. h. alle 15 Minuten, wird dieser Status aktualisiert.  
  
  
