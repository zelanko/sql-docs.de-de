---
title: Definieren von Cubeattributeigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], defining
ms.assetid: 579ca818-f33d-4060-906d-c8bfee93bf99
author: minewiskan
ms.author: owend
ms.openlocfilehash: c02d57e8d24e625dc0613f25d97765c9ae018803
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547042"
---
# <a name="define-cube-attribute-properties"></a>Definieren von Cubeattributeigenschaften
  Durch Cubeattributeigenschaften können Sie eindeutige Einstellungen für Dimensionsattribute in Cubedimensionen angeben, die auf derselben Datenbankdimension basieren. In der folgenden Tabelle werden die Eigenschaften eines Cubeattributs beschrieben.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|`AggregationUsage`|Gibt an, wie der Aggregationsentwurfs-Assistent Aggregationen für das Attribut entwirft. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> `Default`: Standard. Der Aggregationsentwurfs-Assistent wendet eine Standardregel basierend auf dem Typ des Attributs an (Vollständig für Schlüssel, Uneingeschränkt für andere Attribute).<br /><br /> `None`: Keine Aggregation für den Cube darf dieses Attribut enthalten.<br /><br /> `Unrestricted`: Für den Aggregations Entwurfs-Assistenten gelten keine Einschränkungen.<br /><br /> `Full`: Jede Aggregation für den Cube muss dieses Attribut enthalten.|  
|`AttributeHierarchyEnabled`|Identifiziert, ob die Attributhierarchie für diese Cubedimension aktiviert ist. Hierdurch ist es möglich, Attributhierarchien für bestimmte Cubes oder Dimensionsrollen zu deaktivieren. Diese Einstellung hat keine Wirkung, wenn die zugrunde liegende Attributhierarchie deaktiviert ist. Der Standardwert ist `True`.|  
|`OptimizedState`|Zeigt an, ob die Attributhierarchie für diese Cubedimension optimiert ist. Hierdurch ist es möglich, Attributhierarchien für bestimmte Cubes oder Dimensionsrollen zu optimieren. Diese Einstellung hat keine Wirkung, wenn die zugrunde liegende Attributhierarchie nicht optimiert ist. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> `FullyOptimized`: Standard. Durch die Instanz werden Indizes zum Verbessern der Abfrageleistung für die Hierarchie erstellt. Dies ist der Standardwert.<br /><br /> `NotOptimized`: Durch die Instanz werden keine zusätzlichen Indizes erstellt.|  
|`AttributeHierarchyVisible`|Zeigt an, ob die Attributhierarchie für diese Cubedimension sichtbar ist. Hierdurch ist es möglich, dass Attributhierarchien für bestimmte Cubes oder Dimensionsrollen sichtbar gemacht werden. Diese Einstellung hat keine Wirkung, wenn die zugrunde liegende Attributhierarchie nicht sichtbar ist. Der Standardwert ist `True`.|  
|`AttributeID`|Enthält den eindeutigen Bezeichner (ID) des Attributs.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cube-Dimensions Eigenschaften definieren](define-cube-dimension-properties.md)   
 [Definieren von Cubehierarchieeigenschaften](define-cube-hierarchy-properties.md)  
  
  
