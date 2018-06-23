---
title: ClassifiedColumns-Element (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ClassifiedColumns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ClassifiedColumns
helpviewer_keywords:
- ClassifiedColumns element
ms.assetid: f16b4f51-c38d-4601-98b8-1497dbf12d02
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 95c00f4863223caaacfb7cc7554ec9b48a82922d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060592"
---
# <a name="classifiedcolumns-element-assl"></a>ClassifiedColumns-Element (ASSL)
  Enthält die Auflistung der verknüpften Spalten, die von klassifiziert werden die [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningStructureColumn xsi:type="ScalarMiningStructureColumn">  
   ...  
   <ClassifiedColumns>  
      <ClassifiedColumnID>...</ClassifiedColumnID>  
   </ClassifiedColumns>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) des Typs[ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Untergeordnete Elemente|[ClassifiedColumnID](../properties/id-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das das übergeordnete Element des entspricht `ClassifiedColumns` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Siehe auch  
 [MiningStructureColumn-Datentyp &#40;ASSL&#41;](../data-type/miningstructurecolumn-data-type-assl.md)   
 [MiningStructure-Element &#40;ASSL&#41;](../objects/miningstructure-element-assl.md)   
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  