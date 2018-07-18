---
title: HoldoutMaxCases-Element | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f66fca3656bfe0e0e778bf24e500f03c8f2816ba
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34033931"
---
# <a name="holdoutmaxcases-element"></a>HoldoutMaxCases-Element
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Gibt die maximale Anzahl von Fällen an, in der Datenquelle für die zurückhaltungspartition verwendet werden, die den Testsatz enthält eine [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) Element. Die übrigen Fälle im Datensatz werden zum Training verwendet. Ein Wert von 0 gibt an, dass die Anzahl der Fälle, die als Testsatz zurückgehalten werden können, unbegrenzt ist.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutMaxCases>...</ddl100_100:HoldoutMaxCases>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Ganze Zahl, die größer als 0 ist.|  
|Standardwert|0|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie sowohl für **HoldoutMaxPercent** als auch für **HoldoutMaxCases**Werte angeben, beschränkt der Algorithmus den Testsatz auf den kleineren der beiden Werte.  
  
 Ist für **HoldoutMaxCases** der Standardwert von 0 festgelegt, und wurde für **HoldoutMaxPercent**kein Wert definiert, verwendet der Algorithmus den gesamten Datensatz für das Training.  
  
 Die neuen Eigenschaften **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, oder **HoldoutActualSize** stehen nur in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und höheren Versionen. Aus diesem Grund müssen Sie diese Eigenschaften mit dem neuen Namespace voranstellen, wie in der syntaxbeschreibung gezeigt oder [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen Fehler zurück.  
  
> [!NOTE]  
>  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] hat nicht die Verwendung von zurückhaltungspartitionen für Miningstrukturen unterstützt. Aus diesem Grund [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Scripting Language (ASSL)-Anweisungen, die einen der zurückhaltungsparameter enthalten **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, oder **HoldoutActualSize**, kann nicht verwendet werden, [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Wenn Sie einen dieser zurückhaltungsparameter in einer ASSL-Anweisung in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen Fehler zurück.  
  
 Das Element, das das übergeordnete Element des entspricht **HoldoutMaxCases** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [HoldoutMaxPercent-Element](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)   
 [HoldoutSeed-Element](../../../analysis-services/scripting/properties/holdoutseed-element.md)   
 [HoldoutActualSize-Element](../../../analysis-services/scripting/properties/holdoutactualsize-element.md)  
  
  
