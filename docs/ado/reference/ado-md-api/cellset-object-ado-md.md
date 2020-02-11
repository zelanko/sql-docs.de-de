---
title: CellSet-Objekt (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset
helpviewer_keywords:
- Cellset object [ADO MD]
ms.assetid: 5e2452c0-cac0-49b2-8099-836c35794d50
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9524e9801f284d3dff3125b850cdd1fd32a361a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928648"
---
# <a name="cellset-object-ado-md"></a>Cellset-Objekt (ADO MD)
Stellt die Ergebnisse einer mehrdimensionalen Abfrage dar. Es handelt sich um eine Sammlung von Zellen, die aus Cubes oder anderen Cellsets ausgewählt wurden.  
  
## <a name="remarks"></a>Bemerkungen  
 Daten in einem **Cellset** werden mit direktem, Array ähnlichen Zugriff abgerufen. Sie können einen Drilldown zu einem bestimmten Member durchführen, um Daten zu diesem Element abzurufen. Der folgende Code gibt z. b. die Beschriftung des ersten Elements an der ersten Position auf der ersten Achse eines Cellsets mit dem `cst`Namen zurück:  
  
```  
cst.Axes(0).Positions(0).Members(0).Caption  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Es gibt kein Konzept einer aktiven Zelle in einem CellSet. Stattdessen ruft die [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) -Eigenschaft ein bestimmtes [Cell](../../../ado/reference/ado-md-api/cell-object-ado-md.md) -Objekt aus dem Cellset ab. Die Argumente der **Item** -Eigenschaft bestimmen, welche Zelle abgerufen wird. Sie können den eindeutigen Ordinalwert einer Zelle angeben. Sie können auch Zellen abrufen, indem Sie Ihre Positionsnummern entlang der einzelnen Achsen der Cellsets verwenden. Weitere Informationen zum Abrufen von Zellen finden Sie unter der [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) -Eigenschaft.  
  
 Mit den Auflistungen, Methoden und Eigenschaften eines **Cellset** -Objekts können Sie folgende Aufgaben ausführen:  
  
-   Ordnen Sie eine geöffnete Verbindung einem **Cellset** -Objekt zu, indem Sie die zugehörige [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) -Eigenschaft festlegen.  
  
-   Führen Sie aus, und rufen Sie die Ergebnisse einer mehrdimensionalen Abfrage mit der [Open](../../../ado/reference/ado-md-api/open-method-ado-md.md) -Methode ab.  
  
-   Ruft eine **Zelle** aus dem **Cellset** mit der [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) -Eigenschaft ab.  
  
-   Gibt die [Achsen](../../../ado/reference/ado-md-api/axis-object-ado-md.md) Objekte zurück, die das **Cellset** mit der [Achsen](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) Auflistung definieren.  
  
-   Rufen Sie Informationen zu den Dimensionen ab, die zum Filtern der Daten im **Cellset** mit der [FilterAxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) -Eigenschaft verwendet werden.  
  
-   Gibt die Abfrage zurück, die zum Definieren des **Cellsets** mit der [Source](../../../ado/reference/ado-md-api/source-property-ado-md.md) -Eigenschaft verwendet wird.  
  
-   Gibt den aktuellen Status des **Cellsets** (öffnen, schließen, ausführen oder verbinden) mit der [State](../../../ado/reference/ado-md-api/state-property-ado-md.md) -Eigenschaft zurück.  
  
-   Schließen Sie ein geöffnetes **Cellset** mit der [Close](../../../ado/reference/ado-md-api/close-method-ado-md.md) -Methode.  
  
-   Abrufen von anbieterspezifischen Informationen über das **Cellset** mit der standardmäßigen ADO [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-md-api/cellset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cellset-Beispiel (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Achsen Auflistung (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)   
 [Cell-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Verbindungs Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
