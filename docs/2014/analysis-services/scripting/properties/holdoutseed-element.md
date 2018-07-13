---
title: HoldoutSeed-Element | Microsoft-Dokumentation
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
- HoldoutSeed
helpviewer_keywords:
- HoldoutSeed element
ms.assetid: 6b608bb3-c075-4744-9722-f5fb9fa1cc7e
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6b5ba2d0d5d3cb355a4d0d6a372b41207ddce1d6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185227"
---
# <a name="holdoutseed-element"></a>HoldoutSeed-Element
  Gibt den Ausgangswert für eine wiederholbare zurückhaltungspartition an, die den Testsatz enthält eine [MiningStructure](../objects/miningstructure-element-assl.md) Element. Dieser Ausgangswert stellt sicher, dass der Modellinhalt während der Wiederaufbereitung unverändert bleibt. Wenn nicht angegeben oder auf 0 festgelegt, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] erstellt einen Ausgangswert mithilfe eines Hashalgorithmus auf den Namen der Miningstruktur.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutSeed>...</ddl100_100:HoldoutSeed>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Long|  
|Standardwert|0|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie eine Miningstruktur erstmals erstellen, sind ID und Name gleich. Sie können jedoch den Namen der Miningstruktur ändern. Wenn Sie daher die Wiederholbarkeit der Partition sicherstellen möchten, sollten Sie sich nicht auf den Ausgangswert verlassen, der durch den Namen erstellt wird, sondern explizit einen Ausgangswert festlegen.  
  
 Darüber hinaus beim Erstellen Sie eine Kopie einer Miningstruktur mithilfe der `EXPORT` Anweisung [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] behält den Namen für die neue Miningstruktur, jedoch wird automatisch eine neue ID generieren Deshalb können zwei Miningstrukturen vorliegen, die zwar über denselben Namen, jedoch über unterschiedliche IDs verfügen. Alle Miningstrukturen, die denselben Namen haben, verfügen auch über denselben Ausgangswert. Da die Partitionierung der Daten allerdings auch von den Quelldaten abhängt, kann der tatsächliche Inhalt der Partitionen in den einzelnen Strukturen unterschiedlich sein.  
  
 Die neuen Eigenschaften `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, oder `HoldoutActualSize` stehen nur in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und höhere Versionen. Aus diesem Grund müssen Sie diese Eigenschaften mit den neuen Namespace Präfix, wie in der syntaxbeschreibung gezeigt oder [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen Fehler zurück.  
  
 **Beachten Sie** In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] hat nicht die Verwendung von zurückhaltungspartitionen für Miningstrukturen unterstützt. Deshalb können ASSL-Anweisungen ([!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Scripting Language), die die Zurückhaltungsparameter `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` oder `HoldoutActualSize` enthalten, nicht in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] verwendet werden. Wenn Sie einen dieser zurückhaltungsparameter in einer ASSL-Anweisung in verwenden [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen Fehler zurück.  
  
 Das Element, das dem übergeordneten entspricht `HoldoutSeed` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)   
 [HoldoutActualSize-Element](holdoutactualsize-element.md)   
 [HoldoutMaxPercent-Element](holdoutmaxpercent-element.md)   
 [HoldoutMaxCases-Element](holdoutmaxcases-element.md)  
  
  
