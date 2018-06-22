---
title: RelationshipEnd-Datentyp (ASSL) | Microsoft Docs
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
ms.assetid: 3a974dd4-e1d6-45b2-b8c8-1a914bc13a02
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0f201bd910b9fd7f07b04a9b9f30da659dd32f29
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150992"
---
# <a name="relationshipend-data-type-assl"></a>RelationshipEnd-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der ein Beziehungsende in einer Beziehung darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<RelationshipEnd>  
   <Role>...</Role>  
   <Multiplicity>...</Multiplicity>  
   <DimensionID>...</DimensionID>  
   <Attributes>...</Attributes>  
   <Translations>...</Translations>  
   <VisualizationProperties>...</VisualizationProperties>  
</Relationship>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|InclusionThresholdSetting|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Beziehung](relationship-data-type-assl.md)|  
|Untergeordnete Elemente|[Rolle](../../xmla/xml-elements-properties/role-element-xmla.md), [Multiplizität](../properties/multiplicity-element-assl.md), [DimensionID](../properties/id-element-assl.md), [Attribute](../collections/attributes-element-assl.md), [Übersetzungen](../collections/translations-element-assl.md), [VisualizationProperties](relationshipendvisualizationproperties-data-type-assl.md)|  
|Abgeleitete Elemente||  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.RelationshipEnd>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  