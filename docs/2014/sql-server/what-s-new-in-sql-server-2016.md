---
title: Neues in SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/10/2019
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: dfee15f0f8b657074bab4104edb4833bd8e2f05f
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2020
ms.locfileid: "83001063"
---
# <a name="whats-new-in-sql-server-2014"></a>Neuerungen in SQL Server 2014

In diesem Thema werden ausführliche Links zu neuen Funktionen in zusammengefasst [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] und Service Packs für zusammengefasst.[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 
**Probieren Sie es aus:** ![ Azure Virtual Machine Small ](./media/what-s-new-in-sql-server-2016/azure-virtual-machine-small.png) haben Sie ein Azure-Konto?  Wechseln Sie zu https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2014sp1EnterpriseWindowsServer2012R2 , um einen virtuellen Computer zu starten, auf dem SQL Server 2014 Service Pack 1 (SP1) bereits installiert ist.

> [!TIP]
> [Klicken Sie hier](../2014-toc/index.yml) , um die Dokumentationsseite zu Home von SQL Server 2014.

<!--
Do not let this file's filename fool you.
This filename contains "2016", but nevertheless...
This file, at this exact GitHub path, is dedicated to SQL Server version 2014.
-->

## <a name="whats-new-articles"></a>Neuerungen in Artikeln

-   [Neues &#40;Datenbank-Engine&#41;](../database-engine/whats-new-in-sql-server-2016.md)  
  
-   [Neues in Analysis Services und Business Intelligence](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services)  
  
-   [Neuigkeiten in der SQL Server-Installation](install/what-s-new-in-sql-server-installation.md)  
  
 **[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]hat keine wichtigen neuen Features für die folgenden Funktionen eingeführt:**  
  
-   [Neues &#40;Integration Services&#41;](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)  
  
-   [Neues &#40;Reporting Services&#41;](../reporting-services/what-s-new-reporting-services.md)  
  
## <a name="sssql14-service-pack-1-sp1"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Service Pack 1 (SP1)
[!INCLUDE[ssSQL14](../includes/sssql14-md.md)](SP1) hat keine wichtigen neuen Features eingeführt.
-  [Informationen zur 2014 SQL Server Version von Service Pack 1](https://support.microsoft.com/kb/3058865).
-  [ ![ Laden Sie Service Pack 1 für Microsoft SQL Server 2014](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/download/details.aspx?id=46694) [Download Service Pack 1 für Microsoft SQL Server 2014](https://www.microsoft.com/download/details.aspx?id=46694)herunter.


## <a name="sssql14-service-pack-2-sp2"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]Service Pack 2 (SP2)
- [Informationen zur 2014 SQL Server von Service Pack 2](https://support.microsoft.com/kb/3171021).
-  [ ![ Laden Sie Service Pack 2 für Microsoft SQL Server 2014](./media/what-s-new-in-sql-server-2016/download.png)](https://go.microsoft.com/fwlink/?LinkID=821558) [Download Service Pack 2 für Microsoft SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=821558)herunter.
-  [ ![ Download SQL Server 2014 SP2 Feature Pack](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/download/details.aspx?id=53164) [Laden Sie das SQL Server 2014 SP2 Feature Pack herunter](https://www.microsoft.com/download/details.aspx?id=53164).

[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2 Umfasst die folgenden Verbesserungen:

### <a name="performance-and-scalability-improvements"></a>Verbesserungen bei Leistung und Skalierbarkeit 
-   **Automatische weiche NUMA-Partitionierung:** Bei [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 wird die automatische Weiche NUMA aktiviert, wenn das Ablaufverfolgungsflag 8079 beim Starten der Instanz aktiviert wird. Wenn das Ablaufverfolgungsflag 8079 während des Starts aktiviert ist, [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] wird das Hardware Layout von SP2 abgemeldet und Soft-NUMA automatisch auf Systemen konfiguriert, die mindestens 8 CPUs pro NUMA-Knoten melden. Das automatische, weiche NUMA-Verhalten ist Hyperthread (HT/logischer Prozessor). Durch die Partitionierung und Erstellung von weiteren Knoten wird die Hintergrundverarbeitung skaliert, indem die Anzahl von Listenern, Skalierungen sowie Netzwerk- und Verschlüsselungsfunktionen erhöht wird. Es wird empfohlen, dass Sie zunächst die Leistungsauslastung mit automatischer Soft-NUMA testen, bevor Sie Sie in der Produktionsumgebung optimieren. [Weitere Informationen finden Sie im Blog](https://blogs.msdn.microsoft.com/psssql/2016/03/30/sql-2016-it-just-runs-faster-automatic-soft-numa/). 
-  **Dynamischer Arbeitsspeicher-Objekt Skalierung:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 partitioniert Speicher Objekte dynamisch basierend auf der Anzahl von Knoten und Kernen, die auf moderner Hardware skaliert werden sollen. Das Ziel der dynamischen herauf Stufung besteht darin, ein Thread sicheres Speicher Objekt (cmemthread) automatisch zu partitionieren, wenn es zu einem Engpass wird. Nicht partitionierte Speicher Objekte können dynamisch nach Knoten partitioniert werden (Anzahl der Partitionen ist mit der Anzahl der NUMA-Knoten). Durch den Knoten partitionierte Speicher Objekte können durch die CPU weiter partitioniert werden (Anzahl der Partitionen ist größer als die Anzahl der CPUs). [Weitere Informationen finden Sie im Blog](https://blogs.msdn.microsoft.com/psssql/2016/04/06/sql-2016-it-just-runs-faster-dynamic-memory-object-cmemthread-partitioning/).
-  **MAXDOP-Hinweis für DBCC CHECK- \* Befehle:** bei dieser Verbesserung wird das Feedback zur Verbindungs Herstellung angezeigt [(468694)](https://connect.microsoft.com/SQLServer/feedback/details/468694/maxdop-option-in-dbcc-checkdb). Sie können jetzt DBCC CHECKDB mit einer anderen MAXDOP-Einstellung als dem sp_configure Wert ausführen. Wenn MAXDOP den mit Resource Governor konfigurierten Wert überschreitet, verwendet die Datenbank-Engine den in „ALTER WORKLOAD GROUP (Transact-SQL)“ beschriebenen MAXDOP-Wert von Resource Governor. Alle semantischen Regeln, die mit der Konfigurationsoption Max. Grad an Parallelität verwendet werden können, stehen beim Verwenden des MAXDOP-Abfragehinweises zur Verfügung. Weitere Informationen finden Sie unter [DBCC CHECKDB (Transact-SQL)](https://msdn.microsoft.com/library/ms176064.aspx).
-   **>8 TB für den Puffer Pool aktivieren:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 ermöglicht 128 TB virtuellen Adressraum für die Pufferpool Verwendung. Diese Verbesserung ermöglicht SQL Server Pufferpools, auf moderner Hardware über 8 TB zu skalieren.
-   **SOS_RWLock Spinlock-Verbesserung:** Der SOS_RWLock ist eine Synchronisierungs primitive, die an verschiedenen Stellen in der SQL Server Codebasis verwendet wird.  Wie der Name schon sagt, kann der Code über mehrere freigegebene (Leser) oder einen einzelnen (Writer-) Besitz verfügen. Durch diese Verbesserung entfällt die Notwendigkeit von Spinlock für SOS_RWLock, und stattdessen werden Sperr freie Techniken verwendet, ähnlich wie in-Memory OLTP. Mit dieser Änderung können viele Threads eine Datenstruktur, die durch SOS_RWLock parallel geschützt ist, lesen, ohne einander zu blockieren. Diese Parallelisierung bietet eine bessere Skalierbarkeit. Vor dieser Änderung erlaubte die Spinlock-Implementierung nur einem Thread, den SOS_RWLock gleichzeitig zu erhalten, sogar zum Lesen einer Datenstruktur. [Weitere Informationen finden Sie im Blog](https://blogs.msdn.microsoft.com/psssql/2016/04/07/sql-2016-it-just-runs-faster-sos_rwlock-redesign/).
-    **Räumliche Native Implementierung:** Eine deutliche Verbesserung der Leistung von räumlichen Abfragen wird in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 durch Native Implementierung eingeführt. Weitere Informationen finden Sie im [Knowledge Base-Artikel KB3107399](https://support.microsoft.com/kb/3107399).

### <a name="supportability-and-diagnostics-improvements"></a>Verbesserungen der Unterstützung und Diagnose
-   **Daten Bank Klon Vorgang:** Clone Database ist ein neuer DBCC-Befehl, der die Problembehandlung vorhandener Produktionsdatenbanken durch Klonen des Schemas und der Metadaten ohne die Daten verbessert. Der Klon wird mit dem Befehl erstellt `DBCC clonedatabase('source_database_name', 'clone_database_name')` .  **Hinweis:** Geklonte Datenbanken sollten nicht in Produktionsumgebungen verwendet werden. Verwenden Sie den folgenden Befehl, um zu ermitteln, ob eine Datenbank aus einer geklonten Datenbank generiert wurde: `select DATABASEPROPERTYEX('clonedb', 'isClone')` . Der Rückgabewert **1** gibt an, dass die Datenbank aus clonedatabase erstellt wird, während **0** angibt, dass es sich nicht um einen Klon handelt.
-   **Tempdb** -unter Stütz barkeit:  Eine neue Fehlerprotokoll Meldung, die angibt, dass beim Start sowohl die Anzahl der tempdb-Dateien als auch die Größe und die automatische Vergrößerung der tempdb-Datendateien angezeigt werden.
-   **Daten Bank sofortige Datei Initialisierungs Protokollierung:** Eine neue Fehlerprotokoll Meldung, die beim Serverstart den Status der sofortigen Datei Initialisierung der Datenbank angibt (aktiviert/deaktiviert).
-   **Modulnamen in callstack:** Der Aufruf Stapel für erweiterte Ereignisse (XEvent) enthält jetzt anstelle von absoluten Adressen Module-Namen plus Offset.
-   **Neue DMF für inkrementelle Statistiken:** Diese Verbesserung bezieht sich auf das [Feedback (797156)](https://connect.microsoft.com/SQLServer/feedback/details/797156/display-sys-dm-db-stats-properties-per-partition-for-incremental-statistics) , mit dem die inkrementellen Statistiken auf Partitions Ebene nachverfolgt werden können. Ein neues DMF sys. dm_db_incremental_stats_properties wird eingeführt, um Informationen pro Partition für inkrementelle Statistiken verfügbar zu machen.
-   **DMV-Verhalten der Index Verwendung aktualisiert:** Diese Verbesserung bezieht sich auf das [Feedback (739566)](https://connect.microsoft.com/SQLServer/feedback/details/739566/rebuilding-an-index-clears-stats-from-sys-dm-db-index-usage-stats) von Kunden, bei denen das Neuerstellen eines *Indexes keinen vorhandenen* Zeileneintrag aus sys. dm_db_index_usage_stats für diesen Index löscht. Das Verhalten ist nun identisch mit dem in SQL 2008 und SQL Server 2016. [Weitere Informationen finden Sie im Blog](https://blogs.msdn.microsoft.com/sql_server_team/index-usage-dmv-behavior-updated/).
-   **Verbesserte Korrelation zwischen der Diagnose Xe und DMVs:** Diese Verbesserung bezieht sich auf das [Feedback der Verbindung (1934583)](https://connect.microsoft.com/SQLServer/feedback/details/1934583/extended-events-query-hash-and-query-plan-hash-data-types). `Query_hash`und `query_plan_hash` werden zum eindeutigen Identifizieren einer Abfrage verwendet. Sie werden von der DMV als varbinary(8) und von XEvent als UINT64 definiert. Da SQL Server nicht über "unsigned bigint" verfügt, funktioniert die Umwandlung nicht immer. Diese Verbesserung führt neue XEvent-Aktions-und Filter Spalten ein. Die Spalten entsprechen `query_hash` und `query_plan_hash` , es sei denn, Sie sind als Int64 definiert. Mit der Int64-Definition können Sie Abfragen zwischen Xe und DMVs korrelieren.
-   **Unterstützung für UTF-8 in BULK INSERT und bcp:** Diese Verbesserung bezieht sich auf das [Feedback der Verbindung (370419)](https://connect.microsoft.com/SQLServer/feedback/details/370419/bulk-insert-and-bcp-does-not-recognize-codepage-65001). BULK INSERT und bcp können jetzt Daten exportieren oder importieren, die im UTF-8-Zeichensatz codiert sind.
-   **Lightweight-Profilerstellung für die Abfrage Ausführung pro Operator:** Showplan enthält Informationen zu den Kosten der einzelnen Operatoren im Plan. Tatsächlich sind die tatsächlichen Lauf Zeit Statistiken jedoch für Dinge wie CPU, e/a-Lesevorgänge und verstrichene Zeit pro Thread beschränkt. SQL Server 2014 SP2 führt diese zusätzlichen Lauf Zeit Statistiken pro Operator im Showplan ein. R2 führt auch ein XEvent namens ein `query_thread_profile` , um die Problembehandlung bei der Abfrageleistung zu unterstützen. [Weitere Informationen finden Sie im Blog](https://blogs.msdn.microsoft.com/sql_server_team/added-per-operator-level-performance-stats-for-query-processing/).
-   **Änderungsnachverfolgung Bereinigung:** Eine neue gespeicherte Prozedur `sp_flush_CT_internal_table_on_demand` wird eingeführt, um die internen Änderungs nach Verfolgungs Tabellen zu bereinigen.
-   **AlwaysOn-Lease-Timeout Protokollierung** Es wurde eine neue Protokollierungsfunktion für Lease-Timeout-Nachrichten hinzugefügt, sodass die aktuelle Uhrzeit und die erwarteten Erneuerungs Zeiten protokolliert werden. Im SQL-Fehlerprotokoll wurde außerdem eine neue Nachricht bezüglich der Timeouts eingeführt. [Weitere Informationen finden Sie im Blog](https://blogs.msdn.microsoft.com/alwaysonpro/2016/02/23/improved-alwayson-availability-group-lease-timeout-diagnostics/).
-   **Neues DMF zum Abrufen des Eingabe Puffers in SQL Server:** Ein neues DMF zum Abrufen des Eingabe Puffers für eine Sitzung/Anforderung (sys. dm_exec_input_buffer) ist jetzt verfügbar. Dieser DMF ist funktional äquivalent zu DBCC INPUTBUFFER. [Weitere Informationen finden Sie im Blog](https://blogs.msdn.microsoft.com/sql_server_team/new-dmf-for-retrieving-input-buffer-in-sql-server/).
-   **Entschärfung für unterschätzende und überschätzte Speicherzuweisung:** Neue Abfrage Hinweise für Resource Governor über MIN_GRANT_PERCENT und MAX_GRANT_PERCENT hinzugefügt. Diese neue Abfrage ermöglicht es Ihnen, diese Hinweise während der Ausführung von Abfragen zu nutzen, indem Sie Ihre Arbeitsspeicher Zuweisungen zum Verhindern von Speicher Konflikten durchführen. Weitere Informationen finden Sie im [Knowledge Base-Artikel KB310740](https://support.microsoft.com/kb/3107401).
-   **Bessere Speicherzuweisung und Verwendungs Diagnose:** `query_memory_grant_usage`Der Liste der Ablauf Verfolgungs Funktionen in SQL Server wurde ein neues erweitertes Ereignis namens hinzugefügt. Dieses Ereignis verfolgt die angeforderten und gewährten Arbeitsspeicher Zuweisungen. Dieses Ereignis bietet bessere Ablauf Verfolgungs-und Analysefunktionen für die Behandlung von Problemen bei der Abfrage Ausführung im Zusammenhang mit Arbeitsspeicher Zuweisungen. Weitere Informationen finden Sie im [Knowledge Base-Artikel KB3107173](https://support.microsoft.com/kb/3107173).
-   **Abfrage Ausführungs Diagnose für tempdb-Überlauf:**-Hash Warnung und Sortier Warnungen verfügen jetzt über zusätzliche Spalten zum Nachverfolgen physischer e/a-Statistiken, verwendeter Arbeitsspeicher und der betroffenen Zeilen. Wir haben auch ein neues hash_spill_details erweitertes Ereignis eingeführt. Nun können Sie genauere Informationen zu ihren Hash-und Sortier Warnungen ([KB3107172](https://support.microsoft.com/kb/3107172)) verfolgen. Diese Verbesserung wird nun auch über die XML Query Pläne in Form eines neuen Attributs für den komplexen spillytempdbtype-Typ ([KB3107400](https://support.microsoft.com/kb/3107400)) verfügbar gemacht. SET STATISTICS `ON` zeigt nun Arbeits Tabellenstatistiken sortieren an.
-   **Verbesserte Diagnose für Abfrage Ausführungspläne, die Rest-Prädikat Weitergabe einschließen:** Die tatsächlich gelesenen Zeilen werden nun in den Abfrage Ausführungsplänen angezeigt, um die Problembehandlung bei der Abfrageleistung zu verbessern. Diese Zeilen negieren die Notwendigkeit, SET STATISTICS IO separat zu erfassen. Diese Zeilen ermöglichen es Ihnen außerdem, Informationen im Zusammenhang mit einem Rest-Prädikat-Pushdown in einem Abfrageplan anzuzeigen. Weitere Informationen finden Sie im [Knowledge Base-Artikel KB3107397](https://support.microsoft.com/kb/3107397).


## <a name="additional-information"></a>Zusätzliche Informationen  
 [SQL Server 2014-Ressourcen](../2014-toc/index.yml)  
  
 [SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/p/?linkID=296445)  
  
 [SQL Server 2014-Ressourcencenter](https://msdn.microsoft.com/sqlserver/dn135309)  
  
 [SQLCat-Website](https://go.microsoft.com/fwlink/p/?linkID=220963)  
