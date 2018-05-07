---
title: MeasureGroupAttributeBinding-Datentyp (Out-of-Line) (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 623de08bdac340eb3fadccb73c5e5f5c293afdd6
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="measuregroupattributebinding-data-type-out-of-line-assl"></a>MeasureGroupAttributeBinding-Datentyp (Out-of-Line) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert einen abgeleiteten Datentyp, der die Out-of-Line-Bindung eines Attributs in einer Dimension, die in einer Measuregruppe enthalten ist, darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MeasureGroupAttributeBinding>  
   <!-- The following elements extend Binding -->  
   <DatabaseID>...</DatabaseID>  
   <CubeID>...</CubeID>  
   <MeasureGroupID>...</MeasureGroupID>  
   <GranularityAttributeID>...</GranularityAttributeID>  
   <Source>...</Source>  
</MeasureGroupAttributeBinding>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Basisdatentypen|[Bindung](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|Abgeleitete Datentypen|Keine|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|Keine|  
|Untergeordnete Elemente|[CubeID](../../../analysis-services/scripting/properties/cubeid-element-assl.md), [DatabaseID](../../../analysis-services/xmla/xml-elements-properties/databaseid-element-xmla.md), [MeasureGroupID](../../../analysis-services/scripting/properties/measuregroupid-element-assl.md), [GranularityAttributeID](../../../analysis-services/scripting/properties/granularityattributeid-element-assl.md), [Quelle](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|  
|Abgeleitete Elemente|[Binden von](../../../analysis-services/xmla/xml-elements-properties/binding-element-xmla.md) ([Bindungen](../../../analysis-services/scripting/collections/attributes-element-assl.md) Auflistung von XML for Analysis (XMLA) [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) und [Prozess](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) Befehle)|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen über Out-of-Line-Bindungen finden Sie unter [& #40; Datenquellen und Bindungen SSAS – mehrdimensional & #41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
