---
description: Status-Eigenschaft – Beispiel (Field) (VB)
title: Status Eigenschafts Beispiel (Feld) (VB) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Status property [ADO Field], Visual Basic example
ms.assetid: fdd09b60-39c7-44be-8008-e891a031f80e
author: rothja
ms.author: jroth
ms.openlocfilehash: 23a6ebaa724e06ce4a8283b95e3d7a982c8deef1
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988693"
---
# <a name="status-property-example-field-vb"></a>Status-Eigenschaft – Beispiel (Field) (VB)
Im folgenden Beispiel wird ein Dokument aus einem Ordner mit Lese-/Schreibzugriff mit dem [Internet Publishing Provider](../../guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)geöffnet. Die [Status](./status-property-ado-field.md) -Eigenschaft eines [Feld](./field-object.md) Objekts des [Datensatzes](./record-object-ado.md) wird zuerst auf **adfieldpdinginsert**festgelegt und dann auf **adFieldOK**aktualisiert.  
  
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
  
 Mit dem folgenden Code wird ein **Feld** aus einem **Datensatz** gelöscht, der in einem schreibgeschützten Dokument geöffnet wurde. Der **Status** wird auf **adfieldpdingdelete**festgelegt. Bei der [Aktualisierung](./update-method.md)schlägt der Löschvorgang fehl, und der **Status** **lautet adfieldpdingdelete** Plus **adfieldpermissiondenied**. Mit [CancelUpdate](./cancelupdate-method-ado.md) wird die Einstellung für den ausstehenden **Status** gelöscht.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Field-Objekt](./field-object.md)   
 [Record-Objekt (ADO)](./record-object-ado.md)   
 [Status-Eigenschaft (ADO-Feld)](./status-property-ado-field.md)