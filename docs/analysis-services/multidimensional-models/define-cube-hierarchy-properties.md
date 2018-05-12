---
title: Definieren von Cubehierarchieeigenschaften | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 65cd9ae51a89e32c85b46da0c8f14f0c9a593976
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="define-cube-hierarchy-properties"></a>Definieren von Cubehierarchieeigenschaften
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Durch Cubehierarchieeigenschaften können Sie eindeutige Einstellungen für benutzerdefinierte Hierarchien in Cubedimensionen angeben, die auf denselben Datenbankdimensionen basieren. In der folgenden Tabelle werden die Eigenschaften einer Cubehierarchie beschrieben.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|**Aktiviert**|Bestimmt, ob die Hierarchie für die Cubedimension aktiviert ist.|  
|**HierarchyID**|Enthält den eindeutigen Bezeichner (ID) der Hierarchie.|  
|**OptimizedState**|Bestimmt die Optimierungsebene, die auf die Hierarchie angewendet wird. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> **FullyOptimized:**<br />                    Durch die Instanz werden Indizes zum Verbessern der Abfrageleistung für die Hierarchie erstellt. Dies ist der Standardwert.<br /><br /> **NotOptimized:**<br />                    Durch die Instanz werden keine zusätzlichen Indizes erstellt.|  
|**Visible**|Beschreibt die Sichtbarkeit der Cubehierarchie. Der Standardwert lautet **True**.|  
  
## <a name="see-also"></a>Siehe auch  
 [Benutzerhierarchien](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
