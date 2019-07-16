---
title: Member-Objekt (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member
helpviewer_keywords:
- Member object [ADO MD], members
ms.assetid: 3dedf755-0741-4c3f-8b4e-bff8ff8809c8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 44d6b5f06bffb1cea786ba34d3d2aa8a3efb45ee
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67949499"
---
# <a name="member-object-ado-md"></a>Member-Objekt (ADO MD)
Stellt ein Element einer Ebene in einem Cube, die untergeordneten Elemente ein Element einer Ebene oder ein Mitglied einer Position auf einer Achse eines cellSets dar.  
  
## <a name="remarks"></a>Hinweise  
 Die Eigenschaften einer **Member** unterscheiden sich je nach Kontext, in denen es verwendet wird. Ein **Member** von eine [Ebene](../../../ado/reference/ado-md-api/level-object-ado-md.md) in eine [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) verfügt über eine [untergeordnete Elemente](../../../ado/reference/ado-md-api/children-property-ado-md.md) Eigenschaft, die zurückgibt der **Mitglieder** auf der nächstniedrigeren Ebene in der Hierarchie aus der aktuellen **Member**. Für eine **Member** von einer [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md), wird die **untergeordnete Elemente** Sammlung immer leer ist. Darüber hinaus die [Typ](../../../ado/reference/ado-md-api/type-property-ado-md.md) Eigenschaft gilt nur für **Mitglieder** von einer **Ebene**.  
  
 Ein **Member** von **Position** verfügt über zwei Eigenschaften, die hilfreich sind, bei der Anzeige der [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md): [DrilledDown](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md) und [ParentSameAsPrev](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md). Wenn auf diese Eigenschaften zugegriffen werden, wird ein Fehler auftreten. ein **Member** von eine **Ebene**.  
  
 Mit der Auflistungen und Eigenschaften eine **Member** Objekt eine **Ebene**, können Sie Folgendes tun:  
  
-   Identifizieren der **Member** mit der [Namen](../../../ado/reference/ado-md-api/name-property-ado-md.md) und [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) Eigenschaften.  
  
-   Zurückgeben einer Zeichenfolge beim Anzeigen von der **Member** mit der [Beschriftung](../../../ado/reference/ado-md-api/caption-property-ado-md.md) Eigenschaft.  
  
-   Zurückgeben einer sinnvollen Zeichenfolge, die ein Measure oder eine Formel beschreibt **Member** mit der [Beschreibung](../../../ado/reference/ado-md-api/description-property-ado-md.md) Eigenschaft.  
  
-   Bestimmen der Art des der **Member** mit der [Typ](../../../ado/reference/ado-md-api/type-property-ado-md.md) Eigenschaft.  
  
-   Abrufen von Informationen über die **Ebene** von der **Member** mit der [LevelDepth](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md) und [LevelName](../../../ado/reference/ado-md-api/levelname-property-ado-md.md) Eigenschaften.  
  
-   Abrufen verwandte **Mitglieder** in einer [Hierarchie](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md) mit der [übergeordneten](../../../ado/reference/ado-md-api/parent-property-ado-md.md) und [untergeordnete Elemente](../../../ado/reference/ado-md-api/children-property-ado-md.md) Eigenschaften.  
  
-   Anzahl der untergeordneten Elemente ein **Member** mit der [ChildCount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md) Eigenschaft.  
  
-   Verwenden Sie das standard-ADO [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung, um weitere Informationen zum Abrufen der **Ebene** Objekt.  
  
 Für die Auflistungen und Eigenschaften des eine **Member** von eine **Position** entlang einer [Achse](../../../ado/reference/ado-md-api/axis-object-ado-md.md), können Sie Folgendes tun:  
  
-   Identifizieren der **Member** mit der [Namen](../../../ado/reference/ado-md-api/name-property-ado-md.md) und [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) Eigenschaften.  
  
-   Zurückgeben einer Zeichenfolge beim Anzeigen von der **Member** mit der [Beschriftung](../../../ado/reference/ado-md-api/caption-property-ado-md.md) Eigenschaft.  
  
-   Zurückgeben einer sinnvollen Zeichenfolge, die ein Measure oder eine Formel beschreibt **Member** mit der [Beschreibung](../../../ado/reference/ado-md-api/description-property-ado-md.md) Eigenschaft.  
  
-   Abrufen von Informationen über die **Ebene** von der **Member** mit der [LevelDepth](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md) und [LevelName](../../../ado/reference/ado-md-api/levelname-property-ado-md.md) Eigenschaften.  
  
-   Anzahl der untergeordneten Elemente ein **Member** mit der [ChildCount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md) Eigenschaft.  
  
-   Verwenden der [DrilledDown](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md) Eigenschaft, um zu bestimmen, ob mindestens ein untergeordnetes Element vorhanden ist, auf die **Achse** unmittelbar im Anschluss an diese **Member**.  
  
-   Verwenden der [ParentSameAsPrev](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md) Eigenschaft, um zu bestimmen, ob das übergeordnete Element dieses **Member** ist identisch mit das übergeordnete Element des unmittelbar vorangehenden **Member**.  
  
-   Verwenden Sie das standard-ADO [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung, um weitere Informationen zum Abrufen der **Ebene** Objekt.  
  
 Die **Eigenschaften** Auflistung enthält die Eigenschaften vom Anbieter bereitgestellt. Die folgende Tabelle enthält Eigenschaften, die möglicherweise verfügbar sind. Die tatsächliche Eigenschaftenliste kann je nach der Implementierung des Anbieters abweichen. Finden Sie unter der Dokumentation für Ihren Anbieter, um eine vollständige Liste der verfügbaren Eigenschaften.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|CatalogName|Der Name des Katalogs, zu dem dieser Cube gehört.|  
|ChildrenCardinality|Die Anzahl der untergeordneten Elemente des Elements.|  
|CubeName|Der Name des Cubes.|  
|Beschreibung|Eine aussagekräftige Beschreibung des Elements.|  
|DimensionUniqueName|Der eindeutige Name des der [Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md).|  
|HierarchyUniqueName|Der eindeutige Name der Hierarchie.|  
|LevelNumber|Der Abstand zwischen der Ebene und der Stamm der Hierarchie.|  
|LevelUniqueName|Der eindeutige Name der Ebene.|  
|MemberCaption|Eine Bezeichnung oder Beschriftung, die dem Element zugeordnet ist.|  
|MemberGUID|Die GUID des Elements.|  
|MemberName|Der Name des Elements.|  
|MemberOrdinal|Die Ordinalzahl des Elements.|  
|MemberType|Der Typ des Elements.|  
|MemberUniqueName|Der eindeutige Name des Elements.|  
|ParentCount|Die Anzahl der Anzahl von übergeordneten Elementen, die dieses Element verfügt.|  
|ParentLevel|Die Nummer der Ebene des übergeordneten Element.|  
|ParentUniqueName|Der eindeutige Name des übergeordneten Element.|  
|SchemaName|Der Name des Schemas, zu dem dieser Cube gehört.|  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-md-api/member-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Katalog-Beispiel (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Members-Auflistung (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
