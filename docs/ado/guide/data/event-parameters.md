---
title: Ereignisparameter | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 26caf2b54b4f0affbbe7cdc58fa2bf742f0d4101
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925364"
---
# <a name="event-parameters"></a>Ereignisparameter
Jeder Ereignishandler verfügt über eine Status-Parameter, der steuert, den Ereignishandler. Für Ereignisse zum Abschluss wird auch dieser Parameter verwendet, um anzugeben, den Erfolg oder Misserfolg des Vorgangs, der das Ereignis generiert hat. Umfassendste Ereignisse haben auch einen Fehlerparameter, um Aufschluss über alle Fehler, die aufgetreten sind, und einen oder mehrere Objektparameter, die auf die ADO-Objekte, die zum Ausführen des Vorgangs zu verweisen. Z. B. die [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md) Ereignis enthält die Objektparameter, für die **Befehl**, **Recordset**, und **Verbindung** Objekte mit dem Ereignis verknüpft ist. Im folgenden Microsoft® Visual Basic® Beispiel sehen Sie die pCommand pRecordset und pConnection-Objekten, die darstellen der **Befehl**, **Recordset**, und **Verbindung** Objekte, mit denen, die **Execute** Methode.  
  
```  
Private Sub connEvent_ExecuteComplete(ByVal RecordsAffected As Long, _  
     ByVal pError As ADODB.Error, _  
     adStatus As ADODB.EventStatusEnum, _  
     ByVal pCommand As ADODB.Command, _  
     ByVal pRecordset As ADODB.Recordset, _  
     ByVal pConnection As ADODB.Connection)  
```  
  
 Mit Ausnahme der **Fehler** Objekt, auf die Ereignisse werden die gleichen Parameter übergeben werden. Mit diesem können Sie alle Objekte untersuchen, die in den ausstehenden Vorgang verwendet wird, und bestimmen, ob der Vorgang zugelassen werden soll, um den Vorgang abzuschließen.  
  
 Haben Sie einige Ereignishandler eine *Grund* -Parameter, der enthält zusätzliche Informationen darüber, warum das Ereignis aufgetreten ist. Z. B. die **WillMove** und **MoveComplete** Ereignisse können auftreten, aufgrund eines die Navigation-Methoden (**MoveNext**, **MovePrevious**usw.) aufgerufen wird oder als Ergebnis einer erneuten Abfrage.  
  
## <a name="status-parameter"></a>Status-Parameter  
 Wenn die Ereignishandler-Routine aufgerufen wird, die *Status* Parameter auf einen der folgenden Werte festgelegt ist.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**adStatusOK**|Übergeben sowohl die wird als auch die Ereignisse zum Abschluss. Dieser Wert bedeutet, dass den Vorgang, der das Ereignis wurde erfolgreich abgeschlossen verursacht hat.|  
|**adStatusErrorsOccurred**|Um nur Ereignisse zum Abschluss übergeben. Dieser Wert bedeutet, dass der Vorgang, der das Ereignis ausgelöst wurde nicht erfolgreich war, oder ein Ereignis wird der Vorgang wurde abgebrochen. Überprüfen Sie die *Fehler* -Parameter für weitere Details.|  
|**adStatusCantDeny**|Um nur die Ereignisse werden übergeben. Dieser Wert bedeutet, dass das Ereignis wird der Vorgang abgebrochen werden kann nicht an. Sie müssen ausgeführt werden.|  
  
 Wenn Sie in das Ereignis wird, die der Vorgang fortgesetzt werden soll ermitteln, lassen Sie die *Status* Parameter unverändert. Solange die eingehenden Status-Parameter nicht, um festgelegt wurde **AdStatusCantDeny**, jedoch können Sie den ausstehenden Vorgang abbrechen, indem ändern *Status* zu **AdStatusCancel**. Wenn Sie dies tun, ist die ausgelöste Ereignis, das dem Vorgang zugeordnete seine *Status* Parametersatz zu **AdStatusErrorsOccurred**. Die **Fehler** an das Abschlussereignis übergebene Objekt enthält den Wert **AdErrOperationCancelled**.  
  
 Wenn Sie nicht mehr ein Ereignis verarbeiten möchten, legen Sie *Status* zu **AdStatusUnwantedEvent** und empfängt die Anwendung nicht mehr benachrichtigt, wenn das Ereignis. Beachten Sie jedoch, dass einige Ereignisse für mehr als einer der Gründe ausgelöst werden können. In diesem Fall müssen Sie angeben **AdStatusUnwantedEvent** für jeden möglichen Grund. Beispielsweise zum Beenden des Empfangs der Benachrichtigung über ausstehende **RecordChange** Ereignisse, müssen Sie festlegen, die *Status* Parameter **AdStatusUnwantedEvent** für  **AdRsnAddNew**, **AdRsnDelete**, **AdRsnUpdate**, **AdRsnUndoUpdate**, **AdRsnUndoAddNew**, **AdRsnUndoDelete**, und **AdRsnFirstChange** eintreten.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**adStatusUnwantedEvent**|Fordern Sie an, dass dieser Ereignishandler keine weiteren Benachrichtigungen erhalten.|  
|**adStatusCancel**|Fordern Sie Abbruch des Vorgangs, der ausgeführt wird.|  
  
## <a name="error-parameter"></a>Fehlerparameter  
 Die *Fehler* Parameter ist ein Verweis auf ein ADO- [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Wenn die *Status* Parameter auf festgelegt ist **AdStatusErrorsOccurred**, **Fehler** Objekt enthält die Details, warum der Vorgang fehlgeschlagen ist. Ein vollständiges Ereignis zugeordnete wird Ereignis den Vorgang durch Festlegen von abgebrochen hat die *Status* Parameter **AdStatusCancel**, das Fehlerobjekt, das ist immer festgelegt, um  **AdErrOperationCancelled**.  
  
## <a name="object-parameter"></a>Object-Parameter  
 Jedes Ereignis empfängt ein oder mehrere Objekte, die die Objekte, die an dem Vorgang beteiligt sind darstellt. Z. B. die **ExecuteComplete** -Ereignis empfängt. ein **Befehl** Objekt eine **Recordset** -Objekt, und ein **Verbindung** Objekt.  
  
## <a name="reason-parameter"></a>Parameter Grund  
 Die *Grund* Parameter *AdReason*, enthält zusätzliche Informationen darüber, warum das Ereignis aufgetreten ist. Ereignisse mit einem *AdReason* Parameter kann auch für denselben Vorgang für einen anderen Grund jedes Mal mehrere Male aufgerufen werden. Z. B. die **WillChangeRecord** Ereignishandler wird aufgerufen, für Vorgänge, die ausgeführt oder rückgängig gemacht, das Einfügen, löschen oder die Änderung eines Datensatzes. Wenn Sie ein Ereignis verarbeitet, nur wenn er einem bestimmten Grund auftritt, können Sie verwenden möchten. die *AdReason* Parameter, um die Vorkommen filtern Sie nicht interessiert sind. Z. B. wenn, zum Verarbeiten von Datensatz-Change-Ereignissen nur, wenn sie auftreten gewünscht, da ein Eintrag hinzugefügt wurde, können Sie etwa wie folgt verwenden.  
  
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
  
 In diesem Fall kann die Benachrichtigung möglicherweise für jede der anderen Gründe auftreten. Es wird jedoch nur einmal für jeden Grund auftreten. Nachdem die Benachrichtigung einmal für jeden Grund aufgetreten ist, erhalten Sie Benachrichtigungen nur für das Hinzufügen eines neuen Datensatzes.  
  
 Im Gegensatz dazu müssen Sie *AdStatus* zu **AdStatusUnwantedEvent** nur einmal an, die Anforderung einen Ereignishandler, ohne eine **AdReason** empfangenden Parameter Stop-Ereignis Benachrichtigungen.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO-Ereignisinstanziierung nach Sprache](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Zusammenwirken der Ereignishandler](../../../ado/guide/data/how-event-handlers-work-together.md)   
 [Typen von Ereignissen](../../../ado/guide/data/types-of-events.md)
