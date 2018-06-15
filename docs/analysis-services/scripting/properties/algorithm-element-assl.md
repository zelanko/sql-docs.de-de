---
title: Algorithm-Element (ASSL) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d60c8416ef530014ee996f57b321f46ffbb2e436
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34035651"
---
# <a name="algorithm-element-assl"></a>Algorithm-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert den von einem [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) -Element verwendeten Algorithmus.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningModel>  
      ...  
   <Algorithm>...</Algorithm>  
      ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert, der die **Algorithmus** Element ist eine Zeichenfolge, die der Algorithmus identifiziert. Die Zeichenfolge kann z. B. *Microsoft_Naive_Bayes*, *Microsoft_Decision_Trees*, oder *Microsoft_Clustering.* Die Zeichenfolge identifiziert Algorithmen, die vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] und benutzerdefinierte Algorithmen, die vom Benutzer bereitgestellt werden. Verfügbare Werte für die **Algorithmus** Element abgerufen werden kann, aus der Spalte SERVICE_NAME des der [DMSCHEMA_MINING_SERVICES](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md) -Schemarowsets.  
  
 Das Element, das das übergeordnete Element des entspricht **Algorithmus** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningModel>. Ein eng verwandtes Element im AMO-Objektmodell ist <xref:Microsoft.AnalysisServices.MiningModelAlgorithms>.  
  
## <a name="see-also"></a>Siehe auch  
 [AlgorithmParameter-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)   
 [AlgorithmParameters-Element & #40; ASSL & #41;](../../../analysis-services/scripting/collections/algorithmparameters-element-assl.md)   
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
