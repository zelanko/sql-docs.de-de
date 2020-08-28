---
description: Status-Eigenschaft (ADO-Feld)
title: Status-Eigenschaft (ADO-Feld) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 11f59e99eab0a742a4d7618f7ac66cb486af2933
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988721"
---
# <a name="status-property-ado-field"></a>Status-Eigenschaft (ADO-Feld)
Gibt den Status eines [Feld](./field-object.md) Objekts an.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen [fieldstatuusenum](./fieldstatusenum.md) -Wert zurück. Der Standardwert ist **adFieldOK**.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="record-field-status"></a>Status des Daten Satz Felds  
 Änderungen am Wert eines **Feld** Objekts in der Fields-Auflistung eines [Datensatz](./record-object-ado.md) -Objekts werden zwischengespeichert, bis die [Update](./update-method.md) -Methode des Objekts aufgerufen wird. Wenn die Änderung an dem Wert des Felds einen Fehler verursacht hat, löst OLE DB den Fehler **DB_E_ERRORSOCCURRED** (2147749409) aus. Die Status-Eigenschaft aller **Feld** Objekte in der **Fields** -Auflistung, die den Fehler verursacht hat, enthält einen Wert aus dem [FieldStatusEnum](./fieldstatusenum.md) , der die Ursache des Problems beschreibt.  
  
 Um die Leistung zu verbessern, werden Ergänzungen und Löschvorgänge für die [Fields](./fields-collection-ado.md) -Auflistungen des **Datensatz** -Objekts bis zum Aufruf der **Update** -Methode zwischengespeichert, und die Änderungen werden dann in einem optimistischen Batch Update vorgenommen. Wenn die **Update** -Methode nicht aufgerufen wird, wird der Server nicht aktualisiert. Wenn ein Update fehlschlägt, wird ein Fehler des OLE DB Anbieters (DB_E_ERRORSOCCURRED) zurückgegeben, und die **Status** -Eigenschaft gibt die kombinierten Werte des Vorgangs und des Fehler Status Codes an. Beispielsweise **adfieldpdinginsert oder adfieldpermissiondenied**. Mithilfe der Eigenschaft **Status** für jedes **Feld** können Sie feststellen, warum das **Feld** nicht hinzugefügt, geändert oder gelöscht wurde.  
  
 Viele Arten von Problemen, die beim Hinzufügen, ändern oder Löschen eines **Felds** auftreten, werden über die Eigenschaft **Status** gemeldet. Wenn der Benutzer z. b. ein **Feld**löscht, wird er aus der **Fields** -Auflistung zum Löschen markiert. Wenn bei der nachfolgenden **Aktualisierung** ein Fehler zurückgegeben wird, weil der Benutzer versucht hat, ein **Feld** zu löschen, für das Sie nicht über die erforderliche Berechtigung verfügen, hat das **Feld** den **Status** **adfieldpermissiondenied oder adfieldpdingdelete**. Durch Aufrufen der [CancelUpdate](./cancelupdate-method-ado.md) -Methode werden ursprüngliche Werte wieder hergestellt, und der **Status** wird auf **adFieldOK**festgelegt.  
  
 Entsprechend gibt die **Update** -Methode möglicherweise einen Fehler zurück, da ein neues **Feld** hinzugefügt wurde und ein unzulässiger Wert angegeben wurde. In diesem Fall ist das neue **Feld** in der **Fields** -Auflistung enthalten und hat den Status **adfieldpdinginsert** und möglicherweise **adfieldcantcreate** (je nach Anbieter). Sie können einen geeigneten Wert für das neue **Feld** angeben und **Update** erneut abrufen.  
  
## <a name="recordset-field-status"></a>Status des Recordset-Felds  
 Änderungen am Wert eines **Feld** Objekts in der Fields-Auflistung eines [Recordsets](./recordset-object-ado.md) werden zwischengespeichert, bis die [Update](./update-method.md) -Methode des Objekts aufgerufen wird. Wenn die Änderung an dem Wert des Felds einen Fehler verursacht hat, löst OLE DB den Fehler **DB_E_ERRORSOCCURRED** (2147749409) aus. Die Status-Eigenschaft aller **Feld** Objekte in der **Fields** -Auflistung, die den Fehler verursacht hat, enthält einen Wert aus dem [FieldStatusEnum](./fieldstatusenum.md) , der die Ursache des Problems beschreibt.  
  
## <a name="applies-to"></a>Gilt für  
 [Field-Objekt](./field-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Status Eigenschafts Beispiel (Feld) (VB)](./status-property-example-field-vb.md)   
 [Status-Eigenschaft – Beispiel (VC++)](./status-property-example-vc.md)