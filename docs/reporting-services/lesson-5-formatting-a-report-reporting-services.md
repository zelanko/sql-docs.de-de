---
title: 'Lektion 5: Formatieren eines Berichts (Reporting Services) | Microsoft-Dokumentation'
ms.date: 05/23/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: ae46efa9-6e04-48ec-afb4-5a2314dcb05a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1c5a41b39b5c22c05ac4b13a9e57606110b60a2b
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56291108"
---
# <a name="lesson-5-formatting-a-report-reporting-services"></a>Lektion 5: Formatieren eines Berichts (Reporting Services)
Nachdem Sie dem Sales Orders-Bericht einen Datenbereich sowie einige Felder hinzugefügt haben, können Sie die Felder für Datum und Währung sowie die Spaltenköpfe formatieren.  
  
## <a name="bkmk_format_date"></a>Formatieren des Datums  
Im Feld Date werden standardmäßig Datums- und Uhrzeitangaben angezeigt. Durch entsprechende Formatierung kann auch nur das Datum angezeigt werden.  
  
#### <a name="to-format-a-date-field"></a>So formatieren Sie ein Datumsfeld  
  
1.  Klicken Sie auf die Registerkarte **Entwurf** .  
  
2.  Klicken Sie mit der rechten Maustaste auf die Zelle mit dem Feldausdruck `[Date]` und anschließend auf das Dialogfeld **Textfeldeigenschaften**.  
  
3.  Klicken Sie auf **Zahl**und anschließend im Feld **Kategorie** auf **Datum**.  
  
4.  Wählen Sie im Feld **Typ** die Option **31. Januar 2000**aus.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Zeigen Sie den Bericht in der Vorschau an, um die Änderung am Feld `[Date]` zu sehen, und wechseln Sie dann zurück zur Entwurfsansicht.  
  
## <a name="bkmk_format_currency"></a>Formatieren der Währung  
Im Feld **LineTotal** wird eine Zahl im Standardzahlenformat angezeigt. Formatieren Sie das Feld, um die Zahl als Währung anzuzeigen.  
  
#### <a name="to-format-a-currency-field"></a>So formatieren Sie ein Währungsfeld  
  
1.  Klicken Sie mit der rechten Maustaste auf die Zelle mit dem Feldausdruck `[LineTotal]` und anschließend auf das Dialogfeld **Textfeldeigenschaften**.  
  
2.  Klicken Sie auf **Zahl**und wählen Sie im Feld **Kategorie** die Option **Währung**aus.  
  
3.  Wenn die regionale Einstellung Englisch (USA) ist, sollten folgende Standardwerte verwendet werden:  
  
    -   **Dezimalstellen: 2**  
  
    -   **Negative Zahlen: ($12345.00)**  
  
    -   **Symbol: $ Englisch (USA)**  
  
4.  Wählen Sie **1000er-Trennzeichen verwenden**aus.  
  
    Wenn der Beispieltext **$12,345.00**lautet, sind alle Einstellungen korrekt.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Zeigen Sie den Bericht in der Vorschau an, um die Änderung am Feld `[LineTotal]` zu sehen, und wechseln Sie dann zurück zur Entwurfsansicht.  
  
## <a name="bkmk_change_textstyle"></a>Ändern von Textart und Spaltenbreite  
Sie können auch die Formatierung der Kopfzeile ändern, um diese von den anderen Datenzeilen im Bericht zu unterscheiden. Abschließend passen Sie die Breite der Spalten an.  
  
#### <a name="to-format-header-rows-and-table-columns"></a>So formatieren Sie Kopfzeilen und Tabellenspalten  
  
1.  Klicken Sie auf die Tabelle, damit die Spalten- und Zeilenhandles über und neben der Tabelle angezeigt werden. Die grauen Balken oberhalb und neben der Tabelle stellen die Spalten- und Zeilenhandles dar.  
       
  
2.  Zeigen Sie auf die Zeile zwischen Spaltenhandles, sodass sich der Cursor in einen Doppelpfeil ändert. Ziehen Sie die Spalten auf die gewünschte Größe.
 ![rs_GrundlegendeTabellendetailsEntwurf](../reporting-services/media/rs-basictabledetailsdesign.png)   
  
3.  Markieren Sie die Zeile mit den Spaltenkopfbezeichnungen, und zeigen Sie im Menü **Format** auf **Schriftart** . Klicken Sie dann auf **Fett**.  
  
4.  Klicken Sie auf **Vorschau** , um eine Vorschau des Berichts anzuzeigen. Der Bericht könnte beispielsweise wie folgt aussehen:  
  
    ![Vorschau der Tabelle mit fett formatierten Spaltenüberschriften](../reporting-services/media/rs-basictabledetailsformattedpreview.png "Preview of table with bold column headers")  
  
5.  Klicken Sie im Menü **Datei** auf **Alle Speichern** , um den Bericht zu speichern.  
  
## <a name="next-steps"></a>Next Steps  
Sie haben erfolgreich Spaltenköpfe sowie Datums- und Währungswerte formatiert. Als Nächstes fügen Sie dem Bericht Gruppierungen und Gesamtwerte hinzu. Siehe [Lektion 6: Hinzufügen von Gruppierungen und Gesamtwerten &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Formatieren von Zahlen und Datumsangaben &#40;Berichts-Generator und SSRS&#41;](../reporting-services/report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)  
[Renderingverhalten &#40;Berichts-Generator und SSRS&#41;](../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)  
  
  
  

