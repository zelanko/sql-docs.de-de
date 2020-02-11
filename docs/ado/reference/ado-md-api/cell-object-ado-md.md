---
title: Cell-Objekt (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell
helpviewer_keywords:
- Cell object [ADO MD]
ms.assetid: dcc2f044-b785-4a29-9bc5-b673f66eedf9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bbf97a4095f2295b8851f87ba20ab083938e70ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67947747"
---
# <a name="cell-object-ado-md"></a>Cell-Objekt (ADO MD)
Stellt die Daten an der Schnittmenge von Achsen Koordinaten dar, die in einem CellSet enthalten sind.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein **Cell** -Objekt wird von der [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) -Eigenschaft eines [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) -Objekts zurückgegeben.  
  
 Mit den Auflistungen und Eigenschaften eines **Cell** -Objekts können Sie folgende Aufgaben ausführen:  
  
-   Gibt die Daten in der **Zelle** mit der [value](../../../ado/reference/ado-md-api/value-property-ado-md.md) -Eigenschaft zurück.  
  
-   Gibt die Zeichenfolge zurück, die die formatierte Anzeige der **value** -Eigenschaft mit der [FormattedValue](../../../ado/reference/ado-md-api/formattedvalue-property-ado-md.md) -Eigenschaft darstellt.  
  
-   Gibt den Ordinalwert der **Zelle** innerhalb des **Cellsets** mit der [Ordnungszahl](../../../ado/reference/ado-md-api/ordinal-property-ado-md-cell.md) -Eigenschaft zurück.  
  
-   Bestimmen Sie die Position der **Zelle** innerhalb der [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) mit der [Positions](../../../ado/reference/ado-md-api/positions-collection-ado-md.md) Auflistung.  
  
-   Rufen Sie weitere Informationen zur **Zelle** mit der standardmäßigen ADO [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Sammlung ab.  
  
 Die **Properties** -Auflistung enthält vom Anbieter bereitgestellte Eigenschaften. In der folgenden Tabelle sind die verfügbaren Eigenschaften aufgeführt. Die tatsächliche Eigenschaften Liste kann je nach Implementierung des Anbieters abweichen. Eine ausführlichere Liste der verfügbaren Eigenschaften finden Sie in der Dokumentation für Ihren Anbieter.  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|BackColor|Hintergrundfarbe, die beim Anzeigen der Zelle verwendet wird.|  
|FontFlags|Bitmaske, die die Auswirkungen auf die Schriftart detailliert erläutert.|  
|FontName|Schriftart, die zum Anzeigen des Zellwerts verwendet wird.|  
|FontSize|Der Schrift Grad, der zum Anzeigen des Zellwerts verwendet wird.|  
|ForeColor|Vordergrundfarbe, die beim Anzeigen der Zelle verwendet wird.|  
|FormatString|Der Wert in einer formatierten Zeichenfolge.|  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-md-api/cell-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Achsen Beispiel (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [CellSet-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Positions Auflistung (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
