---
title: Algorithm-Element (ASSL) | Microsoft-Dokumentation
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
- Algorithm Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Algorithm
helpviewer_keywords:
- Algorithm element
ms.assetid: 188bf7ce-c5c9-406a-af75-5a026c92a569
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 38ca7406538a81768e8cab8d0c24142c8105c963
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218490"
---
# <a name="algorithm-element-assl"></a>Algorithm-Element (ASSL)
  Definiert den Algorithmus ein, die eine [MiningModel](../objects/miningmodel-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningModel>  
      ...  
   <Algorithm>...</Algorithm>  
      ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningModel](../objects/miningmodel-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert des `Algorithm`-Elements ist eine Zeichenfolge, die den Algorithmus identifiziert. Beispielsweise ist die Zeichenfolge möglicherweise *Microsoft_Naive_Bayes*, *Microsoft_Decision_Trees*, oder *Microsoft_Clustering.* Die Zeichenfolge identifiziert Algorithmen, die vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] und benutzerdefinierte Algorithmen, die vom Benutzer bereitgestellt werden. Verfügbare Werte für die `Algorithm` Element abgerufen werden kann, aus der Spalte SERVICE_NAME des der [DMSCHEMA_MINING_SERVICES](../../schema-rowsets/data-mining/dmschema-mining-services-rowset.md) -Schemarowsets.  
  
 Das Element, das dem übergeordneten entspricht `Algorithm` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningModel>. Ein eng verwandtes Element im AMO-Objektmodell ist <xref:Microsoft.AnalysisServices.MiningModelAlgorithms>.  
  
## <a name="see-also"></a>Siehe auch  
 [AlgorithmParameter-Element &#40;ASSL&#41;](../objects/algorithmparameter-element-assl.md)   
 [AlgorithmParameters-Element &#40;ASSL&#41;](../collections/algorithmparameters-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
