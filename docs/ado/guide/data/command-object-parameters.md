---
title: Befehl Objektparameter | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Command object [ADO], parameters
ms.assetid: 10e7ef4a-78bf-4e91-931e-cbc6c065dd4c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f4fb4128333f1fdc5865186a202188fc64b6109f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47701738"
---
# <a name="command-object-parameters"></a>Parameter für Command-Objekt
Im vorherigen Thema erläutert [erstellen und Ausführen eines einfachen Befehls](../../../ado/guide/data/creating-and-executing-a-simple-command.md). Verwenden Sie einen interessanteren für die [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekt wird im nächsten Beispiel, in dem der SQL-Befehl parametrisiert wurde angezeigt. Diese Änderung ermöglicht es, den Befehl aus, und übergibt einen anderen Wert für den Parameter jedes Mal erneut verwenden. Da die [vorbereitet Eigenschaft](../../../ado/reference/ado-api/prepared-property-ado.md) Eigenschaft für die **Befehl** Objekt nastaven NA hodnotu **"true"**, ADO wird der Anbieter gezwungen, kompilieren Sie den Befehl, der im angegebenen [ CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) bevor Sie ihn zum ersten Mal ausführen. Es wird auch den kompilierten Befehl im Arbeitsspeicher beibehalten. Dies verlangsamt die Ausführung des Befehls etwas beim ersten, die sie aufgrund des Mehraufwands für vorbereiten, sondern führt zu einer Leistungssteigerung jedes Mal, wenn der Befehl, das anschließend aufgerufen wird ausgeführt wird. Aus diesem Grund sollten Befehle darauf vorbereitet sein, nur dann, wenn sie mehr als einmal verwendet werden.  
  
```  
'BeginManualParamCmd  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim objCmd As New ADODB.Command  
    Dim objParm1 As New ADODB.Parameter  
    Dim objRs As New ADODB.Recordset  
  
    ' Set the CommandText as a parameterized SQL query.  
    objCmd.CommandText = "SELECT OrderID, OrderDate, " & _  
                         "RequiredDate, ShippedDate " & _  
                         "FROM Orders " & _  
                         "WHERE CustomerID = ? " & _  
                         "ORDER BY OrderID"  
    objCmd.CommandType = adCmdText  
  
    ' Prepare command because we will be executing it more than once.  
    objCmd.Prepared = True  
  
    ' Create new parameter for CustomerID. Initial value is ALFKI.  
    Set objParm1 = objCmd.CreateParameter("CustId", adChar, _  
                    adParamInput, 5, "ALFKI")  
    objCmd.Parameters.Append objParm1  
  
    ' Connect to the data source.  
    Set objConn = GetNewConnection  
    objCmd.ActiveConnection = objConn  
  
    ' Execute once and display.  
    Set objRs = objCmd.Execute  
  
    Debug.Print objParm1.Value  
    Do While Not objRs.EOF  
        Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                    objRs(2) & vbTab & objRs(3)  
        objRs.MoveNext  
    Loop  
  
    ' .Set new param value, re-execute command, and display.  
    objCmd("CustId") = "CACTU"  
    Set objRs = objCmd.Execute  
  
    Debug.Print objParm1.Value  
    Do While Not objRs.EOF  
        Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                    objRs(2) & vbTab & objRs(3)  
        objRs.MoveNext  
    Loop  
  
    'clean up  
    objRs.Close  
    objConn.Close  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
    Set objParm1 = Nothing  
    Exit Sub  
  
ErrHandler:  
    'clean up  
    If objRs.State = adStateOpen Then  
        objRs.Close  
    End If  
  
    If objConn.State = adStateOpen Then  
        objConn.Close  
    End If  
  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
    Set objParm1 = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
'EndManualParamCmd  
  
'BeginNewConnection  
Private Function GetNewConnection() As ADODB.Connection  
    Dim oCn As New ADODB.Connection  
    Dim sCnStr As String  
  
    sCnStr = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Integrated Security='SSPI';Initial Catalog='Northwind';"  
    oCn.Open sCnStr  
  
    If oCn.State = adStateOpen Then  
        Set GetNewConnection = oCn  
    End If  
  
End Function  
'EndNewConnection  
```  
  
 Nicht alle Anbieter unterstützen vorbereitete Befehle. Wenn der Anbieter die befehlsvorbereitung nicht unterstützt, kann es einen Fehler zurück, sobald diese Eigenschaft, um festgelegt wird **"true"**. Wenn sie keinen Fehler zurückgibt, wird sie ignoriert der Anforderung zur Vorbereitung von dem Befehl und legt die **Prepared** Eigenschaft **"false"**.
