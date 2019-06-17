---
title: Updatemethode für | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Update
helpviewer_keywords:
- Update method [ADO]
ms.assetid: 6b2a9c31-1a7e-40db-8a53-30720d0f6cc1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e48185f0524a920d52092540f5e3ed6d8546edfe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710510"
---
# <a name="update-method"></a>Update-Methode
Speichert alle Änderungen an der aktuellen Zeile eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt oder die [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung von einer [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.Update Fields, Values  
record.Fields.Update  
```  
  
#### <a name="parameters"></a>Parameter  
 *Fields*  
 Optional. Ein **Variant** , die einen eindeutigen Namen, darstellt oder **Variant** Array, das darstellt, Namen oder die Positionen der Felder, die Sie ändern möchten.  
  
 *Werte*  
 Optional. Ein **Variant** , die einen einzelnen Wert darstellt oder **Variant** Array, das Werte für das Feld oder Felder in den neuen Eintrag darstellt.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="recordset"></a>Recordset  
 Verwenden der **Update** Methode zum Speichern von Änderungen Sie, um den aktuellen Datensatz vornehmen eine **Recordset** Objekt seit dem Aufrufen der [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) Methode oder seit Feldwerte im ändern ein vorhandenen Datensatz. Die **Recordset** Objekt muss Updates unterstützen.  
  
 Führen Sie eine der folgenden Schritte aus, um Feldwerte festzulegen:  
  
-   Werte zuweisen einer [Feld](../../../ado/reference/ado-api/field-object.md) des Objekts [Wert](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft, und rufen die **Update** Methode.  
  
-   Übergeben Sie einen Feldnamen und den Wert als Argumente mit den **Update** aufrufen.  
  
-   Übergeben Sie ein Array von Namen und ein Array von Werten mit der **Update** aufrufen.  
  
 Wenn Sie Arrays von Feldern und Werten verwenden, muss eine gleiche Anzahl von Elementen in beiden Arrays vorhanden sein. Darüber hinaus muss die Reihenfolge der Feldnamen, die Reihenfolge der Feldwerte übereinstimmen. Wenn die Anzahl und Reihenfolge der Felder und Werte nicht übereinstimmen, tritt ein Fehler auf.  
  
 Wenn die **Recordset** Objekt unterstützt die Batch zu aktualisieren, können Sie mehrere Änderungen an einen oder mehrere Datensätze zwischenspeichern, lokal, bis Sie aufrufen, die [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) Methode. Wenn Sie den aktuellen Datensatz bearbeiten oder Hinzufügen eines neuen Datensatzes, beim Aufrufen der **UpdateBatch** -Methode, ADO ruft automatisch die **Update** Methode, um alle ausstehenden Änderungen am aktuellen Datensatz vor dem Speichern übertragen die im Batchmodus Änderungen an den Anbieter.  
  
 Wenn Sie aus dem Datensatz verschieben Sie zum Hinzufügen oder bearbeiten Sie vor dem Aufruf der **Update** , ADO wird automatisch Methodenaufruf **Update** zum Speichern der Änderungen. Rufen Sie die [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) Methode, wenn Sie Abbrechen von Änderungen an den aktuellen Datensatz oder einen neu hinzugefügten Datensatz verwerfen möchten.  
  
 Der aktuelle Datensatz bleibt die aktuelle aufzurufen, nachdem Sie die **Update** Methode.  
  
## <a name="record"></a>Datensatz  
 Die **Update** Methode schließt Hinzufügungen, löschungen und Aktualisierungen von Feldern in der [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung von einem **Datensatz** Objekt.  
  
 Z. B. Felder, die gelöscht werden, mit der **löschen** Methode sofort zum Löschen markiert sind, aber bleiben in der Auflistung. Die **Update** -Methode muss aufgerufen werden, um diese Felder aus der Auflistung des Anbieters tatsächlich zu löschen.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Fields-Collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Update- und CancelUpdate-Methode – Beispiel (VB)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [Update- und CancelUpdate-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [AddNew-Methode (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [CancelUpdate-Methode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [EditMode-Eigenschaft](../../../ado/reference/ado-api/editmode-property.md)   
 [UpdateBatch-Methode](../../../ado/reference/ado-api/updatebatch-method.md)
