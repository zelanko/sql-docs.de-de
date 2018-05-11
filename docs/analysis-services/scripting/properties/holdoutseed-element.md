---
title: HoldoutSeed-Element | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3e9b38b6fbc552ac46453df8d95d8332f44eb422
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="holdoutseed-element"></a>HoldoutSeed-Element
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Gibt den Ausgangswert für eine wiederholbare zurückhaltungspartition an, die den Testsatz enthält eine [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) Element. Dieser Ausgangswert stellt sicher, dass der Modellinhalt während der Wiederaufbereitung unverändert bleibt. Wenn nicht angegeben oder auf 0 festgelegt, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] erstellt einen Ausgangswert mithilfe eines Hashalgorithmus auf den Namen der Miningstruktur.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutSeed>...</ddl100_100:HoldoutSeed>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Long|  
|Standardwert|0|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie eine Miningstruktur erstmals erstellen, sind ID und Name gleich. Sie können jedoch den Namen der Miningstruktur ändern. Wenn Sie daher die Wiederholbarkeit der Partition sicherstellen möchten, sollten Sie sich nicht auf den Ausgangswert verlassen, der durch den Namen erstellt wird, sondern explizit einen Ausgangswert festlegen.  
  
 Darüber, wann erstellen Sie eine Kopie einer Miningstruktur mithilfe der **EXPORTIEREN** -Anweisung [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , behalten den Namen für die neue Miningstruktur jedoch generiert automatisch eine neue ID. Deshalb können zwei Miningstrukturen vorliegen, die zwar über denselben Namen, jedoch über unterschiedliche IDs verfügen. Alle Miningstrukturen, die denselben Namen haben, verfügen auch über denselben Ausgangswert. Da die Partitionierung der Daten allerdings auch von den Quelldaten abhängt, kann der tatsächliche Inhalt der Partitionen in den einzelnen Strukturen unterschiedlich sein.  
  
 Die neuen Eigenschaften **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, oder **HoldoutActualSize** stehen nur in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und höheren Versionen. Aus diesem Grund müssen Sie diese Eigenschaften mit dem neuen Namespace voranstellen, wie in der syntaxbeschreibung gezeigt oder [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen Fehler zurück.  
  
 **Hinweis** In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] hat nicht die Verwendung von zurückhaltungspartitionen für Miningstrukturen unterstützt. Aus diesem Grund [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Scripting Language (ASSL)-Anweisungen, die die zurückhaltungsparameter **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, oder **HoldoutActualSize** kann nicht verwendet werden, [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Wenn Sie einen dieser zurückhaltungsparameter in einer ASSL-Anweisung in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen Fehler zurück.  
  
 Das Element, das das übergeordnete Element des entspricht **HoldoutSeed** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [HoldoutActualSize-Element](../../../analysis-services/scripting/properties/holdoutactualsize-element.md)   
 [HoldoutMaxPercent-Element](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)   
 [HoldoutMaxCases-Element](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md)  
  
  
