---
title: Befehls Objekt Parameter | Microsoft-Dokumentation
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
ms.openlocfilehash: 29ad7f3aa9347af77080b04fb309f8b50b95dbe4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925875"
---
# <a name="command-object-parameters"></a>Parameter für Command-Objekt
Im vorherigen Thema wurde erläutert, wie [ein einfacher Befehl erstellt und ausgeführt](../../../ado/guide/data/creating-and-executing-a-simple-command.md)wird. Eine interessantere Verwendung für das [Command](../../../ado/reference/ado-api/command-object-ado.md) -Objekt wird im nächsten Beispiel veranschaulicht, in dem der SQL-Befehl parametrisiert wurde. Diese Änderung ermöglicht es, den Befehl wiederzuverwenden und jedes Mal einen anderen Wert für den Parameter zu übergeben. Da die Eigenschaft [vorbereitete Eigenschaft](../../../ado/reference/ado-api/prepared-property-ado.md) für das **Command** -Objekt auf **true**festgelegt ist, muss der Anbieter den in [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) angegebenen Befehl kompilieren, bevor er zum ersten Mal ausgeführt wird. Außerdem wird der kompilierte Befehl im Arbeitsspeicher beibehalten. Dadurch wird die Ausführung des Befehls bei der ersten Ausführung bei der ersten Ausführung verlangsamt, da der Aufwand für die Vorbereitung erforderlich ist, was jedoch bei jedem Aufruf des Befehls zu einer Leistungssteigerung führt. Daher sollten Befehle nur vorbereitet werden, wenn Sie mehr als einmal verwendet werden.  
  
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
  
 Nicht alle Anbieter unterstützen vorbereitete Befehle. Wenn der Anbieter die Befehls Vorbereitung nicht unterstützt, gibt er möglicherweise einen Fehler zurück, sobald diese Eigenschaft auf " **true**" festgelegt ist. Wenn kein Fehler zurückgegeben wird, wird die Anforderung zum Vorbereiten des Befehls ignoriert und die **vorbereitete** Eigenschaft auf **false**festgelegt.
