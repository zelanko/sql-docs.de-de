---
title: HoldoutMaxCases-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
f1_keywords:
- HoldoutMaxCases
helpviewer_keywords:
- HoldoutMaxCases element
ms.assetid: 58d94d10-e11e-4368-b3b8-dff23e1947cd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aaf0629b51abf7e8dc4fe6efa5ac6b18a2f166b8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48136810"
---
# <a name="holdoutmaxcases-element"></a>HoldoutMaxCases-Element
  Gibt die maximale Anzahl von Fällen in der Datenquelle für die zurückhaltungspartition verwendet werden, die den Testsatz enthält eine [MiningStructure](../objects/miningstructure-element-assl.md) Element. Die übrigen Fälle im Datensatz werden zum Training verwendet. Ein Wert von 0 gibt an, dass die Anzahl der Fälle, die als Testsatz zurückgehalten werden können, unbegrenzt ist.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutMaxCases>...</ddl100_100:HoldoutMaxCases>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Ganze Zahl, die größer als 0 ist.|  
|Standardwert|0|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie Werte für beide angeben `HoldoutMaxPercent` und `HoldoutMaxCases`, beschränkt der Algorithmus den Testsatz auf den kleineren der beiden Werte.  
  
 Ist für `HoldoutMaxCases` der Standardwert von 0 festgelegt, und wurde für `HoldoutMaxPercent` kein Wert definiert, verwendet der Algorithmus den gesamten Datensatz für das Training.  
  
 Die neuen Eigenschaften `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, oder `HoldoutActualSize` stehen nur in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und höhere Versionen. Aus diesem Grund müssen Sie diese Eigenschaften mit den neuen Namespace Präfix, wie in der syntaxbeschreibung gezeigt oder [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen Fehler zurück.  
  
> [!NOTE]  
>  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] hat nicht die Verwendung von zurückhaltungspartitionen für Miningstrukturen unterstützt. Aus diesem Grund [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Scripting Language (ASSL)-Anweisungen, die einen der zurückhaltungsparameter, enthalten `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, oder `HoldoutActualSize`, kann nicht verwendet werden, [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Wenn Sie einen dieser zurückhaltungsparameter in einer ASSL-Anweisung in verwenden [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen Fehler zurück.  
  
 Das Element, das dem übergeordneten entspricht `HoldoutMaxCases` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)   
 [HoldoutMaxPercent-Element](holdoutmaxpercent-element.md)   
 [HoldoutSeed-Element](holdoutseed-element.md)   
 [HoldoutActualSize-Element](holdoutactualsize-element.md)  
  
  
