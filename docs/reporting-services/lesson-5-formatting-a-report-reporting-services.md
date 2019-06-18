---
title: 'Lektion 5: Formatieren eines Berichts (Reporting Services) | Microsoft-Dokumentation'
ms.date: 04/29/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: ae46efa9-6e04-48ec-afb4-5a2314dcb05a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a8bf8b6814f7989a904507cd89fbea397b8b6930
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65105929"
---
# <a name="lesson-5-formatting-a-report-reporting-services"></a>Lektion 5: Formatieren eines Berichts (Reporting Services)

Nachdem Sie dem Sales Orders-Bericht einen Datenbereich sowie einige Felder hinzugefügt haben, können Sie die Felder für Datum und Währung sowie die Spaltenköpfe formatieren.

## <a name="bkmk_format_date"></a>Formatieren des Datums

Im Feldausdruck „Datum“ werden standardmäßig Datums- und Uhrzeitinformationen angezeigt. Durch entsprechende Formatierung kann auch nur das Datum angezeigt werden.

1. Klicken Sie auf die Registerkarte **Entwurf**.
2. Klicken Sie mit der rechten Maustaste auf die Zelle mit dem Feldausdruck `[Date]`, und klicken Sie anschließend auf **Textfeldeigenschaften**.
3. Klicken Sie auf **Zahl** und anschließend im Feld **Kategorie** auf die Option **Datum**.
4. Wählen Sie im Feld **Typ** die Option **31. Januar 2000**aus.
5. Klicken Sie auf **OK**, um das Format zu übernehmen.
6. Zeigen Sie eine Vorschau des Berichts an, um die Formatänderung am Feld `[Date]` zu sehen, und wechseln Sie dann zurück zur Entwurfsansicht.

## <a name="bkmk_format_currency"></a>Formatieren der Währung

Im Feldausdruck „LineTotal“ wird eine Zahl im Standardzahlenformat angezeigt. Sie können das Feld formatieren, um die Zahl als Währung anzuzeigen.

1. Klicken Sie mit der rechten Maustaste auf die Zelle mit dem Ausdruck `[LineTotal]`, und klicken Sie anschließend auf **Textfeldeigenschaften**.
2. Klicken Sie im Spaltenlistenfeld ganz links auf **Zahl** und im Listenfeld **Kategorie** auf **Währung**.
3. Wenn Ihre regionale Einstellung „Englisch (USA)“ ist, sollten die Standardwerte im Listenfeld **Typ** folgendermaßen lauten:
    - **Dezimalstellen: 2**
    - **Negative Zahlen: ($12345.00)**
    - **Symbol: $ Englisch (USA)**
4. Wählen Sie **1000er-Trennzeichen verwenden**aus. Wird der Beispieltext **$12,345.00** angezeigt, sind Ihre Einstellungen korrekt.
5. Klicken Sie auf **OK**, um das Format zu übernehmen.
6. Zeigen Sie eine Vorschau des Berichts an, um die Änderung an der Ausdrucksspalte `[LineTotal]` zu sehen, und wechseln Sie dann zurück zur Entwurfsansicht.  

## <a name="bkmk_change_textstyle"></a>Ändern von Textart und Spaltenbreite

Sie können dem Bericht weitere Formatierungen hinzufügen, indem Sie die Kopfzeile markieren und die Breite der Datenspalten anpassen.

### <a name="to-format-header-rows-and-table-columns"></a>So formatieren Sie Kopfzeilen und Tabellenspalten

1. Klicken Sie auf die Tabelle, damit die Spalten- und Zeilenhandles über und neben der Tabelle angezeigt werden. Die grauen Balken oberhalb und neben der Tabelle stellen die Spalten- und Zeilenhandles dar.

2. Zeigen Sie auf die Zeile zwischen Spaltenhandles, sodass sich der Cursor in einen Doppelpfeil ändert. Ziehen Sie die Spalten auf die gewünschte Größe.
    ![rs_GrundlegendeTabellendetailsEntwurf](media/rs-basictabledetailsdesign.png)

3. Wählen Sie die Zeile mit den Spaltenkopfbezeichnungen aus, und klicken Sie im Menü **Format** auf **Schriftart** > **Fett**.

4. Zeigen Sie eine Vorschau des Berichts an. Dies sollte folgendermaßen aussehen:

    ![Vorschau der Tabelle mit fett formatierten Spaltenüberschriften](media/rs-basictabledetailsformattedpreview.png "Preview of table with bold column headers")  

5. Klicken Sie im Menü **Datei** auf **Alle Speichern**, um den Bericht zu speichern.

## <a name="next-steps"></a>Nächste Schritte

In dieser Lektion haben Sie erfolgreich Spaltenüberschriften und Feldausdrücke formatiert. Als Nächstes erfahren Sie, wie Sie dem Bericht Gruppierungen und Gesamtwerte hinzufügen. Weiter mit [Lektion 6: Hinzufügen von Gruppierungen und Gesamtwerten &#40;Reporting Services&#41;](lesson-6-adding-grouping-and-totals-reporting-services.md).

## <a name="see-also"></a>Siehe auch

[Formatieren von Zahlen und Datumsangaben &#40;Berichts-Generator und SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)
[Renderingverhalten &#40;Berichts-Generator und SSRS&#41;](report-design/rendering-behaviors-report-builder-and-ssrs.md)
