---
title: AlgorithmParameter-Element (ASSL) | Microsoft Docs
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
- AlgorithmParameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AlgorithmParameter
helpviewer_keywords:
- AlgorithmParameter element
ms.assetid: 73211495-065c-43c6-a486-be6044617263
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 70e9e3619eb5f96ff2e64c87855b2bd33063aaf0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060599"
---
# <a name="algorithmparameter-element-assl"></a>AlgorithmParameter-Element (ASSL)
  Definiert einen Parameter für den Algorithmus, der verwendet wird, indem Sie eine [MiningModel](miningmodel-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AlgorithmParameters>  
   <AlgorithmParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </AlgorithmParameter>  
</AlgorithmParameters>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[AlgorithmParameters](../collections/algorithmparameters-element-assl.md)|  
|Untergeordnete Elemente|[Name](../properties/name-element-assl.md), [Value](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 `AlgorithmParameter` ist ein Parameter für einen Miningmodellalgorithmus. `AlgorithmParameter` stellt diesen Parameter als Name/Wert-Paar dar. Die Menge an anwendbaren Parametern, die `AlgorithmParameter` darstellen kann, ist algorithmusabhängig. Weitere Informationen zu Algorithmusparametern für einen gegebenen Algorithmus finden Sie in der entsprechenden Dokumentation des Algorithmus.  
  
 Verfügbare Algorithmusparameter, einschließlich Überprüfung und Anzeigeinformationen, können abgerufen werden, aus der [DMSCHEMA_MINING_SERVICE_PARAMETERS](../../schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md) -Schemarowsets.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.AlgorithmParameter>.  
  
## <a name="see-also"></a>Siehe auch  
 [MiningModel-Element &#40;ASSL&#41;](miningmodel-element-assl.md)   
 [Algorithm-Element &#40;ASSL&#41;](../properties/algorithm-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  