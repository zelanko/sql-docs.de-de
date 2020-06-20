---
title: 'Aufgabe 9: Erstellen einer abgeleiteten Hierarchie mit Master Data Manager | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 56e3d832fccbab849d0646c761964aee9266181e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85006205"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a>Aufgabe 9: Erstellen einer abgeleiteten Hierarchie mithilfe des Master Data Manager
  In dieser Aufgabe erstellen Sie eine abgeleitete Hierarchie mit Master Data Manager. Diese abgeleitete Hierarchie wird von den domänenbasierten Attribut Beziehungen zwischen den Entitäten " **Supplier** " und " **State** " abgeleitet.  
  
1.  Wechseln Sie zur Hauptseite **Master Data Manager** , indem Sie oben auf der Seite auf **SQL Server 2012 Master Data Services** klicken.  
  
2.  Klicken Sie im Abschnitt **administrative Aufgaben** auf **System Verwaltung** .  
  
3.  Zeigen Sie mit der Maus auf **Verwalten** in der Menüleiste, und klicken Sie auf **abgeleitete Hierarchien**.  
  
     ![Menü "Verwalten" – "Abgeleitete Hierarchien" ausgewählt](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "Menü "Verwalten" – "Abgeleitete Hierarchien" ausgewählt")  
  
4.  Klicken Sie auf der Symbolleiste auf **abgeleitete Hierarchie hinzufügen (+)** .  
  
     ![Abgeleitete Hierarchie hinzufügen (Schaltfläche)](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "Abgeleitete Hierarchie hinzufügen (Schaltfläche)")  
  
5.  Geben Sie **suppliersinstate** als **Namen der abgeleiteten Hierarchie**ein.  
  
6.  Klicken Sie in der Symbolleiste auf die Schaltfläche **Speichern** .  
  
     ![Abgeleitete Hierarchie speichern (Schaltfläche)](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "Abgeleitete Hierarchie speichern (Schaltfläche)")  
  
7.  Ziehen Sie **Supplier** von **Verfügbare Ebenen: suppliersinstate** auf **Current Levels: suppliersinstate**.  
  
     ![Auf aktueller Ebene verfügbare Entitäten und Hierarchien](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "Auf aktueller Ebene verfügbare Entitäten und Hierarchien")  
  
8.  Ziehen Sie den **Zustand** von **Verfügbare Ebenen: suppliersinstate** in **aktuelle Ebenen: suppliersinstate**. Der Bildschirm sollte die **aktuellen Ebenen** aufweisen, wie in der folgenden Abbildung dargestellt.  
  
     ![Aktuelle Ebenen und Vorschau der abgeleiteten Hierarchie](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "Aktuelle Ebenen und Vorschau der abgeleiteten Hierarchie")  
  
9. Erweitern Sie im **Vorschaufenster** den Eintrag **NY {New York}** , und Sie sollten einen Lieferanten in diesem Zustand sehen, wie in der obigen Abbildung gezeigt.  
  
10. Wechseln Sie zur Hauptseite **Master Data Manager** , indem Sie oben auf der Seite auf **SQL Server 2012 Master Data Services** klicken.  
  
11. Klicken Sie auf **Explorer**.  
  
12. Zeigen Sie mit der Maus auf **Hierarchien** , und klicken Sie auf **abgeleitet: suppliersinstate**.  
  
     ![Hierarchien – Abgeleitet: SuppliersInState (Menü)](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "Hierarchien – Abgeleitet: SuppliersInState (Menü)")  
  
13. Klicken Sie in der Struktur **Ansicht** auf einen beliebigen **Status** Knoten, und die Lieferanten in diesem Zustand werden im rechten Bereich angezeigt.  
  
     ![Abgeleitete Hierarchie im Explorer](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "Abgeleitete Hierarchie im Explorer")  
  
## <a name="next-step"></a>Nächster Schritt  
 [Lektion 5: Automatisierung der Bereinigung und des Abgleich mit SSIS](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  
