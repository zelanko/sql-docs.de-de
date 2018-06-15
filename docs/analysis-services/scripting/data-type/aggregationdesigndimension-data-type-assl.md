---
title: AggregationDesignDimension-Datentyp (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e83cc8c14e533d67eeab0f9a3d73926fd8f2ac5a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032941"
---
# <a name="aggregationdesigndimension-data-type-assl"></a>AggregationDesignDimension-Datentyp (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert einen Grunddatentyp, der die Beziehung zwischen einer Cubedimension und einem [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md) -Element darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AggregationDesignDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
   <Attributes>...</Attributes>  
      <Annotations>...</Annotations>  
</AggregationDesignDimension>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Basisdatentypen|Keine|  
|Abgeleitete Datentypen|Keine|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|Keine|  
|Untergeordnete Elemente|[Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [Attributes](../../../analysis-services/scripting/collections/attributes-element-assl.md), [CubeDimensionID](../../../analysis-services/scripting/properties/cubedimensionid-element-assl.md)|  
|Abgeleitete Elemente|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md) ([Dimensions](../../../analysis-services/scripting/collections/dimensions-element-assl.md) -Auflistung von [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.AggregationDesignDimension>.  
  
## <a name="see-also"></a>Siehe auch  
 [AggregationDesign-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)   
 [Analysis Services Scripting Language-XML-Datentypen & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
