---
title: 'Tutorial: Einführung in Ausdrücke | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2d05ef4c-5f91-48b2-8795-f0a201a0b3cc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 79563abac2c6a9ed64dff93667ff3d3966b70bc5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098849"
---
# <a name="tutorial-introducing-expressions"></a>Lernprogramm: Einführung in Ausdrücke
  Mit Ausdrücken können Sie leistungsfähige und flexible Berichte erstellen. In diesem Lernprogramm erfahren Sie, wie Sie Ausdrücke mit allgemeinen Funktionen und Operatoren erstellen und implementieren. Verwenden Sie das Dialogfeld **Ausdruck** , um Ausdrücke zu schreiben, die namens Werte verketten, Werte in einem separaten Dataset suchen, verschiedene Bilder auf der Grundlage von Feldwerten anzeigen usw.  
  
 Der Bericht ist ein Balkenbericht mit abwechselnden Zeilenfarben (Weiß und eine beliebige andere Farbe). Der Bericht enthält einen Parameter zur Auswahl der Farbe für alle Zeilen, die nicht weiß dargestellt werden sollen.  
  
 Die folgende Abbildung zeigt einen Bericht, der mit dem Bericht vergleichbar ist, den Sie erstellen werden.  
  
 ![rs_ExpressionsTutorial](../../2014/tutorials/media/rs-expressionstutorial.gif "rs_ExpressionsTutorial")  
  
##  <a name="BackToTop"></a>Was Sie lernen werden  
 In diesem Lernprogramm lernen Sie Folgendes:  
  
1.  [Erstellen eines Tabellenberichts und eines Datasets mit dem Tabellen- oder Matrix-Assistenten](#Setup)  
  
2.  [Aktualisieren der Standardnamen der Datenquelle und des Datensets](#UpdateNames)  
  
3.  [Anzeigen des Vornamens, des Anfangsbuchstabens des zweiten Vornamens und des Nachnamens](#Concatenate)  
  
4.  [Verwenden von Bildern für die Anzeige des Geschlechts](#Gender)  
  
5.  [Suchen des CountryRegion-Namens](#Lookup)  
  
6.  [Ermitteln der vergangenen Tage seit dem letzten Kauf](#Count)  
  
7.  [Verwenden eines Indikators zur Anzeige des Umsatzvergleichs](#Indicator)  
  
8.  [Erstellen des Berichts als "grüner Balken Bericht"](#GreenBar)  
  
### <a name="other-optional-steps"></a>Weitere optionale Schritte  
  
-   [Formatieren der Datumsspalte](#DateFormat)  
  
-   [Hinzufügen eines Berichts Titels](#Title)  
  
-   [Speichern des Berichts](#Save)  
  
 Geschätzte Zeit zum Bearbeiten dieses Lernprogramms: 30 Minuten  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Weitere Informationen zu den Anforderungen finden Sie unter [Voraussetzungen für Tutorials &#40;Berichts-Generator&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="Setup"></a>1. Erstellen eines Tabellen Berichts und eines Datasets mit dem Tabellen-oder Matrix-Assistenten  
 Erstellen Sie einen Tabellenbericht, eine Datenquelle und ein Dataset. Für den Entwurf der Tabelle werden nur einige wenige Felder verwendet. Nach Fertigstellung des Assistenten werden Sie manuell Spalten hinzufügen. Mit dem Assistenten können Sie die Tabelle einfach gestalten und formatieren.  
  
> [!NOTE]  
>  In diesem Lernprogramm sind die Datenwerte in der Abfrage enthalten, sodass keine externe Datenquelle benötigt wird. Die Abfrage ist daher relativ lang. In einer Geschäftsumgebung wären die Daten nicht in der Abfrage enthalten. Dieses Szenario dient nur zu Lernzwecken.  
  
> [!NOTE]  
>  In diesem Lernprogramm werden die Schritte für den Assistenten in einem Verfahren zusammengefasst. Im ersten Tutorial dieser Reihe erhalten Sie detaillierte Anweisungen zum Navigieren zu einem Berichtsserver, zum Auswählen einer Datenquelle sowie zum Erstellen eines Datasets: [Tutorial: Erstellen eines einfachen Tabellenberichts (Berichts-Generator)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
#### <a name="to-create-a-new-table-report"></a>So erstellen Sie einen neuen Tabellenbericht  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Programme**, klicken Sie auf [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Berichts-Generator**, und klicken Sie dann auf **Berichts-Generator**.  
  
     Das Dialogfeld " **Getting Started** " wird angezeigt.  
  
    > [!NOTE]  
    >  Wenn das Dialogfeld " **Getting Started** " nicht angezeigt wird, klicken Sie auf der Schaltfläche " **Berichts-Generator** " auf **neu**.  
  
    > [!NOTE]  
    >  Wenn Sie die ClickOnce-Version von Berichts-Generator bevorzugen, öffnen Sie Berichts-Manager, und klicken Sie auf **Berichts-Generator**, oder wechseln Sie zu einer SharePoint-Website, auf der Reporting Services Inhaltstypen wie Berichte aktiviert sind, und klicken Sie im Menü **Neues Dokument** auf der Registerkarte **Dokumente** einer freigegebenen Dokumentbibliothek auf **Berichts-Generator Bericht** .  
  
2.  Vergewissern Sie sich, dass im linken Bereich **Neuer Bericht** ausgewählt ist.  
  
3.  Klicken Sie im rechten Bereich auf **Tabellen- oder Matrix-Assistent**.  
  
4.  Klicken Sie auf der Seite **Dataset auswählen** auf **Dataset erstellen**.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Wählen Sie auf der Seite **Verbindung mit einer Datenquelle auswählen** eine Datenquelle vom Typ **SQL Server**aus. Wählen Sie in der Liste eine Datenquelle aus, oder navigieren Sie zum Berichtsserver, um eine Datenquelle auszuwählen.  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Klicken Sie auf der Seite **Abfrage entwerfen** auf **als Text bearbeiten**.  
  
9. Fügen Sie die folgende Abfrage in den Abfragebereich ein:  
  
    ```  
    SELECT 'Lauren' AS FirstName,'Johnson' AS LastName, 'American Samoa' AS StateProvince, 1 AS CountryRegionID,'Unknown' AS Gender, CAST(9996.60 AS money) AS YTDPurchase, CAST('2010-6-10' AS date) AS LastPurchase  
    UNION SELECT'Warren' AS FirstName, 'Pal' AS LastName, 'New South Wales' AS StateProvince, 2 AS CountryRegionID, 'Male' AS Gender, CAST(5747.25 AS money) AS YTDPurchase, CAST('2010-7-3' AS date) AS LastPurchase  
    UNION SELECT 'Fernando' AS FirstName, 'Ross' AS LastName, 'Alberta' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(9248.15 AS money) AS YTDPurchase, CAST('2010-10-17' AS date) AS LastPurchase  
    UNION SELECT 'Rob' AS FirstName, 'Caron' AS LastName, 'Northwest Territories' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(742.50 AS money) AS YTDPurchase, CAST('2010-4-29' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Bailey' AS LastName, 'British Columbia' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(1147.50 AS money) AS YTDPurchase, CAST('2010-6-15' AS date) AS LastPurchase  
    UNION SELECT  'Bridget' AS FirstName, 'She' AS LastName, 'Hamburg' AS StateProvince, 4 AS CountryRegionID, 'Female' AS Gender, CAST(7497.30 AS money) AS YTDPurchase, CAST('2010-5-10' AS date) AS LastPurchase  
    UNION SELECT 'Alexander' AS FirstName, 'Martin' AS LastName, 'Saxony' AS StateProvince, 4 AS CountryRegionID, 'Male' AS Gender, CAST(2997.60 AS money) AS YTDPurchase, CAST('2010-11-19' AS date) AS LastPurchase  
    UNION SELECT 'Yolanda' AS FirstName, 'Sharma' AS LastName ,'Micronesia' AS StateProvince, 5 AS CountryRegionID, 'Female' AS Gender, CAST(3247.95 AS money) AS YTDPurchase, CAST('2010-8-23' AS date) AS LastPurchase  
    UNION SELECT 'Marc' AS FirstName, 'Zimmerman' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1200.00 AS money) AS YTDPurchase, CAST('2010-11-16' AS date) AS LastPurchase  
    UNION SELECT 'Katherine' AS FirstName, 'Abel' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Female' AS Gender, CAST(2025.00 AS money) AS YTDPurchase, CAST('2010-12-1' AS date) AS LastPurchase  
    UNION SELECT 'Nicolas' as FirstName, 'Anand' AS LastName, 'Seine (Paris)' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1425.00 AS money) AS YTDPurchase, CAST('2010-12-11' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Peters' AS LastName, 'England' AS StateProvince, 12 AS CountryRegionID, 'Male' AS Gender, CAST(887.50 AS money) AS YTDPurchase, CAST('2010-8-15' AS date) AS LastPurchase  
    UNION SELECT 'Alison' AS FirstName, 'Nath' AS LastName, 'Alaska' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(607.50 AS money) AS YTDPurchase, CAST('2010-10-13' AS date) AS LastPurchase  
    UNION SELECT 'Grace' AS FirstName, 'Patterson' AS LastName, 'Kansas' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(1215.00 AS money) AS YTDPurchase, CAST('2010-10-18' AS date) AS LastPurchase  
    UNION SELECT 'Bobby' AS FirstName, 'Sanchez' AS LastName, 'North Dakota' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(6191.00 AS money) AS YTDPurchase, CAST('2010-9-17' AS date) AS LastPurchase  
    UNION SELECT 'Charles' AS FirstName, 'Reed' AS LastName, 'Nebraska' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8772.00 AS money) AS YTDPurchase, CAST('2010-8-27' AS date) AS LastPurchase  
    UNION SELECT 'Orlando' AS FirstName, 'Romeo' AS LastName, 'Texas' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8578.00 AS money) AS YTDPurchase, CAST('2010-7-29' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    ```  
  
     Die Abfrage spezifiziert Spaltennamen mit Geburtsname, Vorname, Nachname, Bundesland oder Kanton, Bezeichner für Land bzw. Region, Geschlecht sowie Käufe des laufenden Jahrs.  
  
10. Klicken Sie auf der Symbolleiste des Abfrage-Designers auf **Ausführen** (**!**). Das Resultset umfasst 20 Zeilen mit Daten und umfasst folgenden Spalten: FirstName, LastName, StateProvince, CountryRegionID, Gender, YTDPurchase und LastPurchase.  
  
11. Klicken Sie auf **Weiter**.  
  
12. Ziehen Sie auf der Seite **Felder anordnen** die folgenden Felder in der angegebenen Reihenfolge aus der Liste **Verfügbare Felder** in die Liste **Werte** .  
  
    -   StateProvince  
  
    -   CountryRegionID  
  
    -   LastPurchase  
  
    -   YTDPurchase  
  
     Da CountryRegionID und YTDPurchase numerische Daten enthalten, wird die SUM-Aggregatfunktion standardmäßig auf diese Felder angewendet.  
  
    > [!NOTE]  
    >  Die Felder FirstName und LastName werden nicht eingeschlossen. Sie werden in einem späteren Schritt hinzugefügt.  
  
13. Klicken Sie in der Liste **Werte** mit der `CountryRegionID` rechten Maustaste, und klicken Sie auf die Option **Sum** .  
  
     Sum wird nicht länger auf CountryRegionID angewendet.  
  
14. Klicken Sie in der Liste **Werte** mit der rechten Maustaste auf **YTDPurchase** und klicken Sie anschließend auf die Option **Sum** .  
  
     Sum wird nicht länger auf YTDPurchase angewendet.  
  
15. Klicken Sie auf **Weiter**.  
  
16. Klicken Sie auf der Seite **Layout auswählen** auf **Weiter**.  
  
17. Klicken Sie auf der Seite Format **auswählen** auf **Slate**, und klicken Sie dann auf **Fertig**stellen.  
  
##  <a name="UpdateNames"></a>2. Aktualisieren der Standardnamen der Datenquelle und des Datasets  
  
#### <a name="to-update-the-default-name-of-the-data-source"></a>So aktualisieren Sie den Standardnamen der Datenquelle  
  
1.  Erweitern Sie im Bereich „Berichtsdaten“ den Eintrag **Datenquellen**.  
  
2.  Klicken Sie mit der rechten Maustaste auf **DataSource1** und anschließend auf **Datenquelleneigenschaften**.  
  
3.  Geben Sie im Feld **Name** Folgendes ein: **Datenquelle_für_Ausdrücke**  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-update-the-default-name-of-the-dataset"></a>So aktualisieren Sie den Standardnamen des Datasets  
  
1.  Erweitern Sie im Bereich „Berichtsdaten“ den Eintrag **Datasets**.  
  
2.  Klicken Sie mit der rechten Maustaste auf **DataSet1** und anschließend auf **Dataseteigenschaften**.  
  
3.  Geben Sie im Feld **Name** Folgendes ein: **Ausdrücke**  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Concatenate"></a>3. Anzeigen von Vorname, ursprünglicher Name und Nachname  
 Verwenden Sie die **Left**-Funktion und den **Concatenate (Verketten)** (**&**)-Operator in einem Ausdruck, um einen Namen mit den Anfangsbuchstaben des zweiten Vornamens und dem Nachnamen zu erhalten. Sie können den Ausdruck Schritt für Schritt erstellen oder diesen Teil der Prozedur überspringen und den Ausdruck aus dem Tutorial in das Dialogfeld **Ausdruck** kopieren und einfügen.  
  
#### <a name="to-add-the-name-column"></a>So fügen Sie die Spalte "Name" hinzu  
  
1.  Klicken Sie mit der rechten Maustaste auf die Spalte **StateProvince** , zeigen Sie auf **Spalte einfügen**und klicken Sie auf **Links**.  
  
     Links von der Spalte **StateProvince** wird eine neue Spalte hinzugefügt.  
  
2.  Klicken Sie auf den Titel der neuen Spalte und geben Sie **Name** ein  
  
3.  Klicken Sie mit der rechten Maustaste in die Datenzelle der Spalte **Name** und klicken Sie auf **Ausdruck**.  
  
4.  Erweitern Sie im Dialogfeld **Ausdruck** die Option **Allgemeine Funktionen**und klicken Sie anschließend auf **Text**.  
  
5.  Doppelklicken Sie in der Liste **Element** auf **Left**.  
  
     Die Funktion **Left** wird dem Ausdruck hinzugefügt.  
  
6.  Doppelklicken Sie in der Liste **Kategorie** auf **Felder (Ausdrücke)**.  
  
7.  Doppelklicken Sie in der Liste **Werte** auf **FirstName**.  
  
8.  Geben Sie **, 1)** ein  
  
     Der Ausdruck extrahiert ein Zeichen aus dem Wert **FirstName** , beginnend von links.  
  
9. Geben Sie **& "" ein &**  
  
10. Doppelklicken Sie in der Liste **Werte** auf **LastName**.  
  
     Der vollständige Ausdruck lautet wie folgt: `=Left(Fields!FirstName.Value, 1) &" "& Fields!LastName.Value`  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="Gender"></a>4. Verwenden von Bildern zum Anzeigen von Geschlecht  
 Verwenden Sie Bilder, um das Geschlecht einer Person anzuzeigen, und weisen Sie für den Fall unbekannter Werte ein drittes Bild zu. Sie fügen dem Bericht drei versteckte Bilder und eine neue Spalte für die Bildanzeige hinzu. Sie legen dann fest, welches Bild auf Grundlage des Werts im Feld "Geschlecht" in der Spalte angezeigt wird.  
  
 Um eine Farbe auf die Tabellenzelle anzuwenden, die das Bild enthält, wenn Sie aus dem Bericht einen Balkenbericht machen, fügen Sie zuerst ein Rechteck hinzu und dann das Bild in das Rechteck ein. Sie benötigen das Rechteck, da Sie einem Rechteck eine Hintergrundfarbe zuordnen können, nicht aber einem Bild.  
  
 Das Lernprogramm verwendet Bilder, die mit Windows ausgeliefert werden, Sie können aber auch jedes beliebige andere Bild verwenden. Sie verwenden eingebettete Bilder, die nicht auf Ihrem Computer oder dem Berichtsserver installiert sein müssen.  
  
#### <a name="to-add-images-to-the-report-body"></a>So fügen Sie dem Berichtstext Bilder hinzu  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
2.  Klicken Sie auf der Registerkarte **Einfügen** des Menübands auf **Bild** und anschließend auf den Berichtstext unterhalb der Tabelle.  
  
     Das Dialogfeld **Bildeigenschaften** wird angezeigt.  
  
3.  Klicken Sie auf **Importieren**, und navigieren Sie zu C:\Benutzer\Öffentlich\Öffentliche Bilder\Beispielbilder.  
  
4.  Klicken Sie auf „Pinguine.JPG“ und anschließend auf **Öffnen**.  
  
     Klicken Sie im Dialogfeld **Bildeigenschaften** auf **Sichtbarkeit** und anschließend auf **Ausblenden**.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Wiederholen Sie die Schritte 2 bis 5, diesmal aber mit dem Bild "Koala.JPG".  
  
7.  Wiederholen Sie die Schritte 2 bis 5, diesmal aber mit dem Bild "Tulpen.JPG".  
  
#### <a name="to-add-the-gender-column"></a>So fügen Sie die Spalte "Geschlecht" hinzu  
  
1.  Klicken Sie mit der rechten Maustaste auf die Spalte **Name**, zeigen Sie auf **Spalte einfügen** und klicken Sie anschließend auf **Rechts**.  
  
     Rechts von der Spalte **Name** wird eine neue Spalte hinzugefügt.  
  
2.  Klicken Sie auf den Titel der neuen Spalte und geben Sie **Geschlecht** ein  
  
#### <a name="to-add-a-rectangle"></a>So fügen Sie ein Rechteck hinzu  
  
-   Klicken Sie auf der Registerkarte **Einfügen** im Menüband auf **Rechteck** und anschließend in die Datenzelle der Spalte **Geschlecht**.  
  
     Der Zelle wird ein Rechteck hinzugefügt.  
  
#### <a name="to-add-an-image-to-the-rectangle"></a>So fügen Sie dem Rechteck ein Bild hinzu  
  
1.  Klicken Sie mit der rechten Maustaste auf das Rechteck, zeigen Sie auf **Einsetzen** und klicken Sie anschließend auf **Bild**.  
  
2.  Klicken Sie im Dialogfeld **Bildeigenschaften** auf den Nach unten-Pfeil neben **Dieses Bild verwenden** und wählen Sie eines der hinzugefügten Bilder aus, z.B. „Pinguine.JPG“.  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-use-images-to-show-gender"></a>So verwenden Sie Bilder für die Anzeige des Geschlechts  
  
1.  Klicken Sie mit der rechten Maustaste auf das Bild in der Datenzelle in der Spalte **Geschlecht** und anschließend auf **Bildeigenschaften**.  
  
2.  Klicken Sie im Dialogfeld **Bildeigenschaften** auf die Ausdrucksschaltfläche **fx** neben dem Textfeld **Dieses Bild verwenden**.  
  
3.  Erweitern Sie im Dialogfeld **Ausdruck** die Option **Allgemeine Funktionen** und klicken Sie auf **Programmfluss**.  
  
4.  Doppelklicken Sie in der Liste **Element** auf **Switch**.  
  
5.  Doppelklicken Sie in der Liste **Kategorie** auf **Felder (Ausdrücke)**.  
  
6.  Doppelklicken Sie in der Liste **Werte** auf **Geschlecht**.  
  
7.  Geben Sie **="Männlich", "Koala",** ein  
  
8.  Doppelklicken Sie in der Liste **Werte** auf **Geschlecht**.  
  
9. Geben Sie **="Weiblich", "Pinguine",** ein  
  
10. Doppelklicken Sie in der Liste **Werte** auf **Geschlecht**.  
  
11. Geben Sie **="Unbekannt", "Tulpen")** ein  
  
     Der vollständige Ausdruck lautet wie folgt: `=Switch(Fields!Gender.Value ="Male", "Koala",Fields!Gender.Value ="Female","Penguins",Fields!Gender.Value ="Unknown","Tulips")`  
  
12. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
13. Klicken Sie auf **OK**, um das Dialogfeld **Bildeigenschaften** zu schließen.  
  
14. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="Lookup"></a>5. Suchen Sie den CountryRegion-Namen.  
 Erstellen Sie das CountryRegion-Dataset, und verwenden Sie die **Lookup**-Funktion, um den Namen des Lands/der Region anstelle des Bezeichners des Lands/der Region anzuzeigen.  
  
#### <a name="to-create-the-countryregion-dataset"></a>So erstellen Sie das CountryRegion-Dataset  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
2.  Klicken Sie im Berichtsdaten Bereich auf **neu** , und klicken Sie dann auf **DataSet**.  
  
3.  Klicken Sie auf **Ein in den eigenen Bericht eingebettetes Dataset verwenden**.  
  
4.  Wählen Sie in der Liste **Datenquelle** die Option „Datenquelle_für_Ausdrücke“.  
  
5.  Geben Sie im Feld **Name** Folgendes ein: **CountryRegion**  
  
6.  Überprüfen Sie, ob der Abfragetyp **Text** ausgewählt ist und klicken Sie auf **Abfrage-Designer**.  
  
7.  Klicken Sie auf **Als Text bearbeiten**.  
  
8.  Kopieren Sie die folgende Abfrage, und fügen Sie sie in den Abfragebereich ein:  
  
    ```  
    SELECT 1 AS ID, 'American Samoa' AS CountryRegion  
    UNION SELECT 2 AS CountryRegionID, 'Australia' AS CountryRegion  
    UNION SELECT 3 AS ID, 'Canada' AS CountryRegion  
    UNION SELECT 4 AS ID, 'Germany' AS CountryRegion  
    UNION SELECT 5 AS ID, 'Micronesia' AS CountryRegion  
    UNION SELECT 6 AS ID, 'France' AS CountryRegion  
    UNION SELECT 7 AS ID, 'United States' AS CountryRegion  
    UNION SELECT 8 AS ID, 'Brazil' AS CountryRegion  
    UNION SELECT 9 AS ID, 'Mexico' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Japan' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Australia' AS CountryRegion  
    UNION SELECT 12 AS ID, 'United Kingdom' AS CountryRegion  
    ```  
  
9. Klicken Sie auf **Ausführen** (**!**), um die Abfrage auszuführen.  
  
     Abfrage-Ergebnisse sind die Land/Region-Bezeichner und -Namen.  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. Klicken Sie auf **OK** , um das Dialogfeld **Dataseteigenschaften** zu schließen.  
  
#### <a name="to-look-up-values-in-the-countryregion-dataset"></a>So schlagen Sie Werte im CountryRegion-Dataset nach  
  
1.  Klicken Sie auf den Spaltentitel **Country Region ID** und löschen Sie den Text „ID“.  
  
2.  Klicken Sie mit der rechten Maustaste in die Datenzelle der Spalte **Country Region** und klicken Sie auf **Ausdruck**.  
  
3.  Löschen Sie den Ausdruck bis auf das Gleichheitszeichen (=).  
  
     Der verbleibende Ausdruck lautet: `=`  
  
4.  Erweitern Sie im Dialogfeld **Ausdruck** die Option **Allgemeine Funktionen**, und klicken Sie anschließend auf **Sonstiges**.  
  
5.  Doppelklicken Sie in der Liste **Element** auf **Lookup**.  
  
6.  Doppelklicken Sie in der Liste **Kategorie** auf **Felder (Ausdrücke)**.  
  
7.  Doppelklicken **** Sie `CountryRegionID`in der Liste Werte auf.  
  
8.  Wenn der Cursor nicht bereits unmittelbar nach `CountryRegionID.Value` platziert ist, korrigieren Sie das.  
  
9. Löschen Sie die rechte Klammer und geben Sie anschließend **,Fields!ID.value, Fields!CountryRegion.value, „CountryRegion“)** ein  
  
     Der vollständige Ausdruck lautet wie folgt: `=Lookup(Fields!CountryRegionID.Value,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")`  
  
     Die Syntax der **Lookup**-Funktion spezifiziert eine Suche zwischen CountryRegionID und ID im CountryRegion-Dataset, die den CountryRegion-Wert zurückgibt, der sich ebenfalls im CountryRegion-Dataset befindet.  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="Count"></a>6. Anzahl der Tage seit dem letzten Kauf  
 Fügen Sie eine Spalte hinzu, und **** verwenden Sie anschließend die `ExecutionTime` Now-Funktion oder die integrierte globale Variable, um die Anzahl der Tage seit dem letzten Einkauf einer Person zu berechnen.  
  
#### <a name="to-add-the-days-ago-column"></a>So fügen Sie die Spalte "Vor (n) Tagen)" hinzu  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Last Purchase** , zeigen Sie auf **Spalte einfügen**und klicken Sie auf **Rechts**.  
  
     Rechts von der Spalte **Letzter Kauf** wird eine neue Spalte hinzugefügt.  
  
3.  Geben Sie in der Spaltenüberschrift **Vor (n) Tagen**ein  
  
4.  Klicken Sie mit der rechten Maustaste in die Datenzelle der Spalte **Vor (n) Tagen** und klicken Sie auf **Ausdruck**.  
  
5.  Erweitern Sie im Dialogfeld **Ausdruck** die Option **Allgemeine Funktionen**, und klicken Sie anschließend auf **Datum & Uhrzeit**.  
  
6.  Doppelklicken Sie in der Liste **Elemente** auf **DateDiff**.  
  
7.  Wenn der Cursor nicht bereits unmittelbar nach `DateDiff(` platziert ist, korrigieren Sie das.  
  
8.  Geben Sie **„d“,** ein.  
  
9. Doppelklicken Sie in der Liste **Kategorie** auf **Felder (Ausdrücke)**.  
  
10. Doppelklicken Sie in der Liste **Werte** auf **LastPurchase**.  
  
11. Wenn der Cursor nicht bereits unmittelbar nach `Fields!LastPurchase.Value` platziert ist, korrigieren Sie das.  
  
12. Geben Sie ein **,**  
  
13. Klicken Sie in der Liste **Kategorie** erneut auf **Datum & Uhrzeit**.  
  
14. Doppelklicken Sie in der Liste **Element** auf **Now**.  
  
    > [!WARNING]  
    >  In Produktionsberichten dürfen Sie nicht die **Now** -Funktion in Ausdrücken verwenden, die beim Rendern des Berichts mehrmals ausgewertet werden (z.B. in den Detailzeilen eines Berichts). Der Wert von **Now** ändert sich von Zeile zu Zeile, und die verschiedenen Werte wirken sich auf die Auswertungsergebnisse der Ausdrücke aus, was zu inkonsistenten Resultaten führt. Sie müssen stattdessen die globale Variable `ExecutionTime` verwenden, die von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] bereitgestellt wird.  
  
15. Wenn der Cursor nicht bereits unmittelbar nach `Now(` platziert ist, korrigieren Sie das.  
  
16. Löschen Sie die linke Klammer, und geben Sie **)** ein  
  
     Der vollständige Ausdruck lautet wie folgt: `=DateDiff("d", Fields!LastPurchase.Value, Now)`  
  
17. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Indicator"></a>7. Verwenden eines Indikators zur Anzeige des Umsatz Vergleichs  
 Fügen Sie eine neue Spalte hinzu, und verwenden Sie einen Indikator, um anzuzeigen, ob die Käufe im laufenden Jahr oberhalb oder unterhalb des durchschnittlichen YTD-Einkäufen liegen. Die Funktion **Round** entfernt die Dezimalstellen aus den Werten.  
  
 Für die Konfiguration des Indikators und seiner Zustände sind mehrere Schritte erforderlich. Wenn Sie möchten, können Sie im Verfahren "so konfigurieren Sie den Indikator" fortfahren und die fertigen Ausdrücke aus diesem Tutorial in das Dialogfeld **Ausdruck** kopieren bzw. einfügen.  
  
#### <a name="to-add-the--or---avg-sales-column"></a>So fügen Sie die Spalte "+/- durchschnittl. Käufe" hinzu  
  
1.  Klicken Sie mit der rechten Maustaste auf **YTD Purchase** , zeigen Sie auf **Spalte einfügen**und klicken Sie auf **Rechts**.  
  
     Rechts von der Spalte **YTD Purchase** wird eine neue Spalte hinzugefügt.  
  
2.  Klicken Sie auf den Titel der Spalte und geben Sie **+/- durchschnittl. Käufe** ein  
  
#### <a name="to-add-an-indicator"></a>So fügen Sie einen Indikator hinzu  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** im Menüband auf **Indikator** und anschließend in die Datenzelle der Spalte **+/- durchschnittl. Käufe**.  
  
     Das Dialogfeld **Indikatortyp auswählen** wird geöffnet.  
  
2.  Klicken Sie in der Gruppe **Direktional** der Symbolsätze auf den Satz mit den drei grauen Pfeilen.  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-configure-the-indicator"></a>So konfigurieren Sie den Indikator  
  
1.  Klicken Sie mit der rechten Maustaste auf den Indikator, anschließend auf **Indikatoreigenschaften**und schließlich auf **Wert und Status**.  
  
2.  Klicken Sie auf die Ausdrucksschaltfläche **fx** neben dem Textfeld **Wert** .  
  
3.  Erweitern Sie im Dialogfeld **Ausdruck** die Option **Allgemeine Funktionen**, und klicken Sie anschließend auf **Mathematisch**.  
  
4.  Doppelklicken Sie in der Liste **Element** auf **Round**.  
  
5.  Doppelklicken Sie in der Liste **Kategorie** auf **Felder (Ausdrücke)**.  
  
6.  Doppelklicken Sie in der Liste **Werte** auf **YTDPurchase**.  
  
7.  Wenn der Cursor nicht bereits unmittelbar nach `Fields!YTDPurchase.Value` platziert ist, korrigieren Sie das.  
  
8.  Sorte**-**  
  
9. Erweitern Sie die **Allgemeinen Funktionen** erneut und klicken Sie auf **Aggregat**.  
  
10. Doppelklicken Sie in der Liste **Element** auf **Avg**.  
  
11. Doppelklicken Sie in der Liste **Kategorie** auf **Felder (Ausdrücke)**.  
  
12. Doppelklicken Sie in der Liste **Werte** auf **YTDPurchase**.  
  
13. Wenn der Cursor nicht bereits unmittelbar nach `Fields!YTDPurchase.Value` platziert ist, korrigieren Sie das.  
  
14. Geben Sie **, "Expressions"))** ein  
  
     Der vollständige Ausdruck lautet wie folgt: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions"))`  
  
15. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
16. Wählen Sie als **Maßeinheit für Status****Numerisch**aus.  
  
17. Klicken Sie in der Reihe mit dem Pfeil nach unten auf die Schaltfläche **fx** rechts neben dem Textfeld für den **Start** -Wert.  
  
18. Erweitern Sie im Dialogfeld **Ausdruck** die Option **Allgemeine Funktionen**, und klicken Sie anschließend auf **Mathematisch**.  
  
19. Doppelklicken Sie in der Liste **Element** auf **Round**.  
  
20. Doppelklicken Sie in der Liste **Kategorie** auf **Felder (Ausdrücke)**.  
  
21. Doppelklicken Sie in der Liste **Werte** auf **YTDPurchase**.  
  
22. Wenn der Cursor nicht bereits unmittelbar nach `Fields!YTDPurchase.Value` platziert ist, korrigieren Sie das.  
  
23. Sorte**-**  
  
24. Erweitern Sie die **Allgemeinen Funktionen** erneut und klicken Sie auf **Aggregat**.  
  
25. Doppelklicken Sie in der Liste **Element** auf **Avg**.  
  
26. Doppelklicken Sie in der Liste **Kategorie** auf **Felder (Ausdrücke)**.  
  
27. Doppelklicken Sie in der Liste **Werte** auf **YTDPurchase**.  
  
28. Wenn der Cursor nicht bereits unmittelbar nach `Fields!YTDPurchase.Value` platziert ist, korrigieren Sie das.  
  
29. Geben Sie **, "Expressions")) < 0** ein  
  
     Der vollständige Ausdruck lautet wie folgt: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) < 0`  
  
30. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
31. Geben Sie im Textfeld **Ende** den Wert **0**ein  
  
32. Klicken Sie auf die Zeile mit dem horizontalen Pfeil, und klicken Sie auf **Löschen**.  
  
33. Geben Sie in der Zeile mit dem nach oben zeigenden Pfeil im Feld **Start** den Wert **0**ein  
  
34. Klicken Sie auf die Schaltfläche **fx** rechts neben dem Textfeld für den **Ende** -Wert.  
  
35. Erstellen Sie im Dialogfeld **Ausdruck** den Ausdruck:`=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) >0`  
  
36. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
37. Klicken Sie auf **OK** , um das Dialogfeld **Indikatoreigenschaften** zu schließen.  
  
38. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="GreenBar"></a>8. machen Sie den Bericht zu einem "grünen Balken Bericht".  
 Verwenden Sie einen Parameter, um die Farbe zu bestimmen, die abwechselnd auf die Zeilen im Bericht angewendet wird, um einen Balkenbericht zu erstellen.  
  
#### <a name="to-add-a-parameter"></a>So fügen Sie einen Parameter hinzu  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
2.  Klicken Sie im Bereich **Berichtsdaten** mit der rechten Maustaste auf **Parameter** und anschließend auf **Parameter hinzufügen**.  
  
     Das Dialogfeld **Berichtsparametereigenschaften** wird geöffnet.  
  
3.  Geben Sie in die **Eingabeaufforderung****Farbe auswählen**ein  
  
4.  Geben Sie in **Name****Spaltenfarbe**ein  
  
5.  Klicken Sie im linken Bereich auf **Verfügbare Werte**.  
  
6.  Klicken Sie auf **Werte angeben**.  
  
7.  Klicken Sie auf **Hinzufügen**.  
  
8.  Geben Sie im Feld **Bezeichnung** Folgendes ein: **Gelb** .  
  
9. Geben Sie im Feld **Wert** Folgendes ein: **Gelb**  
  
10. Klicken Sie auf **Hinzufügen**.  
  
11. Geben Sie im Feld **Bezeichnung** Folgendes ein: **Grün**  
  
12. Geben Sie im Feld **Wert** Folgendes ein: **Blassgrün**  
  
13. Klicken Sie auf **Hinzufügen**.  
  
14. Geben Sie im Feld **Bezeichnung** Folgendes ein: **Blau**  
  
15. Geben Sie im Feld **Wert** Folgendes ein: **Hellblau**  
  
16. Klicken Sie auf **Hinzufügen**.  
  
17. Geben Sie im Feld **Bezeichnung** Folgendes ein: **Rosa**  
  
18. Geben Sie im Feld **Wert** Folgendes ein: **Rosa**  
  
19. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-apply-alternating-colors-to-detail-rows"></a>So wenden Sie abwechselnde Farben auf Detailzeilen an  
  
1.  Klicken Sie auf die Registerkarte **Ansicht** auf dem Menüband und überprüfen Sie, ob **Eigenschaften** ausgewählt ist.  
  
2.  Klicken Sie mit der rechten Maustaste in die Datenzelle der Spalte **Name** und drücken Sie die UMSCHALTTASTE.  
  
3.  Klicken Sie nacheinander auf die anderen Zellen in der Zeile.  
  
4.  Klicken Sie im Bereich „Eigenschaften“ auf **BackgroundColor**.  
  
     Wenn die Eigenschaften im Eigenschaftenbereich nach Kategorie angezeigt werden, finden Sie **BackgroundColor** in der Kategorie **Ausfüllen**.  
  
5.  Klicken Sie auf den Pfeil nach unten und anschließend auf **Ausdruck**.  
  
6.  Erweitern Sie im Dialogfeld **Ausdruck** die Option **Allgemeine Funktionen**, und klicken Sie anschließend auf **Programmfluss**.  
  
7.  Doppelklicken Sie in der Liste **Element** auf **IIf**.  
  
8.  Erweitern Sie die **Allgemeinen Funktionen** und klicken Sie auf **Aggregat**.  
  
9. Doppelklicken Sie in der Liste **Element** auf **RunningValue**.  
  
10. Doppelklicken Sie in der Liste **Kategorie** auf **Felder (Ausdrücke)**.  
  
11. Doppelklicken Sie in der Liste **Werte** auf **FirstName**.  
  
12. Wenn der Cursor nicht bereits unmittelbar nach `Fields!FirstName.Value` platziert ist, korrigieren Sie das und geben Sie **,** ein  
  
13. Erweitern Sie die **Allgemeinen Funktionen** und klicken Sie auf **Aggregat**.  
  
14. Doppelklicken Sie in der Liste **Element** auf **Count**.  
  
15. Wenn der Cursor nicht bereits unmittelbar nach `Count(` platziert ist, korrigieren Sie das.  
  
16. Löschen Sie die linke Klammer, und geben Sie **, "Ausdrücke")** ein.  
  
    > [!NOTE]  
    >  "Ausdrücke" ist der Name des Datasets, das zum Zählen der Datenzeilen verwendet wird.  
  
17. Erweitern Sie **Operatoren** und klicken Sie auf **Arithmetisch**.  
  
18. Doppelklicken Sie in der Liste **Element** auf **Mod**.  
  
19. Wenn der Cursor nicht bereits unmittelbar nach `Mod` platziert ist, korrigieren Sie das.  
  
20. Geben Sie **2 =0,** ein  
  
    > [!IMPORTANT]  
    >  Stellen Sie sicher, dass vor der Zahl 2 ein Leerzeichen steht.  
  
21. Klicken Sie auf **Parameter** und doppelklicken Sie in der Liste **Werte** auf **Spaltenfarbe**.  
  
22. Wenn der Cursor nicht bereits unmittelbar nach `Parameters!RowColor.Value` platziert ist, korrigieren Sie das.  
  
23. Geben Sie **, "White")** ein.  
  
     Der vollständige Ausdruck lautet wie folgt: `=IIf(RunningValue(Fields!FirstName.Value,Count, "Expressions") Mod 2 =0, Parameters!RowColor.Value, "White")`  
  
24. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="run-the-report"></a>Führen Sie den Bericht aus  
  
1.  Wenn Sie sich nicht auf der Registerkarte **Stamm** befinden, klicken Sie auf **Stamm**, um zur Entwurfsansicht zurückzukehren.  
  
2.  Klicken Sie auf **Ausführen**.  
  
3.  Wählen Sie in der Dropdownliste **Farbe auswählen** die Farbe für diejenigen Balken im Bericht aus, die nicht weiß sein sollen.  
  
4.  Klicken Sie auf **Bericht anzeigen**.  
  
     Der Bericht wird gerendert und die abwechselnden Zeilen weisen den gewünschten Hintergrund auf.  
  
##  <a name="DateFormat"></a>optionale Formatieren der Datums Spalte  
 Formatieren Sie die Spalte **Last Purchase**, die Datumsangaben enthält.  
  
#### <a name="to-format-date-column"></a>So formatieren Sie die Datumsspalte  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
2.  Klicken Sie mit der rechten Maustaste in die Datenzelle der Spalte **Last Purchase** und klicken Sie anschließend auf **Textfeldeigenschaften**.  
  
3.  Klicken Sie im Dialogfeld **Textfeldeigenschaften** auf **Zahl**, dann auf **Datum** und anschließend auf den Typ **\*31.01.2000**.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Title"></a>optionale Hinzufügen eines Berichts Titels  
 Hinzufügen eines Titels zu einem Bericht  
  
#### <a name="to-add-a-report-title"></a>So fügen Sie einen Berichtstitel hinzu  
  
1.  Klicken Sie auf der Entwurfsoberfläche auf **Zum Hinzufügen eines Titels klicken**.  
  
2.  Geben Sie **Umsatzvergleich – Zusammenfassung** ein, und klicken Sie anschließend auf eine Stelle außerhalb des Textfelds.  
  
3.  Klicken Sie mit der rechten Maustaste auf das Textfeld, das **Umsatzvergleich - Zusammenfassung** enthält und klicken Sie auf **Textfeldeigenschaften**.  
  
4.  Klicken Sie im Dialogfeld **Textfeldeigenschaften** auf **Schriftart**.  
  
5.  Wählen Sie in der Liste **Schriftgrad** den Eintrag **18pt**aus.  
  
6.  Wählen Sie in der Liste **Farbe** die Option **Grau** aus.  
  
7.  Wählen Sie **Fett** und **Kursiv**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Save"></a>optionale Speichern des Berichts  
 Sie können Berichte auf einem Berichtsserver, in einer SharePoint-Bibliothek oder auf dem Computer speichern. Weitere Informationen finden Sie unter [Speichern von Berichten &#40;Berichts-Generator&#41;](report-builder/saving-reports-report-builder.md).  
  
 Speichern Sie in diesem Lernprogramm den Bericht auf einem Berichtsserver. Wenn Sie keinen Zugriff auf einen Berichtsserver besitzen, speichern Sie den Bericht auf dem Computer.  
  
#### <a name="to-save-the-report-to-a-report-server"></a>So speichern Sie den Bericht auf einem Berichtsserver  
  
1.  Klicken Sie in der Schaltfläche **Berichts-Generator** auf **Speichern**unter.  
  
2.  Klicken Sie auf **Letzte Sites und Server**.  
  
3.  Wählen Sie den Namen des Berichtsservers aus, auf dem Sie zum Speichern von Berichten berechtigt sind, oder geben Sie ihn ein.  
  
     Die Meldung "Verbindung mit Berichtsserver wird hergestellt" wird angezeigt. Nachdem die Verbindung hergestellt wurde, sehen Sie den Inhalt des Berichtsordners, den der Berichtsserveradministrator als Standardspeicherort für Berichte angegeben hat.  
  
4.  Ersetzen Sie in **Name** den Standardnamen durch **Umsatzvergleich – Zusammenfassung**.  
  
5.  Klicken Sie auf **Speichern**.  
  
 Der Bericht wird auf dem Berichtsserver gespeichert. Der Name des Berichtsservers, mit dem Sie verbunden sind, wird in der Statusleiste unten im Fenster angezeigt.  
  
#### <a name="to-save-the-report-to-your-computer"></a>So speichern Sie den Bericht auf Ihrem Computer  
  
1.  Klicken Sie in der Schaltfläche **Berichts-Generator** auf **Speichern**unter.  
  
2.  Klicken Sie auf **Desktop**, **Meine Dokumente**oder **Arbeitsplatz**, und navigieren Sie anschließend zu dem Ordner, in dem Sie den Bericht speichern möchten.  
  
3.  Ersetzen Sie in **Name** den Standardnamen durch **Umsatzvergleich – Zusammenfassung**.  
  
4.  Klicken Sie auf **Speichern**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Indikatoren &#40;Berichts-Generator und SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md)   
 [Bilder, Textfelder, Rechtecke und Linien &#40;Berichts-Generator und SSRS&#41;](report-design/rectangles-and-lines-report-builder-and-ssrs.md)   
 [Tabellen (Berichts-Generator und SSRS)](report-design/tables-report-builder-and-ssrs.md)   
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)  
  
  
