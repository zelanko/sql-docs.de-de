---
title: 'Aufgabe 8: Hinzufügen eines neuen Werts für die Entität "State" in Excel | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a763d76b-06a3-4d51-9614-01fc9fb1c158
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 831d0b504a65d485413772ee3711e689e29ee2a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489708"
---
# <a name="task-8-adding-a-new-value-for-state-entity-in-excel"></a>Aufgabe 8: Hinzufügen eines neuen Werts für die Entität 'State' in Excel
  In dieser Aufgabe fügen Sie einen Wert für die Entität "State" in Excel hinzu und veröffentlichen die Änderung auf dem MDS-Server.  
  
1.  Fügen Sie ein **Arbeitsblatt** in Excel hinzu, indem Sie unten auf die Registerkarte Neu klicken.  
  
     ![Excel – Neues Arbeitsblatt (Registerkarte)](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel – Neues Arbeitsblatt (Registerkarte)")  
  
2.  Klicken Sie in **Excel**im Menü auf die Registerkarte **Master Daten** , und klicken Sie dann auf dem Menüband auf **Explorer anzeigen** .  
  
3.  Wählen Sie im **Master Daten-Explorer** **Suppliers** für **Model**aus. Es sollten zwei Entitäten angezeigt werden: **Supplier** und **State** in der Liste der Entitäten.  
  
4.  Doppelklicken Sie in der Liste auf **Zustand** . Alle Member der **State** -Entität aus MDS sollten im Arbeitsblatt angezeigt werden.  
  
5.  Fügen Sie nun eine Zeile am Ende mit den folgenden Werten hinzu: **North Carolina** für **Name** und **NC** für **Code**. Die Farbcodierung unterscheidet alle neuen/aktualisierten Datensätze von den anderen Datensätzen.  
  
     ![Excel – Hinzufügen von North Carolina zu Bundesstaaten](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel – Hinzufügen von North Carolina zu Bundesstaaten")  
  
6.  Klicken Sie im Menüband auf **veröffentlichen** , um die Änderung in MDS zu veröffentlichen.  
  
     ![Excel – Schaltfläche "Veröffentlichen" auf der Registerkarte "Masterdaten"](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel – Schaltfläche "Veröffentlichen" auf der Registerkarte "Masterdaten"")  
  
7.  Beachten Sie, dass im Dialogfeld **veröffentlichen und mit Anmerkung** versehen die Option **dieselbe Anmerkung für alle Änderungen verwenden** ausgewählt ist. Hier können Sie eine einzige Anmerkung für alle Änderungen eingeben.  
  
8.  Wählen Sie die Option **Änderungen überprüfen und Anmerkungen einzeln bereitstellen** aus, um eine Anmerkung für jede Änderung bereitzustellen (in diesem Fall nur eine).  
  
     ![Excel – Veröffentlichen und mit Anmerkung versehen (Dialogfeld)](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel – Veröffentlichen und mit Anmerkung versehen (Dialogfeld)")  
  
9. Klicken Sie auf **veröffentlichen** , um die Daten in MDS zu veröffentlichen.  
  
10. Beachten Sie, dass die **Farbcodierung** für die Zeile mit **North Carolina** als **Zustand** mit anderen Datensätzen übereinstimmt.  
  
11. **Optional:** Überprüfen Sie, ob das neue Element (NC) zur Entität **State** hinzugefügt wird, indem Sie den **Explorer** in **Master Data Manager**verwenden.  
  
12. Klicken Sie in Excel im unteren Bereich mit der rechten Maustaste auf das Arbeitsblatt **State** , und klicken Sie auf **Löschen** , um das Arbeitsblatt zu löschen. Durch Löschen des Arbeitsblatts werden keine Daten vom MDS-Server gelöscht.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 9: Erstellen einer abgeleiteten Hierarchie mithilfe von Master Data Manager](../../2014/tutorials/task-9-creating-a-derived-hierarchy-using-master-data-manager.md)  
  
  
