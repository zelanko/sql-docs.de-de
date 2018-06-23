---
title: Language-Element (ASSL) | Microsoft Docs
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
- Language Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- LANGUAGE
helpviewer_keywords:
- Language element
ms.assetid: 4d745d23-6b1f-4a85-97cf-d034cc41356f
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 09a51320df0cf5d4246fbc14307f488c2d754e3c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161222"
---
# <a name="language-element-assl"></a>Language-Element (ASSL)
  Enthält den Sprachenbezeichner des übergeordneten Elements.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Cube> <!-- or Database, Dimension, MiningModel, MiningStructure, Translation -->  
   ...  
   <Language>...</Language>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Integer|  
|Standardwert|InclusionThresholdSetting|  
  
 **Kardinalität**  
  
|Vorgänger oder übergeordnetes Element|Cardinality|  
|------------------------|-----------------|  
|[Übersetzung](../objects/translation-element-assl.md)|1-1: Erforderliches Element, das nur einmal auftritt.|  
|Alle sonstigen|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Cube](../objects/cube-element-assl.md), [Datenbank](../objects/database-element-assl.md), [Dimension](../objects/dimension-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [Übersetzung](../objects/translation-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das `Language`-Element enthält die standardmäßige Sprachen-ID, die vom übergeordneten Element verwendet wird, oder die spezifische Sprachen-ID für ein `Translation`-Element. Die Sprache sollte definiert werden, indem man Gebietsschemabezeichnercodes (LCID) verwendet. Zum Beispiel wird LCID 1033 verwendet, um die englische (U.S.) Sprache anzugeben.  
  
 Die Elemente, die den übergeordneten Elementen des `Language`-Elements im AMO-Objektmodell (Analysis Management Objects) entsprechen, sind <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningStructure> und <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  