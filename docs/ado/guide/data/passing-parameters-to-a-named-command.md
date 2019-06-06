---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6863a14a467e1d884d43b982451ec5807820486b
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66701850"
---
# <a name="passing-parameters-to-a-named-command"></a>Übergeben von Parametern an einen benannten Befehl
Genauso wie das Ergebnis des Befehls als, sich übergeben wird ein *out* Variablen des benannten Befehls, der Parameter wurde für ein parametrisierter Befehl kann als übergebenen *in* Variablen auf den benannten Befehl.  
  
 Im folgenden Codebeispiel wird versucht, alle Aufträge Abrufen vom Kunden aufgegebene, deren **"CustomerID"** "ALKFI" aus der Northwind-Datenbank ist. Der Wert des **"CustomerID"** angegeben wird, auf die Zeit, wenn der benannte Befehl aufgerufen wird.  
  
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
  
 Beachten Sie, dass alle Eingabeparameter müssen alle Output-Variable vor, und die Datentypen der Parameter übereinstimmen oder konvertiert werden können, mit denen die entsprechenden Felder ein. Die folgende Anweisung:  
  
```  
objConn.GetOrdersOf 12345, objRs  
```  
  
 -führt zu einem Fehler nicht übereinstimmende Datentypen, da die erforderliche Eingabeparameter ist eine **Zeichenfolge** Typ nicht von einer **ganze Zahl** Typ.  
  
 Die folgenden Aufruf:  
  
```  
objConn.GetOrdersOf "12345", objRs  
```  
  
 -ist gültig, aber ergibt ein leeres Resultset, weil keine solche Datensätze in der Datenbank vorhanden sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
