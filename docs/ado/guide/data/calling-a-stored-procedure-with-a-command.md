---
title: Aufrufen einer gespeicherten Prozedur mit einem Befehl | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- calling stored procedures [ADO]
- stored procedures [ADO]
- commands [ADO]
ms.assetid: 685f7652-2271-4ede-b552-2eeb8c756b4c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4763939e3eccd0bf4783df87141619cbc0fb011c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702327"
---
# <a name="calling-a-stored-procedure-with-a-command"></a>Aufrufen einer gespeicherten Prozedur mit einem Befehl
Sie können einen Befehl verwenden, um eine gespeicherte Prozedur aufzurufen. Das Codebeispiel am Ende dieses Themas bezieht sich auf eine gespeicherte Prozedur in der Northwind-Beispieldatenbank namens CustOrdersOrders, die wie folgt definiert ist.  
  
```  
CREATE PROCEDURE CustOrdersOrders @CustomerID nchar(5) AS  
SELECT OrderID, OrderDate, RequiredDate, ShippedDate  
FROM Orders  
WHERE CustomerID = @CustomerID  
ORDER BY OrderID  
```  
  
 Sehen Sie, dass es sich bei SQL Server-Dokumentation für Weitere Informationen zum definieren, und rufen gespeicherte Prozeduren.  
  
 Diese gespeicherte Prozedur ist ähnlich wie der Befehl verwendet [Objekt Befehlsparameter](../../../ado/guide/data/command-object-parameters.md). Es dauert eine Kunden-ID-Parameter und gibt Informationen zu den Bestellungen dieses Kunden zurück. Das folgende Codebeispiel verwendet diese gespeicherte Prozedur als Quelle für ein ADO **Recordset**.  
  
 Mithilfe der gespeicherten Prozedur können Sie eine weitere Funktion von ADO zuzugreifen: die **Parameter** Auflistung **aktualisieren** Methode. Mithilfe dieser Methode kann ADO automatisch alle Informationen zu den Parametern, die zur Laufzeit den Befehl erforderlichen ausfüllen. Mit dieser Technik wird eine Leistungseinbuße, da ADO die Datenquelle für die Informationen zu den Parametern Abfrage ausführen muss.  
  
 Andere wichtige Unterschiede zwischen den im folgenden Codebeispiel und dem Code in [Objekt Befehlsparameter](../../../ado/guide/data/command-object-parameters.md), wobei die Parameter manuell eingegeben wurden. Dieser Code wird zunächst nicht festgelegt der **Prepared** Eigenschaft **"true"** da sie eine SQL-Server, die gespeicherte Prozedur und per Definition vorkompiliert ist. Zweitens wird die **Befehlstyp (CommandType)** Eigenschaft der **Befehl** Objekt geändert werden, um **AdCmdStoredProc** im zweiten Beispiel ADO informiert, dass der Befehl eine gespeicherte Prozedur wurde.  
  
 Schließlich muss im zweiten Beispiel der Parameter über einen Index verwiesen werden beim Festlegen des Werts, weil Sie nicht den Namen des Parameters zur Entwurfszeit wissen möglicherweise. Wenn Sie den Namen des Parameters kennen, legen Sie die neue [NamedParameters](../../../ado/reference/ado-api/namedparameters-property-ado.md) Eigenschaft der **Befehl** Objekt auf "true", und verweisen Sie auf den Namen der Eigenschaft. Sie Fragen sich vielleicht, warum die Position des ersten Parameters in der gespeicherten Prozedur erwähnten (@CustomerID) 1 statt 0 (`objCmd(1) = "ALFKI"`). Dies ist da Parameter 0 einen Rückgabewert von der SQL Server gespeicherte Prozedur enthält.  
  
```  
'BeginAutoParamCmd  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim objCmd As New ADODB.Command  
    Dim objParm1 As New ADODB.Parameter  
    Dim objRs As New ADODB.Recordset  
  
    ' Set CommandText equal to the stored procedure name.  
    objCmd.CommandText = "CustOrdersOrders"  
    objCmd.CommandType = adCmdStoredProc  
  
    ' Connect to the data source.  
    Set objConn = GetNewConnection  
    objCmd.ActiveConnection = objConn  
  
    ' Automatically fill in parameter info from stored procedure.  
    objCmd.Parameters.Refresh  
  
    ' Set the param value.  
    objCmd(1) = "ALFKI"  
  
    ' Execute once and display...  
    Set objRs = objCmd.Execute  
  
    Debug.Print objParm1.Value  
    Do While Not objRs.EOF  
        Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                    objRs(2) & vbTab & objRs(3)  
        objRs.MoveNext  
    Loop  
  
    ' ...then set new param value, re-execute command, and display.  
    objCmd(1) = "CACTU"  
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
'EndAutoParamCmd  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Knowledge Base-Artikel 117500](https://go.microsoft.com/fwlink/?LinkId=117500)
