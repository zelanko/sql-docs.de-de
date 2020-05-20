---
title: Anbieter Fehler | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2fce89dd6df633f8cdcf78271c63336b3ecc7b05
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760996"
---
# <a name="provider-errors"></a>Anbieterfehler
Wenn ein Anbieter Fehler auftritt, wird ein Laufzeitfehler von-2147467259 zurückgegeben. Wenn Sie diesen Fehler erhalten, überprüfen Sie die **Fehler** Sammlung des aktiven **Verbindungs** Objekts, das mindestens einen Fehler enthält, der beschreibt, was aufgetreten ist.  
  
## <a name="the-ado-errors-collection"></a>Die ADO Errors-Auflistung  
 Da ein bestimmter ADO-Vorgang mehrere Anbieter Fehler verursachen kann, macht ADO eine Auflistung von Fehler Objekten über das **Verbindungs** Objekt verfügbar. Diese Sammlung enthält keine Objekte, wenn ein Vorgang erfolgreich abgeschlossen wurde und mindestens ein **Fehler** Objekt enthält, wenn ein Fehler aufgetreten ist und der Anbieter mindestens einen Fehler ausgelöst hat. Überprüfen Sie jedes Fehler Objekt, um die genaue Ursache des Fehlers zu ermitteln.  
  
 Sobald Sie alle aufgetretenen Fehler verarbeitet haben, können Sie die Sammlung löschen, indem Sie die **Clear** -Methode aufrufen. Es ist besonders wichtig, die **Fehler** Auflistung explizit zu löschen, bevor Sie die Methode **Resync**, **UpdateBatch**oder **CancelBatch** für ein **Recordset** -Objekt, **die Open** -Methode für ein **Verbindungs** Objekt oder die **Filter** -Eigenschaft für ein **Recordset** -Objekt aufrufen. Wenn Sie die Auflistung explizit löschen, können Sie sicher sein, dass alle **Fehler** Objekte in der Auflistung nicht von einem vorherigen Vorgang ausgelassen werden.  
  
 Einige Vorgänge können zusätzlich zu Fehlern Warnungen generieren. Warnungen werden auch durch **Fehler** Objekte in der **Fehler** Auflistung dargestellt. Wenn ein Anbieter der Auflistung eine Warnung hinzufügt, generiert er keinen Laufzeitfehler. Überprüfen Sie die **count** -Eigenschaft der **Errors** -Auflistung, um zu bestimmen, ob eine Warnung von einem bestimmten Vorgang erzeugt wurde. Wenn die Anzahl ein oder größer ist, wurde der Auflistung ein **Fehler** Objekt hinzugefügt. Sobald Sie festgestellt haben, dass die **Fehler** Auflistung Fehler oder Warnungen enthält, können Sie die Auflistung durchlaufen und Informationen zu jedem **Fehler** Objekt abrufen, das in der Sammlung enthalten ist. Im folgenden kurzen Visual Basic Beispiel wird Folgendes veranschaulicht:  
  
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
  
 Die Fehler Behandlungs Routine schließt eine **for each** -Schleife ein, die jedes Objekt in der **Fehler** Auflistung untersucht. In diesem Beispiel wird eine Meldung zur Anzeige gesammelt. In einem funktionierenden Programm würden Sie Code schreiben, um für jeden Fehler eine geeignete Aufgabe auszuführen, z. b. das Schließen aller geöffneten Dateien und das ordnungsgemäße Herunterfahren des Programms.  
  
## <a name="the-error-object"></a>Das Error-Objekt  
 Durch Untersuchen eines **Fehler** Objekts können Sie feststellen, welcher Fehler aufgetreten ist und was wichtiger ist, welche Anwendung oder welches Objekt den Fehler verursacht hat. Das **Error** -Objekt verfügt über die folgenden Eigenschaften:  
  
|Eigenschaftenname|Beschreibung|  
|-------------------|-----------------|  
|**Beschreibung**|Eine Textbeschreibung des Fehlers, der aufgetreten ist.|  
|**HelpContext, HelpFile**|Bezieht sich auf das Hilfethema und die Hilfedatei, die eine Beschreibung des aufgetretenen Fehlers enthalten.|  
|**NativeError**|Die anbieterspezifische Fehlernummer.|  
|**Number**|Eine lange ganze Zahl, die die Zahl (in der **errorvalueenumeration**aufgelistet) des aufgetretenen Fehlers darstellt.|  
|**Quelle**|Gibt den Namen des Objekts oder der Anwendung an, das einen Fehler generiert hat.|  
|**SQLSTATE**|Ein aus fünf Zeichen bestehende Fehlercode, der vom Anbieter während der Verarbeitung einer SQL-Anweisung zurückgegeben wird.|  
  
 Das ADO- **Fehler** Objekt ähnelt dem Standard Visual Basic **Err** -Objekt. Die Eigenschaften beschreiben den aufgetretenen Fehler. Zusätzlich zur Fehlernummer erhalten Sie auch zwei verwandte Informationen. Die **NativeError** -Eigenschaft enthält eine spezifische Fehlernummer für den von Ihnen verwendeten Anbieter. Im vorherigen Beispiel ist der Anbieter der Anbieter von Microsoft OLE DB für SQL Server. **NativeError** enthält daher spezifische Fehler für SQL Server. Die **SQLSTATE** -Eigenschaft verfügt über einen aus fünf Buchstaben bestehenden Code, der einen Fehler in einer SQL-Anweisung beschreibt.  
  
## <a name="event-related-errors"></a>Ereignisbezogene Fehler  
 Das **Error** -Objekt wird auch verwendet, wenn ereignisbezogene Fehler auftreten. Sie können bestimmen, ob ein Fehler beim Prozess aufgetreten ist, der ein ADO-Ereignis ausgelöst hat, indem Sie das als Ereignis Parameter übergebene **Fehler** Objekt überprüfen.  
  
 Wenn der Vorgang, der ein Ereignis auslöst, erfolgreich abgeschlossen wird, wird der *adStatus* -Parameter des Ereignis Handlers auf *adStatusOK*festgelegt. Wenn andererseits der Vorgang, der das Ereignis ausgelöst hat, nicht erfolgreich war, wird der Parameter *adStatus* auf *adstatuserrorsoccurrred*festgelegt. In diesem Fall enthält der *perror* -Parameter ein **Fehler** Objekt, das den Fehler beschreibt.
