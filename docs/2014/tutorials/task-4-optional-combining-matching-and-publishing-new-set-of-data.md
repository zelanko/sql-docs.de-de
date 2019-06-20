---
title: 'Aufgabe 4 (optional): Kombination, Abgleich und Veröffentlichung eines neuen Satz von Daten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 13a13f03-b307-4555-8e33-6d98c459d994
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 2d27a5bcd87ffd84b33de229d955dc9494846a72
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65489273"
---
# <a name="task-4-optional-combining-matching-and-publishing-new-set-of-data"></a>Aufgabe 4 (optional): Kombination, Abgleich und Veröffentlichung eines neuen Datensatzes
  Es ist möglich, dass Sie dem MDS-Repository im Laufe der Zeit weitere Daten hinzufügen möchten. Bevor Sie Daten hinzufügen, kann es hilfreich sein, die neuen Daten an die Daten verglichen werden soll, die bereits in MDS, um sicherzustellen, dass Sie keine doppelte oder ungenaue Daten hinzufügen, werden verwaltet wird. Im Master Data Services-Add-In für Excel können Sie Daten aus zwei Arbeitsblättern kombinieren und die Daten dann vergleichen, um Duplikate zu identifizieren und zu entfernen, bevor Sie die Daten in MDS veröffentlichen. Die Abgleichsfunktion des MDS-Add-Ins für Excel verwendet die DQS-Abgleichsfunktionalität, um Übereinstimmungen in den Daten zu identifizieren. In dieser Aufgabe kombinieren Sie Daten aus zwei Arbeitsblättern in einem Arbeitsblatt und führen dann die Abgleichsaktivität aus, um Duplikate zu identifizieren und zu entfernen, bevor Sie die Daten in MDS veröffentlichen. Finden Sie unter [Data Quality-Abgleich im MDS-Add-in für Excel](https://msdn.microsoft.com/library/hh548681.aspx) und [Kombinieren von Daten](https://msdn.microsoft.com/library/hh548680.aspx) Themen Weitere Informationen.  
  
1.  Starten Sie die neue Instanz der **Excel**. Klicken Sie auf **starten**, zeigen Sie auf **ausführen**, Typ **Excel**, und klicken Sie auf **OK**.  
  
2.  Wechseln Sie zu der **Masterdaten** Registerkarte, indem Sie auf **Masterdaten** in der Menüleiste.  
  
3.  Klicken Sie auf **Connect** auf dem Menüband in die **verbinden und laden** Gruppe für die Verbindung der **MDS-Server**. Sie haben diese Verbindung zuvor in dieser Lektion konfiguriert.  
  
     ![Excel – Schaltfläche "Explorer" auf Masterdaten anzeigen](../../2014/tutorials/media/et-combinematchandpublishnewsod-01.jpg "Excel – Schaltfläche \"Explorer\" auf Masterdaten anzeigen")  
  
4.  Daraufhin sollte die **Master Data Explorer** rechts. Wenn Sie die Master Data Explorer nicht angezeigt werden, klicken Sie auf **Explorer anzeigen** Schaltfläche auf dem Menüband.  
  
5.  In der **Master Data Explorer** , wählen Sie im Fenster **Lieferanten** in der Dropdown-Liste für die **Modell**. Sollte angezeigt werden, dass das Modell eine Entität verfügt: **Lieferanten**.  
  
     ![Excel – Master Data Explorer-Fenster](../../2014/tutorials/media/et-combinematchandpublishnewsod-02.jpg "Excel – Master Data Explorer-Fenster")  
  
6.  Doppelklicken Sie auf **Lieferanten** in der Liste der Entität, die Entitätselemente in das Excel-Arbeitsblatt zu laden.  
  
7.  Klicken Sie auf **Tabelle2** unten, um zum Wechseln der **Tabelle2** Registerkarte. Wenn Sie nicht sehen **Tabelle2**, fügen Sie ein neues Arbeitsblatt hinzu.  
  
8.  Open **Suppliers.xls** Datei (die ursprüngliche Eingabedatei, die in den Lernprogrammdateien enthalten ist), und kopieren Sie alle (drei) Zeilen aus der **CombineAndCleanse** Arbeitsblatt **Tabelle2**.  
  
9. Wechseln Sie zurück zu der **Lieferanten** Stylesheets in die **Mappe1 - Microsoft Excel** (nicht die **Cleansed and Lieferantenliste abgeglichen** Excel), verbunden ist **MDS**.  
  
10. Klicken Sie auf **Masterdaten** in der Menüleiste.  
  
11. Klicken Sie auf **Kombinieren von Daten** auf dem Menüband. Sie sehen die **Kombinieren von Daten** Dialogfeld.  
  
12. In der **Kombinieren von Daten** Dialogfeld klicken Sie auf die Schaltfläche neben **mit MDS-Daten zu kombinierender Bereich** Textfeld wie in der folgenden Abbildung dargestellt.  
  
     ![Excel – Daten (Dialogfeld) kombinieren](../../2014/tutorials/media/et-combinematchandpublishnewsod-03.jpg "Excel – Kombinieren von Daten (Dialogfeld)")  
  
13. Das Dialogfeld sollte jetzt verkleinert angezeigt werden. Klicken Sie nun **Tabelle2** So wechseln Sie zu der **Tabelle2** Registerkarte, die über die neuen Lieferantendaten mit 4 Zeilen (einschließlich Kopfzeile) verfügt.  
  
14. In der **Tabelle2**Option **alle Zeilen, einschließlich der Kopfzeile** (selbst wenn diese scheinbar bereits ausgewählt sein). Daraufhin sollte die **mit MDS-Daten zu kombinierender Bereich** wird automatisch aktualisiert.  
  
     ![Excel – Kombinieren von Daten (Dialogfeld) – minimiert](../../2014/tutorials/media/et-combinematchandpublishnewsod-04.jpg "Excel – Kombinieren von Daten (Dialogfeld) – minimiert")  
  
15. Wechseln Sie zurück zu den **Lieferanten** Registerkarte ohne zu schließen die **Kombinieren von Daten** Dialogfeld.  
  
16. Klicken Sie auf die **Schaltfläche** neben der **Textfeld**. Das Dialogfeld sollte jetzt erweitert angezeigt werden. Sollte angezeigt werden alle Zuordnungen zwischen den Spalten der **Lieferanten** MDS **Entität** zu **Excel** Spalten werden automatisch aufgefüllt.  
  
     ![Excel – Kombinieren von Daten (Dialogfeld), die mit Daten gefüllt](../../2014/tutorials/media/et-combinematchandpublishnewsod-05.jpg "Excel – Kombinieren von Daten (Dialogfeld), die mit Daten gefüllt")  
  
17. Sicherstellen, dass **Code** entitätsspalte auf die **SupplierID** Spalte im Arbeitsblatt und **Postleitzahl** entitätsspalte auf die **Postleitzahl** Spalte im Arbeitsblatt.  
  
18. Auf der **Kombinieren von Daten** Dialogfeld klicken Sie auf **kombinieren**.  
  
19. Überprüfen Sie, ob drei Datenzeilen am Ende des Arbeitsblatts hinzugefügt wurden und ob diese farblich codiert sind.  
  
     ![Excel – neue Elemente nach dem vereinen](../../2014/tutorials/media/et-combinematchandpublishnewsod-06.jpg "Excel – neue Elemente nach dem vereinen")  
  
20. Klicken Sie auf **Daten abgleichen** auf dem Menüband, um Duplikate zu identifizieren. Diese Funktion verwendet die Abgleichsfunktionalität von DQS.  
  
21. In der **Daten abgleichen** wählen Sie im Dialogfeld **Lieferanten** für **DQS-Wissensdatenbank**.  
  
     ![Excel – Dialogfeld Übereinstimmung](../../2014/tutorials/media/et-combinematchandpublishnewsod-07.jpg "Excel - Übereinstimmung Daten (Dialogfeld)")  
  
22. Ordnen Sie Arbeitsblattspalten Domänen zu, wie in der folgenden Tabelle gezeigt.  
  
    |Arbeitsblattspalte|Domäne|  
    |----------------------|------------|  
    |Code (Sie haben "Supplier ID" als Code für die Entität "Supplier" in MDS hochgeladen)|Supplier ID|  
    |Name (Sie haben "Supplier Name" als Name für die Entität "Supplier" in MDS hochgeladen)|Supplier Name|  
    |ContactEmailAddress|ContactEmail|  
  
23. Wählen Sie **erforderliche** für die **Code** spaltenzuordnung.  
  
24. Geben Sie **70 %** als die **Gewichtung** für **Lieferantenname** und **30 %** als die **Gewichtung** für **Contact Email** wie in der Abbildung dargestellt.  
  
25. Klicken Sie auf **OK**.  
  
26. Der Abgleichsprozess sollte ein Duplikat identifizieren, für den Lieferanten mit **Code: S1**.  
  
     ![Excel – Abgleichsergebnisse](../../2014/tutorials/media/et-combinematchandpublishnewsod-08.jpg "Excel – Abgleichsergebnisse")  
  
27. Wählen Sie die **doppelte Zeile (orangefarben)**, mit der rechten Maustaste, und klicken Sie auf **löschen** zum Löschen der Zeile.  
  
28. Löschen der **CLUSTER_ID** Spalte, da Sie es nicht mehr benötigen.  
  
29. Klicken Sie auf **veröffentlichen** veröffentlichen die anderen zwei neuen Datensätze mit **Codes S66** und **S57** in MDS.  
  
30. In der **veröffentlichen und mit Anmerkung versehen** Dialogfeld hinzu, und ein **Anmerkung**, und klicken Sie auf **veröffentlichen**.  
  
31. Wechseln Sie zu der **Master Data Manager-Webanwendung**.  
  
32. Stellen Sie sicher, die auf der Startseite **Lieferanten** ausgewählt ist, für die **Modell**, und klicken Sie auf **Explorer**. Wenn Sie bereits verfügen die **Explorer** geöffnet ist, aktualisieren Sie den Internetbrowser.  
  
33. **Sortierung** die Liste nach **Code** , und suchen Sie nach Datensätzen mit **S57** und **S66** als Codes. Sie können auch die **Filter** auf der Symbolleiste, um für einen bestimmten Datensatz in der Liste zu suchen.  
  
34. Schließen Sie jetzt **Mappe1 - Microsoft Excel** Fenster ohne Speichern der Datei.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 5: Erstellen eines domänenbasierten Attributs aus Excel](../../2014/tutorials/task-5-creating-a-domain-based-attribute-from-excel.md)  
  
  
