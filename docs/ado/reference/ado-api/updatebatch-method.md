---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 11c930efdffe5eb685494843f2b0abe7b753ea3d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710417"
---
# <a name="updatebatch-method"></a>UpdateBatch-Methode
Schreibt alle ausstehenden BatchUpdates auf den Datenträger.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.UpdateBatch AffectRecords, PreserveStatus  
```  
  
#### <a name="parameters"></a>Parameter  
 *AffectRecords*  
 Optional. Ein [AffectEnum](../../../ado/reference/ado-api/affectenum.md) Wert, der angibt, wie viele Datensätze der **UpdateBatch** Methode wirkt sich auf.  
  
 *PreserveStatus*  
 Optional. Ein **booleschen** -Wert, der angibt, ob lokale geändert wird, wie durch die [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) Eigenschaft Commit ausgeführt werden soll. Wenn dieser Wert, um festgelegt ist **"true"** , **Status** Eigenschaft jedes Datensatzes bleibt unverändert, nachdem das Update abgeschlossen ist.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **UpdateBatch** Methode, die beim Ändern einer **Recordset** Objekt im Modus "Batch-Update", übertragen alle Änderungen, die einer **Recordset** Objekt, das der zugrunde liegenden Datenbank.  
  
 Wenn die **Recordset** Objekt unterstützt die Batch zu aktualisieren, können Sie mehrere Änderungen an einen oder mehrere Datensätze zwischenspeichern, lokal, bis Sie aufrufen, die **UpdateBatch** Methode. Wenn Sie den aktuellen Datensatz bearbeiten oder Hinzufügen eines neuen Datensatzes, beim Aufrufen der **UpdateBatch** -Methode, ADO ruft automatisch die [Update](../../../ado/reference/ado-api/update-method.md) Methode, um alle ausstehenden Änderungen am aktuellen Datensatz vor dem Speichern übertragen die im Batchmodus Änderungen an den Anbieter. Verwenden Sie Batch mit einem Keyset oder static-Cursor wird aktualisiert.  
  
> [!NOTE]
>  Angeben von **AdAffectGroup** wie der Wert für diesen Parameter zu einem Fehler führt, wenn es keine Datensätze angezeigt, in der aktuellen werden **Recordset** (z. B. einen Filter für die keine Datensätze entsprechen).  
  
 Wenn der Versuch zum Übertragen von Änderungen für einige oder alle Datensätze aufgrund eines Konflikts mit der zugrunde liegenden Daten ein Fehler auftritt (z. B. ein Datensatz wurde bereits gelöscht von einem anderen Benutzer), der Anbieter gibt Warnungen, um die [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung und ein während der Ausführung ein Fehler auftritt. Verwenden der [Filter](../../../ado/reference/ado-api/filter-property.md) Eigenschaft (**AdFilterAffectedRecords**) und die [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) Eigenschaft, um Datensätze mit Konflikten zu suchen.  
  
 Um alle ausstehenden Batch-Updates zu stornieren, verwenden die [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) Methode.  
  
 Wenn die [eindeutige Tabelle](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) und [Update Resync](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) dynamische Eigenschaften festgelegt sind, und die **Recordset** ist das Ergebnis der Ausführung einer JOIN-Operation für mehrere Tabellen, und klicken Sie dann die Ausführung der **UpdateBatch** Methode ist implizit, gefolgt von der [Resync](../../../ado/reference/ado-api/resync-method.md) -Methode, abhängig von den Einstellungen von der [Update Resync](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) Eigenschaft.  
  
 Die Reihenfolge an, unter denen die einzelnen Updates eines Batches, für die Datenquelle ausgeführt werden, ist nicht unbedingt identisch mit der Reihenfolge, in denen sie auf dem lokalen ausgeführt wurden **Recordset**. Aktualisierungsreihenfolge ist abhängig von den Anbieter. Berücksichtigen Sie dies beim Programmieren von Updates, die miteinander, z. B. foreign Key-Einschränkungen auf eine INSERT- oder Update verknüpft sind.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [UpdateBatch und CancelBatch-Methode – Beispiel (VB)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [UpdateBatch und CancelBatch-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [CancelBatch-Methode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Clear-Methode (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [LockType-Eigenschaft (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [Update-Methode](../../../ado/reference/ado-api/update-method.md)
