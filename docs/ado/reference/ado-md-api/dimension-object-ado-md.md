---
title: Dimensions Objekt (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Dimension
helpviewer_keywords:
- Dimension object [ADO MD]
ms.assetid: 66adbbd2-23a3-4c19-a91b-84c31309aa1b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f7a13ad87d56f5e7855070d8fe577bb408d6ce9e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67938537"
---
# <a name="dimension-object-ado-md"></a>Dimension-Objekt (ADO MD)
Stellt eine der Dimensionen eines mehrdimensionalen Cubes dar, der mindestens eine Hierarchien von Membern enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit den Auflistungen und Eigenschaften eines **Dimensions** Objekts können Sie folgende Aufgaben ausführen:  
  
-   Identifizieren Sie die **Dimension** mit den Eigenschaften " [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) " und " [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) ".  
  
-   Gibt eine sinnvolle Zeichenfolge zurück, die die **Dimension** mit der [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) -Eigenschaft beschreibt.  
  
-   Gibt die [Hierarchie](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md) Objekte zurück, die die **Dimension** mit der [Hierarchien](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md) -Auflistung bilden.  
  
-   Verwenden Sie die standardmäßige ADO [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung, um zusätzliche Informationen über das **Dimensions** Objekt zu erhalten.  
  
 Die **Properties** -Auflistung enthält vom Anbieter bereitgestellte Eigenschaften. In der folgenden Tabelle sind die verfügbaren Eigenschaften aufgeführt. Die tatsächliche Eigenschaften Liste kann je nach Implementierung des Anbieters abweichen. Eine ausführlichere Liste der verfügbaren Eigenschaften finden Sie in der Dokumentation für Ihren Anbieter.  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|CatalogName|Der Name des Katalogs, zu dem dieser Cube gehört.|  
|CubeName|Der Name des Cubes.|  
|DefaultHierarchy|Der eindeutige Name der Standard Hierarchie.|  
|BESCHREIBUNG|Eine aussagekräftige Beschreibung des Cubes.|  
|DimensionCaption|Eine Bezeichnung oder Beschriftung, die der Dimension zugeordnet ist.|  
|DimensionCardinality|Die Anzahl der Elemente in der Dimension.|  
|DimensionGUID|Die GUID der Dimension.|  
|DimensionName|Der Name der Dimension.|  
|Dimensionordinal|Die Ordinalzahl der Dimension in der Gruppe von Dimensionen, die den Cube bilden.|  
|DimensionType|Der Dimensionstyp.|  
|Dimensionuniquename|Der eindeutige Name der Dimension.|  
|SchemaName|Der Name des Schemas, zu dem dieser Cube gehört.|  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-md-api/dimension-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [CubeDef-Beispiel (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [CubeDef-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)   
 [Dimensions Auflistung (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Hierarchien-Auflistung (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
