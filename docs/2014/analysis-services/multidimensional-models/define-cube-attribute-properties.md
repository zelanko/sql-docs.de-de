---
title: Definieren von Cubeattributeigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], defining
ms.assetid: 579ca818-f33d-4060-906d-c8bfee93bf99
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2e84c49055a1fdb5b11487ab17af19762f86686c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62726414"
---
# <a name="define-cube-attribute-properties"></a>Definieren von Cubeattributeigenschaften
  Durch Cubeattributeigenschaften können Sie eindeutige Einstellungen für Dimensionsattribute in Cubedimensionen angeben, die auf derselben Datenbankdimension basieren. In der folgenden Tabelle werden die Eigenschaften eines Cubeattributs beschrieben.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|`AggregationUsage`|Gibt an, wie der Aggregationsentwurfs-Assistent Aggregationen für das Attribut entwirft. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> `Default`: Standard. Der Aggregationsentwurfs-Assistent wendet eine Standardregel basierend auf dem Typ des Attributs an (Vollständig für Schlüssel, Uneingeschränkt für andere Attribute).<br /><br /> `None`: Keine Aggregation für den Cube darf dieses Attribut enthalten.<br /><br /> `Unrestricted`: Keine Einschränkungen sind für den Aggregationsentwurfs-Assistenten.<br /><br /> `Full`: Jede Aggregation für den Cube muss dieses Attribut enthalten.|  
|`AttributeHierarchyEnabled`|Identifiziert, ob die Attributhierarchie für diese Cubedimension aktiviert ist. Hierdurch ist es möglich, Attributhierarchien für bestimmte Cubes oder Dimensionsrollen zu deaktivieren. Diese Einstellung hat keine Wirkung, wenn die zugrunde liegende Attributhierarchie deaktiviert ist. Der Standardwert ist `True`.|  
|`OptimizedState`|Zeigt an, ob die Attributhierarchie für diese Cubedimension optimiert ist. Hierdurch ist es möglich, Attributhierarchien für bestimmte Cubes oder Dimensionsrollen zu optimieren. Diese Einstellung hat keine Wirkung, wenn die zugrunde liegende Attributhierarchie nicht optimiert ist. Diese Eigenschaft kann die folgenden Werte annehmen:<br /><br /> `FullyOptimized`: Standard. Durch die Instanz werden Indizes zum Verbessern der Abfrageleistung für die Hierarchie erstellt. Dies ist der Standardwert.<br /><br /> `NotOptimized`: Durch die Instanz werden keine zusätzlichen Indizes erstellt.|  
|`AttributeHierarchyVisible`|Zeigt an, ob die Attributhierarchie für diese Cubedimension sichtbar ist. Hierdurch ist es möglich, dass Attributhierarchien für bestimmte Cubes oder Dimensionsrollen sichtbar gemacht werden. Diese Einstellung hat keine Wirkung, wenn die zugrunde liegende Attributhierarchie nicht sichtbar ist. Der Standardwert ist `True`.|  
|`AttributeID`|Enthält den eindeutigen Bezeichner (ID) des Attributs.|  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren von Cubedimensionseigenschaften](define-cube-dimension-properties.md)   
 [Definieren von Cubehierarchieeigenschaften](define-cube-hierarchy-properties.md)  
  
  
