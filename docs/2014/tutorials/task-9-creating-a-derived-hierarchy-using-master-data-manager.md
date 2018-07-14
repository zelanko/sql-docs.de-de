---
title: 'Aufgabe 9: Erstellen einer abgeleiteten Hierarchie mit Master Data Manager | Microsoft-Dokumentation'
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
ms.topic: conceptual
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 22aba36efffe3b4e15d358e6077bb6b58e7aa328
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273586"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a>Aufgabe 9: Erstellen einer abgeleiteten Hierarchie mithilfe von Master Data Manager
  In dieser Aufgabe erstellen Sie eine abgeleitete Hierarchie mit Master Data Manager. Diese abgeleitete Hierarchie wird abgeleitet von den domänenbasierten attributbeziehungen zwischen dem **Lieferanten** und **Zustand** Entitäten.  
  
1.  Wechseln Sie zur Hauptseite des **Master Data Manager** durch Klicken auf **SQL Server 2012 Master Data Services** am oberen Rand der Seite.  
  
2.  Klicken Sie auf **Systemverwaltung** in die **Verwaltungsaufgaben** Abschnitt.  
  
3.  Zeigen Sie auf den **verwalten** auf der Menüleiste, und klicken Sie auf **abgeleitete Hierarchien**.  
  
     ![Verwalten von Menü - abgeleitete Hierarchien, die ausgewählten](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "verwalten im Menü - abgeleitete Hierarchien ausgewählt")  
  
4.  Klicken Sie auf **abgeleitete Hierarchie hinzufügen (+)** auf der Symbolleiste.  
  
     ![Abgeleitete Hierarchie Schaltfläche "hinzufügen"](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "abgeleitete Hierarchie Schaltfläche \"hinzufügen\"")  
  
5.  Typ **SuppliersInState** für die **Name der abgeleiteten Hierarchie**.  
  
6.  Klicken Sie auf **speichern** auf der Symbolleiste.  
  
     ![Abgeleitete Hierarchie Schaltfläche Speichern](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "abgeleitete Schaltfläche Hierarchie speichern")  
  
7.  Ziehen Sie **Lieferanten** aus **verfügbare Ebenen: SuppliersInState** zu **aktuelle Ebenen: SuppliersInState**.  
  
     ![Aktueller-Entitäten und Hierarchien auf aktuelle](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "aktueller-Entitäten und Hierarchien auf aktuelle")  
  
8.  Ziehen Sie **Zustand** aus **verfügbare Ebenen: SuppliersInState** zu **aktuelle Ebenen: SuppliersInState**. Der Bildschirm müssen **aktuelle Ebenen** wie in der folgenden Abbildung dargestellt.  
  
     ![Aktuelle Ebenen und Vorschau der abgeleiteten Hierarchie](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "aktuelle Ebenen und Vorschau der abgeleiteten Hierarchie")  
  
9. In der **Vorschau** Fenster erweitern **NY {New York}+++}** und ein Lieferant in diesem Zustand sollte angezeigt werden, wie in der vorherigen Abbildung dargestellt.  
  
10. Wechseln Sie zur Hauptseite des **Master Data Manager** durch Klicken auf **SQL Server 2012 Master Data Services** am oberen Rand der Seite.  
  
11. Klicken Sie auf **Explorer**.  
  
12. Zeigen Sie auf den **Hierarchien** , und klicken Sie auf **abgeleitet: SuppliersInState**.  
  
     ![Hierarchien – abgeleitet: SuppliersInState Menü](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "Hierarchien – abgeleitet: SuppliersInState-Menü")  
  
13. Klicken Sie auf einen **Zustand** Knoten in der **Strukturansicht** sollte die Lieferanten in diesem Bundesstaat im rechten Bereich angezeigt.  
  
     ![Abgeleitete Hierarchie im Explorer](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "abgeleitete Hierarchie im Explorer")  
  
## <a name="next-step"></a>Nächster Schritt  
 [Lektion 5: Automatisierung der Bereinigung und des Abgleich mit SSIS](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  
