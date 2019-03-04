---
title: Versionsanmerkungen zu SQL Server 2016|Microsoft-Dokumente
ms.date: 04/25/2018
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- build notes
- release issues
ms.assetid: c64077a2-bec8-4c87-9def-3dbfb1ea1fb6
author: craigg-msft
ms.author: craigg
manager: jhubbard
monikerRange: = sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 3e06d2f4bacffb1334724c3d7f936e051009ad04
ms.sourcegitcommit: c3b190f8f87a4c80bc9126bb244896197a6dc453
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56852945"
---
# <a name="sql-server-2016-release-notes"></a>Versionsanmerkungen zu SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
  Im folgenden Artikel werden Einschränkungen und Probleme mit Releases von SQL Server 2016, Service Packs inbegriffen, beschrieben. Informationen zu Neuerungen finden Sie unter [Neues im Berichts-Generator für SQL Server 2016](https://docs.microsoft.com/sql/sql-server/what-s-new-in-sql-server-2016).

- [![Download aus dem Evaluation Center](../includes/media/download2.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) Laden Sie SQL Server 2016 aus dem **[Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)** herunter.
- [![Azure Virtual Machine (klein)](../includes/media/azure-vm.png)](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/) Haben Sie ein Azure-Konto?  Wechseln Sie anschließend **[hierhin](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/)** , um einen virtuellen Computer zu starten, auf dem SQL Server 2016 SP1 bereits installiert ist.
- [![SSMS herunterladen](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) Wechseln Sie zu **[Herunterladen von SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md)**, um die neueste Version von SQL Server Management Studio (SSMS) abzurufen.

## <a name="bkmk_2016sp2"></a>SQL Server 2016 Service Pack 2 (SP2)

![info_tip](../sql-server/media/info-tip.png) SQL Server 2016 SP2 enthält alle kumulativen Updates bis einschließlich CU8, die nach SQL Server 2016 SP1 veröffentlicht wurden.

- [![Microsoft Download Center](../includes/media/download2.png)](https://go.microsoft.com/fwlink/?linkid=869608) [Herunterladen von SQL Server 2016 Service Pack 2 (SP2)](https://go.microsoft.com/fwlink/?linkid=869608)
- Eine vollständige Liste der Updates finden Sie unter [SQL Server 2016 Service Pack 2 release information (Releaseinformationen zu SQL Server 2016 Service Pack 2)](https://support.microsoft.com/help/4052908/sql-server-2016-service-pack-2-release-information).

Sie müssen Ihren Computer möglicherweise nach der Installation von SQL Server 2016 SP2 neu starten. Als bewährte Methode wird empfohlen, nach der Installation von SQL Server 2016 SP2 einen Neustart zu planen und durchzuführen.

Leistungs- und skalierungsbasierte Verbesserungen, die in SQL Server 2016 SP2 enthalten sind

|Funktion|und Beschreibung|Weitere Informationen|
|---|---|---|
|Verbesserter Cleanupvorgang für die Verteilungsdatenbank |   Übergroße Verteilungsdatenbanktabellen führten zu Blockierungs- und Deadlocksituationen. Im Rahmen einer verbesserten Cleanup-Prozedur sollen einige davon beseitigt werden. |   [KB4040276](https://support.microsoft.com/help/4040276/fix-indirect-checkpoints-on-the-tempdb-database-cause-non-yielding)  |
|Bereinigen der Änderungsnachverfolgung    |   Verbesserte Leistung und Effizienz des Cleanups für Nebentabellen bei der Änderungsnachverfolgung.    |   [KB4052129](https://support.microsoft.com//help/4052129/update-for-manual-change-tracking-cleanup-procedure-in-sql-server-2016) |
|Verwenden von CPU-Timeout zum Abbrechen von Resource Governor-Anforderungen   |   Verbessert die Handhabung von Abfrageanforderungen, indem die Anforderung tatsächlich abgebrochen wird, falls CPU-Schwellenwerte für eine Anforderung erreicht werden. Dieses Verhalten wird unter dem Ablaufverfolgungsflag 2422 aktiviert. |   [KB4038419](https://support.microsoft.com/help/4038419/add-cpu-timeout-to-resource-governor-request-max-cpu-time-sec)   |
|Verwenden von SELECT INTO zum Erstellen einer Zieltabelle in der Dateigruppe    |   Ab SQL Server 2016 SP2 unterstützt die T-SQL-Syntax SELECT INTO das Laden einer Tabelle in eine Dateigruppe, die nicht die Standarddateigruppe des Benutzers ist, die das Schlüsselwort ON <Filegroup name> in der T-SQL-Syntax verwendet. |       |
|Verbesserter indirekter Prüfpunkt für tempdb    |   Das Verwenden eines indirekten Prüfpunkts für tempdb wurde verbessert, um die Spinlock-Konflikte für DPLists zu reduzieren. Diese Verbesserung erlaubt der tempdb-Workload in SQL Server 2016 eine sofort einsatzbereite zentrale Hochskalierung, falls die Verwendung des indirekten Prüfpunkts für tempdb ON (Ein) ist.    |   [KB4040276](https://support.microsoft.com/help/4040276) |
|Verbesserte Leistung bei der Datenbanksicherung auf Computern mit großem Speicher  |   SQL Server 2016 SP2 optimiert die Art und Weise, wie wir die fortlaufende E/A während der Sicherung ausgleichen, wodurch wir eine deutliche Leistungssteigerung bei der Sicherung für kleine bis mittlere Datenbanken erreichen. Wenn Sicherungen der Systemdatenbank auf einem Computer mit 2 TB durchgeführt werden, ist die Leistung stark verbessert. Die Leistungssteigerung sinkt mit steigender Datenbankgröße, da die zu sichernden Seiten und die Sicherungs-E/A im Vergleich zur Iteration des Pufferpools mehr Zeit in Anspruch nehmen. Durch diese Änderung können Sie die Sicherungsleistung für Kunden optimieren, die mehrere kleine Datenbanken auf hochwertigen Servern mit hoher Speicherkapazität hosten.    |       |
|Unterstützung für die VDI-Sicherungskomprimierung für mit TDE aktivierte Datenbanken   |   SQL Server 2016 SP2 fügt VDI-Support hinzu, damit VDI-Sicherungslösungen die Komprimierung für mit TDE aktivierte Datenbanken nutzen können. Durch diese Verbesserung wurde ein neues Sicherungsformat eingeführt, um die Sicherungskomprimierung für mit TDE-aktivierte Datenbanken zu unterstützen. Die SQL Server-Engine verarbeitet transparent neue und alte Sicherungsformate, um die Sicherungen wiederherzustellen.   |       |
|Dynamisches Laden von Profilparametern des Replikations-Agents    |   Mithilfe dieser neuen Erweiterungen können Replikations-Agent-Parameter dynamisch geladen werden, ohne dass der Agent neu gestartet werden muss. Diese Änderung gilt nur für die am häufigsten verwendeten Agent-Profilparameter. |       |
|Support der MAXDOP-Option für die CREATE STATISTICS-Anweisung und UPDATE STATISTICS-Anweisung |    Mit dieser Erweiterung kann die MAXDOP-Option für eine CREATE STATISTICS-Anweisung und UPDATE STATISTICS-Anweisung angegeben werden. Zudem kann sichergestellt werden, dass die richtige MAXDOP-Einstellung verwendet wird, wenn Statistiken als Teil eines Erstellungs- oder Neuerstellungsvorgangs für alle Indextypen aktualisiert werden (falls die MAXDOP-Option nicht vorhanden ist).   |   [KB4041809](https://support.microsoft.com/help/4041809) |
|Verbessertes Update für automatische Statistiken für inkrementelle Statistiken |    Wenn z.B. mehrere Datenänderungen für mehrere Partitionen in einer Tabelle vorgenommen wurden und die Anzahl aller Änderung für inkrementelle Statistiken – jedoch keine einzelnen Partitionen – den Grenzwert für automatische Updates überschreitet, kann sich das Statistikupdate so lange verzögern, bis weitere Änderungen in der Tabelle vorgenommen werden. Dieses Verhalten wird unter dem Ablaufverfolgungsflag 11024 korrigiert.   |       |

Unterstützbarkeit und Diagnose betreffende Verbesserungen sind in SQL Server 2016 SP2 beinhaltet.

|Funktion|und Beschreibung|Weitere Informationen|
|---|---|---|
|Vollständige DTC-Unterstützung für Datenbanken in einer Verfügbarkeitsgruppe    |   Datenbankübergreifende Transaktionen für Datenbanken, die Teil einer Verfügbarkeitsgruppe sind, werden für SQL Server 2016 nicht unterstützt. Mit SQL Server 2016 SP2 führen wir die vollständige Unterstützung für verteilte Transaktionen mit Datenbanken der Verfügbarkeitsgruppe ein.   |       |
|Update für die Spalte „is_encrypted“ in „sys.database“ zur genauen Wiedergabe des Verschlüsselungsstatus für TempDB |   Der Wert der Spalte „is_encrypted“ in „sys.databases“ beträgt 1 für tempdb, auch wenn Sie die Verschlüsselung für alle Benutzerdatenbanken deaktivieren und SQL Server neu starten. Das erwartete Verhalten ist, dass der Wert 0 (null) ist, da tempdb in dieser Situation nicht länger verschlüsselt ist. Beginnend mit SQL Server 2016 SP2 gibt „is_encrypted“ in „sys.databases“ nun den Verschlüsselungsstatus für tempdb genau wieder.  |       |
|Neue DBCC CLONEDATABASE-Optionen zum Generieren verifizierter Klone und Sicherungsklone   |   Mit SQL Server 2016 SP2 lässt DBCC CLONEDATABASE jetzt zwei neue Optionen zu: das Erstellen eines verifizierten Klons und das Erstellen eines Sicherungsklons. Wenn eine Klondatenbank mithilfe der Option WITH VERIFY_CLONEDB erstellt wird, wird auch ein konsistenter Datenbankklon erstellt und geprüft, der von Microsoft in der Produktion unterstützt wird. Eine neue Eigenschaft wird eingeführt, um zu überprüfen, ober der Klon die verifizierte Eigenschaft SELECT DATABASEPROPERTYEX(‘clone_database_name’, ‘IsVerifiedClone’) ist. Wenn ein Klon mit der Option BACKUP_CLONEDB erstellt wird, wird eine Sicherung im selben Ordner, in dem sich auch die Datendatei befindet, erstellt. Dadurch können Kunden den Klon leichter auf unterschiedliche Server verschieben oder an den Microsoft-Kundenservice (CSS) zur Problembehandlung senden.  |       |
|Unterstützung für Service Broker (SSB) für DBCC CLONEDATABASE    |   Der erweiterte DBCC CLONEDATABASE-Befehl zum Zulassen der Skripterstellung von SSB-Objekten  |   [KB4092075](https://support.microsoft.com/help/4092075) |
|Neue dynamische Verwaltungssicht (DMV) zur Überwachung des tempdb-Speicherplatzverbrauchs    |   Die neue DMV „sys.dm_tran_version_store_space_usage“ wird in SQL Server 2016 SP2 eingeführt, um die Überwachung von tempdb für die Versionsspeichernutzung zu aktivieren. Datenbankadministratoren können tempdb-Größen basierend auf der Anforderung an die Versionsspeichernutzung pro Datenbank proaktiv planen. Dies geschieht ohne Mehraufwand an Leistung, wenn die Ausführung auf Produktionsservern erfolgt. |       |
|Unterstützung von vollständigen Speicherabbildern für Replikations-Agents | Wenn Replikations-Agents auf Ausnahmefehler stoßen, erstellen sie aktuell standardmäßig ein Miniabbild der Ausnahmesymptome. Dadurch wird die Problembehandlung von Ausnahmefehlern sehr schwierig. Mit dieser Änderung führen wir einen neuen Registrierungsschlüssel ein, der die Erstellung eines vollständigen Speicherabbilds für Replikations-Agents ermöglicht.  |       |
|Verbesserung für erweiterte Ereignisse zum Lesen von Routingfehlern für eine Verfügbarkeitsgruppe |   Derzeit wird „read_only_rout_fail xEvent“ nur ausgelöst, wenn zwar eine Routingliste besteht, jedoch zu keinem der Server auf der Liste eine Verbindung hergestellt werden kann. SQL Server 2016 SP2 beinhaltet zusätzliche Informationen zur Unterstützung bei der Problembehandlung und Erweiterungen zu den Codepunkten, bei denen xEvent ausgelöst wird.  |       |
|Neue DMV, um das Transaktionsprotokoll zu überwachen |   Die neue DMV „sys.dm_db_log_stats“ wurde hinzugefügt, die zusammenfassende Ebenenattribute und Informationen zu den Transaktionsprotokolldateien von Datenbanken zurückgibt. |       |
|Neue DMV zum Überwachen von VLF-Informationen |   Die neue DMV „sys.dm_db_log_info“ wird in SQL Server 2016 SP2 eingeführt, mit der Sie VLF-Informationen ähnlich wie DBCC LOGINFO verfügbar machen können, um potentielle Transaktionsprotokollprobleme, die von Kunden gemeldet wurden, zu überwachen, davor zu warnen und diese zu vermeiden.    |       |
|Prozessorinformationen in „sys.dm_os_sys_info“|   Neue Spalten, die der DMV „sys.dm_os_sys_info“ hinzugefügt wurden, um die sich auf den Prozessor beziehenden Informationen verfügbar zu machen, wie „socket_count und cores_per_numa“  |       |
|Erweiterung modifizierter Informationen in „sys.dm_db_file_space_usage“| Eine neue Spalte, die „sys.dm_db_file_space_usage“ hinzugefügt wurde, um die Anzahl der geänderten Erweiterungen seit der letzten vollständigen Sicherung nachzuverfolgen  |       |
|Segmentinformation in „sys.dm_exec_query_stats“ |   Neue Spalten wurden zu „sys.dm_exec_query_stats“ hinzugefügt, um die Anzahl der übersprungenen und gelesenen Columnstore-Segmente nachzuverfolgen, zum Beispiel „total_columnstore_segment_reads“ und „total_columnstore_segment_skips“.   |   [KB4051358](https://support.microsoft.com/help/4051358) |
|Festlegen des korrekten Kompatibilitätsgrads für die Verteilungsdatenbank  |   Nach der Installation des Service Packs ändert sich der Kompatibilitätsgrad der Verteilungsdatenbank in 90. Der Grund dafür war ein Codepfad in der gespeicherten Prozedur „sp_vupgrade_replication“. Das Service Pack wurde nun dahingehend geändert, dass es nun einen angemessenen Kompatibilitätsgrad für die Verteilungsdatenbank bestimmt.   |       |
|Verfügbarmachen der letzten bekannten funktionierenden DBCC CHECKDB-Information    |   Es wurde eine neue Datenbankoption hinzugefügt, damit die Datumsangabe der letzten erfolgreichen Ausführung von DBCC CHECKDB programmgesteuert zurückgegeben werden kann. Benutzer können nun DATABASEPROPERTYEX([database], ‘lastgoodcheckdbtime’) abfragen, um einen einzelnen Wert abzurufen, der das Datum und die Uhrzeit der letzten erfolgreichen DBCC CHECKDB-Ausführung in der angegebenen Datenbank darstellt.  |       |
|Showplan XML-Erweiterungen| [Informationen darüber, welche Statistiken zum Kompilieren des Abfrageplans verwendet wurden](https://blogs.msdn.microsoft.com/sql_server_team/sql-server-2017-showplan-enhancements/), einschließlich der Name der Statistik, des Änderungszählers und des Prozentsatzes der Stichproben sowie wann das letzte Update für die Statistik stattfand. Gilt nur für CE-Modelle 120 und höher. Dies wird beispielsweise nicht für CE 70 unterstützt.| |
| |Zur Showplan-XML wird ein neues Attribut, [EstimateRowsWithoutRowgoal](https://blogs.msdn.microsoft.com/sql_server_team/more-showplan-enhancements-row-goal/), hinzugefügt, wenn der Abfrageoptimierer die „row goal“-Logik verwendet.| |
| |Die neuen Runtime-Attribute [UdfCpuTime und UdfElapsedTime](https://blogs.msdn.microsoft.com/sql_server_team/more-showplan-enhancements-udfs/) in der tatsächlichen Showplan-XML zum Nachverfolgen der Zeit, die für skalare benutzerdefinierte Funktionen gebraucht wird| |
| |Das Hinzufügen des CXPACKET-Wartetyps zur [Liste der möglichen Top 10 der Wartevorgänge](https://blogs.msdn.microsoft.com/sql_server_team/new-showplan-enhancements/) in der tatsächlichen Showplan-XML: Eine parallele Abfrageausführung erfordert häufig CXPACKET-Wartevorgänge. Dieser Wartevorgangstyp wurde jedoch nicht in der aktuellen Showplan-XML gemeldet. |       |
| |Die Warnung vor dem Runtime-Überlauf wird erweitert, um die Anzahl der Seiten, die in tempdb geschrieben wurden, während des Überlaufs eines Parallelitätsoperators zu melden.| |
|Replikationsunterstützung für Datenbanken mit ergänzenden Zeichensortierungen  |   Die Replikation kann nun auf Datenbanken unterstützt werden, die die ergänzende Zeichensortierung verwenden. |       |
|Verbesserte Handhabung von Service Broker mit Failover einer Verfügbarkeitsgruppe |   Wenn Service Broker für Datenbanken der Verfügbarkeitsgruppe in der aktuellen Implementierung aktiviert ist, bleiben bei einem Failover der Verfügbarkeitsgruppe alle Service Broker-Verbindungen, die dem primären Replikat entstammen, geöffnet. Mit dieser Verbesserung sollen all diese offenen Verbindungen während eines Failover der Verfügbarkeitsgruppe geschlossen werden. |       |
|Verbesserte Problembehandlung für parallele Wartevorgänge |   durch Hinzufügen eines neuen [CXCONSUMER](https://blogs.msdn.microsoft.com/sql_server_team/making-parallelism-waits-actionable/)-Wartevorgangs.   |       |
|Verbesserte Konsistenz zwischen DMVs für dieselbe Information |   Die DMV „sys.dm_exec_session_wait_stats“ verfolgt nun CXPACKET- und CXCONSUMER-Wartevorgänge konsistent mit der DMV„sys.dm_os_wait_stats“. |       |
|Verbesserte Problembehandlung von abfrageinternen Parallelitätsdeadlocks | Ein neues erweitertes exchange_spill-Ereignis, um die Anzahl der in tempdb geschriebenen Ereignisse während des Überlaufs eines Parallelitätsoperators im xEvent-Feldnamen „worktable_physical_writes“ zu melden.| |
| |Die Überlaufspalten in den DMVs „sys.dm_exec_query_stats“, „sys.dm_exec_procedure_stats“ und „sys.dm_exec_trigger_stats“ (wie z.B. „total_spills“) enthalten jetzt auch die Daten, die von Parallelitätsoperatoren zum Überlauf gebracht werden.| |
| |Das XML-Deadlockdiagramm wurde für Szenarios für Parallelitätsdeadlocks verbessert. Der exchangeEvent-Ressource wurden mehr Attribute hinzugefügt.| |
| |Das XML-Deadlockdiagramm wurde für Deadlocks verbessert, die Operatoren im Batchmodus einbeziehen, und der SyncPoint-Ressource wurden mehr Attribute hinzugefügt.| |
|Dynamisches erneutes Laden einiger Profilparametern des Replikations-Agents |   In der aktuellen Implementierung von Replikations-Agents erfordert jede Änderung im Agent-Profilparameter, dass der Agent angehalten und neu gestartet wird. Durch diese Verbesserungen können Parameter dynamisch neu geladen werden, ohne dass der Replikations-Agent neu geladen werden muss.   |       |

![horizontal-bar.png](media/horizontal-bar.png)

## <a name="bkmk_2016sp1"></a>SQL Server 2016 Service Pack 1 (SP1)
![info_tip](../sql-server/media/info-tip.png) SQL Server 2016 SP1 umfasst alle kumulativen Updates bis SQL Server 2016 RTM CU3 Security einschließlich des Sicherheitsupdates MS16-136. Es enthält ein Rollup der in den kumulativen Updates von SQL Server 2016 bereitgestellten Lösungen und umfasst das aktuelle kumulative Update CU3 sowie das Sicherheitsupdate MS16-136 mit Veröffentlichungsdatum am 8. November 2016.

Die folgenden Features sind in der Standard, Web, Express und Local DB Edition von SQL Server SP1 verfügbar (sofern nicht anders angegeben):
- Always Encrypted
- Geänderte Datenerfassung (in Express nicht verfügbar)
- columnstore
- Komprimierung
- Dynamische Datenmaskierung
- Differenzierte Überwachung
- In-Memory OLTP (in Local DB nicht verfügbar)
- Mehrere FileStream-Container (in Local DB nicht verfügbar)
- Partitionierung
- PolyBase
- Sicherheit auf Zeilenebene

In der folgenden Tabelle werden wichtige Verbesserungen in SQL Server 2016 SP1 zusammengefasst.

|Funktion|und Beschreibung|Weitere Informationen|
|---|---|---|
|Masseneinfügung in Heaps mit automatischem TABLOCK unter TF 715| Das Ablaufverfolgungsflag 715 aktiviert Tabellensperren für Massenladevorgänge in einen Heap ohne nicht gruppierte Indizes.|[Migrating SAP workloads to SQL Server just got 2.5x faster (Beschleunigung der Migration von SAP-Workloads zu SQL Server um das 2,5-fache)](https://blogs.msdn.microsoft.com/sql_server_team/migrating-sap-workloads-to-sql-server-just-got-2-5x-faster/)|
|CREATE OR ALTER|Bereitstellen von Objekten wie gespeicherten Prozeduren, Triggern, benutzerdefinierten Funktionen und Ansichten.|[Blog der SQL Server-Datenbank-Engine](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/11/17/create-or-alter-another-great-language-enhancement-in-sql-server-2016-sp1/)|
|DROP TABLE-Unterstützung für die Replikation|DROP TABLE DDL-Unterstützung für die Replikation zum Löschen von Replikationsartikeln.|[KB 3170123](https://support.microsoft.com/help/3170123/supports-drop-table-ddl-for-articles-that-are-included-in-transactiona)|
|Signieren des FileStream RsFx-Treibers|Der Filestream RsFx-Treiber wird im Windows Hardware Developer Center Dashboard-Portal (Dev-Portal) signiert und zertifiziert. Dadurch kann der Filestream RsFx-Treiber von SQL Server 2016 SP1 problemlos unter Windows Server 2016/Windows 10 installiert werden.|[Migrating SAP workloads to SQL Server just got 2.5x faster (Beschleunigung der Migration von SAP-Workloads zu SQL Server um das 2,5-fache)](https://blogs.msdn.microsoft.com/sql_server_team/migrating-sap-workloads-to-sql-server-just-got-2-5x-faster/)|
|LPIM für SQL-Dienstkonto – programmgesteuerte Identifikation|Ermöglicht DBAs die programmgesteuerte Identifikation, wenn die Berechtigung zum Sperren von Seiten im Speicher (Lock Pages in Memory, LPIM) zur Startzeit des Service besteht.|[Developers Choice: Programmatically identify LPIM and IFI privileges in SQL Server (Wahl für Entwickler: LPIM- und IFI-Berechtigungen zur programmgesteuerten Identifikation in SQL Server)](https://blogs.msdn.microsoft.com/sql_server_team/developers-choice-programmatically-identify-lpim-and-ifi-privileges-in-sql-server)|
|Manuelles Bereinigen der Änderungsnachverfolgung|Die neue gespeicherte Prozedur löscht die interne Tabelle der Änderungsnachverfolgung bedarfsgesteuert.| [KB 3173157](https://support.microsoft.com/help/3173157/adds-a-stored-procedure-for-the-manual-cleanup-of-the-change-tracking)|
|Parallele INSERT..SELECT-Änderungen in lokalen temporären Tabellen|Neue parallele INSERT in INSERT..SELECT-Vorgänge.|[SQL Server-Kundenberatungsteam](https://blogs.msdn.microsoft.com/sqlcat/2016/07/21/real-world-parallel-insert-what-else-you-need-to-know/)|
|Showplan XML|Erweiterte Diagnose einschließlich einer aktivierten Zuweisungswarnung und eines aktivierten maximalen Arbeitsspeichers für eine Abfrage, aktivierter Ablaufverfolgungsflags und Oberflächen für andere Diagnoseinformationen. | [KB 3190761](https://support.microsoft.com/help/3190761/update-to-improve-diagnostics-by-expose-data-type-of-the-parameters-fo)|
|Speicherklassenspeicher|Steigern Sie mit dem Speicherklassenspeicher in Windows Server 2016 die Transaktionsverarbeitung, wodurch die Commitzeiten für Transaktionen nach Größenordnungen beschleunigt werden können.|[Blog der SQL Server-Datenbank-Engine](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/12/02/transaction-commit-latency-acceleration-using-storage-class-memory-in-windows-server-2016sql-server-2016-sp1/)|
|USE HINT|Verwenden Sie die Abfrageoption `OPTION(USE HINT('<option>'))`, um das Verhalten des Abfrageoptimierers mit unterstützten Hinweisen auf Abfrageebene zu ändern. Anders als bei der Option QUERYTRACEON sind bei der Option USE HINT keine Systemadministratorberechtigungen erforderlich.|[Developers Choice: USE HINT-Abfragehinweise](https://blogs.msdn.microsoft.com/sql_server_team/developers-choice-use-hint-query-hints/)|
|XEvent-Ergänzungen|Neue XEvents- und Perfmon-Diagnosefunktionen bewirken eine Optimierung der Wartezeit bei der Problembehandlung.|[Erweiterte Ereignisse](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)|

Zudem sollten Sie folgende Problembehandlungen beachten:
- Basierend auf Feedback von DBAs und der SQL-Community werden die Hekaton-Protokollierungsnachrichten ab SQL 2016 SP1 auf ein Minimum reduziert.
- Überprüfen neuer [Ablaufverfolgungsflags](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).
- Die vollständigen Versionen der WideWorldImporters-Beispieldatenbanken können jetzt beginnend mit SQL Server 2016 SP1 mit der Standard Edition und der Express Edition ausgeführt werden und sind auf [Github]( https://github.com/Microsoft/sql-server-samples/releases/tag/wide-world-importers-v1.0) verfügbar. Im Beispiel müssen keine Änderungen vorgenommen werden. Die Datenbanksicherungen, die zum RTM der Enterprise Edition erstellt wurden, werden in SP1 von der Standard und der Express Edition unterstützt.

Für die Installation von SQL Server 2016 SP1 ist nach der Installation möglicherweise ein Neustart erforderlich. Als bewährte Methode wird empfohlen, nach der Installation von SQL Server 2016 SP1 einen Neustart zu planen und durchzuführen.

### <a name="download-pages-and-more-information"></a>Downloadseiten und weitere Informationen

- [Service Pack 1 für Microsoft SQL Server 2016 herunterladen](https://www.microsoft.com/download/details.aspx?id=54276)
- [SQL Server 2016 Service Pack 1 (SP1) freigegeben](https://blogs.msdn.microsoft.com/sqlreleaseservices/sql-server-2016-service-pack-1-sp1-released/)
- [Releaseinformationen zu SQL Server 2016 Service Pack 1](https://support.microsoft.com/kb/3182545)
- ![info_tip](../sql-server/media/info-tip.png) Links und Informationen zu allen unterstützten Versionen finden Sie unter [SQL Server-Update Center](https://msdn.microsoft.com/library/ff803383.aspx). Dort finden Sie auch Informationen zu Service Packs von [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]

![horizontal-bar.png](media/horizontal-bar.png)

##  <a name="bkmk_2016_ga"></a> SQL Server 2016 Release - General Availability (GA)
-   [Datenbank-Engine (GA)](#bkmk_ga_instalpatch)
-   [Stretch Database (GA)](#bkmk_ga_stretch)
-   [Abfragespeicher (GA)](#bkmk_ga_query_store)
-   [Produktdokumentation (GA)](#bkmk_ga_docs)

### ![repl_icon_warn](../database-engine/availability-groups/windows/media/repl-icon-warn.gif) <a name="bkmk_ga_instalpatch"></a> Install Patch Requirement (GA)
**Problem und Kundenbeeinträchtigung:** Microsoft hat ein Problem erkannt, das die Microsoft VC++ 2013 Runtime-Binärdateien betrifft, die von SQL Server 2016 als erforderliche Komponente installiert werden. Ein Update ist verfügbar, um dieses Problem zu beheben. Wenn dieses Update an den VC++ Runtime-Binarys nicht installiert wird, können bei SQL Server 2016 in bestimmten Szenarien Stabilitätsprobleme auftreten. Bevor Sie SQL Server 2016 installieren, überprüfen Sie, ob der Computer das in [KB 3164398](https://support.microsoft.com/kb/3164398)beschriebenen Patch benötigt. Der Patch ist auch im [Kumulativen Updatepaket 1 (CU1) für SQL Server 2016 RTM](https://www.microsoft.com/download/details.aspx?id=53338) enthalten.

**Lösung:** Verwenden Sie eine der folgenden Lösungen:

- Installieren Sie [KB 3138367 – Update für Visual C++ 2013 und Visual C++ Redistributable Package](https://support.microsoft.com/kb/3138367). Der KB-Hotfix ist die bevorzugte Lösung. Sie können dies vor oder nach der Installation von SQL Server 2016 installieren.

    Wenn SQL Server 2016 bereits installiert ist, führen Sie nacheinander die folgenden Schritte aus:

    1.  Laden Sie die passende *vcredist_\*exe* herunter.
    1.  Beenden Sie den SQL Server-Dienst für alle Instanzen der Datenbank-Engine.
    1.  Installieren Sie **KB 3138367**.
    1.  Starten Sie den Computer neu.


 - Installieren Sie  [KB 3164398 – kritisches Update für erforderliche MSVCRT-Komponenten für SQL Server 2016](https://support.microsoft.com/kb/3164398).

    Wenn Sie **KB 3164398**verwenden, können Sie während der Installation von SQL Server über Microsoft Update oder Microsoft Download Center installieren.

    - **Während der Installation von SQL Server 2016:** Wenn der Computer, auf dem Sie SQL Server einrichten, Zugang zum Internet hat, überprüft das SQL Server-Setup im Rahmen der gesamten SQL Server-Installation, ob das Update vorhanden ist. Wenn Sie das Update akzeptieren, lädt das Setupprogramm die Binärdateien im Rahmen der Installation herunter und aktualisiert sie.

    - **Microsoft Update:** Das Update ist bei Microsoft Update als wichtiges, nicht sicherheitsrelevantes Update für SQL Server 2016 verfügbar. Installation über Microsoft Update, nachdem SQL Server 2016 nach dem Update den Neustart des Servers fordert.

    - **Download Center:** Das Update steht im Microsoft Download Center zur Verfügung. Sie können die Software für das Update herunterladen und nach der Installation von SQL Server 2016 auf Servern installieren.


### <a name="bkmk_ga_stretch"></a>Stretch Database

#### <a name="problem-with-a-specific-character-in-a-database-or-table-name"></a>Problem mit einem bestimmten Zeichen in einem Datenbank- oder Tabellennamen

**Problem und Kundenbeeinträchtigung:** Beim Versuch, Stretch Database in einer Datenbank oder Tabelle zu aktivieren, ist ein Fehler aufgetreten. Das Problem tritt auf, wenn der Name des Objekts ein Zeichen enthält, das beim Konvertieren von Klein- und Großschreibung als ein anderes Zeichen behandelt wird. Ein Beispiel für ein Zeichen, das dieses Problem auslöst, ist das Zeichen „ƒ“ (durch Drücken von ALT+159 erstellt).

**Problemumgehung:** Wenn Sie Stretch Database in einer Datenbank oder Tabelle aktivieren möchten, ist die einzige Option, das Objekt umzubenennen und das Problemzeichen zu entfernen.

#### <a name="problem-with-an-index-that-uses-the-include-keyword"></a>Problem mit einem Index, der das Schlüsselwort INCLUDE verwendet

**Problem und Kundenbeeinträchtigung:** Der Versuch, Stretch Database in einer Tabelle zu aktivieren, die über einen Index verfügt, der das INCLUDE-Schlüsselwort verwendet, um zusätzliche Spalten in den Index einzubeziehen, resultiert in einem Fehler.

**Problemumgehung:** Löschen Sie den Index, der das INCLUDE-Schlüsselwort verwendet, aktivieren Sie Stretch Database in der Tabelle, und erstellen Sie den Index neu. Wenn Sie dies tun, achten Sie darauf, die Wartungsmethoden und Richtlinien Ihrer Organisation einzuhalten, um sicherzustellen, dass für Benutzer der betreffenden Tabelle höchstens minimale Auswirkungen entstehen.

### <a name="bkmk_ga_query_store"></a>Query Store

#### <a name="problem-with-automatic-data-cleanup-on-editions-other-than-enterprise-and-developer"></a>Problem mit automatischer Datenbereinigung bei anderen Editionen als Enterprise und Developer

 **Problem und Kundenbeeinträchtigung:** Bei der automatischen Datenbereinigung bei anderen Editionen als Enterprise und Developer tritt ein Fehler auf.
In Folge dessen wächst der vom Abfragespeicher verwendete Speicherplatz mit der Zeit, bis das konfigurierte Limit erreicht ist, wenn Daten nicht manuell gelöscht werden. Wenn dieses Problem nicht beseitigt wird, wird auch der Speicherplatz aufgefüllt, der den Fehlerprotokollen zugeordnet ist, da jeder Bereinigungsversuch eine Dumpdatei erzeugt. Der Aktivierungszeitraum für die Bereinigung hängt von der Häufigkeit der Arbeitsauslastung ab, ist aber nicht länger als 15 Minuten.

 **Problemumgehung:** Wenn Sie den Abfragespeicher bei anderen Editionen als Enterprise und Developer verwenden möchten, müssen Sie explizit die Bereinigungsrichtlinien deaktivieren. Dies kann über SQL Server Management Studio (Seite „Datenbankeigenschaften“) oder über das Transact-SQL-Skript erfolgen:

```ALTER DATABASE <database name> SET QUERY_STORE (OPERATION_MODE = READ_WRITE, CLEANUP_POLICY = (STALE_QUERY_THRESHOLD_DAYS = 0), SIZE_BASED_CLEANUP_MODE = OFF)```

Darüber hinaus sollten Sie manuelle Bereinigungsoptionen erwägen, um zu verhindern, dass der Abfragespeicher in den schreibgeschützten Modus übergeht. Führen Sie z.B. die folgende Abfrage zum Bereinigen des gesamten Datenbereichs in regelmäßigen Abständen aus:

```ALTER DATABASE <database name> SET QUERY_STORE CLEAR```

Führen Sie außerdem die folgenden gespeicherten Prozeduren des Abfragespeichers regelmäßig aus, um Laufzeitstatistik, bestimmte Abfragen oder Plänen zu bereinigen:

- `sp_query_store_reset_exec_stats`

- `sp_query_store_remove_plan`

- `sp_query_store_remove_query`


###  <a name="bkmk_ga_docs"></a> Produktdokumentation (GA)
 **Problem und Kundenbeeinträchtigung:** Eine herunterladbare Version der Dokumentation zu SQL Server 2016 ist noch nicht verfügbar. Wenn Sie den Hilfebibliotheks-Manager verwenden, um zu versuchen, **Inhalt vom Onlinespeicherort zu installieren**, wird Ihnen die Dokumentationen zu SQL Server 2012 und SQL Server 2014 angezeigt. Allerdings gibt es keine Optionen zum Anzeigen der SQL Server 2016-Dokumentation.

 **Problemumgehung:** Sie können eine der folgenden Problemumgehungen verwenden:

 ![Verwalten der Hilfeeinstellungen für SQL Server](../sql-server/media/docs-sql2016-managehelpsettings.png "Verwalten der Hilfeeinstellungen für SQL Server")

-   Verwenden Sie die Option **Onlinehilfe oder lokale Hilfe auswählen** , und konfigurieren Sie die Hilfe für „Ich möchte Onlinehilfe verwenden“.

-   Verwenden Sie die Option **Inhalt von Onlinespeicherort installieren** , und laden Sie den Inhalt von SQL Server 2014 herunter.

 **F1-Hilfe:** Beim Drücken von F1 in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] wird standardmäßig die Onlineversion des F1-Hilfeartikels im Browser angezeigt. Für die Probleme wird browserbasierte Hilfe angeboten, auch wenn Sie die lokale Hilfe konfiguriert und installiert haben.

**Aktualisieren von Inhalten:** In SQL Server Management Studio und Visual Studio kann die Anwendung Help Viewer während des Hinzufügens der Dokumentation einfrieren (hängenbleiben). Führen Sie zur Lösung des Problems folgende Schritte aus. Weitere Informationen zu diesem Problem finden Sie unter [Visual Studio Help Viewer friert beim Begrüßungsbildschirm ein](https://msdn.microsoft.com/library/mt654096.aspx).

* Öffnen Sie die Datei „%LOCALAPPDATA%\Microsoft\HelpViewer2.2\HlpViewer_SSMS16_en-US.settings“ | „HlpViewer_VisualStudio14_en-US.settings“ im Editor, und ändern Sie das Datum im folgenden Code in einen Zeitpunkt in der Zukunft.

```
     Cache LastRefreshed="12/31/2017 00:00:00"
```

## <a name="additional-information"></a>Zusätzliche Informationen
+ [SQL Server 2016-Installation](../database-engine/install-windows/installation-for-sql-server-2016.md)
+ [SQL Server-Update Center – Links und Informationen zu allen unterstützten Versionen](https://msdn.microsoft.com/library/ff803383.aspx)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png "MS_Logo_X-Small")
