---
title: RegularMeasureGroupDimension-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- RegularMeasureGroupDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RegularMeasureGroupDimension
helpviewer_keywords:
- RegularMeasureGroupDimension data type
ms.assetid: 5c4ce400-6d7c-40fc-9bcb-392718b77182
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 072ada60b803f4c8adfde73a228144a4d0157dff
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051813"
---
# <a name="regularmeasuregroupdimension-data-type-assl"></a>RegularMeasureGroupDimension-Datentyp (ASSL)
  Definiert einen abgeleiteten Datentyp, der eine reguläre Beziehung zwischen einer Dimension und einer Measuregruppe darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<RegularMeasureGroupDimension>  
   <!-- The following elements extend MeasureGroupDimension -->  
   <Cardinality>...</Cardinality>  
   <Attributes>...</Attributes>  
</RegularMeasureGroupDimension>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[MeasureGroupDimension](dimension-data-type-assl.md)|  
|Abgeleitete Datentypen|[ReferenceMeasureGroupDimension](measuregroupdimension-data-type-assl.md), [DegenerateMeasureGroupDimension](degeneratemeasuregroupdimension-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[Attribute](../collections/attributes-element-assl.md), [Kardinalität](../properties/cardinality-element-assl.md)|  
|Abgeleitete Elemente|[Dimension](../objects/dimension-element-assl.md) ([Dimensionen](../collections/dimensions-element-assl.md) Auflistung)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.RegularMeasureGroupDimension>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
