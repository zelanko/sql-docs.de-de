---
title: Planen der Richtlinien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 59417a54-55f1-4468-ba41-368aa852c2d4
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8becd7ad30acf1ea2a63feae4760091aede70c06
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63033502"
---
# <a name="schedule-the-policies"></a>Planen der Richtlinien
  In dieser Aufgabe planen Sie die Best Practices-Richtlinien, die Sie in der vorherigen Aufgabe importiert haben.  
  
### <a name="to-schedule-the-best-practices-policies"></a>So planen Sie Best Practices-Richtlinien  
  
1.  Erweitern **Sie in**Objekt-Explorer den Knoten **Verwaltung**, erweitern Sie **Richtlinien Verwaltung**, erweitern Sie **Richtlinien**, klicken Sie mit der rechten Maustaste auf eine Richtlinie für bewährte Methoden, und klicken Sie  
  
    > [!NOTE]  
    >  Um die Best Practices-Kategorien zu sortieren und um einfach zu erkennen, welche Richtlinien zu Best Practices zugeordnet sind, können Sie alternativ **Verwaltung**und dann **Richtlinienverwaltung**erweitern und anschließend auf **Richtlinien**klicken. Klicken Sie im Menü **Ansicht** auf **Details zum Objekt-Explorer**. Klicken Sie im Bereich **Details zum Objekt-Explorer** auf die Überschrift **Kategorie** , um die Richtlinien nach Kategorie zu sortieren. Die Best Practices-Richtlinien sind mit dem Präfix **Microsoft Best Practices**versehen. Klicken Sie mit der rechten Maustaste auf die Richtlinie, die Sie konfigurieren möchten, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf der Seite **Allgemein** des Dialogfelds **Richtlinie öffnen** in der Liste **Auswertungsmodus** auf **Nach Zeitplan**.  
  
3.  Klicken Sie neben dem Feld **Zeitplan** auf **Auswählen** , um einen vorhandenen Zeitplan anzugeben, oder klicken Sie auf **Neu** , um einen neuen Zeitplan zu erstellen.  
  
4.  Nachdem Sie einen Zeitplan konfiguriert haben, können Sie zum Aktivieren der geplanten Richtlinie oben auf der Seite das Kontrollkästchen **Aktiviert** aktivieren.  
  
5.  Wiederholen Sie die Schritte 1 bis 4 für jede Richtlinie, die Sie planen möchten.  
  
    > [!NOTE]  
    >  Um nach der Ausführung einer geplanten Richtlinie die Auswertungsergebnisse anzuzeigen, öffnen Sie auf der Zielinstanz das Protokoll zum Richtlinienverlauf. Um das Protokoll zu öffnen, klicken Sie mit der rechten Maustaste auf **Richtlinien Verwaltung**, und klicken Sie dann auf **Verlauf anzeigen**.  
  
## <a name="summary"></a>Zusammenfassung  
 Sie haben geplante Richtlinien konfiguriert, die auf einer einzelnen Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ausgeführt werden. Wenn Sie geplante Richtlinien auf mehreren Instanzen bereitstellen möchten, setzen Sie das Lernprogramm mit der nächsten Aufgabe fort.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Bereitstellen geplanter Richtlinien auf mehreren Instanzen](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
  
