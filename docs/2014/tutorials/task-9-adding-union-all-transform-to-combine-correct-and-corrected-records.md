---
title: 'Aufgabe 9: Hinzufügen von Union All Transformation, um richtige und korrigierte Datensätze zu kombinieren | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 24ba466d-a7d3-49e7-9111-b348399c9e58
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8900b595bcb90eb7ca0712d2b6e7e3010c4a7b24
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48180910"
---
# <a name="task-9-adding-union-all-transform-to-combine-correct-and-corrected-records"></a>Aufgabe 9: Hinzufügen der Transformation UNION ALL, um richtige und korrigierte Datensätze zu kombinieren
  In dieser Aufgabe fügen Sie dem Datenfluss die Transformation UNION ALL hinzu. Die Transformation für UNION ALL kombiniert mehrere Eingaben zu einer einzigen Ausgabe. In Ihrem Szenario kombiniert sie richtige und korrigierte Datensätze zu einem Datenstrom.  
  
1.  Drag & Drop **Union All** Transformationen von **Common** Teil der **SSIS-Toolbox** auf die **Datenfluss** Registerkarte, und platzieren Sie es unter **Wählen Sie die richtige und korrigierte Datensätze**.  
  
2.  Mit der rechten Maustaste **Union All** transformiert die **Datenfluss** Registerkarte, und klicken Sie auf **umbenennen**. Typ **Combine Correct and Corrected Records**, und drücken Sie die **EINGABETASTE**.  
  
     ![Kombinieren richtiger und korrigierter Datensätze korrigierter Datensätze](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "kombinieren richtiger und korrigierter Datensätze korrigierter Datensätze")  
  
3.  Herstellen einer mit **Pick Correct and Corrected Records** zu **Combine Correct and Corrected Records** in die **Datenfluss** Registerkarte mithilfe des blauen Konnektors. Daraufhin sollte die **Eingabe/Ausgabe-Auswahl** Dialogfeld.  
  
4.  In der **e/a** wählen Sie im Dialogfeld **richtig** für **Ausgabe** , und klicken Sie auf **OK**.  
  
     ![Geben Sie im Dialogfeld Ausgabe](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "Eingabe Ausgabe Spaltenauswahl (Dialogfeld)")  
  
5.  Verschieben Sie den Konnektor mit der Bezeichnung **richtig** links per Drag & Drop den Punkt am Ende des Konnektors nach links.  
  
     ![Herstellen einer mit richtigen Datensätzen zum Kombinieren richtiger und korrigierter Datensätze](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "Herstellen einer mit richtigen Datensätzen zum Kombinieren richtiger und korrigierter Datensätze")  
  
6.  Bei Auswahl von **Pick Correct and Corrected Records** transformieren, sollte ein weiterer blauen Konnektor angezeigt werden. Ziehen Sie diesen blauen Konnektor zu **Combine Correct and Corrected Records**.  
  
     ![Verbinden mit korrigierten Datensätzen zum Kombinieren richtiger und korrigierter Datensätze](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "Verbinden mit korrigierten Datensätzen zum Kombinieren richtiger und korrigierter Datensätze")  
  
7.  Dies **Connector** sollte die Bezeichnung **korrigiert**. Da Sie nur zwei Bedingungen vorliegen **richtig** und **korrigiert**, und eine Bedingung bereits verwendet wurde, wird die **Eingabe/Ausgabe-Auswahl** diesmal im Dialogfeld nicht angezeigt. Wenn sich die Konnektoren überlappen, verschieben Sie einen nach links und den anderen nach rechts, indem Sie den Konnektor nach links bzw. rechts ziehen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 10: Hinzufügen der Transformation für Fuzzygruppierung, um Duplikate zu identifizieren](../../2014/tutorials/task-10-adding-fuzzy-group-transform-to-identify-duplicates.md)  
  
  
