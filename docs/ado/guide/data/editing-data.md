---
title: Bearbeiten von Daten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, editing data
- AdUseClient [ADO]
- editing data [ADO]
ms.assetid: ef514f85-c446-4f05-824e-c9313b2ffae1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8e8fd90849b8e046a7f4fe5d158d4594e612c91f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925493"
---
# <a name="editing-data"></a>Bearbeiten von Daten
Wir haben erläutert, wie ADO verwendet, um eine Verbindung mit einer Datenquelle herzustellen, einen Befehl auszuführen, die Ergebnisse in einem **Recordset** -Objekt zu erhalten und innerhalb des **Recordsets**zu navigieren. Dieser Abschnitt konzentriert sich auf den nächsten grundlegenden ADO-Vorgang: Bearbeiten von Daten.  
  
 In diesem Abschnitt wird weiterhin das in unter [Suchen von Daten](../../../ado/guide/data/examining-data.md)eingeführte **beispielrecordset** verwendet, mit einer wichtigen Änderung. Der folgende Code wird verwendet, um das **Recordset**zu öffnen:  
  
```  
'BeginEditIntro  
    Dim strSQL As String  
    Dim objRs1 As ADODB.Recordset  
  
    strSQL = "SELECT * FROM Shippers"  
  
    Set objRs1 = New ADODB.Recordset  
  
    objRs1.Open strSQL, GetNewConnection, adOpenStatic, _  
                adLockBatchOptimistic, adCmdText  
  
    ' Disconnect the Recordset from the Connection object.  
    Set objRs1.ActiveConnection = Nothing  
'EndEditIntro  
```  
  
 Die wichtige Änderung am Code umfasst das Festlegen der **CursorLocation** -Eigenschaft des **Connection** -Objekts auf **adUseClient** in der *getNewConnection* -Funktion (siehe das nächste Beispiel), das die Verwendung eines Client Cursors angibt. Weitere Informationen zu den Unterschieden zwischen Client seitigen und serverseitigen Cursorn finden Sie Untergrund Legendes zu [Cursorn und Sperren](../../../ado/guide/data/understanding-cursors-and-locks.md).  
  
 Die **adUseClient** -Einstellung der **CursorLocation** -Eigenschaft verschiebt die Position des Cursors aus der Datenquelle (in diesem Fall die SQL Server) an den Speicherort des Client Codes (die Desktop Arbeitsstation). Diese Einstellung erzwingt ADO, das Client Cursor Modul für OLE DB auf dem Client aufzurufen, um den Cursor zu erstellen und zu verwalten.  
  
 Sie haben möglicherweise auch bemerkt, dass der **LockType** -Parameter der **Open** -Methode in **adlockbatchoptimigeändert**wurde. Dadurch wird der Cursor im Batch Modus geöffnet. (Der Anbieter speichert mehrere Änderungen zwischen und schreibt Sie nur dann in die zugrunde liegende Datenquelle, wenn Sie die **UpdateBatch** -Methode aufrufen.) Änderungen, die am **Recordset** vorgenommen wurden, werden erst in der Datenbank aktualisiert, wenn die **UpdateBatch** -Methode aufgerufen wird.  
  
 Schließlich verwendet der Code in diesem Abschnitt eine geänderte Version der getNewConnection-Funktion. Diese Version der Funktion gibt jetzt einen Client seitigen Cursor zurück. Die-Funktion sieht wie folgt aus:  
  
```  
'BeginNewConnection  
Public Function GetNewConnection() As ADODB.Connection  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim strConnStr As String  
  
    strConnStr = "Provider='SQLOLEDB';Initial Catalog='Northwind';" & _  
                 "Data Source='MySqlServer';Integrated Security='SSPI';"  
  
    objConn.ConnectionString = strConnStr  
    objConn.CursorLocation = adUseClient  
    objConn.Open  
  
    Set GetNewConnection = objConn  
  
    Exit Function  
  
ErrHandler:  
    Set objConn = Nothing  
    Set GetNewConnection = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Function  
'EndNewConnection  
```  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Bearbeiten vorhandener Datensätze](../../../ado/guide/data/editing-existing-records.md)  
  
-   [Hinzufügen von Datensätzen](../../../ado/guide/data/adding-records.md)  
  
-   [Bestimmen der unterstützten Vorgänge](../../../ado/guide/data/determining-what-is-supported.md)  
  
-   [Löschen von Datensätzen mit der Delete-Methode](../../../ado/guide/data/deleting-records-using-the-delete-method.md)  
  
-   [Alternativen: Verwenden von SQL-Anweisungen](../../../ado/guide/data/alternatives-using-sql-statements.md)
