---
title: Definieren von Cubehierarchieeigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3b064db7ff0e496ea7a46085825afc202fced605
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087320"
---
# <a name="define-cube-hierarchy-properties"></a>Definieren von Cubehierarchieeigenschaften
  Durch Cubehierarchieeigenschaften können Sie eindeutige Einstellungen für benutzerdefinierte Hierarchien in Cubedimensionen angeben, die auf denselben Datenbankdimensionen basieren. In der folgenden Tabelle werden die Eigenschaften einer Cubehierarchie beschrieben.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|`Enabled`|Bestimmt, ob die Hierarchie für die Cubedimension aktiviert ist.|  
|`HierarchyID`|Enthält den eindeutigen Bezeichner (ID) der Hierarchie.|  
|`OptimizedState`|Bestimmt die Optimierungsebene, die auf die Hierarchie angewendet wird. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> `FullyOptimized`: Die Instanz werden Indizes zum Verbessern der abfrageleistung für die Hierarchie erstellt. Dies ist der Standardwert.<br /><br /> `NotOptimized`: Die Instanz werden keine zusätzlichen Indizes erstellt werden.|  
|`Visible`|Beschreibt die Sichtbarkeit der Cubehierarchie. Der Standardwert lautet `True`.|  
  
## <a name="see-also"></a>Siehe auch  
 [Benutzerhierarchien](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
