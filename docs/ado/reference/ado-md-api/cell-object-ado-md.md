---
description: Cell-Objekt (ADO MD)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 28058d792b0525aafe8850158a71afcc4423b38f
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88778329"
---
# <a name="cell-object-ado-md"></a>Cell-Objekt (ADO MD)
Stellt die Daten an der Schnittmenge von Achsen Koordinaten dar, die in einem CellSet enthalten sind.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein **Cell** -Objekt wird von der [Item](./item-property-ado-md-cellset.md) -Eigenschaft eines [Cellset](./cellset-object-ado-md.md) -Objekts zurückgegeben.  
  
 Mit den Auflistungen und Eigenschaften eines **Cell** -Objekts können Sie folgende Aufgaben ausführen:  
  
-   Gibt die Daten in der **Zelle** mit der [value](./value-property-ado-md.md) -Eigenschaft zurück.  
  
-   Gibt die Zeichenfolge zurück, die die formatierte Anzeige der **value** -Eigenschaft mit der [FormattedValue](./formattedvalue-property-ado-md.md) -Eigenschaft darstellt.  
  
-   Gibt den Ordinalwert der **Zelle** innerhalb des **Cellsets** mit der [Ordnungszahl](./ordinal-property-ado-md-cell.md) -Eigenschaft zurück.  
  
-   Bestimmen Sie die Position der **Zelle** innerhalb der [CubeDef](./cubedef-object-ado-md.md) mit der [Positions](./positions-collection-ado-md.md) Auflistung.  
  
-   Rufen Sie weitere Informationen zur **Zelle** mit der standardmäßigen ADO [Properties](../ado-api/properties-collection-ado.md) -Sammlung ab.  
  
 Die **Properties** -Auflistung enthält vom Anbieter bereitgestellte Eigenschaften. In der folgenden Tabelle sind die verfügbaren Eigenschaften aufgeführt. Die tatsächliche Eigenschaften Liste kann je nach Implementierung des Anbieters abweichen. Eine ausführlichere Liste der verfügbaren Eigenschaften finden Sie in der Dokumentation für Ihren Anbieter.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|BackColor|Hintergrundfarbe, die beim Anzeigen der Zelle verwendet wird.|  
|FontFlags|Bitmaske, die die Auswirkungen auf die Schriftart detailliert erläutert.|  
|FontName|Schriftart, die zum Anzeigen des Zellwerts verwendet wird.|  
|FontSize|Der Schrift Grad, der zum Anzeigen des Zellwerts verwendet wird.|  
|ForeColor|Vordergrundfarbe, die beim Anzeigen der Zelle verwendet wird.|  
|FormatString|Der Wert in einer formatierten Zeichenfolge.|  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](./cell-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Achsen Beispiel (VBScript)](./axis-example-vbscript.md)   
 [CellSet-Objekt (ADO MD)](./cellset-object-ado-md.md)   
 [Positions Auflistung (ADO MD)](./positions-collection-ado-md.md)   
 [Properties-Collection (ADO)](../ado-api/properties-collection-ado.md)