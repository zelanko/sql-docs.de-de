---
title: Übersicht über mehrdimensionale Schemas und Daten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- multidimensional schemas and data
ms.assetid: ce37fa06-c581-4d80-9a9b-c3aa66408909
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2e4681bb9e1fd1028ee1ddc2bd7f72efc03fb6c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923188"
---
# <a name="overview-of-multidimensional-schemas-and-data"></a>Übersicht über mehrdimensionale Schemas und Daten
## <a name="understanding-multidimensional-schemas"></a>Grundlegendes zu mehrdimensionalen Schemas  
 Das zentrale Metadatenobjekt in ADO MD ist der *Cube*, der aus einer strukturierten Menge verwandter Dimensionen, Hierarchien, Ebenen und Elemente besteht.  
  
 Eine *Dimension* ist eine unabhängige Kategorie von Daten aus ihrer mehrdimensionalen Datenbank, die von Ihren Geschäfts Entitäten abgeleitet ist. Eine Dimension enthält normalerweise Elemente, die als Abfrage Kriterien für die Measures der Datenbank verwendet werden sollen.  
  
 Eine *Hierarchie* ist ein Pfad zur Aggregation einer Dimension. Eine Dimension kann mehrere Granularitätsebene aufweisen, die über Beziehungen zwischen übergeordneten und untergeordneten Elementen verfügen. Eine Hierarchie definiert, wie diese Ebenen verknüpft sind.  
  
 Eine *Ebene* ist ein Aggregations Schritt in einer Hierarchie. Bei Dimensionen mit mehreren Informationsebenen ist jede Ebene eine Ebene.  
  
 Ein *Member* ist ein Datenelement in einer Dimension. In der Regel erstellen Sie eine Beschriftung oder beschreiben ein Measure der Datenbank mithilfe von Membern.  
  
 Cubes werden in ADO MD durch [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) -Objekte dargestellt. Dimensionen, Hierarchien, Ebenen und [Member](../../../ado/reference/ado-md-api/member-object-ado-md.md)werden auch durch die entsprechenden ADO MD Objekte dargestellt: [Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [Hierarchie](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [Ebene](../../../ado/reference/ado-md-api/level-object-ado-md.md)und Element.  
  
### <a name="dimensions"></a>Dimensionen  
 Die Dimensionen eines Cubes hängen von Ihren Geschäfts Entitäten und Datentypen ab, die in der Datenbank modelliert werden sollen. In der Regel handelt es sich bei jeder Dimension um einen unabhängigen Einstiegspunkt oder Mechanismus zum Auswählen von Daten.  
  
 Ein Cube, der Umsatzdaten enthält, hat beispielsweise die folgenden fünf Dimensionen: SalesPerson, Geography, Time, Products und Measures. Die Measures-Dimension enthält tatsächliche Umsatzdaten Werte, während die anderen Dimensionen Methoden zum Kategorisieren und Gruppieren der Umsatzdaten Werte darstellen.  
  
 Die Geography-Dimension verfügt über die folgenden Member:  
  
```console
{All, North America, Europe, Canada, USA, UK, Germany, Canada-West,  
Canada-East, USA-NW, USA-SW, USA-NE, USA-SE, England, Scotland,   
Wales,Ireland, Germany-North, Germany-South, Ottawa, Toronto,   
Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston,   
Shreveport, Miami, Boston, New York, London, Dover, Glasgow,   
Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin,   
Hamburg, Munich, Stuttgart}  
```  
  
### <a name="hierarchies"></a>Hierarchien  
 Hierarchien definieren die Möglichkeiten, mit denen die Ebenen einer Dimension "hochskalieren" oder gruppiert werden können. Eine Dimension kann über mehr als eine Hierarchie verfügen. In der Geography-Dimension ist eine natürliche Hierarchie vorhanden:  
  
### <a name="levels"></a>Levels  
 In der in der vorherigen Abbildung abgebildeten geography-Beispiel Dimension stellt jedes Feld eine Ebene in der Hierarchie dar.  
  
 Jede Ebene verfügt über eine Reihe von Membern, wie im folgenden dargestellt:  
  
-   die Welt`= {All}`  
  
-   Sub`= {North America, Europe}`  
  
-   Länder`= {Canada, USA, UK, Germany}`  
  
-   An`= {Canada-East, Canada-West, USA-NE, USA-NW, USA-SE, USA-SW, England, Ireland, Scotland, Wales, Germany-North, Germany-South}`  
  
-   Städte`= {Ottawa, Toronto, Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston, Shreveport, Miami, Boston, New York, London, Dover, Glasgow, Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin, Hamburg, Munich, Stuttgart}`  
  
### <a name="members"></a>Members  
 Elemente auf der Blatt Ebene einer Hierarchie haben keine untergeordneten Elemente, und Elemente auf der Stamm Ebene haben kein übergeordnetes Element. Alle anderen Member haben mindestens ein übergeordnetes Element und mindestens ein untergeordnetes Element. Beispielsweise ergibt eine partielle Durchquerung der Hierarchiestruktur in der Geography-Dimension die folgenden Beziehungen zwischen übergeordneten und untergeordneten Elementen:  
  
-   `{All} (parent of) {Europe, North America}`  
  
-   `{North America} (parent of) {Canada, USA}`  
  
-   `{USA} (parent of) {USA-NE, USA-NW, USA-SE, USA-SW}`  
  
-   `{USA-NW} (parent of) {Boise, Seattle}`  
  
 Member können in einer oder mehreren Hierarchien pro Dimension konsolidiert werden. Stellen Sie sich eine Zeitdimension vor, in der es zwei Möglichkeiten gibt, ein Rollup auf die Year-Ebene von der Days-Ebene auszuführen  
  
 Dieses Beispiel veranschaulicht auch ein weiteres Merkmal: einige Member der Wochen-Hierarchie werden in keiner Ebene der Year-Quarter-Hierarchie angezeigt. Daher muss eine Hierarchie nicht alle Elemente einer Dimension enthalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO MD-Objektmodell](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (mehrdimensional) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Programmieren mit ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Verwenden von ADO mit ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [Arbeiten mit mehrdimensionalen Daten](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
