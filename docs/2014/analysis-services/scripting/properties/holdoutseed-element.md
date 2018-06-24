---
title: HoldoutSeed-Element | Microsoft Docs
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4b17c334a2effbecb24fc3aca41293567f3225ae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046274"
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
  
 Darüber, wann erstellen Sie eine Kopie einer Miningstruktur mithilfe der `EXPORT` -Anweisung [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , behalten den Namen für die neue Miningstruktur jedoch generiert automatisch eine neue ID. Deshalb können zwei Miningstrukturen vorliegen, die zwar über denselben Namen, jedoch über unterschiedliche IDs verfügen. Alle Miningstrukturen, die denselben Namen haben, verfügen auch über denselben Ausgangswert. Da die Partitionierung der Daten allerdings auch von den Quelldaten abhängt, kann der tatsächliche Inhalt der Partitionen in den einzelnen Strukturen unterschiedlich sein.  
  
 Die neuen Eigenschaften `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, oder `HoldoutActualSize` stehen nur in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und höheren Versionen. Aus diesem Grund müssen Sie diese Eigenschaften mit dem neuen Namespace voranstellen, wie in der syntaxbeschreibung gezeigt oder [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen Fehler zurück.  
  
 **Hinweis** In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] hat nicht die Verwendung von zurückhaltungspartitionen für Miningstrukturen unterstützt. Deshalb können ASSL-Anweisungen ([!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Scripting Language), die die Zurückhaltungsparameter `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` oder `HoldoutActualSize` enthalten, nicht in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] verwendet werden. Wenn Sie einen dieser zurückhaltungsparameter in einer ASSL-Anweisung in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen Fehler zurück.  
  
 Das Element, das das übergeordnete Element des entspricht `HoldoutSeed` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)   
 [HoldoutActualSize-Element](holdoutactualsize-element.md)   
 [HoldoutMaxPercent-Element](holdoutmaxpercent-element.md)   
 [HoldoutMaxCases-Element](holdoutmaxcases-element.md)  
  
  