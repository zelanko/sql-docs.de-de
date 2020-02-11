---
title: Behandeln von ADO-Ereignissen | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925223"
---
# <a name="handling-ado-events"></a>Behandeln von ADO-Ereignissen
Das ADO-Ereignis Modell unterstützt bestimmte synchrone und asynchrone ADO-Vorgänge, durch die *Ereignisse*oder Benachrichtigungen ausgegeben werden, bevor der Vorgang gestartet oder abgeschlossen wird. Ein Ereignis ist tatsächlich ein Aufrufen einer Ereignishandlerroutine, die Sie in der Anwendung definieren.  
  
 Wenn Sie Handlerfunktionen oder-Prozeduren für die Gruppe von Ereignissen bereitstellen, die vor dem Starten des Vorgangs auftreten, können Sie die Parameter, die an den Vorgang übermittelt wurden, überprüfen oder ändern. Da es noch nicht ausgeführt wurde, können Sie entweder den Vorgang abbrechen oder zulassen, dass er abgeschlossen wird.  
  
 Die Ereignisse, die nach dem Abschluss eines Vorgangs auftreten, sind besonders wichtig, wenn Sie ADO asynchron verwenden. Beispielsweise wird eine Anwendung, die einen asynchronen [Recordset. Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Vorgang startet, von einem Ereignis zum Abschluss der Ausführung benachrichtigt, wenn der Vorgang beendet wird.  
  
 Die Verwendung des ADO-Ereignis Modells erhöht den mehr Aufwand für Ihre Anwendung, bietet jedoch viel mehr Flexibilität als andere Methoden für den Umgang mit asynchronen Vorgängen, wie z. b. das Überwachen der [State](../../../ado/reference/ado-api/state-property-ado.md) -Eigenschaft eines Objekts mit einer-Schleife.  
  
> [!NOTE]
>  Zum Behandeln von Ereignissen muss ADO über eine nachrichtenpump verfügen oder in einem STA-Modell (Single Thread-Apartment) verwendet werden. ADO-Ereignisse werden intern durch Erstellen eines ausgeblendeten Fensters behandelt. ADO sendet Meldungen an dieses Fenster, wenn Ereignisse ausgelöst werden müssen. Dies geschieht, um sicherzustellen, dass Ereignisse an den Thread gesendet werden, der **IConnectionPoint:: Rat** auf dem Verbindungspunkt aufgerufen hat. Diese Architektur kann Probleme verursachen, wenn der Thread, der die Benachrichtigungen empfangen soll, keine Fenster Meldungen pumpt. Mögliche Probleme sind, dass ADO-Ereignisse nicht an den Thread übermittelt werden und globale Fenster Übertragungen einen Timeout verursachen und möglicherweise das gesamte System verlangsamen, da die ausgeblendeten Fenster die Nachrichten nicht verarbeiten. Für STA-Threads wird normalerweise ein nachrichtenpump ausgeführt, sodass sich dieses Problem nicht selbst auf STA-Threads bezieht. MTA-Threads verfügen in der Regel jedoch nicht über ein nachrichtenpump, sodass sich das Problem in der Regel auf MTA-Threads manifestiert.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [ADO-Ereignishandler – Übersicht](../../../ado/guide/data/ado-event-handler-summary.md)  
  
-   [Ereignistypen](../../../ado/guide/data/types-of-events.md)  
  
-   [Ereignisparameter](../../../ado/guide/data/event-parameters.md)  
  
-   [Zusammenwirken der Ereignishandler](../../../ado/guide/data/how-event-handlers-work-together.md)  
  
-   [ADO-Ereignisinstanziierung nach Sprache](../../../ado/guide/data/ado-event-instantiation-by-language.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-Ereignis Handler-Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO-Ereignis Instanziierung nach Sprache](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [ADO-Ereignisse](../../../ado/reference/ado-api/ado-events.md)   
 [Ereignis Parameter](../../../ado/guide/data/event-parameters.md)   
 [Ereignistypen](../../../ado/guide/data/types-of-events.md)
