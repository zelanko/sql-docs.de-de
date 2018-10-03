---
title: Status-Eigenschaft – Beispiel (Field) (VB) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Status property [ADO Field], Visual Basic example
ms.assetid: fdd09b60-39c7-44be-8008-e891a031f80e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6554e76488cd83452c0ab1617c9bd65e9196c11
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47816368"
---
# <a name="status-property-example-field-vb"></a>Status-Eigenschaft – Beispiel (Field) (VB)
Im folgende Beispiel wird ein Dokument aus einem Ordner mit Lese-/Schreibzugriff geöffnet. die [Internet Publishing-Anbieter](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Die [Status](../../../ado/reference/ado-api/status-property-ado-field.md) Eigenschaft eine [Feld](../../../ado/reference/ado-api/field-object.md) Objekt die [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) wird zunächst festgelegt **AdFieldPendingInsert**, und klicken Sie dann auf aktualisiertwerden**AdFieldOk**.  
  
```  
'BeginStatusFieldVB  
  
 ' to integrate this code replace the values in the source string  
  
Sub Main()  
  
   Dim File As ADODB.Record  
   Dim strFile As String  
   Dim Cnxn As ADODB.Connection  
   Dim strCnxn As String  
  
   Set Cnxn = New ADODB.Connection  
   strCnxn = "url=http://MyServer/"  
   Cnxn.Open strCnxn  
  
   Set File = New ADODB.Record  
   strFile = "Folder/FileName"  
   ' Open a read/write document  
   File.Source = strFile  
   File.ActiveConnection = Cnxn  
   File.Mode = adModeReadWrite  
   File.Open  
  
   Debug.Print "Append a couple of fields"  
  
   File.Fields.Append "chektest:fld1", adWChar, 42, adFldUpdatable, "fld1"  
   File.Fields.Append "chektest:fld2", adWChar, 42, adFldUpdatable, "fld2"  
  
   Debug.Print "status for the fields"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert  
  
    'turn off error-handling to verify field status  
   On Error Resume Next  
  
   File.Fields.Update  
  
   Debug.Print "Update succeeds"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert + adFieldUnavailable  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert + adFieldUnavailable  
  
    ' resume default error-handling  
   On Error GoTo 0  
  
     ' clean up  
    File.Close  
    Cnxn.Close  
    Set File = Nothing  
    Set Cnxn = Nothing  
  
End Sub  
'EndStatusFieldVB  
```  
  
 Im folgenden Beispiel wird ein bekanntes **Feld** aus einem **Datensatz** aus einem Dokument geöffnet. Die **Status** Eigenschaft wird zunächst festgelegt werden, um **AdFieldOK**, klicken Sie dann **AdFieldPendingUnknown**.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
 Der folgende code Löscht ein **Feld** aus einem **Datensatz** in einem Dokument schreibgeschützt geöffnet. **Status** festgelegt **AdFieldPendingDelete**. Am [Update](../../../ado/reference/ado-api/update-method.md), der Löschvorgang schlägt fehl und **Status** werden **AdFieldPendingDelete** plus **AdFieldPermissionDenied**. [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) löscht die ausstehenden **Status** festlegen.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)   
 [-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Status-Eigenschaft (ADO Field)](../../../ado/reference/ado-api/status-property-ado-field.md)
