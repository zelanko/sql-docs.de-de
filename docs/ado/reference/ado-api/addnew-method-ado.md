---
description: AddNew-Methode (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: b3c6d6b33177f3c3db7c2d414759a5067a91b80d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451582"
---
# <a name="addnew-method-ado"></a>AddNew-Methode (ADO)
Erstellt einen neuen Datensatz für ein Aktualisier bares [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.AddNew FieldList, Values  
```  
  
#### <a name="parameters"></a>Parameter  
 *Recordset*  
 Ein **Recordset** -Objekt.  
  
 *FieldList*  
 Optional. Ein einzelner Name oder ein Array von Namen oder Ordinalpositionen der Felder im neuen Datensatz.  
  
 *Werte*  
 Optional. Ein einzelner Wert oder ein Array von Werten für die Felder im neuen Datensatz. Wenn *FieldList* ein Array ist, müssen die *Werte* auch ein Array mit derselben Anzahl von Membern sein. Andernfalls tritt ein Fehler auf. Die Reihenfolge der Feldnamen muss der Reihenfolge der Feldwerte in jedem Array entsprechen.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **AddNew** -Methode, um einen neuen Datensatz zu erstellen und zu initialisieren. Verwenden Sie die Methode [unterstützt](../../../ado/reference/ado-api/supports-method.md) mit **adAddNew** (ein [Cursor](../../../ado/reference/ado-api/cursoroptionenum.md) Wert), um zu überprüfen, ob dem aktuellen **Recordset** -Objektdaten Sätze hinzugefügt werden können.  
  
 Nachdem Sie die **AddNew** -Methode aufgerufen haben, wird der neue Datensatz zum aktuellen Datensatz und bleibt nach dem Abrufen der [Update](../../../ado/reference/ado-api/update-method.md) -Methode aktuell. Da der neue Datensatz an das **Recordset**angehängt wird, wird ein **MoveNext** -Befehl nach dem Update nach dem Ende des **Recordsets**verschoben, sodass **EOF** true ist. Wenn das **Recordset** -Objekt keine Lesezeichen unterstützt, können Sie möglicherweise nicht mehr auf den neuen Datensatz zugreifen, wenn Sie zu einem anderen Datensatz wechseln. Abhängig vom Cursortyp müssen Sie möglicherweise die [Requery](../../../ado/reference/ado-api/requery-method.md) -Methode aufzurufen, um den neuen Datensatz zugänglich zu machen.  
  
 Wenn Sie beim Bearbeiten des aktuellen Datensatzes oder beim Hinzufügen eines neuen Datensatzes **AddNew** aufrufen, ruft ADO die **Update** -Methode auf, um alle Änderungen zu speichern und dann den neuen Datensatz zu erstellen.  
  
 Das Verhalten der **AddNew** -Methode hängt vom Aktualisierungs Modus des **Recordset** -Objekts und davon ab, ob die Argumente *FieldList* und *Values* übergeben werden.  
  
 Im *sofortigen Update Modus* (in dem der Anbieter Änderungen in die zugrunde liegende Datenquelle schreibt, nachdem Sie die **Update** -Methode aufgerufen haben), wird durch Aufrufen der **AddNew** -Methode ohne Argumente die [EditMode](../../../ado/reference/ado-api/editmode-property.md) -Eigenschaft auf **adEditAdd** (ein [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md) -Wert) festgelegt. Der Anbieter speichert alle Feldwert Änderungen lokal zwischen. Durch Aufrufen der **Update** -Methode wird der neue Datensatz in der Datenbank bereitgestellt, und die **EditMode** -Eigenschaft wird auf " **adEditNone** " ( **EditModeEnum** -Wert) zurückgesetzt. Wenn Sie die Argumente *FieldList* und *Values* übergeben, sendet ADO den neuen Datensatz sofort an die Datenbank (kein **Update** -Befehl erforderlich); der **EditMode** -Eigenschafts Wert ändert sich nicht (**adEditNone**).  
  
 Im *Batch Aktualisierungs Modus* (in dem der Anbieter mehrere Änderungen zwischenspeichert und Sie nur dann in die zugrunde liegende Datenquelle schreibt, wenn Sie die [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) -Methode aufrufen), wird durch Aufrufen der **AddNew** -Methode ohne Argumente die **EditMode** -Eigenschaft auf **adEditAdd**festgelegt. Der Anbieter speichert alle Feldwert Änderungen lokal zwischen. Durch den Aufruf der **Update** -Methode wird der neue Datensatz dem aktuellen **Recordset**hinzugefügt, aber der Anbieter sendet die Änderungen nicht an die zugrunde liegende Datenbank oder setzt **EditMode** auf **adEditNone**zurück, bis Sie die **UpdateBatch** -Methode aufrufen. Wenn Sie die Argumente *FieldList* und *Values* übergeben, sendet ADO den neuen Datensatz zum Speichern in einem Cache an den Anbieter und legt **EditMode** auf **adEditAdd**; fest. Sie müssen die **UpdateBatch** -Methode aufrufen, um den neuen Datensatz in der zugrunde liegenden Datenbank zu veröffentlichen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie die AddNew-Methode mit der Liste der Felder und Werte verwendet wird, um zu erfahren, wie Sie die Feldliste und Werteliste als Arrays einschließen.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [AddNew-Methode (Beispiel) (VB)](../../../ado/reference/ado-api/addnew-method-example-vb.md)   
 [AddNew-Methode (Beispiel) (VBScript)](../../../ado/reference/ado-api/addnew-method-example-vbscript.md)   
 [AddNew-Methode (Beispiel) (VC + +)](../../../ado/reference/ado-api/addnew-method-example-vc.md)   
 [CancelUpdate-Methode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [EditMode-Eigenschaft](../../../ado/reference/ado-api/editmode-property.md)   
 [Requery-Methode](../../../ado/reference/ado-api/requery-method.md)   
 [Unterstützt Methode](../../../ado/reference/ado-api/supports-method.md)   
 [Update-Methode](../../../ado/reference/ado-api/update-method.md)   
 [UpdateBatch-Methode](../../../ado/reference/ado-api/updatebatch-method.md)
