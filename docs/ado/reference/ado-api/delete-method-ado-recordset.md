---
title: Delete-Methode (ADO Recordset) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 272b953a39a9ccbb01d94acc59d374304bda3ad0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63140185"
---
# <a name="delete-method-ado-recordset"></a>Delete-Methode (ADO-Recordset)
Löscht den aktuellen Datensatz oder eine Gruppe von Datensätzen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.Delete AffectRecords  
```  
  
#### <a name="parameters"></a>Parameter  
 *AffectRecords*  
 Ein [AffectEnum](../../../ado/reference/ado-api/affectenum.md) Wert, der bestimmt, wie viele Datensätze der **löschen** Methode wirkt sich auf. Der Standardwert ist **AdAffectCurrent**.  
  
> [!NOTE]
>  **AdAffectAll** und **AdAffectAllChapters** sind keine gültigen Argumente, **löschen**.  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe der **löschen** Methode kennzeichnet den aktuellen Datensatz oder eine Gruppe von Datensätzen in einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt zum Löschen. Wenn die **Recordset** Objekt nicht Datensatz löschen, kann ein Fehler auftritt. Wenn Sie sich im sofortupdatemodus sind, werden die Löschvorgänge in der Datenbank sofort. Wenn ein Datensatz (aufgrund von Datenbank-integritätsverletzungen, z. B.) wurde erfolgreich gelöscht werden kann, der Datensatz bleibt im Bearbeitungsmodus nach dem Aufruf von [Update](../../../ado/reference/ado-api/update-method.md). Dies bedeutet, dass Sie die Aktualisierung mit abbrechen müssen [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) vor dem Verlassen des aktuellen Datensatzes (z. B. mit [schließen](../../../ado/reference/ado-api/close-method-ado.md), [verschieben](../../../ado/reference/ado-api/move-method-ado.md), oder [ NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)).  
  
 Wenn Sie im Modus "Batch-Update" sind, werden die Datensätze zum Löschen aus dem Cache markiert und das eigentliche löschen erfolgt beim Aufrufen der [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) Methode. Verwenden der [Filter](../../../ado/reference/ado-api/filter-property.md) Eigenschaft, um die gelöschten Datensätze anzuzeigen.  
  
 Abrufen von Feldwerten aus den gelöschten Datensatz generiert einen Fehler. Nach dem Löschen des aktuellen Datensatzes, bleibt der gelöschte Datensatz aktuell, bis Sie zu einem anderen Datensatz verschieben. Sobald Sie Abkehr von den gelöschten Datensatz, es nicht mehr zugänglich ist.  
  
 Wenn Sie Löschvorgänge in einer Transaktion schachteln, können Sie mit der Wiederherstellen gelöschter Datensätze mit den [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) Methode. Wenn Sie im Modus "Batch-Update" sind, können Sie Abbrechen, einen ausstehenden Löschvorgang oder eine Gruppe von ausstehenden Löschvorgängen mit dem [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) Methode.  
  
 Wenn der Versuch zum Löschen von Datensätzen aufgrund eines Konflikts mit dem zugrunde liegenden fehlschlägt (z. B. ein Datensatz wurde bereits gelöscht von einem anderen Benutzer), der Anbieter gibt Warnungen an, die die [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung jedoch kein Programm angehalten wird die Ausführung. Ein Laufzeitfehler tritt auf, nur dann, wenn Konflikte für alle angeforderten Datensätze bestehen.  
  
 Wenn die [eindeutige Tabelle](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) dynamische Eigenschaft festgelegt ist, und die **Recordset** ist das Ergebnis der Ausführung einer JOIN-Operation für mehrere Tabellen, und klicken Sie dann die **löschen** Methode wird nur gelöscht werden. Zeilen aus der Tabelle, die mit dem Namen in der [eindeutige Tabelle](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) Eigenschaft.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Delete – Methodenbeispiel (VB)](../../../ado/reference/ado-api/delete-method-example-vb.md)   
 [Delete – Methodenbeispiel (VBScript)](../../../ado/reference/ado-api/delete-method-example-vbscript.md)   
 [Delete – Methodenbeispiel (VC++)](../../../ado/reference/ado-api/delete-method-example-vc.md)   
 [Delete-Methode (Fields-Collection – ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete-Methode (ADO-Parameters-Auflistung)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [DeleteRecord-Methode (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
