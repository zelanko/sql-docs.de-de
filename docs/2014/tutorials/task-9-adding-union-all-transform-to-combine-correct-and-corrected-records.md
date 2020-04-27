---
title: 'Aufgabe 9: Hinzufügen der Transformation für Union all zum kombinieren richtiger und korrigierter Datensätze | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 24ba466d-a7d3-49e7-9111-b348399c9e58
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 93b160b6e513ad866126df8b401b82ee1270be84
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "65489655"
---
# <a name="task-9-adding-union-all-transform-to-combine-correct-and-corrected-records"></a>Aufgabe 9: Hinzufügen der Transformation UNION ALL zur Kombination richtiger und korrigierter Datensätze
  In dieser Aufgabe fügen Sie dem Datenfluss die Transformation UNION ALL hinzu. Die Transformation für UNION ALL kombiniert mehrere Eingaben zu einer einzigen Ausgabe. In Ihrem Szenario kombiniert sie richtige und korrigierte Datensätze zu einem Datenstrom.  
  
1.  Ziehen Sie die Transformation **Union all** Transform aus **Common** section der **SSIS-Toolbox** auf die Registerkarte **Datenfluss** , und platzieren Sie Sie unter **richtige und korrigierte Datensätze auswählen**.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Union all** Transform auf der Registerkarte **Datenfluss** , und klicken Sie auf **Umbenennen** Geben **Sie** **richtige und korrigierte Datensätze zusammenfassen**ein  
  
     ![Kombinieren richtiger und korrigierter Datensätze](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "Kombinieren richtiger und korrigierter Datensätze")  
  
3.  Verbinden Sie **richtige und korrigierte Datensätze** , um **korrekte und korrigierte Datensätze** auf der Registerkarte " **Datenfluss** " mit dem blauen Connector zu kombinieren. Das Dialogfeld **Eingabe Ausgabe Auswahl** sollte angezeigt werden.  
  
4.  Wählen Sie im Dialogfeld **Eingabe Ausgabe** die Option für **Ausgabe** **korrigieren** aus, und klicken Sie auf **OK**.  
  
     ![Eingabe-/Ausgabe-Auswahl (Dialogfeld)](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "Eingabe-/Ausgabe-Auswahl (Dialogfeld)")  
  
5.  Verschieben Sie den Connector mit dem Titel **richtig** nach links, indem Sie den Punkt am Ende des Verbindungs Punkts nach links ziehen und ablegen.  
  
     ![Verbinden mit richtigen Datensätzen zum Kombinieren richtiger und korrigierter Datensätze](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "Verbinden mit richtigen Datensätzen zum Kombinieren richtiger und korrigierter Datensätze")  
  
6.  Wenn Sie Transformation für **richtige und korrigierte Datensätze** auswählen auswählen, sollte ein weiterer blauer Connector angezeigt werden. Ziehen Sie diesen blauen Connector, um **korrekte und korrigierte Datensätze zu kombinieren**  
  
     ![Verbinden mit korrigierten Datensätzen zum Kombinieren richtiger und korrigierter Datensätze](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "Verbinden mit korrigierten Datensätzen zum Kombinieren richtiger und korrigierter Datensätze")  
  
7.  Dieser **Connector** sollte mit dem Titel **korrigiert**versehen werden. Da nur zwei Bedingungen **korrekt** und **korrigiert**sind und bereits eine Bedingung verwendet wurde, wird das Dialogfeld Eingabe- **/ausgabeauswahl** nicht angezeigt. Wenn sich die Konnektoren überlappen, verschieben Sie einen nach links und den anderen nach rechts, indem Sie den Konnektor nach links bzw. rechts ziehen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 10: Hinzufügen der Transformation für Fuzzygruppierung zur Identifizierung von Duplikaten](../../2014/tutorials/task-10-adding-fuzzy-group-transform-to-identify-duplicates.md)  
  
  
