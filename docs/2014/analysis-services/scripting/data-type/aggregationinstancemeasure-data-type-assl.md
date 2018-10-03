---
title: AggregationInstanceMeasure-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregationInstanceMeasure Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationInstanceMeasure data type
ms.assetid: 3250970a-a67d-486c-b205-038f1bd1770f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 22c5afdfe38d4068881d8e5611bd2b479121075b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048360"
---
# <a name="aggregationinstancemeasure-data-type-assl"></a>AggregationInstanceMeasure-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der Informationen über ein Measure, das von einer Aggregationsinstanz verwendet wird, darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AggregationInstanceMeasure>  
   <MeasureID>...</MeasureID>  
   <Source>...</Source>  
</AggregationInstanceMeasure>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|None|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[MeasureID](../properties/id-element-assl.md), [Quelle](../properties/source-element-binding-assl.md)|  
|Abgeleitete Elemente|[Measure](../objects/measure-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.AggregationInstanceMeasure>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
