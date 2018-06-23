---
title: 'Aufgabe 3: Erstellen und Ausführen eines Quality-Projekts für den Abgleich | Microsoft Docs'
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
ms.assetid: 6260e911-ea8b-4c69-a39d-d1bccd565a32
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2080aac8b429a9bc3ae21313f2163316b6cebeae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162588"
---
# <a name="task-3-creating-and-running-a-data-quality-project-for-matching"></a>Aufgabe 3: Erstellen und Ausführen eines Data Quality-Projekts für den Abgleich
  In dieser Aufgabe erstellen Sie ein Data Quality-Projekt für die Abgleichsaktivität, und führen den Abgleichsprozess für bereinigte Lieferantendaten durch, um Duplikate in den Daten zu entfernen.  
  
1.  Auf der Hauptseite des **DQS-Client**, klicken Sie auf **neue Data Quality-Projekt**.  
  
2.  Typ **Lieferantenduplikate entfernen+++** aus der **Name des Projekts**.  
  
3.  Wählen Sie **Lieferanten** aus der Liste der KBs für die **Wissensdatenbank verwenden** Feld. Sie haben eine Abgleichsrichtlinie in dieser Wissensdatenbank in der vorherigen Lektion erstellt.  
  
4.  Wählen Sie **Abgleich** aus der **Liste der Aktivitäten** aus dem Bereich unten rechts.  
  
     ![Neue Data Quality-Projekt - Abgleich ausgewählten](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "neue Data Quality-Projekt - Abgleich ausgewählten")  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Wählen Sie auf der Seite **Zuordnen** für **Datenquelle** die Option **Excel-Datei**aus.  
  
7.  Klicken Sie auf **Durchsuchen** , und wählen Sie **Cleansed Supplier List.xls**, also in die Ausgabedatei aus der bereinigungsaktivität.  
  
8.  Zuordnung **SupplierID** Quellspalte, die **Supplier ID** Domäne **Supplier Name** Spalte **Lieferantenname** Domäne und **ContactEmailAddress** Spalte **Contact Email** Domäne.  
  
9. Klicken Sie auf **Weiter** So wechseln Sie zu der **Abgleich** Seite.  
  
10. Klicken Sie auf **starten** um den Abgleichsprozess zu starten. Es sollten Ergebnisse angezeigt werden, die denen aus der vorherigen Aufgabe ähneln, da Sie dieselbe Eingabedatei zur Definition der Abgleichsrichtlinie verwendet haben.  
  
11. Prüfen Sie alle übereinstimmenden Datensätze und ihre Treffergenauigkeit im Listenfeld. Die Ergebnisse sollten denen aus der vorherigen Aufgabe entsprechen. Analysieren Sie die Ergebnisse aus dieser Abgleichsaktivität anhand der Schritte in der vorherigen Aufgabe.  
  
12. Klicken Sie auf **Weiter** So wechseln Sie zu der **exportieren** Seite.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 4: Exportieren der Ergebnisse der Abgleichsaktivität in eine Excel-Datei](../../2014/tutorials/task-4-exporting-the-results-from-matching-activity-to-an-excel-file.md)  
  
  