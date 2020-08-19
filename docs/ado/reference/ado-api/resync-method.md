---
description: Resync-Methode
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 68ece4d9ad109defafa8a0c64dbf901fb20a87b2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442272"
---
# <a name="resync-method"></a>Resync-Methode
Aktualisiert die Daten im aktuellen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt oder der [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung eines [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) -Objekts aus der zugrunde liegenden Datenbank.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Recordset.Resync AffectRecords, ResyncValues Record.Fields.Resync ResyncValues  
```  
  
#### <a name="parameters"></a>Parameter  
 *AffectRecords*  
 Optional. Ein [affectenum](../../../ado/reference/ado-api/affectenum.md) -Wert, der bestimmt, wie viele Datensätze von der **Resync** -Methode betroffen sind. Der Standardwert ist " **adaffectall**". Dieser Wert ist mit der **Resync** -Methode der **Fields** -Auflistung eines **Datensatz** -Objekts nicht verfügbar.  
  
 *ResyncValues*  
 Optional. Ein [ResyncEnum](../../../ado/reference/ado-api/resyncenum.md) -Wert, der angibt, ob zugrunde liegende Werte überschrieben werden. Der Standardwert ist **adResyncAllValues**.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="recordset"></a>Recordset  
 Verwenden Sie die **Resync** -Methode, um Datensätze im aktuellen **Recordset** mit der zugrunde liegenden Datenbank erneut zu synchronisieren. Dies ist nützlich, wenn Sie entweder einen statischen oder einen Vorwärts Cursor verwenden, aber alle Änderungen in der zugrunde liegenden Datenbank anzeigen möchten.  
  
 Wenn Sie die Eigenschaft " [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) " auf " **adUseClient**" festlegen, ist die **erneute Synchronisierung** nur für nicht schreibgeschützte **Recordset** -Objekte verfügbar.  
  
 Anders als bei der [Requery](../../../ado/reference/ado-api/requery-method.md) -Methode führt die **Resync** -Methode den zugrunde liegenden Befehl des **Recordset** -Objekts nicht erneut aus. Neue Datensätze in der zugrunde liegenden Datenbank sind nicht sichtbar.  
  
 Wenn der Versuch der erneuten Synchronisierung aufgrund eines Konflikts mit den zugrunde liegenden Daten (z. b. ein Datensatz von einem anderen Benutzer gelöscht) fehlschlägt, gibt der Anbieter Warnungen an die [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung zurück, und es tritt ein Laufzeitfehler auf. Verwenden Sie die [Filter](../../../ado/reference/ado-api/filter-property.md) -Eigenschaft (**adFilterConflictingRecords**) und die [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) -Eigenschaft, um Datensätze mit Konflikten zu suchen.  
  
 Wenn die dynamischen Eigenschaften für die [eindeutige Tabelle](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) und den [Resync-Befehl](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) festgelegt sind und das **Recordset** das Ergebnis der Ausführung eines Verknüpfungs Vorgangs für mehrere Tabellen ist, führt die **Resync** -Methode den in der Eigenschaft " **Resync Command** " angegebenen Befehl nur für die Tabelle aus, die in der Eigenschaft " **Unique Table** " genannt wird.  
  
## <a name="fields"></a>Felder  
 Verwenden Sie die **Resync** -Methode, um die Werte der **Fields** -Auflistung eines **Datensatz** -Objekts mit der zugrunde liegenden Datenquelle erneut zu synchronisieren. Die [count](../../../ado/reference/ado-api/count-property-ado.md) -Eigenschaft ist von dieser Methode nicht betroffen.  
  
 Wenn *resyncvalues* auf **adResyncAllValues** (Standardwert) festgelegt ist, werden die Eigenschaften " [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)", " [value](../../../ado/reference/ado-api/value-property-ado.md)" und " [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) " der [Feld](../../../ado/reference/ado-api/field-object.md) Objekte in der Sammlung synchronisiert. Wenn *resyncvalues* auf **adresyncunderlyingvalues**festgelegt ist, wird nur die **UnderlyingValue** -Eigenschaft synchronisiert.  
  
 Der Wert der Eigenschaft **Status** für jedes **Feld** Objekt zum Zeitpunkt des Aufrufes wirkt sich auch auf das Verhalten der **erneuten Synchronisierung**aus. Bei **Feld** Objekten, die die **Status** Werte **adfieldkdingunknown** oder **adfieldpdinginsert**aufweisen, hat die **erneute Synchronisierung** keine Auswirkung. Bei den **Status** Werten **adfieldpdingchange** oder **adfieldpdingdelete**synchronisiert **Resync** Datenwerte für Felder, die noch in der Datenquelle vorhanden sind.  
  
 Bei der **erneuten Synchronisierung** werden die **Status** Werte von **Feld** Objekten nur dann geändert, wenn beim Aufruf der **erneuten Synchronisierung** ein Fehler auftritt. Wenn das Feld z. b. nicht mehr vorhanden ist, gibt der Anbieter einen entsprechenden **Status** Wert für das **Feld** Objekt zurück, z. b. **adfielddoesnotexist**. Zurückgegebene **Status** Werte können logisch in dem Wert der **Status** -Eigenschaft kombiniert werden.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Fields-Collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
    :::column-end:::
    :::column:::
        [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine Resync-Methode (VB)](../../../ado/reference/ado-api/resync-method-example-vb.md)   
 [Beispiel für eine Resync-Methode (VC + +)](../../../ado/reference/ado-api/resync-method-example-vc.md)   
 [Clear-Methode (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [UnderlyingValue-Eigenschaft](../../../ado/reference/ado-api/underlyingvalue-property.md)
