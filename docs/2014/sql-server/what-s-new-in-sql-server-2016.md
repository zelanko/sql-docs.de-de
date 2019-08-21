---
title: '&#39;Neues in SQL Server 2014 | Microsoft-Dokumentation'
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
ms.openlocfilehash: f368da503c90595624f476344724719206cdb77c
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893700"
---
# <a name="what39s-new-in-sql-server-2014"></a>&#39;Neues in SQL Server 2014
  In diesem Thema werden ausführliche Links zu neuen Funktionen [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] in zusammengefasst und Service Packs für zusammengefasst.[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 
**Probieren Sie es aus:** ![Azure Virtual Machine Small](./media/what-s-new-in-sql-server-2016/azure-virtual-machine-small.png) haben Sie ein Azure-Konto?  Wechseln Sie anschließend **[hierhin](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2014sp1EnterpriseWindowsServer2012R2)** , um einen virtuellen Computer zu starten, auf dem SQL Server 2014 Service Pack 1 (SP1) bereits installiert ist. 
  
-   [Neues &#40;Datenbank-Engine&#41;](../database-engine/whats-new-in-sql-server-2016.md)  
  
-   [Neues in Analysis Services und Business Intelligence](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services)  
  
-   [Neuigkeiten in der SQL Server-Installation](install/what-s-new-in-sql-server-installation.md)  
  
 **[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]hat keine wichtigen neuen Features für Folgendes eingeführt:**  
  
-   [Neues &#40;Integration Services&#41;](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)  
  
-   [Neues &#40;Reporting Services&#41;](../reporting-services/what-s-new-reporting-services.md)  
  
## <a name="includesssql14includessssql14-mdmd-service-pack-1-sp1"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 1 (SP1)
[!INCLUDE[ssSQL14](../includes/sssql14-md.md)](SP1) hat keine wichtigen neuen Features eingeführt.
-  [Informationen zur 2014 SQL Server Version von Service Pack 1](https://support.microsoft.com/en-us/kb/3058865).
-  [![Service Pack 1 für Microsoft herunterladen? SQL Server? ](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=46694) 2014[laden Sie Service Pack 1 für Microsoft herunter? SQL Server? 2014](https://www.microsoft.com/en-us/download/details.aspx?id=46694).


## <a name="includesssql14includessssql14-mdmd-service-pack-2-sp2"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]Service Pack 2 (SP2)
- [Informationen zur 2014 SQL Server von Service Pack 2](https://support.microsoft.com/en-us/kb/3171021).
-  [![Service Pack 2 für Microsoft herunterladen? SQL Server? ](./media/what-s-new-in-sql-server-2016/download.png)](https://go.microsoft.com/fwlink/?LinkID=821558) 2014[laden Sie Service Pack 2 für Microsoft herunter? SQL Server? 2014](https://go.microsoft.com/fwlink/?LinkID=821558).
-  [![Herunterladen des SQL Server 2014 SP2 Feature Pack](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=53164) [Laden Sie das SQL Server 2014 SP2 Feature Pack herunter](https://www.microsoft.com/en-us/download/details.aspx?id=53164).

[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2 Umfasst die folgenden Verbesserungen:

### <a name="performance-and-scalability-improvements"></a>Verbesserungen bei Leistung und Skalierbarkeit 
-   **Automatische Weiche NUMA-Partitionierung:** Bei [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 wird die automatische Weiche NUMA aktiviert, wenn das Ablaufverfolgungsflag 8079 beim Starten der Instanz aktiviert wird. Wenn das Ablaufverfolgungsflag 8079 während [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] des Starts aktiviert ist, wird das Hardware Layout von SP2 abgemeldet und Soft-NUMA automatisch auf Systemen konfiguriert, die mindestens 8 CPUs pro NUMA-Knoten melden. Das automatische, weiche NUMA-Verhalten ist Hyperthread (HT/logischer Prozessor). Durch die Partitionierung und Erstellung von weiteren Knoten wird die Hintergrundverarbeitung skaliert, indem die Anzahl von Listenern, Skalierungen sowie Netzwerk- und Verschlüsselungsfunktionen erhöht wird. Es wird empfohlen, zuerst die leistungsworkloads mit automatischer Soft-NUMA zu testen, bevor Sie Sie in die Produktionsumgebung schalten. [Weitere Informationen finden Sie im Blog](https://blogs.msdn.microsoft.com/psssql/2016/03/30/sql-2016-it-just-runs-faster-automatic-soft-numa/). 
-  **Dynamischer Arbeitsspeicher-Objekt Skalierung:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2 partitioniert Speicher Objekte dynamisch basierend auf der Anzahl von Knoten und Kernen, die auf moderner Hardware skaliert werden sollen. Das Ziel der dynamischen herauf Stufung besteht darin, ein Thread sicheres Speicher Objekt (cmemthread) automatisch zu partitionieren, wenn es zu einem Engpass wird. Nicht partitionierte Speicher Objekte können dynamisch herauf gestuft werden, um durch den Knoten partitioniert zu werden (Anzahl der Partitionen entspricht der Anzahl der NUMA-Knoten), und durch den Knoten partitionierte Speicher Objekte können weiter herauf gestuft werden, um durch die CPU partitioniert zu werden (Anzahl der Partitionen entspricht der Anzahl von CPUs). [Weitere Informationen finden Sie im Blog](https://blogs.msdn.microsoft.com/psssql/2016/04/06/sql-2016-it-just-runs-faster-dynamic-memory-object-cmemthread-partitioning/).
-  **MAXDOP-Hinweis für DBCC\* Check-Befehle:** Diese Verbesserung bezieht sich auf das [Feedback der Verbindung (468694)](https://connect.microsoft.com/SQLServer/feedback/details/468694/maxdop-option-in-dbcc-checkdb). Sie können jetzt DBCC CHECKDB mit einer anderen MAXDOP-Einstellung als dem Wert sp_configure ausführen. Wenn MAXDOP den mit Resource Governor konfigurierten Wert überschreitet, verwendet die Datenbank-Engine den in „ALTER WORKLOAD GROUP (Transact-SQL)“ beschriebenen MAXDOP-Wert von Resource Governor. Alle semantischen Regeln, die mit der Konfigurationsoption Max. Grad an Parallelität verwendet werden können, stehen beim Verwenden des MAXDOP-Abfragehinweises zur Verfügung. Weitere Informationen finden Sie unter [DBCC CHECKDB (Transact-SQL)](https://msdn.microsoft.com/library/ms176064.aspx).
-   **> 8 TB für den Puffer Pool aktivieren:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2 ermöglicht einen virtuellen Adressraum von 128 TB für die Pufferpool Verwendung. Diese Verbesserung ermöglicht SQL Server Pufferpools, auf moderner Hardware über 8 TB zu skalieren.
-   **SOS_RWLock Spinlock-Verbesserung:** SOS_RWLock ist eine Synchronisierungs primitive, die an verschiedenen Stellen in der SQL Server Codebasis verwendet wird.  Wie der Name schon sagt, kann der Code über mehrere freigegebene (Leser) oder einen einzelnen (Writer-) Besitz verfügen. Durch diese Verbesserung entfällt die Notwendigkeit von Spinlock für SOS_RWLock, und stattdessen werden Sperr freie Techniken verwendet, die mit in-Memory OLTP vergleichbar sind. Mit dieser Änderung können viele Threads eine durch SOS_RWLock geschützte Datenstruktur parallel lesen, ohne einander zu blockieren und dadurch eine größere Skalierbarkeit zu gewährleisten. Vor dieser Änderung erlaubte die Spinlock-Implementierung nur einem Thread, den SOS_RWLock zu einem Zeitpunkt zu erhalten, sogar zum Lesen einer Datenstruktur.  [Weitere Informationen finden Sie im Blog](https://blogs.msdn.microsoft.com/psssql/2016/04/07/sql-2016-it-just-runs-faster-sos_rwlock-redesign/).
-    **Räumliche Native Implementierung:** Eine deutliche Verbesserung der Leistung von räumlichen Abfragen wird [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] in SP2 durch Native Implementierung eingeführt. Weitere Informationen finden Sie im [Knowledge Base-Artikel KB3107399](https://support.microsoft.com/en-us/kb/3107399).

### <a name="supportability-and-diagnostics-improvements"></a>Verbesserungen der Unterstützung und Diagnose
-   **Daten Bank Klon Vorgang:** Clone Database ist ein neuer DBCC-Befehl, der die Problembehandlung vorhandener Produktionsdatenbanken durch Klonen des Schemas und der Metadaten ohne die Daten verbessert. Der Klon wird mit dem Befehl `DBCC clonedatabase('source_database_name', 'clone_database_name')`erstellt.  **Hinweis**: Geklonte Datenbanken dürfen nicht in Produktionsumgebungen verwendet werden. Verwenden Sie den folgenden Befehl, um zu ermitteln, ob eine Datenbank aus einer geklonten Datenbank generiert wurde: `select DATABASEPROPERTYEX('clonedb', 'isClone')`. Der Rückgabewert **1** gibt an, dass die Datenbank aus clonedatabase erstellt wird, während **0** angibt, dass es sich nicht um einen Klon handelt.
-   **Tempdb-unter Stütz barkeit:**  Eine neue Fehlerprotokoll Meldung, die die Anzahl von tempdb-Dateien und die Größe/automatische Vergrößerung von tempdb-Datendateien angibt, die beim Serverstart vorhanden sind.
-   **Daten Bank sofortige Datei Initialisierungs Protokollierung:** Eine neue ErrorLog-Meldung, die auf Serverstatus, den Status der sofortigen Datei Initialisierung der Datenbank angibt (aktiviert/deaktiviert).
-   **Modulnamen in callstack:** Die XEvent-Aufruf Liste enthält nun Module-Namen + Offset anstelle von absoluten Adressen.
-   **Neue DMF für inkrementelle Statistiken:** Diese Verbesserung bezieht sich auf das [Feedback (797156)](https://connect.microsoft.com/SQLServer/feedback/details/797156/display-sys-dm-db-stats-properties-per-partition-for-incremental-statistics) , mit dem die inkrementellen Statistiken auf Partitions Ebene nachverfolgt werden können. Ein neues DMF sys. DM _db_incremental_stats_properties wird eingeführt, um Informationen pro Partition für inkrementelle Statistiken verfügbar zu machen.
-   **DMV-Verhalten der Index Verwendung aktualisiert:** Diese Verbesserung bezieht sich auf das [Feedback (739566)](https://connect.microsoft.com/SQLServer/feedback/details/739566/rebuilding-an-index-clears-stats-from-sys-dm-db-index-usage-stats) von Kunden, bei denen das Neuerstellen eines Indexes keinen vorhandenen Zeileneintrag aus sys. DM _db_index_usage_stats für diesen Index löscht. Das Verhalten ist nun identisch mit dem in SQL 2008 und SQL Server 2016. [Weitere Informationen finden Sie im Blog](https://blogs.msdn.microsoft.com/sql_server_team/index-usage-dmv-behavior-updated/).
-   **Verbesserte Korrelation zwischen der Diagnose Xe und DMVs:** Diese Verbesserung bezieht sich auf das [Feedback der Verbindung (1934583)](https://connect.microsoft.com/SQLServer/feedback/details/1934583/extended-events-query-hash-and-query-plan-hash-data-types). Query_hash und query_plan_hash werden zum eindeutigen Identifizieren einer Abfrage verwendet. Sie werden von der DMV als varbinary(8) und von XEvent als UINT64 definiert. Da SQL Server nicht über "UNISIGNED BIGINT" verfügt, funktioniert die Umwandlung nicht immer. Mit dieser Verbesserung werden neue Aktions- bzw. Filterspalten für XEvent eingeführt, die query_hash und query_plan_hash weitestgehend entsprechen, es sei denn, sie werden als INT64 definiert, wodurch Abfragen zwischen XE und DMV besser korreliert werden können.
-   **Unterstützung für UTF-8 in BULK INSERT und bcp:** Diese Verbesserung bezieht sich auf das [Feedback (370419)](https://connect.microsoft.com/SQLServer/feedback/details/370419/bulk-insert-and-bcp-does-not-recognize-codepage-65001) , bei dem die Unterstützung für den Export und Import von Daten, die im UTF-8-Zeichensatz codiert sind, jetzt in BULK INSERT und bcp aktiviert
-   **Vereinfachte Profilerstellung für die Abfrage Ausführung pro Operator:** Bei der Problembehandlung der Abfrageleistung bietet Showplan zwar viele Informationen zum Abfrage Ausführungsplan und den Kosten des Operators im Plan, aber es sind nur eingeschränkte Informationen zu tatsächlichen Lauf Zeit Statistiken wie (CPU, e/a-Lesevorgänge, verstrichene Zeit pro Thread) enthalten. SQL 2014 SP2 führt diese zusätzlichen Lauf Zeit Statistiken pro Operator im Showplan sowie ein XEvent (query_thread_profile) ein, um die Problembehandlung bei der Abfrageleistung zu unterstützen. [Weitere Informationen finden Sie im Blog](https://blogs.msdn.microsoft.com/sql_server_team/added-per-operator-level-performance-stats-for-query-processing/).
-   **Änderungsnachverfolgung Bereinigung:** Eine neue gespeicherte Prozedur `sp_flush_CT_internal_table_on_demand` wird eingeführt, um bei Bedarf die internen Tabellen für die Änderungs Nachverfolgung zu bereinigen.
-   **AlwaysOn-Lease-Timeout Protokollierung** Es wurde eine neue Protokollierungsfunktion für Lease-Timeout-Nachrichten hinzugefügt, sodass die aktuelle Uhrzeit und die erwarteten Erneuerungs Zeiten protokolliert werden. Außerdem wurde eine neue Nachricht im SQL-Fehlerprotokoll für die Timeouts eingeführt. [Weitere Informationen finden Sie im Blog](https://blogs.msdn.microsoft.com/alwaysonpro/2016/02/23/improved-alwayson-availability-group-lease-timeout-diagnostics/).
-   **Neues DMF zum Abrufen des Eingabe Puffers in SQL Server:** Eine neue DMF zum Abrufen des Eingabepuffers für eine Sitzung/Anforderung (sys.dm_exec_input_buffer) ist jetzt verfügbar. Diese ist funktionell äquivalent zu DBCC INPUTBUFFER. [Weitere Informationen finden Sie im Blog](https://blogs.msdn.microsoft.com/sql_server_team/new-dmf-for-retrieving-input-buffer-in-sql-server/).
-   **Entschärfung für unterschätzende und überschätzte Speicherzuweisung:** Neue Abfrage Hinweise für Resource Governor über MIN_GRANT_PERCENT und MAX_GRANT_PERCENT hinzugefügt. Dies ermöglicht es Ihnen, diese Hinweise während der Ausführung von Abfragen zu nutzen, indem Sie Ihre Arbeitsspeicher Zuweisungen zum Verhindern von Arbeitsspeicher Konflikten durchführen Weitere Informationen finden Sie im [Knowledge Base-Artikel KB310740](https://support.microsoft.com/en-us/kb/3107401)
-   **Bessere Speicherzuweisung und Verwendungs Diagnose:** Der Liste der Ablauf Verfolgungs Funktionen in SQL Server (query_memory_grant_usage) wurde ein neues erweitertes Ereignis hinzugefügt, um die angeforderten und gewährten Arbeitsspeicher Zuweisungen nachzuverfolgen. Dies bietet bessere Ablauf Verfolgungs-und Analysefunktionen für die Behandlung von Problemen bei der Abfrage Ausführung im Zusammenhang mit Speicherzuweisungen Weitere Informationen finden Sie im [Knowledge Base-Artikel KB3107173](https://support.microsoft.com/en-us/kb/3107173).
-   **Abfrage Ausführungs Diagnose für tempdb-Überlauf:** -Hash Warnung und Sortier Warnungen verfügen jetzt über zusätzliche Spalten zum Nachverfolgen physischer e/a-Statistiken, von verwendeter Arbeitsspeicher und der betroffenen Zeilen. Wir haben auch ein neues erweitertes hash_spill_details-Ereignis eingeführt. Nun können Sie genauere Informationen zu ihren Hash-und Sortier Warnungen ([KB3107172](https://support.microsoft.com/en-us/kb/3107172)) verfolgen. Diese Verbesserung wird nun auch über die XML Query Pläne in Form eines neuen Attributs für den komplexen spillytempdbtype-Typ ([KB3107400](https://support.microsoft.com/en-us/kb/3107400)) verfügbar gemacht. Set Statistics on zeigt nun Arbeits Tabellenstatistiken sortieren an. .
-   **Verbesserte Diagnose für Abfrage Ausführungspläne, die Rest-Prädikat Weitergabe einschließen:** Die tatsächlich gelesenen Zeilen werden nun in den Abfrage Ausführungsplänen gemeldet, um die Problembehandlung bei der Abfrageleistung zu verbessern. Dies sollte die Notwendigkeit zum separaten erfassen von SET STATISTICS IO nicht trennen. Dadurch können Sie nun Informationen im Zusammenhang mit einer Rest-Prädikat Weitergabe in einem Abfrageplan anzeigen. Weitere Informationen finden Sie im [Knowledge Base-Artikel KB3107397](https://support.microsoft.com/en-us/kb/3107397).


## <a name="additional-information"></a>Zusätzliche Informationen  
 [SQL Server 2014-Ressourcen](../2014-toc/books-online-for-sql-server-2014.md)  
  
 [SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/p/?linkID=296445)  
  
 [SQL Server 2014-Ressourcen Center](https://msdn.microsoft.com/sqlserver/dn135309)  
  
 [SQLCAT-Website](https://go.microsoft.com/fwlink/p/?linkID=220963)  
  
  
