---
title: 'Aufgabe 3: Erstellen und Ausführen von Data Quality-Projekten für den Abgleich | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 6260e911-ea8b-4c69-a39d-d1bccd565a32
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 00f4c86dd09dd9b88959415459151d4cef518d57
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099530"
---
# <a name="task-3-creating-and-running-a-data-quality-project-for-matching"></a>Aufgabe 3: Erstellen und Ausführen eines Data Quality-Projekts für den Abgleich
  In dieser Aufgabe erstellen Sie ein Data Quality-Projekt für die Abgleichsaktivität, und führen den Abgleichsprozess für bereinigte Lieferantendaten durch, um Duplikate in den Daten zu entfernen.  
  
1.  Klicken Sie auf der Hauptseite des **DQS-Client**, klicken Sie auf **neuen Data Quality-Projekt**.  
  
2.  Typ **Lieferantenduplikate entfernen+++** aus der **Name des Projekts**.  
  
3.  Wählen Sie **Lieferanten** aus der Liste der KBs für das **Wissensdatenbank verwenden** Feld. Sie haben eine Abgleichsrichtlinie in dieser Wissensdatenbank in der vorherigen Lektion erstellt.  
  
4.  Wählen Sie **übereinstimmende** aus der **Liste der Aktivitäten** aus dem Bereich unten rechts.  
  
     ![Neues Data Quality-Projekt - Abgleich ausgewählten](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "neuen Data Quality-Projekt - Abgleich ausgewählten")  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Wählen Sie auf der Seite **Zuordnen** für **Datenquelle** die Option **Excel-Datei**aus.  
  
7.  Klicken Sie auf **Durchsuchen** , und wählen Sie **Cleansed Supplier List.xls**, d.h., dass die Ausgabedatei aus der bereinigungsaktivität.  
  
8.  Zuordnung **SupplierID** Quellspalte, die **Supplier ID** Domäne **Supplier Name** Spalte **Supplier Name** Domänen- und **ContactEmailAddress** Spalte **Contact Email** Domäne.  
  
9. Klicken Sie auf **Weiter** zum Wechseln der **übereinstimmende** Seite.  
  
10. Klicken Sie auf **starten** um den Abgleichsprozess zu starten. Es sollten Ergebnisse angezeigt werden, die denen aus der vorherigen Aufgabe ähneln, da Sie dieselbe Eingabedatei zur Definition der Abgleichsrichtlinie verwendet haben.  
  
11. Prüfen Sie alle übereinstimmenden Datensätze und ihre Treffergenauigkeit im Listenfeld. Die Ergebnisse sollten denen aus der vorherigen Aufgabe entsprechen. Analysieren Sie die Ergebnisse aus dieser Abgleichsaktivität anhand der Schritte in der vorherigen Aufgabe.  
  
12. Klicken Sie auf **Weiter** zum Wechseln der **exportieren** Seite.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 4: Exportieren der Ergebnisse der Abgleichsaktivität in eine Excel-Datei](../../2014/tutorials/task-4-exporting-the-results-from-matching-activity-to-an-excel-file.md)  
  
  
