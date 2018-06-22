---
title: OLE DB für OLAP-Schemarowsets | Microsoft Docs
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
helpviewer_keywords:
- schema rowsets [Analysis Services], OLE DB for OLAP
- OLE DB for OLAP schema rowsets
- schema rowsets [OLE DB for OLAP]
- rowsets [Analysis Services], OLE DB for OLAP
ms.assetid: 5fad3ecc-407c-4148-862e-ea6119cc7480
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 898749e17cb5b85e61a2b2c3a94b7247a7ab219b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059265"
---
# <a name="ole-db-for-olap-schema-rowsets"></a>OLE DB für OLAP-Schemarowsets
  Die folgenden OLE DB für OLAP-Schemarowsets werden vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis-Anbieter (XMLA) unterstützt.  
  
> [!NOTE]  
>  Verwenden Sie zum Überprüfen, ob ein bestimmter Datenquellenanbieter ein Rowset unterstützt die `DISCOVER_ENUMERATIONS` Rowset mit der [Discover](../../xmla/xml-elements-methods-discover.md) Methode.  
  
 Sie erhalten auch ausführliche Informationen über diese Rowsets finden Sie im Thema "OLAP-Schemarowsets" Suchen in der MSDN Library auf dieser [Microsoft-Website](http://go.microsoft.com/fwlink/?LinkId=15426).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Schemarowset<sup>1</sup>|Description|  
|-------------------------------|-----------------|  
|[DISCOVER_INSTANCES-Rowset](discover-instances-rowset.md)|Beschreibt die Instanzen auf dem Server.|  
|[DISCOVER_KEYWORDS-Rowset &#40;OLE DB für OLAP&#41;](discover-keywords-rowset-ole-db-for-olap.md)|Listet eine Liste von vom Anbieter reservierten Wörtern auf.|  
|[MDSCHEMA_ACTIONS-Rowset](mdschema-actions-rowset.md)|Beschreibt die Aktionen, die der Clientanwendung möglicherweise zur Verfügung stehen.|  
|[MDSCHEMA_CUBES-Rowset](mdschema-cubes-rowset.md)|Beschreibt die Struktur der Cubes innerhalb einer Datenbank.|  
|[MDSCHEMA_DIMENSIONS-Rowset](mdschema-dimensions-rowset.md)|Beschreibt die freigegebenen und privaten Dimensionen innerhalb einer Datenbank.|  
|[MDSCHEMA_FUNCTIONS-Rowset](mdschema-functions-rowset.md)|Beschreibt die Funktionen, die mit der Datenbank verbundene Clientanwendungen zur Verfügung stehen.|  
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
  
  