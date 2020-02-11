---
title: 'Lektion 6: Hinzufügen von Gruppierungen und Gesamtergebnissen (Reporting Services) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e3d61228-2aa4-42cc-955e-602dbf3406a7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5607dfb046e7f50eb3a015e1f4f13711256435a8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108405"
---
# <a name="lesson-6-adding-grouping-and-totals-reporting-services"></a>Lesson 6: Adding Grouping and Totals (Reporting Services)
  Fügen Sie dem Bericht Gruppierungen und Gesamtwerte hinzu, um Daten zu gruppieren und zusammenzufassen.  
  
 Weitere Informationen zum Hinzufügen von laufenden Summen zu Berichten finden Sie unter [Hinzufügen von Summen zu Reporting Services Berichten (SSRS)](https://www.tutorialgateway.org/add-total-and-subtotal-to-ssrs-report/).  
  
 **In diesem Thema:**  
  
-   [So gruppieren Sie Daten in einem Bericht](#bkmk_groupdata)  
  
-   [So fügen Sie einem Bericht Summen hinzu](#bkmk_addtotals)  
  
-   [So fügen Sie einem Bericht ein Tagesergebnis hinzu](#bkmk_adddailytotal)  
  
-   [So fügen Sie einem Bericht ein Gesamtergebnis hinzu](#bkmk_addgrandtotal)  
  
-   [So veröffentlichen Sie den Bericht auf dem Berichts Server (optional)](#bkmk_publishreport)  
  
##  <a name="bkmk_groupdata"></a>So gruppieren Sie Daten in einem Bericht  
  
1.  Klicken Sie auf die Registerkarte **Entwurf** .  
  
2.  Wenn der Bereich **Zeilen Gruppen** nicht angezeigt wird, klicken Sie mit der rechten Maustaste auf die Entwurfs Oberfläche, und klicken Sie auf **anzeigen** und dann auf **Gruppierung**.  
  
3.  Ziehen Sie im **Berichtsdatenbereich** das Feld `Date` in den Bereich **Zeilengruppen**. Platzieren Sie das Feld über der Zeile **(Details)**.  
  
     Beachten Sie, dass das Zeilenhandle nun Klammern zum Anzeigen einer Gruppe aufweist. Außerdem verfügt die Tabelle nun auf jeder Seite der vertikalen gepunkteten Linie einmal über die Spalte Date.  
  
     ![](../../2014/tutorials/media/rs-basictablegroups1design.gif "rs_BasicTableGroups1Design")  
  
4.  Ziehen Sie im **Berichtsdatenbereich** das Feld `Order` in den Bereich **Zeilengruppen**. Platzieren das Feld unter Date und über **Details**.  
  
     Beachten Sie, dass das Zeilenhandle nun zweimal Klammern zum Anzeigen von zwei Gruppen aufweist. Die Tabelle verfügt nun auch `Order` über zwei Spalten.  
  
5.  Löschen Sie die ursprünglichen Spalten Date und Order**rechts** der doppelten Linie. Dadurch werden die einzelnen Datensatzwerte entfernt, und nur der Gruppenwert wird angezeigt. Wählen Sie die Spaltenhandles für die beiden Spalten aus, klicken Sie mit der rechten Maustaste und wählen Sie **Spalten löschen**aus.  
  
     ![Auswählen der zu löschenden Spalten](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "Auswählen der zu löschenden Spalten")  
  
     Die Spaltenkopfzeilen und der Datumswert können erneut formatiert werden.  
  
6.  Wechseln Sie zur Registerkarte **Vorschau** , um eine Vorschau des Berichts anzuzeigen. Die Vorschau sollte ähnlich der folgenden Abbildung aussehen:  
  
     ![Tabelle gruppiert nach 'Date' und dann 'Order'](../../2014/tutorials/media/rs-basictablegroupspreview.gif "Tabelle gruppiert nach 'Date' und dann 'Order'")  
  
##  <a name="bkmk_addtotals"></a>So fügen Sie einem Bericht Summen hinzu  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Datenbereichszelle mit dem Feld `[LineTotal]`und anschließend auf **Gesamtergebnis hinzufügen**.  
  
     Dadurch wird eine Zeile mit dem Gesamtwert für die einzelnen Bestellungen in Dollar hinzugefügt.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Zelle mit dem Feld `[Qty]`und anschließend auf **Gesamtergebnis hinzufügen**.  
  
     Dadurch wird der Ergebniszeile eine Gesamtmenge für die einzelnen Bestellungen hinzugefügt.  
  
4.  Geben Sie in die leere Zelle links von `Sum[Qty]`die Bezeichnung**Order Total**ein.  
  
5.  Sie können der Ergebniszeile eine Hintergrundfarbe hinzufügen. Wählen Sie die beiden Gesamtergebniszellen und die Bezeichnungszelle aus.  
  
6.  Klicken Sie im Menü **Format** auf **Hintergrundfarbe**, klicken Sie auf **Hellgrau**und dann auf **OK**.  
  
     ![Entwurfsansicht: Einfache Tabelle mit Gesamtergebnis der Bestellungen](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "Entwurfsansicht: Einfache Tabelle mit Gesamtergebnis der Bestellungen")  
  
##  <a name="bkmk_adddailytotal"></a>So fügen Sie einem Bericht ein Tagesergebnis hinzu  
  
1.  Klicken Sie mit der rechten Maustaste auf die Zelle Order , zeigen Sie auf **Gesamtergebnis hinzufügen**, und klicken Sie auf **Danach**.  
  
     Dadurch wird eine neue Zeile mit Summen der Menge und Dollarbetrag für jeden Tag und der Bezeichnung "**Total**" in der Spalte Order hinzugefügt.  
  
2.  Geben Sie das Wort **Daily** in der gleichen Zelle vor dem Wort **Total** ein, sodass es die **tägliche Summe**liest.  
  
3.  Wählen Sie die Zelle **Daily Total** aus, und markieren Sie die beiden Zellen für **Sum** sowie die leere Zelle dazwischen.  
  
4.  Klicken Sie im Menü **Format** auf **Hintergrundfarbe**, klicken Sie auf **Orange**und dann auf **OK**.  
  
     ![](../../2014/tutorials/media/rs-basictablesumdaytotaldesign.gif "rs_BasicTableSumDayTotalDesign")  
  
##  <a name="bkmk_addgrandtotal"></a>So fügen Sie einem Bericht ein Gesamtergebnis hinzu  
  
1.  Klicken Sie mit der rechten Maustaste auf die Zelle Date, zeigen Sie auf **Gesamtergebnis hinzufügen**, und klicken Sie auf **Danach**.  
  
     Dadurch wird eine neue Zeile mit Summen der Menge und dem Dollarbetrag für den gesamten Bericht und die **Gesamt** Bezeichnung in der `Date` Spalte hinzugefügt.  
  
2.  Geben Sie in der gleichen Zelle zuerst das Wort **Grand** und anschließend das Wort **Total** ein, um **Grand Total**zu erhalten.  
  
3.  Wählen Sie die Zelle **Grand Total** aus, und markieren Sie die beiden Zellen für **Sum** sowie die leeren Zellen dazwischen.  
  
4.  Klicken Sie im Menü **Format** auf **Hintergrundfarbe**, klicken Sie auf **Hellblau**und dann auf **OK**.  
  
     ![Entwurfsansicht: Gesamtergebnis in einfacher Tabelle](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "Entwurfsansicht: Gesamtergebnis in einfacher Tabelle")  
  
5.  Klicken Sie auf "Vorschau".  
  
     Die letzte Seite sollte etwa folgendermaßen aussehen:  
  
     ![Vorschau: Einfache Tabelle mit Gesamtergebnis](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "Vorschau: Einfache Tabelle mit Gesamtergebnis")  
  
##  <a name="bkmk_publishreport"></a>So veröffentlichen Sie den Bericht auf dem Berichts Server (optional)  
  
1.  Ein optionaler Schritt besteht darin, den vervollständigten Bericht auf dem Berichtsserver im einheitlichen Modus zu veröffentlichen, damit Sie den Bericht im Berichts-Manager anzeigen können.  
  
2.  Klicken Sie auf der Symbolleiste auf **Projekt** , und klicken Sie dann auf auf die Option für die **Eigenschaften des Lernprogramms**.  
  
3.  Geben Sie in **TargetServerURL** den Namen des Berichts Servers ein, z. b. **http://\<Servername>/ReportServer**  
  
4.  Klicken Sie auf **OK**  
  
5.  Klicken Sie auf der Symbolleiste auf **Erstellen** , und klicken Sie dann auf **Tutorial bereitstellen**.  
  
     Wenn Sie im Ausgabefenster eine Meldung wie die Folgende sehen, war die Bereitstellung erfolgreich:  
  
    > ------ Build started: Project: tutorial, Configuration: Debug ------Skipping 'Sales Orders.rdl'. Das Element ist auf dem neuesten Stand. Build abgeschlossen--0 Fehler, 0 Warnungen------Bereitstellung gestartet: Projekt: Tutorial, Konfiguration: Debuggen------\<bereitstellen auf http://Servername>/reportserverdeploying Bericht "/Tutorial/Sales Orders". Bereitstellung abgeschlossen--0 Fehler, 0 Warnungen = = = = = = = = = = Build: 1 erfolgreich oder aktuell, 0 fehlgeschlagen, 0 übersprungen = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =  
  
     Wenn Sie eine Fehlermeldung wie die Folgende sehen, überprüfen Sie, ob Sie über Berechtigungen für den Berichtsserver verfügen und ob Sie [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] mit Administratorrechten gestartet haben.  
  
    > "Die dem Benutzer ' xxxxxxxx\\<Ihrem Benutzernamen\>' gewährten Berechtigungen reichen zum Ausführen dieses Vorgangs nicht aus."  
  
6.  Starten Sie Berichts-Manager mit Administratorrechten, indem Sie z. B. mit der rechten Maustaste auf das Symbol für Internet Explorer und dann auf **Als Administrator ausführen**klicken.  
  
     Wechseln Sie zur Berichts-Manager-URL z. B.: `http://<server name>/reports`.  
  
7.  Wechseln Sie zum Ordner, der den Bericht enthält, und klicken Sie auf den Namen des Berichts `Sales Orders`, um den gerenderten Bericht im Browser anzuzeigen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben nun das Lernprogramm zum Erstellen eines grundlegenden Tabellenberichts erfolgreich abgeschlossen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
