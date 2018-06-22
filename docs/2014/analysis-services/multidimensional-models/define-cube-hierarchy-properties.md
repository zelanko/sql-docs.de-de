---
title: Definieren von Cubehierarchieeigenschaften | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 199e00331e26cea5c84242582f9c6382215ad411
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047298"
---
# <a name="define-cube-hierarchy-properties"></a>Definieren von Cubehierarchieeigenschaften
  Durch Cubehierarchieeigenschaften können Sie eindeutige Einstellungen für benutzerdefinierte Hierarchien in Cubedimensionen angeben, die auf denselben Datenbankdimensionen basieren. In der folgenden Tabelle werden die Eigenschaften einer Cubehierarchie beschrieben.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|`Enabled`|Bestimmt, ob die Hierarchie für die Cubedimension aktiviert ist.|  
|`HierarchyID`|Enthält den eindeutigen Bezeichner (ID) der Hierarchie.|  
|`OptimizedState`|Bestimmt die Optimierungsebene, die auf die Hierarchie angewendet wird. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> `FullyOptimized`: Der Instanz werden Indizes zum Verbessern der Leistung von Abfragen für die Hierarchie erstellt. Dies ist der Standardwert.<br /><br /> `NotOptimized`: Der Instanz werden keine zusätzlichen Indizes erstellt.|  
|`Visible`|Beschreibt die Sichtbarkeit der Cubehierarchie. Der Standardwert lautet `True`.|  
  
## <a name="see-also"></a>Siehe auch  
 [Benutzerhierarchien](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  