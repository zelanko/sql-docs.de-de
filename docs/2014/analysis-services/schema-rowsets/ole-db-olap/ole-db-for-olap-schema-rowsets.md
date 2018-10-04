---
title: OLE DB für OLAP-Schemarowsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- schema rowsets [Analysis Services], OLE DB for OLAP
- OLE DB for OLAP schema rowsets
- schema rowsets [OLE DB for OLAP]
- rowsets [Analysis Services], OLE DB for OLAP
ms.assetid: 5fad3ecc-407c-4148-862e-ea6119cc7480
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bd2e29e03617ccc3929ca0845e2b703e406cbfb2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172970"
---
# <a name="ole-db-for-olap-schema-rowsets"></a>OLE DB für OLAP-Schemarowsets
  Die folgenden OLE DB für OLAP-Schemarowsets werden vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis-Anbieter (XMLA) unterstützt.  
  
> [!NOTE]  
>  Um zu überprüfen, ob ein bestimmter Datenquellenanbieter ein Rowset unterstützt, verwenden die `DISCOVER_ENUMERATIONS` Rowset mit der [ermitteln](../../xmla/xml-elements-methods-discover.md) Methode.  
  
 Sie erhalten auch detaillierte Informationen über diese Rowsets durch Suchen im Thema "OLAP Schema Rowsets" in der MSDN Library auf dieser [Microsoft-Website](http://go.microsoft.com/fwlink/?LinkId=15426).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Schemarowsets<sup>1</sup>|Description|  
|-------------------------------|-----------------|  
|[DISCOVER_INSTANCES-Rowset](discover-instances-rowset.md)|Beschreibt die Instanzen auf dem Server.|  
|[DISCOVER_KEYWORDS-Rowset &#40;OLE DB für OLAP&#41;](discover-keywords-rowset-ole-db-for-olap.md)|Listet eine Liste von vom Anbieter reservierten Wörtern auf.|  
|[MDSCHEMA_ACTIONS-Rowset](mdschema-actions-rowset.md)|Beschreibt die Aktionen, die der Clientanwendung möglicherweise zur Verfügung stehen.|  
|[MDSCHEMA_CUBES-Rowset](mdschema-cubes-rowset.md)|Beschreibt die Struktur der Cubes innerhalb einer Datenbank.|  
|[MDSCHEMA_DIMENSIONS-Rowset](mdschema-dimensions-rowset.md)|Beschreibt die freigegebenen und privaten Dimensionen innerhalb einer Datenbank.|  
|[MDSCHEMA_FUNCTIONS-Rowset](mdschema-functions-rowset.md)|Beschreibt die Funktionen, die in der Datenbank verbundene Clientanwendungen zur Verfügung stehen.|  
|[MDSCHEMA_HIERARCHIES-Rowset](mdschema-hierarchies-rowset.md)|Beschreibt jede Hierarchie, die in einer bestimmten Dimension enthalten ist.|  
|[MDSCHEMA_INPUT_DATASOURCES-Rowset](mdschema-input-datasources-rowset.md)|Beschreibt die innerhalb der Datenbank definierten Datenquellen.|  
|[MDSCHEMA_KPIS-Rowset](mdschema-kpis-rowset.md)|Beschreibt die Key Performance Indicators (KPIs) innerhalb einer Datenbank.|  
|[MDSCHEMA_LEVELS-Rowset](mdschema-levels-rowset.md)|Beschreibt jede Ebene innerhalb einer bestimmten Hierarchie.|  
|[MDSCHEMA_MEASUREGROUP_DIMENSIONS-Rowset](mdschema-measuregroup-dimensions-rowset.md)|Listet die Dimensionen der Measuregruppe auf.|  
|[MDSCHEMA_MEASUREGROUPS-Rowset](mdschema-measuregroups-rowset.md)|Beschreibt die Measuregruppen innerhalb einer Datenbank.|  
|[MDSCHEMA_MEASURES-Rowset](mdschema-measures-rowset.md)|Beschreibt jedes Measure in einem Cube.|  
|[MDSCHEMA_MEMBERS-Rowset](mdschema-members-rowset.md)|Beschreibt die Elemente innerhalb einer Datenbank.|  
|[MDSCHEMA_PROPERTIES-Rowset](mdschema-properties-rowset.md)|Beschreibt die Eigenschaften von Elementen in einer Datenbank.|  
|[MDSCHEMA_SETS-Rowset](mdschema-sets-rowset.md)|Beschreibt alle Sätze, die zurzeit in einer Datenbank definiert werden, einschließlich Sätzen im Bereich einer Sitzung.|  
  
 <sup>1</sup> alle hier aufgeführten Rowsets werden von der MSOLAP-Datenquellenanbieter für unterstützt die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XMLA-Anbieter.  
  
## <a name="see-also"></a>Siehe auch  
 [DISCOVER_ENUMERATORS-Rowset](../xml/discover-enumerators-rowset.md)   
 [Analysis Services-Schemarowsets](../../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
