---
title: Eigenschaften der Cube-Hierarchie definieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0ace708cc4ee09295380b814bbf21f5a1c350974
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66075706"
---
# <a name="define-cube-hierarchy-properties"></a>Definieren von Cubehierarchieeigenschaften
  Durch Cubehierarchieeigenschaften können Sie eindeutige Einstellungen für benutzerdefinierte Hierarchien in Cubedimensionen angeben, die auf denselben Datenbankdimensionen basieren. In der folgenden Tabelle werden die Eigenschaften einer Cubehierarchie beschrieben.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|`Enabled`|Bestimmt, ob die Hierarchie für die Cubedimension aktiviert ist.|  
|`HierarchyID`|Enthält den eindeutigen Bezeichner (ID) der Hierarchie.|  
|`OptimizedState`|Bestimmt die Optimierungsebene, die auf die Hierarchie angewendet wird. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> `FullyOptimized`: Von der Instanz werden Indizes zum Verbessern der Abfrageleistung für die Hierarchie erstellt. Dies ist der Standardwert.<br /><br /> `NotOptimized`: Durch die Instanz werden keine zusätzlichen Indizes erstellt.|  
|`Visible`|Beschreibt die Sichtbarkeit der Cubehierarchie. Der Standardwert ist `True`.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerhierarchien](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
