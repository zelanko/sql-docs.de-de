---
title: ADO-Fehler | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO]
ms.assetid: 9bb84114-a1df-4122-a1b8-ad98dcd85cc3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4fadb19aac4700738f4c6ec43449b3de7d4a4a18
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47776368"
---
# <a name="ado-run-time-errors"></a>ADO-Laufzeitfehler
ADO-Fehler werden mit dem Programm als Laufzeitfehler gemeldet. Sie können den Mechanismus zum Abfangen von Fehlern Ihre bevorzugte Programmiersprache verwenden, abfangen und behandeln. In Visual Basic verwenden, z. B. die **On Error** Anweisung. In Visual C++ hängt von der Methode, die Sie verwenden, um die ADO-Bibliotheken zugreifen. Mit #import, verwenden eine **Try / Catch** Block. Andernfalls müssen die C++-Programmierer explizit das Fehlerobjekt, das durch den Aufruf abrufen **GetErrorInfo**. Die folgende Visual Basic-Sub-Prozedur veranschaulicht einen ADO-Fehler abfangen:

```
' BeginErrorHandlingVB01
Private Sub Form_Load()
' Turn on error handling
On Error GoTo FormLoadError

'Open the database and the recordset for processing.
'
Dim strCnn As String
strCnn = "Provider=sqloledb;" & _
    "Data Source=a-iresmi2000;" & _
    "Initial Catalog=Northwind;Integrated Security=SSPI"

' cnn is a Public Connection Object because
' it was defined WithEvents
Set cnn = New ADODB.Connection
cnn.Open strCnn

' The next line of code intentionally causes
' an error by trying to open a connection
' that has already been opened.
cnn.Open strCnn

' rst is a Public Recordset because it
' was defined WithEvents
Set rst = New ADODB.Recordset
rst.Open "Customers", cnn

Exit Sub

' Error handler
FormLoadError:
    Dim strErr As String
    Select Case Err
        Case adErrObjectOpen
            strErr = "Error #" & Err.Number & ": " & Err.Description & vbCrLf
            strErr = strErr & "Error reported by: " & Err.Source & vbCrLf
            strErr = strErr & "Help File: " & Err.HelpFile & vbCrLf
            strErr = strErr & "Topic ID: " & Err.HelpContext
            MsgBox strErr
            Debug.Print strErr
            Err.Clear
            Resume Next
        ' If some other error occurs that
        ' has nothing to do with ADO, show
        ' the number and description and exit.
        Case Else
            strErr = "Error #" & Err.Number & ": " & Err.Description & vbCrLf
            MsgBox strErr
            Debug.Print strErr
            Unload Me
    End Select
End Sub
' EndErrorHandlingVB01
```

 Dies **Form_Load** Ereignisprozedur erstellt absichtlich einen Fehler mit dem Versuch, öffnen Sie die gleichen **Verbindung** zweimal Objekt. Beim zweiten Mal die **öffnen** Methode aufgerufen wird, wird der Fehlerhandler ist aktiviert. In diesem Fall wird der Fehler des Typs ist **AdErrObjectOpen**, sodass der Fehlerhandler die folgende Meldung angezeigt, vor dem Fortsetzen der Ausführung des Programms:

```
Error #3705: Operation is not allowed when the object is open.
Error reported by: ADODB.Connection
Help File: E:\WINNT\HELP\ADO260.CHM Topic ID: 1003705
```

 Die Fehlermeldung enthält Informationen, die von der Visual Basic bereitgestellten **Err** Objekt, mit Ausnahme der **LastDLLError** -Wert, der hier nicht anwendbar ist. Die Fehlernummer teilt Ihnen mit, welche Fehler aufgetreten ist. Die Beschreibung ist hilfreich in Fällen, in denen Sie nicht, die den Fehler zu behandeln möchten. Sie können es einfach an den Benutzer übergeben. Empfiehlt, sich jedoch in der Regel verwendet für Ihre Anwendung angepasste werden können können nicht alle Fehler erwartungsgemäß; die Beschreibung gibt einen Hinweis, welche Fehler aufgetreten sind. Im Beispielcode wird der Fehler gemeldet wurde, durch die **Verbindung** Objekt. Sie sehen, Typ oder hier Programm-ID des Objekts, nicht auf einen Variablennamen ein.

> [!NOTE]
>  Die Visual Basic **Err** Objekt enthält nur Informationen zu der zuletzt aufgetretene Fehler. Das ADO **Fehler** Auflistung von der **Verbindung** Objekt enthält ein **Fehler** Objekt für jeden Fehler, die von den neuesten ADO-Vorgang ausgelöst. Verwenden der **Fehler** Sammlung anstelle der **Err** Objekt, das mehrere Fehler zu behandeln. Weitere Informationen zu den **Fehler** Sammlung finden Sie unter [Anbieterfehler](../../../ado/guide/data/provider-errors.md). Allerdings, wenn keine gültige **Verbindung** -Objekt, das **Err** Objekt ist die einzige Quelle für Informationen zur ADO-Fehler.

 Welche Arten von Vorgängen sind wahrscheinlich dazu führen, dass bei der ADO-Fehler? Häufige ADO-Fehler können z. B. ein Objekt öffnet umfassen eine **Verbindung** oder **Recordset**, es wird versucht, Daten zu aktualisieren oder das Aufrufen einer Methode oder Eigenschaft, die von Ihrem Anbieter nicht unterstützt wird.

 OLE DB-Fehler übergeben werden können, an Ihrer Anwendung zur Laufzeit Fehler in der **Fehler** Auflistung.

 Das folgende Thema enthält weitere Informationen zum ADO-Fehler.

-   [ADO Error Reference (ADO-Fehlerreferenz)](../../../ado/guide/data/ado-error-reference.md)
