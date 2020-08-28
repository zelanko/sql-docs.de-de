---
description: Resync-Methode
title: Resync-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 79a43a36fb68063c2f0c880f0d8d086714dcfffe
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989481"
---
# <a name="resync-method"></a>Resync-Methode
Aktualisiert die Daten im aktuellen [Recordset](./recordset-object-ado.md) -Objekt oder der [Fields](./fields-collection-ado.md) -Auflistung eines [Datensatz](./record-object-ado.md) -Objekts aus der zugrunde liegenden Datenbank.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Recordset.Resync AffectRecords, ResyncValues Record.Fields.Resync ResyncValues  
```  
  
#### <a name="parameters"></a>Parameter  
 *AffectRecords*  
 Optional. Ein [affectenum](./affectenum.md) -Wert, der bestimmt, wie viele Datensätze von der **Resync** -Methode betroffen sind. Der Standardwert ist " **adaffectall**". Dieser Wert ist mit der **Resync** -Methode der **Fields** -Auflistung eines **Datensatz** -Objekts nicht verfügbar.  
  
 *ResyncValues*  
 Optional. Ein [ResyncEnum](./resyncenum.md) -Wert, der angibt, ob zugrunde liegende Werte überschrieben werden. Der Standardwert ist **adResyncAllValues**.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="recordset"></a>Recordset  
 Verwenden Sie die **Resync** -Methode, um Datensätze im aktuellen **Recordset** mit der zugrunde liegenden Datenbank erneut zu synchronisieren. Dies ist nützlich, wenn Sie entweder einen statischen oder einen Vorwärts Cursor verwenden, aber alle Änderungen in der zugrunde liegenden Datenbank anzeigen möchten.  
  
 Wenn Sie die Eigenschaft " [Cursor Location](./cursorlocation-property-ado.md) " auf " **adUseClient**" festlegen, ist die **erneute Synchronisierung** nur für nicht schreibgeschützte **Recordset** -Objekte verfügbar.  
  
 Anders als bei der [Requery](./requery-method.md) -Methode führt die **Resync** -Methode den zugrunde liegenden Befehl des **Recordset** -Objekts nicht erneut aus. Neue Datensätze in der zugrunde liegenden Datenbank sind nicht sichtbar.  
  
 Wenn der Versuch der erneuten Synchronisierung aufgrund eines Konflikts mit den zugrunde liegenden Daten (z. b. ein Datensatz von einem anderen Benutzer gelöscht) fehlschlägt, gibt der Anbieter Warnungen an die [Fehler](./errors-collection-ado.md) Auflistung zurück, und es tritt ein Laufzeitfehler auf. Verwenden Sie die [Filter](./filter-property.md) -Eigenschaft (**adFilterConflictingRecords**) und die [Status](./status-property-ado-recordset.md) -Eigenschaft, um Datensätze mit Konflikten zu suchen.  
  
 Wenn die dynamischen Eigenschaften für die [eindeutige Tabelle](./unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) und den [Resync-Befehl](./resync-command-property-dynamic-ado.md) festgelegt sind und das **Recordset** das Ergebnis der Ausführung eines Verknüpfungs Vorgangs für mehrere Tabellen ist, führt die **Resync** -Methode den in der Eigenschaft " **Resync Command** " angegebenen Befehl nur für die Tabelle aus, die in der Eigenschaft " **Unique Table** " genannt wird.  
  
## <a name="fields"></a>Felder  
 Verwenden Sie die **Resync** -Methode, um die Werte der **Fields** -Auflistung eines **Datensatz** -Objekts mit der zugrunde liegenden Datenquelle erneut zu synchronisieren. Die [count](./count-property-ado.md) -Eigenschaft ist von dieser Methode nicht betroffen.  
  
 Wenn *resyncvalues* auf **adResyncAllValues** (Standardwert) festgelegt ist, werden die Eigenschaften " [UnderlyingValue](./underlyingvalue-property.md)", " [value](./value-property-ado.md)" und " [OriginalValue](./originalvalue-property-ado.md) " der [Feld](./field-object.md) Objekte in der Sammlung synchronisiert. Wenn *resyncvalues* auf **adresyncunderlyingvalues**festgelegt ist, wird nur die **UnderlyingValue** -Eigenschaft synchronisiert.  
  
 Der Wert der Eigenschaft **Status** für jedes **Feld** Objekt zum Zeitpunkt des Aufrufes wirkt sich auch auf das Verhalten der **erneuten Synchronisierung**aus. Bei **Feld** Objekten, die die **Status** Werte **adfieldkdingunknown** oder **adfieldpdinginsert**aufweisen, hat die **erneute Synchronisierung** keine Auswirkung. Bei den **Status** Werten **adfieldpdingchange** oder **adfieldpdingdelete**synchronisiert **Resync** Datenwerte für Felder, die noch in der Datenquelle vorhanden sind.  
  
 Bei der **erneuten Synchronisierung** werden die **Status** Werte von **Feld** Objekten nur dann geändert, wenn beim Aufruf der **erneuten Synchronisierung** ein Fehler auftritt. Wenn das Feld z. b. nicht mehr vorhanden ist, gibt der Anbieter einen entsprechenden **Status** Wert für das **Feld** Objekt zurück, z. b. **adfielddoesnotexist**. Zurückgegebene **Status** Werte können logisch in dem Wert der **Status** -Eigenschaft kombiniert werden.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Fields-Collection (ADO)](./fields-collection-ado.md)  
    :::column-end:::
    :::column:::
        [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine Resync-Methode (VB)](./resync-method-example-vb.md)   
 [Beispiel für eine Resync-Methode (VC + +)](./resync-method-example-vc.md)   
 [Clear-Methode (ADO)](./clear-method-ado.md)   
 [UnderlyingValue-Eigenschaft](./underlyingvalue-property.md)