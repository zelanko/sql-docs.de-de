---
title: 'Tutorial: Hinzufügen eines Säulendiagramms zu einem Bericht (Berichts-Generator) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 63480059-b7b9-44b5-9d7f-91780db708b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 723e8fe5f657d3b9eda2d6ab73966830a13a3aac
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66099127"
---
# <a name="tutorial-add-a-column-chart-to-your-report-report-builder"></a>Lernprogramm: Hinzufügen eines Säulendiagramms zu einem Bericht (Berichts-Generator)
  Ein Säulendiagramm zeigt eine Reihe als Satz vertikaler Balken an, die nach Kategorie gruppiert sind. Ein Säulendiagramm kann für folgende Zwecke verwendet werden:  
  
-   Anzeigen von Datenänderungen über einen bestimmten Zeitraum  
  
-   Vergleichen des relativen Werts mehrerer Reihen  
  
-   Anzeigen eines gleitenden Durchschnitts, um Trends darzustellen  
  
 In der folgenden Abbildung sehen Sie das zu erstellende Säulendiagramm mit einem gleitenden Durchschnitt:  
  
 ![rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "rs_TutorialColChartFinished")  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>Was Sie lernen werden  
 In diesem Lernprogramm lernen Sie Folgendes:  
  
1.  [Erstellen eines Diagramms mithilfe des Diagramm-Assistenten](#Chart)  
  
2.  [Auswählen des Diagrammtyps](#ChartType)  
  
3.  [Formatieren und Beschriften der horizontalen Achse](#Horizontal)  
  
4.  [Verschieben der Legende](#Legend)  
  
5.  [Benennen des Diagramms](#ChartTitle)  
  
6.  [Formatieren und Beschriften der vertikalen Achse](#Vertical)  
  
7.  [Hinzufügen eines gleitenden Durchschnitts](#Average)  
  
8.  [Hinzufügen eines Berichts Titels](#Title)  
  
9. [Speichern des Berichts](#Save)  
  
> [!NOTE]  
>  In diesem Lernprogramm werden die Schritte für den Assistenten in einem Verfahren zusammengefasst. Im ersten Tutorial dieser Reihe erhalten Sie detaillierte Anweisungen zum Navigieren zu einem Berichtsserver, zum Auswählen einer Datenquelle sowie zum Erstellen eines Datasets: [Tutorial: Erstellen eines einfachen Tabellenberichts (Berichts-Generator)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Geschätzte Zeit zum Bearbeiten dieses Tutorials: 15 Minuten.  
  
## <a name="requirements"></a>Anforderungen  
 Weitere Informationen zu den Anforderungen finden Sie unter [Voraussetzungen für Tutorials &#40;Berichts-Generator&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="1-create-a-chart-report-from-the-chart-wizard"></a><a name="Chart"></a>1. Erstellen eines Diagramm Berichts mithilfe des Diagramm-Assistenten  
 Verwenden Sie im Dialogfeld " **Getting Started** " den Diagramm-Assistenten, um ein eingebettetes DataSet zu erstellen, eine freigegebene Datenquelle auszuwählen und ein Säulendiagramm zu erstellen.  
  
> [!NOTE]  
>  In diesem Lernprogramm sind die Datenwerte in der Abfrage enthalten, sodass keine externe Datenquelle benötigt wird. Die Abfrage ist daher relativ lang. In einer Geschäftsumgebung wären die Daten nicht in der Abfrage enthalten. Dieses Szenario dient nur zu Lernzwecken.  
  
#### <a name="to-create-a-new-chart-report"></a>So erstellen Sie einen neuen Diagrammbericht  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Microsoft SQL Server 2012 Berichts-Generator**, und klicken Sie dann auf **Berichts-Generator**.  
  
     Das Dialogfeld " **Getting Started** " wird angezeigt.  
  
    > [!NOTE]  
    >  Wenn das Dialogfeld " **Getting Started** " nicht angezeigt wird, klicken Sie auf der Schaltfläche " **Berichts-Generator** " auf **neu**.  
  
2.  Vergewissern Sie sich, dass im linken Bereich **Neuer Bericht** ausgewählt ist.  
  
3.  Klicken Sie im rechten Bereich auf **Diagramm-Assistent**.  
  
4.  Klicken Sie auf der **Seite Dataset auswählen**auf **DataSet erstellen**, und klicken Sie dann auf **weiter**.  
  
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
  
8.  (Optional) Klicken Sie auf die Schaltfläche Ausführen (**!**), um die Daten anzuzeigen, auf denen das Diagramm basiert.  
  
9. Klicken Sie auf **Weiter**.  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a>2. Wählen Sie den Diagrammtyp aus.  
 Sie können aus einer Vielzahl vordefinierter Diagrammtypen auswählen.  
  
#### <a name="to-add-a-column-chart"></a>So fügen Sie einem Bericht ein Säulendiagramm hinzu  
  
1.  Das Säulendiagramm ist der Standarddiagrammtyp der Seite **Diagrammtyp auswählen** . Klicken Sie auf **Weiter**.  
  
2.  Ziehen Sie auf der Seite **Diagrammfelder anordnen** das Feld „SalesDate“ in **Kategorien**. Kategorien werden auf der horizontalen Achse angezeigt.  
  
3.  Ziehen Sie das Feld „Sales“ in **Werte**. Im Feld **Werte** wird „Sum(Sales)“ angezeigt, da die Summe des Gesamtumsatzwerts für jedes Datum aggregiert wird. Werte werden auf der vertikalen Achse angezeigt.  
  
4.  Klicken Sie auf **Weiter**.  
  
5.  Wählen Sie auf der Seite Format **auswählen** im Feld Stile einen Stil aus.  
  
     Ein Format dient zum Angeben eines Schriftschnitts, einer Farbpalette und einer Rahmenart. Wenn Sie ein Format auswählen, wird im Vorschaubereich ein Beispiel für das Diagramm mit diesem Format angezeigt.  
  
6.  Klicken Sie auf **Fertig stellen**.  
  
     Das Diagramm wird der Entwurfsoberfläche hinzugefügt.  
  
7.  Klicken Sie auf das Diagramm, um die Diagrammziehpunkte anzuzeigen. Ziehen Sie die rechte untere Ecke des Diagramms, um das Diagramm zu vergrößern. Die Berichtsentwurfsoberfläche wird vergrößert, um genügend Platz für das Diagramm zu bieten.  
  
8.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="3-format-and-label-the-horizontal-axis"></a><a name="Horizontal"></a>3. Formatieren und beschriften der horizontalen Achse  
 Standardmäßig werden die Werte auf der horizontalen Achse in einem allgemeinen Format angezeigt, dessen Größe automatisch an die Diagrammgröße angepasst wird.  
  
#### <a name="to-format-a-date-on-the-horizontal-axis"></a>So formatieren Sie ein Datum auf der horizontalen Achse  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Klicken Sie mit der rechten Maustaste auf die horizontale Achse, und klicken Sie auf **Eigenschaften für horizontale Achsen**.  
  
3.  Klicken Sie auf **Number**.  
  
4.  Wählen Sie unter **Kategorie**die Option **Datum**aus.  
  
5.  Wählen Sie im Feld **Typ** die Option **31. Jan. 2000**aus.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Klicken Sie auf der Registerkarte Stamm auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Das Datum wird im ausgewählten Datumsformat angezeigt. Beachten Sie, dass im Diagramm nicht jede Kategorie auf der horizontalen Achse beschriftet ist. Standardmäßig werden nur Bezeichnungen aufgenommen, die neben die Achse passen.  
  
 Sie können die Bezeichnungsanzeige anpassen, indem Sie die Bezeichnungen drehen und das Intervall angeben.  
  
#### <a name="to-rotate-the-axis-labels-and-change-the-display-interval-along-the-horizontal-axis"></a>So drehen Sie die Achsenbezeichnungen und ändern das Anzeigeintervall auf der horizontalen Achse  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Klicken Sie mit der rechten Maustaste auf den horizontalen Achsentitel, und klicken Sie dann auf **Achsentitel anzeigen** , um den Titel zu entfernen. Da auf der horizontalen Achse Datumsangaben angezeigt werden, wird der Titel nicht benötigt.  
  
3.  Klicken Sie mit der rechten Maustaste auf die horizontale Achse und dann auf **Eigenschaften für horizontale Achsen**.  
  
4.  Geben Sie auf der Seite **Achsen Optionen** unter **Achsen Bereich und-Intervall**den Namen **3** für **Intervall**ein. Im Diagramm wird jedes dritte Datum angezeigt.  
  
5.  Klicken Sie auf **Bezeichnungen**.  
  
6.  Wählen Sie unter **Optionen für automatische Anpassung der Achsen Bezeichnung ändern die Option** **Automatische Anpassung deaktivieren**aus.  
  
7.  Wählen Sie in **Drehwinkel für Bezeichnungen**den Wert **-90**aus.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Der Beispieltext für die horizontale Achse wird um 90 Grad gedreht.  
  
9. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Im Diagramm werden die Bezeichnungen gedreht, und die Bezeichnung für jedes dritte Datum wird angezeigt.  
  
##  <a name="4-move-the-legend"></a><a name="Legend"></a>4. Verschieben der Legende  
 Die Legende wird automatisch auf Basis der Kategorie- und Reihendaten erstellt.  
  
#### <a name="to-move-the-legend-below-the-chart-area-of-a-column-chart"></a>So verschieben Sie die Legende unter den Diagrammbereich eines Säulendiagramms  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Legende im Diagramm, und klicken Sie dann auf **Legenden Eigenschaften**.  
  
3.  Wählen Sie unter **Layout und Position**eine andere Position aus. Legen Sie z. B. eine Position unten in der Mitte fest.  
  
     Wenn Sie die Legende über oder unter einem Diagramm platzieren, ändert sich das Layout der Legende von vertikal zu horizontal. In der Dropdownliste **Layout** können Sie ein anderes Layout auswählen.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  (Optional) Da es nur eine Kategorie in diesem Lernprogramm gibt, wird die Legende nicht benötigt. Klicken Sie zum Entfernen der Legende mit der rechten Maustaste auf die Legende, und klicken Sie dann auf **Legende löschen**.  
  
6.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="5-title-the-chart"></a><a name="ChartTitle"></a>5. Titel des Diagramms  
  
#### <a name="to-change-the-chart-title-above-the-chart-area"></a>So ändern Sie den Diagrammtitel über dem Diagrammbereich  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Markieren Sie am oberen Rand des Diagramms den Text **Diagramm Titel** , und geben Sie dann den folgenden Text ein: **Store Sales Order Total**.  
  
3.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="6-format-and-label-the-vertical-axis"></a><a name="Vertical"></a>6. Formatieren und beschriften der vertikalen Achse  
 Standardmäßig werden die Werte auf der vertikalen Achse in einem allgemeinen Format angezeigt, dessen Größe automatisch an die Diagrammgröße angepasst wird.  
  
#### <a name="to-format-as-currency-the-numbers-on-the-vertical-axis"></a>So formatieren Sie die Zahlen auf der vertikalen Achse als Währung  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Doppelklicken Sie neben dem Diagramm auf die Bezeichnungen der vertikalen Achse, um sie auszuwählen.  
  
3.  Klicken Sie im Menüband auf der Registerkarte **Startseite** in der Gruppe **Zahl** auf die Schaltfläche **Währung** . Die Achsenbezeichnungen werden nun im Währungsformat dargestellt.  
  
4.  Klicken Sie im Menüband auf der Registerkarte **Startseite** in der Gruppe **Zahl** zweimal auf die Schaltfläche **Dezimalstellen verringern** , um die auf den nächstgelegenen Dollar gerundete Zahl anzuzeigen.  
  
5.  Klicken Sie mit der rechten Maustaste auf die vertikale Achse, und klicken Sie auf **Eigenschaften für vertikale**  
  
6.  Klicken Sie auf **Number**. Beachten Sie, dass im Feld **Kategorie** bereits die Option **Währung** ausgewählt und **Dezimalstellen** bereits **0** (null) ist.  
  
7.  Klicken Sie im Feld **Werte anzeigen in** auf **tausende**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Klicken Sie mit der rechten Maustaste auf den Titel der vertikalen Achse entlang der Seite des Diagramms, und klicken Sie auf **Achsentitel Eigenschaften**.  
  
10. Ersetzen Sie den Text im **Textfeld Titel** durch den folgenden Text: **Sales Total (in Tausender)**. Darüber hinaus können Sie das gewünschte Format für den Titel festlegen.  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="7-add-a-moving-average"></a><a name="Average"></a>7. Hinzufügen eines gleitenden Durchschnitts  
  
#### <a name="to-add-a-moving-average"></a>So fügen Sie einen gleitenden Durchschnitt hinzu  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Doppelklicken Sie auf das Diagramm, um den Bereich **Diagrammdaten** anzuzeigen.  
  
3.  Klicken Sie mit der rechten Maustaste auf das Feld **[Sum (Sales)]** , das sich im Bereich **Werte** befindet, und klicken Sie dann auf **berechnete Reihe hinzufügen**.  
  
4.  Überprüfen Sie in **Formel**, ob **Gleitender Durchschnitt** ausgewählt ist.  
  
5.  Wählen Sie in **Formelparameter festlegen**für **Zeitraum**den Wert **4**aus.  
  
6.  Klicken Sie auf **Border**.  
  
7.  Wählen Sie unter **Linienbreite**den Eintrag **3 pt liegen**aus.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Im Diagramm wird eine Linie angezeigt, die den gleitenden Durchschnitt für den Gesamtumsatz nach Datum darstellt – gemittelt über jeweils vier Datumsangaben.  
  
##  <a name="8-add-a-report-title"></a><a name="Title"></a>8. Hinzufügen eines Berichts Titels  
  
#### <a name="to-add-a-report-title"></a>So fügen Sie einen Berichtstitel hinzu  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Klicken Sie auf der Entwurfsoberfläche auf **Zum Hinzufügen eines Titels klicken**.  
  
3.  Geben Sie **Umsatz Diagramm**ein, drücken Sie die EINGABETASTE, und geben Sie dann **Januar bis Dezember 2009**ein, sodass Sie wie folgt aussieht:  
  
     **Umsatzdiagramm**  
  
     **Januar bis Dezember 2009**  
  
4.  Wählen Sie **Umsatz Diagramm**aus, und klicken Sie im Abschnitt **Schriftart** auf der Registerkarte **Home** des Menübands auf die Schaltfläche **Fett** .  
  
5.  Wählen Sie **Januar bis Dezember 2009**aus, und legen Sie auf der Registerkarte **Home** im Abschnitt **Schriftart** den Schrift Grad auf **10**fest.  
  
6.  Optionale Möglicherweise müssen Sie das Textfeld **Titel** vergrößern, um die zwei Textzeilen aufnehmen zu können, indem Sie die Pfeile mit zwei Spitzen nach unten ziehen, wenn Sie in die Mitte des unteren Rands klicken.  
  
     Dieser Titel wird am Anfang des Berichts angezeigt. Ist keine Kopfzeile definiert, erfüllen die Elemente über dem Berichtshauptteil die Funktion einer Berichtskopfzeile.  
  
7.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="9-save-the-report"></a><a name="Save"></a>9. Speichern des Berichts  
  
#### <a name="to-save-the-report"></a>So speichern Sie den Bericht  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Klicken Sie auf die Schaltfläche Berichts-Generator und anschließend auf **Speichern unter**.  
  
3.  Geben Sie im Feld **Name**den Text **Sales Order Column Chart**ein.  
  
4.  Klicken Sie auf **Speichern**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben das Lernprogramm "Hinzufügen eines Säulendiagramms zu einem Bericht" erfolgreich abgeschlossen. Weitere Informationen zu Diagrammen finden Sie unter [Diagramme (Berichts-Generator und SSRS)](report-design/charts-report-builder-and-ssrs.md) und [Sparklines und Datenbalken (Berichts-Generator und SSRS)](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Lernprogramme &#40;Berichts-Generator&#41;](report-builder-tutorials.md)   
 [Berichts-Generator in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
