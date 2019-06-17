---
title: Status-Eigenschaft (ADO Field) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field::Status
- Field::get_Status
- Field::GetStatus
helpviewer_keywords:
- Status property [ADO Field]
ms.assetid: 8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a647051e7953d6f2977074feda94cf7e9f3d9d82
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711016"
---
# <a name="status-property-ado-field"></a>Status-Eigenschaft (ADO-Feld)
Gibt den Status einer [Feld](../../../ado/reference/ado-api/field-object.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) Wert. Der Standardwert ist **AdFieldOK**.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="record-field-status"></a>Datensatzstatus-Feld  
 Ändert sich der Wert des eine **Feld** Objekt in der Fields-Sammlung von einer [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt werden zwischengespeichert, bis des Objekts des [Update](../../../ado/reference/ado-api/update-method.md) Methode wird aufgerufen. Wenn die Änderung an der Wert des Felds einen Fehler verursacht, löst OLE DB zu diesem Zeitpunkt den Fehler **DB_E_ERRORSOCCURRED** (2147749409). Die Status-Eigenschaft aller der **Feld** Objekte in der **Felder** -Auflistung, die den Fehler verursacht hat, enthält einen Wert aus der [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) , beschreibt die Ursache des das Problem.  
  
 Zur Verbesserung der Leistung, Hinzufügungen und löschungen von der [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Sammlungen von der **Datensatz** Objekt werden zwischengespeichert, bis die **Update** -Methode aufgerufen wird, und klicken Sie dann die Änderungen werden in einer Batchaktualisierung optimistische vorgenommen. Wenn die **Update** -Methode nicht aufgerufen wird, der Server wird nicht aktualisiert. Wenn alle Updates ein Fehler auftritt, und klicken Sie dann ein OLE DB-Anbieter-Fehler (DB_E_ERRORSOCCURRED) zurückgegeben wird und die **Status** Eigenschaft gibt an, die kombinierten Werte des Statuscodes Vorgang und Fehler. Z. B. **AdFieldPendingInsert OR AdFieldPermissionDenied**. Die **Status** -Eigenschaft für jedes **Feld** können verwendet werden, um zu bestimmen, warum die **Feld** wurde nicht hinzugefügt, geändert oder gelöscht.  
  
 Viele Arten von Problemen beim Hinzufügen, ändern oder Löschen einer **Feld** gemeldet werden, über die **Status** Eigenschaft. Wenn der Benutzer löscht z. B. eine **Feld**, für die Löschung markiert ist die **Felder** Auflistung. Wenn die nachfolgenden **Update** gibt einen Fehler zurück, da der Benutzer versucht hat, löschen Sie eine **Feld** für die sie verfügen nicht über die Berechtigung, die **Feld** müssen eine  **Status** von **AdFieldPermissionDenied OR AdFieldPendingDelete**. Aufrufen der [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) Methode Wiederherstellungen ursprünglichen Werte und legt die **Status** zu **AdFieldOK**.  
  
 Auf ähnliche Weise die **Update** Methode möglicherweise einen Fehler zurück, da eine neue **Feld** hinzugefügt und einen Ungültiger Wert angegeben wurde. In diesem Fall die neue **Feld** werden in der **Felder** Auflistung und haben den Status der **AdFieldPendingInsert** und vielleicht **AdFieldCantCreate** (abhängig von Ihrem Anbieter). Sie können einen geeigneten Wert angeben, für die neue **Feld** , und rufen Sie **Update** erneut aus.  
  
## <a name="recordset-field-status"></a>Recordset-Feldstatus  
 Ändert sich der Wert des eine **Feld** Objekt in der Fields-Sammlung, der entweder ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) werden zwischengespeichert, bis des Objekts des [Update](../../../ado/reference/ado-api/update-method.md) Methode wird aufgerufen. Wenn die Änderung an der Wert des Felds einen Fehler verursacht, löst OLE DB zu diesem Zeitpunkt den Fehler **DB_E_ERRORSOCCURRED** (2147749409). Die Status-Eigenschaft aller der **Feld** Objekte in der **Felder** -Auflistung, die den Fehler verursacht hat, enthält einen Wert aus der [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) , beschreibt die Ursache des das Problem.  
  
## <a name="applies-to"></a>Gilt für  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Status-Eigenschaft – Beispiel (Field) (VB)](../../../ado/reference/ado-api/status-property-example-field-vb.md)   
 [Status-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
