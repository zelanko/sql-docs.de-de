---
title: Ereignis Parameter | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Error parameter [ADO]
- Object parameter [ADO]
- Status parameter [ADO]
- events [ADO], parameters
- Reason parameter [ADO]
- event parameters [ADO]
ms.assetid: bd5c5afa-d301-4899-acda-40f98a6afa4d
author: rothja
ms.author: jroth
ms.openlocfilehash: 32e3cd177089fb99009490b82941928e091ab7c6
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763191"
---
# <a name="event-parameters"></a>Ereignisparameter
Jeder Ereignishandler verfügt über einen Status Parameter, der den Ereignishandler steuert. Bei Abschluss Ereignissen wird dieser Parameter auch verwendet, um den Erfolg oder Misserfolg des Vorgangs anzugeben, der das Ereignis generiert hat. Die meisten vollständigen Ereignisse verfügen auch über einen Fehler Parameter, um Informationen zu ggf. aufgetretenen Fehlern und einen oder mehrere Objekt Parameter bereitzustellen, die auf die ADO-Objekte verweisen, die zum Ausführen des Vorgangs verwendet werden. Das Ereignis [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md) enthält z. b. Objekt Parameter für die **Befehle**, **Recordsets**und **Verbindungs** Objekte, die dem Ereignis zugeordnet sind. Im folgenden Beispiel zu Microsoft® Visual Basic® werden die Objekte pcommand, precordset und pconnection angezeigt, die den **Befehl**, das **Recordset**und die **Verbindungs** Objekte darstellen, die von der **Execute** -Methode verwendet werden.  
  
```  
Private Sub connEvent_ExecuteComplete(ByVal RecordsAffected As Long, _  
     ByVal pError As ADODB.Error, _  
     adStatus As ADODB.EventStatusEnum, _  
     ByVal pCommand As ADODB.Command, _  
     ByVal pRecordset As ADODB.Recordset, _  
     ByVal pConnection As ADODB.Connection)  
```  
  
 Mit Ausnahme des **Error** -Objekts werden die gleichen Parameter an die-Ereignisse des-Objekts übermittelt. Auf diese Weise können Sie jedes der Objekte untersuchen, die im ausstehenden Vorgang verwendet werden, und bestimmen, ob der Vorgang beendet werden soll.  
  
 Einige Ereignishandler verfügen über einen *reason* -Parameter, der zusätzliche Informationen darüber bereitstellt, warum das Ereignis aufgetreten ist. Beispielsweise können die Ereignisse " **WillMove** " und " **MoveComplete** " auftreten, wenn eine der Navigationsmethoden (**MoveNext**, **MovePrevious**usw.) aufgerufen wird, oder als Ergebnis einer Anforderung.  
  
## <a name="status-parameter"></a>Status Parameter  
 Wenn die Ereignishandlerroutine aufgerufen wird, wird der *Status* Parameter auf einen der folgenden Werte festgelegt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**adStatus**|Wird an die beiden-und-Abschluss Ereignisse übermittelt. Dieser Wert bedeutet, dass der Vorgang, der das Ereignis ausgelöst hat, erfolgreich abgeschlossen wurde.|  
|**adstatuuserrorsoccurrred**|Wird nur an Complete-Ereignisse übermittelt. Dieser Wert bedeutet, dass der Vorgang, der das Ereignis verursacht hat, nicht erfolgreich war, oder ein Ereignis hat den Vorgang abgebrochen. Weitere Informationen finden Sie im *Fehler* Parameter.|  
|**adStatus-kandeny**|An werden nur Ereignisse übermittelt. Dieser Wert bedeutet, dass der Vorgang nicht vom Ereignis Ereignis abgebrochen werden kann. Er muss ausgeführt werden.|  
  
 Wenn Sie in dem Ereignis feststellen, dass der Vorgang fortgesetzt werden soll, lassen Sie den *Status* Parameter unverändert. Solange der eingehende Status Parameter nicht auf **adStatusCantDeny**festgelegt wurde, können Sie den ausstehenden Vorgang jedoch abbrechen, indem Sie den *Status* in **adStatusCancel**ändern. Wenn Sie dies tun, ist der *Status* Parameter für das Complete-Ereignis, das dem Vorgang zugeordnet ist, auf **adstatuserrorsoccurrred**festgelegt. Das **Fehler** Objekt, das an das Complete-Ereignis übertragen wird, enthält den Wert **aderroperationabgeb Rochen**.  
  
 Wenn Sie ein Ereignis nicht mehr verarbeiten möchten, können Sie den *Status* auf **adStatusUnwantedEvent** festlegen, und Ihre Anwendung erhält keine Benachrichtigung mehr über dieses Ereignis. Denken Sie jedoch daran, dass einige Ereignisse aus mehr als einem Grund ausgelöst werden können. In diesem Fall müssen Sie für jeden möglichen Grund **adStatus-unwantedebug** angeben. Wenn Sie z. b. keine Benachrichtigung über **ausstehende recordchange** -Ereignisse mehr erhalten möchten, Sie müssen den *Status* -Parameter auf **adStatusUnwantedEvent** für **adrsnaddnew**, **adrsndelete**, **adrsnupdate**, **adrsnundoupdate**, **adrsnundoaddnew**, **adrsnundodelete**und **adrsnfirstchange** festlegen, wenn diese auftreten.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**adStatus-unwantedebug**|Fordern Sie an, dass dieser Ereignishandler keine weiteren Benachrichtigungen empfängt.|  
|**adStatus Cancel**|Anforderungs Abbruch des Vorgangs, der ausgeführt werden soll.|  
  
## <a name="error-parameter"></a>Error-Parameter  
 Der *Error* -Parameter ist ein Verweis auf ein ADO- [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Wenn der *Status* Parameter auf **adstatuserrorsoccurrred**festgelegt ist, enthält das **Fehler** Objektdetails darüber, warum der Vorgang fehlgeschlagen ist. Wenn das Ereignis, das einem abgeschlossenen Ereignis zugeordnet ist, den Vorgang abgebrochen hat, indem der *Status* Parameter auf **adStatusCancel**festgelegt wurde, wird das Fehler Objekt immer auf **aderroperationcancel**festgelegt.  
  
## <a name="object-parameter"></a>Object-Parameter  
 Jedes Ereignis empfängt mindestens ein-Objekt, das die Objekte darstellt, die an dem Vorgang beteiligt sind. Das Ereignis **ExecuteComplete** erhält z. b. ein **Befehls** Objekt, ein **Recordset** -Objekt und ein **Verbindungs** Objekt.  
  
## <a name="reason-parameter"></a>Reason-Parameter  
 Der Parameter " *reason* ", *adReason*, bietet zusätzliche Informationen darüber, warum das Ereignis aufgetreten ist. Ereignisse mit einem *adReason* -Parameter können auch für denselben Vorgang mehrmals aufgerufen werden, und zwar aus einem anderen Grund jedes Mal. Der **WillChangeRecord** -Ereignishandler wird z. b. für Vorgänge aufgerufen, die im Begriff sind, das Einfügen, löschen oder Ändern eines Datensatzes rückgängig zu machen oder rückgängig zu machen. Wenn Sie ein Ereignis nur dann verarbeiten möchten, wenn es aus einem bestimmten Grund auftritt, können Sie den *adReason* -Parameter verwenden, um die vorkommen herauszufiltern, an denen Sie nicht interessiert sind. Wenn Sie z. b. Daten Satz Änderungs Ereignisse nur dann verarbeiten möchten, wenn Sie auftreten, weil ein Datensatz hinzugefügt wurde, können Sie Folgendes verwenden:  
  
```  
' BeginEventExampleVB01  
Private Sub rsTest_WillChangeRecord(ByVal adReason As ADODB.EventReasonEnum, ByVal cRecords As Long, adStatus As ADODB.EventStatusEnum, ByVal pRecordset As ADODB.Recordset)  
   If adReason = adRsnAddNew Then  
       ' Process event  
       '...  
   Else  
       ' Cancel event notification for all  
       ' other possible adReason values.  
       adStatus = adStatusUnwantedEvent  
   End If  
End Sub  
' EndEventExampleVB01  
```  
  
 In diesem Fall kann für jeden der anderen Gründe eine Benachrichtigung auftreten. Allerdings wird Sie nur einmal pro Grund ausgeführt. Nachdem die Benachrichtigung aus jedem Grund einmal aufgetreten ist, erhalten Sie nur dann eine Benachrichtigung, wenn ein neuer Datensatz hinzugefügt wird.  
  
 Im Gegensatz dazu müssen Sie *adStatus* nur einmal auf **adStatusUnwantedEvent** festlegen, um anzufordern, dass ein Ereignishandler ohne einen **adReason** -Parameter den Empfang von Ereignis Benachrichtigungen beenden kann.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-Ereignis Handler-Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO-Ereignis Instanziierung nach Sprache](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Zusammenarbeiten von Ereignis Handlern](../../../ado/guide/data/how-event-handlers-work-together.md)   
 [Ereignis Typen](../../../ado/guide/data/types-of-events.md)
