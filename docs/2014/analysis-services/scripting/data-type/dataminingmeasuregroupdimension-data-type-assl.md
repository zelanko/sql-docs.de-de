---
title: DataMiningMeasureGroupDimension-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataMiningMeasureGroupDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataMiningMeasureGroupDimension
helpviewer_keywords:
- DataMiningMeasureGroupDimension data type
ms.assetid: 56d5c2ec-7e03-4dc7-a668-c8d598d59e55
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9f92fb25375c3741b06ad873ac5f9facd6585570
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171830"
---
# <a name="dataminingmeasuregroupdimension-data-type-assl"></a>DataMiningMeasureGroupDimension-Datentyp (ASSL)
  Definiert einen abgeleiteten Datentyp, der die Beziehung zwischen einer Measuregruppe und einer Data Mining-Dimension darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataMiningMeasureGroupDimension>  
   <!-- The following elements extend MeasureGroupDimension -->  
      <CaseCubeDimensionID>...</CaseCubeDimensionID>  
</DataMiningMeasureGroupDimension>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[MeasureGroupDimension](dimension-data-type-assl.md)|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[CaseCubeDimensionID](../properties/id-element-assl.md)|  
|Abgeleitete Elemente|Finden Sie unter [Dimension](../objects/dimension-element-assl.md) ([Dimensionen](../collections/dimensions-element-assl.md) Auflistung von [MeasureGroup](../objects/group-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.DataMiningMeasureGroupDimension>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
