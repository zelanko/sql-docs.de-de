---
title: 'Lektion 6: Hinzufügen von Gruppierungen und Gesamtergebnissen (Reporting Services) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e3d61228-2aa4-42cc-955e-602dbf3406a7
caps.latest.revision: 50
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: c71c785f6d5cd5130223335830f53cc0fa8bf6f2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047538"
---
# <a name="lesson-6-adding-grouping-and-totals-reporting-services"></a>Lesson 6: Adding Grouping and Totals (Reporting Services)
  Fügen Sie dem Bericht Gruppierungen und Gesamtwerte hinzu, um Daten zu gruppieren und zusammenzufassen.  
  
 Informationen zum Hinzufügen laufender Gesamtwerte zu Berichten finden Sie in der Kuratierung auf curah.microsoft.com: [Hinzufügen von Gesamtwerten zu Reporting-Services-Berichten (SSRS)](http://go.microsoft.com/fwlink/p/?LinkId=403698).  
  
 **In diesem Thema:**  
  
-   [Zum Gruppieren von Daten in einem Bericht](#bkmk_groupdata)  
  
-   [So fügen Sie Summen zu einem Bericht hinzu](#bkmk_addtotals)  
  
-   [Ein Bericht einen tagesgesamtwert hinzu](#bkmk_adddailytotal)  
  
-   [Einen Bericht ein Gesamtergebnis hinzu](#bkmk_addgrandtotal)  
  
-   [So veröffentlichen Sie den Bericht auf dem Berichtsserver (Optional)](#bkmk_publishreport)  
  
##  <a name="bkmk_groupdata"></a> Zum Gruppieren von Daten in einem Bericht  
  
1.  Klicken Sie auf die Registerkarte **Entwurf** .  
  
2.  Wenn Sie den Bereich **Zeilengruppen** nicht sehen, klicken Sie mit der rechten Maustaste auf die Entwurfsoberfläche. Klicken Sie auf **Sicht** und dann auf **Gruppierung**.  
  
3.  Aus der **Berichtsdaten** ziehen Sie die `Date` -Feld der **Zeilengruppen** Bereich. Platzieren Sie das Feld über der Zeile **(Details)**.  
  
     Beachten Sie, dass das Zeilenhandle nun Klammern zum Anzeigen einer Gruppe aufweist. Außerdem verfügt die Tabelle nun auf jeder Seite der vertikalen gepunkteten Linie einmal über die Spalte Date.  
  
     ![](../../2014/tutorials/media/rs-basictablegroups1design.gif "rs_BasicTableGroups1Design")  
  
4.  Aus der **Berichtsdaten** ziehen Sie die `Order` -Feld der **Zeilengruppen** Bereich. Platzieren das Feld unter Date und über **Details**.  
  
     Beachten Sie, dass das Zeilenhandle nun zweimal Klammern zum Anzeigen von zwei Gruppen aufweist. Die Tabelle verfügt jetzt über zwei `Order` Spalten zu.  
  
5.  Löschen Sie die ursprünglichen Datum und die Reihenfolge der Spalten, die **rechten** der doppelten Linie. Dadurch werden die einzelnen Datensatzwerte entfernt, und nur der Gruppenwert wird angezeigt. Wählen Sie die Spaltenhandles für die beiden Spalten aus, klicken Sie mit der rechten Maustaste und wählen Sie **Spalten löschen**aus.  
  
     ![Zu löschende Spalten auswählen](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "Select columns to delete")  
  
     Die Spaltenkopfzeilen und der Datumswert können erneut formatiert werden.  
  
6.  Wechseln Sie zur Registerkarte **Vorschau** , um eine Vorschau des Berichts anzuzeigen. Die Vorschau sollte ähnlich der folgenden Abbildung aussehen:  
  
     ![Nach „Date“ (Datum) und dann nach „Order“ (Auftrag) gruppierte Tabelle](../../2014/tutorials/media/rs-basictablegroupspreview.gif "Table grouped by date and then order")  
  
##  <a name="bkmk_addtotals"></a> So fügen Sie Summen zu einem Bericht hinzu  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Datenbereichszelle mit dem Feld `[LineTotal]`und anschließend auf **Gesamtergebnis hinzufügen**.  
  
     Dadurch wird eine Zeile mit dem Gesamtwert für die einzelnen Bestellungen in Dollar hinzugefügt.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Zelle mit dem Feld `[Qty]`und anschließend auf **Gesamtergebnis hinzufügen**.  
  
     Dadurch wird der Ergebniszeile eine Gesamtmenge für die einzelnen Bestellungen hinzugefügt.  
  
4.  Geben Sie in die leere Zelle links von `Sum[Qty]`die Bezeichnung**Order Total**ein.  
  
5.  Sie können der Ergebniszeile eine Hintergrundfarbe hinzufügen. Wählen Sie die beiden Gesamtergebniszellen und die Bezeichnungszelle aus.  
  
6.  Klicken Sie im Menü **Format** auf **Hintergrundfarbe**, klicken Sie auf **Hellgrau**und dann auf **OK**.  
  
     ![Entwurfsansicht: einfache Tabelle mit Gesamtergebnis der Bestellungen](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "Design view: Basic table with order total")  
  
##  <a name="bkmk_adddailytotal"></a> Ein Bericht einen tagesgesamtwert hinzu  
  
1.  Mit der rechten Maustaste in der Zelle Order, zeigen Sie auf **Gesamtergebnis hinzufügen**, und klicken Sie auf **nach**.  
  
     Dadurch wird eine neue Zeile mit der Menge und dem Gesamtbetrag in Dollar für jeden Tag und die Bezeichnung "**insgesamt**" in der Spalte Order.  
  
2.  Geben Sie in der gleichen Zelle zuerst das Wort **Daily** und anschließend das Wort **Total** ein, um **Daily Total**zu erhalten.  
  
3.  Wählen Sie die Zelle **Daily Total** aus, und markieren Sie die beiden Zellen für **Sum** sowie die leere Zelle dazwischen.  
  
4.  Klicken Sie im Menü **Format** auf **Hintergrundfarbe**, klicken Sie auf **Orange**und dann auf **OK**.  
  
     ![](../../2014/tutorials/media/rs-basictablesumdaytotaldesign.gif "rs_BasicTableSumDayTotalDesign")  
  
##  <a name="bkmk_addgrandtotal"></a> Einen Bericht ein Gesamtergebnis hinzu  
  
1.  Klicken Sie mit der rechten Maustaste auf die Zelle Date, zeigen Sie auf **Gesamtergebnis hinzufügen**, und klicken Sie auf **Danach**.  
  
     Dadurch wird eine neue Zeile mit der Menge und dem Gesamtbetrag in Dollar für den gesamten Bericht hinzugefügt und die **insgesamt** -Bezeichnung in der `Date` Spalte.  
  
2.  Geben Sie in der gleichen Zelle zuerst das Wort **Grand** und anschließend das Wort **Total** ein, um **Grand Total**zu erhalten.  
  
3.  Wählen Sie die Zelle **Grand Total** aus, und markieren Sie die beiden Zellen für **Sum** sowie die leeren Zellen dazwischen.  
  
4.  Klicken Sie im Menü **Format** auf **Hintergrundfarbe**, klicken Sie auf **Hellblau**und dann auf **OK**.  
  
     ![Entwurfsansicht: Gesamtergebnis in einfacher Tabelle](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "Design view: Grand total in basic table")  
  
5.  Klicken Sie auf "Vorschau".  
  
     Die letzte Seite sollte etwa folgendermaßen aussehen:  
  
     ![Vorschau: Einfache Tabelle mit Gesamtergebnis](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "Preview: Basic table with grand total")  
  
##  <a name="bkmk_publishreport"></a> So veröffentlichen Sie den Bericht auf dem Berichtsserver (Optional)  
  
1.  Ein optionaler Schritt besteht darin, den vervollständigten Bericht auf dem Berichtsserver im einheitlichen Modus zu veröffentlichen, damit Sie den Bericht im Berichts-Manager anzeigen können.  
  
2.  Klicken Sie auf der Symbolleiste auf **Projekt** , und klicken Sie dann auf auf die Option für die **Eigenschaften des Lernprogramms**.  
  
3.  In der **TargetServerURL** Geben Sie den Namen des Namens des Berichtsservers, z. B. **http://\<Servername > / Reportserver**  
  
4.  Klicken Sie auf **OK**.  
  
5.  Klicken Sie auf der Symbolleiste auf **Erstellen** , und klicken Sie dann auf **Tutorial bereitstellen**.  
  
     Wenn Sie im Ausgabefenster eine Meldung wie die Folgende sehen, war die Bereitstellung erfolgreich:  
  
    > ------ Build started: Project: tutorial, Configuration: Debug ------Skipping 'Sales Orders.rdl'. Element ist auf dem neuesten Stand. Erstellung abgeschlossen--0 Fehler, 0 Warnungen---bereitstellen, die gestartet: Projekt: Lernprogramm Konfiguration: Debug---zu http:// Bereitstellen\<Servername > / ReportserverDeploying melden "/ Tutorial/Sales Orders". Bereitstellen abgeschlossen--0 Fehler, 0 Warnungen ==== Build: 1 erfolgreich oder aktuell, 0 fehlgeschlagen, 0 übersprungen ==== bereitstellen: 1 erfolgreich, 0 fehlgeschlagen, 0 übersprungen ====  
  
     Wenn Sie eine Fehlermeldung wie die Folgende sehen, überprüfen Sie, ob Sie über Berechtigungen für den Berichtsserver verfügen und ob Sie [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] mit Administratorrechten gestartet haben.  
  
    > "Die Berechtigungen für Benutzer" XXXXXXXX\\< Ihr Benutzername\>"zum Ausführen des Vorgangs unzureichend sind"  
  
6.  Starten Sie Berichts-Manager mit Administratorrechten, indem Sie z. B. mit der rechten Maustaste auf das Symbol für Internet Explorer und dann auf **Als Administrator ausführen**klicken.  
  
     Wechseln Sie zur Berichts-Manager-URL z. B.: `http://<server name>/reports`.  
  
7.  Navigieren Sie zum Ordner mit dem Bericht, und klicken Sie auf den Namen des Berichts `Sales Orders` auf den gerenderten Bericht im Browser anzuzeigen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben nun das Lernprogramm zum Erstellen eines grundlegenden Tabellenberichts erfolgreich abgeschlossen.  
  
## <a name="see-also"></a>Siehe auch  
 [Filtern, gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  