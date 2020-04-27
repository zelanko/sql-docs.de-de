---
title: Status Eigenschafts Beispiel (Feld) (VB) | Microsoft-Dokumentation
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
ms.openlocfilehash: c28a0b615a9f250c8539e87abf9fefbc11f513ee
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67916825"
---
# <a name="status-property-example-field-vb"></a>Status-Eigenschaft – Beispiel (Field) (VB)
Im folgenden Beispiel wird ein Dokument aus einem Ordner mit Lese-/Schreibzugriff mit dem [Internet Publishing Provider](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)geöffnet. Die [Status](../../../ado/reference/ado-api/status-property-ado-field.md) -Eigenschaft eines [Feld](../../../ado/reference/ado-api/field-object.md) Objekts des [Datensatzes](../../../ado/reference/ado-api/record-object-ado.md) wird zuerst auf **adfieldpdinginsert**festgelegt und dann auf **adFieldOK**aktualisiert.  
  
```  
'BeginStatusFieldVB  
  
 ' to integrate this code replace the values in the source string  
  
Sub Main()  
  
   Dim File As ADODB.Record  
   Dim strFile As String  
   Dim Cnxn As ADODB.Connection  
   Dim strCnxn As String  
  
   Set Cnxn = New ADODB.Connection  
   strCnxn = "url=https://MyServer/"  
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
  
 Im folgenden Beispiel wird ein bekanntes **Feld** aus einem **Datensatz** gelöscht, der aus einem Dokument geöffnet wurde. Die Eigenschaft **Status** wird zuerst auf **adFieldOK**und dann auf **adfieldpdingunknown**festgelegt.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
 Mit dem folgenden Code wird ein **Feld** aus einem **Datensatz** gelöscht, der in einem schreibgeschützten Dokument geöffnet wurde. Der **Status** wird auf **adfieldpdingdelete**festgelegt. Bei der [Aktualisierung](../../../ado/reference/ado-api/update-method.md)schlägt der Löschvorgang fehl, und der **Status** **lautet adfieldpdingdelete** Plus **adfieldpermissiondenied**. Mit [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) wird die Einstellung für den ausstehenden **Status** gelöscht.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)   
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Status-Eigenschaft (ADO-Feld)](../../../ado/reference/ado-api/status-property-ado-field.md)
