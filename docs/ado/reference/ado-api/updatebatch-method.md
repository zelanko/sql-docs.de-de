---
description: UpdateBatch-Methode
title: UpdateBatch-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::UpdateBatch
- Recordset15::raw_UpdateBatch
helpviewer_keywords:
- UpdateBatch method [ADO]
ms.assetid: 23f9314c-b027-4a51-aeae-50caa2977740
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b462fb22758481f3237a2a8c793b76dc50956ad
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776959"
---
# <a name="updatebatch-method"></a>UpdateBatch-Methode
Schreibt alle ausstehenden Batch Aktualisierungen auf den Datenträger.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.UpdateBatch AffectRecords, PreserveStatus  
```  
  
#### <a name="parameters"></a>Parameter  
 *AffectRecords*  
 Optional. Ein [affectenum](./affectenum.md) -Wert, der angibt, wie viele Datensätze von der **UpdateBatch** -Methode betroffen sind.  
  
 *PreserveStatus*  
 Optional. Ein **boolescher** Wert, der angibt, ob für lokale Änderungen, wie von der [Status](./status-property-ado-recordset.md) -Eigenschaft angegeben, ein Commit ausgeführt werden soll. Wenn dieser Wert auf **true**festgelegt ist, bleibt die **Status** -Eigenschaft jedes Datensatzes unverändert, nachdem das Update abgeschlossen wurde.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie die **UpdateBatch** -Methode, wenn Sie ein **Recordset** -Objekt im Batch Update Modus ändern, um alle in einem **Recordset** -Objekt vorgenommenen Änderungen an die zugrunde liegende Datenbank zu übertragen  
  
 Wenn das **Recordset** -Objekt die Batch Aktualisierung unterstützt, können Sie mehrere Änderungen an einem oder mehreren Datensätzen lokal zwischenspeichern, bis Sie die **UpdateBatch** -Methode aufrufen. Wenn Sie den aktuellen Datensatz bearbeiten oder einen neuen Datensatz hinzufügen, wenn Sie die **UpdateBatch** -Methode aufrufen, ruft ADO automatisch die [Update](./update-method.md) -Methode auf, um ausstehende Änderungen am aktuellen Datensatz zu speichern, bevor die Batch Änderungen an den Anbieter übertragen werden. Sie sollten die Batch Aktualisierung entweder mit einem Keyset-oder STATIC-Cursor verwenden.  
  
> [!NOTE]
>  Das Angeben von **adAffectGroup** als Wert für diesen Parameter führt zu einem Fehler, wenn im aktuellen **Recordset** keine sichtbaren Datensätze vorhanden sind (z. b. ein Filter, bei dem keine Datensätze vorhanden sind).  
  
 Wenn der Versuch, Änderungen zu übertragen, aufgrund eines Konflikts mit den zugrunde liegenden Daten (z. b. ein Datensatz bereits von einem anderen Benutzer gelöscht) fehlschlägt, gibt der Anbieter Warnungen an die [Fehler](./errors-collection-ado.md) Auflistung zurück, und es tritt ein Laufzeitfehler auf. Verwenden Sie die [Filter](./filter-property.md) -Eigenschaft (**adFilterAffectedRecords**) und die [Status](./status-property-ado-recordset.md) -Eigenschaft, um Datensätze mit Konflikten zu suchen.  
  
 Verwenden Sie die [CancelBatch](./cancelbatch-method-ado.md) -Methode, um alle ausstehenden Batch Aktualisierungen abzubrechen.  
  
 Wenn die dynamischen Eigenschaften [Unique Table](./unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) und [Update Resync](./update-resync-property-dynamic-ado.md) festgelegt sind und das **Recordset** das Ergebnis der Ausführung einer Verknüpfungs Operation für mehrere Tabellen ist, dann wird die Ausführung der **UpdateBatch** -Methode implizit von der [Resync](./resync-method.md) -Methode gefolgt von den Einstellungen der Eigenschaft [Update Resync](./update-resync-property-dynamic-ado.md) gefolgt.  
  
 Die Reihenfolge, in der die einzelnen Updates eines Batches in der Datenquelle ausgeführt werden, ist nicht notwendigerweise identisch mit der Reihenfolge, in der Sie für das lokale **Recordset**ausgeführt wurden. Die Aktualisierungs Reihenfolge hängt vom Anbieter ab. Berücksichtigen Sie dies beim Codieren von Aktualisierungen, die miteinander verknüpft sind, z. b. Foreign Key-Einschränkungen bei einer INSERT-oder Update-Datei.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für UpdateBatch und CancelBatch-Methoden (VB)](./updatebatch-and-cancelbatch-methods-example-vb.md)   
 [Beispiel für UpdateBatch und CancelBatch-Methoden (VC + +)](./updatebatch-and-cancelbatch-methods-example-vc.md)   
 [CancelBatch-Methode (ADO)](./cancelbatch-method-ado.md)   
 [Clear-Methode (ADO)](./clear-method-ado.md)   
 [LockType-Eigenschaft (ADO)](./locktype-property-ado.md)   
 [Update-Methode](./update-method.md)