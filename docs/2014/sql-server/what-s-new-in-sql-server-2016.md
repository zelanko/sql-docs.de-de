---
title: Was&#39;s neu in SQLServer 2014 | Microsoft Docs
ms.custom: ''
ms.date: 05/25/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- database-engine
- integration-services
- master-data-services
- replication
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- new features [SQL Server]
- SQL Server, what's new
- SQL Server 2008 what's new
- what's new [SQL Server]
- sql server 2014 sp1
- sql server 2014 sp2
ms.assetid: 6a428023-e3cc-4626-a88a-4c13ccbd7db0
caps.latest.revision: 70
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9144eeb653649e36cfed3551e4ec465d403ffdcb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050694"
---
# <a name="what39s-new-in-sql-server-2014"></a>Was&#39;s neu in SQLServer 2014
  Dieses Thema fasst zusammen, ausführliche Links zu neuen Funktionen in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] und Service Packs für zusammengefasst [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 
**Probieren Sie es aus:** ![Azure Virtual Machine, klein](./media/what-s-new-in-sql-server-2016/azure-virtual-machine-small.png) haben ein Azure-Konto?  Wechseln Sie anschließend **[hierhin](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2014sp1EnterpriseWindowsServer2012R2)** , um einen virtuellen Computer zu starten, auf dem SQL Server 2014 Service Pack 1 (SP1) bereits installiert ist. 
  
-   [Neues &#40;-Datenbankmodul&#41;](../database-engine/whats-new-in-sql-server-2016.md)  
  
-   [Neuigkeiten in Analysis Services und Business Intelligence](../analysis-services/what-s-new-in-analysis-services.md)  
  
-   [Neuigkeiten in der SQL Server-Installation](install/what-s-new-in-sql-server-installation.md)  
  
 **[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Die folgende wurde nicht wichtige neue Features eingeführt werden:**  
  
-   [Neues &#40;Integrationsservices&#41;](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)  
  
-   [Neues &#40;Replikation&#41;](../relational-databases/replication/what-s-new-replication.md)  
  
-   [Neues &#40;Reporting Services&#41;](../reporting-services/what-s-new-reporting-services.md)  
  
## <a name="includesssql14includessssql14-mdmd-service-pack-1-sp1"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 1 (SP1)
[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP1) nicht wichtige neue Features eingeführt.
-  [Versionsinformationen zu SQL Server 2014 Service Pack 1 ](https://support.microsoft.com/en-us/kb/3058865).
-  [![Servicepack 1 für Microsoft® SQL Server® 2014 herunterladen](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=46694) [Servicepack 1 für Microsoft® SQL Server® 2014 herunterladen](https://www.microsoft.com/en-us/download/details.aspx?id=46694).


## <a name="includesssql14includessssql14-mdmd-service-pack-2-sp2"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Servicepack 2 (SP2)
- [Versionsinformationen zu SQL Server 2014 Service Pack 2](https://support.microsoft.com/en-us/kb/3171021).
-  [![Servicepack 2 für Microsoft® SQL Server® 2014 herunterladen](./media/what-s-new-in-sql-server-2016/download.png)](http://go.microsoft.com/fwlink/?LinkID=821558) [Servicepack 2 für Microsoft® SQL Server® 2014 herunterladen](http://go.microsoft.com/fwlink/?LinkID=821558).
-  [![SQL Server 2014 SP2 Feature Pack herunterladen](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=53164) [das SQL Server 2014 SP2 Feature Pack herunterladen](https://www.microsoft.com/en-us/download/details.aspx?id=53164).

[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP2) Bietet die folgenden Verbesserungen:

### <a name="performance-and-scalability-improvements"></a>Leistung und Skalierbarkeitsverbesserungen 
-   **Automatische Soft-NUMA-Partitionierung:** mit [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2, automatische Soft-NUMA wird aktiviert, wenn während des Starts der Instanz der Trace Flag 8079 eingeschaltet ist. Wenn die Trace Flag 8079 während des Starts aktiviert ist [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 wird das Layout Hardware abzufragen und konfigurieren Sie Soft-NUMA automatisch auf Systemen, die mindestens 8 CPUs pro NUMA-Knoten reporting. Das automatische, soft-NUMA-Verhalten ist Hyperthread (HT/logischen Prozessor) beachten. Durch die Partitionierung und Erstellung von weiteren Knoten wird die Hintergrundverarbeitung skaliert, indem die Anzahl von Listenern, Skalierungen sowie Netzwerk- und Verschlüsselungsfunktionen erhöht wird. Es wird zum ersten Test die Performance-arbeitsauslastung mit automatischen Soft-NUMA empfohlen vor dem Aktivieren sie in der Produktion. [Finden Sie im Blog Informationen](https://blogs.msdn.microsoft.com/psssql/2016/03/30/sql-2016-it-just-runs-faster-automatic-soft-numa/). 
-  **Dynamische Skalierung für die Speicher-Objekt:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 dynamisch basierend auf der Anzahl von Knoten und Kerne, die für die Skalierung auf moderner Hardware Speicherobjekte partitioniert. Das Ziel des dynamischen heraufstufung wird automatisch ein Thread-sichere Speicherobjekt (CMEMTHREAD) partitioniert, wenn es sich um einen Engpass wird. Unpartitionierte Speicherobjekte können dynamisch heraufgestuft werden, um nach Knoten (Anzahl der Partitionen gleich Anzahl von NUMA-Knoten) partitioniert werden, und Arbeitsspeicher an, die Objekte, die von Knoten partitioniert durch weitere können höher gestuft, um CPU-Nutzung (Anzahl der Partitionen gleich Anzahl der zu partitionierenden CPUs). [Finden Sie im Blog Informationen](https://blogs.msdn.microsoft.com/psssql/2016/04/06/sql-2016-it-just-runs-faster-dynamic-memory-object-cmemthread-partitioning/).
-  **MAXDOP-Hinweis für DBCC CHECK\* Befehle:** dieser Verbesserung Adressen [verbinden Feedback (468694)](https://connect.microsoft.com/SQLServer/feedback/details/468694/maxdop-option-in-dbcc-checkdb). Sie können jetzt führen Sie DBCC CHECKDB mit der eine MAXDOP-Einstellung als der Wert für Sp_configure. Wenn MAXDOP den mit Resource Governor konfigurierten Wert überschreitet, verwendet die Datenbank-Engine den in „ALTER WORKLOAD GROUP (Transact-SQL)“ beschriebenen MAXDOP-Wert von Resource Governor. Alle semantischen Regeln, die mit der Konfigurationsoption Max. Grad an Parallelität verwendet werden können, stehen beim Verwenden des MAXDOP-Abfragehinweises zur Verfügung. Weitere Informationen finden Sie unter [DBCC CHECKDB (Transact-SQL)](https://msdn.microsoft.com/library/ms176064.aspx).
-   **Aktivieren Sie > 8TB für den Pufferpool:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 ermöglicht 128 TB des virtuellen Adressraums für die Nutzung des Arbeitsthreadpools Puffer. Diese Verbesserung ermöglicht SQL Server-Pufferpool über 8 TB bei moderner Hardware skaliert.
-   **SOS_RWLock Spinlock Verbesserung:** der SOS_RWLock ist eine Synchronisierungsprimitive an verschiedenen Orten im gesamten Code von SQL Server verwendet.  Wie der Name schon sagt, kann der Code mehrere freigegebene (Leser) oder der Besitz der einzelnen (Writer) enthalten. Diese Verbesserung beseitigt die Notwendigkeit für Spinlock SOS_RWLock und verwendet stattdessen sperrenfreie Techniken, die in-Memory-OLTP ähnelt. Durch diese Änderung können viele Threads eine Datenstruktur, geschützt durch SOS_RWLock parallel ohne gegenseitig blockieren, und bietet somit eine bessere Skalierbarkeit lesen. Vor dieser Änderung zulässig Spinlock-Implementierung nur ein Thread beim Abrufen der SOS_RWLock gleichzeitig auch die Datenstruktur zu lesen.  [Finden Sie im Blog Informationen](https://blogs.msdn.microsoft.com/psssql/2016/04/07/sql-2016-it-just-runs-faster-sos_rwlock-redesign/).
-    **Räumliche systemeigene Implementierung:** erhebliche Verbesserung der Leistung der Abfrage nach räumlichen Daten wird in eingeführt [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 über systemeigene Implementierung. Weitere Informationen finden Sie unter der [Knowledge Base-Artikel KB3107399](https://support.microsoft.com/en-us/kb/3107399).

### <a name="supportability-and-diagnostics-improvements"></a>Hinsichtlich der unterstützbarkeit und Verbesserungen der Diagnose
-   **Datenbank beim Klonen des Domänencontrollers:** klondatenbank ist ein neuer DBCC-Befehl, die Behebung von Problemen mit vorhandenen Produktionsdatenbanken Klonen das Schema und die Metadaten ohne die Daten verbessert. Der Klon wird erstellt, mit dem Befehl `DBCC clonedatabase(‘source_database_name’, ‘clone_database_name’)`.  **Hinweis:** Cloned Datenbanken sollten nicht in produktionsumgebungen verwendet werden. Verwenden Sie den folgenden Befehl bestimmen, ob eine Datenbank aus einer geklonten Datenbank generiert wurde: `select DATABASEPROPERTYEX('clonedb', 'isClone')`. Der Rückgabewert der **1** gibt an, die Datenbank wird erstellt, aus der Clonedatabase beim **0** gibt an, es ist dabei nicht um einen Klon.
-   **Tempdb-unterstützbarkeit:** eine neue Errorlog-Nachricht, die die Anzahl der Tempdb-Dateien und der Größe/die automatische Vergrößerung der Tempdb-Daten weisen darauf hin Dateien beim Serverstart vorhanden.
-   **Datenbank Instant Datei Initialisierung Protokollierung:** eine neue Errorlog-Nachricht, die auf dem Server Statup, den Status des Datenbankdateiinitialisierung (aktiviert/deaktiviert) angibt.
-   **Modulnamen in der Aufrufliste:** der Xevent-Aufrufliste enthält jetzt Module Namen + Offset anstelle von absoluten Adressen.
-   **Neue DMF für inkrementelle Statistiken:** dieser Verbesserung Adressen [Feedback (797156) verbinden](https://connect.microsoft.com/SQLServer/feedback/details/797156/display-sys-dm-db-stats-properties-per-partition-for-incremental-statistics) So aktivieren Sie die inkrementellen Statistiken auf Partitionsebene nachverfolgen. Eine neue DMF sys.dm_db_incremental_stats_properties wurde eingeführt, um Informationen pro Partition für das inkrementelle Statistiken verfügbar zu machen.
-   **Index Nutzung DMV Verhalten aktualisiert:** dieser Verbesserung Adressen [verbinden Feedback (739566)](https://connect.microsoft.com/SQLServer/feedback/details/739566/rebuilding-an-index-clears-stats-from-sys-dm-db-index-usage-stats) von Kunden, wo beim Neuerstellen eines Indexes wird *nicht* deaktivieren Sie alle vorhandenen Zeileneintrag aus sys.dm_db _index_usage_stats für diesen Index. Das Verhalten wird jetzt in SQL 2008 und SQL Server 2016 identisch sein. [Finden Sie im Blog Informationen](https://blogs.msdn.microsoft.com/sql_server_team/index-usage-dmv-behavior-updated/).
-   **Verbesserte Korrelation zwischen XE-Diagnose und DMVs:** dieser Verbesserung Adressen [verbinden Feedback (1934583)](https://connect.microsoft.com/SQLServer/feedback/details/1934583/extended-events-query-hash-and-query-plan-hash-data-types). Query_hash und Query_plan_hash dienen zum Identifizieren von einer Abfrage eindeutig. Sie werden von der DMV als varbinary(8) und von XEvent als UINT64 definiert. Seit SQLServer keine "Unisigned Bigint", wird die Umwandlung ist nicht immer möglich. Mit dieser Verbesserung werden neue Aktions- bzw. Filterspalten für XEvent eingeführt, die query_hash und query_plan_hash weitestgehend entsprechen, es sei denn, sie werden als INT64 definiert, wodurch Abfragen zwischen XE und DMV besser korreliert werden können.
-   **Unterstützung für UTF-8 in BULK INSERT und BCP:** dieser Verbesserung Adressen [verbinden Feedback (370419)](https://connect.microsoft.com/SQLServer/feedback/details/370419/bulk-insert-and-bcp-does-not-recognize-codepage-65001) , Unterstützung für das Exportieren und Importieren von Daten in UTF-8-Zeichensatz codiert sind jetzt in BULK INSERT und BCP aktiviert ist.
-   **Profilerstellung für einfache pro-Operator Abfrage Ausführung:** bei der Behebung von Query Performance, obwohl Showplan zahlreiche Informationen auf den Ausführungsplan für Abfrage und die Kosten des Operators im Plan enthält, aber sie Informationen zu tatsächlichen eingeschränkte bieten Laufzeitstatistiken wie (CPU, e/a-Lesevorgänge, verstrichene Zeit pro Thread). SQL 2014 SP2 werden diese zusätzlichen Laufzeitstatistiken pro Operator und in der Showplan als auch ein XEvent (Query_thread_profile) bei der Problembehandlung bei abfrageleistung eingeführt. [Finden Sie im Blog Informationen](https://blogs.msdn.microsoft.com/sql_server_team/added-per-operator-level-performance-stats-for-query-processing/).
-   **Change Tracking-Cleanup:** eine neue gespeicherte Prozedur `sp_flush_CT_internal_table_on_demand` Cleanup änderungsnachverfolgungstabellen interne bedarfsgesteuert eingeführt wird.
-   **AlwaysON Lease Timeout Protokollierung** neuen Protokollierungsfunktionen für LeaseTimeout Nachrichten hinzugefügt, damit, dass die erwarteten Erneuerung und die aktuelle Uhrzeit protokolliert werden. Außerdem wurde eine neue Nachricht in SQL Errorlog bezüglich der Timeouts eingeführt. [Finden Sie im Blog Informationen](https://blogs.msdn.microsoft.com/alwaysonpro/2016/02/23/improved-alwayson-availability-group-lease-timeout-diagnostics/).
-   **Neue DMF zum Abrufen von Eingabepuffer in SQL Server:** eine neue DMF zum Abrufen des Eingabepuffers für eine Sitzung/Anforderung (sys. dm_exec_input_buffer) jetzt verfügbar ist. Diese ist funktionell äquivalent zu DBCC INPUTBUFFER. [Finden Sie im Blog Informationen](https://blogs.msdn.microsoft.com/sql_server_team/new-dmf-for-retrieving-input-buffer-in-sql-server/).
-   **Zur Risikominderung für unterschätzte und overestimated arbeitsspeicherzuweisung:** neue Abfragehinweise-für die Ressourcenkontrolle über MIN_GRANT_PERCENT und MAX_GRANT_PERCENT hinzugefügt. Dadurch können Sie diese Hinweise zu nutzen, während der Ausführung von Abfragen durch deren arbeitsspeicherzuweisungen, um zu verhindern, dass der Arbeitsspeicher zu beschränken. Weitere Informationen finden Sie unter [Knowledge Base-Artikel KB310740](https://support.microsoft.com/en-us/kb/3107401)
-   **Grant/Verwendung Speicherdiagnose zu einer besseren:** eine neue erweiterte Ereignisse wurde der Liste hinzugefügt Tracing-Funktionen in SQL Server (Query_memory_grant_usage) zum Nachverfolgen von arbeitsspeicherzuweisungen angefordert und erteilt. Dies bietet eine bessere und die Ablaufverfolgung und Analysefunktionen für die Problembehandlung bei Ausführung in Zusammenhang mit Abfragen im Zusammenhang mit arbeitsspeicherzuweisungen. Weitere Informationen finden Sie unter [Knowledge Base-Artikel KB3107173](https://support.microsoft.com/en-us/kb/3107173).
-   **Abfragen die Ausführung Diagnose für Tempdb-Überlauf:**-Hash Warning und Sort Warnings verfügen jetzt über zusätzliche Spalten zum Nachverfolgen von physischen e/a-Statistiken, Speicherverbrauch und betroffenen Zeilen. Darüber hinaus wurde ein neues erweiterte Hash_spill_details-Ereignis. Nun zum Nachverfolgen von Informationen mit höherer Granularität für die Warnungen Hash und sortieren ([KB3107172](https://support.microsoft.com/en-us/kb/3107172)). Diese Verbesserung ist jetzt auch über die XML-Abfragepläne in Form eines neuen Attributs SpillToTempDbType komplexen Typ verfügbar gemacht ([KB3107400](https://support.microsoft.com/en-us/kb/3107400)). Legen Sie Statistiken für jetzt zeigt Arbeitstabelle Statistiken sortieren. zugreifen.
-   **Verbesserte Diagnose für Abfrageausführungspläne, die residual prädikatweitergabe umfassen:** der tatsächlichen gelesenen Zeilen werden jetzt in die Abfrageausführungspläne zur Verbesserung von Leistungsproblemen gemeldet werden. Dies sollte die Notwendigkeit, erfassen SET STATISTICS IO separat negieren. Nun können Sie Informationen im Zusammenhang mit einem residual prädikatweitergabe in einem Abfrageplan finden Sie unter. Weitere Informationen finden Sie unter [Knowledge Base-Artikel KB3107397](https://support.microsoft.com/en-us/kb/3107397).


## <a name="additional-information"></a>Zusätzliche Informationen  
 [SQL Server 2014-Ressourcen](../2014-toc/books-online-for-sql-server-2014.md)  
  
 [SQL Server 2014 Release Notes](http://go.microsoft.com/fwlink/p/?linkID=296445)  
  
 [SQL Server 2014-Ressourcencenter](http://msdn.microsoft.com/sqlserver/dn135309)  
  
 [SQLCat-Website](http://go.microsoft.com/fwlink/p/?linkID=220963)  
  
  