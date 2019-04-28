---
title: Anbieterfehler | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors collection [ADO]
- provider errors [ADO]
- event-related errors [ADO]
- errors [ADO], provider
- Error object [ADO], provider errors
ms.assetid: cc7d6ff9-2034-45c6-9d61-90b177010054
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18370885fedb106f02c9b404ea946680aa048b8b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62911369"
---
# <a name="provider-errors"></a>Anbieterfehler
Tritt ein Fehler auf, wird ein Fehler während der Ausführung von-2147467259 zurückgegeben. Wenn Sie diesen Fehler erhalten, überprüfen Sie die **Fehler** Auflistung der aktiven **Verbindung** -Objekt, das enthält mindestens ein Fehler, die beschreiben, was aufgetreten ist.  
  
## <a name="the-ado-errors-collection"></a>Die Auflistung der ADO-Fehler  
 Da ein ADO-Vorgang mehrere anbieterfehlern führen kann, macht ADO eine Auflistung von Fehlerobjekten über die **Verbindung** Objekt. Diese Sammlung enthält keine Objekte aus, wenn ein Vorgang wird erfolgreich abgeschlossen, und ein oder mehrere enthält **Fehler** Objekte an, wenn Fehler aufgetreten, und der Anbieter wird mindestens ein Fehler ausgelöst. Überprüfen Sie jeden Error-Objekt, um die genaue Ursache des Fehlers zu bestimmen.  
  
 Sobald Sie fertig sind, behandeln alle Fehler, die aufgetreten sind, können Sie die Sammlung löschen, durch Aufrufen der **löschen** Methode. Es ist besonders wichtig, um explizit löschen, die **Fehler** Auflistung vor dem Aufruf der **Resync**, **UpdateBatch**, oder **CancelBatch**Methode für eine **Recordset** Objekt der **öffnen** Methode für eine **Verbindung** Objekt, oder legen Sie die **Filter** Eigenschaft eine **Recordset** Objekt. Wenn Sie die Auflistung explizit deaktivieren, werden Sie sicher, dass alle **Fehler** Objekte in der Auflistung werden nicht von einem vorherigen Vorgang übrig.  
  
 Einige Vorgänge können Warnungen, die zusätzlich zu Fehlern generieren. Warnungen werden auch von dargestellt **Fehler** Objekte in der **Fehler** Auflistung. Wenn ein Anbieter eine Warnung auf die Auflistung hinzufügt, wird er kein Laufzeitfehler generiert. Überprüfen Sie die **Anzahl** Eigenschaft der **Fehler** -Auflistung, um zu bestimmen, ob eine Warnung von einem bestimmten Vorgang erstellt wurde. Sofern die Anzahl die oder größer ist, eine **Fehler** Objekt der Auflistung hinzugefügt wurde. Sobald Sie, dass festgestellt haben die **Fehler** Auflistung enthält, Fehler oder Warnungen können Sie die Auflistung durchlaufen und Abrufen von Informationen zu den einzelnen **Fehler** -Objekts an. Im folgende kurze Visual Basic-Beispiel veranschaulicht dies:  
  
```  
' BeginErrorHandlingVB02  
Private Function DeleteCustomer(ByVal CompanyName As String) As Long  
    On Error GoTo DeleteCustomerError  
  
    rst.Find "CompanyName='" & CompanyName & "'"  
DeleteCustomerError:  
Dim objError As ADODB.Error  
Dim strError As String  
  
    If cnn.Errors.Count > 0 Then  
        For Each objError In cnn.Errors  
            strError = strError & "Error #" & objError.Number & _  
                " " & objError.Description & vbCrLf & _  
                "NativeError: " & objError.NativeError & vbCrLf & _  
                "SQLState: " & objError.SQLState & vbCrLf & _  
                "Reported by: " & objError.Source & vbCrLf & _  
                "Help file: " & objError.HelpFile & vbCrLf & _  
                "Help Context ID: " & objError.HelpContext  
        Next  
        MsgBox strError  
    End If  
End Function  
' EndErrorHandlingVB02  
```  
  
 Enthält die Fehlerbehandlungsroutine ein **für jede** Schleife, die untersucht jedes Objekt in der **Fehler** Auflistung. In diesem Beispiel sammelt er eine Nachricht für die Anzeige. In einem Programm arbeiten, führen Sie einen entsprechenden Task für jeden Fehler, Code schreiben, würde z. B. das schließen alle Dateien öffnen und das Beenden des Programms in strukturierter Weise.  
  
## <a name="the-error-object"></a>Die Error-Objekt  
 Anhand einer **Fehler** -Objekt können Sie bestimmen, welcher Fehler aufgetreten ist, und noch wichtiger ist, welche Anwendung oder welches Objekt den Fehler verursacht hat. Die **Fehler** Objekt hat die folgenden Eigenschaften:  
  
|Eigenschaftenname|Description|  
|-------------------|-----------------|  
|**Beschreibung**|Eine textbeschreibung des Fehlers, der aufgetreten ist.|  
|**HelpContext, HelpFile**|Bezieht sich auf die Hilfe-Thema und in der Hilfe-Datei, die eine Beschreibung des Fehlers enthalten, die aufgetreten sind.|  
|**NativeError**|Die anbieterspezifischen-Fehlernummer.|  
|**Anzahl**|Eine lange ganze Zahl, der angibt (aufgeführt der **ErrorValueEnum**) des aufgetretenen Fehlers.|  
|**Quelle**|Gibt den Namen des Objekts oder der Anwendung, einen Fehler generiert hat.|  
|**SQLState**|Eine fünfstellige Fehlercode, den der Anbieter während des Prozesses der SQL-Anweisung zurückgibt.|  
  
 Das ADO **Fehler** -Objekt ähnelt sehr der standardmäßigen Visual Basic **Err** Objekt. Die Eigenschaften beschreiben den aufgetretenen Fehler. Zusätzlich zu der Nummer des Fehlers erhalten Sie auch zwei miteinander in Beziehung stehenden Informationen. Die **NativeError** Eigenschaft enthält die Fehlernummer für den Anbieter Sie verwenden. Im vorherigen Beispiel ist der Anbieter ist der Microsoft OLE DB-Anbieter für SQL Server, also **NativeError** enthält Fehler, die spezifisch für SQL Server. Die **SQLState** Eigenschaft verfügt über ein fünf Buchstaben-Code, der ein Fehler in einer SQL­Anweisung beschrieben wird.  
  
## <a name="event-related-errors"></a>Fehler im Zusammenhang mit Ereignis  
 Die **Fehler** Objekt wird auch verwendet werden, wenn ereignisbezogene Fehler auftreten. Sie können bestimmen, ob im Prozess ist ein Fehler, die ein ADO-Ereignis wird ausgelöst aufgetreten, indem Sie überprüfen die **Fehler** -Objekt als Ereignisparameter übergeben.  
  
 Wenn der Vorgang, der bewirkt, ein Ereignis dass erfolgreich abgeschlossen wird die *AdStatus* auf Parameter des ereignishandlers festgelegt *AdStatusOK*. Andererseits, wenn der Vorgang, der das Ereignis ausgelöst wurde nicht erfolgreich war, die *AdStatus* Parametersatz zu *AdStatusErrorsOccurred*. In diesem Fall die *pError* -Parameter enthält eine **Fehler** -Objekt, das den Fehler beschreibt.
