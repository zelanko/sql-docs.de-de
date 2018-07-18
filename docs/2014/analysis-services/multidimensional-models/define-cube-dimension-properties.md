---
title: Definieren von Cubedimensionseigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 9314e749-0918-4862-abaf-a21692188122
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4bda79152cc17ef8f9e94afde2f8166ecd73ba4b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157061"
---
# <a name="define-cube-dimension-properties"></a>Definieren von Cubedimensionseigenschaften
  Eine Cubedimension ist eine Instanz einer Datenbankdimension in einem Cube. Eine Datenbankdimension kann in mehreren Cubes verwendet werden, und mehrere Cubedimensionen können auf einer einzigen Datenbankdimension basieren. In der folgenden Tabelle werden die Eigenschaften einer Cubedimension beschrieben.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|`AllMemberAggregationUsage`|Steuert, wie Aggregationen vom Aggregations-Designer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]entworfen werden. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> **Full:** Jede Aggregation für den Cube muss das Alle-Element enthalten.<br /><br /> **None:** Keine Aggregation für den Cube darf das Alle-Element enthalten. Dies ist der Standardwert.<br /><br /> **Unrestricted:** Keine Einschränkungen für den Aggregations-Designer.<br /><br /> **Default:** Dieselbe Funktion wie Unbeschränkt.|  
|`Description`|Stellt einen aussagekräftigen Namen für die Ebene bereit.|  
|`DimensionID`|Enthält den eindeutigen Bezeichner (ID) für die Datenbankdimension.|  
|`HierarchyUniqueNameStyle`|Bestimmt, wie eindeutige Namen für Hierarchien generiert werden, die in der Cubedimension enthalten sind. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> `IncludeDimensionName`: Der Name der Dimension wird als Teil des Namens der Hierarchie enthalten. Dies ist der Standardwert.<br /><br /> `ExcludeDimensionName`: Der Name der Dimension ist nicht als Teil des Namens der Hierarchie enthalten.|  
|`ID`|Enthält den eindeutigen Bezeichner für die Cubedimension.|  
|`MemberUniqueNameStyle`|Bestimmt, wie eindeutige Namen für Elemente in Hierarchien generiert werden, die in der Cubedimension enthalten sind. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> `Native`: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bestimmt automatisch die eindeutigen Namen von Elementen. Dies ist der Standardwert.<br /><br /> `NamePath`: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] generiert einen zusammengesetzten Namen, die aus den Namen der einzelnen Ebenen und die Beschriftung des Elements besteht.|  
|`Name`|Enthält den Anzeigename für die Cubedimension. Der Name einer Cubedimension ist standardmäßig derselbe wie der Name der Datenbankdimension, sofern nicht bereits eine andere Cubedimension mit demselben Namen definiert ist.|  
|`Visible`|Bestimmt, ob die Cubedimension sichtbar ist. Der Standardwert lautet `True`.|  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
