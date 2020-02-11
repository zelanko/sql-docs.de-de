---
title: SQL Server Profiler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], about SQL Server Profiler
- traces [SQL Server], SQL Server Profiler
- database monitoring [SQL Server], SQL Server Profiler
- tuning databases [SQL Server], SQL Server Profiler
- SQL Server Profiler
- server performance [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler]
- tracing [SQL Server]
- monitoring performance [SQL Server], SQL Server Profiler
- events [SQL Server], SQL Server Profiler
- SQL Server Profiler, about SQL Server Profiler
- tools [SQL Server], SQL Server Profiler
- database performance [SQL Server], SQL Server Profiler
- trace [SQL Server]
ms.assetid: 3ad5f33d-559e-41a4-bde6-bb98792f7f1a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c9b0bb789dc7571a988c434f526070546d8db454
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211044"
---
# <a name="sql-server-profiler"></a>SQL Server Profiler
  
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ist eine funktionsreiche Benutzeroberfläche zum Erstellen und Verwalten von Ablaufverfolgungen sowie zum Analysieren und Wiedergeben von Ablaufverfolgungsergebnissen. Die Ereignisse werden in einer Ablaufverfolgungsdatei gespeichert, die später analysiert oder beim Versuch, ein Problem zu diagnostizieren, zur Wiedergabe einer bestimmten Reihe von Schritten verwendet werden kann.  
  
> [!IMPORTANT]  
>  Wir kündigen die Veraltung von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] für die [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Ablaufverfolgungssammlung und -Ablaufverfolgungswiedergabe an. Diese Funktionen werden in der nächsten Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]noch unterstützt, in zukünftigen Versionen jedoch entfernt. Die betreffende Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wurde noch nicht festgelegt. Der *Microsoft.SqlServer.Management.Trace* -Namespace, der die Objekte für die Microsoft SQL Server-Ablaufverfolgung und -Wiedergabe enthält, ist ebenfalls veraltet. Beachten Sie, dass [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] für die Analysis Services-Arbeitsauslastungen nicht veraltet ist und weiterhin unterstützt wird.  
>   
>  In der folgenden Tabelle werden die Funktionen angezeigt, deren Verwendung wir in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] empfehlen, um Ablaufverfolgungsdaten zu erfassen und wiederzugeben:  
  
||||  
|-|-|-|  
|**Feature\zielworkloads**|**Relationale Engine**|**Analysis Services**|  
|**Ablauf Verfolgungs Erfassung**|Grafische Benutzeroberfläche für erweiterte Ereignisse in SQL Server Management Studio|SQL Server Profiler|  
|**Ablauf Verfolgungs Wiedergabe**|Distributed Replay|SQL Server Profiler|  
  
## <a name="benefits-of-sql-server-profiler"></a>Vorteile von SQL Server Profiler  
 Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ist eine grafische Benutzeroberfläche für die SQL-Ablaufverfolgung zur Überwachung einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] oder Analysis Services. Daten über die einzelnen Ereignisse können aufgezeichnet und in einer Datei oder Tabelle zur späteren Analyse gespeichert werden. Beispielsweise können Sie eine Produktionsumgebung überwachen und feststellen, welche gespeicherten Prozeduren langsam ablaufen und dadurch die Leistung beeinträchtigen. 
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] wird beispielsweise für folgende Aktivitäten verwendet:  
  
-   Schrittweises Untersuchen problematischer Abfragen, um die Ursache des Problems zu ermitteln.  
  
-   Suchen und Diagnostizieren von Abfragen, die sehr langsam ausgeführt werden.  
  
-   Erfassen der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, die zu einem Problem geführt haben. Mithilfe der gespeicherten Ablaufverfolgung kann das Problem auf einem Testserver repliziert werden, um es dort zu diagnostizieren.  
  
-   Überwachen der Leistung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Optimierung der Arbeitsauslastung. Informationen zum Optimieren des physischen Datenbankentwurfs für Datenbankarbeitslasten finden Sie unter [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).  
  
-   Korrelieren von Leistungsindikatoren zur Diagnose von Problemen.  
  
 
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] unterstützt auch die Überwachung von Aktionen, die für Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt werden. Durch Überwachungen werden sicherheitsbezogene Aktionen aufgezeichnet, die später von einem Sicherheitsadministrator überprüft werden können.  
  
## <a name="sql-server-profiler-concepts"></a>SQL Server Profiler-Konzepte  
 Um [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]verwenden zu können, müssen Sie die Begriffe verstehen, mit denen die Funktionsweise des Tools beschrieben wird.  
  
> [!NOTE]  
>  Für die Arbeit mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]ist es hilfreich, die SQL-Ablaufverfolgung zu verstehen. Weitere Informationen finden Sie unter [SQL Trace](../../relational-databases/sql-trace/sql-trace.md).  
  
 **Ereignis**  
 Ein Ereignis ist eine Aktion, die innerhalb einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]generiert wird. Im Folgenden sind Beispiele dafür aufgeführt:  
  
-   Anmeldeverbindungen, fehlgeschlagene und getrennte Verbindungen.  
  
-   Die Transact-SQL-Anweisungen SELECT, INSERT, UPDATE und DELETE.  
  
-   Der Status von RPC-Batches (Remote Procedure Call, Remoteprozeduraufruf).  
  
-   Der Start oder das Ende einer gespeicherten Prozedur.  
  
-   Der Start oder das Ende von Anweisungen innerhalb gespeicherter Prozeduren.  
  
-   Der Start oder das Ende eines SQL-Batches.  
  
-   Ein Fehler, der in das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll geschrieben wird.  
  
-   Eine Sperre, die für ein Datenbankobjekt eingerichtet oder aufgehoben wird.  
  
-   Ein geöffneter Cursor.  
  
-   Überprüfungen der Sicherheitsberechtigungen.  
  
 Die gesamten von einem Ereignis generierten Daten werden in der Ablaufverfolgung in einer einzelnen Zeile angezeigt. Diese Zeile wird von Datenspalten unterbrochen, die Details zu den Ereignissen enthält.  
  
 **EventClass**  
 Eine Ereignisklasse ist ein Ereignistyp, dessen Ablauf verfolgt werden kann. Die Ereignisklasse enthält alle Daten, die von einem Ereignis berichtet werden können. Im Folgenden sind Beispiele für Ereignisklassen aufgeführt:  
  
-   **SQL: batchabgeschlossene**  
  
-   **Audit Login**  
  
-   **Audit Logout**  
  
-   **Sperre: abgerufen**  
  
-   **Sperre: freigegeben**  
  
 **EventCategory**  
 Eine Ereigniskategorie bestimmt, wie Ereignisse innerhalb von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]zusammengefasst werden. So sind beispielsweise alle Sperrereignisklassen in der Ereigniskategorie **Sperren** zusammengefasst. Ereigniskategorien sind jedoch nur in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]vorhanden. Dieser Begriff drückt nicht aus, wie Engine-Ereignisse gruppiert werden.  
  
 **DataColumn**  
 Eine Datenspalte ist ein Attribut einer Ereignisklasse, die in der Ablaufverfolgung erfasst ist. Da von der Ereignisklasse der Typ der Daten festgelegt wird, die gesammelt werden können, gelten nicht alle Datenspalten für alle Ereignisklassen. In einer Ablaufverfolgung, in der die **Lock:Acquired** -Ereignisklasse erfasst wird, enthält die **BinaryData** -Datenspalte beispielsweise den Wert der gesperrten Seiten-ID oder der Zeile, aber die **Integer Data** -Datenspalte enthält keine Werte, weil sie nicht auf die erfasste Ereignisklasse anwendbar ist.  
  
 **Fungiert**  
 Eine Vorlage definiert die Standardkonfiguration für eine Ablaufverfolgung. Dazu gehören insbesondere die Ereignisklassen, die mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]überwacht werden sollen. Sie können beispielsweise eine Vorlage erstellen, mit der die zu verwendenden Ereignisse, Datenspalten und Filter angegeben werden. Eine Vorlage wird nicht ausgeführt, sondern als Datei mit der Erweiterung TDF gespeichert. Nach dem Speichern steuert die Vorlage die Ablaufverfolgungsdaten, die beim Starten einer auf der Vorlage basierenden Ablaufverfolgung erfasst werden.  
  
 **Ablauf Verfolgungs**  
 Eine Ablaufverfolgung zeichnet Daten auf der Grundlage der ausgewählten Ereignisklassen, Datenspalten und Filter auf. Sie können beispielsweise eine Ablaufverfolgung erstellen, um Ausnahmefehler aufzuzeichnen. Wählen Sie dazu die **Exception** -Ereignisklasse und die Datenspalten **Fehler**, **Status**und **Schweregrad** aus. Daten aus diesen drei Spalten müssen gesammelt werden, damit die Ablaufverfolgung sinnvolle Daten als Ergebnis liefert. Sie können dann eine solcherart konfigurierte Ablaufverfolgung ausführen und Daten aufgrund aller **Exception** -Ereignisse sammeln, die auf dem Server auftreten. Ablaufverfolgungsdaten können gespeichert oder sofort für Analysezwecke verwendet werden. Ablaufverfolgungen können zu einem späteren Zeitpunkt wiedergegeben werden, obwohl bestimmte Ereignisse wie **Exception** -Ereignisse nie wiedergegeben werden. Sie können die Ablaufverfolgung als Vorlage speichern, um in Zukunft ähnliche Ablaufverfolgungen zu erstellen.  
  
 SQL Server bietet zwei Möglichkeiten für die Ablaufverfolgung einer Instanz von SQL Server: [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] und gespeicherte Systemprozeduren.  
  
 **Filter**  
 Beim Erstellen einer Ablaufverfolgung oder Vorlage können Sie Kriterien definieren, um die von dem Ereignis gesammelten Daten zu filtern. Damit Ablaufverfolgungen nicht zu groß werden, können Sie sie filtern, sodass nur eine Teilmenge der Ereignisdaten gesammelt wird. Sie können beispielsweise die Microsoft Windows-Benutzernamen in der Ablaufverfolgung auf bestimmte Benutzer beschränken, wodurch die Ausgabedatenmenge kleiner wird.  
  
 Ist kein Filter eingerichtet, werden alle Ereignisse der ausgewählten Ereignisklassen in der Ablaufverfolgungsausgabe zurückgegeben.  
  
## <a name="sql-server-profiler-tasks"></a>SQL Server Profiler-Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Listet die vordefinierten Vorlagen, die SQL Server zum Überwachen bestimmter Ereignistypen bereitstellt, und die zum Wiedergeben von Ablaufverfolgungen erforderlichen Berechtigungen auf.|[Vorlagen und Berechtigungen in SQL Server Profiler](sql-server-profiler-templates-and-permissions.md)|  
|Beschreibt, wie SQL Server Profiler ausgeführt wird.|[Erforderliche Berechtigungen zum Ausführen von SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md)|  
|Beschreibt, wie eine Ablaufverfolgung erstellt wird.|[Erstellen einer Ablaufverfolgung &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md)|  
|Beschreibt, wie Ereignisse und Datenspalten für eine Ablaufverfolgungsdatei angegeben werden.|[Angeben von Ereignissen und Datenspalten für eine Ablauf Verfolgungs Datei &#40;SQL Server Profiler&#41;](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)|  
|Beschreibt, wie Ablaufverfolgungsergebnisse in einer Datei gespeichert werden.|[Speichert Ablauf Verfolgungs Ergebnisse in einer Datei &#40;SQL Server Profiler&#41;](save-trace-results-to-a-file-sql-server-profiler.md)|  
|Beschreibt, wie Ablaufverfolgungsergebnisse in einer Tabelle gespeichert werden.|[Speichern von Ablauf Verfolgungs Ergebnissen in einer Tabelle &#40;SQL Server Profiler&#41;](save-trace-results-to-a-table-sql-server-profiler.md)|  
|Beschreibt, wie Ereignisse in einer Ablaufverfolgung gefiltert werden.|[Filtern von Ereignissen in einer Ablaufverfolgung &#40;SQL Server Profiler&#41;](filter-events-in-a-trace-sql-server-profiler.md)|  
|Beschreibt, wie Filterinformationen angezeigt werden.|[Filter Informationen &#40;SQL Server Profiler anzeigen&#41;](view-filter-information-sql-server-profiler.md)|  
|Beschreibt, wie ein Filter geändert wird.|[Ändern eines Filters &#40;SQL Server Profiler&#41;](modify-a-filter-sql-server-profiler.md)|  
|Beschreibt, wie eine maximale Dateigröße für eine Ablaufverfolgungsdatei (SQL Server Profiler) festgelegt wird.|[Festlegen einer maximalen Dateigröße für eine Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)|  
|Beschreibt, wie eine maximale Tabellengröße für eine Ablaufverfolgungstabelle festgelegt wird.|[Festlegen der maximalen Tabellengröße für eine Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)|  
|Beschreibt, wie eine Ablaufverfolgung gestartet wird.|[Starten einer Ablaufverfolgung](start-a-trace.md)|  
|Beschreibt, wie eine Ablaufverfolgung nach dem Herstellen einer Verbindung mit einem Server automatisch gestartet wird.|[Automatisches Starten einer Ablaufverfolgung nach dem Herstellen einer Verbindung mit einem Server &#40;SQL Server Profiler&#41;](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)|  
|Beschreibt, wie Ereignisse basierend auf der Ereignisstartzeit gefiltert werden.|[Ereignisse basierend auf der Ereignis Start Zeit &#40;SQL Server Profiler Filtern&#41;](filter-events-based-on-the-event-start-time-sql-server-profiler.md)|  
|Beschreibt, wie Ereignisse basierend auf der Ereignisendzeit gefiltert werden.|[Filtern von Ereignissen anhand der Ereignisendzeit &#40;SQL Server Profiler&#41;](filter-events-based-on-the-event-end-time-sql-server-profiler.md)|  
|Beschreibt, wie Serverprozess-IDs (SPIDs) in einer Ablaufverfolgung gefiltert werden.|[Filtert Server-Prozess-IDs &#40;SPIDs&#41; in einer Ablauf Verfolgungs &#40;SQL Server Profiler&#41;](filter-server-process-ids-spids-in-a-trace-sql-server-profiler.md)|  
|Beschreibt, wie eine Ablaufverfolgung angehalten wird.|[Anhalten einer Ablaufverfolgung &#40;SQL Server Profiler&#41;](pause-a-trace-sql-server-profiler.md)|  
|Beschreibt, wie eine Ablaufverfolgung beendet wird.|[Beenden einer Ablaufverfolgung &#40;SQL Server Profiler&#41;](stop-a-trace-sql-server-profiler.md)|  
|Beschreibt, wie eine Ablaufverfolgung ausgeführt wird, nachdem sie angehalten oder beendet wurde.|[Ausführen einer Ablaufverfolgung, nachdem sie angehalten oder beendet wurde &#40;SQL Server Profiler&#41;](run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)|  
|Beschreibt, wie ein Ablaufverfolgungsfenster gelöscht wird.|[Löschen des Inhalts eines Ablaufverfolgungsfensters &#40;SQL Server Profiler&#41;](clear-a-trace-window-sql-server-profiler.md)|  
|Beschreibt, wie ein Ablaufverfolgungsfenster geschlossen wird.|[Schließen Sie ein Ablauf Verfolgungs Fenster &#40;SQL Server Profiler&#41;](close-a-trace-window-sql-server-profiler.md)|  
|Beschreibt, wie Standardeinstellungen für Ablaufverfolgungsdefinitionen festgelegt werden.|[Standardeinstellungen für Ablauf Verfolgungs Definitionen festlegen &#40;SQL Server Profiler&#41;](set-trace-definition-defaults-sql-server-profiler.md)|  
|Beschreibt, wie Standardeinstellungen für die Ablaufverfolgungsanzeige festgelegt werden.|[Festlegen der Standardeinstellungen für die Ablaufverfolgungsanzeige &#40;SQL Server Profiler&#41;](set-trace-display-defaults-sql-server-profiler.md)|  
|Beschreibt, wie eine Ablaufverfolgungsdatei geöffnet wird.|[Öffnen einer Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md)|  
|Beschreibt, wie eine Ablaufverfolgungstabelle geöffnet wird.|[Öffnen einer Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)|  
|Beschreibt, wie eine Ablaufverfolgungstabelle wiedergegeben wird.|[Wiedergeben einer Ablauf Verfolgungs Tabelle &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md)|  
|Beschreibt, wie eine Ablaufverfolgungsdatei wiedergegeben wird.|[Wiedergeben einer Ablauf Verfolgungs Datei &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md)|  
|Beschreibt, wie jeweils ein einzelnes Ereignis wiedergegeben wird.|[Wiedergeben eines einzelnen Ereignisses zu einem Zeitpunkt &#40;SQL Server Profiler&#41;](replay-a-single-event-at-a-time-sql-server-profiler.md)|  
|Beschreibt die Wiedergabe bis zu einem Breakpoint.|[Wiedergeben bis zu einem Breakpoint &#40;SQL Server Profiler&#41;](replay-to-a-breakpoint-sql-server-profiler.md)|  
|Beschreibt die Wiedergabe bis zu einer Cursorposition.|[Wiedergeben bis zu einer Cursorposition &#40;SQL Server Profiler&#41;](replay-to-a-cursor-sql-server-profiler.md)|  
|Beschreibt, wie ein Transact-SQL-Skript wiedergegeben wird.|[Wiedergeben eines Transact-SQL-Skripts &#40;SQL Server Profiler&#41;](replay-a-transact-sql-script-sql-server-profiler.md)|  
|Beschreibt, wie eine Ablaufverfolgungsvorlage erstellt wird.|[Erstellen einer Ablaufverfolgungsvorlage &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md)|  
|Beschreibt, wie eine Ablaufverfolgungsvorlage geändert wird.|[Modify a Trace Template &#40;SQL Server Profiler&#41; (Ändern einer Ablaufverfolgungsvorlage &#40;SQL Server Profiler&#41)](../../database-engine/modify-a-trace-template-sql-server-profiler.md)|  
|Beschreibt, wie globale Ablaufverfolgungsoptionen festgelegt werden.|[Festlegen globaler Ablauf Verfolgungs Optionen &#40;SQL Server Profiler&#41;](set-global-trace-options-sql-server-profiler.md)|  
|Beschreibt, wie ein Wert oder eine Datenspalte während der Ablaufverfolgung gesucht wird.|[Suchen eines Werts oder einer Datenspalte während der Ablauf Verfolgung &#40;SQL Server Profiler&#41;](find-a-value-or-data-column-while-tracing-sql-server-profiler.md)|  
|Beschreibt, wie eine Vorlage aus einer ausgeführten Ablaufverfolgung abgeleitet wird.|[Ableiten einer Vorlage von einer zurzeit ausgeführten Ablaufverfolgung &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md)|  
|Beschreibt, wie eine Vorlage aus einer Ablaufverfolgungsdatei oder Ablaufverfolgungstabelle abgeleitet wird.|[Ableiten einer Vorlage von einer Ablaufverfolgungsdatei oder Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)|  
|Beschreibt, wie ein Transact-SQL-Skript für das Ausführen einer Ablaufverfolgung erstellt wird.|[Erstellen eines Transact-SQL-Skripts zum Ausführen einer Ablauf Verfolgung &#40;SQL Server Profiler&#41;](create-a-transact-sql-script-for-running-a-trace-sql-server-profiler.md)|  
|Beschreibt, wie eine Ablaufverfolgungsvorlage exportiert wird.|[Exportieren einer Ablaufverfolgungsvorlage &#40;SQL Server Profiler&#41;](export-a-trace-template-sql-server-profiler.md)|  
|Beschreibt, wie eine Ablaufverfolgungsvorlage importiert wird.|[Importieren einer Ablauf Verfolgungs Vorlage &#40;SQL Server Profiler&#41;](import-a-trace-template-sql-server-profiler.md)|  
|Beschreibt, wie ein Skript aus einer Ablaufverfolgung extrahiert wird.|[Extrahieren eines Skripts aus einer Ablauf Verfolgung &#40;SQL Server Profiler&#41;](extract-a-script-from-a-trace-sql-server-profiler.md)|  
|Beschreibt, wie eine Ablaufverfolgung mit Windows-Leistungsprotokolldaten korreliert wird.|[Korrelieren einer Ablauf Verfolgung mit Windows-Leistungs Protokolldaten &#40;SQL Server Profiler&#41;](../../database-engine/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)|  
|Beschreibt, wie in einer Ablaufverfolgung angezeigte Spalten organisiert werden.|[Organisieren der in einer Ablauf Verfolgung angezeigten Spalten &#40;SQL Server Profiler&#41;](organize-columns-displayed-in-a-trace-sql-server-profiler.md)|  
|Beschreibt, wie SQL Server Profiler gestartet wird.|[Starten von SQL Server Profiler](start-sql-server-profiler.md)|  
|Beschreibt, wie Ablaufverfolgungen und Ablaufverfolgungsvorlagen gespeichert werden.|[Speichern von Ablaufverfolgungen und Ablaufverfolgungsvorlagen](save-traces-and-trace-templates.md)|  
|Beschreibt, wie Ablaufverfolgungsvorlagen geändert werden.|[Ändern von Ablauf Verfolgungs Vorlagen](modify-trace-templates.md)|  
|Beschreibt, wie eine Ablaufverfolgung mit Windows-Leistungsprotokolldaten korreliert wird.|[Korrelieren einer Ablaufverfolgung mit Windows-Leistungsprotokolldaten](correlate-a-trace-with-windows-performance-log-data.md)|  
|Beschreibt, wie Ablaufverfolgungen mit SQL Server Profiler angezeigt und analysiert werden.|[Anzeigen und Analysieren von Ablaufverfolgungen mit SQL Server Profiler](view-and-analyze-traces-with-sql-server-profiler.md)|  
|Beschreibt, wie Deadlocks mit SQL Server Profiler analysiert werden.|[Analysieren von Deadlocks mit SQL Server Profiler](analyze-deadlocks-with-sql-server-profiler.md)|  
|Beschreibt, wie Abfragen mit SHOWPLAN-Ergebnissen in SQL Server Profiler analysiert werden.|[Analysieren von Abfragen mit SHOWPLAN-Ergebnissen in SQL Server Profiler](analyze-queries-with-showplan-results-in-sql-server-profiler.md)|  
|Beschreibt, wie Ablaufverfolgungen mit SQL Server Profiler gefiltert werden.|[Filtern von Ablaufverfolgungen mit SQL Server Profiler](filter-traces-with-sql-server-profiler.md)|  
|Beschreibt, wie die Wiedergabefunktionen von SQL Server Profiler verwendet werden.|[Wiedergeben von Ablaufverfolgungen](replay-traces.md)|  
|Listet die kontextbezogenen Hilfethemen für SQL Server Profiler auf.|[SQL Server Profiler (F1-Hilfe)](sql-server-profiler-f1-help.md)|  
|Listet die von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zur Leistungs- und Aktivitätsüberwachung verwendeten gespeicherten Systemprozeduren auf.|[Gespeicherte Prozeduren von SQL Server Profiler &#40;SQL Server Profiler&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sperren (Ereignis Kategorie)](../../relational-databases/event-classes/locks-event-category.md)   
 [Sitzungen (Ereignis Kategorie)](../../relational-databases/event-classes/sessions-event-category.md)   
 [Gespeicherte Prozeduren-Ereignis Kategorie](../../relational-databases/event-classes/stored-procedures-event-category.md)   
 [Ereignis Kategorie "t-QL"](../../relational-databases/event-classes/tsql-event-category.md)   
 [Überwachen der Serverleistung und -aktivität](../../relational-databases/performance/server-performance-and-activity-monitoring.md)  
  
  
