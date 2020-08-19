---
description: Beispiel für Cursor Type, LockType und EditMode Properties (VB)
title: Beispiel für Cursor Type, LockType und EditMode Properties (VB) | Microsoft-Dokumentation
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
- EditMode property [ADO], Visual Basic example
- CursorType property [ADO], Visual Basic example
- LockType property [ADO], Visual Basic example
ms.assetid: 2cb4a304-f40a-4897-8b93-82c2d8e93500
author: rothja
ms.author: jroth
ms.openlocfilehash: 3d9b0ae19ce5fbac150a86fc7db3d08b16840fbd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444282"
---
# <a name="cursortype-locktype-and-editmode-properties-example-vb"></a>Beispiel für Cursor Type, LockType und EditMode Properties (VB)
Dieses Beispiel veranschaulicht das Festlegen der Eigenschaften " [Cursor Type](../../../ado/reference/ado-api/cursortype-property-ado.md) " und " [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) " vor dem Öffnen eines [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md). Außerdem wird der Wert der [EditMode](../../../ado/reference/ado-api/editmode-property.md) -Eigenschaft unter verschiedenen Bedingungen angezeigt. Die EditModeOutput-Funktion ist erforderlich, damit diese Prozedur ausgeführt werden kann.  
  
```  
'BeginEditModeVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    ' recordset variables  
    Dim rstEmployees As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim SQLEmployees As String  
  
     ' open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
      ' set recordset properties through object refs  
      ' instead of through arguments to Open method  
    Set rstEmployees = New ADODB.Recordset  
    Set rstEmployees.ActiveConnection = Cnxn  
    rstEmployees.CursorLocation = adUseClient  
    rstEmployees.CursorType = adOpenStatic  
    rstEmployees.LockType = adLockBatchOptimistic  
  
     ' open recordset with data from Employee table  
    SQLEmployees = "employee"  
    rstEmployees.Open SQLEmployees, , , , adCmdTable  
  
    ' Show the EditMode property under different editing states  
    rstEmployees.AddNew  
        rstEmployees!emp_id = "T-T55555M"  
        rstEmployees!fname = "temp_fname"  
        rstEmployees!lname = "temp_lname"  
            'call function below  
            'to output results to debug window  
        EditModeOutput "After AddNew:", rstEmployees.EditMode  
        rstEmployees.UpdateBatch  
        EditModeOutput "After UpdateBatch:", rstEmployees.EditMode  
        rstEmployees!fname = "test"  
        EditModeOutput "After Edit:", rstEmployees.EditMode  
    rstEmployees.Close  
  
    ' Delete new record because this is a demonstration  
    Cnxn.Execute "DELETE FROM employee WHERE emp_id = 'T-T55555M'"  
  
    ' clean up  
    Cnxn.Close  
    Set rstEmployees = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstEmployees Is Nothing Then  
        If rstEmployees.State = adStateOpen Then rstEmployees.Close  
    End If  
    Set rstEmployees = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
  
Public Function EditModeOutput(strTemp As String, _  
   intEditMode As Integer)  
  
   ' Print report based on the value of the EditMode  
   ' property  
   Debug.Print strTemp  
   Debug.Print "  EditMode = ";  
  
   Select Case intEditMode  
      Case adEditNone  
         Debug.Print "adEditNone"  
      Case adEditInProgress  
         Debug.Print "adEditInProgress"  
      Case adEditAdd  
         Debug.Print "adEditAdd"  
   End Select  
  
End Function  
'EndEditModeVB  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cursor Type-Eigenschaft (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)   
 [Cursor typeumum](../../../ado/reference/ado-api/cursortypeenum.md)   
 [EditMode-Eigenschaft](../../../ado/reference/ado-api/editmode-property.md)   
 [Editmodeerum](../../../ado/reference/ado-api/editmodeenum.md)   
 [LockType-Eigenschaft (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [Locktypeaufumum](../../../ado/reference/ado-api/locktypeenum.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
