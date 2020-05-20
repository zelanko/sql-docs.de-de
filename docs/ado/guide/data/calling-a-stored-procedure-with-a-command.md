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
author: rothja
ms.author: jroth
ms.openlocfilehash: 998bda7d2c940b16f298fdfe436a2d60b27f09ba
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761216"
---
# <a name="calling-a-stored-procedure-with-a-command"></a>Aufrufen einer gespeicherten Prozedur mit einem Befehl
Sie können einen Befehl verwenden, um eine gespeicherte Prozedur aufzurufen. Das Codebeispiel am Ende dieses Themas bezieht sich auf eine gespeicherte Prozedur in der Northwind-Beispieldatenbank mit dem Namen CustOrdersOrders, die wie folgt definiert ist.  
  
```  
CREATE PROCEDURE CustOrdersOrders @CustomerID nchar(5) AS  
SELECT OrderID, OrderDate, RequiredDate, ShippedDate  
FROM Orders  
WHERE CustomerID = @CustomerID  
ORDER BY OrderID  
```  
  
 Weitere Informationen zum Definieren und Abrufen gespeicherter Prozeduren finden Sie in der SQL Server-Dokumentation.  
  
 Diese gespeicherte Prozedur ähnelt dem Befehl, der in [Befehls Objekt Parametern](../../../ado/guide/data/command-object-parameters.md)verwendet wird. Er übernimmt einen Kunden-ID-Parameter und gibt Informationen zu den Aufträgen dieses Kunden zurück. Im folgenden Codebeispiel wird diese gespeicherte Prozedur als Quelle für ein ADO- **Recordset**verwendet.  
  
 Mithilfe der gespeicherten Prozedur können Sie auf eine andere Funktion von ADO zugreifen: die **Aktualisierungs** Methode für die **Parameter** Auflistung. Mit dieser Methode kann ADO automatisch alle Informationen zu den Parametern ausfüllen, die für den Befehl zur Laufzeit erforderlich sind. Bei der Verwendung dieses Verfahrens gibt es eine Leistungs Einbuße, da ADO die Datenquelle nach den Informationen zu den Parametern Abfragen muss.  
  
 Andere wichtige Unterschiede bestehen zwischen dem folgenden Codebeispiel und dem Code in [Befehls Objekt Parametern](../../../ado/guide/data/command-object-parameters.md), bei denen die Parameter manuell eingegeben wurden. Zunächst wird in diesem Code die **vorbereitete** Eigenschaft nicht auf " **true** " festgelegt, da es sich um eine SQL Server gespeicherte Prozedur handelt, die definitionsgemäß vorkompiliert ist. Zweitens wurde die **CommandType** -Eigenschaft des **Command** -Objekts in **adCmdStoredProc** im zweiten Beispiel geändert, um ADO darüber zu informieren, dass der Befehl eine gespeicherte Prozedur war.  
  
 Schließlich muss im zweiten Beispiel beim Festlegen des Werts der-Parameter auf den-Parameter verwiesen werden, da Sie den Namen des Parameters zur Entwurfszeit möglicherweise nicht kennen. Wenn Sie den Namen des Parameters kennen, können Sie die neue [namedParameters](../../../ado/reference/ado-api/namedparameters-property-ado.md) -Eigenschaft des **Befehls** Objekts auf "true" festlegen und sich auf den Namen der Eigenschaft beziehen. Sie Fragen sich vielleicht, warum die Position des ersten Parameters, der in der gespeicherten Prozedur ( @CustomerID ) erwähnt wird, 1 anstelle von 0 ( `objCmd(1) = "ALFKI"` ) ist. Der Grund hierfür ist, dass der Parameter 0 einen Rückgabewert aus der gespeicherten Prozedur SQL Server enthält.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Knowledge Base-Artikel 117500](https://go.microsoft.com/fwlink/?LinkId=117500)
