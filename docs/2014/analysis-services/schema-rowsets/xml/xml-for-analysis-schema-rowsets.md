---
title: XML for Analysis-Schemarowsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- rowsets [Analysis Services], XML for Analysis
- XML for Analysis, schema rowsets
- schema rowsets [Analysis Services], XML for Analysis
- schema rowsets [XML for Analysis]
ms.assetid: 36e3ecfd-fcc3-415a-9c43-f59921d2468a
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6c8125b3543e6f3c088ad8b7ae7dd5952d52df26
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159271"
---
# <a name="xml-for-analysis-schema-rowsets"></a>XML for Analysis Schema Rowsets
  Der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XMLA-Anbieter (XML for Analysis) schließt Schemarowsets ein, die Metadaten zu Serverstatus, Aktivität und Objekten zurückgeben. Es ist nötig, Metadaten abzurufen, wenn Sie eine Clientanwendung entwickeln, die eine Verbindung mit einem Analysis Services-Modell herstellt, dessen Struktur und Eigenschaften variabel sind.  
  
 Schemarowsets gewähren auch Einblicke in interne Prozesse und Vorgänge, die Ihnen helfen können, den Server zu überwachen und Probleme zu beheben. Sie können für die meisten Schemarowsets eine DMV-Abfrage (Dynamic Management View, dynamische Verwaltungssicht) ausführen, um administrative Ad-hoc-Aufgaben besser zu unterstützen. DMV-Abfragen geben Ergebnisse in einem lesbaren, tabellarischen Format zurück, das Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] anzeigen können.  
  
 In der folgenden Tabelle sind sämtliche XMLA-Schemarowsets sowie deren Beschreibungen enthalten. Zudem wird darin angegeben, ob Informationen zu tabellarischen Datenmodellen zurückgegeben werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Rowset<sup>1</sup>|Description|  
|------------------------|-----------------|  
|[DISCOVER_CALC_DEPENDENCY-Rowset](discover-calc-dependency-rowset.md)|Gibt Informationen zu Abhängigkeiten unter Tabellen, Spalten, Measures und berechneten Spaltenformeln zurück.<br /><br /> Gilt für tabellarische auf einer Analysis Services-Instanz bereitgestellte Modelle sowie für PowerPivot-Modelle in Excel-Arbeitsmappen, die in einer SharePoint-Umgebung ausgeführt werden.|  
|[DISCOVER_CONNECTIONS-Rowset](discover-connections-rowset.md)|Stellt Informationen zur Ressourcenverwendung und Aktivität der zurzeit geöffneten Verbindungen auf dem Server bereit.|  
|[DISCOVER_COMMAND_OBJECTS-Rowset](discover-command-objects-rowset.md)|Stellt Ressourcenverwendungs- und Aktivitätsinformationen über die Objekte bereit, die durch den Befehl, auf den verwiesen wird, verwendet werden.|  
|[DISCOVER_COMMANDS-Rowset](discover-commands-rowset.md)|Stellt Ressourcenverwendungs- und Aktivitätsinformationen über die zurzeit oder zuletzt ausgeführten Befehle im Rahmen der aktiven Verbindungen auf dem Server bereit.|  
|[DISCOVER_CSDL_METADATA-Rowset](discover-csdl-metadata-rowset.md)|Gibt in einem Client, der ein tabellarisches oder PowerPivot-Modell nutzen und die Quelldaten als Teil eines Berichts präsentieren kann, eine XML-Definition einer Datenquelle zurück.<br /><br /> Gilt für tabellarische auf einer Analysis Services-Instanz bereitgestellte Modelle sowie für PowerPivot-Modelle in Excel-Arbeitsmappen, die in einer SharePoint-Umgebung ausgeführt werden.|  
|[DISCOVER_DATASOURCES-Rowset](discover-datasources-rowset.md)|Gibt eine Liste der XMLA-Anbieterdatenquellen zurück, die auf dem Server oder dem Webdienst verfügbar sind.|  
|[DISCOVER_DB_CONNECTIONS-Rowset](discover-db-connections-rowset.md)|Stellt Informationen zur Ressourcenauslastung und Aktivität der zurzeit geöffneten Verbindungen vom Server in einer Datenbank bereit.|  
|[DISCOVER_DIMENSION_STAT-Rowset](discover-dimension-stat-rowset.md)|Gibt Statistiken zur angegebenen Dimension zurück.|  
|[DISCOVER_ENUMERATORS-Rowset](discover-enumerators-rowset.md)|Gibt eine Liste mit Namen, Datentypen und Enumerationswerten von Enumeratoren zurück, die vom XMLA-Anbieter für eine bestimmte Datenquelle unterstützt werden.|  
|[DISCOVER_JOBS-Rowset](discover-jobs-rowset.md)|Stellt Informationen über die aktiven Aufträge bereit, die auf dem Server ausgeführt werden.|  
|[DISCOVER_KEYWORDS-Rowset &#40;XMLA&#41;](discover-keywords-rowset-xmla.md)|Gibt Informationen über vom XMLA-Anbieter reservierte Schlüsselwörter zurück.|  
|[DISCOVER_LITERALS-Rowset](discover-literals-rowset.md)|Gibt Informationen zu Literalen zurück, einschließlich Datentypen und Werten, die vom XMLA-Anbieter unterstützt werden.|  
|[DISCOVER_LOCATIONS-Rowset](discover-locations-rowset.md)|Gibt Informationen zum Inhalt einer Sicherungsdatei zurück.|  
|[DISCOVER_LOCKS-Rowset](discover-locks-rowset.md)|Stellt Informationen über die aktuellen Sperren auf dem Server bereit.|  
|[DISCOVER_MEMORYGRANT-Rowset](discover-memorygrant-rowset.md)|Gibt eine Liste interner Arbeitsspeicherkontingent-Erteilungen zurück, die von Aufträgen in Anspruch genommen werden, die derzeit auf dem Server ausgeführt werden.|  
|[DISCOVER_MEMORYUSAGE-Rowset](discover-memoryusage-rowset.md)|Gibt die Speicherauslastungsstatistiken für verschiedene vom Server zugeordnete Objekte zurück.|  
|[DISCOVER_OBJECT_ACTIVITY-Rowset](discover-object-activity-rowset.md)|Stellt die Ressourcenverwendung pro Objekt seit dem Start des Diensts bereit.|  
|[DISCOVER_OBJECT_MEMORY_USAGE-Rowset](discover-object-memory-usage-rowset.md)|Stellt Informationen über von Objekten verwendete Speicherressourcen bereit.|  
|[DISCOVER_PARTITION_DIMENSION_STAT-Rowset](discover-partition-dimension-stat-rowset.md)|Gibt Statistiken für die Dimension, die einer Partition zugeordnet ist.|  
|[DISCOVER_PARTITION_STAT-Rowset](discover-partition-stat-rowset.md)|Gibt Statistiken zu Aggregationen in einer bestimmten Partition zurück.|  
|[DISCOVER_PERFORMANCE_COUNTERS-Rowset](discover-performance-counters-rowset.md)|Gibt den Wert von mindestens einem angegebenen Leistungsindikator zurück.|  
|[DISCOVER_PROPERTIES-Rowset](discover-properties-rowset.md)|Gibt eine Liste mit Informationen und Werten zu den standardmäßigen und anwenderspezifischen Eigenschaften zurück, die vom XMLA-Anbieter für die angegebene Datenquelle unterstützt werden.|  
|[DISCOVER_SCHEMA_ROWSETS-Rowsets](discover-schema-rowsets-rowset.md)|Gibt die Namen, Einschränkungen, Beschreibungen und anderen Informationen für alle Enumerationswerte und zusätzliche anbieterspezifische Enumerationswerte zurück, die vom XMLA-Anbieter unterstützt werden.|  
|[DISCOVER_SESSIONS-Rowset](discover-sessions-rowset.md)|Stellt Informationen zur Ressourcenverwendung und Aktivität der zurzeit geöffneten Sitzungen auf dem Server bereit.|  
|[DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS-Rowset](discover-storage-table-column-segments-rowset.md)|Stellt Informationen zu Speichertabellen auf Spalten- und Segmentebene bereit, die von einer tabellarischen oder PowerPivot-Datenbank verwendet werden.<br /><br /> Gilt für tabellarische auf einer Analysis Services-Instanz bereitgestellte Modelle sowie für PowerPivot-Modelle in Excel-Arbeitsmappen, die in einer SharePoint-Umgebung ausgeführt werden.|  
|[DISCOVER_STORAGE_TABLE_COLUMNS-Rowset](discover-storage-table-columns-rowset.md)|Ermöglicht dem Client die Zuweisung von Spalten zu Speichertabellen, die von einer tabellarischen oder PowerPivot-Datenbank verwendet wurden.<br /><br /> Gilt für tabellarische auf einer Analysis Services-Instanz bereitgestellte Modelle sowie für PowerPivot-Modelle in Excel-Arbeitsmappen, die in einer SharePoint-Umgebung ausgeführt werden.|  
|[DISCOVER_STORAGE_TABLES-Rowset](discover-storage-tables-rowset.md)|Gibt Informationen zu den in einem Modell verwendeten Tabellen zurück.<br /><br /> Gilt für tabellarische auf einer Analysis Services-Instanz bereitgestellte Modelle sowie für PowerPivot-Modelle in Excel-Arbeitsmappen, die in einer SharePoint-Umgebung ausgeführt werden.|  
|[DISCOVER_TRACE_COLUMNS-Rowset](discover-trace-columns-rowset.md)|Beschreibt die vom Ablaufverfolgungsanbieter bereitgestellten Ablaufverfolgungsspalten.|  
|[DISCOVER_TRACE_DEFINITION_PROVIDERINFO-Rowset](discover-trace-definition-providerinfo-rowset.md)|Gibt grundlegende Informationen zum Ablaufverfolgungsanbieter zurück, beispielsweise dessen Name und Beschreibung.|  
|[DISCOVER_TRACE_EVENT_CATEGORIES-Rowset](discover-trace-event-categories-rowset.md)|Beschreibt die vom Ablaufverfolgungsanbieter bereitgestellten Ereigniskategorien.|  
|[DISCOVER_TRACES-Rowset](discover-traces-rowset.md)|Gibt Informationen zu Ablaufverfolgungen zurück, die auf einem Server ausgeführt werden.|  
|[DISCOVER_TRANSACTIONS-Rowset](discover-transactions-rowset.md)|Gibt den aktuellen Satz von ausstehenden Transaktionen auf dem System zurück.|  
|[DISCOVER_XML_METADATA-Rowset](discover-xml-metadata-rowset.md)|Gibt ein XML-Dokument zurück, in dem ein angefordertes Objekt beschrieben wird.|  
  
 <sup>1</sup> alle hier aufgeführten Rowsets werden von der MSOLAP-Datenquellenanbieter für unterstützt die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XMLA-Anbieter.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln mit XMLA in Analysis Services](../../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)   
 [Verwenden von dynamischen Verwaltungssichten &#40;DMVs&#41; zum Überwachen von Analysis Services](../../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)   
 [Abrufen von Metadaten aus einer analytischen Datenquelle](../../multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
  
