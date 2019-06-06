---
title: 'ADO-Ereignisinstanziierung: Visual Basic | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
ms.assetid: dce0a2a3-326f-4aaf-a822-6c5549833afa
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 590a3c282492fd07a86eae1715ffc9b027764fac
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702414"
---
# <a name="ado-event-instantiation-visual-basic"></a>ADO-Ereignisinstanziierung: Visual Basic
Um ADO-Ereignisse in Microsoft® Visual Basic® behandeln zu können, müssen Sie deklarieren, einem auf Modulebene Variablen mithilfe der **WithEvents** Schlüsselwort. Die Variable kann nur als Teil eines Moduls Klasse deklariert werden und muss auf der Modulebene deklariert werden. Dies ist nicht so restriktiv wie es, aber scheint da Visual Basic **Formular** Objekte sind ebenfalls Klassen. Die einfachste Möglichkeit zum Behandeln von ADO-Ereignissen wird zum Deklarieren einer Variablen mit **WithEvents**. Das folgende Beispiel verarbeitet die **ConnectComplete** -Ereignis für eine **Verbindung** Objekt:  
  
```  
' BeginEventExampleVB02  
Dim WithEvents connEvent As Connection  
Attribute connEvent.VB_VarHelpID = -1  
  
Private Sub Form_Load()  
Dim strConn As String  
  
   ' Create a new object with event  
   ' handling enabled.  
   strConn = "Provider=sqloledb;" & _  
      "Data Source=MyServer;" & _  
      "Initial Catalog=Northwind;" & _  
      "Integrated Security=SSPI;"  
   Set connEvent = New ADODB.Connection  
   connEvent.Open strConn  
End Sub  
  
Private Sub connEvent_ConnectComplete(ByVal pError As ADODB.Error, _  
    adStatus As ADODB.EventStatusEnum, _  
    ByVal pConnection As ADODB.Connection)  
Dim strMsg As String  
  
   If adStatus = adStatusErrorsOccurred Then  
      Select Case pError.Number  
         Case adErrOperationCancelled  
            ' The operation was cancelled in the  
            ' Will event. Notify the user and exit.  
            strMsg = "I'm sorry you can't connect right now." & vbCrLf  
            strMsg = strMsg & "Click OK to exit."  
            Unload Me  
         Case Else  
            strMsg = "Error " & Format(pError.Number) & vbCrLf  
            strMsg = strMsg & pError.Description  
            strMsg = strMsg & "Click OK to exit."  
            Unload Me  
      End Select  
   End If  
   frmWait.btnOK.Enabled = True  
End Sub  
' EndEventExampleVB02  
```  
  
 Die **Verbindung** -Objekt deklariert wird, auf die **Formular** mithilfe der **WithEvents** Schlüsselwort, um die Behandlung von Ereignissen zu aktivieren. Der Form_Load-Ereignishandler erstellt das Objekt tatsächlich durch Zuweisung eines neuen **Verbindung** -Objekt *ConnEvent* , und klicken Sie dann die Verbindung wird geöffnet. Natürlich möchten eine echte Anwendung weitere Verarbeitung in den Form_Load-Ereignishandler als hier dargestellt wird.
