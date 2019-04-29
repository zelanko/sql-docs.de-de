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
manager: craigg
ms.openlocfilehash: 002e0f570aa2143ddba4a5b55f3cba1537389e77
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63138682"
---
# <a name="field-object"></a>Field-Objekt
Stellt eine Spalte mit einem gemeinsamen Datentyp.  
  
## <a name="remarks"></a>Hinweise  
 Jede **Feld** -Objekt entspricht, auf eine Spalte in der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Sie verwenden die [Wert](../../../ado/reference/ado-api/value-property-ado.md) Eigenschaft **Feld** Objekte festlegen oder Zurückgeben von Daten für den aktuellen Datensatz. Abhängig von den Funktionen der Anbieter verfügbar macht, einige Auflistungen, Methoden oder Eigenschaften eine **Feld** Objekt möglicherweise nicht zur Verfügung.  
  
 Mit den Auflistungen, Methoden und Eigenschaften einer **Feld** -Objekts können Sie folgende Möglichkeiten:  
  
-   Der Name eines Felds mit Zurückgeben der [Namen](../../../ado/reference/ado-api/name-property-ado.md) Eigenschaft.  
  
-   Anzeigen oder ändern Sie die Daten in das Feld mit dem **Wert** Eigenschaft. **Wert** ist die Standardeigenschaft der **Feld** Objekt.  
  
-   Zurückgeben der grundlegenden Merkmale eines Felds mit dem [Typ](../../../ado/reference/ado-api/type-property-ado.md), [Genauigkeit](../../../ado/reference/ado-api/precision-property-ado.md), und [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) Eigenschaften.  
  
-   Zurückgeben der deklarierte Größe eines Felds mit dem [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) Eigenschaft.  
  
-   Zurückgeben von der tatsächlichen Größe der Daten in einem bestimmten Feld mit dem [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md) Eigenschaft.  
  
-   Bestimmen, welche Arten von Funktionen unterstützt werden, für ein bestimmtes Feld mit dem [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) Eigenschaft und [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung.  
  
-   Bearbeiten Sie die Werte der Felder, die lange Binär- oder Zeichendaten Daten mit der [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) und [GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md) Methoden.  
  
-   Wenn der Anbieter Batchaktualisierungen unterstützt, Auflösen von Diskrepanzen bei Feldwerten während des BatchUpdates mit der [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) und [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) Eigenschaften.  
  
 Alle Metadateneigenschaften (**Namen**, **Typ**, **DefinedSize**, **Genauigkeit**, und **NumericScale**) stehen Sie vor dem Öffnen der **Feld** des Objekts **Recordset**. Zu diesem Zeitpunkt festlegen eignet sich für die dynamische Erstellung von Formularen.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Feld Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/field-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Fields-Auflistung (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
