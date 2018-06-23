---
title: StorageMode-Element (ASSL) | Microsoft Docs
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
- StorageMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- StorageMode
helpviewer_keywords:
- StorageMode element
ms.assetid: 197e8153-1ab6-43ba-a7e9-ae9be19ac511
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0d65d778e54a712e3fce18bdac5b3a0e31426863
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148474"
---
# <a name="storagemode-element-assl"></a>StorageMode-Element (ASSL)
  Bestimmt den Speichermodus für das übergeordnete Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <StorageMode>...</StorageMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*MOLAP*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Cube-Element &#40;ASSL&#41;](../objects/cube-element-assl.md), [Dimension-Element &#40;ASSL&#41;](../objects/dimension-element-assl.md), [MeasureGroup-Element &#40;ASSL&#41;](../objects/group-element-assl.md), [Partition Element &#40;ASSL&#41;](../objects/partition-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*MOLAP*|Das übergeordnete Element verwendet die mehrdimensionale OLAP (MOLAP)-Speicherung.|  
|*ROLAP*|Das übergeordnete Element verwendet die relationale OLAP (ROLAP)-Speicherung.|  
|*HOLAP*|Das übergeordnete Element verwendet die hybride OLAP (HOLAP)-Speicherung. **Hinweis:** dieser Wert gilt nicht für [Dimension](../objects/dimension-element-assl.md) übergeordneten Elementen.|  
|*InMemory*|Das übergeordnete Element verwendet IMBI-Speicher.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `StorageMode` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.StorageMode>.  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `StorageMode` im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MeasureGroup>, und <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  