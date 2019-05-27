---
title: Verwenden von dynamischen Verwaltungssichten (DMVs) zum Überwachen von Analysis Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 22b82b2d-867f-4ebf-9288-79d1cdd62f18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a02d8d5b113e4773aa7cdfbbf20975fd70218e1a
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66079583"
---
# <a name="use-dynamic-management-views-dmvs-to-monitor-analysis-services"></a>Verwenden von dynamischen Verwaltungssichten (DMVs) zum Überwachen von Analysis Services
  Dynamische Verwaltungssichten (DMV) von Analysis Services sind Abfragestrukturen, die Informationen zu lokalen Servervorgängen und zum Serverstatus verfügbar machen. Die Abfragestruktur stellt eine Schnittstelle zu Schemarowsets dar, die Metadaten und Überwachungsinformationen zu einer Analysis Services-Instanz zurückgeben.  
  
 Für die meisten DMV-Abfragen verwenden Sie eine `SELECT`-Anweisung und das `$System`-Schema mit einem XML/A-Schemarowset.  
  
```  
SELECT * FROM $System.<schemaRowset>  
```  
  
 DMV-Abfragen geben Informationen zum Serverstatus zurück, der während der Ausführung der Abfrage gegolten hat. Verwenden Sie stattdessen die Ablaufverfolgung, um Vorgänge in Echtzeit zu überwachen. Weitere Informationen finden Sie unter [Use SQL Server Profiler to Monitor Analysis Services](use-sql-server-profiler-to-monitor-analysis-services.md).  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Vorteile der Verwendung von DMV-Abfragen](#bkmk_ben)  
  
 [Beispiele und Szenarien](#bkmk_ex)  
  
 [Abfragesyntax](#bkmk_syn)  
  
 [Tools und Berechtigungen](#bkmk_tools)  
  
 [DMV-Referenz](#bkmk_ref)  
  
##  <a name="bkmk_ben"></a> Vorteile der Verwendung von DMV-Abfragen  
 DMV-Abfragen geben Informationen zu Vorgängen und zum Ressourcenverbrauch zurück, die nicht auf anderen Wegen verfügbar sind.  
  
 DMV-Abfragen stellen eine Alternative zur Ausführung von XML/A-Discover-Befehlen dar. Für die meisten Administratoren ist das Schreiben einer DMV-Abfrage einfacher, weil die Abfragesyntax auf SQL basiert. Außerdem wird das Resultset in einem tabellarischen Format zurückgegeben, das besser lesbar ist und aus dem besser kopiert werden kann.  
  
##  <a name="bkmk_ex"></a> Beispiele und Szenarien  
 Eine DMV-Abfrage kann Ihnen helfen, Fragen zu aktiven Sitzungen und Verbindungen sowie die Frage zu beantworten, welche Objekte zu einem bestimmten Zeitpunkt den höchsten CPU-Anteil oder den meisten Arbeitsspeicher nutzen. Dieser Abschnitt enthält Beispiele für die Szenarien, in denen DMV-Abfragen am häufigsten verwendet werden. Weitere Informationen zur Verwendung von DMV-Abfragen für die Überwachung einer Serverinstanz finden Sie auch im [SQL Server 2008 R2 Analysis Services-Vorgangshandbuch](https://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409) .  
  
 `Select * from $System.discover_object_activity` /** Diese Abfrage erstellt einen Bericht zu der Objektaktivität seit dem letzten Start des Diensts. Beispielabfragen auf Grundlage dieser DMV-Abfrage finden Sie unter [New System.Discover_Object_Activity](https://go.microsoft.com/fwlink/?linkid=221322).  
  
 `Select * from $System.discover_object_memory_usage` /** Diese Abfrage erstellt einen Bericht zum Arbeitsspeicherverbrauch nach Objekt.  
  
 `Select * from $System.discover_sessions` /** Diese Abfrage erstellt einen Bericht zu aktiven Sitzungen, einschließlich Sitzungsbenutzer und -dauer.  
  
 `Select * from $System.discover_locks` /** Diese Abfrage gibt eine Momentaufnahme der Sperren zurück, die zu verschiedenen Zeitpunkten verwendet werden.  
  
##  <a name="bkmk_syn"></a> Abfragesyntax  
 Die Abfrage-Engine für DMVs ist der Data Mining-Parser. Die DMV-Abfragesyntax basiert auf der [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx)-Anweisung.  
  
 Obwohl die DMV-Abfragesyntax auf einer SELECT-SQL-Anweisung basiert, bietet sie keine vollständige Unterstützung einer SELECT-Anweisung. JOIN, GROUP BY, LIKE, CAST und CONVERT werden z. B. nicht unterstützt.  
  
```  
SELECT [DISTINCT] [TOP <n>] <select list>  
FROM $System.<schemaRowset>  
[WHERE <condition expression>]  
[ORDER BY <expression>[DESC|ASC]]  
```  
  
 Im folgenden Beispiel für DISCOVER_CALC_DEPENDENCY wird die Verwendung der WHERE-Klausel zum Angeben eines Parameters für die Abfrage veranschaulicht:  
  
```  
SELECT * FROM $System.DISCOVER_CALC_DEPENDENCY  
WHERE OBJECT_TYPE = 'ACTIVE_RELATIONSHIP'  
```  
  
 Für Schemarowsets, die über Einschränkungen verfügen, muss die Abfrage alternativ dazu die SYSTEMRESTRICTSCHEMA-Funktion enthalten. Im folgenden Beispiel werden CSDL-Metadaten zu tabellarischen Modellen zurückgegeben, die auf einem Server im tabellarischen Modus ausgeführt werden. Beachten Sie, dass bei CATALOG_NAME Groß- und Kleinschreibung unterschieden wird:  
  
```  
Select * from SYSTEMRESTRICTSCHEMA ($System.Discover_csdl_metadata, [CATALOG_NAME] = 'Adventure Works DW')  
```  
  
##  <a name="bkmk_tools"></a> Tools und Berechtigungen  
 Sie müssen über Systemadministratorberechtigungen für die Analysis Services-Instanz verfügen, um eine DMV-Abfrage ausführen zu können.  
  
 Sie können jede beliebige Clientanwendung verwenden, die MDX- oder DMX-Abfragen unterstützt, z. B. SQL Server Management Studio, einen Reporting Services-Bericht oder ein PerformancePoint-Dashboard.  
  
 Stellen Sie zum Ausführen einer DMV-Abfrage in Management Studio eine Verbindung mit der Instanz her, die Sie abfragen möchten, und klicken Sie auf **Neue Abfrage**. Sie können eine Abfrage über ein MDX- oder DMX-Abfragefenster ausführen.  
  
##  <a name="bkmk_ref"></a> DMV-Referenz  
 Nicht alle Schemarowsets verfügen über eine DMV-Schnittstelle. Führen Sie die folgende Abfrage aus, um eine Liste aller Schemarowsets zurückzugeben, die per DMV abgefragt werden können.  
  
```  
SELECT * FROM $System.DBSchema_Tables   
WHERE TABLE_TYPE = 'SCHEMA'   
ORDER BY TABLE_NAME ASC  
```  
  
> [!NOTE]  
>  Wenn eine DMV für ein angegebenes Rowset nicht vorliegen, gibt der Server den folgenden Fehler zurück: "Die \<Schemarowset > wurde vom Server nicht erkannt". Alle anderen Fehler weisen auf Probleme mit der Syntax hin.  
  
|Rowset|Description|  
|------------|-----------------|  
|[DBSCHEMA_CATALOGS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db/dbschema-catalogs-rowset)|Gibt eine Liste der Analysis Services-Datenbanken für die aktuelle Verbindung zurück.|  
|[DBSCHEMA_COLUMNS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db/dbschema-columns-rowset)|Gibt eine Liste aller Spalten in der aktuellen Datenbank zurück. Sie können diese Liste verwenden, um eine DMV-Abfrage zu erstellen.|  
|[DBSCHEMA_PROVIDER_TYPES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db/dbschema-provider-types-rowset)|Gibt Eigenschaften zu den vom OLE DB-Datenanbieter unterstützten Basisdatentypen zurück.|  
|[DBSCHEMA_TABLES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db/dbschema-tables-rowset)|Gibt eine Liste aller Tabellen in der aktuellen Datenbank zurück. Sie können diese Liste verwenden, um eine DMV-Abfrage zu erstellen.|  
|[DISCOVER_CALC_DEPENDENCY-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-calc-dependency-rowset)|Gibt eine Liste der Spalten und Tabellen zurück, die in einem Modell verwendet werden und über Abhängigkeiten von anderen Spalten und Tabellen verfügen.|  
|[DISCOVER_COMMAND_OBJECTS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-command-objects-rowset)|Stellt Ressourcenverwendungs- und Aktivitätsinformationen zu Objekten bereit, die von dem Befehl, auf den verwiesen wird, verwendet werden.|  
|[DISCOVER_COMMANDS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-commands-rowset)|Stellt Informationen zur Ressourcenauslastung und Aktivität in Verbindung mit dem momentan ausgeführten Befehl bereit.|  
|[DISCOVER_CONNECTIONS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-connections-rowset)|Stellt Informationen zur Ressourcenauslastung und Aktivität in Verbindung mit geöffneten Verbindungen zu Analysis Services bereit.|  
|[DISCOVER_CSDL_METADATA-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset)|Gibt Informationen zu einem tabellarischen Modell zurück.<br /><br /> Erfordert die Hinzufügung von SYSTEMRESTRICTSCHEMA und weiteren Parametern.|  
|[DISCOVER_DB_CONNECTIONS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-db-connections-rowset)|Stellt Informationen zur Ressourcenauslastung und Aktivität in Bezug auf geöffnete Verbindungen von Analysis Services für externe Datenquellen bereit, z. B. während der Verarbeitung oder während des Imports.|  
|[DISCOVER_DIMENSION_STAT-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-dimension-stat-rowset)|Gibt je nach Modelltyp die Attribute in einer Dimension oder Spalten in einer Tabelle zurück.|  
|[DISCOVER_ENUMERATORS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-enumerators-rowset)|Gibt Metadaten zu den Enumeratoren zurück, die für eine bestimmte Datenquelle unterstützt werden.|  
|[DISCOVER_INSTANCES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/discover-instances-rowset)|Gibt Informationen zur angegebenen Instanz zurück.<br /><br /> Erfordert die Hinzufügung von SYSTEMRESTRICTSCHEMA und weiteren Parametern.|  
|[DISCOVER_JOBS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-jobs-rowset)|Gibt Informationen zu aktuellen Aufträgen zurück.|  
|[DISCOVER_KEYWORDS-Rowset &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-keywords-rowset-xmla)|Gibt die Liste der reservierten Schlüsselwörter zurück.|  
|[DISCOVER_LITERALS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-literals-rowset)|Gibt die Liste der Literale zurück, einschließlich Datentypen und Werte mit XMLA-Unterstützung.|  
|[DISCOVER_LOCKS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-locks-rowset)|Gibt eine Momentaufnahme der zu einem bestimmten Zeitpunkt verwendeten Sperren zurück.|  
|[DISCOVER_MEMORYGRANT-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-memorygrant-rowset)|Gibt Informationen zum Arbeitsspeicher zurück, der von Analysis Services beim Start zugeordnet wird.|  
|[DISCOVER_MEMORYUSAGE-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-memoryusage-rowset)|Zeigt die Speicherauslastung bestimmter Objekte an.|  
|[DISCOVER_OBJECT_ACTIVITY-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-object-activity-rowset)|Erstellt einen Bericht zur Objektaktivität seit dem letzten Start des Diensts.|  
|[DISCOVER_OBJECT_MEMORY_USAGE-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-object-memory-usage-rowset)|Erstellt einen Bericht zur Arbeitsspeichernutzung nach Objekt.|  
|[DISCOVER_PARTITION_DIMENSION_STAT-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-partition-dimension-stat-rowset)|Stellt Informationen zu den Attributen in einer Dimension bereit.<br /><br /> Erfordert die Hinzufügung von SYSTEMRESTRICTSCHEMA und weiteren Parametern.|  
|[DISCOVER_PARTITION_STAT-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-partition-stat-rowset)|Stellt Informationen zu den Partitionen in einer Dimension, Tabelle oder Measuregruppe bereit.<br /><br /> Erfordert die Hinzufügung von SYSTEMRESTRICTSCHEMA und weiteren Parametern.|  
|[DISCOVER_PERFORMANCE_COUNTERS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-performance-counters-rowset)|Listet die in einem Leistungsindikator verwendeten Spalten auf.<br /><br /> Erfordert die Hinzufügung von SYSTEMRESTRICTSCHEMA und weiteren Parametern.|  
|[DISCOVER_PROPERTIES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-properties-rowset)|Gibt Informationen zu Eigenschaften mit XMLA-Unterstützung für die angegebene Datenquelle zurück.|  
|[DISCOVER_SCHEMA_ROWSETS-Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-schema-rowsets-rowset)|Gibt Namen, Einschränkungen, Beschreibungen und andere Informationen für alle von XMLA unterstützten Enumerationswerte zurück.|  
|[DISCOVER_SESSIONS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-sessions-rowset)|Erstellt Berichte zu aktiven Sitzungen, einschließlich Sitzungsbenutzer und -dauer.|  
|[DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-storage-table-column-segments-rowset)|Stellt Informationen zu Speichertabellen auf Spalten- und Segmentebene bereit, die von einer im Tabellenmodus oder SharePoint-Modus ausgeführten Analysis Services-Datenbank verwendet werden.|  
|[DISCOVER_STORAGE_TABLE_COLUMNS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-storage-table-columns-rowset)|Ermöglicht dem Client die Zuweisung von Spalten zu Speichertabellen, die von einer im Tabellenmodus oder SharePoint-Modus ausgeführten Analysis Services-Datenbank verwendet wurden.|  
|[DISCOVER_STORAGE_TABLES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-storage-tables-rowset)|Gibt Informationen zu den Tabellen zurück, die als Speicher für Modelle in einer tabellarische Modelldatenbank verwendet werden.|  
|[DISCOVER_TRACE_COLUMNS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-trace-columns-rowset)|Gibt eine XML-Beschreibung der in einer Ablaufverfolgung verfügbaren Spalten zurück.|  
|[DISCOVER_TRACE_DEFINITION_PROVIDERINFO-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-trace-definition-providerinfo-rowset)|Gibt Namens- und Versionsinformationen des Anbieters zurück.|  
|[DISCOVER_TRACE_EVENT_CATEGORIES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-trace-event-categories-rowset)|Gibt eine Liste verfügbarer Kategorien zurück.|  
|[DISCOVER_TRACES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-traces-rowset)|Gibt eine Liste von Ablaufverfolgungen zurück, die über die aktuelle Verbindung aktiv ausgeführt werden.|  
|[DISCOVER_TRANSACTIONS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-transactions-rowset)|Gibt eine Liste von Transaktionen zurück, die über die aktuelle Verbindung aktiv ausgeführt werden.|  
|[DISCOVER_XEVENT_TRACE_DEFINITION-Rowset](../dev-guide/discover-xevent-trace-definition-rowset.md)|Gibt eine Liste von xevent-Ablaufverfolgungen zurück, die über die aktuelle Verbindung aktiv ausgeführt werden.|  
|[DMSCHEMA_MINING_COLUMNS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-columns-rowset)|Listet die einzelnen Spalten aller Miningmodelle auf, die für die aktuelle Verbindung verfügbar sind.|  
|[DMSCHEMA_MINING_FUNCTIONS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-functions-rowset)|Gibt eine Liste mit den Funktionen zurück, die von den Data Mining-Algorithmen auf dem Server unterstützt werden.|  
|[DMSCHEMA_MINING_MODEL_CONTENT-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)|Gibt ein Rowset zurück, das aus Spalten besteht, in denen das aktuelle Modell beschrieben wird.|  
|[DMSCHEMA_MINING_MODEL_CONTENT_PMML-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset)|Gibt ein Rowset zurück, das aus Spalten besteht, in denen das aktuelle Modell im PMML-Format beschrieben wird.|  
|[DMSCHEMA_MINING_MODEL_XML-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-xml-rowset)|Gibt ein Rowset zurück, das aus Spalten besteht, in denen das aktuelle Modell im PMML-Format beschrieben wird.|  
|[DMSCHEMA_MINING_MODELS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-models-rowset)|Gibt eine Liste der Miningmodelle in der aktuellen Datenbank zurück.|  
|[DMSCHEMA_MINING_SERVICE_PARAMETERS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset)|Gibt eine Liste der Parameter für die Algorithmen auf dem Server zurück.|  
|[DMSCHEMA_MINING_SERVICES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset)|Stellt eine Liste der auf dem Server verfügbaren Data Mining-Algorithmen bereit.|  
|[DMSCHEMA_MINING_STRUCTURE_COLUMNS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset)|Gibt eine Liste aller Spalten in allen Miningmodellen zurück, die für die aktuelle Verbindung verfügbar sind.|  
|[DMSCHEMA_MINING_STRUCTURES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-structures-rowset)|Listet die Miningstrukturen auf, die für die aktuelle Verbindung verfügbar sind.|  
|[MDSCHEMA_CUBES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-cubes-rowset)|Gibt Informationen zu den Cubes zurück, die in der aktuellen Datenbank definiert sind.|  
|[MDSCHEMA_DIMENSIONS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-dimensions-rowset)|Gibt Informationen zu den Dimensionen zurück, die in der aktuellen Datenbank definiert sind.|  
|[MDSCHEMA_FUNCTIONS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-functions-rowset)|Gibt eine Liste der Funktionen zurück, die für mit der Datenbank verbundene Clientanwendungen zur Verfügung stehen.|  
|[MDSCHEMA_HIERARCHIES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset)|Gibt Informationen zu den Hierarchien zurück, die in der aktuellen Datenbank definiert sind.|  
|[MDSCHEMA_INPUT_DATASOURCES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset)|Gibt Informationen zu den Datenquellenobjekten zurück, die in der aktuellen Datenbank definiert sind.|  
|[MDSCHEMA_KPIS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-kpis-rowset)|Gibt Informationen zu den KPIs zurück, die in der aktuellen Datenbank definiert sind.|  
|[MDSCHEMA_LEVELS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-levels-rowset)|Gibt Informationen zu den Ebenen innerhalb der Hierarchien zurück, die in der aktuellen Datenbank definiert sind.|  
|[MDSCHEMA_MEASUREGROUP_DIMENSIONS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset)|Listet die Dimension von Measuregruppen auf.|  
|[MDSCHEMA_MEASUREGROUPS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset)|Gibt eine Liste von Measuregruppen unter der aktuellen Verbindung zurück.|  
|[MDSCHEMA_MEASURES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-measures-rowset)|Gibt eine Liste von Measures unter der aktuellen Verbindung zurück.|  
|[MDSCHEMA_MEMBERS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-members-rowset)|Gibt eine Liste aller Elemente für die aktuelle Verbindung sortiert nach Datenbank, Cube und Dimension zurück.|  
|[MDSCHEMA_PROPERTIES-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-properties-rowset)|Gibt den vollqualifizierten Namen jeder Eigenschaft zusammen mit Eigenschaftstyp, Datentyp und anderen Metadaten zurück.|  
|[MDSCHEMA_SETS-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-sets-rowset)|Gibt eine Liste mit den Sätzen zurück, die unter der aktuellen Verbindung definiert sind.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server 2008 R2 Analysis Services-Vorgangshandbuch](https://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409)   
 [New System.Discover_Object_Activity](https://go.microsoft.com/fwlink/?linkid=221322)   
 [Neue SYSTEMRESTRICTEDSCHEMA-Funktion für eingeschränkte Rowsets und DMVs](https://go.microsoft.com/fwlink/?LinkId=231885)  
  
  
