---
title: 'Tutorial: Hinzufügen eines Säulendiagramms zu einem Bericht (Berichts-Generator) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 63480059-b7b9-44b5-9d7f-91780db708b6
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: cc295fcd58d3e7609989f35a382e780614e9d7a3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161901"
---
# <a name="tutorial-add-a-column-chart-to-your-report-report-builder"></a>Lernprogramm: Hinzufügen eines Säulendiagramms zu einem Bericht (Berichts-Generator)
  Ein Säulendiagramm zeigt eine Reihe als Satz vertikaler Balken an, die nach Kategorie gruppiert sind. Ein Säulendiagramm kann für folgende Zwecke verwendet werden:  
  
-   Anzeigen von Datenänderungen über einen bestimmten Zeitraum  
  
-   Vergleichen des relativen Werts mehrerer Reihen  
  
-   Anzeigen eines gleitenden Durchschnitts, um Trends darzustellen  
  
 In der folgenden Abbildung sehen Sie das zu erstellende Säulendiagramm mit einem gleitenden Durchschnitt:  
  
 ![Rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "Rs_TutorialColChartFinished")  
  
##  <a name="BackToTop"></a> Lernziele  
 In diesem Lernprogramm lernen Sie Folgendes:  
  
1.  [Erstellen eines Diagramms mithilfe des Diagramm-Assistenten](#Chart)  
  
2.  [Auswählen des Diagrammtyps](#ChartType)  
  
3.  [Formatieren und Beschriften der horizontalen Achse](#Horizontal)  
  
4.  [Verschieben der Legende](#Legend)  
  
5.  [Benennen des Diagramms](#ChartTitle)  
  
6.  [Formatieren und Beschriften der vertikalen Achse](#Vertical)  
  
7.  [Hinzufügen eines gleitenden Durchschnitts](#Average)  
  
8.  [Hinzufügen eines Berichtstitels](#Title)  
  
9. [Speichern des Berichts](#Save)  
  
> [!NOTE]  
>  In diesem Lernprogramm werden die Schritte für den Assistenten in einem Verfahren zusammengefasst. Im ersten Tutorial dieser Reihe erhalten Sie detaillierte Anweisungen zum Navigieren zu einem Berichtsserver, zum Auswählen einer Datenquelle sowie zum Erstellen eines Datasets: [Tutorial: Erstellen eines einfachen Tabellenberichts (Berichts-Generator)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Geschätzte Zeit zum Bearbeiten dieses Tutorials: 15 Minuten.  
  
## <a name="requirements"></a>Anforderungen  
 Weitere Informationen zu den Anforderungen finden Sie unter [Voraussetzungen für Tutorials &#40;Berichts-Generator&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="Chart"></a> 1. Erstellen eines Diagrammberichts mithilfe des Diagramm-Assistenten  
 Von der **Einstieg** Dialogfeld verwenden des Diagramm-Assistenten erstellen Sie ein eingebettetes Dataset, wählen Sie eine freigegebene Datenquelle und erstellen Sie ein Säulendiagramm.  
  
> [!NOTE]  
>  In diesem Lernprogramm sind die Datenwerte in der Abfrage enthalten, sodass keine externe Datenquelle benötigt wird. Die Abfrage ist daher relativ lang. In einer Geschäftsumgebung wären die Daten nicht in der Abfrage enthalten. Dieses Szenario dient nur zu Lernzwecken.  
  
#### <a name="to-create-a-new-chart-report"></a>So erstellen Sie einen neuen Diagrammbericht  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Microsoft SQL Server 2012 Berichts-Generator**, und klicken Sie dann auf **Berichts-Generator**.  
  
     Das Dialogfeld **Erste Schritte** wird angezeigt.  
  
    > [!NOTE]  
    >  Wenn die **Einstieg** Dialogfeld nicht angezeigt wird, aus der **Berichts-Generator** , zeigen Sie auf **neu**.  
  
2.  Vergewissern Sie sich, dass im linken Bereich **Neuer Bericht** ausgewählt ist.  
  
3.  Klicken Sie im rechten Bereich auf **Diagramm-Assistent**.  
  
4.  Klicken Sie auf der Seite **Dataset auswählen**auf **Dataset erstellen**und anschließend auf **Weiter**.  
  
5.  Wählen Sie auf der Seite **Verbindung mit einer Datenquelle auswählen** eine vorhandene Datenquelle aus, oder navigieren Sie zum Berichtsserver, und wählen Sie eine Datenquelle aus. Klicken Sie anschließend auf **Weiter**. Möglicherweise müssen Benutzername und Kennwort eingegeben werden.  
  
    > [!NOTE]  
    >  Welche Datenquelle Sie auswählen, ist unwichtig, solange Sie über ausreichende Berechtigungen verfügen. Aus der Datenquelle werden keine Daten abgerufen. Weitere Informationen finden Sie unter [Alternative Methoden zum Herstellen einer Datenverbindung (Berichts-Generator)](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
6.  Klicken Sie auf der Seite **Abfrage entwerfen** auf **Als Text bearbeiten**.  
  
7.  Fügen Sie die folgende Abfrage in den Abfragebereich ein:  
  
    ```  
    SELECT CAST('2009-01-01' AS date) AS SalesDate, CAST(54995.21 AS money) AS Sales  
    UNION SELECT CAST('2009-01-05' AS date) AS SalesDate, CAST(64499.04 AS money) AS Sales  
    UNION SELECT CAST('2009-02-11' AS date) AS SalesDate, CAST(37821.79 AS money) AS Sales  
    UNION SELECT CAST('2009-03-18' AS date) AS SalesDate, CAST(53633.08 AS money) AS Sales  
    UNION SELECT CAST('2009-04-23' AS date) AS SalesDate, CAST(24019.3 AS money) AS Sales  
    UNION SELECT CAST('2009-05-01' AS date) AS SalesDate, CAST(93245.5 AS money) AS Sales  
    UNION SELECT CAST('2009-06-06' AS date) AS SalesDate, CAST(55288.0 AS money) AS Sales  
    UNION SELECT CAST('2009-06-16' AS date) AS SalesDate, CAST(68733.5 AS money) AS Sales  
    UNION SELECT CAST('2009-07-16' AS date) AS SalesDate, CAST(24750.85 AS money) AS Sales  
    UNION SELECT CAST('2009-08-23' AS date) AS SalesDate, CAST(43452.3 AS money) AS Sales  
    UNION SELECT CAST('2009-09-24' AS date) AS SalesDate, CAST(58656. AS money) AS Sales  
    UNION SELECT CAST('2009-10-15' AS date) AS SalesDate, CAST(44583. AS money) AS Sales  
    UNION SELECT CAST('2009-11-21' AS date) AS SalesDate, CAST(81568. AS money) AS Sales  
    UNION SELECT CAST('2009-12-15' AS date) AS SalesDate, CAST(45973. AS money) AS Sales  
    UNION SELECT CAST('2009-12-26' AS date) AS SalesDate, CAST(96357. AS money) AS Sales  
    UNION SELECT CAST('2009-12-31' AS date) AS SalesDate, CAST(81946. AS money) AS Sales  
    ```  
  
8.  (Optional) Klicken Sie auf die Schaltfläche „Ausführen“ (**!**), um die Daten anzuzeigen, auf denen das Diagramm basiert.  
  
9. Klicken Sie auf **Weiter**.  
  
##  <a name="ChartType"></a> 2. Auswählen des Diagrammtyps  
 Sie können aus einer Vielzahl vordefinierter Diagrammtypen auswählen.  
  
#### <a name="to-add-a-column-chart"></a>So fügen Sie einem Bericht ein Säulendiagramm hinzu  
  
1.  Das Säulendiagramm ist der Standarddiagrammtyp der Seite **Diagrammtyp auswählen** . Klicken Sie auf **Weiter**.  
  
2.  Ziehen Sie auf der Seite **Diagrammfelder anordnen** das Feld „SalesDate“ in **Kategorien**. Kategorien werden auf der horizontalen Achse angezeigt.  
  
3.  Ziehen Sie das Feld „Sales“ in **Werte**. Im Feld **Werte** wird „Sum(Sales)“ angezeigt, da die Summe des Gesamtumsatzwerts für jedes Datum aggregiert wird. Werte werden auf der vertikalen Achse angezeigt.  
  
4.  Klicken Sie auf **Weiter**.  
  
5.  Auf der **Auswählen eines Formats** Seite Wählen Sie im Feld "Stile", eine Art.  
  
     Ein Format dient zum Angeben eines Schriftschnitts, einer Farbpalette und einer Rahmenart. Wenn Sie ein Format auswählen, wird im Vorschaubereich ein Beispiel für das Diagramm mit diesem Format angezeigt.  
  
6.  Klicken Sie auf **Fertig stellen**.  
  
     Das Diagramm wird der Entwurfsoberfläche hinzugefügt.  
  
7.  Klicken Sie auf das Diagramm, um die Diagrammziehpunkte anzuzeigen. Ziehen Sie die rechte untere Ecke des Diagramms, um das Diagramm zu vergrößern. Die Berichtsentwurfsoberfläche wird vergrößert, um genügend Platz für das Diagramm zu bieten.  
  
8.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="Horizontal"></a> 3. Formatieren und Beschriften der horizontalen Achse  
 Standardmäßig werden die Werte auf der horizontalen Achse in einem allgemeinen Format angezeigt, dessen Größe automatisch an die Diagrammgröße angepasst wird.  
  
#### <a name="to-format-a-date-on-the-horizontal-axis"></a>So formatieren Sie ein Datum auf der horizontalen Achse  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Mit der rechten Maustaste in der horizontalen Achse, und klicken Sie dann auf **Eigenschaften für horizontale Achsen**.  
  
3.  Klicken Sie auf **Anzahl**.  
  
4.  In **Kategorie**Option **Datum**.  
  
5.  Wählen Sie im Feld **Typ** die Option **31. Jan. 2000**aus.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Klicken Sie auf der Registerkarte „Stamm“ auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Das Datum wird im ausgewählten Datumsformat angezeigt. Beachten Sie, dass im Diagramm nicht jede Kategorie auf der horizontalen Achse beschriftet ist. Standardmäßig werden nur Bezeichnungen aufgenommen, die neben die Achse passen.  
  
 Sie können die Bezeichnungsanzeige anpassen, indem Sie die Bezeichnungen drehen und das Intervall angeben.  
  
#### <a name="to-rotate-the-axis-labels-and-change-the-display-interval-along-the-horizontal-axis"></a>So drehen Sie die Achsenbezeichnungen und ändern das Anzeigeintervall auf der horizontalen Achse  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Mit der rechten Maustaste in den Titel der horizontalen Achse, und klicken Sie dann auf **Achsentitel anzeigen** auf den Titel zu entfernen. Da auf der horizontalen Achse Datumsangaben angezeigt werden, wird der Titel nicht benötigt.  
  
3.  Mit der rechten Maustaste in der horizontalen Achse, und klicken Sie dann auf **Eigenschaften für horizontale Achsen**.  
  
4.  In der **Achsenoptionen** Seite **Achsenbereich und-Intervall**, Typ **3** für **Intervall**. Im Diagramm wird jedes dritte Datum angezeigt.  
  
5.  Klicken Sie auf **Bezeichnungen**.  
  
6.  In **Optionen für automatische Anpassung von achsenbezeichnungen ändern**Option **automatische Anpassung deaktivieren**.  
  
7.  Wählen Sie in **Drehwinkel für Bezeichnungen**den Wert **-90**aus.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Der Beispieltext für die horizontale Achse wird um 90 Grad gedreht.  
  
9. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Im Diagramm werden die Bezeichnungen gedreht, und die Bezeichnung für jedes dritte Datum wird angezeigt.  
  
##  <a name="Legend"></a> 4. Verschieben der Legende  
 Die Legende wird automatisch auf Basis der Kategorie- und Reihendaten erstellt.  
  
#### <a name="to-move-the-legend-below-the-chart-area-of-a-column-chart"></a>So verschieben Sie die Legende unter den Diagrammbereich eines Säulendiagramms  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Mit der rechten Maustaste in der Legende des Diagramms, und klicken Sie dann auf **Legendeneigenschaften**.  
  
3.  Für **Layout und Position**, wählen Sie eine andere Position. Legen Sie z. B. eine Position unten in der Mitte fest.  
  
     Wenn Sie die Legende über oder unter einem Diagramm platzieren, ändert sich das Layout der Legende von vertikal zu horizontal. In der Dropdownliste **Layout** können Sie ein anderes Layout auswählen.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  (Optional) Da es nur eine Kategorie in diesem Lernprogramm gibt, wird die Legende nicht benötigt. Um die Legende zu entfernen, mit der rechten Maustaste in der Legende, und klicken Sie dann auf **Legende löschen**.  
  
6.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="ChartTitle"></a> 5. Benennen des Diagramms  
  
#### <a name="to-change-the-chart-title-above-the-chart-area"></a>So ändern Sie den Diagrammtitel über dem Diagrammbereich  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Wählen Sie die Wörter **Diagrammtitel** am oberen Rand des Diagramms, und geben Sie dann den folgenden Text: **Store Sales Order Totals**.  
  
3.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="Vertical"></a> 6. Formatieren und Beschriften der vertikalen Achse  
 Standardmäßig werden die Werte auf der vertikalen Achse in einem allgemeinen Format angezeigt, dessen Größe automatisch an die Diagrammgröße angepasst wird.  
  
#### <a name="to-format-as-currency-the-numbers-on-the-vertical-axis"></a>So formatieren Sie die Zahlen auf der vertikalen Achse als Währung  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Doppelklicken Sie neben dem Diagramm auf die Bezeichnungen der vertikalen Achse, um sie auszuwählen.  
  
3.  Auf dem Menüband auf die **Startseite** Registerkarte die **Anzahl** gruppieren, klicken Sie auf die **Währung** Schaltfläche. Die Achsenbezeichnungen werden nun im Währungsformat dargestellt.  
  
4.  Auf dem Menüband auf die **Startseite** Registerkarte die **Anzahl** gruppieren, klicken Sie auf die **Dezimalstelle löschen** Schaltfläche zweimal, damit die Zahl, die vollständigen Dollarbetrag gerundet wird.  
  
5.  Mit der rechten Maustaste in der vertikalen Achse, und klicken Sie auf **Eigenschaften für vertikale Achsen**.  
  
6.  Klicken Sie auf **Anzahl**. Beachten Sie, dass **Währung** bereits ausgewählt ist, der **Kategorie** Feld und **Dezimalstellen** bereits **0** (null).  
  
7.  In der **Werte anzeigen in** auf **Tausende**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Mit der rechten Maustaste in den Titel der vertikalen Achse auf der Seite des Diagramms, und klicken Sie auf **Achsentiteleigenschaften**.  
  
10. Ersetzen Sie den Text in die **Titeltext** Feld mit dem folgenden Text: **Sales Total (in Tausend)**. Darüber hinaus können Sie das gewünschte Format für den Titel festlegen.  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="Average"></a> 7. Hinzufügen eines gleitenden Durchschnitts  
  
#### <a name="to-add-a-moving-average"></a>So fügen Sie einen gleitenden Durchschnitt hinzu  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Doppelklicken Sie auf das Diagramm, um den Bereich **Diagrammdaten** anzuzeigen.  
  
3.  Mit der rechten Maustaste die **[SUM(Sales)"angezeigt]** Feld, das in der **Werte** Bereich, und klicken Sie dann auf **berechnete Reihe hinzufügen**.  
  
4.  Überprüfen Sie in **Formel**, ob **Gleitender Durchschnitt** ausgewählt ist.  
  
5.  Wählen Sie in **Formelparameter festlegen**für **Zeitraum**den Wert **4**aus.  
  
6.  Klicken Sie auf **Rahmen**.  
  
7.  In **Linienstärke**Option **3 pt**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Im Diagramm wird eine Linie angezeigt, die den gleitenden Durchschnitt für den Gesamtumsatz nach Datum darstellt – gemittelt über jeweils vier Datumsangaben.  
  
##  <a name="Title"></a> 8. Hinzufügen eines Berichtstitels  
  
#### <a name="to-add-a-report-title"></a>So fügen Sie einen Berichtstitel hinzu  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Klicken Sie auf der Entwurfsoberfläche auf **Zum Hinzufügen eines Titels klicken**.  
  
3.  Typ **Umsatzdiagramm**, drücken Sie die EINGABETASTE, und geben dann **Januar bis Dezember 2009**, sodass sie wie folgt aussieht:  
  
     **Umsatzdiagramm**  
  
     **Januar bis Dezember 2009**  
  
4.  Wählen Sie **Umsatzdiagramm**, und klicken Sie auf die **fett** Schaltfläche der **Schriftart** im Abschnitt der **Startseite** Registerkarte des Menübands.  
  
5.  Wählen Sie **Januar bis Dezember 2009**, und klicken Sie in der **Schriftart** im Abschnitt der **Startseite** Registerkarte, legen Sie den Schriftgrad auf **10**.  
  
6.  (Optional) Möglicherweise müssen Sie die **Titel** Textfeld vergrößern, um die beiden Textzeilen eingehen, indem Sie auf die Pfeile mit zwei Spitzen nach unten ziehen, wenn Sie in der Mitte am unteren Rand klicken.  
  
     Dieser Titel wird am Anfang des Berichts angezeigt. Ist keine Kopfzeile definiert, erfüllen die Elemente über dem Berichtshauptteil die Funktion einer Berichtskopfzeile.  
  
7.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="Save"></a> 9. Speichern des Berichts  
  
#### <a name="to-save-the-report"></a>So speichern Sie den Bericht  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Klicken Sie auf die Schaltfläche "Berichts-Generator" und anschließend auf **Speichern unter**.  
  
3.  Geben Sie im Feld **Name**den Text **Sales Order Column Chart**ein.  
  
4.  Klicken Sie auf **Speichern**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben das Lernprogramm "Hinzufügen eines Säulendiagramms zu einem Bericht" erfolgreich abgeschlossen. Weitere Informationen zu Diagrammen finden Sie unter [Diagramme (Berichts-Generator und SSRS)](report-design/charts-report-builder-and-ssrs.md) und [Sparklines und Datenbalken (Berichts-Generator und SSRS)](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Lernprogramme &#40;Berichts-Generator&#41;](report-builder-tutorials.md)   
 [Berichts-Generator in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
