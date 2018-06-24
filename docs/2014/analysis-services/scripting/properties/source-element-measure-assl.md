---
title: Source-Element (Measure) (ASSL) | Microsoft Docs
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
- Source Element (Measure)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Source
helpviewer_keywords:
- Source element
ms.assetid: 9bae7ba4-3065-4623-b3e0-d54cebea7503
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ed41316f62469268d86a89d0c0a5e59f07c8f726
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050852"
---
# <a name="source-element-measure-assl"></a>Source-Element (Measure) (ASSL)
  Enthält die Details der Quelle, die den Wert der [Measure](../objects/measure-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Measure>  
      ...  
   <Source xsi:type="DataItem">...</Source>  
      ...  
</Measure>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Measure](../objects/measure-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die `Source` von der `DataItem`, dem dient als die `Source` von der `Measure`, kann wiederum vom Typ [RowBinding](../data-type/binding-data-type-assl.md), [ColumnBinding](../data-type/columnbinding-data-type-assl.md), [MeasureBinding ](../data-type/measurebinding-data-type-assl.md), oder [CubeDimensionBinding](../data-type/dimensionbinding-data-type-assl.md).  
  
 Weitere Informationen zu den `DataItem` Typ, einschließlich einer Tabelle der ASSL-Objekte und Eigenschaften von der `DataItem` finden Sie unter [DataItem-Datentyp &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 Das übergeordnete Element des entsprechende Element `Source` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Measure>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  