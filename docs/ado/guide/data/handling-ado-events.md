---
description: Behandeln von ADO-Ereignissen
title: Behandeln von ADO-Ereignissen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO]
- ADO, events
- event handlers [ADO]
ms.assetid: e9003457-0762-48b3-942f-0820266b158f
author: rothja
ms.author: jroth
ms.openlocfilehash: ff36542abb462ffc63e8704a5c6c3cdd6670d280
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980701"
---
# <a name="handling-ado-events"></a>Behandeln von ADO-Ereignissen
Das ADO-Ereignis Modell unterstützt bestimmte synchrone und asynchrone ADO-Vorgänge, durch die *Ereignisse*oder Benachrichtigungen ausgegeben werden, bevor der Vorgang gestartet oder abgeschlossen wird. Ein Ereignis ist tatsächlich ein Aufrufen einer Ereignishandlerroutine, die Sie in der Anwendung definieren.  
  
 Wenn Sie Handlerfunktionen oder-Prozeduren für die Gruppe von Ereignissen bereitstellen, die vor dem Starten des Vorgangs auftreten, können Sie die Parameter, die an den Vorgang übermittelt wurden, überprüfen oder ändern. Da es noch nicht ausgeführt wurde, können Sie entweder den Vorgang abbrechen oder zulassen, dass er abgeschlossen wird.  
  
 Die Ereignisse, die nach dem Abschluss eines Vorgangs auftreten, sind besonders wichtig, wenn Sie ADO asynchron verwenden. Beispielsweise wird eine Anwendung, die einen asynchronen [Recordset. Open](../../reference/ado-api/open-method-ado-recordset.md) -Vorgang startet, von einem Ereignis zum Abschluss der Ausführung benachrichtigt, wenn der Vorgang beendet wird.  
  
 Die Verwendung des ADO-Ereignis Modells erhöht den mehr Aufwand für Ihre Anwendung, bietet jedoch viel mehr Flexibilität als andere Methoden für den Umgang mit asynchronen Vorgängen, wie z. b. das Überwachen der [State](../../reference/ado-api/state-property-ado.md) -Eigenschaft eines Objekts mit einer-Schleife.  
  
> [!NOTE]
>  Zum Behandeln von Ereignissen muss ADO über eine nachrichtenpump verfügen oder in einem STA-Modell (Single Thread-Apartment) verwendet werden. ADO-Ereignisse werden intern durch Erstellen eines ausgeblendeten Fensters behandelt. ADO sendet Meldungen an dieses Fenster, wenn Ereignisse ausgelöst werden müssen. Dies geschieht, um sicherzustellen, dass Ereignisse an den Thread gesendet werden, der **IConnectionPoint:: Rat** auf dem Verbindungspunkt aufgerufen hat. Diese Architektur kann Probleme verursachen, wenn der Thread, der die Benachrichtigungen empfangen soll, keine Fenster Meldungen pumpt. Mögliche Probleme sind, dass ADO-Ereignisse nicht an den Thread übermittelt werden und globale Fenster Übertragungen einen Timeout verursachen und möglicherweise das gesamte System verlangsamen, da die ausgeblendeten Fenster die Nachrichten nicht verarbeiten. Für STA-Threads wird normalerweise ein nachrichtenpump ausgeführt, sodass sich dieses Problem nicht selbst auf STA-Threads bezieht. MTA-Threads verfügen in der Regel jedoch nicht über ein nachrichtenpump, sodass sich das Problem in der Regel auf MTA-Threads manifestiert.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [ADO-Ereignishandler – Übersicht](./ado-event-handler-summary.md)  
  
-   [Ereignistypen](./types-of-events.md)  
  
-   [Ereignisparameter](./event-parameters.md)  
  
-   [Zusammenwirken der Ereignishandler](./how-event-handlers-work-together.md)  
  
-   [ADO-Ereignisinstanziierung nach Sprache](./ado-event-instantiation-by-language.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-Ereignis Handler-Zusammenfassung](./ado-event-handler-summary.md)   
 [ADO-Ereignis Instanziierung nach Sprache](./ado-event-instantiation-by-language.md)   
 [ADO-Ereignisse](../../reference/ado-api/ado-events.md)   
 [Ereignis Parameter](./event-parameters.md)   
 [Ereignistypen](./types-of-events.md)