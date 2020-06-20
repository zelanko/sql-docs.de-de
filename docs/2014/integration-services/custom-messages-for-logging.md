---
title: Benutzerdefinierte Meldungen für die Protokollierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], custom
- writing log entries
- SSIS packages, logs
- custom messages for logging [Integration Services]
ms.assetid: 3c74bba9-02b7-4bf5-bad5-19278b680730
author: janinezhang
ms.author: janinez
ms.openlocfilehash: a7fe7d714d93915814b6658409a9f892c28e03b7
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84917150"
---
# <a name="custom-messages-for-logging"></a>Benutzerdefinierte Meldungen für die Protokollierung
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stellt einen umfangreichen Satz an benutzerdefinierten Ereignissen zum Schreiben von Protokolleinträgen für Pakete und für mehrere Tasks bereit. Sie können diese Einträge verwenden, um detaillierte Informationen zum Fortschritt sowie über die Ergebnisse und Probleme der Ausführung zu speichern, indem Sie vordefinierte Ereignisse bzw. benutzerdefinierte Meldungen für die spätere Analyse erfassen. Sie können beispielsweise Beginn und Ende eines Masseneinfügungsvorgangs erfassen, um Leistungsprobleme beim Ausführen des Pakets zu identifizieren.  
  
 Die benutzerdefinierten Protokolleinträge unterscheiden sich von den für Pakete und alle Container und Tasks verfügbaren Standardprotokollierungsereignissen. Die benutzerdefinierten Protokolleinträge dienen zum Erfassen nützlicher Informationen zu einem bestimmten Task eines Pakets. Beispielsweise zeichnet einer der benutzerdefinierten Protokolleinträge für den Task SQL ausführen die von dem Task ausgeführte SQL-Anweisung im Protokoll auf.  
  
 In allen Protokolleinträgen sind jeweils das Datum und die Uhrzeit enthalten, einschließlich der beim Beginnen und Beenden eines Pakets automatisch geschriebenen Protokolleinträge. Bei vielen Protokollereignissen werden mehrere Einträge in das Protokoll geschrieben. In der Regel tritt dies dann auf, wenn ein Ereignis verschiedene Phasen aufweist. Beispielsweise schreibt das `ExecuteSQLExecutingQuery`-Protokollereignis drei Einträge: einen Eintrag, nachdem der Task eine Verbindung mit der Datenbank erhalten hat; einen weiteren, nachdem der Task begonnen hat, die SQL-Anweisung vorzubereiten; und noch einen, nachdem die Ausführung der SQL-Anweisung abgeschlossen wurde.  
  
 Die folgenden [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Objekte verfügen über benutzerdefinierte Protokolleinträge:  
  
 [Pakete](#Package)  
  
 [Masseneinfügungstask](#BulkInsert)  
  
 [Datenflusstask](#DataFlow)  
  
 [DTS 2000-Aufgabe ausführen](#ExecuteDTS200)  
  
 [Prozess ausführen (Task)](#ExecuteProcess)  
  
 [SQL ausführen (Task)](#ExecuteSQL)  
  
 [Task „Dateisystem“](#FileSystem)  
  
 [FTP-Task](#FTP)  
  
 [Nachrichtenwarteschlange (Task)](#MessageQueue)  
  
 [Skripttask](#Script)  
  
 [Mail senden (Task)](#SendMail)  
  
 [Datenbanken übertragen (Task)](#TransferDatabase)  
  
 [Fehlermeldungen übertragen (Task)](#TransferErrorMessages)  
  
 [Aufträge übertragen (Task)](#TransferJobs)  
  
 [Task „Anmeldungen übertragen“](#TransferLogins)  
  
 [In master gespeicherte Prozeduren übertragen (Task)](#TransferMasterStoredProcedures)  
  
 [SQL Server-Objekte kopieren (Task)](#TransferSQLServerObjects)  
  
 [Webdienst (Task)](#WebServices)  
  
 [WMI-Datenleser (Task)](#WMIDataReader)  
  
 [WMI-Ereignisüberwachung (Task)](#WMIEventWatcher)  
  
 [XML-Task](#XML)  
  
## <a name="log-entries"></a>Protokolleinträge  
  
###  <a name="package"></a><a name="Package"></a>Paketen  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für Pakete aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`PackageStart`|Zeigt den Beginn der Paketausführung an.<br /><br /> Hinweis: Dieser Protokolleintrag wird automatisch in das Protokoll geschrieben. Dieser Eintrag kann nicht ausgeschlossen werden.|  
|`PackageEnd`|Zeigt den Abschluss der Paketausführung an.<br /><br /> Hinweis: Dieser Protokolleintrag wird automatisch in das Protokoll geschrieben. Dieser Eintrag kann nicht ausgeschlossen werden.|  
|`Diagnostic`|Enthält Informationen zur Systemkonfiguration, die sich auf die Paketausführung auswirken, wie z. B. die Anzahl ausführbarer Dateien, die gleichzeitig ausgeführt werden können.<br /><br /> Der Protokolleintrag `Diagnostic` enthält auch vorherige und nachfolgende Einträge für Aufrufe von externen Datenanbietern. Weitere Informationen finden Sie unter [Troubleshooting Tools Package Connectivity](troubleshooting/troubleshooting-tools-for-package-connectivity.md).|  
  
###  <a name="bulk-insert-task"></a><a name="BulkInsert"></a>Massen Einfügungs Task  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Masseneinfügungstask aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`DTSBulkInsertTaskBegin`|Zeigt den Beginn der Masseneinfügung an.|  
|`DTSBulkInsertTaskEnd`|Zeigt die Fertigstellung der Masseneinfügung an.|  
|`DTSBulkInsertTaskInfos`|Enthält beschreibende Informationen zum Task.|  
  
###  <a name="data-flow-task"></a><a name="DataFlow"></a>Datenfluss Task  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Datenflusstask aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`BufferSizeTuning`|Zeigt an, dass der Datenflusstask die Größe des Puffers geändert hat. Der Protokolleintrag beschreibt die Gründe für die Größenänderung und listet die temporäre neue Puffergröße auf.|  
|`OnPipelinePostEndOfRowset`|Gibt an, dass eine Komponente das Signal für das Ende des Rowsets erhalten hat. Dieses Signal wird durch den letzten Aufruf der `ProcessInput`-Methode festgelegt. Für jede Komponente im Datenfluss, die eine Eingabe verarbeitet, wird ein Eintrag geschrieben. Der Eintrag schließt den Namen der Komponente ein.|  
|`OnPipelinePostPrimeOutput`|Zeigt an, dass die Komponente ihren letzten Aufruf der `PrimeOutput`-Methode abgeschlossen hat. Je nach Datenfluss werden möglicherweise mehrere Protokolleinträge geschrieben. Wenn es sich bei der Komponente um eine Quelle handelt, bedeutet das, dass die von der Komponente durchgeführte Zeilenverarbeitung fertig gestellt wurde.|  
|`OnPipelinePreEndOfRowset`|Zeigt an, dass eine Komponente das Signal für das Ende des Rowsets erhalten soll. Dieses Signal wird durch den letzten Aufruf der `ProcessInput`-Methode festgelegt. Für jede Komponente im Datenfluss, die eine Eingabe verarbeitet, wird ein Eintrag geschrieben. Der Eintrag schließt den Namen der Komponente ein.|  
|`OnPipelinePrePrimeOutput`|Zeigt an, dass die Komponente einen Aufruf aus der `PrimeOutput`-Methode erhalten soll. Je nach Datenfluss werden möglicherweise mehrere Protokolleinträge geschrieben.|  
|`OnPipelineRowsSent`|Berichtet die Anzahl von Zeilen, die einer Komponenteneingabe durch einen Aufruf der `ProcessInput`-Methode bereitgestellt wurden. Der Protokolleintrag enthält den Komponentennamen.|  
|`PipelineBufferLeak`|Stellt Informationen zu Komponenten bereit, die Puffer aufrechterhalten haben, nachdem der Puffer-Manager beendet wurde. Das bedeutet, dass Pufferressourcen nicht freigegeben wurden, was zu Speicherverlusten führen kann. Der Protokolleintrag stellt den Namen der Komponente und die ID des Puffers bereit.|  
|`PipelineExecutionPlan`|Berichtet den Ausführungsplan des Datenflusses. Es werden Informationen darüber bereitgestellt, wie Puffer an Komponenten gesendet werden. Diese Informationen in Verbindung mit dem PipelineExecutionTrees-Eintrag beschreiben, was in dem Task geschieht.|  
|`PipelineExecutionTrees`|Berichtet die Ausführungsstrukturen des Layouts im Datenfluss. Der Planer der Datenfluss-Engine verwendet die Strukturen zum Erstellen des Datenflussplans.|  
|`PipelineInitialization`|Bietet Initialisierungsinformationen zu dem Task. Zu diesen Informationen gehören die Verzeichnisse für die temporäre Speicherung von BLOB-Daten, die Standardpuffergröße und die Zeilenanzahl in einem Puffer. Je nach der Konfiguration des Datenflusstasks werden möglicherweise mehrere Protokolleinträge geschrieben.|  
  
###  <a name="execute-dts-2000-task"></a><a name="ExecuteDTS200"></a> DTS 2000 ausführen (Task)  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Task DTS 2000 ausführen aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`ExecuteDTS80PackageTaskBegin`|Zeigt an, dass die Ausführung eines DTS 2000-Pakets über den Task gestartet wurde.|  
|`ExecuteDTS80PackageTaskEnd`|Zeigt an, dass die Ausführung über den Task beendet wurde.<br /><br /> Hinweis: Das DTS 2000-Paket kann nach Beendigung des Tasks mit der Ausführung fortfahren.|  
|`ExecuteDTS80PackageTaskTaskInfo`|Enthält beschreibende Informationen zum Task.|  
|`ExecuteDTS80PackageTaskTaskResult`|Berichtet das Ausführungsergebnis des durch den Task ausgeführten DTS 2000-Pakets.|  
  
###  <a name="execute-process-task"></a><a name="ExecuteProcess"></a>Prozess ausführen (Task)  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Task Prozess ausführen aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`ExecuteProcessExecutingProcess`|Enthält Informationen zum Ausführprozess der zur Ausführung konfigurierten ausführbaren Datei.<br /><br /> Es werden zwei Protokolleinträge geschrieben. Der eine Protokolleintrag enthält Informationen über den Namen und Speicherort der vom Task ausgeführten ausführbaren Datei, im anderen Eintrag wird das Beenden der ausführbaren Datei erfasst.|  
|`ExecuteProcessVariableRouting`|Enthält Informationen darüber, welche Variablen an die Eingabe und an die Ausgaben der ausführbaren Datei geleitet werden. Es werden Protokolleinträge für stdin (für die Eingabe), für stdout (für die Ausgabe) und für stderr (für die Fehlerausgabe) geschrieben.|  
  
###  <a name="execute-sql-task"></a><a name="ExecuteSQL"></a>SQL ausführen (Task)  
 In der folgenden Tabelle wird der benutzerdefinierte Protokolleintrag für den Task <legacyBold>SQL ausführen</legacyBold> beschrieben.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`ExecuteSQLExecutingQuery`|Enthält Informationen zu den Ausführungsphasen der SQL-Anweisung. Protokolleinträge werden geschrieben, wenn der Task eine Verbindung mit der Datenbank erhält, wenn der Task beginnt, die SQL-Anweisung vorzubereiten, und nachdem die Ausführung der SQL-Anweisung abgeschlossen wurde. Der Protokolleintrag für die Vorbereitungsphase schließt die vom Task verwendete SQL-Anweisung ein.|  
  
###  <a name="file-system-task"></a><a name="FileSystem"></a>Task "Datei System"  
 In der folgenden Tabelle wird der benutzerdefinierte Protokolleintrag für den Task "Dateisystem" beschrieben.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`FileSystemOperation`|Berichtet den vom Task durchgeführten Vorgang. Der Protokolleintrag wird geschrieben, wenn der Dateisystemvorgang begonnen wird, und schließt Informationen über die Quelle und das Ziel ein.|  
  
###  <a name="ftp-task"></a><a name="FTP"></a>FTP-Task  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den FTP-Task aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`FTPConnectingToServer`|Zeigt an, dass mit dem Task eine Verbindung zum FTP-Server initiiert wurde.|  
|`FTPOperation`|Berichtet den Beginn und Typ des vom Task ausgeführten FTP-Vorgangs.|  
  
###  <a name="message-queue-task"></a><a name="MessageQueue"></a>Message Queue-Task  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Task Nachrichtenwarteschlange aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`MSMQAfterOpen`|Zeigt an, dass das Öffnen der Warteschlange beendet wurde.|  
|`MSMQBeforeOpen`|Zeigt an, dass das Öffnen der Warteschlange begonnen wurde.|  
|`MSMQBeginReceive`|Zeigt an, dass das Empfangen einer Meldung begonnen wurde.|  
|`MSMQBeginSend`|Zeigt an, dass das Senden einer Meldung begonnen wurde.|  
|`MSMQEndReceive`|Zeigt an, dass das Empfangen einer Meldung beendet wurde.|  
|`MSMQEndSend`|Zeigt an, dass das Senden einer Meldung beendet wurde.|  
|`MSMQTaskInfo`|Enthält beschreibende Informationen zum Task.|  
|`MSMQTaskTimeOut`|Zeigt an, dass beim Task ein Timeout eingetreten ist.|  
  
###  <a name="script-task"></a><a name="Script"></a>Skript Task  
 In der folgenden Tabelle wird der benutzerdefinierte Protokolleintrag für den Skripttask beschrieben.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`ScriptTaskLogEntry`|Gibt die Ergebnisse des Implementierens der Protokollierung innerhalb des Skripts an. Für jeden Aufruf der `Log`-Methode des `Dts`-Objekts wird jeweils ein Protokolleintrag geschrieben. Der Eintrag wird beim Ausführen des Codes geschrieben. Weitere Informationen finden Sie unter [Logging in the Script Task](extending-packages-scripting/task/logging-in-the-script-task.md).|  
  
###  <a name="send-mail-task"></a><a name="SendMail"></a>Task ' Mail senden '  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Task 'Mail senden' aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`SendMailTaskBegin`|Zeigt an, dass das Senden einer E-Mail-Nachricht begonnen wurde.|  
|`SendMailTaskEnd`|Zeigt an, dass das Senden einer E-Mail-Nachricht beendet wurde.|  
|`SendMailTaskInfo`|Enthält beschreibende Informationen zum Task.|  
  
###  <a name="transfer-database-task"></a><a name="TransferDatabase"></a>Daten Bank Task übertragen  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Task Datenbanken übertragen aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`SourceDB`|Gibt die vom Task kopierte Datenbank an.|  
|`SourceSQLServer`|Gibt den Computer an, von dem die Datenbank kopiert wurde.|  
  
###  <a name="transfer-error-messages-task"></a><a name="TransferErrorMessages"></a>Task "Fehlermeldungen übertragen"  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Task Fehlermeldungen übertragen aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`TransferErrorMessagesTaskFinishedTransferringObjects`|Zeigt an, dass das Übertragen von Fehlermeldungen beendet wurde.|  
|`TransferErrorMessagesTaskStartTransferringObjects`|Zeigt an, dass das Übertragen von Fehlermeldungen gestartet wurde.|  
  
###  <a name="transfer-jobs-task"></a><a name="TransferJobs"></a>Task Aufträge übertragen  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Task Aufträge übertragen aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`TransferJobsTaskFinishedTransferringObjects`|Zeigt an, dass das Übertragen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Aufträgen beendet wurde.|  
|`TransferJobsTaskStartTransferringObjects`|Zeigt an, dass das Übertragen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Aufträgen gestartet wurde.|  
  
###  <a name="transfer-logins-task"></a><a name="TransferLogins"></a>Task "Anmeldungen übertragen"  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Task Anmeldungen übertragen aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`TransferLoginsTaskFinishedTransferringObjects`|Zeigt an, dass das Übertragen von Anmeldungen beendet wurde.|  
|`TransferLoginsTaskStartTransferringObjects`|Zeigt an, dass das Übertragen von Anmeldungen gestartet wurde.|  
  
###  <a name="transfer-master-stored-procedures-task"></a><a name="TransferMasterStoredProcedures"></a>Task ' Master ' gespeicherte Prozeduren  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Task In master gespeicherte Prozeduren übertragen aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`TransferStoredProceduresTaskFinishedTransferringObjects`|Zeigt an, dass das Übertragen von benutzerdefinierten gespeicherten Prozeduren, die in der **master** -Datenbank gespeichert sind, beendet wurde.|  
|`TransferStoredProceduresTaskStartTransferringObjects`|Zeigt an, dass das Übertragen von benutzerdefinierten gespeicherten Prozeduren, die in der **master** -Datenbank gespeichert sind, gestartet wurde.|  
  
###  <a name="transfer-sql-server-objects-task"></a><a name="TransferSQLServerObjects"></a>SQL Server Objekte übertragen (Task)  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Task [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Objekte kopieren aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`TransferSqlServerObjectsTaskFinishedTransferringObjects`|Zeigt an, dass das Übertragen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbankobjekten beendet wurde.|  
|`TransferSqlServerObjectsTaskStartTransferringObjects`|Zeigt an, dass das Übertragen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbankobjekten gestartet wurde.|  
  
###  <a name="web-services-task"></a><a name="WebServices"></a> Webdienste (Task)  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge aufgelistet, die für den Task Webdienste aktiviert werden können.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`WSTaskBegin`|Der Zugriff auf einen Webdienst wurde begonnen.|  
|`WSTaskEnd`|Eine Webdienstmethode wurde beendet.|  
|`WSTaskInfo`|Beschreibende Informationen zum Task.|  
  
###  <a name="wmi-data-reader-task"></a><a name="WMIDataReader"></a>WMI-Daten Leser (Task)  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Task WMI-Datenleser aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`WMIDataReaderGettingWMIData`|Zeigt an, dass das Lesen der WMI-Daten begonnen wurde.|  
|`WMIDataReaderOperation`|Berichtet die vom Task ausgeführte WQL-Abfrage.|  
  
###  <a name="wmi-event-watcher-task"></a><a name="WMIEventWatcher"></a>Task "WMI-Ereignisüberwachung"  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Task WMI-Ereignisüberwachung aufgelistet.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`WMIEventWatcherEventOccurred`|Zeigt an, dass das vom Task überwachte Ereignis aufgetreten ist.|  
|`WMIEventWatcherTimedout`|Zeigt an, dass beim Task ein Timeout eingetreten ist.|  
|`WMIEventWatcherWatchingForWMIEvents`|Zeigt an, dass die Ausführung der WQL-Abfrage begonnen wurde. Der Eintrag schließt die Abfrage ein.|  
  
###  <a name="xml-task"></a><a name="XML"></a>XML-Task  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den XML-Task beschrieben.  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|`XMLOperation`|Stellt Informationen über den vom Task durchgeführten Vorgang bereit.|   
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Protokollierung &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
