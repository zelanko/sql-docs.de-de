---
title: HoldoutMaxPercent-Element | Microsoft-Dokumentation
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
topic_type:
- apiref
f1_keywords:
- HoldoutMaxPercent
helpviewer_keywords:
- HoldoutMaxPercent element
ms.assetid: e375cc51-5f9d-4252-98a1-326ca0dbbf83
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 53689f28351a4a5505f1c1bc1d4c8a9586074704
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278146"
---
# <a name="holdoutmaxpercent-element"></a>HoldoutMaxPercent-Element
  Gibt den maximalen Prozentsatz von Fällen in der Datenquelle, die für die zurückhaltungspartition verwendet werden, die den Testsatz enthält eine [MiningStructure](../objects/miningstructure-element-assl.md) Element. Die übrigen Fälle werden zum Training verwendet. Ein Wert von 0 gibt an, dass die Anzahl der Fälle, die als Testsatz zurückgehalten werden können, unbegrenzt ist.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutMaxPercent>...</ddl100_100:HoldoutMaxPercent>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Ganzzahl zwischen 0 und 99.|  
|Standardwert|30|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie Werte für beide angeben `HoldoutMaxPercent` und `HoldoutMaxCases`, beschränkt der Algorithmus den Testsatz auf den kleineren der beiden Werte.  
  
 Wenn `HoldoutMaxCases` auf den Standardwert von 0 (null) festgelegt ist und ein Wert wurde nicht festgelegt wurde, für die `HoldoutMaxPercent`, der Algorithmus verwendet den vollständigen Satz von Daten für das Training.  
  
 Die neuen Eigenschaften `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, oder `HoldoutActualSize` stehen nur in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und höhere Versionen. Deshalb müssen Sie diese Eigenschaften wie in der Syntaxbeschreibung gezeigt mit dem neuen Namespace als Präfix versehen, da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] anderenfalls einen Fehler ausgibt.  
  
> [!NOTE]  
>  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] hat nicht die Verwendung von zurückhaltungspartitionen für Miningstrukturen unterstützt. Aus diesem Grund [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Scripting Language (ASSL)-Anweisungen, die einen der zurückhaltungsparameter, enthalten `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, oder `HoldoutActualSize`, kann nicht verwendet werden, [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Wenn Sie einen dieser zurückhaltungsparameter in einer ASSL-Anweisung in verwenden [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen Fehler zurück.  
  
 Das Element, das dem übergeordneten entspricht `HoldoutMaxPercent` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)   
 [HoldoutMaxCases-Element](holdoutmaxcases-element.md)   
 [HoldoutSeed-Element](holdoutseed-element.md)   
 [HoldoutActualSize-Element](holdoutactualsize-element.md)  
  
  
