---
title: AggregationAttribute-Datentyp (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f70849c878feb95eab4e55b41ce7a203721ab294
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="aggregationattribute-data-type-assl"></a>AggregationAttribute-Datentyp (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert den Grunddatentyp, der die Zuordnung zwischen einem [Aggregation](../../../analysis-services/scripting/objects/aggregation-element-assl.md) -Element und einem Attribut darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AggregationAttribute>  
   <AttributeID>...</AttributeID>  
      <Annotations>...</Annotations>  
</AggregationAttribute>  
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
|Untergeordnete Elemente|[AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md), [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
|Abgeleitete Elemente|[Attribute](../../../analysis-services/scripting/objects/attribute-element-assl.md) ([Attributes](../../../analysis-services/scripting/collections/attributes-element-assl.md) -Auflistung von [AggregationDimension](../../../analysis-services/scripting/data-type/aggregationdimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Die entsprechende Klasse im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.AggregationAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Aggregation-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/aggregation-element-assl.md)   
 [Analysis Services Scripting Language-XML-Datentypen & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
