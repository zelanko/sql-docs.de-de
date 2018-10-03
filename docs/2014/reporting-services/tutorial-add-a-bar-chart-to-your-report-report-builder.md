---
title: 'Tutorial: Hinzufügen eines Balkendiagramms zu einem Bericht (Berichts-Generator) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 6956ebd6-0217-4087-a4fa-5cc1c3804691
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 25d3fafc654ab1c272d7688e49d67cd2af5d1820
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106800"
---
# <a name="tutorial-add-a-bar-chart-to-your-report-report-builder"></a>Tutorial: Hinzufügen eines Balkendiagramms zu einem Bericht (Berichts-Generator)
  In einem Balkendiagramm werden Kategoriedaten horizontal angezeigt. Diese Darstellung bietet folgende Vorteile:  
  
-   Bessere Lesbarkeit langer Kategorienamen  
  
-   Bessere Verständlichkeit von Zeiten, die als Werte ausgegeben werden  
  
-   Vergleichen des relativen Werts mehrerer Reihen  
  
 Die folgende Abbildung zeigt das zu erstellende Balkendiagramm mit den Umsätzen der fünf besten Vertriebsmitarbeiter für die Jahre 2008 und 2009 in alphabetischer Reihenfolge.  
  
 ![Rs_BarChartTutorial](../../2014/tutorials/media/rs-barcharttutorial.gif "Rs_BarChartTutorial")  
  
##  <a name="BackToTop"></a> Lernziele  
 In diesem Lernprogramm lernen Sie Folgendes:  
  
1.  [Erstellen eines Diagramms mithilfe des Diagramm-Assistenten](#Chart)  
  
2.  [Auswählen des Diagrammtyps](#ChartType)  
  
3.  [Zeigen Sie aller Kategoriewerte auf der Vertikalachse an](#AllValues)  
  
4.  [Ändern der Darstellung von Namen auf der vertikalen Achse](#Sort)  
  
5.  [Verschieben der Legende](#Legend)  
  
6.  [Verschieben des Diagrammtitels](#ChartTitle)  
  
7.  [Formatieren und Beschriften der horizontalen Achse](#Horizontal)  
  
8.  [Hinzufügen eines Filters zum Anzeigen der fünf besten Werte](#Filter)  
  
9. [Hinzufügen eines Berichtstitels](#Title)  
  
10. [Speichern des Berichts](#Save)  
  
> [!NOTE]  
>  In diesem Lernprogramm werden die Schritte für den Assistenten in einem Verfahren zusammengefasst. Detaillierte Anweisungen zum Navigieren zu einem Berichtsserver, zum Erstellen eines Datasets und zum Auswählen einer Datenquelle finden Sie im ersten Tutorial dieser Reihe unter [Tutorial: Erstellen eines einfachen Tabellenberichts (Berichts-Generator)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Geschätzte Zeit zum Bearbeiten dieses Tutorials: 15 Minuten.  
  
## <a name="requirements"></a>Anforderungen  
 Weitere Informationen zu den Anforderungen finden Sie unter [Voraussetzungen für Tutorials &#40;Berichts-Generator&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="Chart"></a> 1. Erstellen eines Diagrammberichts mithilfe des Diagramm-Assistenten  
 Von der **Einstieg** im Dialogfeld ein eingebettetes Dataset erstellen, wählen Sie eine freigegebene Datenquelle, und erstellen Sie mithilfe des Diagramm-Assistenten ein Balkendiagramm.  
  
> [!NOTE]  
>  In diesem Tutorial sind die Datenwerte in der Abfrage enthalten, sodass keine externe Datenquelle benötigt wird. Die Abfrage ist daher relativ lang. In einer Geschäftsumgebung wären die Daten nicht in der Abfrage enthalten. Dieses Szenario dient nur zu Lernzwecken.  
  
#### <a name="to-create-a-new-chart-report"></a>So erstellen Sie einen neuen Diagrammbericht  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Microsoft SQL Server 2012 Berichts-Generator**, und klicken Sie dann auf **Berichts-Generator**.  
  
     Das Dialogfeld **Erste Schritte** wird angezeigt.  
  
    > [!NOTE]  
    >  Wenn die **Einstieg** Dialogfeld nicht angezeigt werden, klicken Sie auf die Schaltfläche "Berichts-Generator", und klicken Sie dann auf **neu**.  
  
2.  Vergewissern Sie sich, dass im linken Bereich **Neuer Bericht** ausgewählt ist.  
  
3.  Klicken Sie im rechten Bereich auf **Diagramm-Assistent**.  
  
4.  Klicken Sie auf der Seite **Dataset auswählen** auf **Dataset erstellen**und anschließend auf **Weiter**.  
  
5.  Wählen Sie auf der Seite **Verbindung mit einer Datenquelle auswählen** eine vorhandene Datenquelle aus, oder navigieren Sie zum Berichtsserver, und wählen Sie eine Datenquelle aus. Klicken Sie anschließend auf **Weiter**. Möglicherweise müssen Benutzername und Kennwort eingegeben werden.  
  
    > [!NOTE]  
    >  Welche Datenquelle Sie auswählen, ist unwichtig, solange Sie über ausreichende Berechtigungen verfügen. Aus der Datenquelle werden keine Daten abgerufen. Weitere Informationen finden Sie unter [Alternative Methoden zum Herstellen einer Datenverbindung (Berichts-Generator)](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
6.  Klicken Sie auf der Seite **Abfrage entwerfen** auf **Als Text bearbeiten**.  
  
7.  Fügen Sie die folgende Abfrage in den Abfragebereich ein:  
  
    ```  
    SELECT 'Luis' as FirstName, 'Alverca' as LastName, CAST(170000.00 AS money) AS SalesYear2009, CAST(150000. AS money) AS SalesYear2008  
    UNION SELECT 'Jeffrey' as FirstName, 'Zeng' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(190000. AS money) AS SalesYear2008  
    UNION SELECT 'Houman' as FirstName, 'Pournasseh' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Robin' as FirstName, 'Wood' as LastName, CAST(75000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'Daniela' as FirstName, 'Guaita' as LastName,  CAST(170000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'John' as FirstName, 'Yokim' as LastName, CAST(160000. AS money) AS SalesYear2009, CAST(195000. AS money) AS SalesYear2008  
    UNION SELECT 'Delphine' as FirstName, 'Ribaute' as LastName, CAST(180000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Robert' as FirstName, 'Hernady' as LastName, CAST(140000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Tanja' as FirstName, 'Plate' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(160000. AS money) AS SalesYear2008  
    UNION SELECT 'David' as FirstName, 'Bradley' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Michal' as FirstName, 'Jaworski' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(220000. AS money) AS SalesYear2008  
    UNION SELECT 'Chris' as FirstName, 'Ashton' as LastName, CAST(195000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Pongsiri' as FirstName, 'Hirunyanitiwatna' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(215000. AS money) AS SalesYear2008  
    UNION SELECT 'Brian' as FirstName, 'Burke' as LastName, CAST(187000. AS money) AS SalesYear2009, CAST(207000. AS money) AS SalesYear2008  
    ```  
  
8.  (Optional) Klicken Sie auf die Schaltfläche „Ausführen“ (**!**), um die Daten anzuzeigen, auf denen das Diagramm basiert.  
  
9. Klicken Sie auf **Weiter**.  
  
##  <a name="ChartType"></a> 2. Auswählen des Diagrammtyps  
 Sie können aus einer Vielzahl vordefinierter Diagrammtypen auswählen.  
  
#### <a name="to-add-a-column-chart"></a>So fügen Sie einem Bericht ein Säulendiagramm hinzu  
  
1.  Das Säulendiagramm ist der Standarddiagrammtyp der Seite **Diagrammtyp auswählen** .  
  
2.  Klicken Sie auf **Balken**und anschließend auf **Weiter**.  
  
     Auf der **Diagrammfelder** Seite, gibt es vier Felder in der **verfügbare Felder** Bereich: FirstName, LastName, "salesyear2009" und "salesyear2008".  
  
3.  Ziehen Sie "LastName" in den Bereich "Kategorien".  
  
4.  Ziehen Sie "SalesYear2009" in den Bereich "Werte". "SalesYear2009" steht für den Umsatz der einzelnen Vertriebsmitarbeiter im Jahr 2009. Im Bereich Werte wird `[Sum(SalesYear2009)]` angezeigt, da im Diagramm der aggregierte Wert für die einzelnen Produkte angezeigt wird.  
  
5.  Ziehen Sie "SalesYear2008" im Bereich "Werte" unter "SalesYear2009". "SalesYear2008" steht für den Umsatz der einzelnen Vertriebsmitarbeiter im Jahr 2008.  
  
6.  Klicken Sie auf **Weiter**.  
  
7.  Auf der **Auswählen eines Formats** Seite Wählen Sie im Bereich "Formate", eine Art.  
  
     Ein Format dient zum Angeben eines Schriftschnitts, einer Farbpalette und einer Rahmenart. Wenn Sie ein Format auswählen, wird im Vorschaubereich ein Beispiel für das Diagramm mit diesem Format angezeigt.  
  
8.  Klicken Sie auf **Fertig stellen**.  
  
     Das Diagramm wird der Entwurfsoberfläche hinzugefügt.  
  
9. Klicken Sie auf das Diagramm, um die Diagrammziehpunkte anzuzeigen. Ziehen Sie die rechte untere Ecke des Diagramms, um das Diagramm zu vergrößern.  
  
10. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Im Bericht wird das Balkendiagramm für die Umsätze der einzelnen Vertriebsmitarbeiter in den Jahren 2008 und 2009 angezeigt. Die Balkenlänge entspricht dem jeweiligen Gesamtumsatz.  
  
##  <a name="AllValues"></a> 3. Ändern der Darstellung von Namen auf der vertikalen Achse  
 Standardmäßig werden auf der vertikalen Achse nur einige der Werte angezeigt. Sie können das Diagramm so ändern, dass alle Kategorien angezeigt werden.  
  
#### <a name="to-display-all-sales-persons-along-the-category-axis-of-a-bar-chart"></a>So zeigen Sie auf der Kategorieachse eines Balkendiagramms alle Vertriebsmitarbeiter an  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Mit der rechten Maustaste in der vertikalen Achse, und klicken Sie dann auf **Eigenschaften für vertikale Achsen**.  
  
3.  Geben Sie unter **Achsenbereich und -intervall**im Feld **Intervall** den Wert **1**ein.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Mit der rechten Maustaste in der vertikales **Achsentitel** und deaktivieren Sie die **Achsentitel anzeigen** Kontrollkästchen.  
  
6.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
> [!NOTE]  
>  Wenn Sie die Namen der Vertriebsmitarbeiter auf der vertikalen Achse nicht lesen können, können Sie das Diagramm vergrößern oder die Formatierungsoptionen für die Achsenbezeichnungen ändern.  
  
###  <a name="CategoryExpression"></a> Anzeigen der Nachnamen und Vornamen auf der vertikalen Achse  
 Sie können den Kategorieausdruck so ändern, dass die Nach- und Vornamen der einzelnen Vertriebsmitarbeiter angezeigt werden.  
  
##### <a name="to-change-the-category-expression"></a>So ändern Sie den Kategorieausdruck  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Doppelklicken Sie auf das Diagramm, um den Bereich **Diagrammdaten** anzuzeigen.  
  
3.  Klicken Sie mit der rechten Maustaste im Bereich **Kategoriegruppen** auf „[LastName]“, und klicken Sie anschließend auf **Kategoriegruppeneigenschaften**.  
  
4.  Klicken Sie unter "Bezeichnung" auf die Ausdrucksschaltfläche ("Fx").  
  
5.  Geben Sie den folgenden Ausdruck ein: `=Fields!LastName.Value & ", " & Fields!FirstName.Value`  
  
     Durch diesen Ausdruck wird eine Verkettung aus dem Nachnamen, einem Komma und dem Vornamen erstellt.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Sollten beim Ausführen des Berichts keine Vornamen angezeigt werden, können Sie die Daten manuell aktualisieren. Klicken Sie im Vorschaumodus auf der Registerkarte **Ausführen** in der Gruppe **Navigation** auf **Aktualisieren**.  
  
> [!NOTE]  
>  Wenn Sie die Namen der Vertriebsmitarbeiter auf der vertikalen Achse nicht lesen können, können Sie das Diagramm vergrößern oder die Formatierungsoptionen für die Achsenbezeichnungen ändern.  
  
##  <a name="Sort"></a> 4. Ändern der Sortierreihenfolge für Namen auf der vertikalen Achse  
 Beim Sortieren der Daten eines Diagramms wird die Reihenfolge der Werte auf der Kategorieachse geändert.  
  
#### <a name="to-sort-the-names-in-alphabetical-order-on-the-bar-chart"></a>So sortieren Sie die Namen im Balkendiagramm in alphabetischer Reihenfolge  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Doppelklicken Sie auf das Diagramm, um den Bereich **Diagrammdaten** anzuzeigen.  
  
3.  Klicken Sie mit der rechten Maustaste im Bereich **Kategoriegruppen** auf „[LastName]“, und klicken Sie anschließend auf **Kategoriegruppeneigenschaften**.  
  
4.  Klicken Sie auf **Sortierung**. Auf der Seite **Ändern Sie die Sortieroptionen** wird eine Liste mit Sortierausdrücken angezeigt. Standardmäßig enthält diese Liste einen einzelnen Sortierungsausdruck, der dem ursprünglichen Kategoriegruppenausdruck entspricht.  
  
5.  Sortieren nach Klicken Sie auf die Ausdrucksschaltfläche (**Fx**) Schaltfläche.  
  
6.  Geben Sie den folgenden Ausdruck ein: `=Fields!LastName.Value & ", " & Fields!FirstName.Value`  
  
7.  Klicken Sie auf **OK**.  
  
8.  Auf der **Kategoriegruppeneigenschaften** auf der Seite die **Reihenfolge** Dropdown-Liste **Z bis A**. Dadurch wird die umgekehrte alphabetische Reihenfolge ausgewählt, damit die Namen von oben nach unten angezeigt werden.  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Die Namen auf der horizontalen Achse werden in umgekehrter Reihenfolge sortiert, mit **Alerca** am Anfang und **Zeng** am unteren Rand.  
  
##  <a name="Legend"></a> 5. Verschieben der Legende  
 Um die Lesbarkeit der Diagrammwerte zu verbessern, können Sie gegebenenfalls die Diagrammlegende verschieben. So können Sie zum Beispiel in einem Balkendiagramm mit einer horizontalen Anordnung der Balken die Legende oberhalb oder unterhalb des Diagrammbereichs platzieren. Dann bleibt horizontal mehr Platz für die Balken.  
  
#### <a name="to-display-the-legend-below-the-chart-area-of-a-bar-chart"></a>So zeigen Sie die Legende unterhalb des Diagrammbereichs eines Balkendiagramms an  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Legende des Diagramms.  
  
3.  Wählen Sie **Legendeneigenschaften**aus.  
  
4.  Wählen Sie unter **Legendenposition**eine andere Position aus. Legen Sie z. B. eine Position unten in der Mitte fest.  
  
     Wenn Sie die Legende über oder unter einem Diagramm platzieren, ändert sich das Layout der Legende von vertikal zu horizontal. In der Dropdownliste **Layout** können Sie ein anderes Layout auswählen.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="ChartTitle"></a> 6. Benennen des Diagramms  
  
#### <a name="to-change-the-chart-title-above-the-chart-area-of-a-bar-chart"></a>So ändern Sie den Diagrammtitel über dem Diagrammbereich eines Balkendiagramms  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Wählen Sie die Wörter **Diagrammtitel** am oberen Rand des Diagramms, und geben Sie dann den folgenden Text: **Sales for 2008 and 2009**.  
  
3.  Klicken Sie auf eine Stelle außerhalb des Texts.  
  
4.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="Horizontal"></a> 7. Formatieren und Beschriften der horizontalen Achse  
 Standardmäßig werden die Werte auf der horizontalen Achse in einem allgemeinen Format angezeigt, dessen Größe automatisch an die Diagrammgröße angepasst wird.  
  
#### <a name="to-format-the-numbers-on-the-horizontal-axis"></a>So formatieren Sie die Zahlen auf der horizontalen Achse  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Klicken Sie unten im Diagramm auf die horizontale Achse, um sie auszuwählen.  
  
     Auf dem Menüband auf die **Startseite** Registerkarte die **Anzahl** gruppieren, klicken Sie auf die **Währung** Schaltfläche. Die horizontalen Achsenbezeichnungen werden zu Währungsbezeichnungen geändert.  
  
3.  (Optional) Entfernen Sie die Dezimalstellen. Klicken Sie in der Nähe der Schaltfläche **Währung** zweimal auf die Schaltfläche **Dezimalstelle löschen** .  
  
4.  Klicken Sie mit der rechten Maustaste auf die horizontale Achse, und klicken Sie anschließend auf **Eigenschaften für horizontale Achsen**.  
  
5.  Auf der **Anzahl** Registerkarte **Werte in Schritten von Tausend anzeigen.**  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Mit der rechten Maustaste **Achsentitel** , und klicken Sie auf **Achsentiteleigenschaften**.  
  
8.  In der **Titeltext** geben **Sales in Schritten von Tausend** , und klicken Sie auf **OK**.  
  
9. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Auf der horizontalen Achse des Berichts werden die Umsätze als Währung in Tausendern ohne Dezimalstellen angezeigt.  
  
##  <a name="Filter"></a> 8. Hinzufügen eines Filters zum Anzeigen der fünf besten Werte  
 Sie können dem Diagramm einen Filter hinzufügen, um anzugeben, welche Daten des Datasets ein- oder ausgeschlossen werden sollen.  
  
#### <a name="to-add-a-filter-and-display-the-top-five-values"></a>So können Sie einen Filtern hinzufügen und die fünf besten Werte anzeigen  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Doppelklicken Sie auf das Diagramm, um den Bereich **Diagrammdaten** anzuzeigen.  
  
3.  Klicken Sie im Bereich **Kategoriegruppen** mit der rechten Maustaste auf das Feld [LastName]. Klicken Sie danach auf **Kategoriegruppeneigenschaften**.  
  
4.  Klicken Sie auf **Filter**. Die Seite **Filter ändern** zeigt eine Liste von Filterausdrücken an. Standardmäßig ist diese Liste leer.  
  
5.  Klicken Sie auf **Hinzufügen**. Ein neuer leerer Filter wird angezeigt.  
  
6.  In **Ausdruck**, Typ **[Sum(SalesYear2009)]**. Dies erstellt den zugrunde liegenden Ausdruck `=Sum(Fields!SalesYear2009.Value)`, die Sie sehen können, wenn Sie auf die **fx** Schaltfläche.  
  
7.  Überprüfen Sie, ob der Datentyp gleich **Text**ist.  
  
8.  Wählen Sie in **Operator**in der Dropdownliste den Eintrag **Erste N** aus.  
  
9. Geben Sie unter **Wert**den folgenden Ausdruck ein: **=5**  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Sollten die Ergebnisse nicht gefiltert werden, wenn Sie den Bericht ausführen, können Sie die Daten manuell aktualisieren. Klicken Sie auf der Registerkarte **Ausführen** in der Gruppe **Navigation** auf **Aktualisieren**.  
  
 Im Diagramm werden die Namen der fünf besten Vertriebsmitarbeiter gemäß den Umsatzdaten des Jahres 2009 angezeigt.  
  
##  <a name="Title"></a> 9. Hinzufügen eines Berichtstitels  
  
#### <a name="to-add-a-report-title"></a>So fügen Sie einen Berichtstitel hinzu  
  
1.  Klicken Sie auf der Entwurfsoberfläche auf **Zum Hinzufügen eines Titels klicken**.  
  
2.  Typ **Umsatz-Balkendiagramm**, drücken Sie die EINGABETASTE, und geben dann **Top Five-Verkaufsschlager 2009**, sodass sie wie folgt aussieht:  
  
     **Umsatz-Balkendiagramm**  
  
     **Top Five-Verkaufsschlager 2009**  
  
3.  Markieren Sie **Umsatz-Balkendiagramm**, und klicken Sie auf die Schaltfläche **Fett** .  
  
4.  Wählen Sie **Top Five-Verkaufsschlager 2009**, und klicken Sie in der **Schriftart** im Abschnitt der **Startseite** Registerkarte, legen Sie den Schriftgrad auf **10**.  
  
5.  (Optional) Das Textfeld "Titel" muss ggf. vergrößert werden, damit die beiden Textzeilen hineinpassen.  
  
     Dieser Titel wird am Anfang des Berichts angezeigt. Ist keine Kopfzeile definiert, erfüllen die Elemente über dem Berichtshauptteil die Funktion einer Berichtskopfzeile.  
  
6.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="Save"></a> 10. Speichern des Berichts  
  
#### <a name="to-save-the-report"></a>So speichern Sie den Bericht  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Klicken Sie auf die Schaltfläche **Berichts-Generator** und anschließend auf **Speichern unter**.  
  
3.  Geben Sie im Feld **Name**die Zeichenfolge **Umsatz-Balkendiagramm**ein.  
  
4.  Klicken Sie auf **Speichern**.  
  
 Der Bericht wird auf dem Berichtsserver gespeichert.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben das Lernprogramm "Hinzufügen eines Balkendiagramms zu einem Bericht" erfolgreich abgeschlossen. Weitere Informationen zu Diagrammen finden Sie unter [Diagramme (Berichts-Generator und SSRS)](report-design/charts-report-builder-and-ssrs.md) und [Sparklines und Datenbalken (Berichts-Generator und SSRS)](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Lernprogramme &#40;Berichts-Generator&#41;](report-builder-tutorials.md)   
 [Berichts-Generator in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
