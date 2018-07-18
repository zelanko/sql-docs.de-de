---
title: Problembehandlung bei SQLServer Managed Backup für Windows Azure | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a34d35b0-48eb-4ed1-9f19-ea14754650da
caps.latest.revision: 18
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fd751224b24583cf5426194d7b4fc5074349bdfd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306149"
---
# <a name="troubleshooting-sql-server-managed--backup-to-windows-azure"></a>Problembehandlung bei SQLServer Managed Backup für Windows Azure
  Dieses Thema enthält zudem Informationen zu den Aufgaben und Tools, die Sie verwenden können, um Fehler bei [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Vorgängen zu beheben.  
  
## <a name="overview"></a>Übersicht  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verfügt über integrierte Prüfungen und Fehlerbehebungen, d. h., in vielen Fällen kümmert sich der [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Prozess selbst um interne Fehler.  
  
 Ein Beispiel für einen solchen Fall ist ein Löschen einer Sicherungsdatei mit dem Ergebnis einer Unterbrechung in der Protokollkette, was die Wiederherstellbarkeit beeinträchtigt – [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] identifiziert die Unterbrechung in der Protokollkette und plant eine sofort auszuführende Sicherung. Nichtsdestotrotz sollten Sie den Status überwachen und mögliche Fehler, die ein manuelles Eingreifen erfordern, entsprechend behandeln.  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] protokolliert Ereignisse und Fehler anhand gespeicherter Systemprozeduren, Systemsichten und erweiterter Ereignisse. Systemsichten und gespeicherte Prozeduren stellen [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Konfigurationsinformationen, Status von geplanten Sicherungen sowie Fehler bereit, die von erweiterten Ereignissen aufgezeichnet wurden. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verwendet erweiterte Ereignisse zur Aufzeichnung von Fehlern für die Fehlerbehebung. Zusätzlich zur Ereignisprotokollierung stellen die intelligenten Administrations-Richtlinien von SQL Server einen Integritätsstatus bereit, der von einem E-Mail-Benachrichtigungs-Auftrag zur Bereitstellung von Benachrichtigungen zu Fehlern und Problemen verwendet wird. Weitere Informationen finden Sie unter [Monitor SQL Server Managed Backup für Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verwendet dieselbe Protokollierung, die verwendet wird, wenn der Windows Azure-Speicher (SQL Server-URL-Sicherung) manuell gesichert wird. Weitere Informationen zum URL-Sicherung zu verwandten Problemen finden Sie im Abschnitt zur Problembehandlung in [SQL Server Backup to URL Best Practices und Problembehandlung](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
### <a name="general-troubleshooting-steps"></a>Allgemeine Schritte zur Problembehandlung  
  
1.  Aktivieren Sie die E-Mail-Benachrichtigung, um E-Mails zu Fehlern und Warnungen zu erhalten.  
  
     Alternativ können Sie auch `smart_admin.fn_get_health_status` regelmäßig ausführen, um die aggregierten Fehler und Zahlen zu überprüfen. Zum Beispiel gibt `number_of_invalid_credential_errors` an, wie häufig die intelligente Sicherung eine Sicherung versucht, aber einen Fehler aufgrund ungültiger Anmeldeinformationen erhalten hat. `Number_of_backup_loops` und `number_of_retention_loops` sind keine Fehler; sie geben an, wie häufig Sicherungsthread und Beibehaltungsthread die Liste der Datenbanken überprüft haben. In der Regel, wenn @begin_time und @end_time sind nicht angegeben wird, wird die Funktion die Informationen aus den letzten 30 Minuten nicht angezeigt wird, sollten wir normalerweise Werte ungleich NULL für diese beiden Spalten angezeigt. Wenn sie null sind, weist dies auf eine Systemüberlastung oder sogar auf ein nicht reagierendes System hin. Weitere Informationen finden Sie unter **Behandlung von Systemproblemen** weiter unten in diesem Thema.  
  
2.  Prüfen Sie die Protokolle der erweiterten Ereignisse, um weitere Details zu den Fehlern und zu den zugehörigen Ereignissen zu erfahren.  
  
3.  Anhand der Informationen in den Protokollen sollten Sie das Problem lösen können.  Bei einem Systemproblem oder -fehler müssen Sie den Dienst oder SQL Server-Agent möglicherweise neu starten.  
  
### <a name="common-causes-of-errors"></a>Häufige Fehlerursachen  
 Es folgt eine Liste häufiger Ursachen von Fehlern:  
  
1.  **Änderungen an den SQL-Anmeldeinformationen:** , wenn der Name der Anmeldeinformationen von verwendet [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] geändert oder gelöscht wird, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ist nicht möglich, Sicherungen zu erstellen. Die Änderung sollte auf die [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]-Konfigurationseinstellungen angewendet werden.  
  
2.  **Änderungen an den Speicherzugriff-Schlüsselwerten:** Wenn der Speicher-Schlüsselwerte für das Windows Azure-Konto geändert werden, aber SQL-Anmeldeinformationen wird nicht mit den neuen Werten aktualisiert [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] schlägt fehl, wenn in den Speicher, Authentifizierung und ein Fehler auftritt, für die Sicherung Datenbanken, die so konfiguriert, dass dieses Konto verwenden.  
  
3.  **Änderungen an Windows Azure Storage-Konto:** löschen oder Umbenennen des Speicherkontos ohne entsprechende Änderung der SQL-Anmeldeinformationen führt [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] fehlschlägt und keine Sicherungen vorgenommen werden. Wenn Sie ein Speicherkonto löschen, müssen Sie sicherstellen, dass die Datenbanken mit gültigen Speicherkontoinformationen neu konfiguriert werden. Wenn ein Speicherkonto umbenannt oder die Schlüsselwerte geändert werden, stellen Sie sicher, dass diese Änderungen sich entsprechend in den von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] verwendeten SQL-Anmeldeinformationen widerspiegeln.  
  
4.  **Änderungen an Datenbankeigenschaften:** Änderungen an Wiederherstellungsmodellen oder Ändern des Namens kann dazu führen, dass Sicherungen fehlschlagen.  
  
5.  **Änderungen an Wiederherstellungsmodell:** , wenn das Wiederherstellungsmodell der Datenbank von der vollständigen oder massenprotokollierten einfach geändert wird, Sicherungen angehalten und die Datenbanken übersprungen werden, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Weitere Informationen finden Sie unter [SQL Server Managed Backup für Windows Azure: Interoperabilität und Koexistenz](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
### <a name="most-common-error-messages-and-solutions"></a>Häufigste Fehlermeldungen und Lösungen  
  
1.  **Fehler beim Aktivieren oder Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]:**  
  
     Fehler: "Fehler beim Zugriff auf Speicher-URL .... Geben Sie gültige SQL-Anmeldeinformationen..." : Sie können diese und andere ähnliche Fehler werden auf der SQL-Anmeldeinformationen finden Sie unter.  Prüfen Sie in solchen Fällen den Namen der von Ihnen bereitgestellten Anmeldeinformationen sowie die in den SQL-Anmeldeinformationen gespeicherten Informationen wie den Speicherkontonamen und den Speicherzugriffsschlüssel, und stellen Sie sicher, dass die Werte aktuell und gültig sind.  
  
     Fehler: "... Konfigurieren Sie die Datenbank... nicht möglich, da es sich um eine Systemdatenbank handelt": Dieser Fehler wird angezeigt, wenn Sie versuchen, aktivieren Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Systemdatenbank.  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] unterstützt keine Sicherungen von Systemdatenbanken.  Um die Sicherung einer Systemdatenbank zu konfigurieren, verwenden Sie andere SQL Server-Sicherungstechnologien, z. B. Wartungspläne.  
  
     Fehler: "... Geben Sie eine Beibehaltungsdauer..." : Sie können Fehler für den Beibehaltungszeitraum angezeigt, wenn Sie entweder nicht einen Aufbewahrungszeitraum für die Datenbank oder Instanz angegeben haben, wenn Sie diese Werte zum ersten Mal konfigurieren. Es wird außerdem ein Fehler angezeigt, wenn Sie einen anderen Wert als eine Zahl zwischen 1 und 30 angeben. Der zulässige Wert für die Beibehaltungsdauer ist eine Zahl zwischen 1 und 30.  
  
2.  **E-Mail-Benachrichtigungsfehler:**  
  
     Fehler: "Database Mail ist nicht aktiviert..." – Sie werden dieser Fehler angezeigt, wenn Sie die e-Mail-Benachrichtigungen aktivieren, aber Database Mail ist für die Instanz nicht konfiguriert. Sie müssen Datenbank-E-Mail für die Instanz konfigurieren, um Benachrichtigungen zum Integritätsstatus von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] empfangen zu können. Informationen zum Aktivieren von Datenbank-e-Mails finden Sie unter [Konfigurieren von Datenbank-e-Mails](../relational-databases/database-mail/configure-database-mail.md). Sie müssen außerdem den SQL Server-Agent aktivieren, um Datenbank-E-Mail für Benachrichtigungen verwenden zu können. Weitere Informationen finden Sie unter [Vorbemerkungen](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md#BeforeYouBegin).  
  
     Es folgt eine Liste der Fehlernummern, die möglicherweise angezeigt werden und die E-Mail-Benachrichtigungen zugeordnet sind:  
  
    -   Fehlernummer: 45209  
  
    -   Fehlernummer: 45210  
  
    -   Fehlernummer: 45211  
  
3.  **Verbindungsfehler:**  
  
    -   **Fehler im Zusammenhang mit SQL-Konnektivität:** diese Fehler treten auf, wenn eine Verbindung mit SQL Server-Instanz Probleme vorliegen. Dieser Fehlertyp wird durch erweiterte Ereignisse über den Adminkanal verfügbar gemacht. Die folgenden beiden erweiterten Ereignisse können bei Fehlern im Zusammenhang mit dieser Art von Verbindungsproblemen auftreten:  
  
         FileRetentionAdminXEvent mit event_type = SqlError. Ausführliche Informationen zu diesem Fehler finden Sie im Ereignis unter error_code, error_message und stack_trace. error_code entspricht der SqlException-Fehlernummer.  
  
         SmartBackupAdminXevent mit folgenden Meldungspräfixen:  
  
         *"Interner Fehler beim Konfigurieren von SQL Server Managed Backup auf Windows Azure-Standardeinstellungen für die Instanz. Fehler kann vorübergehend sein."*  
  
         *"Wahrscheinlich Verbindungsprobleme mit SQL Server. Datenbank wird in der aktuellen Iteration übersprungen."*  
  
         *"Fehler zur Protokollverwendung Abfragen. Der Fehler ist möglicherweise vorübergehend. Datenbank wird in der aktuellen Iteration übersprungen."*  
  
         *"SQL-Ausnahme beim Laden von SSMBackup2WA-Agent-Metadaten. Der Fehler ist möglicherweise vorübergehend. Der Vorgang wird wiederholt."*  
  
         *"SSMBackup2WA gefunden SQL-Ausnahme beim... "*  
  
    -   **Fehler bei der eine Verbindung mit dem Speicherkonto:**  
  
         Speicherausnahmen werden in FileRetentionAdminXEvent mit event_type = XstoreError angegeben. Ausführliche Informationen zum Fehler finden Sie im Ereignis unter error_message und stack_trace.  
  
         Da SQL Server Managed Backup die zugrunde liegende URL-Sicherungstechnologie nutzt, beziehen sich die Fehler zu Speicherverbindungen auf beide Funktionen. Weitere Informationen mit Schritten zur Problembehandlung finden Sie unter **Abschnitt zur Problembehandlung** von der [SQL Server Backup to URL Best Practices and Troubleshooting](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md) Artikel.  
  
### <a name="troubleshooting-system-issues"></a>Behandlung von Systemproblemen  
 Es folgen einige Szenarien, wenn es ein Problem mit dem System (SQL Server, SQL Server-Agent) und den Auswirkungen auf [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] gibt:  
  
-   **Sqlservr.exe reagiert nicht mehr oder funktioniert nicht bei [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ausgeführt wird:** Wenn SQL Server nicht mehr funktioniert, SQL Agent ordnungsgemäß heruntergefahren, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] beendet und die Ereignisse werden auch in der Datei SQL Agent.out protokolliert.  
  
     Wenn SQL Server nicht mehr reagiert, werden Ereignisse im Adminkanal protokolliert.  Ein Beispiel für das Ereignisprotokoll:  
  
     *SQL-Fehler (engine reagiert nicht oder get SqlException: SqlException:*   
     *Fehlercode, Nachrichten und stapelüberwachung werden in einem Xevent, zusammen mit zusätzlichen Informationen, wie z. B. angezeigt:*   
    *"Wahrscheinlich Verbindungsprobleme mit SQL Server. Datenbank wird in der aktuellen Iteration übersprungen"*  
  
-   **SQL-Agent reagiert nicht mehr oder funktioniert nicht bei [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ausgeführt wird:**  
  
     Wenn SQL Agent nicht mehr funktioniert, wird auch [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] angehalten, und Ereignisse werden im Adminkanal protokolliert. Dies ist Szenarien ähnlich, in denen SQL Server nicht mehr reagiert.  
  
     Wenn SQL Agent nicht mehr reagiert, kann [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] die Sicherungsvorgänge nicht mehr fortsetzen, und Ereignisse werden im Adminkanal protokolliert. Ein Beispiel für das Ereignisprotokoll:  
  
     *Auftrag hängt: finden Sie unter adminkanal-Xevents*   
    *"Ein StatusUpdate noch nicht empfangen wurden, von SQL Server in mehr als" + Constants.DBBackupInfoMsgMaxWaitTime + "Stunden für die datenbanksicherung.   SSM-Cloud-Sicherung wird weiter ausgesetzt."*  
  
 Wenn Sie e-Mail-Benachrichtigungen aktiviert haben, erhalten Sie eine Benachrichtigung, die **Anzahl der Sicherungsschleifen** und **Anzahl der Beibehaltungsschleifen**. Wenn der Wert, der in der Benachrichtigung für eine oder beide Spalten zurückgegeben wird, null ist, kann dies ein Hinweis darauf sein, dass das System nicht reagiert.  
  
> [!WARNING]  
>  Bei den internen Prozessen, durch die die Ergebnisse für den Bericht generiert werden, wird davon ausgegangen, dass sich die Diagnoseprotokolle der Engine am selben Speicherort wie das SQL Agent-Fehlerprotokoll befinden, das standardmäßig im selben Ordner wie die Fehlerprotokolle der SQL Server-Instanz gespeichert wird. Wenn die Diagnoseprotokolle der Engine an einen anderen Speicherort als den des SQL Agent-Fehlerprotokolls verschoben werden, ist das System nicht in der Lage, die Diagnoseprotokolle für intelligente Sicherungen zu finden, sodass der Bericht in der E-Mail-Benachrichtigung u. U. fehlerhaft ist. Beispielsweise sehen Sie möglicherweise einen Wert von **0** in allen Feldern gemeldet, einschließlich der Anzahl der Sicherungsschleifen und die Anzahl der Beibehaltungsschleifen. Wenn die Diagnoseprotokolle also an einen anderen Speicherort verschoben werden, bedeutet dies nicht, dass das System nicht reagiert, sondern dass es nicht in der Lage ist, die Protokolle zu finden. Stellen Sie zunächst sicher, dass sich die Diagnoseprotokolle und SQL Agent-Fehlerprotokolle am selben Speicherort befinden. Um den aktuellen Speicherort für die Diagnoseprotokolle zu überprüfen, können Sie [dm_os_server_diagnostics_log_configurations](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-server-diagnostics-log-configurations). Die `path` Spalte gibt die aktuelle Position der Engine Diagnoseprotokolle zurück.  Es muss sich im selben Ordner wie die SQL-Agent-Fehlerprotokolle. Der Pfad der SQL Agent-Fehlerprotokolle kann mithilfe der gespeicherten Prozedur `dbo.sp_get_sqlagent_properties` abgerufen werden.  
  
 Überprüfen Sie die Protokolle mit erweiterten Ereignisses, um Details zu den Fehlern anzuzeigen. Beheben Sie die Fehler oder starten Sie den SQL Server-Agent neu, um die Situation zu korrigieren.  
  
  
