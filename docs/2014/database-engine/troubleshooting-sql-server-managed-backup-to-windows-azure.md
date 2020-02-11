---
title: Problembehandlung SQL Server Managed Backup in Azure | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: a34d35b0-48eb-4ed1-9f19-ea14754650da
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 385fa6f6bd874734207c6fec10ddc687b951825a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "76929435"
---
# <a name="troubleshooting-sql-server-managed--backup-to-azure"></a>Problembehandlung für die verwaltete SQL Server-Sicherung in Azure
  Dieses Thema enthält zudem Informationen zu den Aufgaben und Tools, die Sie verwenden können, um Fehler bei [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Vorgängen zu beheben.  
  
## <a name="overview"></a>Übersicht  
 
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verfügt über integrierte Prüfungen und Fehlerbehebungen, d. h., in vielen Fällen kümmert sich der [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Prozess selbst um interne Fehler.  
  
 Ein Beispiel für einen solchen Fall ist das Löschen einer Sicherungsdatei, die zu einer Unterbrechung der Protokoll Kette führt, die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] die Wiederherstellbarkeit beeinträchtigt. in wird die Unterbrechung in der Protokoll Kette identifiziert und eine sofortige Sicherung geplant. Nichtsdestotrotz sollten Sie den Status überwachen und mögliche Fehler, die ein manuelles Eingreifen erfordern, entsprechend behandeln.  
  
 
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] protokolliert Ereignisse und Fehler anhand gespeicherter Systemprozeduren, Systemsichten und erweiterter Ereignisse. Systemsichten und gespeicherte Prozeduren stellen [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Konfigurationsinformationen, Status von geplanten Sicherungen sowie Fehler bereit, die von erweiterten Ereignissen aufgezeichnet wurden. 
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verwendet erweiterte Ereignisse zur Aufzeichnung von Fehlern für die Fehlerbehebung. Zusätzlich zur Ereignisprotokollierung stellen die intelligenten Administrations-Richtlinien von SQL Server einen Integritätsstatus bereit, der von einem E-Mail-Benachrichtigungs-Auftrag zur Bereitstellung von Benachrichtigungen zu Fehlern und Problemen verwendet wird. Weitere Informationen finden [Sie unter Überwachen SQL Server verwalteten Sicherung in Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]verwendet auch die gleiche Protokollierung, die beim manuellen Sichern in Azure Storage (SQL Server Sicherung auf URL) verwendet wird. Weitere Informationen zu Problemen bei der Sicherung auf URL finden Sie im Abschnitt zur Problembehandlung unter [SQL Server bewährte Methoden und Problem](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md) Behandlung bei der Sicherung von URLs.  
  
### <a name="general-troubleshooting-steps"></a>Allgemeine Schritte zur Problembehandlung  
  
1.  Aktivieren Sie die E-Mail-Benachrichtigung, um E-Mails zu Fehlern und Warnungen zu erhalten.  
  
     Alternativ können Sie auch `smart_admin.fn_get_health_status` regelmäßig ausführen, um die aggregierten Fehler und Zahlen zu überprüfen. Zum Beispiel gibt `number_of_invalid_credential_errors` an, wie häufig die intelligente Sicherung eine Sicherung versucht, aber einen Fehler aufgrund ungültiger Anmeldeinformationen erhalten hat. 
  `Number_of_backup_loops` und `number_of_retention_loops` sind keine Fehler; sie geben an, wie häufig Sicherungsthread und Beibehaltungsthread die Liste der Datenbanken überprüft haben. Wenn @begin_time und @end_time nicht bereitgestellt werden, zeigt die Funktion in der Regel die Informationen in den letzten 30 Minuten an. für diese beiden Spalten sollten normalerweise Werte ungleich Null angezeigt werden. Wenn sie null sind, weist dies auf eine Systemüberlastung oder sogar auf ein nicht reagierendes System hin. Weitere Informationen finden Sie im Abschnitt Problembehandlung bei **System Problemen** weiter unten in diesem Thema.  
  
2.  Prüfen Sie die Protokolle der erweiterten Ereignisse, um weitere Details zu den Fehlern und zu den zugehörigen Ereignissen zu erfahren.  
  
3.  Anhand der Informationen in den Protokollen sollten Sie das Problem lösen können.  Bei einem Systemproblem oder -fehler müssen Sie den Dienst oder SQL Server-Agent möglicherweise neu starten.  
  
### <a name="common-causes-of-errors"></a>Häufige Fehlerursachen  
 Es folgt eine Liste häufiger Ursachen von Fehlern:  
  
1.  **Änderungen an den SQL** -Anmelde Informationen: Wenn der Name der von verwendeten Anmelde Informationen geändert [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] wird oder gelöscht wird, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] kann keine Sicherungen durchführen. Die Änderung sollte auf die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Konfigurationseinstellungen angewendet werden.  
  
2.  **Änderungen an Speicherzugriffs Schlüssel-Werten:** Wenn die Speicher Schlüsselwerte für das Azure-Konto geändert werden, die SQL-Anmelde Informationen jedoch nicht mit den neuen Werten [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] aktualisiert werden, schlägt bei der Authentifizierung beim Speicher fehl, und es werden keine Datenbanken gesichert, die für die Verwendung dieses Kontos konfiguriert sind.  
  
3.  **Änderungen an Azure Storage Konto:** Das Löschen oder Umbenennen des Speicher Kontos ohne entsprechende Änderungen an den SQL- [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Anmelde Informationen führt dazu, dass fehlschlägt und keine Sicherungen erstellt werden. Wenn Sie ein Speicherkonto löschen, müssen Sie sicherstellen, dass die Datenbanken mit gültigen Speicherkontoinformationen neu konfiguriert werden. Wenn ein Speicherkonto umbenannt oder die Schlüsselwerte geändert werden, stellen Sie sicher, dass diese Änderungen sich entsprechend in den von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verwendeten SQL-Anmeldeinformationen widerspiegeln.  
  
4.  **Änderungen an Daten Bank Eigenschaften:** Änderungen an Wiederherstellungs Modellen oder eine Änderung des Namens können dazu führen, dass Sicherungen fehlschlagen.  
  
5.  **Änderungen am Wiederherstellungs Modell:** Wenn das Wiederherstellungs Modell der Datenbank von vollständig oder Massen protokolliert in einfach geändert wird, werden die Sicherungen angehalten, und die Datenbanken werden von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]übersprungen. Weitere Informationen finden Sie unter [SQL Server verwaltete Sicherung in Azure: Interoperabilität und Koexistenz](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
### <a name="most-common-error-messages-and-solutions"></a>Häufigste Fehlermeldungen und Lösungen  
  
1.  **Fehler beim Aktivieren oder konfigurieren [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]von:**  
  
     Fehler: "Fehler beim Zugriff auf die Speicher-URL.... Geben Sie gültige SQL-Anmelde Informationen an... ": möglicherweise werden diese und andere ähnliche Fehler angezeigt, die sich auf die SQL-Anmelde Informationen beziehen.  Überprüfen Sie in diesen Fällen den Namen der angegebenen SQL-Anmelde Informationen sowie die in den SQL-Anmelde Informationen gespeicherten Informationen, den Speicherkonto Namen und den Speicherzugriffs Schlüssel, und stellen Sie sicher, dass Sie aktuell und gültig sind.  
  
     Fehler: "... die Datenbank kann nicht konfiguriert werden... Da es sich um eine Systemdatenbank handelt ": dieser Fehler wird angezeigt, wenn Sie versuchen [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] , für eine Systemdatenbank zu aktivieren.  
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] unterstützt keine Sicherungen von Systemdatenbanken.  Um die Sicherung einer Systemdatenbank zu konfigurieren, verwenden Sie andere SQL Server-Sicherungstechnologien, z. B. Wartungspläne.  
  
     Fehler: "... Geben Sie eine Beibehaltungs Dauer an.... ": möglicherweise werden Fehler bezüglich der Beibehaltungs Dauer angezeigt, wenn Sie für die Datenbank oder Instanz bei der erstmaligen Konfiguration dieser Werte keine Beibehaltungs Dauer angegeben haben. Es wird außerdem ein Fehler angezeigt, wenn Sie einen anderen Wert als eine Zahl zwischen 1 und 30 angeben. Der zulässige Wert für die Beibehaltungsdauer ist eine Zahl zwischen 1 und 30.  
  
2.  **E-Mail-Benachrichtigungsfehler:**  
  
     Fehler: "Datenbank-E-Mail ist nicht aktiviert...". dieser Fehler wird angezeigt, wenn Sie e-Mail-Benachrichtigungen aktivieren, aber Datenbank-E-Mail ist für die Instanz nicht konfiguriert. Sie müssen Datenbank-E-Mail für die Instanz konfigurieren, um Benachrichtigungen zum Integritätsstatus von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] empfangen zu können. Informationen zum Aktivieren von Datenbank-e-Mail finden Sie unter [Konfigurieren von Datenbank-E-Mail](../relational-databases/database-mail/configure-database-mail.md). Sie müssen außerdem den SQL Server-Agent aktivieren, um Datenbank-E-Mail für Benachrichtigungen verwenden zu können. Weitere Informationen finden [Sie](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md#BeforeYouBegin)unter Vorbereitung.  
  
     Es folgt eine Liste der Fehlernummern, die möglicherweise angezeigt werden und die E-Mail-Benachrichtigungen zugeordnet sind:  
  
    -   ErrorNumber: 45209  
  
    -   ErrorNumber: 45210  
  
    -   Fehlernummer: 45211  
  
3.  **Verbindungsfehler:**  
  
    -   **Fehler im Zusammenhang mit der SQL-Konnektivität:** Diese Fehler treten auf, wenn Probleme beim Herstellen einer Verbindung mit SQL Server-Instanz auftreten. Dieser Fehlertyp wird durch erweiterte Ereignisse über den Adminkanal verfügbar gemacht. Die folgenden beiden erweiterten Ereignisse können bei Fehlern im Zusammenhang mit dieser Art von Verbindungsproblemen auftreten:  
  
         FileRetentionAdminXEvent mit event_type = SqlError. Ausführliche Informationen zu diesem Fehler finden Sie im Ereignis unter error_code, error_message und stack_trace. Der error_code ist die Fehlernummer der SqlException.  
  
         SmartBackupAdminXevent mit folgenden Meldungspräfixen:  
  
         *"Interner Fehler beim Konfigurieren SQL Server Managed Backup in Azure-Standardeinstellungen. Der Fehler ist möglicherweise vorübergehend. "*  
  
         *"Wahrscheinlich treten Verbindungsprobleme mit SQL Server auf. Die Datenbank wird in der aktuellen Iterations Datenbank übersprungen. "*  
  
         *"Fehler beim Abfragen der Protokoll Verwendungs Informationen. Der Fehler ist möglicherweise vorübergehend. Die Datenbank wird in der aktuellen Iterations Datenbank übersprungen. "*  
  
         *"SQL-Ausnahme beim Laden von SSMBackup2WA-Agent-Metadaten. Der Fehler ist möglicherweise vorübergehend. Der Vorgang wird wiederholt. "*  
  
         *"SSMBackup2WA hat eine SQL-Ausnahme gefunden, während... "*  
  
    -   **Fehler bei Verbindungen mit dem Speicherkonto:**  
  
         Speicherausnahmen werden in FileRetentionAdminXEvent mit event_type = XstoreError angegeben. Ausführliche Informationen zum Fehler finden Sie im Ereignis unter error_message und stack_trace.  
  
         Da SQL Server Managed Backup die zugrunde liegende URL-Sicherungstechnologie nutzt, beziehen sich die Fehler zu Speicherverbindungen auf beide Funktionen. Weitere Informationen zu Problem Behandlungsschritten finden Sie im **Abschnitt "Problem** Behandlung" im Artikel [bewährte Methoden und Problembehandlung bei der SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md) .  
  
### <a name="troubleshooting-system-issues"></a>Behandlung von Systemproblemen  
 Es folgen einige Szenarien, wenn es ein Problem mit dem System (SQL Server, SQL Server-Agent) und den Auswirkungen auf [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] gibt:  
  
-   **"Sqlservr. exe" reagiert nicht mehr oder [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] funktioniert nicht mehr, wenn ausgeführt wird:** wenn SQL Server nicht mehr funktioniert, wird der [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] SQL-Agent ordnungsgemäß heruntergefahren, und die Ereignisse werden in der Datei "SQL Agent. out" protokolliert.  
  
     Wenn SQL Server nicht mehr reagiert, werden Ereignisse im Adminkanal protokolliert.  Ein Beispiel für das Ereignisprotokoll:  
  
     *SQL-Fehler (Engine antwortet nicht oder SqlException: SqlException: SqlException:*   
     *Fehlercode, Message und StackTrace werden in einem Admin Channel-XEvent angezeigt, sowie einige zusätzliche Informationen, wie z. b.:*   
    *"Wahrscheinlich treten Verbindungsprobleme mit SQL Server auf. Die Datenbank wird in der aktuellen Iterations Datenbank übersprungen.*  
  
-   **Der SQL-Agent reagiert nicht mehr oder [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] funktioniert nicht mehr, wenn ausgeführt wird:**  
  
     Wenn SQL Agent nicht mehr funktioniert, wird auch [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] angehalten, und Ereignisse werden im Adminkanal protokolliert. Dies ist Szenarien ähnlich, in denen SQL Server nicht mehr reagiert.  
  
     Wenn SQL Agent nicht mehr reagiert, kann [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] die Sicherungsvorgänge nicht mehr fortsetzen, und Ereignisse werden im Adminkanal protokolliert. Ein Beispiel für das Ereignisprotokoll:  
  
     *Auftrags hängen: siehe admin Channel xevents*   
    *"Es wurde kein Fortschrittsupdate von SQL Server in mehr als" + Konstanten. dbbackupinfomsgmaxwaittime + "Stunden für die Datenbanksicherung empfangen.   SSM-cloudsicherung wird weiterhin gewartet. "*  
  
 Wenn Sie e-Mail-Benachrichtigungen aktiviert haben, erhalten Sie eine Benachrichtigung, die die **Anzahl der Sicherungs Schleifen** und die **Anzahl der Beibehaltungs Schleifen**umfasst. Wenn der Wert, der in der Benachrichtigung für eine oder beide Spalten zurückgegeben wird, null ist, kann dies ein Hinweis darauf sein, dass das System nicht reagiert.  
  
> [!WARNING]  
>  Bei den internen Prozessen, durch die die Ergebnisse für den Bericht generiert werden, wird davon ausgegangen, dass sich die Diagnoseprotokolle der Engine am selben Speicherort wie das SQL Agent-Fehlerprotokoll befinden, das standardmäßig im selben Ordner wie die Fehlerprotokolle der SQL Server-Instanz gespeichert wird. Wenn die Diagnoseprotokolle der Engine an einen anderen Speicherort als den des SQL Agent-Fehlerprotokolls verschoben werden, ist das System nicht in der Lage, die Diagnoseprotokolle für intelligente Sicherungen zu finden, sodass der Bericht in der E-Mail-Benachrichtigung u. U. fehlerhaft ist. Beispielsweise kann in allen gemeldeten Feldern der Wert **0** (null) angezeigt werden, einschließlich der Anzahl der Sicherungs Schleifen und der Anzahl der Beibehaltungs Schleifen. Wenn die Diagnoseprotokolle also an einen anderen Speicherort verschoben werden, bedeutet dies nicht, dass das System nicht reagiert, sondern dass es nicht in der Lage ist, die Protokolle zu finden. Stellen Sie zunächst sicher, dass sich die Diagnoseprotokolle und SQL Agent-Fehlerprotokolle am selben Speicherort befinden. Um den aktuellen Speicherort der Diagnoseprotokolle zu überprüfen, können Sie [sys. dm_os_server_diagnostics_log_configurations](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-server-diagnostics-log-configurations)verwenden. Die `path` -Spalte gibt den aktuellen Speicherort der Diagnoseprotokolle der Engine zurück.  Er sollte sich im gleichen Ordner befinden wie die SQL Agent-Fehlerprotokolle. Der Pfad der SQL Agent-Fehlerprotokolle kann mithilfe der gespeicherten Prozedur `dbo.sp_get_sqlagent_properties` abgerufen werden.  
  
 Überprüfen Sie die Protokolle mit erweiterten Ereignisses, um Details zu den Fehlern anzuzeigen. Beheben Sie die Fehler oder starten Sie den SQL Server-Agent neu, um die Situation zu korrigieren.  
  
  
