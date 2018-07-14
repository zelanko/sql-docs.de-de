---
title: AlgorithmParameters-Element (ASSL) | Microsoft-Dokumentation
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
- AlgorithmParameters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AlgorithmParameters
helpviewer_keywords:
- AlgorithmParameters element
ms.assetid: 240cbb60-7fa3-46ef-b5be-cd14c9ec10de
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3ab357b16b8b10b13d3ddb23b2a2bc1e7a32c486
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37330430"
---
# <a name="algorithmparameters-element-assl"></a>AlgorithmParameters-Element (ASSL)
  Enthält die Auflistung der Parameter für den Algorithmus ein, die eine [MiningModel](../objects/miningmodel-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningModel>  
   ...  
   <AlgorithmParameters>  
      <AlgorithmParameter>...</AlgorithmParameter>  
   </AlgorithmParameters>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine (Auflistung)|  
|Standardwert|Keine (Auflistung)|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningModel](../objects/miningmodel-element-assl.md)|  
|Untergeordnete Elemente|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `AlgorithmParameters` Auflistung enthält eine erweiterbare Menge aus Parametern, dargestellt als Name/Wert-Paaren für einen Miningmodellalgorithmus. Die Menge aus anwendbaren Parametern ist algorithmusabhängig. Weitere Informationen zu Algorithmusparametern für einen gegebenen Algorithmus finden Sie in der entsprechenden Dokumentation des Algorithmus.  
  
 Verfügbare Algorithmusparameter, einschließlich Überprüfung und Anzeigeinformationen, können vom DMSCHEMA_MINING_SERVICE_PARAMETERS-Schemarowset abgerufen werden.  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.AlgorithmParameterCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Algorithm-Element &#40;ASSL&#41;](../properties/algorithm-element-assl.md)   
 [DMSCHEMA_MINING_SERVICE_PARAMETERS-Rowset](../../schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)   
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
