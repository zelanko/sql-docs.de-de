---
title: CubeDimension-Datentyp (ASSL) | Microsoft Docs
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
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4a043895929e09a59d3ae14c5995804c4fa5c7eb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047303"
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
|Basisdatentypen|InclusionThresholdSetting|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[AllMemberAggregationUsage](../properties/aggregationusage-element-assl.md), [Anmerkungen](../collections/annotations-element-assl.md), [Attribute](../collections/attributes-element-assl.md), [DimensionID](../properties/id-element-assl.md), [Hierarchien](../collections/hierarchies-element-assl.md), [HierarchyUniqueNameStyle](../properties/hierarchyuniquenamestyle-element-assl.md), [ID](../properties/id-element-assl.md), [MemberUniqueNameStyle](../properties/memberuniquenamestyle-element-assl.md), [Namen](../properties/name-element-assl.md), [sichtbar](../properties/visible-element-assl.md), [Übersetzungen](../collections/translations-element-assl.md)|  
|Abgeleitete Elemente|[Dimension](../objects/dimension-element-assl.md) ([Dimensionen](../collections/dimensions-element-assl.md) Auflistung von [Cube](../objects/cube-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Es gibt eine `CubeDimension` für jede Dimensionsbeziehung auf einem `Cube`. Die `CubeDimension` deckt alle die `MeasureGroups` des Cubes.  
  
 Ein `CubeDimension` umfasst eine [CubeHierarchy](hierarchy-data-type-assl.md) , wenn die Dimension etwas bestimmtes über die Hierarchie treffen kann, darunter Deaktivieren der Hierarchie (, wodurch der Hierarchien, gelten für eine bestimmte Auswahl Dimensionsverwendung), oder die Hierarchie unsichtbar zu machen.  
  
 Auf ähnliche Weise eine `CubeDimension` umfasst eine [CubeAttribute](cubeattribute-data-type-assl.md) nur, wenn die Dimension bestimmte Aussagen über das Attribut treffen. (Es kann nicht ausgewählt werden, für welche Attribute eine bestimmte Dimensionsverwendung gilt, jedoch können Attribute ausgeblendet werden.)  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  