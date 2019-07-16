---
title: Hierarchy-Objekt (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 35e02e4823d0a3abf245e1885b95176d6350d712
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67949695"
---
# <a name="hierarchy-object-ado-md"></a>Hierarchy-Objekt (ADO MD)
Stellt eine Möglichkeit dar, in dem die Mitglieder einer [Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md) aggregiert werden können oder die "wird durchgeführt." Eine Dimension kann entlang einer oder mehreren Hierarchien aggregiert werden.  
  
## <a name="remarks"></a>Hinweise  
 Mit dem Auflistungen und Eigenschaften einer **Hierarchie** -Objekts können Sie folgende Möglichkeiten:  
  
-   Identifizieren der **Hierarchie** mit der [Namen](../../../ado/reference/ado-md-api/name-property-ado-md.md) und [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) Eigenschaften.  
  
-   Zurückgeben einer sinnvollen Zeichenfolge, die beschreibt, die **Hierarchie** mit der [Beschreibung](../../../ado/reference/ado-md-api/description-property-ado-md.md) Eigenschaft.  
  
-   Zurückgeben der [Ebene](../../../ado/reference/ado-md-api/level-object-ado-md.md) Objekte, aus denen die **Hierarchie** mit der [Ebenen](../../../ado/reference/ado-md-api/levels-collection-ado-md.md) Auflistung.  
  
-   Verwenden Sie das standard-ADO [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung, um weitere Informationen zum Abrufen der **Hierarchie** Objekt.  
  
 Die **Eigenschaften** Auflistung enthält die Eigenschaften vom Anbieter bereitgestellt. Die folgende Tabelle enthält Eigenschaften, die möglicherweise verfügbar sind. Die tatsächliche Eigenschaftenliste kann je nach der Implementierung des Anbieters abweichen. Finden Sie unter der Dokumentation für Ihren Anbieter, um eine vollständige Liste der verfügbaren Eigenschaften.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|AllMember|Das Element auf der höchsten Ebene des Rollups in der Hierarchie.|  
|CatalogName|Der Name des Katalogs, zu dem dieser Cube gehört.|  
|CubeName|Der Name des Cubes.|  
|DefaultMember|Der eindeutige Name des Standardelements für diese Hierarchie.|  
|Beschreibung|Eine aussagekräftige Beschreibung der Hierarchie.|  
|DimensionType|Der Typ der Dimension, zu dem diese Hierarchie gehört.|  
|DimensionUniqueName|Der eindeutige Name der Dimension.|  
|HierarchyCaption|Eine Bezeichnung oder Beschriftung, die der Hierarchie zugeordnet ist.|  
|HierarchyCardinality|Die Anzahl der Member in der Hierarchie.|  
|HierarchyGUID|Die GUID der Hierarchie.|  
|HierarchyName|Der Name der Hierarchie.|  
|HierarchyUniqueName|Der eindeutige Name der Hierarchie.|  
|SchemaName|Der Name des Schemas, zu dem dieser Cube gehört.|  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-md-api/hierarchy-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [CubeDef-Beispiel (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Dimension-Objekt (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [Hierarchies-Auflistung (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Levels-Auflistung (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
