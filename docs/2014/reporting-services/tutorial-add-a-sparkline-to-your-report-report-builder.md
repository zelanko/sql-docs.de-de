---
title: 'Tutorial: Hinzufügen einer Sparkline zum Bericht (Berichts-Generator) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 18c90a36-48bf-4805-a960-2d1e8f00c2dc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a543182d5c367be9cc1be875f05c1ab5d4c9bfcf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66099041"
---
# <a name="tutorial-add-a-sparkline-to-your-report-report-builder"></a>Tutorial: Hinzufügen einer Sparkline zum Bericht (Berichts-Generator)
  In diesem Lernprogramm erstellen Sie auf Grundlage der Beispielumsatzdaten einen einfachen Tabellenbericht und fügen anschließend einer Zelle in der Tabelle ein Sparklinediagramm hinzu.  
  
 Eine erweiterte Version des Berichts, den Sie in diesem Lernprogramm erstellen, ist als [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Berichts-Generator-Beispielbericht verfügbar. Weitere Informationen zum Herunterladen dieses Beispielberichts und anderer finden Sie unter [Beispielberichte für Berichts-Generator](https://go.microsoft.com/fwlink/?LinkId=184851). Die folgende Abbildung zeigt den Beispielbericht, der dem Bericht ähnelt, den Sie erstellen.  
  
 ![rs_SparklineMatrixTutorial](../../2014/tutorials/media/rs-sparklinematrixtutorial.gif "rs_SparklineMatrixTutorial")  
  
 Das Video [Vorgehensweise: Erstellen einer Sparkline in einer Tabelle (Video zu Berichts-Generator)](https://technet.microsoft.com/bi/ff871942.aspx) wird veranschaulicht, wie einen ähnlichen Bericht mit Sparklines erstellt.  
  
##  <a name="BackToTop"></a> Lernziele  
 In diesem Lernprogramm lernen Sie Folgendes:  
  
 1. [Erstellen Sie einen Bericht mit einer Tabelle](#CreateTable)  
  
 2. [Erstellen Sie eine Abfrage in der Tabelle oder Matrix-Assistenten](#Query)  
  
 3. [Hinzufügen einer Sparklines zur Tabelle](#Sparkline)  
  
 4. [Vertikales und Horizontales Ausrichten der Sparklines](#AlignSparklines)  
  
### <a name="other-optional-steps"></a>Weitere optionale Schritte  
 5. [Formatieren von Daten als Währung](#FormatCurrency)  
  
 6. [Formatieren von Daten als Datumsangaben](#FormatDates)  
  
 7. [Ändern der Spaltenbreite](#Width)  
  
 8. [Hinzufügen eines Berichtstitels](#Title)  
  
 9. [Speichern des Berichts](#Save)  
  
 Ungefähre Dauer dieses Lernprogramms: 30 Minuten.  
  
## <a name="requirements"></a>Anforderungen  
 Weitere Informationen zu den Anforderungen finden Sie unter [Voraussetzungen für Tutorials &#40;Berichts-Generator&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="CreateTable"></a> 1. Erstellen eines Berichts mit einer Tabelle  
  
#### <a name="to-create-a-report"></a>So erstellen Sie einen Bericht  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Microsoft SQL Server 2012 Berichts-Generator**, und klicken Sie dann auf **Berichts-Generator**.  
  
     Die **Einstieg** Dialogfeld wird geöffnet.  
  
    > [!NOTE]  
    >  Wenn die **Einstieg** Dialogfeld nicht angezeigt wird, aus der **Berichts-Generator** , zeigen Sie auf **neu**.  
  
2.  Vergewissern Sie sich, dass im linken Bereich **Neuer Bericht** ausgewählt ist.  
  
3.  Klicken Sie im rechten Bereich auf **Tabellen- oder Matrix-Assistent**.  
  
4.  Klicken Sie auf der Seite **Dataset auswählen** auf **Dataset erstellen**und anschließend auf **Weiter**. Die Seite **Verbindung mit einer Datenquelle auswählen** wird geöffnet.  
  
    > [!NOTE]  
    >  Für dieses Lernprogramm sind keine bestimmten Daten erforderlich; es wird lediglich eine Verbindung mit einer [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] -Datenbank benötigt. Wenn unter **Datenquellenverbindungen** bereits eine Datenquellenverbindung aufgeführt ist, können Sie sie auswählen und zu Schritt 10 wechseln. Weitere Informationen finden Sie unter [Alternative Methoden zum Herstellen einer Datenverbindung (Berichts-Generator)](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
5.  Klicken Sie auf **Neu**. Das Dialogfeld **Datenquelleneigenschaften** wird angezeigt.  
  
6.  Geben Sie im Feld **Name**den Namen **Product Sales**für die Datenquelle ein.  
  
7.  Vergewissern Sie sich, dass unter **Verbindungstyp auswählen**die Option **Microsoft SQL Server** ausgewählt ist.  
  
8.  Geben Sie für **Verbindungszeichenfolge**den folgenden Text ein:  
  
     **Datenquelle =\<Servername >**  
  
     Der Ausdruck \<Servername >, z.B. Report001, bezeichnet einen Computer, auf dem eine Instanz von SQL Server-Datenbankmoduls installiert ist. Da die Berichtsdaten nicht aus einer SQL Server-Datenbank extrahiert werden, muss der Name einer Datenbank nicht eingeschlossen werden. Die Standarddatenbank auf dem angegebenen Server wird verwendet, um die Abfrage zu analysieren.  
  
9. Klicken Sie auf **Anmeldeinformationen**. Geben Sie die für den Zugriff auf die externe Datenquelle benötigten Anmeldeinformationen ein.  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Nun wird wieder die Seite **Verbindung mit einer Datenquelle auswählen** angezeigt.  
  
11. Klicken Sie auf **Verbindung testen**, um sicherzustellen, dass die Verbindung mit der Datenquelle hergestellt werden kann.  
  
     Die Meldung "Die Verbindung wurde erfolgreich hergestellt" wird angezeigt.  
  
12. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
13. Klicken Sie auf **Weiter**.  
  
##  <a name="Query"></a> 2. Erstellen einer Abfrage im Tabellen-Assistenten  
 In einem Bericht können Sie ein freigegebenes Dataset mit einer vordefinierten Abfrage verwenden oder ein eingebettetes Dataset erstellen, das nur in Ihrem Bericht verwendet wird. In diesem Lernprogramm erstellen Sie ein eingebettetes Dataset.  
  
> [!NOTE]  
>  In diesem Lernprogramm sind die Datenwerte in der Abfrage enthalten, sodass keine externe Datenquelle benötigt wird. Die Abfrage ist daher relativ lang. In einer Geschäftsumgebung wären die Daten nicht in der Abfrage enthalten. Dieses Szenario dient nur zu Lernzwecken.  
  
#### <a name="to-create-a-query"></a>So erstellen Sie eine Abfrage  
  
1.  Auf der Seite **Abfrage entwerfen** ist der relationale Abfrage-Designer geöffnet. Für dieses Lernprogramm verwenden Sie den textbasierten Abfrage-Designer.  
  
2.  Klicken Sie auf **Als Text bearbeiten**. Der textbasierte Abfrage-Designer umfasst zwei Bereiche: den Abfragebereich und den Ergebnisbereich.  
  
3.  Fügen Sie die folgende [!INCLUDE[tsql](../includes/tsql-md.md)] -Abfrage in das Feld **Abfrage** ein.  
  
    ```  
    SELECT CAST('2010-01-04' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Carrying Case' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2010-01-10' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Carrying Case' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2010-01-04' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Budget Movie-Maker' as Product, CAST(1056.00 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate,  'Accessories' as Subcategory,  
       'Slim Digital' as Product, CAST(1380.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate,'Accessories' as Subcategory,    
       'Budget Movie-Maker' as Product, CAST(780.00 AS money) AS Sales, 26 as Quantity  
    UNION SELECT CAST('2010-01-07' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3798.00 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2010-01-08' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(10400.00 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2010-01-09' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3000.00 AS money) AS Sales, 60 as Quantity  
    UNION SELECT CAST('2010-01-10' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(7234.50 AS money) AS Sales, 39 as Quantity  
    UNION SELECT CAST('2010-01-06' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Carrying Case' as Product, CAST(10836.00 AS money) AS Sales, 84 as Quantity  
    UNION SELECT CAST('2010-01-07' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(2550.00 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2010-01-04' AS date) as SalesDate, 'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2010-01-08' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'Slim Digital' as Product, CAST(18530.00 AS money) AS Sales, 34 as Quantity  
    UNION SELECT CAST('2010-01-06' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'Slim Digital' as Product, CAST(26576.00 AS money) AS Sales, 88 as Quantity  
    ```  
  
4.  Klicken Sie auf der Symbolleiste des Abfrage-Designers auf „Ausführen“ ( **!** ).  
  
     Die Abfrage wird ausgeführt, und das Resultset für die Felder **SalesDate**, **Subcategory**, **Product**, **Sales**und **Quantity**wird angezeigt.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Ziehen Sie auf der Seite **Felder anordnen** das Feld **Sales** in **Werte**.  
  
     **Sales** wird von der Sum-Funktion aggregiert. Der Wert ist "[Sum(Sales)]".  
  
7.  Ziehen Sie **Product** in **Zeilengruppen**.  
  
8.  Ziehen Sie **SalesDate** in **Spaltengruppen**.  
  
9. Klicken Sie auf **Weiter**.  
  
10. Vergewissern Sie sich auf der Seite **Layout auswählen** , dass unter **Optionen**die Option **Teil- und Gesamtergebnisse anzeigen** ausgewählt ist.  
  
     Im Vorschaubereich des Assistenten wird eine Tabelle mit drei Zeilen angezeigt. Bei der Ausführung des Berichts wird jede Zeile wie folgt angezeigt:  
  
    1.  Die erste Zeile erscheint einmal, damit Spaltenüberschriften in der Tabelle angezeigt werden.  
  
    2.  Die zweite Zeile wird einmal für jedes Produkt wiederholt. In dieser Zeile werden Produktname, Summe pro Tag und die Zeilensumme angezeigt.  
  
    3.  Die dritte Zeile erscheint einmal, damit Gesamtsummen in der Tabelle angezeigt werden.  
  
11. Klicken Sie auf **Weiter**.  
  
12. Wählen Sie auf der Seite **Format auswählen** im Bereich **Formate** die Option **Schiefer**aus.  
  
     Im Vorschaubereich wird ein Beispiel für die Tabelle mit diesem Format angezeigt.  
  
13. Klicken Sie auf **Fertig stellen**.  
  
14. Die Tabelle wird der Entwurfsoberfläche hinzugefügt. Die Tabelle enthält drei Spalten und drei Zeilen.  
  
     Betrachten Sie den Gruppierungsbereich. Wenn der Gruppierungsbereich nicht angezeigt wird, klicken Sie im Menü **Ansicht** auf **Gruppierung**. Im Bereich Zeilengruppen wird eine Zeilengruppe angezeigt: **Product**. Im spaltengruppenbereich wird eine Spaltengruppe angezeigt: **SalesDate**. Detaildaten sind alle Daten, die von der Datasetabfrage abgerufen werden.  
  
15. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="Sparkline"></a> 3. Hinzufügen einer Sparkline  
  
#### <a name="to-add-a-sparkline-chart-to-a-table"></a>So fügen Sie einer Tabelle ein Sparklinediagramm hinzu  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
2.  Wählen Sie die Summenspalte in der Tabelle aus.  
  
3.  Führen Sie einen Rechtsklick aus, zeigen Sie auf **Spalte einfügen**, und klicken Sie anschließend auf **Links**.  
  
4.  Die neue Spalte, mit der Maustaste in die Zeile [Product], zeigen Sie auf die **einfügen** Registerkarte des Menübands, und klicken Sie dann auf **Sparkline**.  
  
5.  Stellen Sie sicher, dass die erste Sparkline in der **Spalte** Zeile ausgewählt ist, und klicken Sie dann auf **OK**.  
  
6.  Klicken Sie zum Anzeigen des Diagrammdatenbereichs auf die Sparkline.  
  
7.  Klicken Sie auf das Pluszeichen (+) im Wertefeld anmelden, und klicken Sie dann auf **Sales**.  
  
     Die Werte im Feld **Sales** sind nun die Werte für die Sparkline.  
  
8.  Klicken Sie auf das Pluszeichen (+), melden Sie sich kategoriegruppenfeld, und klicken Sie dann auf **"salesdate"** .  
  
9. Klicken Sie auf **Ausführen** , um den Bericht in der Vorschau anzuzeigen.  
  
     In jeder Zeile der Tabelle sind Sparklinediagramme enthalten, die jedoch nicht korrekt sind. Die Balken in den Diagrammen weisen nicht die gleiche Breite auf. In der zweiten Datenzeile befinden sich nur vier Balken, weshalb die Balken breiter als in der ersten Zeile sind, die sechs Balken enthält. Werte für die einzelnen Produkte können nicht pro Tag verglichen werden. Sie müssen die gleiche Breite aufweisen.  
  
     Für jede Zeile entspricht die maximale Balkenlänge der jeweiligen Höhe der Zeile. Dies ist ebenfalls irreführend, da die größten Werte für jede Zeile nicht identisch sind: der größte Wert für Budget Movie-Maker ist USD 10.400, aber der größte Wert für Slim Digital beträgt USD 26.576 – mehr als doppelt so groß ist. Dennoch sind die größten Balken in diesen zwei Zeilen etwa gleich hoch. Auch das muss an die anderen Sparklines angepasst werden.  
  
     ![rs_SprklineMtrxUnaligndBars](../../2014/tutorials/media/rs-sprklinemtrxunaligndbars.gif "rs_SprklineMtrxUnaligndBars")  
  
##  <a name="AlignSparklines"></a> 4. Vertikales und horizontales Ausrichten der Sparklines  
 Die Sparklines sind schwierig zu lesen, wenn sie alle der gleiche Maßstab verwendet nicht. Sowohl die horizontale als auch die vertikale Achse muss mit dem Rest übereinstimmen.  
  
#### <a name="to-set-alignment-for-the-sparklines-in-the-table"></a>So legen Sie die Ausrichtung für die Sparklines in der Tabelle fest  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Sparkline, und klicken Sie auf **Eigenschaften für vertikale Achsen**.  
  
3.  Aktivieren Sie das Kontrollkästchen **Achsen ausrichten in** .  
  
     Tablix1 wird in der Liste angezeigt. Das ist die einzige Option. Dadurch wird die Höhe der Balken in jeder Sparkline relativ zu den anderen Balken festgelegt.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Sparkline, und klicken Sie auf **Eigenschaften für horizontale Achsen**.  
  
6.  Aktivieren Sie das Kontrollkästchen **Achsen ausrichten in** .  
  
     Tablix1 wird in der Liste angezeigt. Das ist die einzige Option. Dadurch wird die Breite der Balken in jeder Sparkline relativ zu den anderen Balken festgelegt. Wenn in einigen Sparklines weniger Balken enthalten sind, enthalten diese Sparklines Leerräume für die fehlenden Daten.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie auf **Ausführen** , um den Bericht erneut in der Vorschau anzuzeigen.  
  
 Die Ausrichtung aller Balken entspricht nun der der Balken in den anderen Zeilen.  
  
##  <a name="FormatCurrency"></a> 5. (Optional) Formatieren von Daten als Währung  
 Die Zusammenfassungsdaten für das Feld **Sales** werden standardmäßig als eine Zahl im Standardzahlenformat angezeigt. Formatieren Sie das Feld, um die Zahl als Währung anzuzeigen. Ändern Sie die Einstellung der Option **Platzhalterformate** , um formatierte Textfelder und Platzhaltertext als Beispielwerte anzuzeigen.  
  
#### <a name="to-format-a-currency-field"></a>So formatieren Sie ein Währungsfeld  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zu wechseln.  
  
2.  Klicken Sie auf die Zelle in der zweiten Zeile (unter der Zeile mit den Spaltenüberschriften) in der **"salesdate"** Spalte, und ziehen Sie, um alle Zellen auszuwählen, die enthalten `[Sum(Sales)]`.  
  
3.  Klicken Sie auf der Registerkarte **Stamm** in der Gruppe **Zahl** auf die Schaltfläche **Währung** . Die Zellen ändern sich, um die formatierte Währung anzuzeigen.  
  
     Wenn Sie das Gebietsschema „Deutsch (Deutschland)“ verwenden, lautet der Standardbeispieltext [**12,345.00€**]. Wenn Sie kein beispielwährungswert angezeigt werden, klicken Sie auf **Platzhalterformate** in die **Zahlen** gruppieren, und klicken Sie dann auf **Beispielwerte**.  
  
4.  Klicken Sie auf **Ausführen** , um den Bericht in der Vorschau anzuzeigen.  
  
 Die Zusammenfassungswerte für **Sales** werden als Währung angezeigt.  
  
##  <a name="FormatDates"></a> 6. Formatieren von Daten als Datumsangaben (optional)  
 Im Feld **SalesDate** werden standardmäßig sowohl Datums- als auch Zeitangaben angezeigt. Durch entsprechende Formatierung kann auch nur das Datum angezeigt werden.  
  
#### <a name="to-format-a-date-field-as-the-default-format"></a>So formatieren Sie ein Datumsfeld als Standardformat  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
2.  Klicken Sie auf die Zelle, die `[SalesDate]`enthält.  
  
3.  Auf dem Menüband auf die **Startseite** Registerkarte die **Anzahl** Gruppe wählen Sie in der Dropdown-Liste **Datum**.  
  
     In der Zelle wird das Beispieldatum **[31.01.2000]** angezeigt. Falls kein Beispieldatum angezeigt wird, klicken Sie in der Gruppe **Zahlen** auf **Platzhalterformate** und anschließend auf **Beispielwerte**.  
  
4.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Die **"salesdate"** -Werte werden im Standarddatumsformat angezeigt.  
  
##  <a name="Width"></a> 7. Ändern der Spaltenbreite (optional)  
 Standardmäßig enthält jede Zelle in einer Tabelle ein Textfeld. Textfelder werden beim Rendern der Seite entsprechend dem anzuzeigenden Text vertikal erweitert. Im gerenderten Bericht werden alle Zeilen auf die Höhe des größten gerenderten Textfelds in der Zeile vergrößert. Die Höhe der Zeile auf der Entwurfsoberfläche hat keinen Einfluss auf die Höhe der Zeile im gerenderten Bericht.  
  
 Um die Höhe der Zeilen zu reduzieren, vergrößern Sie die Spaltenbreite, sodass der erwartete Inhalt der Textfelder in der Spalte in einer Zeile untergebracht werden kann.  
  
#### <a name="to-change-the-width-of-columns"></a>So ändern Sie die Breite von Spalten  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
2.  Klicken Sie auf die Tabelle, damit die Spalten- und Zeilenhandles über und neben der Tabelle angezeigt werden.  
  
     Die grauen Balken oberhalb und neben der Tabelle stellen die Spalten- und Zeilenhandles dar.  
  
3.  Zeigen Sie auf die Zeile zwischen Spaltenhandles, sodass sich der Cursor in einen Doppelpfeil ändert. Ziehen Sie die Spalten auf die gewünschte Größe. Erweitern Sie beispielsweise die Spalte für **Produkt** , damit der Produktname auf einer Zeile angezeigt.  
  
4.  Klicken Sie auf **Ausführen** , um den Bericht in der Vorschau anzuzeigen.  
  
##  <a name="Title"></a> 8. Hinzufügen eines Berichtstitels (optional)  
 Ein Berichtstitel wird oben im Bericht angezeigt. Sie können den Berichtstitel in eine Berichtskopfzeile einfügen oder, wenn der Bericht keine Kopfzeile enthält, in einem Textfeld am oberen Rand des Berichtshauptteils. In diesem Lernprogramm verwenden Sie das Textfeld, das automatisch am oberen Rand des Berichtshauptteils platziert wird.  
  
 Die Darstellung des Texts kann weiter verbessert werden, indem andere Schriftschnitte, Größen und Farben für Ausdrücke und einzelne Zeichen des Texts angewendet werden. Weitere Informationen finden Sie unter [Formatieren von Text in einem Textfeld (Berichts-Generator und SSRS)](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).  
  
#### <a name="to-add-a-report-title"></a>So fügen Sie einen Berichtstitel hinzu  
  
1.  Klicken Sie auf der Entwurfsoberfläche auf **Zum Hinzufügen eines Titels klicken**.  
  
2.  Geben Sie **Product Sales**ein, und klicken Sie anschließend außerhalb des Textfelds.  
  
3.  Klicken Sie mit der rechten Maustaste auf das Textfeld, das **Product Sales** enthält, und klicken Sie auf **Textfeldeigenschaften**.  
  
4.  Klicken Sie im Dialogfeld **Textfeldeigenschaften** auf **Schriftart**.  
  
5.  Wählen Sie in der Liste **Schriftgrad** den Eintrag **18pt**aus.  
  
6.  In der **Farbe** Liste **Kastanienbraun**.  
  
7.  Wählen Sie **Fett**aus.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Save"></a> 9. Speichern des Berichts  
 Speichern Sie den Bericht auf einem Berichtsserver oder auf Ihrem Computer. Wenn Sie den Bericht nicht auf dem Berichtsserver speichern, ist eine Reihe von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Funktionen nicht verfügbar, z. B. Berichtsteile und Unterberichte.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>So speichern Sie den Bericht auf einem Berichtsserver  
  
1.  Klicken Sie auf die Schaltfläche **Berichts-Generator** und anschließend auf **Speichern unter**.  
  
2.  Klicken Sie auf **Letzte Sites und Server**.  
  
3.  Wählen Sie den Namen des Berichtsservers aus, auf dem Sie zum Speichern von Berichten berechtigt sind, oder geben Sie ihn ein.  
  
     Die Meldung "Verbindung mit Berichtsserver wird hergestellt" wird angezeigt. Nachdem die Verbindung hergestellt wurde, sehen Sie den Inhalt des Berichtsordners, den der Berichtsserveradministrator als Standardspeicherort für Berichte angegeben hat.  
  
4.  Ersetzen Sie im Feld **Name**den Standardnamen durch **Product Sales**.  
  
5.  Klicken Sie auf **Speichern**.  
  
 Der Bericht wird auf dem Berichtsserver gespeichert. Der Name des Berichtsservers, mit dem Sie verbunden sind, wird in der Statusleiste unten im Fenster angezeigt.  
  
#### <a name="to-save-the-report-on-your-computer"></a>So speichern Sie den Bericht auf dem Computer  
  
1.  Klicken Sie auf die Schaltfläche **Berichts-Generator** und anschließend auf **Speichern unter**.  
  
2.  Klicken Sie auf **Desktop**, **Eigene Dokumente**oder **Computer**, und navigieren Sie zu dem Ordner, in dem Sie den Bericht speichern möchten.  
  
3.  Ersetzen Sie im Feld **Name**den Standardnamen durch **Product Sales**.  
  
4.  Klicken Sie auf **Speichern**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Hiermit ist das Lernprogramm zum Erstellen eines Tabellenberichts mit Sparklinediagrammen abgeschlossen. Weitere Informationen zu Sparklines finden Sie unter [Sparklines und Datenbalken &#40;Berichts-Generator und SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Lernprogramme &#40;Berichts-Generator&#41;](report-builder-tutorials.md)   
 [Berichts-Generator in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
