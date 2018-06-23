---
title: 'Aufgabe 9: Erstellen einer abgeleiteten Hierarchie mithilfe von Master Data Manager | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 35584d33afac7a2a8f74abd013288a974cade512
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162821"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a>Aufgabe 9: Erstellen einer abgeleiteten Hierarchie mithilfe von Master Data Manager
  In dieser Aufgabe erstellen Sie eine abgeleitete Hierarchie mit Master Data Manager. Diese abgeleitete Hierarchie wird abgeleitet von den domänenbasierten attributbeziehungen zwischen dem **Lieferanten** und **Zustand** Entitäten.  
  
1.  Wechseln Sie zur Hauptseite des **Master Data Manager** durch Klicken auf **SQL Server 2012 Master Data Services** am oberen Rand der Seite.  
  
2.  Klicken Sie auf **Systemverwaltung** in der **Verwaltungsaufgaben** Abschnitt.  
  
3.  Zeigen Sie mit der Maus auf **verwalten** auf der Menüleiste, und klicken Sie auf **abgeleitete Hierarchien**.  
  
     ![Menü - abgeleitete Hierarchien ausgewählt "verwalten"](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "Menü - abgeleitete Hierarchien ausgewählt \"verwalten\"")  
  
4.  Klicken Sie auf **abgeleitete Hierarchie hinzufügen (+)** auf der Symbolleiste.  
  
     ![Abgeleitete Hierarchie Schaltfläche "hinzufügen"](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "abgeleitete Hierarchie Schaltfläche \"hinzufügen\"")  
  
5.  Typ **SuppliersInState** für die **Name der abgeleiteten Hierarchie**.  
  
6.  Klicken Sie auf **speichern** auf der Symbolleiste.  
  
     ![Speichern abgeleitete Hierarchie Schaltfläche](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "speichern abgeleitete Hierarchie-Schaltfläche")  
  
7.  Ziehen Sie **Lieferanten** aus **verfügbare Ebenen: SuppliersInState** auf **aktuelle Ebenen: SuppliersInState**.  
  
     ![Aktueller Entitäten und Hierarchien auf aktuelle](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "aktueller Entitäten und Hierarchien auf aktuelle")  
  
8.  Ziehen Sie **Status** aus **verfügbare Ebenen: SuppliersInState** auf **aktuelle Ebenen: SuppliersInState**. Der Bildschirm müsste **aktuelle Ebenen** wie im folgenden Bild gezeigt.  
  
     ![Aktuelle Ebenen und Vorschau der abgeleiteten Hierarchie](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "aktuelle Ebenen und Vorschau der abgeleiteten Hierarchie")  
  
9. In der **Vorschau** Fenster, erweitern Sie **NY {New York}+++}** und ein Lieferant in diesem Status sollte angezeigt werden, wie in der vorherigen Abbildung dargestellt.  
  
10. Wechseln Sie zur Hauptseite des **Master Data Manager** durch Klicken auf **SQL Server 2012 Master Data Services** am oberen Rand der Seite.  
  
11. Klicken Sie auf **Explorer**.  
  
12. Zeigen Sie mit der Maus auf **Hierarchien** , und klicken Sie auf **abgeleitet: SuppliersInState**.  
  
     ![Hierarchien – abgeleitet: SuppliersInState Menü](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "Hierarchien – abgeleitet: SuppliersInState-Menü")  
  
13. Klicken Sie auf eine **Status** Knoten in der **Strukturansicht** und Lieferanten in diesem Bundesstaat im rechten Bereich angezeigt.  
  
     ![Abgeleitete Hierarchie im Explorer](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "abgeleitete Hierarchie im Explorer")  
  
## <a name="next-step"></a>Nächster Schritt  
 [Lektion 5: Automatisierung der Bereinigung und des Abgleich mit SSIS](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  