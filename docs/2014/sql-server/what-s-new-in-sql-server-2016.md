---
title: Was&#39;Neues in SQLServer 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/25/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- new features [SQL Server]
- SQL Server, what's new
- SQL Server 2008 what's new
- what's new [SQL Server]
- sql server 2014 sp1
- sql server 2014 sp2
ms.assetid: 6a428023-e3cc-4626-a88a-4c13ccbd7db0
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 26d0c84194f6f2aafb8bc499ff5404a1438ee577
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2019
ms.locfileid: "57578840"
---
# <a name="what39s-new-in-sql-server-2014"></a>Was&#39;Neues in SQLServer 2014
  Dieses Thema fasst zusammen, detaillierten Links zu neuen Funktionen in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] und Service Packs für Informationen [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 
**Probieren Sie es aus:** ![Azure Virtual Machine, klein](./media/what-s-new-in-sql-server-2016/azure-virtual-machine-small.png) Azure-Konto?  Wechseln Sie anschließend **[hierhin](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2014sp1EnterpriseWindowsServer2012R2)** , um einen virtuellen Computer zu starten, auf dem SQL Server 2014 Service Pack 1 (SP1) bereits installiert ist. 
  
-   [Neues &#40;Datenbank-Engine&#41;](../database-engine/whats-new-in-sql-server-2016.md)  
  
-   [Neuigkeiten in Analysis Services und Business Intelligence](../analysis-services/what-s-new-in-analysis-services.md)  
  
-   [Neuigkeiten in der SQL Server-Installation](install/what-s-new-in-sql-server-installation.md)  
  
 **[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] wichtige neue Features wurde, die der folgenden nicht eingeführt werden:**  
  
-   [Neues &#40;Integrationsdienste&#41;](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)  
  
-   [Neues &#40;Reporting Services&#41;](../reporting-services/what-s-new-reporting-services.md)  
  
## <a name="includesssql14includessssql14-mdmd-service-pack-1-sp1"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 1 (SP1)
[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP1) nicht wichtige neue Features eingeführt.
-  [SQL Server 2014 Service Pack 1-Versionsinformationen](https://support.microsoft.com/en-us/kb/3058865).
-  [![Laden Sie Servicepack 1 für Microsoft?? SqlServer? 2014](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=46694) [Laden Sie Servicepack 1 für Microsoft?? SqlServer? 2014](https://www.microsoft.com/en-us/download/details.aspx?id=46694).


## <a name="includesssql14includessssql14-mdmd-service-pack-2-sp2"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Servicepack 2 (SP2)
- [SQL Server 2014 Service Pack 2-Versionsinformationen](https://support.microsoft.com/en-us/kb/3171021).
-  [![Laden Sie Servicepack 2 für Microsoft?? SqlServer? 2014](./media/what-s-new-in-sql-server-2016/download.png)](https://go.microsoft.com/fwlink/?LinkID=821558) [Laden Sie Servicepack 2 für Microsoft?? SqlServer? 2014](https://go.microsoft.com/fwlink/?LinkID=821558).
-  [![SQL Server 2014 SP2 FeaturePack herunterladen](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=53164) [das SQL Server 2014 SP2 FeaturePack herunterladen](https://www.microsoft.com/en-us/download/details.aspx?id=53164).

[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP2) Enthält die folgenden Verbesserungen:

### <a name="performance-and-scalability-improvements"></a>Skalierbarkeitsverbesserungen der Leistung und 
-   **Automatische Soft-NUMA-Partitionierung:** Mit [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2, automatische Soft-NUMA wird aktiviert, wenn das Ablaufverfolgungsflag 8079 beim Starten der Instanz aktiviert ist. Wenn das Ablaufverfolgungsflag 8079 beim Start aktiviert ist [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 das hardwarelayout wird, und Konfigurieren von Soft-NUMA automatisch auf Systemen, die mindestens 8 CPUs pro NUMA-Knoten. Die automatische, soft NUMA ist Hyperthread-fähig (HT/logischer Prozessor). Durch die Partitionierung und Erstellung von weiteren Knoten wird die Hintergrundverarbeitung skaliert, indem die Anzahl von Listenern, Skalierungen sowie Netzwerk- und Verschlüsselungsfunktionen erhöht wird. Zunächst zu testen wird die Leistung-Workload mit automatischen Soft-NUMA empfohlen, bevor Sie sie in der Produktion aktivieren. [Finden Sie im Blog Informationen](https://blogs.msdn.microsoft.com/psssql/2016/03/30/sql-2016-it-just-runs-faster-automatic-soft-numa/). 
-  **Dynamic Memory Object Scaling:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 Partitionen dynamisch Arbeitsspeicher auf Grundlage von Objekten auf der Anzahl von Knoten und Kernen auf moderner Hardware zu skalieren. Das Ziel der dynamischen Promotion ist eine threadsichere Speicherobjekte (CMEMTHREAD) automatisch partitioniert, wenn es sich um einen Engpass wird. Unpartitionierte Speicherobjekte können dynamisch höher gestuft werden um anhand der Knoten (Anzahl der Partitionen gleich Anzahl von NUMA-Knoten) partitioniert werden, und Arbeitsspeicher an, die Objekte, die anhand der Knoten partitioniert durch weitere können höher gestuft, um die CPU-Nutzung (Anzahl der Partitionen gleich Anzahl der zu partitionierenden CPUs). [Finden Sie im Blog Informationen](https://blogs.msdn.microsoft.com/psssql/2016/04/06/sql-2016-it-just-runs-faster-dynamic-memory-object-cmemthread-partitioning/).
-  **MAXDOP-Hinweis für DBCC CHECK\* Befehle:** Diese Verbesserung Adressen [connect Feedback (468694)](https://connect.microsoft.com/SQLServer/feedback/details/468694/maxdop-option-in-dbcc-checkdb). Sie können nun führen Sie DBCC CHECKDB mit der eine MAXDOP-Einstellung als der Wert für Sp_configure. Wenn MAXDOP den mit Resource Governor konfigurierten Wert überschreitet, verwendet die Datenbank-Engine den in „ALTER WORKLOAD GROUP (Transact-SQL)“ beschriebenen MAXDOP-Wert von Resource Governor. Alle semantischen Regeln, die mit der Konfigurationsoption Max. Grad an Parallelität verwendet werden können, stehen beim Verwenden des MAXDOP-Abfragehinweises zur Verfügung. Weitere Informationen finden Sie unter [DBCC CHECKDB (Transact-SQL)](https://msdn.microsoft.com/library/ms176064.aspx).
-   **Aktivieren Sie > 8TB für Pufferpool:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 aktiviert 128-TB virtuellen Adressraum für die Verwendung des Pufferpools. Diese Verbesserung ermöglicht SQL Server-Pufferpools über 8 TB hinaus auf moderner Hardware zu skalieren.
-   **SOS_RWLock-Spinlock zur Verbesserung der:** Der SOS_RWLock ist ein primitiver Synchronisierungstyp, die an verschiedenen Stellen in der SQL Server-Codebasis verwendet.  Wie der Name schon sagt, kann der Code mehrere freigegebene (Leser) oder der Besitz der einzelnen (Writer) enthalten. Diese Verbesserung entfällt die Notwendigkeit für Spinlock sos_rwlock und verwendet stattdessen sperrfrei Techniken, die in-Memory-OLTP ähnelt. Mit dieser Änderung können viele Threads eine Datenstruktur, ohne dass die und dadurch erhöhte Skalierbarkeit von SOS_RWLock parallel geschützt lesen. Vor dieser Änderung haben darf die Spinlock-Implementierung nur ein Thread zum Abrufen der SOS_RWLock zu einem Zeitpunkt, sogar in einer Datenstruktur zu lesen.  [Finden Sie im Blog Informationen](https://blogs.msdn.microsoft.com/psssql/2016/04/07/sql-2016-it-just-runs-faster-sos_rwlock-redesign/).
-    **Räumliche Native Implementierung:** Erhebliche Verbesserung der Leistung der Abfrage nach räumlichen Daten wird in eingeführt [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 über native Implementierung. Weitere Informationen finden Sie unter den [Knowledge Base-Artikel KB3107399](https://support.microsoft.com/en-us/kb/3107399).

### <a name="supportability-and-diagnostics-improvements"></a>Unterstützungs- und Verbesserungen bei der Diagnose
-   **Das Klonen der Datenbank:** Klondatenbank ist ein neuer DBCC-Befehl, der verbessert die Behebung von Problemen mit bestehenden Produktionsdatenbanken Klonen das Schema und die Metadaten ohne die Daten. Der Klon erstellt wird, mit dem Befehl `DBCC clonedatabase('source_database_name', 'clone_database_name')`.  **Hinweis**: Geklonte Datenbanken dürfen nicht in Produktionsumgebungen verwendet werden. Mit dem folgenden Befehl bestimmen, ob eine Datenbank aus einer geklonten Datenbank generiert wurde: `select DATABASEPROPERTYEX('clonedb', 'isClone')`. Der Rückgabewert von **1** gibt an, die Datenbank wird erstellt, aus der Clonedatabase beim **0** gibt an, es ist dabei nicht um einen Klon.
-   **Tempdb-unterstützbarkeit:**  Eine neue Errorlog-Nachricht, die die Anzahl der Tempdb-Dateien und die Größe/für die automatische Vergrößerung von Tempdb-Datendateien vorhanden ist, beim Starten des Servers angibt.
-   **Datenbank Instant File Initialization-Protokollierung:** Eine neue Errorlog-Nachricht, die auf dem Server Statup, den Status der sofortige Datenbankdateiinitialisierung (aktiviert/deaktiviert) angibt.
-   **Modulnamen in der Aufrufliste:** Die Xevent-Aufrufliste enthält jetzt die Namen der Module "und" Offset anstelle von absoluten Adressen.
-   **Neue DMF für inkrementelle Statistiken:** Diese Verbesserung Adressen [connect Feedback (797156)](https://connect.microsoft.com/SQLServer/feedback/details/797156/display-sys-dm-db-stats-properties-per-partition-for-incremental-statistics) , ermöglichen die nachverfolgung der inkrementellen Statistiken auf Partitionsebene. Eine neue dm_db_incremental_stats_properties der DMF wird eingeführt, um Informationen pro Partition zu inkrementellen Statistiken verfügbar zu machen.
-   **Index Nutzung DMV-Verhalten wurde aktualisiert:** Diese Verbesserung Adressen [connect Feedback (739566)](https://connect.microsoft.com/SQLServer/feedback/details/739566/rebuilding-an-index-clears-stats-from-sys-dm-db-index-usage-stats) von Kunden, in dem Neuerstellen eines Indexes wird *nicht* jeder vorhandenen Zeileneintrag aus sys. dm_db_index_usage_stats für diesen Index löschen. Das Verhalten wird jetzt mit SQL 2008 und SQL Server 2016 identisch sein. [Finden Sie im Blog Informationen](https://blogs.msdn.microsoft.com/sql_server_team/index-usage-dmv-behavior-updated/).
-   **Verbesserte Korrelation zwischen XE- und DMVs:** Diese Verbesserung Adressen [connect Feedback (1934583)](https://connect.microsoft.com/SQLServer/feedback/details/1934583/extended-events-query-hash-and-query-plan-hash-data-types). Query_hash und Query_plan_hash werden verwendet, eine Abfrage um eindeutig zu identifizieren. Sie werden von der DMV als varbinary(8) und von XEvent als UINT64 definiert. Da SQLServer nicht "Unisigned Bigint" verfügt, funktioniert die Umwandlung nicht immer. Mit dieser Verbesserung werden neue Aktions- bzw. Filterspalten für XEvent eingeführt, die query_hash und query_plan_hash weitestgehend entsprechen, es sei denn, sie werden als INT64 definiert, wodurch Abfragen zwischen XE und DMV besser korreliert werden können.
-   **Unterstützung für UTF-8 in BULK INSERT und BCP:** Diese Verbesserung Adressen [connect Feedback (370419)](https://connect.microsoft.com/SQLServer/feedback/details/370419/bulk-insert-and-bcp-does-not-recognize-codepage-65001) , in denen Unterstützung für Export und Import von Daten mit Codierung im UTF-8-Zeichensatz ausgewählt werden jetzt in BULK INSERT und BCP aktiviert ist.
-   **Einfache pro-Operator Abfrage profilerstellung für die Ausführung:** Während der Problembehandlung die abfrageleistung, obwohl Showplan enthält zahlreiche Informationen auf den Ausführungsplan für Abfrage und die Kosten der Operator im Plan, aber es bietet eine eingeschränkte Informationen zu den tatsächlichen wie Laufzeitstatistiken (CPU, e/a-liest, verstrichene Zeit pro Thread). SQL 2014 SP2 führt diese zusätzliche Laufzeitstatistiken pro Operator und in der Showplan als auch ein XEvent (Query_thread_profile) bei der Problembehandlung der abfrageleistung. [Finden Sie im Blog Informationen](https://blogs.msdn.microsoft.com/sql_server_team/added-per-operator-level-performance-stats-for-query-processing/).
-   **Bereinigen der änderungsnachverfolgung:** Eine neue gespeicherte Prozedur `sp_flush_CT_internal_table_on_demand` wird eingeführt, um die Bereinigung der änderungsnachverfolgung interne Tabellen bei Bedarf.
-   **Protokollierung von AlwaysON Lease Timeout** neue Protokollierungsfunktion für Leasezeitlimit-Nachrichten hinzugefügt, sodass die aktuelle Uhrzeit und die Zeiten für die erwartete Erneuerung protokolliert werden. Außerdem wurde eine neue Nachricht in SQL Errorlog in Bezug auf die Timeouts eingeführt. [Finden Sie im Blog Informationen](https://blogs.msdn.microsoft.com/alwaysonpro/2016/02/23/improved-alwayson-availability-group-lease-timeout-diagnostics/).
-   **Neue DMF zum Abrufen von Eingabepuffer in SQL Server:** Eine neue DMF zum Abrufen des Eingabepuffers für eine Sitzung/Anforderung (sys.dm_exec_input_buffer) ist jetzt verfügbar. Diese ist funktionell äquivalent zu DBCC INPUTBUFFER. [Finden Sie im Blog Informationen](https://blogs.msdn.microsoft.com/sql_server_team/new-dmf-for-retrieving-input-buffer-in-sql-server/).
-   **Entschärfung für die arbeitsspeicherzuweisung unterschätzte und überschätzt:** Hinzugefügte neue Abfragehinweise für die Ressourcenkontrolle über MIN_GRANT_PERCENT und MAX_GRANT_PERCENT. Dadurch können Sie diese Hinweise zu nutzen, während der Ausführung von Abfragen durch deren arbeitsspeicherzuweisungen speicherzuweisungen beschränken. Weitere Informationen finden Sie unter [Knowledge Base-Artikel KB310740](https://support.microsoft.com/en-us/kb/3107401)
-   **Bessere Arbeitsspeicher Diagnose der speicherzuweisung:** Die Liste der Ablaufverfolgungsfunktionen in SQL Server (Query_memory_grant_usage) zum Nachverfolgen der speicherzuweisungen angefordert und erteilt wurde eine neue erweiterte Ereignisse hinzugefügt. Dies bietet eine bessere Ablaufverfolgungs- und Analysis-Funktionen für die Problembehandlung bei der Ausführung in Zusammenhang mit Abfragen im Zusammenhang mit der arbeitsspeicherzuweisungen. Weitere Informationen finden Sie unter [Knowledge Base-Artikel KB3107173](https://support.microsoft.com/en-us/kb/3107173).
-   **Abfrageausführungsdiagnose bei Tempdb Spill:**-Hash Warning und Sort Warnings verfügen nun über zusätzliche Spalten zum Nachverfolgen von physischen e/a-Statistiken, verwendete Speicher und betroffenen Zeilen. Wir darüber hinaus eine neue erweiterte Ereignisse von Hash_spill_details eingeführt. Nachdem Sie detaillierte Informationen für Ihre Warnungen Hash- und nachverfolgen können ([KB3107172](https://support.microsoft.com/en-us/kb/3107172)). Diese Verbesserung wird nun auch über die XML-Abfragepläne in Form von ein neues Attribut mit dem SpillToTempDbType komplexen Typ verfügbar gemacht ([KB3107400](https://support.microsoft.com/en-us/kb/3107400)). Jetzt zeigt die Arbeitstabelle Statistiken zu sortieren, legen Sie für Statistiken. .
-   **Verbesserte Diagnosefunktionen für Abfrageausführungspläne, die residual-Prädikat-pushdowns umfassen:** Die tatsächlichen gelesen Zeilen werden jetzt in die Abfrageausführungspläne zur Verbesserung der Problembehandlung der abfrageleistung gemeldet. Dies sollte die Notwendigkeit, erfassen SET STATISTICS IO separat negieren. Jetzt können Sie Informationen für ein residual-Prädikat-pushdowns in einem Abfrageplan angezeigt. Weitere Informationen finden Sie unter [Knowledge Base-Artikel KB3107397](https://support.microsoft.com/en-us/kb/3107397).


## <a name="additional-information"></a>Zusätzliche Informationen  
 [SQL Server 2014-Ressourcen](../2014-toc/books-online-for-sql-server-2014.md)  
  
 [SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/p/?linkID=296445)  
  
 [SQL Server 2014 Resource Center](https://msdn.microsoft.com/sqlserver/dn135309)  
  
 [SQLCat Web Site](https://go.microsoft.com/fwlink/p/?linkID=220963)  
  
  
