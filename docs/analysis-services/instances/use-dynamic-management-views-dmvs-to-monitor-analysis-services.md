---
title: Verwenden von dynamischen Verwaltungssichten (DMVs) in Analysis Services | Microsoft-Dokumentation
ms.date: 09/25/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d59601d0706b65186ed5f260128c3c44a134d60e
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "48906400"
---
# <a name="dynamic-management-views-dmvs"></a>Dynamische Verwaltungssichten (DMVs) 

[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

Analysis Services dynamische Verwaltungssichten (DMV) handelt es sich um Abfragen, die Informationen zu modellobjekten, Servervorgängen und Integrität der Server zurückgeben. Die Abfrage, die basierend auf SQL ist eine Benutzeroberfläche zum *Schemarowsets*. Schemarowsets sind predescribed Tabellen mit Informationen zu Analysis Services-Objekten und des Serverstatus, einschließlich Datenbankschema, aktive Sitzungen, Verbindungen, Befehle und Aufträge, die auf dem Server ausgeführt werden.

DMV-Abfragen stellen eine Alternative zur Ausführung von XML/A-Discover-Befehlen dar. Für die meisten Administratoren ist das Schreiben einer DMV-Abfrage einfacher, weil die Syntax SQL basiert. Darüber hinaus ist das Ergebnis in einem Tabellenformat zurückgegeben, der leichter zu lesen und zu kopieren. 
  
Die meisten DMV-Abfragen verwenden eine **wählen** Anweisung und die **$System** Schema mit einem XML/A-Schemarowset, z.B.:  
  
```  
SELECT * FROM $System.<schemaRowset>  
```  
  
 DMV-Abfragen zurückgeben von Informationen zu Server und Objekt Zustand zum Zeitpunkt, dass die Abfrage ausgeführt wird. Um Vorgänge in stattdessen in Echtzeit, verwenden die Ablaufverfolgung zu überwachen. Weitere Informationen zu in Echtzeit mithilfe von ablaufverfolgungen finden Sie unter [verwenden SQL Server Profiler zum Überwachen von Analysis Services](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md).  
  
## <a name="query-syntax"></a>Abfragesyntax

Die Abfrage-Engine für DMVs ist der Data Mining-Parser. Die DMV-Abfragesyntax basiert darauf, dass die SELECT-Anweisung &#40;DMX&#41; Anweisung. Obwohl die DMV-Abfragesyntax auf einer SELECT-SQL-Anweisung basiert, bietet sie keine vollständige Unterstützung einer SELECT-Anweisung. JOIN, GROUP BY, LIKE, CAST und CONVERT werden z. B. nicht unterstützt.  
  
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
  
Für die Schemarowsets, die Einschränkungen aufweisen, muss die Abfrage die SYSTEMRESTRICTSCHEMA-Funktion enthalten. Das folgende Beispiel gibt die CSDL-Metadaten etwa 1103 Kompatibilität tabellarischen Modellen mit Kompatibilitätsgrad. Beachten Sie, dass bei CATALOG_NAME Groß- und Kleinschreibung unterschieden wird:  
  
```  
Select * from SYSTEMRESTRICTSCHEMA ($System.Discover_csdl_metadata, [CATALOG_NAME] = 'Adventure Works DW')  
```  

## <a name="examples-and-scenarios"></a>Beispiele und Szenarien

Eine DMV-Abfrage kann Ihnen helfen, Fragen zu aktiven Sitzungen und Verbindungen sowie die Frage zu beantworten, welche Objekte zu einem bestimmten Zeitpunkt den höchsten CPU-Anteil oder den meisten Arbeitsspeicher nutzen. Zum Beispiel:
  
 `Select * from $System.discover_object_activity`  
Diese Abfrage erstellt einen Bericht zu der Objektaktivität seit dem letzten des Diensts Start. 
  
 `Select * from $System.discover_object_memory_usage`  
Diese Abfrage einen Bericht zum Arbeitsspeicherverbrauch nach Objekt.  
  
 `Select * from $System.discover_sessions`  
Diese Abfrage erstellt einen Bericht zu aktiven Sitzungen, einschließlich Sitzungsbenutzer und -Dauer.  
  
 `Select * from $System.discover_locks`   
Diese Abfrage gibt eine Momentaufnahme zu einem bestimmten Zeitpunkt verwendeten Sperren zurück.  


## <a name="tools-and-permissions"></a>Tools und Berechtigungen

Sie können eine beliebige Clientanwendung verwenden, die MDX- oder DMX-Abfragen unterstützt. In den meisten Fällen ist es am besten, SQL Server Management Studio verwenden. Serveradministratorberechtigungen benötigen Sie auf die Instanz aus, um eine DMV-Abfrage.  
  
 **Zum Ausführen einer DMV-Abfrage aus SQL Server Management Studio**

1. Verbinden Sie mit dem Server und der Model-Objekts, die Sie abfragen möchten. 
2. Mit der rechten Maustaste in den Server oder Datenbank-Objekt > **neue Abfrage** > **MDX**.
3. Geben Sie Ihre Abfrage aus, und klicken Sie dann auf **Execute**, oder drücken Sie F5.
  
## <a name="schema-rowsets"></a>Schemarowsets

Nicht alle Schemarowsets verfügen über eine DMV-Schnittstelle. Führen Sie die folgende Abfrage aus, um eine Liste aller Schemarowsets zurückzugeben, die per DMV abgefragt werden können.  
 
```  
SELECT * FROM $System.DBSchema_Tables   
WHERE TABLE_TYPE = 'SCHEMA'   
ORDER BY TABLE_NAME ASC  
```  
  
Wenn eine DMV für ein angegebenes Rowset nicht vorliegen, gibt der Server Fehler zurück: `The <schemarowset> request type was not recognized by the server.` alle anderen Fehler weisen auf Probleme mit der Syntax.  

Schemarowsets werden in zwei SQL Server Analysis Services-Protokollen beschrieben:   

[[MS-SSAS-T]: SQL Server Analysis Services Tabular Protocol](https://msdn.microsoft.com/library/mt719260) -beschreibt die Schemarowsets für tabellarische Modelle mit den Kompatibilitätsgraden 1200 und höher.

[[MS-SSAS]: SQL Server Analysis Services-Protokoll](https://msdn.microsoft.com/library/ee320606) -Schemarowsets für mehrdimensionale und tabellarische Modelle mit dem Kompatibilitätsgrad 1100 und 1103 beschreibt.

### <a name="rowsets-described-in-the-ms-ssas-t-sql-server-analysis-services-tabular-protocol"></a>Rowsets, die in der [MS-SSAS-T] beschriebenen: SQL Server Analysis Services Tabular Protocol

|Rowset  |Description  |
|---------|---------|
|[TMSCHEMA_ANNOTATIONS](https://msdn.microsoft.com/library/mt704370)|Enthält Informationen zu den Annotation-Objekten im Modell.|
|[TMSCHEMA_ATTRIBUTE_HIERARCHIES](https://msdn.microsoft.com/library/mt704362)     |   Enthält Informationen über die AttributeHierarchy-Objekte für eine Spalte.      |
|[TMSCHEMA_COLUMNS](https://msdn.microsoft.com/library/mt704373)    |  Enthält Informationen zu den Column-Objekten in jeder Tabelle.       |
|[TMSCHEMA_COLUMN_PERMISSIONS](https://msdn.microsoft.com/library/mt842440)|Enthält Informationen zu den ColumnPermission-Objekten in jeder Tabelle-Berechtigung.|
|[TMSCHEMA_CULTURES](https://msdn.microsoft.com/library/mt719125)|Enthält Informationen zu den Objekten Kultur im Modell.|
|[TMSCHEMA_DATA_SOURCES](https://msdn.microsoft.com/library/mt719191)   |   Enthält Informationen über die DataSource-Objekte im Modell.      |
|[TMSCHEMA_DETAIL_ROWS_DEFINITIONS](https://msdn.microsoft.com/library/mt825017)|Enthält Informationen zu den DetailRowsDefinition-Objekten im Modell.|
|[TMSCHEMA_EXPRESSIONS](https://msdn.microsoft.com/library/mt825015)|Enthält Informationen zu den Expression-Objekten im Modell.|
|[TMSCHEMA_EXTENDED_PROPERTIES](https://msdn.microsoft.com/library/mt842451)|Enthält Informationen zu den ExtendedProperty-Objekten im Modell.|
|[TMSCHEMA_HIERARCHIES](https://msdn.microsoft.com/library/mt719136)    |    Enthält Informationen über die Hierarchy-Objekten in jeder Tabelle.     |
|[TMSCHEMA_KPIS](https://msdn.microsoft.com/library/mt719002)     |    Enthält Informationen zu den KPI-Objekte im Modell.     |
|[TMSCHEMA_LEVELS](https://msdn.microsoft.com/library/mt719038)     |   Enthält Informationen über die Objekte, die in jeder Hierarchie auf Serverebene.      |
|[TMSCHEMA_LINGUISTIC_METADATA](https://msdn.microsoft.com/library/mt719169)|Enthält Informationen über die Synonyme für Objekte im Modell für eine bestimmte Kultur|
|[TMSCHEMA_MEASURES](https://msdn.microsoft.com/library/mt719218)     |    Enthält Informationen zu den Objekten Measure in jeder Tabelle.     |
|[TMSCHEMA_MODEL](https://msdn.microsoft.com/library/mt719042)    |  Gibt ein Model-Objekt in der Datenbank an.       |
|[TMSCHEMA_OBJECT_TRANSLATIONS](https://msdn.microsoft.com/library/mt719119)|Bietet Informationen zu den Übersetzungen der verschiedene Objekte für eine Kultur an.|
|[TMSCHEMA_PARTITIONS](https://msdn.microsoft.com/library/mt704375)     |     Enthält Informationen zu den Partition-Objekten in jeder Tabelle.    |
|[TMSCHEMA_PERSPECTIVE_COLUMNS](https://msdn.microsoft.com/library/mt719164)     |   Enthält Informationen zu den PerspectiveColumn-Objekten in jedem PerspectiveTable-Objekt.      |
|[TMSCHEMA_PERSPECTIVE_HIERARCHIES](https://msdn.microsoft.com/library/mt719104)     |  Enthält Informationen zu den PerspectiveHierarchy-Objekten in jedem PerspectiveTable-Objekt.       |
|[TMSCHEMA_PERSPECTIVE_MEASURES](https://msdn.microsoft.com/library/mt719135)     |    Enthält Informationen über die PerspectiveMeasure-Objekte in jedem PerspectiveTable-Objekt.     |
|[TMSCHEMA_PERSPECTIVE_TABLES](https://msdn.microsoft.com/library/mt719272)     |    Enthält Informationen über die Tabellenobjekte in einer Perspektive.     |
|[TMSCHEMA_PERSPECTIVES](https://msdn.microsoft.com/library/mt704340)     |     Enthält Informationen über die Perspective-Objekte im Modell.    |
|[TMSCHEMA_RELATIONSHIPS](https://msdn.microsoft.com/library/mt704355)     |    Enthält Informationen zu den Relationship-Objekten im Modell.     |
|[TMSCHEMA_ROLE_MEMBERSHIPS](https://msdn.microsoft.com/library/mt704584)     |  Enthält Informationen zu den RoleMembership-Objekte in jeder Rolle.      |
|[TMSCHEMA_ROLES](https://msdn.microsoft.com/library/mt719267)    |   Enthält Informationen über die Role-Objekte im Modell.      |
|[TMSCHEMA_TABLE_PERMISSIONS](https://msdn.microsoft.com/library/mt704347)    |    Enthält Informationen zu den TablePermission-Objekten in jeder Rolle.     |
|[TMSCHEMA_TABLES](https://msdn.microsoft.com/library/mt719250)     |   Enthält Informationen über die Tabellenobjekte in das Modell.      |
|[TMSCHEMA_VARIATIONS](https://msdn.microsoft.com/library/mt825008)|Enthält Informationen zu den Variation-Objekten in jeder Spalte.|

### <a name="rowsets-described-in-the-ms-ssas-sql-server-analysis-services-protocol"></a>Rowsets, die in der [MS-SSAS] beschriebenen: SQL Server Analysis Services-Protokoll

|Rowset|Description|  
|------------|-----------------|  
|[DBSCHEMA_CATALOGS](https://msdn.microsoft.com/library/ee302115)|Beschreibt die Kataloge, die auf dem Server zugegriffen werden kann.|  
|[DBSCHEMA_COLUMNS](https://msdn.microsoft.com/library/ee301789)|Gibt eine Zeile für jedes Measure, jedes Dimensionsattribut Cube und jede Spalte Schema Rowsets, als einer Spalte verfügbar gemacht werden.|  
|[DBSCHEMA_PROVIDER_TYPES](https://msdn.microsoft.com/library/ee301696)|Gibt die vom Server unterstützten (Basis-) Datentypen.|  
|[DBSCHEMA_TABLES](https://msdn.microsoft.com/library/ee320843)|Gibt zurück, Dimensionen, Measuregruppen oder Schemarowsets als Tabellen verfügbar gemacht.|  
|[DISCOVER_CALC_DEPENDENCY](https://msdn.microsoft.com/library/hh770226)| Gibt Informationen zu die Berechnung-Abhängigkeit für ein Objekt, das angegeben wird, in einer tabellarischen Datenbank oder in einer DAX-Abfrage, die für eine tabellarische Datenbank ausgeführt wird. |  
|[DISCOVER_COMMAND_OBJECTS](https://msdn.microsoft.com/library/ee320662)|Stellt Ressourcenverwendungs- und Aktivitätsinformationen über die Objekte bereit, die durch den Befehl, auf den verwiesen wird, verwendet werden.|  
|[DISCOVER_COMMANDS](https://msdn.microsoft.com/library/ee320715)|Stellt Ressourcenverwendungs- und Aktivitätsinformationen über die zurzeit ausgeführten oder zuletzt ausgeführten Befehle auf den offenen Verbindungen auf dem Server bereit.|  
|[DISCOVER_CONNECTIONS](https://msdn.microsoft.com/library/ee301889)|Stellt Informationen zur Ressourcenverwendung und Aktivität der zurzeit geöffneten Verbindungen auf dem Server bereit.|  
|[DISCOVER_CSDL_METADATA](https://msdn.microsoft.com/library/gg587670)|Gibt Informationen zu Datenbankmetadaten für in-Memory-Datenbanken.|  
|[DISCOVER_DATASOURCES](https://msdn.microsoft.com/library/ee320285)|Gibt eine Liste der Datenquellen, die auf dem Server verfügbar sind.|
|[DISCOVER_DB_CONNECTIONS](https://msdn.microsoft.com/library/ee320467)|Stellt Informationen zur Ressourcenauslastung und Aktivität der zurzeit geöffneten Verbindungen vom Server in einer Datenbank bereit.|  
|[DISCOVER_DIMENSION_STAT](https://msdn.microsoft.com/library/ee320284)|Gibt Statistiken zur angegebenen Dimension zurück.|  
|[DISCOVER_ENUMERATORS](https://msdn.microsoft.com/library/ee302012)|Gibt eine Liste mit Namen, Datentypen und Enumerationswerten von Enumeratoren zurück, die vom XMLA-Anbieter für eine bestimmte Datenquelle unterstützt werden.|  
|[DISCOVER_INSTANCES](https://msdn.microsoft.com/library/ee320541)|Beschreibt die Instanzen auf dem Server.|  
|[DISCOVER_JOBS](https://msdn.microsoft.com/library/ee320363)|Stellt Informationen über die aktiven Aufträge bereit, die auf dem Server ausgeführt werden. Ein Auftrag ist ein Teil eines Befehls, der für den Befehl einen bestimmten Task ausführt.|  
|[DISCOVER_KEYWORDS &AMP;#40;XMLA&AMP;#41;](https://msdn.microsoft.com/library/ee301719)|Gibt Informationen zu Schlüsselwörtern, die vom XMLA-Server reserviert sind.|  
|[DISCOVER_LITERALS](https://msdn.microsoft.com/library/ee301320)|Gibt Informationen zu Literalen, die vom Server unterstützt.|  
|[DISCOVER_LOCATIONS](https://msdn.microsoft.com/library/ee302024)|Gibt Informationen zum Inhalt einer Sicherungsdatei zurück. |
|[DISCOVER_LOCKS](https://msdn.microsoft.com/library/ee320398)|Stellt Informationen über die aktuellen Sperren auf dem Server bereit.|  
|[DISCOVER_MASTER_KEY](https://msdn.microsoft.com/library/ee301825)|Gibt das Serverzertifikat masterverschlüsselungsschlüssel zurück.|
|[DISCOVER_MEMORYGRANT](https://msdn.microsoft.com/library/ee320945)|Gibt eine Liste interner Arbeitsspeicherkontingent-Erteilungen zurück, die von Aufträgen in Anspruch genommen werden, die derzeit auf dem Server ausgeführt werden.|  
|[DISCOVER_MEMORYUSAGE](https://msdn.microsoft.com/library/ee320910)|Gibt die DISCOVER_MEMORYUSAGE-Statistiken für verschiedene vom Server zugeordnete Objekte zurück.|  
|[DISCOVER_OBJECT_ACTIVITY](https://msdn.microsoft.com/library/ee320661)|Stellt die Ressourcenverwendung pro Objekt seit dem Start des Diensts bereit.|  
|[DISCOVER_OBJECT_MEMORY_USAGE](https://msdn.microsoft.com/library/ee320910)|Gibt die DISCOVER_MEMORYUSAGE-Statistiken für verschiedene vom Server zugeordnete Objekte zurück.|  
|[DISCOVER_PARTITION_DIMENSION_STAT](https://msdn.microsoft.com/library/ee320268)|Gibt Statistiken für die Dimension, die einer Partition zugeordnet ist.|  
|[DISCOVER_PARTITION_STAT](https://msdn.microsoft.com/library/ee320483)|Gibt Statistiken zu Aggregationen in einer bestimmten Partition zurück.|  
|[DISCOVER_PERFORMANCE_COUNTERS](https://msdn.microsoft.com/library/ee320809)|Gibt den Wert von mindestens einem angegebenen Leistungsindikator zurück. |  
|[DISCOVER_PROPERTIES](https://msdn.microsoft.com/library/ee320589)|Gibt eine Liste mit Informationen und Werten zu den Eigenschaften, die vom Server für die angegebene Datenquelle unterstützt werden.|  
|[DISCOVER_RING_BUFFERS](https://msdn.microsoft.com/library/mt719204)|Informationen zu den aktuellen XEvent-Ringpuffer zurückgegeben auf dem Server.|
|[DISCOVER_SCHEMA_ROWSETS](https://msdn.microsoft.com/library/ee320478)|Gibt zurück, die Namen, Einschränkungen, Beschreibung und andere Informationen für alle ermittlungsanforderungen.|  
|[DISCOVER_SESSIONS](https://msdn.microsoft.com/library/ee301962)|Stellt Informationen zur Ressourcenverwendung und Aktivität der zurzeit geöffneten Sitzungen auf dem Server bereit.|  
|[DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS](https://msdn.microsoft.com/library/ee320710)|Gibt Informationen zu der spaltensegmente, die zum Speichern von Daten für in-Memory-Tabellen verwendet.|  
|[DISCOVER_STORAGE_TABLE_COLUMNS](https://msdn.microsoft.com/library/ee302101)|Enthält Informationen zu den Spalten, die zum Darstellen von Spalten einer Tabelle im Arbeitsspeicher verwendet.|  
|[DISCOVER_STORAGE_TABLES](https://msdn.microsoft.com/library/ee302014)|Gibt Statistiken zu in-Memory-Tabellen ist verfügbar auf dem Server zurück.|  
|[DISCOVER_TRACE_COLUMNS]()||  
|[DISCOVER_TRACE_DEFINITION_PROVIDERINFO](https://msdn.microsoft.com/library/ee301342)|Enthält DISCOVER_TRACE_COLUMNS-Schemarowsets an.|  
|[DISCOVER_TRACE_EVENT_CATEGORIES](https://msdn.microsoft.com/library/ee320442)|Enthält DISCOVER_TRACE_EVENT_CATEGORIES-Schemarowsets an.|  
|[DISCOVER_TRACES](https://msdn.microsoft.com/library/ee301643)|Enthält DISCOVER_TRACES-Schemarowsets an.|  
|[DISCOVER_TRANSACTIONS](https://msdn.microsoft.com/library/ee301363)|Gibt den aktuellen Satz von ausstehenden Transaktionen auf dem System zurück.|  
|[DISCOVER_XEVENT_TRACE_DEFINITION](https://msdn.microsoft.com/library/mt704568)|Enthält Informationen zu den XEvent-ablaufverfolgungen, die derzeit auf dem Server aktiv sind.|  
|[DISCOVER_XEVENT_PACKAGES](https://msdn.microsoft.com/library/mt704569)|Stellt Informationen über die XEvent-Pakete, die beschrieben werden auf dem Server bereit.|
|[DISCOVER_XEVENT_OBJECTS](https://msdn.microsoft.com/library/mt704543)|Stellt Informationen über die XEvent-Objekte, die beschrieben werden auf dem Server bereit.|
|[DISCOVER_XEVENT_OBJECT_COLUMNS](https://msdn.microsoft.com/library/mt719352)|Stellt Informationen zum Schema der XEvent-Objekte, die beschrieben werden auf dem Server bereit.|
|[DISCOVER_XEVENT_SESSIONS](https://msdn.microsoft.com/library/mt704397)|Stellt Informationen über die aktuellen XEvent-Sitzungen auf dem Server bereit.|
|[DISCOVER_XEVENT_SESSION_TARGETS](https://msdn.microsoft.com/library/mt704564)|Stellt Informationen zu den Zielen der aktuellen XEvent-Sitzung auf dem Server bereit.|
|[DISCOVER_XML_METADATA](https://msdn.microsoft.com/library/ee301560)|Gibt ein Rowset mit einer Zeile und einer Spalte zurück. |
|[DMSCHEMA_MINING_COLUMNS](https://msdn.microsoft.com/library/ee301664)|Beschreibt die einzelnen Spalten aller beschriebenen Datamining-Modelle, die bereitgestellt werden, auf dem Server.|  
|[DMSCHEMA_MINING_FUNCTIONS](https://msdn.microsoft.com/library/ee320415)|Beschreibt die Datamining-Funktionen, die von Datamining-Algorithmen unterstützt werden, die auf einem Server verfügbar sind, die Analysis Services ausgeführt wird.|  
|[DMSCHEMA_MINING_MODEL_CONTENT](https://msdn.microsoft.com/library/ee302124)|Ermöglicht die Clientanwendung, die den Inhalt des trainierten Datamining-Modelle durchsuchen.|  
|[DMSCHEMA_MINING_MODEL_CONTENT_PMML](https://msdn.microsoft.com/library/ee320692)|Gibt die XML-Struktur des Miningmodells wieder. Das Format der XML-Zeichenfolge folgt den PMML 2.1-Standard.|  
|[DMSCHEMA_MINING_MODEL_XML](https://msdn.microsoft.com/library/ee301916)|Gibt die XML-Struktur des Miningmodells wieder. Das Format der XML-Zeichenfolge folgt den PMML 2.1-Standard.|  
|[DMSCHEMA_MINING_MODELS](https://msdn.microsoft.com/library/ee320603)|Listet die Data Mining-Modelle auf, die auf dem Server verteilt werden.|  
|[DMSCHEMA_MINING_SERVICE_PARAMETERS](https://msdn.microsoft.com/library/ee320378)|Stellt eine Liste von Parametern bereit, die zur Konfiguration des Verhaltens eines jeden auf dem Server installierten Data Mining-Algorithmus verwendet werden kann.|  
|[DMSCHEMA_MINING_SERVICES](https://msdn.microsoft.com/library/ee320487)|Enthält Informationen zu einzelnen Datamining-Algorithmus, der der Server unterstützt.|  
|[DMSCHEMA_MINING_STRUCTURE_COLUMNS](https://msdn.microsoft.com/library/ee320277)|Beschreibt die einzelnen Spalten aller Data Mining-Strukturen, die auf dem Server verteilt werden.|  
|[DMSCHEMA_MINING_STRUCTURES](https://msdn.microsoft.com/library/ee320704)|Listet Informationen über die Miningstrukturen im aktuellen Katalog auf.|  
|[MDSCHEMA_ACTIONS](https://msdn.microsoft.com/library/ee320890)|Beschreibt die Aktionen, die für die Client-Anwendung zur Verfügung stehen.|
|[MDSCHEMA_CUBES](https://msdn.microsoft.com/library/ee301304)|Beschreibt die Struktur der Cubes innerhalb einer Datenbank. Perspektiven werden ebenfalls in diesem Schema zurückgegeben.|
|[MDSCHEMA_DIMENSIONS](https://msdn.microsoft.com/library/ee301366)|Beschreibt die Dimensionen in einer Datenbank.|  
|[MDSCHEMA_FUNCTIONS](https://msdn.microsoft.com/library/mt719467)|Gibt Informationen zu den Funktionen, die derzeit für die Verwendung in DAX und MDX-Sprachen verfügbar sind.|
|[MDSCHEMA_HIERARCHIES](https://msdn.microsoft.com/library/ee320250)|Beschreibt jede Hierarchie innerhalb einer bestimmten Dimension.|  
|[MDSCHEMA_INPUT_DATASOURCES](https://msdn.microsoft.com/library/ee301386)|Beschreibt die Datenquellenobjekte, die in der Datenbank beschrieben.|  
|[MDSCHEMA_KPIS](https://msdn.microsoft.com/library/ee320406)|Beschreibt die KPIs in einer Datenbank an.|  
|[MDSCHEMA_LEVELS](https://msdn.microsoft.com/library/ee320746)|Beschreibt jede Ebene innerhalb einer bestimmten Hierarchie.|  
|[MDSCHEMA_MEASUREGROUP_DIMENSIONS](https://msdn.microsoft.com/library/ee320977)|Listet die Dimensionen der Measuregruppe auf.|  
|[MDSCHEMA_MEASUREGROUPS](https://msdn.microsoft.com/library/ee320601)|Beschreibt die Measuregruppen innerhalb einer Datenbank.|  
|[MDSCHEMA_MEASURES](https://msdn.microsoft.com/library/ee301871)|Beschreibt jedes Measure.|  
|[MDSCHEMA_MEMBERS](https://msdn.microsoft.com/library/ee320960)|Beschreibt die Elemente innerhalb einer Datenbank.|  
|[MDSCHEMA_PROPERTIES](https://msdn.microsoft.com/library/ee320393)|Beschreibt die Eigenschaften von Elementen und Zelleigenschaften.|  
|[MDSCHEMA_SETS](https://msdn.microsoft.com/library/ee301356)|Beschreibt alle Sätze, die derzeit in einer Datenbank, einschließlich der Mengen im Bereich einer Sitzung beschrieben werden.|  

> [!NOTE]
> Ein Schemarowset beschrieben, die im Protokoll keine Speicher-DMVs.