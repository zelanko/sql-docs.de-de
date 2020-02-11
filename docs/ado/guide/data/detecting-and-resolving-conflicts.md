---
title: Erkennen und Auflösen von Konflikten | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925563"
---
# <a name="detecting-and-resolving-conflicts"></a>Erkennen und Lösen von Konflikten
Wenn Sie mit dem Recordset im unmittelbaren Modus arbeiten, ist die Wahrscheinlichkeit, dass Parallelitäts Probleme auftreten, weitaus geringer. Wenn Ihre Anwendung dagegen eine Batch Modus-Aktualisierung verwendet, kann es sinnvoll sein, dass ein Benutzer einen Datensatz ändert, bevor Änderungen, die von einem anderen Benutzer bearbeitet wurden, der denselben Datensatz bearbeitet hat, gespeichert werden. In einem solchen Fall möchten Sie, dass Ihre Anwendung den Konflikt ordnungsgemäß behandeln kann. Möglicherweise möchten Sie, dass die letzte Person ein Update an den Server "WINS" sendet. Oder Sie möchten dem aktuellen Benutzer gestatten, sich zu entscheiden, welches Update Vorrang haben sollte, indem er eine Auswahl zwischen den beiden in Konflikt stehenden Werten bietet.  
  
 Der Fall ist, dass ADO die Eigenschaften UnderlyingValue und OriginalValue des Field-Objekts bereitstellt, um diese Arten von Konflikten zu behandeln. Verwenden Sie diese Eigenschaften in Kombination mit der Resync-Methode und der Filter-Eigenschaft des Recordsets.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ADO während eines Batch Updates einen Konflikt feststellt, wird der Fehler Auflistung eine Warnung hinzugefügt. Daher sollten Sie immer nach Fehlern suchen, nachdem Sie BatchUpdate aufgerufen haben. Wenn Sie diese gefunden haben, testen Sie die Annahme, dass ein Konflikt aufgetreten ist. Der erste Schritt besteht darin, die Filter-Eigenschaft für das Recordset auf "adFilterConflictingRecords" festzulegen. Dadurch wird die Ansicht Ihres Recordsets auf die Datensätze beschränkt, die in Konflikt stehen. Wenn die RecordCount-Eigenschaft nach diesem Schritt gleich 0 ist, wissen Sie, dass der Fehler von einem anderen als einem Konflikt ausgelöst wurde.  
  
 Wenn Sie BatchUpdate aufzurufen, werden von ADO und der Anbieter SQL-Anweisungen zum Ausführen von Aktualisierungen für die Datenquelle erstellt. Beachten Sie, dass bestimmte Datenquellen Einschränkungen aufweisen, welche Spaltentypen in einer WHERE-Klausel verwendet werden können.  
  
 Im nächsten Schritt wird die Resync-Methode für das Recordset aufgerufen, wobei das affectrecords-Argument auf adAffectGroup und das resyncvalues-Argument auf adresyncunderlyingvalues festgelegt ist. Die Resync-Methode aktualisiert die Daten im aktuellen Recordset-Objekt aus der zugrunde liegenden Datenbank. Mithilfe von adAffectGroup stellen Sie sicher, dass nur die Datensätze, die mit der aktuellen Filtereinstellung sichtbar sind, d. h. nur die in Konflikt stehenden Datensätze, mit der Datenbank neu synchronisiert werden. Dies kann einen erheblichen Leistungsunterschied bewirken, wenn Sie mit einem großen Recordset arbeiten. Wenn Sie das resyncvalues-Argument auf adresyncunderlyingvalues festlegen, wenn Sie RESYNC aufrufen, stellen Sie sicher, dass die UnderlyingValue-Eigenschaft den (Konflikt verursachenden) Wert aus der Datenbank enthält, dass die Value-Eigenschaft den vom Benutzer eingegebenen Wert beibehält. die OriginalValue-Eigenschaft enthält den ursprünglichen Wert für das Feld (der Wert, der vor dem letzten erfolgreichen Update Batch-Befehl enthalten war). Anschließend können Sie diese Werte verwenden, um den Konflikt Programm gesteuert aufzulösen, oder den Benutzer dazu auffordern, den zu verwendenden Wert auszuwählen.  
  
 Dieses Verfahren wird im folgenden Codebeispiel gezeigt. Das Beispiel erstellt künstlich einen Konflikt mithilfe eines separaten Recordsets, um einen Wert in der zugrunde liegenden Tabelle zu ändern, bevor UpdateBatch aufgerufen wird.  
  
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
  
 Sie können die Eigenschaft Status des aktuellen Datensatzes oder eines bestimmten Felds verwenden, um zu bestimmen, welche Art von Konflikt aufgetreten ist.  
  
 Ausführliche Informationen zur Fehlerbehandlung finden Sie unter [Fehlerbehandlung](../../../ado/guide/data/error-handling.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Batchmodus](../../../ado/guide/data/batch-mode.md)
