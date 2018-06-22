---
title: Schreiben einer Sitzung für erweiterte Ereignisse | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80f9fdde-1f13-4292-a4fc-55da826be3b4
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 71b9918e2f05efcc5a8720dcedeef023392f99ce
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060779"
---
# <a name="script-an-extended-event-session"></a>Schreiben einer Sitzung für erweiterte Ereignisse
  In diesem Thema wird beschrieben, wie ein Skript für eine Ereignissitzung geschrieben wird. Sie können die Ereignissitzung exportieren, ändern oder löschen, oder Sie können die Ereignissitzung wie folgt löschen und erstellen:  
  
-   **Neues Abfrage-Editor-Fenster**  
  
-   **File**  
  
-   **Zwischenablage**  
  
-   **-Agent-Auftrag**  
  
### <a name="to-script-an-existing-event-session"></a>So schreiben Sie ein Skript für eine vorhandene Ereignissitzung  
  
1.  Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung** , und erweitern Sie dann **Erweiterte Ereignisse**.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Sitzung, für die Sie ein Skript schreiben möchten, zeigen Sie auf **Skript für Sitzung als**, zeigen Sie auf **CREATE in**, und wählen Sie dann aus, wo das Skript für die Sitzung geschrieben werden soll.  
  
### <a name="to-script-a-new-event-session"></a>So schreiben Sie ein Skript für eine neue Ereignissitzung  
  
1.  Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung** , und erweitern Sie dann **Erweiterte Ereignisse**.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Sitzungen**, und klicken Sie dann auf **Neue Sitzung**.  
  
3.  Erstellen Sie in der Benutzeroberfläche **Neue Sitzung** die Ereignissitzung, und wählen Sie aus der Dropdownliste **Skript** aus, wo das Skript für die Ereignissitzung geschrieben werden soll.  
  
### <a name="to-script-a-modified-event-session"></a>So schreiben Sie ein Skript für eine geänderte Ereignissitzung  
  
1.  Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung** , und erweitern Sie dann **Erweiterte Ereignisse**.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Sitzung, den Sie ändern möchten, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Ändern Sie die Ereignissitzung im Dialogfeld **Sitzungseigenschaften** , und wählen Sie aus der Dropdownliste **Skript** aus, wo das Skript für die geänderte Sitzung geschrieben werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../relational-databases/extended-events/extended-events.md)  
  
  