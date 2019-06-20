---
title: 'Tutorial: Erstellen eines Freiformberichts (Berichts-Generator) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 87288b59-faf2-4b1d-a8e4-a7582baedf2f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 332c67f47c8096cbeb5a94c4e2a288cd532038cf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66098952"
---
# <a name="tutorial-creating-a-free-form-report-report-builder"></a>Tutorial: Erstellen eines Freiformberichts (Berichts-Generator)
  Dieses Lernprogramm zeigt Ihnen, wie Sie einen SSRS-Freiformbericht erstellen, der einem Formularbrief gleicht. Sie können Berichtselemente zu einem Formular mit Textfeldern, Bildern und anderen Datenbereichen anordnen.  
  
 Der Bericht, den Sie in diesem Lernprogramm erstellen, basiert auf Beispielumsatzdaten, die im Lernprogramm enthalten sind. Im Bericht werden Informationen nach Gebiet gruppiert und der Name des Vertriebsmanagers für das Gebiet sowie ausführliche und zusammenfassende Umsatzdaten angezeigt. Der Listendatenbereich wird als Grundlage für den formfreien Bericht verwendet. Anschließend werden folgende Objekte hinzugefügt: ein dekorativer Bereich mit einem Bild, statischer Text mit eingefügten Daten, eine Tabelle zum Anzeigen ausführlicher Informationen und optional Kreis- und Säulendiagramme zum Anzeigen von Zusammenfassungsinformationen.  
  
##  <a name="BackToTop"></a> Lernziele  
 In diesem Lernprogramm lernen Sie Folgendes:  
  
-   [Erstellen eines leeren Berichts, Datenquelle, und eines Datasets](#BlankReport)  
  
-   [Hinzufügen und Konfigurieren einer Liste](#List)  
  
-   [Hinzufügen von Grafiken](#Graphics)  
  
-   [Hinzufügen von Freitext](#Text)  
  
-   [Hinzufügen einer Tabelle zum Anzeigen von Details](#Table)  
  
-   [Formatieren von Daten](#Format)  
  
-   [Speichern des Berichts](#Save)  
  
### <a name="other-optional-steps"></a>Weitere optionale Schritte  
  
-   [Hinzufügen einer Zeile zum Trennen von Bereichen des Berichts](#Line)  
  
-   [Hinzufügen von Zusammenfassungsdatenvisualisierung](#Visualization)  
  
 Ungefähre Dauer dieses Lernprogramms: 20 Minuten.  
  
## <a name="requirements"></a>Anforderungen  
 Weitere Informationen zu den Anforderungen finden Sie unter [Voraussetzungen für Tutorials &#40;Berichts-Generator&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="BlankReport"></a> 1. Erstellen eines leeren Berichts, einer leeren Datenquelle und eines leeren Datasets  
  
> [!NOTE]  
>  In diesem Lernprogramm sind die Datenwerte in der Abfrage enthalten, sodass keine externe Datenquelle für den Bericht benötigt wird. Die Verwendung dieser Art von internen Daten eignet sich hervorragend für Lernzwecke, aber macht die Abfrage lang. .  
  
#### <a name="to-create-a-blank-report"></a>So erstellen Sie einen leeren Bericht  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Microsoft SQL Server 2012 Berichts-Generator**, und klicken Sie dann auf **Berichts-Generator**.  
  
    > [!NOTE]  
    >  Das Dialogfeld **Erste Schritte** wird angezeigt. Wenn dies nicht der Fall ist, klicken Sie auf der Schaltfläche des Berichts-Generators auf **Neu**.  
  
2.  Vergewissern Sie sich links im Dialogfeld **Erste Schritte** , dass die Option **Neuer Bericht** ausgewählt ist.  
  
3.  Klicken Sie im rechten Bereich auf **Leerer Bericht**.  
  
#### <a name="to-create-a-new-data-source"></a>So erstellen Sie eine neue Datenquelle  
  
1.  Klicken Sie im Berichtsdatenbereich auf **Neu**, und klicken Sie dann auf **Datenquelle**.  
  
2.  In der `Name` geben: **ListDataSource**.  
  
3.  Klicken Sie auf **In Bericht eingebettete Verbindung verwenden**.  
  
4.  Überprüfen Sie, ob der Verbindungstyp Microsoft SQL Server ist, und geben Sie anschließend im Feld **Verbindungszeichenfolge** Folgendes ein: **Data Source = \<servername>**  
  
     \<Servername >, z.B. Report001, bezeichnet einen Computer, auf dem eine Instanz von SQL Server-Datenbankmoduls installiert ist. Da die Berichtsdaten nicht aus einer SQL Server-Datenbank extrahiert werden, muss der Name einer Datenbank nicht eingeschlossen werden. Die Standarddatenbank auf dem angegebenen Server wird verwendet, um die Abfrage zu analysieren.  
  
5.  Klicken Sie auf **Anmeldeinformationen**und geben Sie die zur Verbindung mit der Instanz der SQL Server-Datenbank-Engine benötigten Anmeldeinformationen ein.  
  
6.  Klicken Sie auf **OK**.  
  
#### <a name="to-create-a-new-dataset"></a>So erstellen Sie ein neues Dataset  
  
1.  Klicken Sie im Berichtsdatenbereich auf **Neu**und anschließend auf **Dataset**.  
  
2.  In der `Name` geben: **ListDataset.**  
  
3.  Klicken Sie auf **Ein in den eigenen Bericht eingebettetes Dataset verwenden**und überprüfen Sie, ob **ListDataSource**die Datenquelle ist.  
  
4.  Überprüfen Sie, ob der Abfragetyp **Text** ausgewählt ist, und klicken Sie anschließend auf **Abfrage-Designer**.  
  
5.  Klicken Sie auf **Als Text bearbeiten**.  
  
6.  Kopieren Sie die folgende Abfrage, und fügen Sie sie in den Abfragebereich ein:  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity  
    ```  
  
7.  Klicken Sie auf das Symbol „Ausführen“, um die Abfrage auszuführen.  
  
     Bei den Abfrageergebnissen handelt es sich um die Daten, die im Bericht angezeigt werden können.  
  
     ![Abfragedesigner](../../2014/tutorials/media/tutorial-querydesigner.png "Abfragedesigner")  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="List"></a> 2. Hinzufügen und Konfigurieren einer Liste  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] stellt drei Datenbereichsvorlagen bereit: Tabelle, Matrix und Liste. Diese Vorlagen basieren alle auf einem Tablix-Datenbereich.  
  
 In diesem Lernprogramm verwenden Sie eine Liste, um die Umsatzdaten für Vertriebsgebiete in einem Bericht anzuzeigen, der einem Newsletter ähnelt. Die Informationen werden nach Gebiet gruppiert. Sie fügen eine neue Zeilengruppe hinzu, in der Daten nach Gebiet gruppiert werden, und löschen dann die integrierte Zeilengruppe "Details". Die Listenvorlage ist ideal zum Erstellen von Freiformberichten. Weitere Informationen finden Sie unter [listet &#40;Berichts-Generator und SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Für diesen Bericht werden als Papierformat Letter (21,6 x 28) und Ränder mit einer Breite von ca. 2,5 cm verwendet. Eine Berichtsseite, die höher als 22,9 cm oder breiter als 16,5 cm ist, kann zu leeren Seiten führen.  
  
#### <a name="to-add-a-list"></a>So fügen Sie eine Liste hinzu  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** des Menübands im Bereich **Datenbereiche** auf **Liste** , und ziehen Sie dann die Liste in den Berichtstext. Legen Sie für die Liste eine Höhe von 17,8 cm und eine Breite von 15,9 cm fest.  
  
2.  Klicken Sie in die Liste, klicken Sie mit Rechtsklick auf den oberen Rand der Liste, und klicken Sie dann auf **Tablix-Eigenschaften**.  
  
     ![Hinzufügen einer Liste](../../2014/tutorials/media/tutorial-addinglistwithnumbers.png "Hinzufügen einer Liste")  
  
3.  Wählen Sie in der Dropdownliste **Datasetname** die Option **ListDataset**aus.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Klicken Sie mit der rechten Maustaste in die Liste und anschließend auf **Rechteckeigenschaften**.  
  
     ![Rechteckeigenschaften (Befehl)](../../2014/tutorials/media/tutorial-rectanglepropertiescommand.png "Rechteckeigenschaften-Befehl")  
  
6.  Aktivieren Sie auf der Registerkarte **Allgemein** das Kontrollkästchen **Seitenumbruch hinzufügen nach** .  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-add-a-new-row-group-and-to-delete-the-details-group"></a>So fügen Sie eine neue Zeilengruppe hinzu und löschen die Detailgruppe  
  
1.  Klicken Sie im Bereich „Zeilengruppen“ mit der rechten Maustaste auf die Gruppe „Details“, zeigen Sie auf **Gruppe hinzufügen**, und klicken Sie anschließend auf **Übergeordnete Gruppe**.  
  
     ![Übergeordnete Gruppe Befehl](../../2014/tutorials/media/tutorial-parentgroupcommand.png "Parent Group-Befehl")  
  
2.  Wählen Sie in der Dropdown-Liste `[Territory].`  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Eine neue Spalte wird der Liste hinzugefügt. Die Spalte enthält die Zelle `[Territory].`  
  
4.  Klicken Sie mit der rechten Maustaste in der Liste auf die Spalte „Territory“, und klicken Sie anschließend auf **Spalten löschen**.  
  
     ![Löschen von Spalten](../../2014/tutorials/media/tutorial-deletecolumnscommand.png "Spalten löschen")  
  
5.  Klicken Sie auf **Nur Spalten löschen**.  
  
     ![Löschen Sie im Dialogfeld Spalten](../../2014/tutorials/media/tutorial-deletecolumnsdialog.png "löschen (Dialogfeld)")  
  
6.  Klicken Sie im Bereich "Zeilengruppen" mit der rechten Maustaste auf die Gruppe **Details** , und klicken Sie dann auf **Gruppe löschen**.  
  
     ![Löschen der Detailgruppe](../../2014/tutorials/media/tutorial-deletedetailsgroup.png "Löschen der Gruppe \"Details\"")  
  
7.  Klicken Sie auf **Nur Gruppe löschen**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Graphics"></a> 3. Hinzufügen von Grafiken  
 Einer der Vorteile der Verwendung eines Listendatenbereichs besteht darin, dass Berichtselemente wie z. B. Rechtecke und Textfelder überall hingefügt werden können und keine Beschränkung auf ein tabellarisches Layout besteht. Sie verbessern die Darstellung des Berichts durch Hinzufügen einer Grafik (ein mit einer Farbe ausgefülltes Rechteck).  
  
#### <a name="to-add-graphic-elements-to-the-report"></a>So fügen Sie dem Bericht grafische Elemente hinzu  
  
1.  Auf der **einfügen** Registerkarte des Menübands, klicken Sie auf **Rechteck**, und ziehen Sie dann ein Rechteck in der oberen linken Ecke der Liste. Legen Sie für das Rechteck eine Höhe von 17,8 cm und eine Breite von 2,5 cm fest.  
  
2.  Klicken Sie mit der rechten Maustaste auf das Rechteck, und klicken Sie anschließend auf **Rechteckeigenschaften**.  
  
3.  Klicken Sie auf die Registerkarte **Ausfüllen** .  
  
4.  Klicken Sie in der Dropdownliste **Füllfarbe** auf **Weitere Farben**, und wählen Sie dann die Farbe **Dunkelgrau** aus.  
  
     ![Wählen Sie Füllfarbe](../../2014/tutorials/media/tutorial-selectfillcolorwithnumbers.png "wählen Füllfarbe")  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Die linke Seite des Berichts enthält nun eine vertikale Grafik, die aus einem dunkelgrauen Rechteck besteht.  
  
##  <a name="Text"></a> 4. Hinzufügen von Freitext  
 Ein Textfeld enthält statischen Text, der auf jeder Berichtsseite sowie in allen Datenfeldern wiederholt wird.  
  
#### <a name="to-add-text-to-the-report"></a>So fügen Sie dem Bericht Text hinzu  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
2.  Klicken Sie auf der Registerkarte **Einfügen** des Menübands auf **Textfeld**, und ziehen Sie dann ein Textfeld in die linke obere Ecke der Liste, jedoch innerhalb des zuvor hinzugefügten Rechtecks. Legen Sie für das Textfeld eine Höhe von ca. 7,5 cm und eine Breite von ca. 12,7 cm fest.  
  
3.  Platzieren Sie den Cursor in den oberen Bereich des Textfelds, und geben Sie dann: **Newsletter für** .  
  
     ![Hinzufügen von Text für Newsletterüberschriften](../../2014/tutorials/media/tutorial-newsletterfor.png "Add newsletter heading text")  
  
    > [!NOTE]  
    >  Fügen Sie nach dem Begriff "für" zusätzliche Leerzeichen ein. Durch die Leerzeichen werden der Text und das Feld getrennt, die im nächsten Schritt hinzugefügt werden.  
  
4.  Ziehen Sie das Feld "Territory" in das Textfeld, und platzieren Sie es nach dem Text, den Sie in Schritt 3 eingegeben haben.  
  
     ![Hinzufügen von gebietsfelds](../../2014/tutorials/media/tutorial-addterritorialfield.png "hinzufügen gebietsfelds")  
  
5.  Markieren Sie den gesamten Text, klicken Sie mit der rechten Maustaste, und klicken Sie anschließend auf **Texteigenschaften**.  
  
6.  Klicken Sie auf die Registerkarte **Schriftart** .  
  
7.  Wählen Sie in der Liste **Schriftart** die Schriftart **Times New Roman**, in **Größe** den Wert **20 pt**und in **Farbe** die Option **Rot**aus.  
  
     ![Texteigenschaften](../../2014/tutorials/media/tutorial-textpropertieswithnumbers.png "Texteigenschaften")  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Platzieren Sie den Cursor unterhalb des Texts, den Sie in Schritt 3 und Datentyp eingegeben: **Hello** .  
  
    > [!NOTE]  
    >  Fügen Sie nach dem Begriff "Hello" zusätzliche Leerzeichen ein. Durch die Leerzeichen werden der Text und das Feld getrennt, die im nächsten Schritt hinzugefügt werden.  
  
10. Ziehen Sie das Feld "FullName" in das Textfeld, ordnen Sie es hinter dem Text an, den Sie in Schritt 9 eingegeben haben, und geben Sie dann ein Komma (,) ein.  
  
     ![Vollständiger Name-Feld hinzufügen](../../2014/tutorials/media/tutorial-addfullnamefield.png "Feld hinzufügen vollständiger Name")  
  
11. Wählen Sie den Text aus, den Sie in Schritt 9 und 10 hinzugefügt haben, klicken Sie mit der rechten Maustaste, und klicken Sie dann auf **Texteigenschaften**.  
  
12. Klicken Sie auf die Registerkarte **Schriftart** .  
  
13. Wählen Sie in der Liste **Schriftart** die Schriftart **Times New Roman**, in **Größe** den Wert **16 pt**und in **Farbe** die Option **Schwarz** aus.  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
15. Setzen Sie den Cursor unter den Text, den Sie in den Schritten 9 bis 13 hinzugefügt haben, und kopieren Sie anschließend den folgenden "griechischen" Text, und fügen Sie ihn ein:  
  
    ```  
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin sed dolor in ipsum pulvinar egestas. Sed sed lacus at leo ornare ultricies. Vivamus velit risus, euismod nec sodales gravida, gravida in dui. Etiam ullamcorper elit vitae justo fermentum ut ullamcorper augue sodales. Ut placerat, nisl quis feugiat adipiscing, nibh est aliquet est, mollis faucibus mauris lectus quis arcu. In mollis tincidunt lacinia. In vitae erat ut lorem tincidunt luctus. Curabitur et magna nunc, sit amet adipiscing nisi. Nulla rhoncus elementum orci nec tincidunt. Aliquam imperdiet cursus erat vel tincidunt. Donec et neque ac urna rutrum sodales. In id purus et nisl dignissim dapibus. Sed rhoncus metus at felis feugiat eu tempor dolor vehicula. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam faucibus consectetur diam eu pellentesque.   
    Nulla facilisi. Proin ligula enim, porta ut tincidunt id, adipiscing sit amet eros. Ut purus sem, bibendum et vulputate sit amet, facilisis eget magna. Sed aliquam erat non erat eleifend hendrerit. Ut a ligula est, sit amet eleifend enim. Ut et nisl enim, sit amet adipiscing augue. Vivamus eu arcu ac libero posuere elementum. Integer condimentum bibendum venenatis. Integer odio tellus, feugiat in pellentesque semper, interdum nec sem. Sed cursus euismod sem, ut elementum sapien placerat vel.   
    ```  
  
16. Markieren Sie den Text, den Sie in Schritt 15 hinzugefügt haben, klicken Sie mit der rechten Maustaste, und klicken Sie dann auf **Texteigenschaften**.  
  
17. Klicken Sie auf die Registerkarte **Schriftart** .  
  
18. Wählen Sie in der Liste **Schriftart** die Schriftart **Arial**in **Größe** den Wert **10 pt**und in **Farbe** die Option **Schwarz**.  
  
19. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     ![Hinzufügen von newslettertext](../../2014/tutorials/media/tutorial-newslettertext.png "Hinzufügen von newslettertext")  
  
20. Platzieren Sie den Cursor unterhalb des Texts, die Sie in Schritt 15 eingefügt haben, und geben Sie dann: **Herzlichen Glückwunsch zum Gesamtumsatz von** .  
  
    > [!NOTE]  
    >  Fügen Sie nach dem Begriff "von" zusätzliche Leerzeichen ein. Durch die Leerzeichen werden der Text und das Feld getrennt, die im nächsten Schritt hinzugefügt werden.  
  
21. Ziehen Sie das Feld "Sales" in das Textfeld, platzieren Sie es hinter dem in Schritt 20 eingegebenen Text, und geben Sie dann ein Ausrufezeichen (!) ein.  
  
22. Markieren Sie das Feld "Sales", mit der rechten Maustaste in des Felds, und klicken Sie dann auf **Ausdruck**.  
  
23. Ändern Sie im Ausdrucksfeld den Ausdruck folgendermaßen so, dass er die Sum-Funktion einschließt:  
  
    ```  
    =Sum(Fields!Sales.value)  
    ```  
  
24. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     ![Hinzufügen eines Ausdrucks zum sales-Feld](../../2014/tutorials/media/tutorial-addexpressiontosalesfield.png "Hinzufügen eines Ausdrucks zum sales-Feld")  
  
25. Wählen Sie den Text aus, den Sie in den Schritten 20 bis 23 hinzugefügt haben, klicken Sie mit der rechten Maustaste, und klicken Sie dann auf **Texteigenschaften**.  
  
26. Klicken Sie auf die Registerkarte **Schriftart** .  
  
27. Wählen Sie in der Liste **Schriftart** die Schriftart **Times New Roman**, in **Größe** den Wert **16 pt**und in **Farbe** die Option **Rot**aus.  
  
28. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
29. Wählen Sie `[Sum(Sales)]` aus. Klicken Sie anschließend auf der Registerkarte **Home** in der Gruppe **Zahl** auf die Schaltfläche **Währung** .  
  
     ![Hinzufügen von Währungssymbol](../../2014/tutorials/media/tutorial-addcurrencysymbol.png "Währungssymbol hinzufügen")  
  
30. Klicken Sie mit der rechten Maustaste auf das Textfeld mit dem Text „Zum Hinzufügen eines Titels klicken“, und klicken Sie anschließend auf **Löschen**.  
  
31. Markieren Sie das Listenfeld, und verschieben Sie es mithilfe der Pfeiltasten an den Seitenanfang.  
  
32. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Im Bericht wird statischer Text angezeigt, und jede Berichtsseite enthält Daten, die sich auf ein Gebiet beziehen. Umsatz wird als Währung formatiert.  
  
 ![Vorschau für Newsletter](../../2014/tutorials/media/tutorial-newsletters.png "Vorschau für Newsletter")  
  
##  <a name="Table"></a> 5. Hinzufügen einer Tabelle, die Umsatzdetails anzeigt  
 Fügen Sie dem formfreien Bericht mithilfe des Assistenten für neue Tabellen und Matrizen eine Tabelle hinzu. Nach Fertigstellung des Assistenten wird manuell eine Zeile für Summen hinzugefügt.  
  
#### <a name="to-add-a-table"></a>So fügen Sie eine Tabelle hinzu  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** des Menübands im Bereich **Datenbereiche** auf **Tabelle**und anschließend auf **Tabellen-Assistent**.  
  
2.  Klicken Sie auf der Seite "Dataset auswählen" auf **ListDataset**.  
  
3.  Klicken Sie auf **Weiter**.  
  
4.  Ziehen Sie auf der Seite **Felder anordnen** das Feld „Product“ von **Verfügbare Felder** zu **Werte**.  
  
5.  Wiederholen Sie Schritt 4 für "SalesDate", "Quantity und "Sales". Orden Sie "SalesDate" unter Produkt, "Quantity" unter "SalesDate" und "Sales" unter "SalesDate" an.  
  
6.  Klicken Sie auf **Weiter**.  
  
7.  Zeigen Sie auf der Seite **Layout auswählen** das Layout der Tabelle an.  
  
     Die Tabelle ist sehr einfach. Sie besteht aus fünf Spalten und enthält keine Zeilen- oder Spaltengruppen. Da die Tabelle keine Gruppen enthält, sind die gruppenbezogenen Layoutoptionen nicht verfügbar. Im späteren Verlauf des Lernprogramms wird Tabelle manuell aktualisiert, damit sie eine Summe enthält.  
  
8.  Klicken Sie auf **Weiter**.  
  
9. Wählen Sie auf der Seite **Format auswählen** im Bereich **Formate** die Option **Schiefer**aus.  
  
10. Klicken Sie auf **Fertig stellen**.  
  
11. Ziehen Sie die Tabelle unter das Textfeld, das Sie in Lektion 4 hinzugefügt haben.  
  
    > [!NOTE]  
    >  Stellen Sie sicher, dass sich die Tabelle in der Liste befindet.  
  
12. Nachdem Sie bestätigt haben, dass die Tabelle ausgewählt wurde, klicken Sie im Zeilengruppenbereich mit der rechten Maustaste auf „Details“, zeigen Sie auf **Gesamtergebnis hinzufügen**, und klicken Sie dann auf **Nach**.  
  
     ![Fügen Sie die Summe des Berichts](../../2014/tutorials/media/tutorial-addtotal.png "Summe des Berichts hinzufügen")  
  
13. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Im Bericht wird eine Tabelle mit Umsatzdetails und Gesamtbeträgen angezeigt.  
  
 ![Gesamtumsatz im Bericht](../../2014/tutorials/media/tutorial-reportsalestotals.png "Gesamtumsätze im Bericht")  
  
##  <a name="Format"></a> 6. Formatieren von Daten  
 Formatieren Sie numerische Daten nur als Währung und Datumsangaben nur als Tag- und Uhrzeitangaben.  
  
#### <a name="to-format-fields-table"></a>So formatieren Sie die Feldtabelle  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zu wechseln.  
  
2.  Klicken Sie auf die Tabellenzellen, die `[Sum(SalesSales)]` enthalten, und klicken Sie auf der Registerkarte **Home** in der Gruppe **Zahl** auf die Schaltfläche **Währung** .  
  
     ![Hinzufügen des Währungssymbols zur Verkaufssumme](../../2014/tutorials/media/tutorial-sumsales-currencysymbol.png "hinzufügen Währungssymbols zur Verkaufssumme")  
  
3.  Klicken Sie auf die Zelle, die `[SalesDate]` enthält, und wählen Sie in der Gruppe **Zahl** aus der Dropdownliste **Datum**aus.  
  
4.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Im Bericht werden nun formatierte Daten angezeigt, und die Lesbarkeit wurde verbessert.  
  
 ![Formatieren von Gesamtumsätzen im Bericht](../../2014/tutorials/media/tutorial-reportsalestotals-formatted.png "Formatieren von Gesamtumsätzen im Bericht")  
  
##  <a name="Save"></a> 7. Speichern des Berichts  
 Sie können Berichte auf einem Berichtsserver, in einer SharePoint-Bibliothek oder auf dem Computer speichern. Sie können den Bericht auch in eine Vielzahl von Formaten wie Word und PDF exportieren, indem Sie den Bericht ausführen und das Format aus dem Menü **Exportieren** auswählen.  
  
 Speichern Sie in diesem Lernprogramm den Bericht auf einem Berichtsserver. Wenn Sie keinen Zugriff auf einen Berichtsserver besitzen, speichern Sie den Bericht auf dem Computer.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>So speichern Sie den Bericht auf einem Berichtsserver  
  
1.  Klicken Sie auf die Schaltfläche **Berichts-Generator** und anschließend auf **Speichern unter**.  
  
2.  Klicken Sie auf **Letzte Sites und Server**.  
  
3.  Wählen Sie den Namen des Berichtsservers aus, auf dem Sie zum Speichern von Berichten berechtigt sind, oder geben Sie ihn ein.  
  
     Die Meldung "Verbindung mit Berichtsserver wird hergestellt" wird angezeigt. Nachdem die Verbindung hergestellt wurde, sehen Sie den Inhalt des Berichtsordners, den der Berichtsserveradministrator als Standardspeicherort für Berichte angegeben hat.  
  
4.  In `Name`, ersetzen Sie den Standardnamen durch **SalesInformationByTerritory**.  
  
5.  Klicken Sie auf **Speichern**.  
  
 Der Bericht wird auf dem Berichtsserver gespeichert. Der Name des Berichtsservers, mit dem Sie verbunden sind, wird in der Statusleiste unten im Fenster angezeigt.  
  
#### <a name="to-save-the-report-on-your-computer"></a>So speichern Sie den Bericht auf dem Computer  
  
1.  Klicken Sie auf die Schaltfläche **Berichts-Generator** und anschließend auf **Speichern unter**.  
  
2.  Klicken Sie auf **Desktop**, **Meine Dokumente**oder **Arbeitsplatz**, und navigieren Sie anschließend zu dem Ordner, in dem Sie den Bericht speichern möchten.  
  
3.  In `Name`, ersetzen Sie den Standardnamen durch **SalesInformationByTerritory**.  
  
4.  Klicken Sie auf **Speichern**.  
  
##  <a name="Line"></a> 8. Hinzufügen einer Zeile, um Bereiche des Berichts zu trennen (optional)  
 Fügen Sie eine Zeile hinzu, um den Leitartikel und die Details des Berichts zu trennen.  
  
#### <a name="to-add-a-line"></a>So fügen Sie eine Linie hinzu  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
2.  Klicken Sie auf der Registerkarte **Einfügen** des Menübands im Bereich **Berichtselemente** auf **Linie**.  
  
3.  Zeichnen Sie eine Linie unter dem Freitextfeld, das Sie in Lektion 4 hinzugefügt haben.  
  
4.  Klicken Sie auf die Zeile.  
  
5.  Klicken Sie auf die Registerkarte **Home** .  
  
6.  Wählen Sie im Bereich **Rahmen** für die Breite den Wert **4 1/2** pt aus, und wählen Sie für Farbe **Rot**aus.  
  
     ![Fügen Sie die Zeile zum Bericht](../../2014/tutorials/media/tutorial-reportwithline.png "Zeile zum Bericht hinzufügen")  
  
##  <a name="Visualization"></a> 9. (Optional) Hinzufügen von Zusammenfassungsdatenvisualisierung  
 Mit Rechtecken kann das Rendern des Berichts beeinflusst werden. Platzieren Sie in einem Rechteck ein Kreis- und ein Säulendiagramm, um sicherzustellen, dass der Bericht wunschgemäß gerendert wird.  
  
#### <a name="to-add-a-rectangle"></a>So fügen Sie ein Rechteck hinzu  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
2.  Klicken Sie auf der Registerkarte **Einfügen** des Menübands im Bereich **Berichtselemente** auf **Rechteck**, und ziehen Sie das Rechteck in die Liste rechts neben der Tabelle. Legen Sie für das Rechteck eine Breite von 5 cm und eine Höhe von 10 cm fest.  
  
3.  Richten Sie den oberen Bereich des Rechtecks und der Tabelle aus.  
  
#### <a name="to-add-a-pie-chart"></a>So fügen Sie ein Kreisdiagramm hinzu  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** des Menübands im Bereich **Datenvisualisierungen** auf **Diagramm** und anschließend auf **Diagramm-Assistent**.  
  
2.  Klicken Sie auf der Seite Dataset auswählen auf **ListDataset**und anschließend auf **Weiter**.  
  
3.  Klicken Sie auf **Kreis**, und klicken Sie dann auf **Weiter**.  
  
4.  Ziehen Sie auf der Seite „Diagrammfelder anordnen“ das Feld „Product“ in **Kategorien**.  
  
5.  Ziehen Sie Quantity in **Werte**, und klicken Sie dann auf **Weiter**.  
  
6.  Wählen Sie auf der Seite **Format auswählen** im Bereich **Formate** die Option **Schiefer**aus.  
  
7.  Klicken Sie auf **Fertig stellen**.  
  
8.  Ändern Sie die Größe des Diagramms, das oben links im Bericht angezeigt wird, auf eine Höhe von 4 cm und eine Breite von 5 cm.  
  
9. Ziehen Sie das Diagramm in das Rechteck.  
  
     ![Hinzufügen von Kreisdiagramm](../../2014/tutorials/media/tutorial-addpiechart.png "Kreisdiagramm hinzufügen")  
  
10. Klicken Sie mit der rechten Maustaste auf den Diagrammtitel, und klicken Sie dann auf **Titeleigenschaften**.  
  
11. In der **Diagrammtiteleigenschaften** im Dialogfeld im Titeltext Folgendes ein: **Verkaufte Produktmengen**.  
  
12. Klicken Sie auf die Registerkarte **Schriftart** , und klicken Sie in der Liste **Größe** auf **10 pt**.  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-add-a-column-chart"></a>So fügen Sie einem Bericht ein Säulendiagramm hinzu  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** des Menübands im Bereich **Datenvisualisierungen** auf **Diagramm** und anschließend auf **Diagramm-Assistent**.  
  
2.  Klicken Sie auf der Seite **Dataset auswählen** auf **ListDataset**, und anschließend auf **Weiter**.  
  
3.  Klicken Sie auf **Spalte**und anschließend auf **Weiter**.  
  
4.  Auf der Seite Diagrammfelder anordnen, ziehen Sie das Feld "Product" zu **Kategorien**.  
  
5.  Ziehen Sie „Sales“ in das Feld **Werte** , und klicken Sie anschließend auf **Weiter**.  
  
     Werte werden auf der vertikalen Achse angezeigt.  
  
6.  Wählen Sie auf der Seite **Format auswählen** im Bereich **Formate** die Option **Schiefer**aus.  
  
7.  Klicken Sie auf **Fertig stellen**.  
  
     Ein Säulendiagramm wird oben links im Bericht hinzugefügt.  
  
8.  Legen Sie die für das Diagramm eine Breite von 5 cm und eine Höhe von 5 cm fest.  
  
9. Ziehen Sie das Diagramm in das Rechteck unter dem Kreisdiagramm.  
  
     ![Diagramm der hinzufügen-Spalte](../../2014/tutorials/media/tutorial-addcolumnchart.png "Säulendiagramm hinzufügen")  
  
10. Klicken Sie mit der rechten Maustaste auf den Diagrammtitel, und klicken Sie dann auf **Titeleigenschaften**.  
  
11. In der **Diagrammtiteleigenschaften** im Dialogfeld im Titeltext Folgendes ein: **Produktverkaufszahlen**.  
  
12. Klicken Sie auf die Registerkarte **Schriftart** , und klicken Sie in der Liste **Größe** auf **10 pt**, und klicken Sie dann auf **OK**.  
  
13. Klicken Sie im Säulendiagramm mit der rechten Maustaste auf den Titel der vertikalen Achse, und deaktivieren Sie anschließend das Kontrollkästchen **Achsentitel anzeigen**.  
  
14. Wiederholen Sie Schritt 13 für den Titel der horizontalen Achse.  
  
15. Klicken Sie mit der rechten Maustaste auf die Legende, und klicken Sie dann auf **Legende löschen**.  
  
    > [!NOTE]  
    >  Durch Entfernen der Achsentitel und der Legende wird die Lesbarkeit des Diagramms bei geringer Größe verbessert.  
  
 ![Ändern von Diagrammtiteln und Entfernen des Achsentitels](../../2014/tutorials/media/tutorial-columnchart-newtitle-noaxistitle.png "Ändern von Diagrammtiteln und Entfernen des Achsentitels")  
  
#### <a name="to-verify-the-charts-are-inside-the-rectangle"></a>So überprüfen Sie, ob die Diagramme im Rechteck enthalten sind  
  
1.  Klicken Sie auf das Rechteck, das Sie zuvor in dieser Lektion hinzugefügt haben.  
  
     Im Eigenschaftenbereich zeigt die `Name`-Eigenschaft den Namen des Rechtecks an.  
  
     ![Name des Rechtecks](../../2014/tutorials/media/tutorial-rectanglename.png "Namen des Rechtecks")  
  
2.  Klicken Sie auf das Kreisdiagramm.  
  
3.  In der **Eigenschaften** Bereich, überprüfen Sie, ob die `Parent` Eigenschaft enthält den Namen des Rechtecks.  
  
     ![Parent-Eigenschaft für Kreisdiagramm](../../2014/tutorials/media/tutorial-piechart-parentproperty.png "Parent-Eigenschaft für Kreisdiagramm")  
  
4.  Klicken Sie auf das Säulendiagramm, und wiederholen Sie die Schritte 2 und 3.  
  
    > [!NOTE]  
    >  Wenn die Diagramme nicht im Rechteck enthalten sind, werden die Diagramme im gerenderten Bericht nicht zusammen angezeigt.  
  
#### <a name="to-make-the-charts-the-same-size"></a>So legen Sie für die Diagramme die gleiche Größe fest  
  
1.  Klicken Sie auf das Kreisdiagramm, drücken Sie die STRG-TASTE, und klicken Sie anschließend auf das Säulendiagramm.  
  
2.  Wenn beide Diagramme markiert sind, klicken Sie mit der rechten Maustaste darauf, zeigen Sie auf **Layout**, und klicken Sie anschließend auf **Breite angleichen**.  
  
     ![Diagrammbreiten gleich](../../2014/tutorials/media/tutorial-makechartssamewidth.png "Diagrammbreiten identisch")  
  
    > [!NOTE]  
    >  Das Element, auf das Sie zuerst klicken, bestimmt die Breite aller ausgewählten Elemente.  
  
3.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Im Bericht werden nun Zusammenfassungsumsatzdaten in Kreis- und Säulendiagrammen angezeigt.  
  
 ![SSRS-Lernprogramm, formfreien Bericht](../../2014/tutorials/media/tutorial-reportfinal.png "SSRS-Lernprogramm, formfreien Bericht")  
  
## <a name="more-information"></a>Weitere Informationen  
 Weitere Informationen zu Listen finden Sie unter [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](report-design/tables-matrices-and-lists-report-builder-and-ssrs.md), [listet &#40;Berichts-Generator und SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), [Tablix-Daten Region Bereiche &#40;Berichts-Generator und SSRS&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md), und [Tablix-Zellen, Zeilen und Spalten &#40;Berichts-Generator&#41; und SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).  
  
 Weitere Informationen zu Abfrage-Designern finden Sie unter [Abfrage-Designer (Berichts-Generator)](../../2014/reporting-services/query-designers-report-builder.md) und [Benutzeroberfläche des textbasierten Abfrage-Designers (Berichts-Generator)](report-data/text-based-query-designer-user-interface-report-builder.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Lernprogramme &#40;Berichts-Generator&#41;](report-builder-tutorials.md)   
 [Berichts-Generator in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
