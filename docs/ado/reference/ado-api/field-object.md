---
title: Field-Objekt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field
helpviewer_keywords:
- Field object [ADO]
ms.assetid: b10a72fc-3c4b-4186-a70b-993dc9f7a092
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 04dbf3069896b9a7668d64a2f1d322f0b17ca5f3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67918682"
---
# <a name="field-object"></a>Field-Objekt
Stellt eine Datenspalte mit einem gemeinsamen Datentyp dar.  
  
## <a name="remarks"></a>Hinweise  
 Jedes **Feld** Objekt entspricht einer Spalte im [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Mit der [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft von **Feld** Objekten können Sie Daten für den aktuellen Datensatz festlegen oder zurückgeben. Abhängig von der vom Anbieter verfügbar gemachten Funktionalität sind einige Auflistungen, Methoden oder Eigenschaften eines **Feld** Objekts möglicherweise nicht verfügbar.  
  
 Mit den Auflistungen, Methoden und Eigenschaften eines **Feld** Objekts können Sie folgende Aufgaben ausführen:  
  
-   Gibt den Namen eines Felds mit der [Name](../../../ado/reference/ado-api/name-property-ado.md) -Eigenschaft zurück.  
  
-   Anzeigen oder Ändern der Daten im Feld mit der **value** -Eigenschaft. **Value** ist die Standard Eigenschaft des **Field** -Objekts.  
  
-   Gibt die grundlegenden Eigenschaften eines Felds mit den Eigenschaften [Type](../../../ado/reference/ado-api/type-property-ado.md), [Precision](../../../ado/reference/ado-api/precision-property-ado.md)und [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) zurück.  
  
-   Gibt die deklarierte Größe eines Felds mit der [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) -Eigenschaft zurück.  
  
-   Gibt die tatsächliche Größe der Daten in einem angegebenen Feld mit der [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md) -Eigenschaft zurück.  
  
-   Bestimmen Sie, welche Funktionstypen für ein bestimmtes Feld mit der [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) -Eigenschaft und der [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung unterstützt werden.  
  
-   Bearbeiten Sie die Werte von Feldern mit langen Binär-oder Long-Zeichendaten mit der [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) -Methode und der [GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md) -Methode.  
  
-   Wenn der Anbieter Batch Aktualisierungen unterstützt, lösen Sie bei der Batch Aktualisierung Unterschiede in den Feldwerten mit den Eigenschaften [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) und [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) .  
  
 Alle Metadateneigenschaften ("**Name**", " **Type**", " **DefinedSize**", " **Precision**" und " **NumericScale**") stehen vor dem Öffnen des **Recordsets**des **Feld** Objekts zur Verfügung. Die Festlegung zu diesem Zeitpunkt ist für das dynamische Erstellen von Formularen nützlich.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Feld Objekteigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/field-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fields-Auflistung (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
