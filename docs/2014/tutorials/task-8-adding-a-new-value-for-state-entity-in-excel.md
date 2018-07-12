---
title: "Aufgabe 8: Hinzufügen eines neuen Werts für die Entität ' State ' in Excel | Microsoft-Dokumentation"
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
ms.topic: conceptual
ms.assetid: a763d76b-06a3-4d51-9614-01fc9fb1c158
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4f4e79915ba28beb7cd28920faff2f79e6b339d6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163771"
---
# <a name="task-8-adding-a-new-value-for-state-entity-in-excel"></a>Aufgabe 8: Hinzufügen eines neuen Werts für die Entität 'State' in Excel
  In dieser Aufgabe fügen Sie einen Wert für die Entität "State" in Excel hinzu und veröffentlichen die Änderung auf dem MDS-Server.  
  
1.  Hinzufügen einer **Arbeitsblatt** in Excel, indem Sie auf die neue Registerkarte am unteren Rand.  
  
     ![Excel – neues Arbeitsblatt-Registerkarte](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel – neues Arbeitsblatt-Registerkarte")  
  
2.  In **Excel**, klicken Sie auf die **Masterdaten** auf das Menü, und klicken Sie dann auf **Explorer anzeigen** auf dem Menüband.  
  
3.  In der **Master Data Explorer**Option **Lieferanten** für **Modell**. Sie sollten zwei Entitäten zu sehen: **Lieferanten** und **Zustand** in der Liste.  
  
4.  Doppelklicken Sie auf **Zustand** in der Liste. Alle Mitglieder der **Zustand** Entität aus MDS in das Arbeitsblatt angezeigt werden soll.  
  
5.  Fügen Sie nun eine Zeile am Ende mit den folgenden Werten: **North Carolina** für **Namen** und **NC** für **Code**. Die Farbcodierung unterscheidet alle neuen/aktualisierten Datensätze von den anderen Datensätzen.  
  
     ![Excel – Hinzufügen von North Carolina Status](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel – Hinzufügen von North Carolina Status")  
  
6.  Klicken Sie auf **veröffentlichen** auf dem Menüband, um die Änderung in MDS zu veröffentlichen.  
  
     ![Excel – Schaltfläche auf der Registerkarte "Daten" Master "Veröffentlichen"](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel – Schaltfläche auf der Registerkarte \"Daten\" Master \"Veröffentlichen\"")  
  
7.  Auf der **veröffentlichen und mit Anmerkung versehen** Dialogfeld Beachten Sie, dass die **verwenden Sie dieselbe Anmerkung für alle Änderungen** ausgewählt ist. Hier können Sie eine einzige Anmerkung für alle Änderungen eingeben.  
  
8.  Wählen Sie **Änderungen überprüfen und Anmerkungen einzeln bereitstellen** Option aus, um die Anmerkung für jede Änderung (in diesem Fall einzigen) bereitstellen.  
  
     ![Excel – veröffentlichen und mit Anmerkungen versehen Sie im Dialogfeld](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel – veröffentlichen und mit Anmerkungen versehen (Dialogfeld)")  
  
9. Klicken Sie auf **veröffentlichen** , Daten in MDS zu veröffentlichen.  
  
10. Beachten Sie, dass **farbcodierung** für die Zeile mit **North Carolina** als die **Zustand** jetzt anderen Datensätzen identisch ist.  
  
11. **Optional:** stellen Sie sicher, das das neue Element (NC) hinzugefügt wird, die **Zustand** Entität mithilfe der **Explorer** in **Master Data Manager**.  
  
12. In Excel, mit der Maustaste der **Zustand** Arbeitsblatt unten enthält, und klicken Sie auf **löschen** auf das Arbeitsblatt zu löschen. Durch Löschen des Arbeitsblatts werden keine Daten vom MDS-Server gelöscht.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 9: Erstellen einer abgeleiteten Hierarchie mithilfe von Master Data Manager](../../2014/tutorials/task-9-creating-a-derived-hierarchy-using-master-data-manager.md)  
  
  
