---
title: Typen von Ereignissen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- EventComplete event [ADO]
- events [ADO], types
- Will events [ADO]
- complete events [ADO]
- WillEvent event [ADO]
ms.assetid: f3327ea0-635a-43d4-bd78-c1674f62f1a2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 78505f010706a39e5278d50219dd4504e33dd67c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63142939"
---
# <a name="types-of-events"></a>Ereignistypen
Es gibt zwei grundlegende Arten von Ereignissen. "Werden Ereignisse" die aufgerufen werden, bevor ein Vorgang gestartet wird, stehen in der Regel "Wird" im Namen – beispielsweise **WillChangeRecordset** oder **WillConnect**. Ereignisse, die aufgerufen werden, nachdem ein Ereignis in der Regel abgeschlossen wurde enthalten "Abgeschlossen" im Namen – beispielsweise **RecordChangeComplete** oder **ConnectComplete**. Ausnahmen vorhanden sind – z. B. **InfoMessage** –, aber diese treten auf, nachdem der zugeordnete Vorgang abgeschlossen wurde.  
  
## <a name="will-events"></a>Ereignisse werden  
 -Ereignishandler wird aufgerufen, bevor der Vorgang beginnt Sie die Möglichkeit zum Untersuchen bieten oder ändern die Vorgangsparameter, und klicken Sie dann den Vorgang abbrechen oder erlauben, dass Sie abgeschlossen. Dieser Ereignishandler-Routinen haben in der Regel die Namen im Format <strong>wird*Ereignis*</strong>.  
  
## <a name="complete-events"></a>Ereignisse durch Abschluss  
 -Ereignishandler wird aufgerufen, nachdem ein Vorgang abgeschlossen ist, können die Anwendung benachrichtigt, die eine Operation abgeschlossen wurde. Ein solcher Ereignishandler ist auch benachrichtigt werden, wenn ein Ereignishandler wird über einen ausstehenden Vorgang abbricht. Dieser Ereignishandler-Routinen haben in der Regel die Namen im Format  <strong>*Ereignis*abschließen</strong>.  
  
 Wird und Ereignisse zum Abschluss werden in der Regel paarweise verwendet.  
  
## <a name="other-events"></a>Andere Ereignisse  
 Die anderen Ereignishandler – d.h. die Ereignisse, deren Namen nicht im Format sind <strong>wird*Ereignis*</strong>  oder  <strong>*Ereignis*abschließen</strong> -erst aufgerufen werden ein Vorgang abgeschlossen ist. Diese Ereignisse sind **trennen**, **EndOfRecordset**, und **InfoMessage**.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO-Ereignisinstanziierung nach Sprache](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Ereignisparameter](../../../ado/guide/data/event-parameters.md)   
 [Zusammenwirken der Ereignishandler](../../../ado/guide/data/how-event-handlers-work-together.md)
