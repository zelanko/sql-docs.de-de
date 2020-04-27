---
title: EditMode-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::EditMode
helpviewer_keywords:
- EditMode property
ms.assetid: a1b04bb2-8c8b-47f9-8477-bfd0368b6f68
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c0ffc6fb258799b0ab0bb03e7acbd922f6a67d1f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67918984"
---
# <a name="editmode-property"></a>EditMode-Eigenschaft
Gibt den Bearbeitungsstatus des aktuellen Datensatzes an.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md) -Wert zurück.  
  
## <a name="remarks"></a>Hinweise  
 ADO verwaltet einen Bearbeitungs Puffer, der dem aktuellen Datensatz zugeordnet ist. Diese Eigenschaft gibt an, ob an diesem Puffer Änderungen vorgenommen wurden oder ob ein neuer Datensatz erstellt wurde. Verwenden Sie die **EditMode** -Eigenschaft, um den Bearbeitungsstatus des aktuellen Datensatzes zu bestimmen. Sie können auf ausstehende Änderungen testen, wenn ein Bearbeitungsvorgang unterbrochen wurde, und feststellen, ob Sie die [Update](../../../ado/reference/ado-api/update-method.md) -oder [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) -Methode verwenden müssen.  
  
 Im *sofort Update Modus* wird die **EditMode** -Eigenschaft auf " **adEditNone** " zurückgesetzt, nachdem ein erfolgreicher Aufruf der **Update** -Methode aufgerufen wurde. Wenn durch einen [Delete-DELETE](../../../ado/reference/ado-api/delete-method-ado-recordset.md) -Vorgang der Datensatz oder die Datensätze in der Datenquelle (z. b. aufgrund von Verletzungen der referenziellen Integrität) nicht erfolgreich gelöscht werden, verbleibt das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) im Bearbeitungsmodus (**EditMode** = **adEditInProgress**). Daher muss **CancelUpdate** aufgerufen werden, bevor der aktuelle Datensatz (z. b. [Move](../../../ado/reference/ado-api/move-method-ado.md), [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)oder [Close](../../../ado/reference/ado-api/close-method-ado.md) ) verschoben wird.  
  
 Im *Batch Update Modus* (in dem der Anbieter mehrere Änderungen zwischenspeichert und Sie nur dann in die zugrunde liegende Datenquelle schreibt, wenn Sie die [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) -Methode aufrufen), wird der Wert der **EditMode** -Eigenschaft geändert, wenn der erste Vorgang ausgeführt wird, und er wird nicht durch einen Aufrufen der **Update** -Methode zurückgesetzt. Nachfolgende Vorgänge ändern den Wert der **EditMode** -Eigenschaft nicht, auch wenn verschiedene Vorgänge ausgeführt werden. Wenn beispielsweise der erste Vorgang ist, einen neuen Datensatz hinzuzufügen, und der zweite Vorgang Änderungen an einem vorhandenen Datensatz vornimmt, ist die Eigenschaft von **EditMode** weiterhin **adEditAdd**. Die **EditMode** -Eigenschaft wird erst nach dem Aufrufen von **UpdateBatch**auf ' **adEditNone** ' zurückgesetzt. Um zu ermitteln, welche Vorgänge ausgeführt wurden, legen Sie die [Filter](../../../ado/reference/ado-api/filter-property.md) -Eigenschaft auf [adfilterpending](../../../ado/reference/ado-api/filtergroupenum.md) fest, sodass nur Datensätze mit ausstehenden Änderungen sichtbar sind, und untersuchen Sie die [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) -Eigenschaft jedes Datensatzes, um zu bestimmen, welche Änderungen an den Daten vorgenommen wurden.  
  
> [!NOTE]
>  **EditMode** kann nur dann einen gültigen Wert zurückgeben, wenn ein aktueller Datensatz vorhanden ist. **EditMode** gibt einen Fehler zurück, wenn [BOF oder EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) true ist oder wenn der aktuelle Datensatz gelöscht wurde.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Cursor Type, LockType und EditMode Properties (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [Beispiel für Cursor Type, LockType und EditMode Properties (VC + +)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [AddNew-Methode (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Delete-Methode (ADO-Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [CancelUpdate-Methode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Update-Methode](../../../ado/reference/ado-api/update-method.md)
