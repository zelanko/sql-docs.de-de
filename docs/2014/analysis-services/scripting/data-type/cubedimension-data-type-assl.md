---
title: CubeDimension-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CubeDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeDimension
helpviewer_keywords:
- CubeDimension data type
ms.assetid: 128ac790-65a1-4e35-b909-8dba2a61b24c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c3ea688681749a2b22f8c457fb9a5eb8ee39d8eb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059519"
---
# <a name="cubedimension-data-type-assl"></a>CubeDimension-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der die Beziehung zwischen einer Dimension und einem Cube darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CubeDimension>  
      <ID>...</ID>  
   <Name>...</Name>  
   <Translations>...</Translations>  
   <DimensionID>...</DimensionID>  
   <Visible>...</Visible>  
   <AllMemberAggregationUsage>...</AllMemberAggregationUsage>  
   <HierarchyUniqueNameStyle>...</HierarchyUniqueNameStyle>  
   <MemberUniqueNameStyle>...</MemberUniqueNameStyle>  
      <Attributes>...</Attributes>  
   <Hierarchies>...</Hierarchies>  
      <Annotations>...</Annotation>  
</CubeDimension>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|None|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[AllMemberAggregationUsage](../properties/aggregationusage-element-assl.md), [Anmerkungen](../collections/annotations-element-assl.md), [Attribute](../collections/attributes-element-assl.md), [DimensionID](../properties/id-element-assl.md), [Hierarchien](../collections/hierarchies-element-assl.md), [HierarchyUniqueNameStyle](../properties/hierarchyuniquenamestyle-element-assl.md), [ID](../properties/id-element-assl.md), [MemberUniqueNameStyle](../properties/memberuniquenamestyle-element-assl.md), [Namen](../properties/name-element-assl.md), [sichtbar](../properties/visible-element-assl.md), [Übersetzungen](../collections/translations-element-assl.md)|  
|Abgeleitete Elemente|[Dimension](../objects/dimension-element-assl.md) ([Dimensionen](../collections/dimensions-element-assl.md) Auflistung von [Cube](../objects/cube-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Es gibt eine `CubeDimension` für jede Dimensionsbeziehung auf einem `Cube`. Die `CubeDimension` deckt alle die `MeasureGroups` des Cubes.  
  
 Ein `CubeDimension` müssen eine [CubeHierarchy](hierarchy-data-type-assl.md) , wenn die Dimension bestimmte Aussagen über die Hierarchie treffen kann, darunter Deaktivieren der Hierarchie (können und dabei auswählen von Hierarchien, die auf einen bestimmten gilt Dimensionsverwendung), oder Ausblenden der Hierarchie.  
  
 Auf ähnliche Weise eine `CubeDimension` müssen eine [CubeAttribute](cubeattribute-data-type-assl.md) nur dann, wenn die Dimension bestimmte Aussagen über das Attribut verfügt. (Es kann nicht ausgewählt werden, für welche Attribute eine bestimmte Dimensionsverwendung gilt, jedoch können Attribute ausgeblendet werden.)  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
