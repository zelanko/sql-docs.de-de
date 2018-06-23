---
title: ManyToManyMeasureGroupDimension-Datentyp (ASSL) | Microsoft Docs
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
- ManyToManyMeasureGroupDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ManyToManyMeasureGroupDimension
helpviewer_keywords:
- ManyToManyMeasureGroupDimension data type
ms.assetid: f2b914cb-c817-43ff-9cb4-ac8d326136b5
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 14233f2e39771174b4d1b15acdeafb76bc76f32d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061036"
---
# <a name="manytomanymeasuregroupdimension-data-type-assl"></a>ManyToManyMeasureGroupDimension-Datentyp (ASSL)
  Definiert einen abgeleiteten Datentyp, der die Beziehung zwischen einer m:n-Dimension und einer Measuregruppe darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ManyToManyMeasureGroupDimension>  
   <!-- The following elements extend MeasureGroupDimension -->  
   <MeasureGroupID>...</MeasureGroupID>  
   <DefaultMember>...</DefaultMember>  
</ManyToManyMeasureGroupDimension>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[MeasureGroupDimension](dimension-data-type-assl.md)|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[DefaultMember](../objects/member-element-assl.md), [MeasureGroupID](../properties/id-element-assl.md)|  
|Abgeleitete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.ManyToManyMeasureGroupDimension>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  