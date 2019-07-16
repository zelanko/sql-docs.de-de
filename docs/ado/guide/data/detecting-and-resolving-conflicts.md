---
title: Erkennen und Lösen von Konflikten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- conflicts [ADO], detecting and resolving
- ADO, detecting and resolving conflicts
ms.assetid: b28fdd26-c1a4-40ce-a700-2b0c9d201514
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bce9917f144e8c63160f571a986263d8d7e97b21
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925563"
---
# <a name="detecting-and-resolving-conflicts"></a>Erkennen und Lösen von Konflikten
Wenn Sie das Recordset im unmittelbaren Modus arbeiten, ist viel weniger wahrscheinlich für Parallelitätsprobleme auftreten. Andererseits, wenn Ihre Anwendung Mode BatchUpdates verwendet, liegt möglicherweise eine gute chance, dass ein Benutzer ändert einen Datensatz, bevor von einem anderen Benutzer, die den gleichen Datensatz bearbeiten vorgenommenen Änderungen gespeichert werden. In diesem Fall sollten Sie Ihre Anwendung den Konflikt ordnungsgemäß zu verarbeiten. Es kann Ihr Wunsch sein, die letzte Person, die ein Update an den Server senden "gewinnt". Oder Sie können, damit der letzten Benutzer, um zu entscheiden, welche Updates Vorrang haben soll, stellen Sie ihm eine Wahl zwischen den beiden in Konflikt stehenden Werten.  
  
 In jedem Fall stellt ADO die UnderlyingValue und OriginalValue-Eigenschaften, von der Field-Objekt, um diese Art von Konflikten zu behandeln. Verwenden Sie diese Eigenschaften in Kombination mit dem Resync-Methode und die Filter-Eigenschaft des Recordset-Objekts.  
  
## <a name="remarks"></a>Hinweise  
 Bei ADO einen Konflikt während der Batchaktualisierung auftritt, wird eine Warnung der Fehlersammlung hinzugefügt. Aus diesem Grund sollten Sie immer auf Fehler überprüfen, sobald Sie BatchUpdate aufrufen und wenn Sie gefunden werden mit dem Testen beginnen der Annahme, dass Sie einen Konflikt aufgetreten ist. Der erste Schritt ist, legen Sie die Filter-Eigenschaft auf den Gleichheitsoperator Recordsets vorliegt. Dadurch wird die Sicht auf das Recordset, nur die Datensätze, die miteinander in Konflikt stehen. Wenn die RecordCount-Eigenschaft gleich 0 (null), nach diesem Schritt ist, wissen Sie, dass der Fehler durch etwas anderes als ein Konflikt ausgelöst wurde.  
  
 Wenn Sie BatchUpdate aufrufen, ADO und der Anbieter SQL-Anweisungen zum Durchführen von Updates in der Datenquelle generieren. Denken Sie daran, dass bestimmte Datenquellen Einschränkungen gelten für die Datentypen der Spalten in einer WHERE-Klausel verwendet werden können.  
  
 Rufen Sie als Nächstes die Resync-Methode auf das Recordset mit dem AffectRecords-Argument, das gleich AdAffectGroup und das ResyncValues-Argument, das gleich AdResyncUnderlyingValues festgelegt. Die Resync-Methode aktualisiert die Daten in das aktuelle Recordset-Objekt, aus der zugrunde liegenden Datenbank. Verwenden Sie AdAffectGroup, stellen Sie sicher, dass nur die Datensätze, die mit dem aktuellen Filter festlegen, d. h. nur die in Konflikt stehende Datensätze angezeigt, mit der Datenbank synchronisiert werden. Dies kann einen bedeutender Leistungsunterschied stellen, wenn Sie ein umfangreiches Recordset zu tun haben. Durch das ResyncValues-Argument auf AdResyncUnderlyingValues festlegen, bei der Neusynchronisierung aufrufen, stellen Sie sicher, dass die UnderlyingValue-Eigenschaft den Wert aus der Datenbank (in Konflikt stehende) enthält, die Value-Eigenschaft den vom Benutzer eingegebenen Wert beibehält und dass die OriginalValue-Eigenschaft enthält den ursprünglichen Wert des Felds (der Wert, der vor der letzten erfolgreiche UpdateBatch-Aufruf erfolgt ist). Sie können diese Werte dann verwenden, zum Lösen des Konflikts programmgesteuert oder muss der Benutzer den Wert auswählen, der verwendet werden.  
  
 Diese Technik wird im folgenden Codebeispiel wird angezeigt. Das Beispiel erstellt künstlich einen Konflikt mit einem getrennten Recordset so ändern Sie einen Wert in der zugrunde liegenden Tabelle, bevor UpdateBatch aufgerufen wird.  
  
```  
'BeginConflicts  
    strConn = "Provider=SQLOLEDB;Initial Catalog=Northwind;" & _  
              "Data Source=MySQLServer;Integrated Security=SSPI;"  
  
    strSQL = "SELECT * FROM Shippers WHERE ShipperID = 2"  
  
    'Open Rs and change a value  
    Set objRs1 = New ADODB.Recordset  
    Set objRs2 = New ADODB.Recordset  
    objRs1.CursorLocation = adUseClient  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Introduce a conflict at the db...  
    objRs2.Open strSQL, strConn, adOpenKeyset, adLockOptimistic, adCmdText  
    objRs2("Phone") = "(999) 555-9999"  
    objRs2.Update  
    objRs2.Close  
    Set objRs2 = Nothing  
  
    On Error Resume Next  
    objRs1.UpdateBatch  
  
    If objRs1.ActiveConnection.Errors.Count <> 0 Then  
        Dim intConflicts As Integer  
  
        intConflicts = 0  
  
        objRs1.Filter = adFilterConflictingRecords  
  
        intConflicts = objRs1.RecordCount  
  
        'Resync so we can see the UnderlyingValue and offer user a choice.  
        'This sample only displays all three values and resets to original.  
        objRs1.Resync adAffectGroup, adResyncUnderlyingValues  
  
        If intConflicts > 0 Then  
            strMsg = "A conflict occurred with updates for " & intConflicts & _  
                     " record(s)." & vbCrLf & "The values will be restored" & _  
                     " to their original values." & vbCrLf & vbCrLf  
  
            objRs1.MoveFirst  
            While Not objRs1.EOF  
              strMsg = strMsg & "SHIPPER = " & objRs1("CompanyName") & vbCrLf  
              strMsg = strMsg & "Value = " & objRs1("Phone").Value & vbCrLf  
              strMsg = strMsg & "UnderlyingValue = " & _  
                                 objRs1("Phone").UnderlyingValue & vbCrLf  
              strMsg = strMsg & "OriginalValue = " & _  
                                 objRs1("Phone").OriginalValue & vbCrLf  
              strMsg = strMsg & vbCrLf & "Original value has been restored."  
  
              MsgBox strMsg, vbOKOnly, _  
                    "Conflict " & objRs1.AbsolutePosition & _  
                    " of " & intConflicts  
  
              objRs1("Phone").Value = objRs1("Phone").OriginalValue  
              objRs1.MoveNext  
            Wend  
  
            objRs1.UpdateBatch adAffectGroup  
        Else  
            'Other error occurred. Minimal handling in this example.  
             strMsg = "Errors occurred during the update. " & _  
                        objRs1.ActiveConnection.Errors(0).Number & " " & _  
                        objRs1.ActiveConnection.Errors(0).Description  
        End If  
  
        On Error GoTo 0  
    End If  
  
    objRs1.MoveFirst  
    objRs1.Close  
    Set objRs1 = Nothing  
'EndConflicts  
```  
  
 Sie können die Status-Eigenschaft des aktuellen Datensatzes oder von einem bestimmten Feld verwenden, um zu bestimmen, welche Art von ein Konflikt aufgetreten ist.  
  
 Ausführliche Informationen zur Fehlerbehandlung finden Sie unter [Fehlerbehandlung](../../../ado/guide/data/error-handling.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Batchmodus](../../../ado/guide/data/batch-mode.md)
