---
title: Data Mining-Schemarowsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
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
- schema rowsets [Analysis Services], data mining
- schema rowsets [Analysis Services]
- rowsets [Analysis Services], data mining
- data mining [Analysis Services], schema rowsets
ms.assetid: bd7d5df5-500b-4159-8467-880e141bc043
caps.latest.revision: 43
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1a3b3e54f53eb93ea58a45c92e88503a186a441f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37210050"
---
# <a name="data-mining-schema-rowsets"></a>Data Mining Schema Rowsets
  Ein Server mit [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützt folgende Data mining-Schemarowsets. Verwenden Sie zum Überprüfen, ob ein bestimmter XML/A-Anbieter ein bestimmtes Rowset unterstützt die [DISCOVER_ENUMERATORS](../xml/discover-enumerators-rowset.md) Rowset mit der [ermitteln](../../xmla/xml-elements-methods-discover.md) Methode.  
  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]werden die Data mining Schema Rowsets als Tabellen in der Transact-SQL-Sprache, in dem Schema $SYSTEM verfügbar gemacht werden. Die folgende Abfrage einer Analysis Services-Instanz gibt eine Liste der Schemas zurück, die auf der aktuellen Instanz verfügbar sind.  
  
```  
SELECT * FROM [$system].[DBSCHEMA_TABLES]  
```  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Schemarowset|Description|  
|-------------------|-----------------|  
|[DMSCHEMA_MINING_COLUMNS-Rowset](dmschema-mining-columns-rowset.md)|Beschreibt die einzelnen Spalten aller definierten Data Mining-Modelle, die auf dem Server verteilt werden.|  
|[DMSCHEMA_MINING_FUNCTIONS-Rowset](dmschema-mining-functions-rowset.md)|Beschreibt die Vorhersagefunktionen und Miningfunktionen, die mit jedem Data Mining-Algorithmus verwendet werden können, der auf dem Server installiert ist.|  
|[DMSCHEMA_MINING_MODEL_CONTENT-Rowset](dmschema-mining-model-content-rowset.md)|Ermöglicht es der Clientanwendung, den Inhalt eines trainierten Data Mining-Modells zu durchsuchen.|  
|[DMSCHEMA_MINING_MODEL_CONTENT_PMML-Rowset](dmschema-mining-model-content-pmml-rowset.md)|Gibt die XML-Darstellung (PMML 2.1) des Miningmodellinhalts wieder.|  
|[DMSCHEMA_MINING_MODEL_XML-Rowset](dmschema-mining-model-xml-rowset.md)|Gibt die XML-Struktur (PMML 2.1) des Miningmodells wieder. Dies ist das gleiche Schema wie DMSCHEMA_MINING_MODEL_PMML, das aus Gründen der Abwärtskompatibilität beibehalten wurde.|  
|[DMSCHEMA_MINING_MODELS-Rowset](dmschema-mining-models-rowset.md)|Listet die Data Mining-Modelle auf, die auf dem Server verteilt werden.|  
|[DMSCHEMA_MINING_SERVICE_PARAMETERS-Rowset](dmschema-mining-service-parameters-rowset.md)|Stellt eine Liste von Parametern bereit, die zur Konfiguration des Verhaltens eines jeden auf dem Server installierten Data Mining-Algorithmus verwendet werden kann.|  
|[DMSCHEMA_MINING_SERVICES-Rowset](dmschema-mining-services-rowset.md)|Stellt eine Beschreibung aller Data Mining-Algorithmen bereit, die auf dem Server verfügbar sind.|  
|[DMSCHEMA_MINING_STRUCTURE_COLUMNS-Rowset](dmschema-mining-structure-columns-rowset.md)|Beschreibt die einzelnen Spalten aller Data Mining-Strukturen, die auf dem Server verteilt werden.|  
|[DMSCHEMA_MINING_STRUCTURES-Rowset](dmschema-mining-structures-rowset.md)|Listet Informationen zu Miningstrukturen auf.|  
  
 Alle hier aufgeführten Schemarowsets werden vom Server unterstützt, die ausgeführt wird [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Schemarowsets](../../schema-rowsets/analysis-services-schema-rowsets.md)   
 [Abfragen des SQL Server-Systemkatalogs](https://technet.microsoft.com/en-us/library/ms189082\(v=sql.110\).aspx)   
 [Abfragen der Data Mining-Schemarowsets &#40;Analysis Services – Datamining&#41;](../../data-mining/data-mining-schema-rowsets-ssas.md)  
  
  
