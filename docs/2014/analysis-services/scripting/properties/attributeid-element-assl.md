---
title: AttributeID-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AttributeID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeID
helpviewer_keywords:
- AttributeID element
ms.assetid: 13d2e92b-e4bf-4f2d-b34c-a6f483da3a9e
caps.latest.revision: 43
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 666bfadbcf08c9154796cd155c05fb1a7f2e79c9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169479"
---
# <a name="attributeid-element-assl"></a>AttributeID-Element (ASSL)
  Enthält die ID des Attributs, das dem übergeordneten Element zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AggregationAttribute> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <AttributeID>...</AttributeID>  
   ...  
</AggregationAttribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[AggregationAttribute](../data-type/aggregationattribute-data-type-assl.md), [AggregationDesignAttribute](../data-type/aggregationdesignattribute-data-type-assl.md), [AggregationInstanceAttribute](../data-type/aggregationinstanceattribute-data-type-assl.md), [AttributeBinding](../data-type/binding-data-type-assl.md), [ AttributePermission](../objects/attributepermission-element-assl.md), [AttributeRelationship](../objects/attributerelationship-element-assl.md), [CubeAttribute](../data-type/cubeattribute-data-type-assl.md), [CubeAttributeBinding](../data-type/cubeattributebinding-data-type-assl.md), [ DimensionAttributeBinding](../data-type/dimensionattributebinding-data-type-out-of-line-assl.md), [MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md), [MeasureGroupAttributeBinding](../data-type/measuregroupattributebinding-data-type-out-of-line-assl.md), [PerspectiveAttribute](../data-type/perspectiveattribute-data-type-assl.md), [ UserDefinedGroupBinding](../data-type/userdefinedgroupbinding-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die Elemente, die den übergeordneten Elementen von entsprechen `AttributeID` im Analysis Management Objects (AMO)-Objektmodell werden <xref:Microsoft.AnalysisServices.AggregationAttribute>, <xref:Microsoft.AnalysisServices.AggregationDesignAttribute>, <xref:Microsoft.AnalysisServices.AggregationInstanceAttribute>, <xref:Microsoft.AnalysisServices.AttributeBinding>, <xref:Microsoft.AnalysisServices.AttributePermission>, <xref:Microsoft.AnalysisServices.AttributeRelationship>, <xref:Microsoft.AnalysisServices.CubeAttribute>, <xref:Microsoft.AnalysisServices.CubeAttributeBinding>, <xref:Microsoft.AnalysisServices.PerspectiveAttribute>, und <xref:Microsoft.AnalysisServices.UserDefinedGroupBinding>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
