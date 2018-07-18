---
title: Planen der Richtlinien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 59417a54-55f1-4468-ba41-368aa852c2d4
caps.latest.revision: 5
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: c328073f25c27ff05b8b6edbd79a56ad1fda85ab
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37315130"
---
# <a name="schedule-the-policies"></a>Planen der Richtlinien
  In dieser Aufgabe planen Sie die Best Practices-Richtlinien, die Sie in der vorherigen Aufgabe importiert haben.  
  
### <a name="to-schedule-the-best-practices-policies"></a>So planen Sie Best Practices-Richtlinien  
  
1.  Erweitern Sie im Objekt-Explorer **Management**, erweitern Sie **richtlinienverwaltung**, erweitern Sie **Richtlinien**mit der rechten Maustaste auf eine best Practices-Richtlinie, und klicken Sie dann auf  **Eigenschaften**.  
  
    > [!NOTE]  
    >  Um die Best Practices-Kategorien zu sortieren und um einfach zu erkennen, welche Richtlinien zu Best Practices zugeordnet sind, können Sie alternativ **Verwaltung**und dann **Richtlinienverwaltung**erweitern und anschließend auf **Richtlinien**klicken. Klicken Sie im Menü **Ansicht** auf **Details zum Objekt-Explorer**. Klicken Sie im Bereich **Details zum Objekt-Explorer** auf die Überschrift **Kategorie** , um die Richtlinien nach Kategorie zu sortieren. Die Best Practices-Richtlinien sind mit dem Präfix **Microsoft Best Practices**versehen. Mit der rechten Maustaste in der Richtlinie, die Sie konfigurieren möchten, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf der Seite **Allgemein** des Dialogfelds **Richtlinie öffnen** in der Liste **Auswertungsmodus** auf **Nach Zeitplan**.  
  
3.  Klicken Sie neben dem Feld **Zeitplan** auf **Auswählen** , um einen vorhandenen Zeitplan anzugeben, oder klicken Sie auf **Neu** , um einen neuen Zeitplan zu erstellen.  
  
4.  Nachdem Sie einen Zeitplan konfiguriert haben, können Sie zum Aktivieren der geplanten Richtlinie oben auf der Seite das Kontrollkästchen **Aktiviert** aktivieren.  
  
5.  Wiederholen Sie die Schritte 1 bis 4 für jede Richtlinie, die Sie planen möchten.  
  
    > [!NOTE]  
    >  Um nach der Ausführung einer geplanten Richtlinie die Auswertungsergebnisse anzuzeigen, öffnen Sie auf der Zielinstanz das Protokoll zum Richtlinienverlauf. Öffnen das Protokoll, mit der Maustaste **richtlinienverwaltung**, und klicken Sie dann auf **Versionsgeschichte**.  
  
## <a name="summary"></a>Zusammenfassung  
 Sie haben geplante Richtlinien konfiguriert, die auf einer einzelnen Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ausgeführt werden. Wenn Sie geplante Richtlinien auf mehreren Instanzen bereitstellen möchten, setzen Sie das Lernprogramm mit der nächsten Aufgabe fort.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Bereitstellen geplanter Richtlinien auf mehreren Instanzen](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
  
