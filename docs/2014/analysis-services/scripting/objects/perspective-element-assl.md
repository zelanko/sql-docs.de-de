---
title: Perspective-Element (ASSL) | Microsoft-Dokumentation
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
- Perspective Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Perspective
helpviewer_keywords:
- Perspective element
ms.assetid: 0442334c-8b00-4451-ad81-02e58c735e8f
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3b006d7d48c072cb98a68e42c04cf75c4aaa9e04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297400"
---
# <a name="perspective-element-assl"></a>Perspective-Element (ASSL)
  Details für eine Perspektive definiert eine [Cube](cube-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Perspectives>  
   <<Perspective>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <Translations>...</Translations>  
      <DefaultMeasure>...</DefaultMeasure>  
      <Dimensions>...</Dimensions>  
            <MeasureGroups>...</MeasureGroups>  
      <Calculations>...</Calculations>  
      <Kpis>...</Kpis>  
            <Actions>...</Actions>  
      <Annotations>...</Annotations>  
   </Perspective>  
</Perspectives>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Perspektiven](../collections/perspectives-element-assl.md)|  
|Untergeordnete Elemente|[Aktionen](../collections/actions-element-assl.md), [Anmerkungen](../collections/annotations-element-assl.md), [Berechnungen](../collections/calculations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [DefaultMeasure](measure-element-assl.md), [ Beschreibung](../properties/description-element-assl.md), [Dimensionen](../collections/dimensions-element-assl.md), [ID](../properties/id-element-assl.md), [Kpis](../collections/kpis-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [ MeasureGroups](../collections/groups-element-assl.md), [Namen](../properties/name-element-assl.md), [Übersetzungen](../collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Eine Perspektive bietet eine Untermenge eines Cubes, indem sie die einzubeziehenden Dimensionen, Hierarchien, Attribute und anderen Details auswählt und einen einzubeziehenden Datenslice definiert. Eine Perspektive gehört einem einzelnen Cube. Objekte innerhalb einer Perspektive können nicht überschrieben oder hinzugefügt werden; alle Dimensionen, Hierarchien und anderen Details müssen im zugrunde liegenden Cube existieren. Es ist nicht möglich, Objekte einzuschließen und sie als nicht sichtbar zu markieren.  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.Perspective>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
