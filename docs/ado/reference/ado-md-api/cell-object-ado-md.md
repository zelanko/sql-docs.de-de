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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67947747"
---
# <a name="cell-object-ado-md"></a>Cell-Objekt (ADO MD)
Stellt die Daten am Schnittpunkt der Achsenkoordinaten enthalten, die in einem Cellset dar.  
  
## <a name="remarks"></a>Hinweise  
 Ein **Zelle** -Objekt zurück, die [Element](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) Eigenschaft eine [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) Objekt.  
  
 Mit dem Auflistungen und Eigenschaften einer **Zelle** -Objekts können Sie folgende Möglichkeiten:  
  
-   Zurückgeben von Daten in die **Zelle** mit der [Wert](../../../ado/reference/ado-md-api/value-property-ado-md.md) Eigenschaft.  
  
-   Zurückgeben der Zeichenfolge, die die formatierte Anzeige der die **Wert** Eigenschaft mit dem [FormattedValue](../../../ado/reference/ado-md-api/formattedvalue-property-ado-md.md) Eigenschaft.  
  
-   Zurückgeben den Ordinalwert des der **Zelle** innerhalb der **Cellset** mit der [Ordinal](../../../ado/reference/ado-md-api/ordinal-property-ado-md-cell.md) Eigenschaft.  
  
-   Bestimmen die Position der der **Zelle** innerhalb der [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) mit der [Positionen](../../../ado/reference/ado-md-api/positions-collection-ado-md.md) Auflistung.  
  
-   Weitere Informationen zum Abrufen der **Zelle** mit dem standard-ADO [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung.  
  
 Die **Eigenschaften** Auflistung enthält die Eigenschaften vom Anbieter bereitgestellt. Die folgende Tabelle enthält Eigenschaften, die möglicherweise verfügbar sind. Die tatsächliche Eigenschaftenliste kann je nach der Implementierung des Anbieters abweichen. Finden Sie unter der Dokumentation für Ihren Anbieter, um eine vollständige Liste der verfügbaren Eigenschaften.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|Hintergrundfarbe|Hintergrundfarbe die Zelle angezeigt.|  
|FontFlags|Bitmaske, die mit Details zu Auswirkungen auf die Schriftart.|  
|FontName|Der Wert der Zelle anzuzeigenden verwendete Schriftart.|  
|FontSize|Der Schriftgrad ist der Wert der Zelle angezeigt.|  
|ForeColor|Beim Anzeigen der Zelle verwendete Vordergrundfarbe.|  
|FormatString|Der Wert in eine formatierte Zeichenfolge.|  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-md-api/cell-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Achse-Beispiel (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Cellset-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Positionen-Auflistung (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
