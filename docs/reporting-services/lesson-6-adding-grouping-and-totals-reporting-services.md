---
title: 'Lektion 6: Hinzufügen von Gruppierungen und Gesamtergebnissen (Reporting Services) | Microsoft-Dokumentation'
ms.date: 04/18/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: e3d61228-2aa4-42cc-955e-602dbf3406a7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b5b9846a20615cf613dd50752ac63f2669b1e399
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65089664"
---
# <a name="lesson-6-adding-grouping-and-totals-reporting-services"></a>Lesson 6: Adding Grouping and Totals (Reporting Services)

In dieser letzten Lektion des Tutorials werden Sie Ihrem [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Bericht Gruppierungen und Gesamtergebnisse hinzufügen, um Ihre Daten zu organisieren und zusammenzufassen.  

## <a name="to-group-data-in-a-report"></a>So gruppieren Sie Daten in einem Bericht

1. Klicken Sie auf die Registerkarte **Entwurf**.
2. Wenn Sie den Bereich **Zeilengruppen** nicht sehen, klicken Sie mit der rechten Maustaste auf die Entwurfsoberfläche. Klicken Sie auf **Ansicht** >**Gruppierung**.
3. Ziehen Sie im **Berichtsdatenbereich** das Feld `[Date]` in den Bereich **Zeilengruppen**. Platzieren Sie es oberhalb der Zeile, die als **= (Details)** angezeigt wird.

    > [!NOTE]
    > Beachten Sie, dass das Zeilenhandle nun Klammern zur Angabe einer Gruppe aufweist. Außerdem verfügt die Tabelle nun auf jeder Seite der vertikalen gepunkteten Linie über eine Spalte für den Ausdruck `[Date]`.
    >
    >![Datumsgruppe hinzugefügt](media/rs-basictablegroups1design.png "date group added")
4. Ziehen Sie im **Berichtsdatenbereich** das Feld `[Order]` in den Bereich **Zeilengruppen**. Platzieren das Feld unter **Date** und über **= (Details)** .

    ![ssrs_ssdt_Feld_Order_hinzufügen](media/ssrs-ssdt-addorderfield.png)

    > [!NOTE]
    > Beachten Sie, dass das Zeilenhandle nun zwei Klammern (![ssrs_ssdt_rowgroupdoublehandles](media/ssrs-ssdt-rowgroupdoublehandles.png)) zur Angabe von zwei Gruppen enthält. Zudem verfügt die Tabelle jetzt über zwei Spalten für den Ausdruck `[Order]`.

5. Löschen Sie die ursprünglichen Spalten für die Ausdrücke `[Date]` und `[Order]` rechts neben der doppelten Linie. Wählen Sie die Spaltenhandles für die beiden Spalten aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Spalten löschen** aus. Der Berichts-Designer entfernt die einzelnen Zeilenausdrücke, sodass nur die Gruppenausdrücke angezeigt werden.

    ![Zu löschende Spalten auswählen](media/rs-basictablegroupsdeletecols.gif "Select columns to delete")

6. Zum Formatieren der neuen Spalte `[Date]` klicken Sie mit der rechten Maustaste auf die Datenbereichszelle, die den Ausdruck `[Date]` enthält, und wählen Sie **Textfeldeigenschaften**.
7. Klicken Sie im Spaltenlistenfeld ganz links auf **Zahl** und im Listenfeld **Kategorie** auf **Datum**.
8. Wählen Sie im Listenfeld **Typ** die Option **31. Januar 2000** aus.
9. Klicken Sie auf **OK**, um das Format zu übernehmen.
10. Zeigen Sie erneut eine Vorschau des Berichts an. Sie sollte wie folgt aussehen:

    ![rs_Basistabelle_Gruppen_Vorschau](media/rs-basictablegroupspreview.png)

## <a name="adding-totals-to-a-report"></a>Hinzufügen von Gesamtwerten zu einem Bericht

1. Wechseln Sie in die **Designansicht**.
2. Klicken Sie mit der rechten Maustaste auf die Datenbereichszelle mit dem Ausdruck `[LineTotal]`, und wählen Sie anschließend **Gesamtergebnis hinzufügen** aus. Der Berichts-Designer fügt eine Zeile mit dem Gesamtwert für die einzelnen Bestellungen in Dollar hinzu.
3. Klicken Sie mit der rechten Maustaste auf die Zelle mit dem Feld `[Qty]`und anschließend auf **Gesamtergebnis hinzufügen**. Der Berichts-Designer fügt der Ergebniszeile eine Gesamtmenge für die einzelnen Bestellungen hinzu.
4. Geben Sie in die leere Zelle links von `Sum[Qty]` die Zeichenfolge „Order Total“ ein.
5. Sie können der Ergebniszeile eine Hintergrundfarbe hinzufügen. Wählen Sie die beiden Gesamtergebniszellen und die Bezeichnungszelle aus.  
6. Wählen Sie im Menü **Format** die Option **Hintergrundfarbe** > **Hellgrau** aus.
7. Klicken Sie auf **OK**, um das Format zu übernehmen.

   ![Entwurfsansicht: einfache Tabelle mit Gesamtergebnis der Bestellungen](media/rs-basictablesumlinetotaldesign.gif "Design view: Basic table with order total")

## <a name="add-the-daily-total-to-the-report"></a>Hinzufügen des Tagesgesamtwerts zum Bericht

1. Klicken Sie mit der rechten Maustaste auf die Ausdruckszelle `[Order]`, und wählen Sie **Gesamtergebnis hinzufügen** > **Nach** aus. Der Berichts-Designer fügt eine neue Zeile mit den Summen der Werte `[Qty]` und `[Linetotal]` für jeden Tag und die Zeichenfolge „Total“ am Ende der Spalte mit dem Ausdruck `[Order]` hinzu.
2. Geben Sie in der gleichen Zelle zuerst das Wort „Daily“ und anschließend das Wort „Total“ ein, um „Daily Total“zu erhalten.
3. Wählen Sie diese Zelle und die beiden benachbarten Zellen mit den Gesamtwerten rechts sowie die leere Zelle dazwischen aus.
4. Wählen Sie im Menü **Format** die Option **Hintergrundfarbe** > **Orange** aus.
5. Klicken Sie auf **OK**, um das Format zu übernehmen.

   ![Set background color to Orange (Festlegen der Hintergrundfarbe auf Orange)](media/rs-basictablesumdaytotaldesign.gif "rs_BasicTableSumDayTotalDesign")

## <a name="add-the-grand-total-to-the-report"></a>Hinzufügen des Gesamtergebnisses zum Bericht

1. Klicken Sie mit der rechten Maustaste auf die Ausdruckszelle `[Date]`, und wählen Sie **Gesamtergebnis hinzufügen** > **Nach** aus. Der Berichts-Designer fügt eine neue Zeile mit den Summen der Werte `[Qty]` und `[LineTotal]` für den gesamten Bericht und die Zeichenfolge „Total“ am Ende der Spalte mit dem Ausdruck `[Date]` hinzu.
2. Geben Sie in der gleichen Zelle zuerst die Zeichenfolge „Grand“ und anschließend das Wort „Total“ ein, um „Grand Total“ zu erhalten.
3. Wählen Sie die Zelle „Grand Total“ aus, und markieren Sie die beiden Ausdruckszellen `Sum()` sowie die leeren Zellen dazwischen.
4. Wählen Sie im Menü **Format** die Option **Hintergrundfarbe** > **Hellblau** aus.
5. Klicken Sie auf **OK**, um das Format zu übernehmen.

    ![Entwurfsansicht: Gesamtergebnis in einfacher Tabelle](media/rs-basictablesumgrandtotaldesign.gif "Design view: Grand total in basic table")

## <a name="preview-the-report"></a>Anzeigen des Berichts in der Vorschau

Zur Anzeige der geänderten Formatierung wählen Sie die Registerkarte **Vorschau** aus. Wählen Sie in der Symbolleiste **Vorschau** die Schaltfläche **Letzte Seite**, die wie ![ssrs_ssdt_viewertoolbar_lastpage](media/ssrs-ssdt-viewertoolbar-lastpage.png) aussieht. Die Vorschau sollte folgendermaßen aussehen:

   ![Vorschau: Einfache Tabelle mit Gesamtergebnis](media/rs-basictablesumgrandtotalpreview.gif "Preview: Basic table with grand total")

## <a name="publishing-the-report-to-the-report-server-optional"></a>Veröffentlichen des Berichts auf dem *Berichtsserver* (Optional)

Ein optionaler Schritt besteht darin, den vervollständigten Bericht auf dem Berichtsserver zu veröffentlichen, damit Sie den Bericht im Webportal anzeigen können.

1. Wählen Sie das Menü **Projekt** > **Tutorial Properties...** (Tutorialeigenschaften...) aus.
2. Geben Sie in **TargetServerURL** den Namen Ihres Berichtsservers ein, z. B.:
    - `http:/<servername>/reportserver` oder
    - `https://localhost/reportserver` funktioniert, wenn Sie den Bericht auf dem Berichtsserver erstellen.

3. Für **TargetReportFolder** wurde „Tutorial“ angegeben – der Name des Projekts. Der Bericht wird vom Berichts-Designer in diesem Ordner bereitgestellt.
4. Wählen Sie **OK**.
5. Wählen Sie im Menü **Erstellen** > **Deploy Tutorial** (Tutorial bereitstellen).

    Wenn Sie im **Ausgabefenster** eine Meldung wie die Folgende sehen, war die Bereitstellung erfolgreich:

    > ------ Build started: Project: tutorial, Configuration: Debug ------  
    > Skipping 'Sales Orders.rdl'. Item is up to date.  
    > Erstellung abgeschlossen -- 0 Fehler, 0 Warnungen  
    > ------ Deploy started: Project: tutorial, Configuration: Debug ------  
    > Bereitstellen für `https://[server name]/reportserver`  
    > Deploying report '/tutorial/Sales Orders'.  
    > Deploy complete -- 0 errors, 0 warnings  
    > ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    > ========== Deploy: 1 succeeded, 0 failed, 0 skipped ==========  

    Wenn Sie eine Fehlermeldung wie die Folgende sehen, überprüfen Sie, ob Sie über die entsprechenden Berechtigungen für den Berichtsserver verfügen und ob Sie [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] mit Administratorrechten gestartet haben.
    >
    > „Die dem Benutzer 'XXXXXXXX\\[Ihr Benutzername]' erteilten Berechtigungen reichen zum Ausführen des Vorgangs nicht aus.“

6. Öffnen Sie einen Browser mit Administratorrechten. Klicken Sie zum Beispiel mit der rechten Maustaste auf das Symbol für den Internet Explorer, und wählen Sie **Als Administrator ausführen** aus.
7. Navigieren Sie zur Webportal-URL.
   - `https://<server name>/reports`.
   - `https://localhost/reports` funktioniert, wenn Sie den Bericht auf dem Berichtsserver erstellen.

8. Wählen Sie den Ordner „Tutorial“ aus, und wählen Sie dann den Bericht „Sales Orders“ aus, um den Bericht anzuzeigen.

    ![ssrs_Tutorial_Tutorial_Ordner](media/ssrs-tutorial-tutorialfolder.png)  

Sie haben das Tutorial zum **Erstellen eines einfachen Tabellenberichts** erfolgreich abgeschlossen.

## <a name="see-also"></a>Siehe auch

[Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)
