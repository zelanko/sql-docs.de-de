---
title: Ereignis Typen | Microsoft-Dokumentation
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
ms.openlocfilehash: c02d8d115a4336470c0e0d32aebabea63c05ab0b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923817"
---
# <a name="types-of-events"></a>Ereignistypen
Es gibt zwei grundlegende Arten von Ereignissen. "Will-Ereignisse", die vor dem Start eines Vorgangs aufgerufen werden, enthalten in der Regel "will" in ihren Namen, z. b. " **WillChangeRecordset** " oder " **WillConnect**". Ereignisse, die nach dem Abschluss eines Ereignisses aufgerufen werden, enthalten in der Regel den Namen "Complete" (z. b. **RecordChangeComplete** oder **ConnectComplete**). Ausnahmen sind vorhanden, z. **b. infomess** . Diese werden jedoch nach Abschluss des zugehörigen Vorgangs auftreten.  
  
## <a name="will-events"></a>Ereignisse  
 Ereignishandler, die aufgerufen werden, bevor der Vorgang gestartet wird, bieten Ihnen die Möglichkeit, die Vorgangs Parameter zu überprüfen oder zu ändern und dann entweder den Vorgang abzubrechen oder den Vorgang abzuschließen. Diese Ereignishandlerroutinen enthalten in der Regel Namen <strong>des** Formulars.</strong>  
  
## <a name="complete-events"></a>Ereignisse vervollständigen  
 Ereignishandler, die aufgerufen werden, nachdem ein Vorgang abgeschlossen wurde, können die Anwendung Benachrichtigen, dass ein Vorgang abgeschlossen wurde. Ein solcher Ereignishandler wird auch benachrichtigt, wenn ein Ereignishandler einen ausstehenden Vorgang abbricht. Diese Ereignishandlerroutinen enthalten in der Regel Namen des Formular <strong> *Ereignisses*Complete</strong>.  
  
 Die Ereignisse werden in der Regel in Paaren verwendet.  
  
## <a name="other-events"></a>Andere Ereignisse  
 Die anderen Ereignishandler, d. h. Ereignisse, deren Namen nicht das Formular darstellen, <strong>werden als*Ereignis* </strong> oder <strong> *Ereignis*abgeschlossen</strong> bezeichnet. Sie werden erst aufgerufen, nachdem ein Vorgang abgeschlossen wurde. Diese Ereignisse sind **Disconnect**, **endosrecordset**und **infomess**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-Ereignis Handler-Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO-Ereignis Instanziierung nach Sprache](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Ereignis Parameter](../../../ado/guide/data/event-parameters.md)   
 [Zusammenwirken der Ereignishandler](../../../ado/guide/data/how-event-handlers-work-together.md)
