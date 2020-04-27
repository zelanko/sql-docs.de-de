---
title: Cubedimensionseigenschaften definieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 9314e749-0918-4862-abaf-a21692188122
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ecf47eff045aa379a8e67332a82b2045a8569a2a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66075688"
---
# <a name="define-cube-dimension-properties"></a>Definieren von Cubedimensionseigenschaften
  Eine Cubedimension ist eine Instanz einer Datenbankdimension in einem Cube. Eine Datenbankdimension kann in mehreren Cubes verwendet werden, und mehrere Cubedimensionen können auf einer einzigen Datenbankdimension basieren. In der folgenden Tabelle werden die Eigenschaften einer Cubedimension beschrieben.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|`AllMemberAggregationUsage`|Steuert, wie Aggregationen vom Aggregationen-Designer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]in entworfen werden. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> **Full:** Jede Aggregation für den Cube muss das Alle-Element enthalten.<br /><br /> **None:** Keine Aggregation für den Cube darf das Alle-Element enthalten. Dies ist der Standardwert.<br /><br /> **Unrestricted:** Keine Einschränkungen für den Aggregations-Designer.<br /><br /> **Default:** Dieselbe Funktion wie Unbeschränkt.|  
|`Description`|Stellt einen aussagekräftigen Namen für die Ebene bereit.|  
|`DimensionID`|Enthält den eindeutigen Bezeichner (ID) für die Datenbankdimension.|  
|`HierarchyUniqueNameStyle`|Bestimmt, wie eindeutige Namen für Hierarchien generiert werden, die in der Cubedimension enthalten sind. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> `IncludeDimensionName`: Der Name der Dimension ist im Namen der Hierarchie enthalten. Dies ist der Standardwert.<br /><br /> `ExcludeDimensionName`: Der Name der Dimension ist nicht im Namen der Hierarchie enthalten.|  
|`ID`|Enthält den eindeutigen Bezeichner für die Cubedimension.|  
|`MemberUniqueNameStyle`|Bestimmt, wie eindeutige Namen für Elemente in Hierarchien generiert werden, die in der Cubedimension enthalten sind. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> `Native`: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] legt die eindeutigen Namen von Elementen automatisch fest. Dies ist der Standardwert.<br /><br /> `NamePath`: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] generiert einen zusammengesetzten Namen, der aus dem Namen den einzelnen Ebenen und der Beschriftung des Elements besteht.|  
|`Name`|Enthält den Anzeigename für die Cubedimension. Der Name einer Cubedimension ist standardmäßig derselbe wie der Name der Datenbankdimension, sofern nicht bereits eine andere Cubedimension mit demselben Namen definiert ist.|  
|`Visible`|Bestimmt, ob die Cubedimension sichtbar ist. Der Standardwert ist `True`.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
