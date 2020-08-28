---
description: Hierarchy-Objekt (ADO MD)
title: Hierarchy-Objekt (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Hierarchy
helpviewer_keywords:
- Hierarchy object [ADO MD]
ms.assetid: 034af340-ac79-494e-ba5e-2b57da1cb9de
author: rothja
ms.author: jroth
ms.openlocfilehash: 60d779ec3ed3393417725c9f574a798e5efc0efd
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986651"
---
# <a name="hierarchy-object-ado-md"></a>Hierarchy-Objekt (ADO MD)
Stellt eine Methode dar, mit der die [Elemente einer Dimension](./dimension-object-ado-md.md) aggregiert oder "ein Rollup ausgeführt werden können". Eine Dimension kann entlang einer oder mehrerer Hierarchien aggregiert werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit den Auflistungen und Eigenschaften eines **Hierarchy** -Objekts können Sie folgende Aufgaben ausführen:  
  
-   Identifizieren Sie die **Hierarchie** mit den Eigenschaften " [Name](./name-property-ado-md.md) " und " [UniqueName](./uniquename-property-ado-md.md) ".  
  
-   Gibt eine sinnvolle Zeichenfolge zurück, die die **Hierarchie** mit der [Description](./description-property-ado-md.md) -Eigenschaft beschreibt.  
  
-   Gibt die [Level](./level-object-ado-md.md) -Objekte zurück, die die **Hierarchie** mit der [Ebenen](./levels-collection-ado-md.md) -Auflistung bilden.  
  
-   Verwenden Sie die standardmäßige ADO [Properties](../ado-api/properties-collection-ado.md) -Auflistung, um zusätzliche Informationen zum **Hierarchy** -Objekt zu erhalten.  
  
 Die **Properties** -Auflistung enthält vom Anbieter bereitgestellte Eigenschaften. In der folgenden Tabelle sind die verfügbaren Eigenschaften aufgeführt. Die tatsächliche Eigenschaften Liste kann je nach Implementierung des Anbieters abweichen. Eine ausführlichere Liste der verfügbaren Eigenschaften finden Sie in der Dokumentation für Ihren Anbieter.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|AllMember|Der Member auf der höchsten Rollup-Ebene in der Hierarchie.|  
|CatalogName|Der Name des Katalogs, zu dem dieser Cube gehört.|  
|CubeName|Der Name des Cubes.|  
|DefaultMember|Der eindeutige Name des Standard Members für diese Hierarchie.|  
|Beschreibung|Eine aussagekräftige Beschreibung der Hierarchie.|  
|DimensionType|Der Typ der Dimension, zu der diese Hierarchie gehört.|  
|Dimensionuniquename|Der eindeutige Name der Dimension.|  
|Hierarchycaption|Eine Bezeichnung oder Beschriftung, die der Hierarchie zugeordnet ist.|  
|Hierarchycardinality|Die Anzahl der Member in der Hierarchie.|  
|Hierarchyguid|Die GUID der Hierarchie.|  
|HierarchyName|Der Name der Hierarchie.|  
|Hierarchyuniquename|Der eindeutige Name der Hierarchie.|  
|SchemaName|Der Name des Schemas, zu dem dieser Cube gehört.|  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](./hierarchy-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [CubeDef-Beispiel (VBScript)](./cubedef-example-vbscript.md)   
 [Dimensions Objekt (ADO MD)](./dimension-object-ado-md.md)   
 [Hierarchien-Auflistung (ADO MD)](./hierarchies-collection-ado-md.md)   
 [Levels-Auflistung (ADO MD)](./levels-collection-ado-md.md)   
 [Properties-Collection (ADO)](../ado-api/properties-collection-ado.md)