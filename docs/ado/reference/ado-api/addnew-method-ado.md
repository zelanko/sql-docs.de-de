---
title: AddNew-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::AddNew
- Recordset15::raw_AddNew
helpviewer_keywords:
- AddNew method [ADO]
ms.assetid: a9f54be9-5763-45d0-a6eb-09981b03bc08
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 911509c62c5ae93bc73ca94469ac776195d2a8b1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63065264"
---
# <a name="addnew-method-ado"></a>AddNew-Methode (ADO)
Erstellt einen neuen Datensatz für einen aktualisierbaren [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.AddNew FieldList, Values  
```  
  
#### <a name="parameters"></a>Parameter  
 *recordset*  
 Ein **Recordset** Objekt.  
  
 *FieldList*  
 Dies ist optional. Ein einzelner Name oder ein Array von Namen oder die Ordnungspositionen der Felder im neuen Datensatz.  
  
 *Werte*  
 Dies ist optional. Ein einzelner Wert oder ein Array von Werten für die Felder im neuen Datensatz. Wenn *Fieldlist* ist ein Array, *Werte* muss auch ein Array mit der gleichen Anzahl von Elementen andernfalls, ein Fehler auftritt. Die Reihenfolge von Feldnamen muss es sich um die Reihenfolge der Werte des Felds in jedem Array entsprechen.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **AddNew** Methode zum Erstellen und initialisieren einen neuen Datensatz. Verwenden der [unterstützt](../../../ado/reference/ado-api/supports-method.md) -Methode mit **AdAddNew** (eine [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md) Wert) zu überprüfen, ob Sie Datensätze, mit dem aktuellen hinzufügen können **Recordset**Objekt.  
  
 Nach dem Aufrufen der **AddNew** Methode, der neue Datensatz wird zum aktuellen Datensatz und bleibt der aktuelle aufzurufen, nachdem Sie die [Update](../../../ado/reference/ado-api/update-method.md) Methode. Da der neue Datensatz angefügt wird die **Recordset**, einen Aufruf von **MoveNext** befolgen das Update wird das Ende verschoben der **Recordset**, sodass **EOF**  "True". Wenn die **Recordset** Objekt unterstützt keine Lesezeichen, das Sie möglicherweise nicht in der Lage, den neuen Datensatz zugreifen, nachdem Sie zu einem anderen Datensatz wechseln. Je nach Cursortyp unter Umständen müssen Sie zum Aufrufen der [Requery](../../../ado/reference/ado-api/requery-method.md) Methode, um den neuen Datensatz zugänglich zu machen.  
  
 Aufrufen **AddNew** beim Bearbeiten des aktuellen Datensatzes oder beim Hinzufügen eines neuen Datensatzes, ADO Ruft die **Update** Methode, um alle speichern Änderungen und erstellt dann den neuen Datensatz.  
  
 Das Verhalten von der **AddNew** Methode hängt von der Updatemodus von der **Recordset** Objekt und gibt an, ob Sie übergeben die *Fieldlist* und *Werte*Argumente.  
  
 In *sofortupdatemodus* (in dem der Anbieter schreibt Änderungen in der zugrunde liegenden Datenquelle nach Aufrufen der **aktualisieren** Methode), wird beim Aufruf der **AddNew** -Methode ohne Argumente legt die [EditMode](../../../ado/reference/ado-api/editmode-property.md) Eigenschaft **AdEditAdd** (ein [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md) Wert). Der Anbieter wird jeder Wert feldänderungen lokal zwischengespeichert. Aufrufen der **Update** Methode wird der neue Datensatz in der Datenbank und setzt die **EditMode** Eigenschaft **AdEditNone** (ein **EditModeEnum**Wert). Übergeben der *Fieldlist* und *Werte* Argumente ADO sofort wird der neue Datensatz in der Datenbank (keine **Update** Aufruf erforderlich ist); die **EditMode**  Eigenschaftswert nicht ändert (**AdEditNone**).  
  
 In *Update Batchmodus* (in dem der Anbieter speichert mehrere Änderungen, und sie in der zugrunde liegenden Datenquelle schreibt, nur bei Aufruf der [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) Methode), wird beim Aufruf der **AddNew** -Methode ohne Argumente legt die **EditMode** Eigenschaft **AdEditAdd**. Der Anbieter wird jeder Wert feldänderungen lokal zwischengespeichert. Aufrufen der **Update** Methode fügt den neuen Eintrag mit dem aktuellen **Recordset**, aber der Anbieter die Änderungen der zugrunde liegenden Datenbank bereitstellen, oder nicht Zurücksetzen der **EditMode** um **AdEditNone**, bis Sie rufen die **UpdateBatch** Methode. Übergeben der *Fieldlist* und *Werte* Argumente ADO sendet des neuen Eintrags an den Anbieter für die Speicherung in einem Cache und legt die **EditMode** zu **AdEditAdd** ; aufrufen, müssen Sie die **UpdateBatch** Methode, um den neuen Datensatz in der zugrunde liegenden Datenbank zu veröffentlichen.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie mit der AddNew-Methode mit der Feldliste und die Werteliste enthalten, um zu erfahren, wie die Feldliste und die Werteliste als Arrays enthalten.  
  
```  
create table aa1 (intf int, charf char(10))  
insert into aa1 values (2, 'aa')  
  
Dim cn As New adodb.Connection  
Dim rs As New adodb.Recordset  
Dim cmd As New adodb.Command  
  
cn.ConnectionString = "Provider=SQLOLEDB;Data Source=alexverb2;uid=sa;pwd=foo$bar00;"  
  
cn.Open  
rs.Open "select * from xxx..aa1", cn, adOpenKeyset, adLockOptimistic  
  
Dim fieldsArray(1) As Variant  
fieldsArray(0) = "intf"  
fieldsArray(1) = "charf"  
Dim values(1) As Variant  
values(0) = 4  
values(1) = "as"  
rs.AddNew fieldsArray, values  
rs.Update  
```  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [AddNew-Methode – Beispiel (VB)](../../../ado/reference/ado-api/addnew-method-example-vb.md)   
 [AddNew-Methode – Beispiel (VBScript)](../../../ado/reference/ado-api/addnew-method-example-vbscript.md)   
 [AddNew-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/addnew-method-example-vc.md)   
 [CancelUpdate-Methode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [EditMode-Eigenschaft](../../../ado/reference/ado-api/editmode-property.md)   
 [Requery-Methode](../../../ado/reference/ado-api/requery-method.md)   
 [Supports-Methode](../../../ado/reference/ado-api/supports-method.md)   
 [Update-Methode](../../../ado/reference/ado-api/update-method.md)   
 [UpdateBatch-Methode](../../../ado/reference/ado-api/updatebatch-method.md)
