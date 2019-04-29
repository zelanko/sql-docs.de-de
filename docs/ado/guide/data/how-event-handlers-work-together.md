---
title: Zusammenwirken der Ereignishandler | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO], about event handlers
- unpaired event handlers [ADO]
- paired event handlers [ADO]
- single event handlers [ADO]
- event handlers [ADO]
- multiple object event handlers [ADO]
ms.assetid: a86c8a02-dd69-420d-8a47-0188b339858d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a575e4df609430d5dc71517032f4c3da739bba24
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63161387"
---
# <a name="how-event-handlers-work-together"></a>Zusammenwirken der Ereignishandler
Es sei denn, Sie in Visual Basic für alle Ereignishandler programmieren **Verbindung** und **Recordset** Ereignisse implementiert werden müssen, unabhängig davon, ob Sie tatsächlich alle Ereignisse verarbeiten. Der Arbeitsaufwand Implementierung, die man dazu Unternehmen muss, hängt von der Programmiersprache ab. Weitere Informationen finden Sie unter [ADO-Ereignisinstanziierung nach Sprache](../../../ado/guide/data/ado-event-instantiation-by-language.md).  
  
## <a name="paired-event-handlers"></a>Gekoppelte-Ereignishandler  
 Jeder Ereignishandler wird, verfügt über eine zugeordnete **abschließen** -Ereignishandler. Wenn Ihre Anwendung ändert beispielsweise den Wert eines Felds oder der **WillChangeField** Ereignishandler wird aufgerufen. Wenn die Änderung akzeptabel ist, bleibt die Anwendung die **AdStatus** Parameter unverändert, und der Vorgang ausgeführt wird. Wenn der Vorgang abgeschlossen ist, eine **FieldChangeComplete** -Ereignis benachrichtigt die Anwendung, die der Vorgang abgeschlossen ist. Wenn sie erfolgreich abgeschlossen wird, **AdStatus** enthält **AdStatusOK**ist, andernfalls **AdStatus** enthält **AdStatusErrorsOccurred** und Sie müssen überprüfen, die **Fehler** Objekt, das die Ursache des Fehlers zu ermitteln.  
  
 Wenn **WillChangeField** wird aufgerufen, Sie können feststellen, dass die Änderung nicht vorgenommen werden soll. In diesem Fall legen **AdStatus** zu **AdStatusCancel.** Der Vorgang abgebrochen und die **FieldChangeComplete** -Ereignis empfängt ein **AdStatus** Wert **AdStatusErrorsOccurred**. Die **Fehler** Objekt enthält **AdErrOperationCancelled** , damit Ihre **FieldChangeComplete** Handler weiß, dass der Vorgang abgebrochen wurde. Allerdings müssen Sie den Wert der überprüfen die **AdStatus** Parameter vor dem ändern, da das Festlegen **AdStatus** zu **AdStatusCancel** hat keine Auswirkungen, wenn der Parameter festgelegt wurde um **AdStatusCantDeny** beim Einstieg in die Prozedur.  
  
 Manchmal kann ein Vorgang mehr als ein Ereignis auslösen. Z. B. die **Recordset** Objekt verfügt über Ereignisse für gekoppelte **Feld** Änderungen und **Datensatz** Änderungen. Wenn Ihre Anwendung ändert den Wert für eine **Feld**, wird die **WillChangeField** Ereignishandler wird aufgerufen. Wenn es feststellt, dass der Vorgang fortgesetzt werden kann, die **WillChangeRecord** -Ereignishandler wird auch ausgelöst werden. Wenn dieser Handler auch weiterhin das Ereignis zulässt, der die Änderung vorgenommen wird und die **FieldChangeComplete** und **RecordChangeComplete** -Ereignishandler werden aufgerufen. Die Reihenfolge, in der Ereignishandler wird für einen bestimmten Vorgang aufgerufen werden, ist nicht definiert, sollte also das Schreiben von Code, der zum Aufrufen von Handlern in einer bestimmten Reihenfolge abhängig ist.  
  
 In Fällen, wenn mehrere werden Ereignisse ausgelöst werden, kann eines der Ereignisse den ausstehenden Vorgang abgebrochen werden. Z. B. wenn die Anwendung ändert den Wert des einem **Feld**, beide **WillChangeField** und **WillChangeRecord** normalerweise-Ereignishandler aufgerufen. Aber wenn der Vorgang, in der erste Ereignishandler, die die zugehörigen abgebrochen wird **abschließen** Handler wird sofort aufgerufen, mit **AdStatusOperationCancelled**. Der zweite Handler wird nie aufgerufen. Wenn der erste Ereignishandler kann jedoch für das Ereignis, um den Vorgang fortzusetzen, wird der andere Ereignishandler aufgerufen werden. Wenn sie dann den Vorgang abbricht, beide **abschließen** Ereignisse werden aufgerufen, wie in den früheren Beispielen.  
  
## <a name="unpaired-event-handlers"></a>Nicht zugeordnete Ereignis-Handler  
 So lange der Status zu übergeben. das Ereignis ist kein **AdStatusCantDeny**, Sie können ereignisbenachrichtigungen für alle Ereignisse deaktivieren, indem zurückgegeben **AdStatusUnwantedEvent** in die *Status*Parameter. Z. B., wenn Ihre **abschließen** -Ereignishandler wird zum ersten Mal aufgerufen, können Sie zurückkehren **AdStatusUnwantedEvent**. Sie erhalten anschließend nur **wird** Ereignisse. Allerdings können einige Ereignisse für mehr als einer der Gründe ausgelöst werden. In diesem Fall das Ereignis hat einen *Grund* Parameter. Bei der Rückkehr **AdStatusUnwantedEvent**, halten Sie Empfang von Benachrichtigungen für dieses Ereignis nur, wenn sie für diesen bestimmten Grund auftreten. Das heißt, erhalten potenziell Benachrichtigung für jeden möglichen Grund Sie, dass das Ereignis ausgelöst werden kann.  
  
 Einzelne **wird** -Ereignishandler können nützlich sein, wenn die Parameter zu überprüfen, die in einem Vorgang verwendet werden sollen. Sie können diese Operationsparameter ändern oder brechen Sie den Vorgang.  
  
 Sie lassen **abschließen** ereignisbenachrichtigung aktiviert. Wenn Ihre erste werden Ereignishandler aufgerufen wird, zurückgeben **AdStatusUnwantedEvent**. Sie erhalten anschließend nur **abschließen** Ereignisse.  
  
 Einzelne **abschließen** -Ereignishandler für das Verwalten von asynchronen Vorgängen nützlich sein können. Jeden asynchronen Vorgang hat eine entsprechende **abschließen** Ereignis.  
  
 Beispielsweise kann eine lange dauern Auffüllen eines großen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt. Wenn Ihre Anwendung richtig geschrieben ist, können Sie starten einen `Recordset.Open(...,adAsyncExecute)` Vorgang und fahren Sie mit anderen Verarbeitung fort. Schließlich werden Sie benachrichtigt, wenn die **Recordset** werden ausgefüllt, indem ein **ExecuteComplete** Ereignis.  
  
## <a name="single-event-handlers-and-multiple-objects"></a>Einzelne Ereignishandler und mehrere Objekte  
 Die Flexibilität, einer Programmiersprache wie Microsoft Visual C++® können Sie eine Ereignis-Handler Verarbeiten von Ereignissen aus mehreren Objekten verfügen. Angenommen, Sie verfügen über eine **trennen** Event Handler Verarbeiten von Ereignissen aus mehreren **Verbindung** Objekte. Wenn eine der Verbindungen beendet wurde, die **trennen** -Ereignishandler aufgerufen. Können Sie feststellen, welche Verbindung das Ereignis verursacht hat, da der Ereignishandler-Objektparameter mit der entsprechenden festgelegt werden, würde **Verbindung** Objekt.  
  
> [!NOTE]
>  Diese Technik kann nicht in Visual Basic verwendet werden, da diese Sprache nur ein Objekt an einen Ereignishandler in Beziehung setzen kann.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO-Ereignisinstanziierung nach Sprache](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Ereignisparameter](../../../ado/guide/data/event-parameters.md)   
 [Typen von Ereignissen](../../../ado/guide/data/types-of-events.md)
