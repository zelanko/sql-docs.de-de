---
title: Mit dem Namen Befehle | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- named commands [ADO]
- commands [ADO]
ms.assetid: 5a0ec8f9-5ba3-4f9f-b80d-2073aa049586
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9d38f80dcc44afa0d399885559b10f20027f906
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670596"
---
# <a name="named-commands"></a>Benannte Befehle
[Erstellen und Ausführen eines einfachen Befehls](../../../ado/guide/data/creating-and-executing-a-simple-command.md) zeigt eine Möglichkeit, einen Befehl auszuführen. Es ist eine weitere Möglichkeit: Sie können es einen benannten Befehl, und rufen Sie dann diese benannte Befehl, die direkt auf die **Verbindung** Objekt (zugewiesen der **ActiveConnection** Eigenschaft der **Befehl** Objekt). Benennen einen Befehl bedeutet, dass ein Name zugewiesen der **Namen** Eigenschaft eine **Befehl** Objekt. Beispiel:  
  
```  
objCmd.Name = "GetCustomers"  
objCmd.ActiveConnection = objConn  
objConn.GetCustomers objRs  
```  
  
 Der benannte Befehl fungiert als handele es sich um eine "benutzerdefinierte Methode" auf die **Verbindung** Objekt. Das Ergebnis des Befehls wird als Out-Parameter dieser Methode"benutzerdefinierten" zurückgegeben.  
  
 Das folgende Beispiel veranschaulicht dieses Feature.  
  
```  
'BeginNamedCmd  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim objCmd As New ADODB.Command  
    Dim objRs As New ADODB.Recordset  
  
    ' Connect to the data source.  
    Set objConn = GetNewConnection  
  
    objCmd.CommandText = "SELECT CustomerID, CompanyName FROM Customers"  
    objCmd.CommandType = adCmdText  
  
    'Name the command.  
    objCmd.Name = "GetCustomers"  
  
    objCmd.ActiveConnection = objConn  
  
    ' Execute using Command.Name from the Connection.  
    objConn.GetCustomers objRs  
  
    ' Display.  
    Do While Not objRs.EOF  
        Debug.Print objRs(0) & vbTab & objRs(1)  
        objRs.MoveNext  
    Loop  
  
    'clean up  
    objRs.Close  
    objConn.Close  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
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
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
'EndNamedCmd  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
