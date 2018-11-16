---
title: Übersicht über multidimensionale Schemas und Daten | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: f06f62768637ebb48ffa6e1cfd2560ff3b53c383
ms.sourcegitcommit: 96b2355d54dfad259826e88bdff91cc9344e16f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51350414"
---
# <a name="overview-of-multidimensional-schemas-and-data"></a>Übersicht über mehrdimensionale Schemas und Daten
## <a name="understanding-multidimensional-schemas"></a>Grundlegendes zu MDX-Schemas  
 Das zentrale Metadatenobjekt in ADO MD ist die *Cube*, die besteht aus einem strukturierten Satz von verwandten Dimensionen, Hierarchien, Ebenen und Elemente.  
  
 Ein *Dimension* ist eine unabhängige Kategorie von Daten aus der mehrdimensionalen Datenbank, die Geschäftsentitäten abgeleitet. Eine Dimension enthält in der Regel die Elemente, die als Kriterien eine Abfrage für die Measures der Datenbank verwendet werden.  
  
 Ein *Hierarchie* entspricht dem Pfad der Aggregation einer Dimension. Eine Dimension möglicherweise mehrere Ebenen der Granularität, die über-/ unterordnungsbeziehung aufweisen. Eine Hierarchie definiert, wie diese Ebenen verknüpft sind.  
  
 Ein *Ebene* ist ein Schritt der Aggregation in einer Hierarchie. Für Dimensionen mit mehreren Ebenen von Informationen ist jede Ebene ein auf.  
  
 Ein *Member* ein Datenelement in einer Dimension ist. In der Regel erstellen eine Beschriftung oder ein Maß für die Datenbank mithilfe von Membern zu beschreiben.  
  
 Cubes werden durch dargestellt [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) Objekte im ADO MD. Dimensionen, Hierarchien, Ebenen und Elemente werden auch durch die entsprechenden ADO MD-Objekte dargestellt: [Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [Hierarchie](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [Ebene](../../../ado/reference/ado-md-api/level-object-ado-md.md), und [ Member](../../../ado/reference/ado-md-api/member-object-ado-md.md).  
  
### <a name="dimensions"></a>Dimensionen  
 Die Dimensionen eines Cubes richten sich nach Ihrer Geschäftseinheiten und die Arten von Daten, die in der Datenbank modelliert werden. In der Regel ist jede Dimension, eine unabhängige Einstiegspunkt oder einen Mechanismus zum Auswählen von Daten.  
  
 Ein Cube mit Umsatzdaten verfügt beispielsweise über die folgenden fünf Dimensionen: Vertriebsmitarbeiter, Geography, Zeit, Produkte und Measures. Die Measures-Dimension enthält Werte des tatsächlichen Umsatzdaten, während die anderen Dimensionen darstellen Möglichkeiten zum Kategorisieren und gruppiert die Werte für die Verkaufsdaten.  
  
 Die Geography-Dimension sind die folgenden Elemente:  
  
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
 Definieren von Hierarchien die Methoden in denen die Ebenen einer Dimension "Rollup" oder gruppiert werden können. Eine Dimension kann mehr als eine Hierarchie aufweisen. Eine natürliche Hierarchie ist in der Geography-Dimension vorhanden:  
  
### <a name="levels"></a>Levels  
 In der Beispiel-Geography-Dimension in der vorherigen Abbildung dargestellte stellt jedes Feld eine Ebene in der Hierarchie dar.  
  
 Jede Ebene weist eine Menge von Elementen, wie folgt aus:  
  
-   die Welt `= {All}`  
  
-   Kontinente `= {North America, Europe}`  
  
-   Länder `= {Canada, USA, UK, Germany}`  
  
-   Regionen `= {Canada-East, Canada-West, USA-NE, USA-NW, USA-SE, USA-SW, England, Ireland, Scotland, Wales, Germany-North, Germany-South}`  
  
-   Städte `= {Ottawa, Toronto, Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston, Shreveport, Miami, Boston, New York, London, Dover, Glasgow, Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin, Hamburg, Munich, Stuttgart}`  
  
### <a name="members"></a>Member  
 Elemente auf der Blattebene einer Hierarchie keine untergeordneten Elemente aufweisen, und Elemente auf der Stammebene kein übergeordnetes Element aufweisen. Alle anderen Elemente verfügen über mindestens ein übergeordnetes Element und mindestens ein untergeordnetes Element. Ein teilweise Durchlauf der Hierarchiestruktur in der Geography-Dimension gibt z. B. die folgenden über-und untergeordneten Beziehungen:  
  
-   `{All} (parent of) {Europe, North America}`  
  
-   `{North America} (parent of) {Canada, USA}`  
  
-   `{USA} (parent of) {USA-NE, USA-NW, USA-SE, USA-SW}`  
  
-   `{USA-NW} (parent of) {Boise, Seattle}`  
  
 Mitglieder können auf eine oder mehrere Hierarchien pro Dimension konsolidiert werden. Erwägen Sie eine Time-Dimension, es zwei Möglichkeiten gibt, die Rollup auf der Year-Ebene auf der Ebene von Tagen:  
  
 Dieses Beispiel verdeutlicht außerdem ein weiteres Merkmal: Einige Elemente der Ebene der Hierarchie Jahr-Woche-Woche werden nicht in einer beliebigen Ebene der Quarter-Year-Hierarchie angezeigt. Daher muss eine Hierarchie nicht eingeschlossen werden alle Elemente einer Dimension.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO MD-Objektmodell](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (mehrdimensional) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Programmieren mit ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Verwenden von ADO mit ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [Arbeiten mit mehrdimensionalen Daten](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
