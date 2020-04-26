---
title: 'Aufgabe 4 (optional): kombinieren, abgleichen und Veröffentlichen eines neuen Datensatzes | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "65489273"
---
# <a name="task-4-optional-combining-matching-and-publishing-new-set-of-data"></a>Aufgabe 4 (optional): Kombination, Abgleich und Veröffentlichung eines neuen Datensatzes
  Es ist möglich, dass Sie dem MDS-Repository im Laufe der Zeit weitere Daten hinzufügen möchten. Vor dem Hinzufügen von Daten kann es hilfreich sein, die neuen Daten mit den bereits in MDS verwalteten Daten zu vergleichen, um sicherzustellen, dass Sie keine doppelten oder ungenauen Daten hinzufügen. Im Master Data Services-Add-In für Excel können Sie Daten aus zwei Arbeitsblättern kombinieren und die Daten dann vergleichen, um Duplikate zu identifizieren und zu entfernen, bevor Sie die Daten in MDS veröffentlichen. Die Abgleichsfunktion des MDS-Add-Ins für Excel verwendet die DQS-Abgleichsfunktionalität, um Übereinstimmungen in den Daten zu identifizieren. In dieser Aufgabe kombinieren Sie Daten aus zwei Arbeitsblättern in einem Arbeitsblatt und führen dann die Abgleichsaktivität aus, um Duplikate zu identifizieren und zu entfernen, bevor Sie die Daten in MDS veröffentlichen. Weitere Informationen finden Sie [unter Data Quality](https://msdn.microsoft.com/library/hh548681.aspx) -Abgleich in den Themen MDS-Add-in für Excel und [Kombinieren von Daten](https://msdn.microsoft.com/library/hh548680.aspx) .  
  
1.  Startet eine neue Instanz von **Excel**. Zeigen Sie im **Startmenü**auf **Ausführen**, geben Sie **Excel**ein, und klicken Sie auf **OK**.  
  
2.  Wechseln Sie zur Registerkarte **Master Daten** , indem Sie in der Menüleiste auf **Master Daten** klicken.  
  
3.  Klicken Sie im Menüband in der Gruppe **verbinden und laden** auf **verbinden** , um eine Verbindung mit dem **MDS-Server**herzustellen. Sie haben diese Verbindung zuvor in dieser Lektion konfiguriert.  
  
     ![Excel – Schaltfläche "Explorer anzeigen" auf der Registerkarte "Masterdaten"](../../2014/tutorials/media/et-combinematchandpublishnewsod-01.jpg "Excel – Schaltfläche "Explorer anzeigen" auf der Registerkarte "Masterdaten"")  
  
4.  Der Bereich **Master Daten-Explorer** auf der rechten Seite sollte angezeigt werden. Wenn die Master Daten-Explorer nicht angezeigt wird, klicken Sie im Menüband auf die Schaltfläche **Explorer anzeigen** .  
  
5.  Wählen Sie im Fenster **Master Daten-Explorer** in der Dropdown Liste für das **Modell**die Option **Suppliers** aus. Sie sollten sehen, dass das Modell über eine Entität verfügt: **Supplier**.  
  
     ![Excel – Master Data Explorer (Fenster)](../../2014/tutorials/media/et-combinematchandpublishnewsod-02.jpg "Excel – Master Data Explorer (Fenster)")  
  
6.  Doppelklicken Sie in der Liste Entität auf **Lieferant** , um die Entitäts Elemente in das Excel-Arbeitsblatt zu laden.  
  
7.  Klicken Sie unten auf **Tabelle2** , um zur Registerkarte **Tabelle2** zu wechseln. Wenn **Tabelle2**nicht angezeigt wird, fügen Sie ein neues Arbeitsblatt hinzu.  
  
8.  Öffnen Sie die Datei **Suppliers. xls** (die ursprüngliche Eingabedatei, die in den Tutorial-Dateien enthalten ist), und kopieren Sie alle (drei) Zeilen aus dem **combineandreinigen** -Arbeitsblatt in **Tabelle2**.  
  
9. Wechseln Sie zurück zum **Lieferanten** Blatt im **Buch 1-Microsoft Excel** (nicht zur **bereinigten und übereinstimmenden Lieferantenliste** Excel), das mit **MDS**verbunden ist.  
  
10. Klicken Sie in der Menüleiste auf **Master Daten** .  
  
11. Klicken Sie im Menüband auf **Daten kombinieren** . Das Dialogfeld **Daten kombinieren** wird angezeigt.  
  
12. Klicken Sie im Dialogfeld **Daten kombinieren** auf die Schaltfläche neben dem Textfeld **mit MDS-Daten zu kombinierender Bereich** , wie in der folgenden Abbildung dargestellt.  
  
     ![Excel – Daten kombinieren (Dialogfeld)](../../2014/tutorials/media/et-combinematchandpublishnewsod-03.jpg "Excel – Daten kombinieren (Dialogfeld)")  
  
13. Das Dialogfeld sollte jetzt verkleinert angezeigt werden. Klicken Sie nun auf **Tabelle2** , um zur Registerkarte **Tabelle2** zu wechseln, die die neuen Lieferantendaten mit vier Zeilen (einschließlich einer Kopfzeile) enthält.  
  
14. Wählen Sie im **Tabelle2** **alle Zeilen einschließlich der Kopfzeile** aus (auch wenn Sie bereits ausgewählt sind). Sie sollten sehen, dass der **Bereich, der mit MDS-Daten kombiniert** werden soll, automatisch aktualisiert wird.  
  
     ![Excel – Daten kombinieren (Dialogfeld) – minimiert](../../2014/tutorials/media/et-combinematchandpublishnewsod-04.jpg "Excel – Daten kombinieren (Dialogfeld) – minimiert")  
  
15. Wechseln Sie zurück zur Registerkarte **Suppliers** , ohne das Dialogfeld **Daten kombinieren** zu schließen.  
  
16. Klicken Sie neben dem **Textfeld**auf die **Schaltfläche** . Das Dialogfeld sollte jetzt erweitert angezeigt werden. Alle Zuordnungen zwischen den Spalten der MDS- **Entität** " **Supplier** " und " **Excel** " werden automatisch aufgefüllt.  
  
     ![Excel – Daten kombinieren (Dialogfeld) – mit Daten gefüllt](../../2014/tutorials/media/et-combinematchandpublishnewsod-05.jpg "Excel – Daten kombinieren (Dialogfeld) – mit Daten gefüllt")  
  
17. Stellen Sie sicher, dass die Spalte " **Code** Entität" der Spalte " **SupplierID** " im Arbeitsblatt und die Entitäts Spalte " **ZIP-Code** " der Spalte " **ZIP** -Code" im Arbeitsblatt zugeordnet ist.  
  
18. Klicken Sie im Dialogfeld **Daten kombinieren** auf **kombinieren**.  
  
19. Überprüfen Sie, ob drei Datenzeilen am Ende des Arbeitsblatts hinzugefügt wurden und ob diese farblich codiert sind.  
  
     ![Excel – Neue Elemente nach dem Kombinieren](../../2014/tutorials/media/et-combinematchandpublishnewsod-06.jpg "Excel – Neue Elemente nach dem Kombinieren")  
  
20. Klicken Sie im Menüband auf **mathematische Daten** , um Duplikate zu identifizieren. Diese Funktion verwendet die Abgleichsfunktionalität von DQS.  
  
21. Wählen Sie im Dialogfeld **Daten abgleichen** die Option **Suppliers** für die **DQS-Wissensdatenbank**aus.  
  
     ![Excel – Daten abgleichen (Dialogfeld)](../../2014/tutorials/media/et-combinematchandpublishnewsod-07.jpg "Excel – Daten abgleichen (Dialogfeld)")  
  
22. Ordnen Sie Arbeitsblattspalten Domänen zu, wie in der folgenden Tabelle gezeigt.  
  
    |Arbeitsblattspalte|Domäne|  
    |----------------------|------------|  
    |Code (Sie haben "Supplier ID" als Code für die Entität "Supplier" in MDS hochgeladen)|Supplier ID|  
    |Name (Sie haben "Supplier Name" als Name für die Entität "Supplier" in MDS hochgeladen)|Supplier Name|  
    |ContactEmailAddress|ContactEmail|  
  
23. Wählen Sie **Voraussetzung** für die **Code** Spalten Zuordnung aus.  
  
24. Geben Sie **70%** als **Gewichtung** für **Lieferanten Name** und **30%** als **Gewichtung** für die **Kontakt-e-Mail** ein, wie in der Abbildung dargestellt.  
  
25. Klicken Sie auf **OK**.  
  
26. Der Abgleichsprozess sollte ein Duplikat für den Lieferanten mit dem folgenden **Code identifizieren: S1**.  
  
     ![Excel – Abgleichsergebnisse](../../2014/tutorials/media/et-combinematchandpublishnewsod-08.jpg "Excel – Abgleichsergebnisse")  
  
27. Wählen Sie die **doppelte Zeile (Orange)**, klicken Sie mit der rechten Maustaste, und klicken Sie auf **Löschen** , um die Zeile zu löschen.  
  
28. Löschen Sie die Spalte **CLUSTER_ID** , da Sie Sie nicht mehr benötigen.  
  
29. Klicken Sie auf **veröffentlichen** , um die anderen beiden neuen Datensätze mit den **Codes S66** und **S57** in MDS zu veröffentlichen.  
  
30. Fügen Sie im Dialogfeld **veröffentlichen und** **kommentieren eine Anmerkung**hinzu, und klicken Sie auf **veröffentlichen**.  
  
31. Wechseln Sie zur **Master Data Manager-Webanwendung**.  
  
32. Vergewissern Sie sich, dass auf der Startseite die Option **Suppliers** für das **Modell**ausgewählt ist, und klicken Sie auf **Explorer**. Wenn der **Explorer** bereits geöffnet ist, aktualisieren Sie den Internetbrowser.  
  
33. **Sortieren** Sie die Liste nach **Code** , und suchen Sie nach Datensätzen mit **S57** und **S66** als Codes. Sie können auch die **Filter** Schaltfläche auf der Symbolleiste verwenden, um nach einem bestimmten Datensatz in der Liste zu suchen.  
  
34. Schließen Sie jetzt **Mappe1-Microsoft Excel-** Fenster, ohne die Datei zu speichern.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 5: Erstellen eines domänenbasierten Attributs aus Excel](../../2014/tutorials/task-5-creating-a-domain-based-attribute-from-excel.md)  
  
  
