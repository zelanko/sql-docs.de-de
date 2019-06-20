---
title: Resync-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::raw_Resync
- Fields::Resync
- Recordset20::Resync
- Fields::raw_Resync
helpviewer_keywords:
- Resync method [ADO]
ms.assetid: 73b355d4-a4c0-434b-bfc4-039b1c76b32e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 251c2f67861dd996ac78efc9a8e599d7ec191072
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711555"
---
# <a name="resync-method"></a>Resync-Methode
Aktualisiert die Daten in der aktuellen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt oder [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung von einem [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt, aus der zugrunde liegenden Datenbank.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Recordset.Resync AffectRecords, ResyncValues Record.Fields.Resync ResyncValues  
```  
  
#### <a name="parameters"></a>Parameter  
 *AffectRecords*  
 Optional. Ein [AffectEnum](../../../ado/reference/ado-api/affectenum.md) Wert, der bestimmt, wie viele Datensätze der **Resync** Methode wirkt sich auf. Der Standardwert ist **AdAffectAll**. Dieser Wert ist nicht verfügbar, mit der **Resync** -Methode der der **Felder** Auflistung von einem **Datensatz** Objekt.  
  
 *ResyncValues*  
 Optional. Ein [ResyncEnum](../../../ado/reference/ado-api/resyncenum.md) Wert, der angibt, ob die zugrunde liegende Werte überschrieben werden. Der Standardwert ist **AdResyncAllValues**.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="recordset"></a>Recordset  
 Verwenden der **Resync** Methode, um Datensätze in der aktuellen resynchronisieren **Recordset** mit der zugrunde liegenden Datenbank. Dies ist nützlich, wenn Sie einen statischen oder eines Vorwärtscursors Cursor verwenden, aber Sie Änderungen an der zugrunde liegenden Datenbank anzeigen möchten.  
  
 Setzen Sie die [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaft **AdUseClient**, **Resync** steht nur für nicht schreibgeschützte **Recordset** Objekte.  
  
 Im Gegensatz zu den [Requery](../../../ado/reference/ado-api/requery-method.md) -Methode, die **Resync** Methode wird nicht erneut ausgeführt. die **Recordset** Objekt zugrunde liegende Befehl. Neue Datensätze in der zugrunde liegenden Datenbank werden nicht angezeigt.  
  
 Wenn der Versuch zur neusynchronisierung aufgrund eines Konflikts mit der zugrunde liegenden Daten ein Fehler auftritt (z. B. ein Datensatz wurde wurde gelöscht von einem anderen Benutzer), der Anbieter gibt Warnungen an, die die [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung und ein Laufzeitfehler tritt auf. Verwenden der [Filter](../../../ado/reference/ado-api/filter-property.md) Eigenschaft (**vorliegt**) und die [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) Eigenschaft, um Datensätze mit Konflikten zu suchen.  
  
 Wenn die [eindeutige Tabelle](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) und [Resync Command](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) dynamische Eigenschaften festgelegt sind, und die **Recordset** ist das Ergebnis der Ausführung einer JOIN-Operation auf mehrere Tabellen, und klicken Sie dann auf die  **Resync-** Methode führt den Befehl in der **Resync Command** Eigenschaft nur für die Tabelle mit dem Namen in der **eindeutige Tabelle** Eigenschaft.  
  
## <a name="fields"></a>Felder  
 Verwenden der **Resync** Methode, um die Werte der erneut zu synchronisieren der **Felder** Auflistung von einer **Datensatz** Objekt mit der zugrunde liegenden Datenquelle. Die [Anzahl](../../../ado/reference/ado-api/count-property-ado.md) -Eigenschaft wird von dieser Methode nicht beeinflusst.  
  
 Wenn *ResyncValues* nastaven NA hodnotu **AdResyncAllValues** (der Standardwert), die [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md), [Wert](../../../ado/reference/ado-api/value-property-ado.md), und [ OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) Eigenschaften [Feld](../../../ado/reference/ado-api/field-object.md) Objekte in der Auflistung synchronisiert werden. Wenn *ResyncValues* nastaven NA hodnotu **AdResyncUnderlyingValues**, wird nur die **UnderlyingValue** Eigenschaft synchronisiert wird.  
  
 Der Wert des der **Status** -Eigenschaft für jedes **Feld** -Objekts zum Zeitpunkt des Aufrufs wirkt sich auch auf das Verhalten der **Resync**. Für **Feld** Objekte mit **Status** Werte **AdFieldPendingUnknown** oder **AdFieldPendingInsert**, **erneut synchronisieren**  hat keine Auswirkungen. Für **Status** Werte **AdFieldPendingChange** oder **AdFieldPendingDelete**, **Resync** synchronisiert Datenwerte für Felder, weiterhin in der Datenquelle vorhanden.  
  
 **Resync-** ändert nicht **Status** Werte **Feld** Objekte, es sei denn, ein Fehler tritt auf, beim **Resync** aufgerufen wird. Z. B. wenn das Feld nicht mehr vorhanden ist, der Anbieter gibt eine entsprechende **Status** Wert für die **Feld** Objekt, z. B. **AdFieldDoesNotExist**. Zurückgegebene **Status** Werte können kombiniert werden, logisch im Wert der **Status** Eigenschaft.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Fields-Collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Resync – Methodenbeispiel (VB)](../../../ado/reference/ado-api/resync-method-example-vb.md)   
 [Resync – Methodenbeispiel (VC++)](../../../ado/reference/ado-api/resync-method-example-vc.md)   
 [Clear-Methode (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [UnderlyingValue-Eigenschaft](../../../ado/reference/ado-api/underlyingvalue-property.md)
