---
title: Zusammenarbeiten von Ereignis Handlern | Microsoft-Dokumentation
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
ms.openlocfilehash: b744dbd464aedbd9b87d22aa74277787fcc3c7a3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925044"
---
# <a name="how-event-handlers-work-together"></a>Zusammenwirken der Ereignishandler
Sofern Sie nicht in Visual Basic programmieren, müssen alle Ereignishandler für **Verbindungs** -und **recordsetereignisse** implementiert werden, unabhängig davon, ob Sie tatsächlich alle Ereignisse verarbeiten. Die Menge der Implementierungs Arbeit, die Sie erledigen müssen, hängt von ihrer Programmiersprache ab. Weitere Informationen finden Sie unter [ADO Event Instantiierung by Language](../../../ado/guide/data/ado-event-instantiation-by-language.md).  
  
## <a name="paired-event-handlers"></a>Paarweise Ereignishandler  
 Jedem Ereignishandler wird ein **kompletter** Ereignishandler zugeordnet. Wenn Ihre Anwendung z. b. den Wert eines Felds ändert, wird der Ereignishandler " **WillChangeField** " aufgerufen. Wenn die Änderung zulässig ist, lässt die Anwendung den Parameter " **adStatus** " unverändert, und der Vorgang wird ausgeführt. Wenn der Vorgang abgeschlossen ist, benachrichtigt das Ereignis **FieldChangeComplete** Ihre Anwendung, dass der Vorgang abgeschlossen wurde. Wenn der Vorgang erfolgreich abgeschlossen wurde, enthält **adStatus** **adStatusOK**; Andernfalls enthält **adStatus** **adstatuserrorsoccurrred** , und Sie müssen das **Fehler** Objekt überprüfen, um die Ursache des Fehlers zu ermitteln.  
  
 Wenn " **WillChangeField** " aufgerufen wird, können Sie feststellen, dass die Änderung nicht vorgenommen werden sollte. Legen Sie in diesem Fall **adStatus** auf **adStatusCancel fest.** Der Vorgang wird abgebrochen, und das **FieldChangeComplete** -Ereignis empfängt den **adStatus** -Wert **adstatuserrorsoccurrred**. Das **Error** -Objekt enthält **aderroperationabgeb Rochen** , sodass der **FieldChangeComplete** -Handler weiß, dass der Vorgang abgebrochen wurde. Sie müssen jedoch den Wert des Parameters " **adStatus** " vor der Änderung überprüfen, da das Festlegen von " **adStatus** " auf " **adStatusCancel** " keine Auswirkung hat, wenn der Parameter für den Eintrag für die Prozedur auf **adStatusCantDeny** festgelegt wurde.  
  
 Manchmal kann ein Vorgang mehr als ein Ereignis hervorrufen. Beispielsweise weist das **Recordset** -Objekt gekoppelte Ereignisse für **Feld** Änderungen und **Daten Satz** Änderungen auf. Wenn die Anwendung den Wert eines **Felds**ändert, wird der Ereignishandler " **WillChangeField** " aufgerufen. Wenn festgelegt wird, dass der Vorgang fortgesetzt werden kann, wird auch der Ereignishandler " **WillChangeRecord** " ausgelöst. Wenn dieser Handler auch das Fortsetzen des Ereignisses zulässt, wird die Änderung vorgenommen, und die Ereignishandler **FieldChangeComplete** und **RecordChangeComplete** werden aufgerufen. Die Reihenfolge, in der die Ereignishandler für einen bestimmten Vorgang aufgerufen werden, ist nicht definiert. Daher sollten Sie vermeiden, Code zu schreiben, der von aufrufenden Handlern in einer bestimmten Sequenz abhängt.  
  
 In Fällen, in denen mehrere Ereignisse ausgelöst werden, kann eines der Ereignisse den ausstehenden Vorgang abbrechen. Wenn Ihre Anwendung z. b. den Wert eines **Felds**ändert, werden die Ereignishandler " **WillChangeField** " und " **WillChangeRecord** " normalerweise aufgerufen. Wenn der Vorgang jedoch im ersten Ereignishandler abgebrochen wird, wird der zugehörige **komplette** Handler sofort mit " **adStatus operationabgeb Rochen**" aufgerufen. Der zweite Handler wird nie aufgerufen. Wenn jedoch der erste Ereignishandler zulässt, dass das Ereignis fortgesetzt werden kann, wird der andere Ereignishandler aufgerufen. Wenn der Vorgang dann abgebrochen wird, werden **beide abgeschlossenen** Ereignisse wie in den vorherigen Beispielen aufgerufen.  
  
## <a name="unpaired-event-handlers"></a>Nicht paarweise zugeordnete Ereignishandler  
 Solange der an das Ereignis übergebenen Status nicht " **adStatusCantDeny**" ist, können Sie Ereignis Benachrichtigungen für jedes Ereignis deaktivieren, indem Sie " **adStatusUnwantedEvent** " im *Status* Parameter zurückgeben. Wenn z. b. der **Complete** -Ereignishandler zum ersten Mal aufgerufen wird, können Sie " **adStatus-unwantedevent**" zurückgeben. Anschließend **werden nur Ereignisse** empfangen. Einige Ereignisse können jedoch aus mehreren Gründen ausgelöst werden. In diesem Fall verfügt das Ereignis über einen *reason* -Parameter. Wenn Sie " **adStatus-unwantedevent**" zurückgeben, beenden Sie den Empfang von Benachrichtigungen für dieses Ereignis nur dann, wenn Sie aus diesem speziellen Grund auftreten. Das heißt, Sie erhalten möglicherweise eine Benachrichtigung für jeden möglichen Grund, warum das Ereignis ausgelöst werden konnte.  
  
 Single **-** Ereignishandler können nützlich sein, wenn Sie die Parameter untersuchen möchten, die in einem Vorgang verwendet werden. Sie können diese Vorgangs Parameter ändern oder den Vorgang abbrechen.  
  
 Lassen Sie alternativ Ereignis Benachrichtigung **Beenden** aktiviert. Wenn Ihr erster Ereignishandler aufgerufen wird, wird **adStatus-unwantedevent**zurückgegeben. Anschließend **werden nur die** abgeschlossenen Ereignisse angezeigt.  
  
 Single **Complete** -Ereignishandler können für die Verwaltung von asynchronen Vorgängen nützlich sein. Jeder asynchrone Vorgang verfügt über ein entsprechendes **Complete** -Ereignis.  
  
 Beispielsweise kann es sehr lange dauern, bis ein großes [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt aufgefüllt ist. Wenn Ihre Anwendung ordnungsgemäß geschrieben wird, können Sie einen `Recordset.Open(...,adAsyncExecute)` -Vorgang starten und mit der anderen Verarbeitung fortfahren. Sie werden letztendlich benachrichtigt, wenn das **Recordset** durch ein **ExecuteComplete** -Ereignis aufgefüllt wird.  
  
## <a name="single-event-handlers-and-multiple-objects"></a>Einzelne Ereignishandler und mehrere Objekte  
 Die Flexibilität einer Programmiersprache wie Microsoft Visual C++® ermöglicht, dass ein ereignishandlerereignis Ereignisse aus mehreren Objekten verarbeitet. Beispielsweise können Sie einen Ereignishandler zum **trennen** von Ereignissen von mehreren **Verbindungs** Objekten verarbeiten. Wenn eine der Verbindungen beendet wurde, wird der **Disconnect** -Ereignishandler aufgerufen. Sie können feststellen, welche Verbindung das Ereignis verursacht hat, da der ereignishandlerobjektparameter auf das entsprechende **Verbindungs** Objekt festgelegt wird.  
  
> [!NOTE]
>  Diese Methode kann nicht in Visual Basic verwendet werden, da diese Sprache nur ein Objekt mit einem Ereignishandler korrelieren kann.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-Ereignis Handler-Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO-Ereignis Instanziierung nach Sprache](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Ereignis Parameter](../../../ado/guide/data/event-parameters.md)   
 [Ereignis Typen](../../../ado/guide/data/types-of-events.md)
