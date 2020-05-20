---
title: 'ADO-Ereignis Instanziierung: Visual Basic | Microsoft-Dokumentation'
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
author: rothja
ms.author: jroth
ms.openlocfilehash: dba3be9c80160dca2773c63b2ed7f7c706678625
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761316"
---
# <a name="ado-event-instantiation-visual-basic"></a>ADO-Ereignisinstanziierung: Visual Basic
Um ADO-Ereignisse in Microsoft® Visual Basic® behandeln zu können, müssen Sie eine Variable auf Modulebene mithilfe des **widervents** -Schlüssel Worts deklarieren. Die Variable kann nur als Teil eines Klassen Moduls deklariert werden und muss auf Modulebene deklariert werden. Dies ist jedoch nicht so restriktiv wie anscheinend, da Visual Basic **Form** -Objekte auch Klassen sind. Die einfachste Möglichkeit, ADO-Ereignisse zu verarbeiten, besteht darin, eine Variable mithilfe von **wiwitvents**zu deklarieren. Im folgenden Beispiel wird das **ConnectComplete** -Ereignis für ein **Verbindungs** Objekt behandelt:  
  
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
  
 Das **Verbindungs** Objekt wird auf der **Formular** Ebene deklariert, wobei das **widervents** -Schlüsselwort verwendet wird, um die Ereignis Behandlung zu aktivieren. Der Form_Load Ereignishandler erstellt das Objekt tatsächlich durch Zuweisen eines neuen **Verbindungs** Objekts zu *connecvent* und öffnet dann die Verbindung. Natürlich würde eine echte Anwendung im Form_Load Ereignishandler mehr Verarbeitungsvorgänge ausführen als hier gezeigt wird.
