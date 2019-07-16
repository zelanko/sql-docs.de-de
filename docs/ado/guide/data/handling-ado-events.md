---
title: ADO-Ereignisbehandlung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO]
- ADO, events
- event handlers [ADO]
ms.assetid: e9003457-0762-48b3-942f-0820266b158f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 452259b6e4e406d7a406211a9e9b42ebbf60da53
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925223"
---
# <a name="handling-ado-events"></a>Behandeln von ADO-Ereignissen
Das ADO-Ereignismodell unterstützt bestimmte synchrone und asynchrone ADO-Vorgänge, die ausstellen *Ereignisse*, oder Benachrichtigungen, bevor der Vorgang gestartet oder nachdem es abgeschlossen ist. Ein Ereignis ist tatsächlich ein Aufruf an eine Ereignishandler-Routine, die Sie in Ihrer Anwendung zu definieren.  
  
 Wenn Sie für die Gruppe von Ereignissen Handlerfunktionen oder Prozeduren, die vor dem Starten der Operation auftreten angeben, können Sie untersuchen oder ändern Sie die Parameter, die für den Vorgang übergeben wurden. Da sie noch nicht ausgeführt wurde, können Sie den Vorgang abbrechen oder zuzulassen, dass sie zum Abschließen.  
  
 Die Ereignisse, die nach Abschluss eines Vorgangs auftreten, sind besonders wichtig, wenn Sie ADO, asynchron verwenden. Z. B. eine Anwendung, die einen asynchronen startet [Recordset.Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) Vorgang wird benachrichtigt, von einem vollständigen Ausführung-Ereignis, wenn die Operation abgeschlossen ist.  
  
 Mit dem ADO-Ereignismodell zusätzlichen Aufwand für Ihre Anwendung hinzugefügt, jedoch bietet weit mehr Flexibilität als die anderen Methoden für den Umgang mit asynchronen Vorgängen, z. B. Überwachung der [Zustand](../../../ado/reference/ado-api/state-property-ado.md) Eigenschaft eines Objekts mit einer Schleife.  
  
> [!NOTE]
>  Zum Verarbeiten von Ereignissen, ADO-Meldungsverteilschleife oder muss in einem Singlethread-Apartment (STA)-Modell verwendet werden. ADO-Ereignisse werden intern behandelt, durch ein ausgeblendetes Fenster erstellen. ADO sendet Nachrichten an dieses Fenster, wenn Ereignisse ausgelöst werden müssen. Dies geschieht, um sicherzustellen, dass Ereignisse an den Thread gesendet werden, die aufgerufen **IConnectionPoint:: Advise** auf dem Verbindungspunkt. Diese Architektur kann Probleme verursachen, wenn der Thread, der die Benachrichtigungen erhalten sollen nicht fenstermeldungen senden ist. Potenzielle Probleme enthalten ADO-Ereignisse, die nicht zugestellt werden, auf den Thread und das Fenster "global" Broadcasts Timeout und das gesamte System möglicherweise verlangsamt, da die ausgeblendete Fenster keine Nachrichten verarbeiten. STA-Threads verfügen in der Regel eine Meldungsverteilschleife, die ausgeführt werden, damit dieses Problem nicht selbst auf STA-Threads-manifest. MTA-Threads, jedoch haben nicht in der Regel ein Nachrichtensystem, damit das Problem selbst in der Regel auf MTA-Threads manifest.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)  
  
-   [Typen von Ereignissen](../../../ado/guide/data/types-of-events.md)  
  
-   [Ereignisparameter](../../../ado/guide/data/event-parameters.md)  
  
-   [Zusammenwirken der Ereignishandler](../../../ado/guide/data/how-event-handlers-work-together.md)  
  
-   [ADO-Ereignisinstanziierung nach Sprache](../../../ado/guide/data/ado-event-instantiation-by-language.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO-Ereignisinstanziierung nach Sprache](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [ADO-Ereignisse](../../../ado/reference/ado-api/ado-events.md)   
 [Ereignisparameter](../../../ado/guide/data/event-parameters.md)   
 [Typen von Ereignissen](../../../ado/guide/data/types-of-events.md)
