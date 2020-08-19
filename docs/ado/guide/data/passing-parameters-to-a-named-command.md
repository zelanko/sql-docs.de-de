---
description: Übergeben von Parametern an einen benannten Befehl
title: Übergeben von Parametern an einen benannten Befehl | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- named commands [ADO]
- commands [ADO], passing parameters to a named command
ms.assetid: 36e0cdbe-7f50-40f5-af0d-700f5d8dc75a
author: rothja
ms.author: jroth
ms.openlocfilehash: fa6ac56c3bb3e632ace019a2c8b2a97c96262421
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453072"
---
# <a name="passing-parameters-to-a-named-command"></a>Übergeben von Parametern an einen benannten Befehl
Ebenso wie das Ergebnis des Befehls als *out* -Variable des benannten Befehls ausgegeben wird, können Parameter für einen parametrisierten Befehl als *in* Variablen an den benannten Befehl übermittelt werden.  
  
 Im folgenden Codebeispiel wird versucht, alle Bestellungen des Kunden abzurufen, dessen **CustomerID** "alkfi" aus der Northwind-Datenbank ist. Der Wert von **CustomerID** wird zu dem Zeitpunkt bereitgestellt, zu dem der benannte Befehl aufgerufen wird.  
  
```  
Const DS = "MySqlServer"  
Const DB = "Northwind"  
Const DP = "SQLOLEDB"  
  
Dim objConn As New ADODB.Connection  
Dim objRs As New ADODB.Recordset  
Dim objComm As New ADODB.Command  
  
CommandText = "SELECT OrderID, OrderDate, " & _  
                     "RequiredDate, ShippedDate " & _  
                     "FROM Orders " & _  
                     "WHERE CustomerID = ? " & _  
                     "ORDER BY OrderID"  
  
ConnectionString = "Provider=" & DP & _  
                   ";Data Source=" & DS & _  
                   ";Initial Catalog=" & DB & _  
                   ";Integrated Security=SSPI;"  
  
' Connect to the data source.  
objConn.Open ConnectionString  
  
' Set a named command.  
objComm.CommandText = CommandText  
objComm.CommandType = adCmdText  
objComm.Name = "GetOrdersOf"  
Set objComm.ActiveConnection = objConn  
  
' Call the named command, passing a CustomerID value  
' as the input parameter.   
'    "ALFKI" is the required input parameter,  
'    objRs is the resultant output variable.  
objConn.GetOrdersOf "ALKFI", objRs  
  
' Display the result.  
Debug.Print "All orders by ALFKI:"  
Do While Not objRs.EOF  
    Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                objRs(2) & vbTab & objRs(3)  
    objRs.MoveNext  
Loop  
  
' Clean up.  
objRs.Close  
objConn.Close  
Set objRs = Nothing  
Set objConn = Nothing  
Set objComm = Nothing  
```  
  
 Beachten Sie, dass alle Eingabeparameter allen Ausgabevariablen vorangestellt werden müssen und die Datentypen der Parameter übereinstimmen müssen oder in die entsprechenden Felder konvertiert werden können. Die folgende Anweisung:  
  
```  
objConn.GetOrdersOf 12345, objRs  
```  
  
 -führt zu einem Fehler von nicht übereinstimmenden Datentypen, da der erforderliche Eingabeparameter von einem **Zeichen** Folgentyp und nicht vom **ganzzahligen** Typ ist.  
  
 Der folgende-Befehl:  
  
```  
objConn.GetOrdersOf "12345", objRs  
```  
  
 -ist gültig, führt jedoch zu einem leeren Resultset, da in der Datenbank keine Datensätze vorhanden sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
