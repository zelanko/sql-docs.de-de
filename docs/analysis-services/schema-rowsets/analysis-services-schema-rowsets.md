---
title: Analysis Services-Schemarowsets | Microsoft-Dokumentation
ms.date: 10/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4ec9d6c75ef1d3cdc8effdc44861eed5971ced60
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116680"
---
# <a name="analysis-services-schema-rowsets"></a>Analysis Services-Schemarowsets
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Schemarowsets sind vordefinierte Tabellen, die Informationen zu Analysis Services-Objekten und zum Serverstatus enthalten, einschließlich Datenbankschema, aktive Sitzungen, Verbindungen, Befehle und Aufträge, die auf dem Server ausgeführt werden. Sie können Schemarowsettabellen in einem XML/A-Skriptfenster in SQL Server Management Studio abfragen, eine DMV-Abfrage für ein Schemarowset ausführen oder eine benutzerdefinierte Anwendung erstellen, die Schemarowsetinformationen enthält (z. B. eine Berichterstellungsanwendung, durch die die Liste der verfügbaren Dimensionen abgerufen wird, die zum Erstellen eines Berichts verwendet werden können).  
  
> [!NOTE]  
>  Bei Verwendung von Schemarowsets im XML/A-Skripts, die Informationen, die in zurückgegeben wird die *Ergebnis* Parameter, der die [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) -Methode ist entsprechend der in diesem beschriebenen rowsetspaltenlayouts strukturiert Abschnitt. Vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] XML for Analysis-Anbieter (XMLA) werden die Rowsets unterstützt, die von der XML for Analysis-Spezifikation benötigt werden. Einige der standardmäßigen Schemarowsets für OLE DB, OLE DB für OLAP und OLE DB für Data Mining-Datenquellenanbieter werden vom XMLA-Anbieter ebenfalls unterstützt. Die unterstützten Rowsets werden in den folgenden Themen beschrieben.  

Schemarowsets werden in zwei SQL Server Analysis Services-Protokollen beschrieben:   

[[MS-SSAS-T]: SQL Server Analysis Services Tabular Protocol](https://msdn.microsoft.com/library/mt719260) -beschreibt die Schemarowsets für tabellarische Modelle mit den Kompatibilitätsgraden 1200 und höher.

[[MS-SSAS]: SQL Server Analysis Services-Protokoll](https://msdn.microsoft.com/library/ee320606) -Schemarowsets für mehrdimensionale und tabellarische Modelle mit dem Kompatibilitätsgrad 1100 und 1103 beschreibt.

## <a name="rowsets-described-in-the-ms-ssas-t-sql-server-analysis-services-tabular-protocol"></a>Rowsets, die in der [MS-SSAS-T] beschriebenen: SQL Server Analysis Services Tabular Protocol

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

## <a name="rowsets-described-in-the-ms-ssas-sql-server-analysis-services-protocol"></a>Rowsets, die in der [MS-SSAS] beschriebenen: SQL Server Analysis Services-Protokoll

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

  
  
