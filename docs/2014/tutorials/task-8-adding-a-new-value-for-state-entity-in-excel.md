---
title: "Aufgabe 8: Hinzufügen eines neuen Werts für die Entität ' State ' in Excel | Microsoft Docs"
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a763d76b-06a3-4d51-9614-01fc9fb1c158
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: db2eaccd4d9b344cbc1b7c25b6fec940ff9c77a9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151702"
---
# <a name="task-8-adding-a-new-value-for-state-entity-in-excel"></a>Aufgabe 8: Hinzufügen eines neuen Werts für die Entität 'State' in Excel
  In dieser Aufgabe fügen Sie einen Wert für die Entität "State" in Excel hinzu und veröffentlichen die Änderung auf dem MDS-Server.  
  
1.  Hinzufügen einer **Arbeitsblatt** in Excel, indem Sie auf die neue Registerkarte unten.  
  
     ![Excel - Arbeitsblattregisterkarte](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel - Arbeitsblattregisterkarte")  
  
2.  In **Excel**, klicken Sie auf die **Masterdaten** Registerkarte auf das Menü, und klicken Sie dann auf **Explorer anzeigen** auf dem Menüband.  
  
3.  In der **Master Data Explorer**Option **Lieferanten** für **Modell**. Sie sollten zwei Entitäten finden Sie unter: **Lieferanten** und **Zustand** in der Liste.  
  
4.  Doppelklicken Sie auf **Zustand** in der Liste. Alle Member der **Zustand** Entität aus MDS sollten im Arbeitsblatt angezeigt werden.  
  
5.  Fügen Sie nun eine Zeile am Ende mit den folgenden Werten: **North Carolina** für **Namen** und **NC** für **Code**. Die Farbcodierung unterscheidet alle neuen/aktualisierten Datensätze von den anderen Datensätzen.  
  
     ![Excel – Hinzufügen von North Carolina zu Bundesstaaten](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel – Hinzufügen von North Carolina zu Bundesstaaten")  
  
6.  Klicken Sie auf **veröffentlichen** auf dem Menüband auf die Änderung in MDS zu veröffentlichen.  
  
     ![Excel – Schaltfläche auf der Registerkarte "Daten" Master "Veröffentlichen"](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel – Schaltfläche auf der Registerkarte \"Daten\" Master \"Veröffentlichen\"")  
  
7.  Auf der **veröffentlichen und mit Anmerkung versehen** Dialogfeld Beachten Sie, dass die **verwenden Sie dieselbe Anmerkung für alle Änderungen** ausgewählt ist. Hier können Sie eine einzige Anmerkung für alle Änderungen eingeben.  
  
8.  Wählen Sie **Änderungen überprüfen und Anmerkungen einzeln bereitstellen** Option aus, um die Anmerkung für jede Änderung (in diesem Fall nur eine) bereitstellen.  
  
     ![Excel – veröffentlichen und mit einer Anmerkung versehen (Dialogfeld)](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel – veröffentlichen und mit einer Anmerkung versehen (Dialogfeld)")  
  
9. Klicken Sie auf **veröffentlichen** , Daten in MDS zu veröffentlichen.  
  
10. Beachten Sie, dass **farbcodierung** für die Zeile mit **North Carolina** als die **Zustand** jetzt anderen Datensätzen identisch ist.  
  
11. **Optional:** stellen Sie sicher, das das neue Element (NC) hinzugefügt wird, die **Status** Entität mithilfe der **Explorer** in **Master Data Manager**.  
  
12. In Excel, mit der Maustaste die **Status** Arbeitsblatt am unten, und klicken Sie auf **löschen** auf das Arbeitsblatt zu löschen. Durch Löschen des Arbeitsblatts werden keine Daten vom MDS-Server gelöscht.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 9: Erstellen einer abgeleiteten Hierarchie mithilfe von Master Data Manager](../../2014/tutorials/task-9-creating-a-derived-hierarchy-using-master-data-manager.md)  
  
  