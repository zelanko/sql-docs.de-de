---
description: Delete-Methode (ADO-Recordset)
title: Delete-Methode (ADO-Recordset) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_Delete
- Recordset15::Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 1eb9209c-602c-4507-b0c2-6527a599b67d
author: rothja
ms.author: jroth
ms.openlocfilehash: b494885b6dafc7b91b76c37ac1817ac198335360
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444152"
---
# <a name="delete-method-ado-recordset"></a>Delete-Methode (ADO-Recordset)
Löscht den aktuellen Datensatz oder eine Gruppe von Datensätzen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.Delete AffectRecords  
```  
  
#### <a name="parameters"></a>Parameter  
 *AffectRecords*  
 Ein [affectenum](../../../ado/reference/ado-api/affectenum.md) -Wert, der bestimmt, wie viele Datensätze von der **Delete** -Methode betroffen sind. Der Standardwert ist **adaffectcurrent**.  
  
> [!NOTE]
>  " **adaffectall** " und " **adaffectallchapters** " sind keine gültigen Argumente zum **Löschen**.  
  
## <a name="remarks"></a>Bemerkungen  
 Mithilfe der **Delete** -Methode wird der aktuelle Datensatz oder eine Gruppe von Datensätzen in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt zum Löschen markiert. Wenn das **Recordset** -Objekt das Löschen von Datensätzen nicht zulässt, tritt ein Fehler auf. Wenn Sie sich im sofortigen Update Modus befinden, werden Löschungen sofort in der Datenbank ausgeführt. Wenn ein Datensatz nicht erfolgreich gelöscht werden kann (z. b. aufgrund von Daten Bank Integritäts Verstößen), verbleibt der Datensatz nach dem [Update Update](../../../ado/reference/ado-api/update-method.md)im Bearbeitungsmodus. Dies bedeutet, dass Sie das Update mit [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) abbrechen müssen, bevor Sie den aktuellen Datensatz verschieben (z. b. mit " [Close](../../../ado/reference/ado-api/close-method-ado.md)", " [Move](../../../ado/reference/ado-api/move-method-ado.md)" oder " [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)").  
  
 Wenn Sie sich im Batch Aktualisierungs Modus befinden, werden die Datensätze zum Löschen aus dem Cache markiert, und der tatsächliche Löschvorgang erfolgt, wenn Sie die [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) -Methode aufrufen. Verwenden Sie die [Filter](../../../ado/reference/ado-api/filter-property.md) -Eigenschaft, um die gelöschten Datensätze anzuzeigen.  
  
 Beim Abrufen von Feldwerten aus dem gelöschten Datensatz wird ein Fehler generiert. Nach dem Löschen des aktuellen Datensatzes bleibt der gelöschte Datensatz aktuell, bis Sie zu einem anderen Datensatz wechseln. Nachdem Sie den gelöschten Datensatz entfernt haben, ist er nicht mehr zugänglich.  
  
 Wenn Sie Löschungen in einer Transaktion Schachteln, können Sie gelöschte Datensätze mit der [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) -Methode wiederherstellen. Wenn Sie sich im Batch Aktualisierungs Modus befinden, können Sie ein ausstehendes löschen oder eine Gruppe von ausstehenden Löschungen mit der [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) -Methode abbrechen.  
  
 Wenn der Versuch, Datensätze zu löschen, aufgrund eines Konflikts mit den zugrunde liegenden Daten (z. b. ein Datensatz bereits von einem anderen Benutzer gelöscht) fehlschlägt, gibt der Anbieter Warnungen an die [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung zurück, hält die Ausführung des Programms jedoch nicht an. Ein Laufzeitfehler tritt nur auf, wenn für alle angeforderten Datensätze Konflikte vorliegen.  
  
 Wenn die dynamische Eigenschaft der [eindeutigen Tabelle](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) festgelegt ist und das **Recordset** das Ergebnis der Ausführung eines Verknüpfungs Vorgangs für mehrere Tabellen ist, löscht die **Delete** -Methode nur Zeilen aus der Tabelle mit dem Namen in der [eindeutigen Table](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) -Eigenschaft.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Delete-Methode (Beispiel) (VB)](../../../ado/reference/ado-api/delete-method-example-vb.md)   
 [Delete-Methode (Beispiel) (VBScript)](../../../ado/reference/ado-api/delete-method-example-vbscript.md)   
 [Delete-Methode (Beispiel) (VC + +)](../../../ado/reference/ado-api/delete-method-example-vc.md)   
 [Delete-Methode (ADO Fields-Auflistung)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete-Methode (ADO Parameters-Sammlung)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [DeleteRecord-Methode (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
