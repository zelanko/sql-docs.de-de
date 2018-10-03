---
title: Technische Referenz für BI-Anmerkungen zu CSDL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 63b3e069-6ba5-474e-b769-47b7cc87b7dd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6e0a166f1c81b9e010d7e9cfd7a0547c3a4b9c72
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094190"
---
# <a name="technical-reference-for-bi-annotations-to-csdl"></a>Technische Referenz für BI-Anmerkungen zu CSDL
  In diesem Abschnitt sind die Elemente, Attribute, und Eigenschaften in CSDL auf, die verwendet werden, um darzustellen [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] tabellarische Modelle. Einige Elemente sind neu; andere wurden mit Anmerkungen versehen oder zur Unterstützung von Business Intelligence-Modellen erweitert.  
  
 Eine Übersicht über tabellarische Modelle und wie die Entitäten, Beziehungen und Formeln in CSDL dargestellt werden, finden Sie unter [CSDL-Anmerkungen für Business Intelligence &#40;CSDLBI&#41;](../csdl-annotations-for-business-intelligence-csdlbi.md).  
  
## <a name="extended-csdl-elements-complex-types"></a>Erweiterte CSDL-Elemente: Komplexe Typen  
 Die folgenden CSDL-Elemente wurden hinzugefügt oder erweitert, um tabellarische und mehrdimensionale Business Intelligence-Modelle zu unterstützen.  
  
-   [AssociationSet-Element &#40;CSDLBI&#41;](associationset-element-csdlbi.md)  
  
-   [BaseProperty-Element &#40;CSDLBI&#41;](property-element-csdlbi.md)  
  
-   [DefaultDetails-Element &#40;CSDLBI&#41;](defaultdetails-element-csdlbi.md)  
  
-   [DisplayKey-Element &#40;CSDLBI&#41;](displaykey-element-csdlbi.md)  
  
-   [EntityContainer-Element &#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)  
  
-   [EntitySet-Element &#40;CSDLBI&#41;](entityset-element-csdlbi.md)  
  
-   [EntityType-Element &#40;CSDLBI&#41;](entitytype-element-csdlbi.md)  
  
-   [Hierarchy-Element &#40;CSDLBI&#41;](hierarchy-element-csdlbi.md)  
  
-   [KPI-Element &#40;CSDLBI&#41;](kpi-element-csdlbi.md)  
  
-   [KpiGoal-Element &#40;CSDLBI&#41;](kpigoal-element-csdlbi.md)  
  
-   [KpiStatus-Element &#40;CSDLBI&#41;](kpistatus-element-csdlbi.md)  
  
-   [Level-Element &#40;CSDLBI&#41;](level-element-csdlbi.md)  
  
-   [Measure-Element &#40;CSDLBI&#41;](measure-element-csdlbi.md)  
  
-   [Member-Element &#40;CSDLBI&#41;](member-element-csdlbi.md)  
  
-   [MemberRef-Element &#40;CSDLBI&#41;](memberref-element-csdlbi.md)  
  
-   [NavigationProperty-Element &#40;CSDLBI&#41;](navigationproperty-element-csdlbi.md)  
  
-   [Property-Element &#40;CSDLBI&#41;](property-element-csdlbi.md)  
  
-   [PropertyRef-Element &#40;CSDLBI&#41;](propertyref-element-csdlbi.md)  
  
## <a name="simple-type-and-subtypes"></a>Einfacher Typ und Untertypen  
 Die folgende Tabelle enthält einige einfache Typen sowie einige untergeordnete komplexe Typen, die in den Definitionen der oben aufgeführten komplexen Typen enthalten sind. Die Dokumentation für die in der linken Spalte aufgeführten einfachen Typen oder Untertypen wird bei den übergeordneten Elementen in der rechten Spalte bereitgestellt.  
  
|Einfacher Typ|Aus dem Thema|  
|-----------------|--------------------|  
|Ausrichtung|[BaseProperty-Element &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|CompareOptions|[EntityContainer-Element &#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)|  
|Inhalt|[EntityType-Element &#40;CSDLBI&#41;](entitytype-element-csdlbi.md)|  
|ContextualNameRule|[Member-Element &#40;CSDLBI&#41;](member-element-csdlbi.md)|  
|DefaultAggregationFunction|[Property-Element &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|DirectQueryMode|[EntityContainer-Element &#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)|  
|GroupingBehavior|[Property-Element &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|MemberRefs|[MemberRef-Element &#40;CSDLBI&#41;](memberref-element-csdlbi.md)|  
|PropertyRefs|[PropertyRef-Element &#40;CSDLBI&#41;](propertyref-element-csdlbi.md)|  
|SortDirection|[BaseProperty-Element &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|Status|[AssociationSet-Element &#40;CSDLBI&#41;](associationset-element-csdlbi.md)|  
|Stability|[Property-Element &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|SortDirection|[BaseProperty-Element &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [CSDLBI-Konzepte](../csdlbi-concepts.md)  
  
  
