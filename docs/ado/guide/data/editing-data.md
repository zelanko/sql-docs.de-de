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
manager: jroth
ms.openlocfilehash: 998fd4ee425f1a4356bdc675b53b23247d89c3f8
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700779"
---
# <a name="editing-data"></a>Bearbeiten von Daten
Wir haben erläutert wie ADO verwenden, um eine Verbindung mit einer Datenquelle herstellen, einen Befehl ausführen, erhalten die Ergebnisse einem **Recordset** Objekt aus, und navigieren Sie in der **Recordset**. Dieser Abschnitt konzentriert sich auf den nächsten grundlegende ADO-Vorgang: Bearbeiten von Daten.  
  
 In diesem Abschnitt verwenden Sie das Beispiel weiterhin **Recordset** in eingeführte [Untersuchen von Daten](../../../ado/guide/data/examining-data.md), mit einer wichtigen Änderung. Der folgende Code dient zum Öffnen der **Recordset**:  
  
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
  
 Der wichtige Änderungen am Code umfasst das der **CursorLocation** Eigenschaft der **Verbindung** Objekt gleich **AdUseClient** in die  *GetNewConnection* -Funktion (Siehe das nächste Beispiel), die die Verwendung eines Clientcursors angibt. Weitere Informationen zu den Unterschieden zwischen clientseitigen und serverseitigen Cursor finden Sie unter [Grundlegendes zu Cursors und Sperren](../../../ado/guide/data/understanding-cursors-and-locks.md).  
  
 Die **CursorLocation** Eigenschaft **AdUseClient** Einstellung verschiebt die Position des Cursors aus der Datenquelle (in diesem Fall die SQL-Server) auf den Speicherort der Clientcode (die desktop-Arbeitsstation). Diese Einstellung erzwingt ADO aufruft, die Client-Cursor-Engine für OLE DB auf dem Client zum Erstellen und verwalten den Cursor.  
  
 Außerdem haben Sie gesehen, die die **LockType** Parameter der **öffnen** Methode geändert werden, um **AdLockBatchOptimistic**. Den Cursor wird im Modus "Batch" geöffnet. (Der Anbieter speichert mehrere Änderungen, und sie in der zugrunde liegenden Datenquelle schreibt, nur bei Aufruf der **UpdateBatch** Methode.) Änderungen wurden an der **Recordset** wird nicht aktualisiert werden, in der Datenbank, bis der **UpdateBatch** Methode wird aufgerufen.  
  
 Schließlich verwendet der Code in diesem Abschnitt eine geänderte Version der GetNewConnection-Funktion. Diese Version der Funktion gibt nun einen clientseitigen Cursor zurück. Die Funktion sieht folgendermaßen aus:  
  
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
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Bearbeiten vorhandener Einträge](../../../ado/guide/data/editing-existing-records.md)  
  
-   [Hinzufügen von Datensätzen](../../../ado/guide/data/adding-records.md)  
  
-   [Bestimmen, was unterstützt wird](../../../ado/guide/data/determining-what-is-supported.md)  
  
-   [Deleting Records Using the Delete Method (Löschen von Datensätzen mit der Delete-Methode)](../../../ado/guide/data/deleting-records-using-the-delete-method.md)  
  
-   [Alternativen: Mithilfe von SQL­Anweisungen](../../../ado/guide/data/alternatives-using-sql-statements.md)
