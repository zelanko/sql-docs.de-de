---
title: 'Lektion 4: Hinzufügen einer Tabelle zum Bericht (Reporting Services) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ddf2914-bcdd-427d-8cba-0ccb8342f819
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3bb152b749041451cdb3a3294c24d8b172c49a99
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108451"
---
# <a name="lesson-4-adding-a-table-to-the-report-reporting-services"></a>Lektion 4: Hinzufügen einer Tabelle zum Bericht (Reporting Services)
  Nach dem Definieren des Datasets können Sie mit dem Entwerfen des Berichts beginnen. Zum Erstellen eines Berichtslayouts verschieben Sie mit Drag und Drop Datenbereiche, Textfelder, Bilder und andere Elemente auf die Entwurfsoberfläche, die in den Bericht eingebunden werden sollen.  
  
 Elemente, die wiederholte Zeilen von Daten aus zugrunde liegenden Datasets enthalten, werden als *Datenbereiche*bezeichnet. Ein grundlegender Bericht enthält typischerweise nur einen Datenbereich. Sie können jedoch weitere Datenbereiche hinzufügen, z. B. wenn dem Tabellenbericht ein Diagramm hinzugefügt werden soll. Nachdem Sie einen Datenbereich hinzugefügt haben, können Sie diesem Felder hinzufügen.  
  
### <a name="to-add-a-table-data-region-and-fields-to-a-report-layout"></a>So fügen Sie einem Berichtslayout einen Tabellendatenbereich und Felder hinzu  
  
1.  Klicken Sie in **Toolbox**auf **Tabelle**, und klicken Sie anschließend auf die Entwurfsoberfläche und ziehen Sie die Maus. Vom Berichts-Designer wird ein Tabellendatenbereich mit drei Spalten in der Mitte der Entwurfsoberfläche gezeichnet.  
  
    > [!NOTE]  
    >  Die **Toolbox** kann auf der linken Seite des **Berichtsdatenbereichs** als Registerkarte angezeigt werden. Um die **Toolbox**zu öffnen, bewegen Sie den Mauszeiger über die Registerkarte **Toolbox** . Wenn die **Toolbox** nicht sichtbar ist, klicken Sie im Menü **Ansicht** auf **Toolbox**.  
  
2.  Erweitern Sie im **Berichtsdaten** Bereich das **AdventureWorksDataSet** -DataSet, um die Felder anzuzeigen.  
  
3.  Ziehen Sie das Feld Date aus dem **Berichtsdatenbereich** in die erste Spalte in der Tabelle.  
  
     Wenn Sie das Feld in der ersten Spalte ablegen, werden zwei Vorgänge ausgeführt. Zunächst wird in der Datenzelle der als *Feldausdruck*bezeichnete Feldname in Klammern: `[Date]`angezeigt. Dann wird automatisch der Kopfzeile ein Wert für den Spaltenkopf hinzugefügt, und zwar direkt über dem Feldausdruck. Standardmäßig ist die Spalte der Name des Felds. Sie können den Kopfzeilentext auswählen und einen neuen Namen eingeben.  
  
4.  Ziehen Sie das Feld Order aus dem **Berichtsdatenbereich** in die zweite Spalte in der Tabelle.  
  
5.  Ziehen Sie das Feld Product aus dem **Berichtsdatenbereich** in die dritte Spalte in der Tabelle.  
  
6.  Ziehen Sie das Feld Qty an den rechten Rand der dritten Spalte, bis Sie einen vertikalen Cursor erhalten und der Mauszeiger ein Pluszeichen [+] aufweist. Wenn Sie die Maustaste loslassen, wird eine vierte Spalte für `[Qty]`erstellt.  
  
7.  Fügen Sie das Feld LineTotal auf dieselbe Weise hinzu, wodurch eine fünfte Spalte erstellt wird.  
  
    > [!NOTE]  
    >  Der Spaltenheader lautet "Line Total". Der Berichts-Designer erstellt für die Spalte automatisch einen besser lesbaren Namen, indem er "LineTotal" in zwei Wörter unterteilt.  
  
     Die folgende Abbildung zeigt einen Datenbereich einer Tabelle, der mit folgenden Feldern aufgefüllt wurde: Date, Order, Product, Qty und Line Total.  
  
     ![Entwurf, Tabelle mit Kopfzeile und Detailzeile](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "Entwurf, Tabelle mit Kopfzeile und Detailzeile")  
  
## <a name="preview-your-report"></a>Zeigen Sie den Bericht in der Vorschau an.  
 Wenn Sie einen Bericht in der Vorschau anzeigen, können Sie den gerenderten Bericht überprüfen, ohne ihn zuvor auf einem Berichtsserver zu veröffentlichen. Es empfiehlt sich beispielsweise, den Bericht zur Entwurfszeit häufig in der Vorschau anzuzeigen. Wenn Sie den Bericht in der Vorschau anzuzeigen, wird auch eine Überprüfung des Entwurfs und der Datenverbindungen ausgeführt, damit Sie Fehler und Probleme korrigieren können, bevor Sie den Bericht auf einem Berichtsserver veröffentlichen.  
  
#### <a name="to-preview-a-report"></a>So zeigen Sie die Vorschau eines Berichts an  
  
-   Klicken Sie auf die Registerkarte **Vorschau** . Berichts-Designer führt den Bericht aus und zeigt ihn in der Vorschau Ansicht an.  
  
     In der folgenden Abbildung wird ein Teil des Berichts in der Ansicht Vorschau angezeigt.  
  
     ![Vorschau, Detailzeilen der Tabelle mit 5 Spalten](../../2014/tutorials/media/rs-basictabledetailspreview.gif "Vorschau, Detailzeilen der Tabelle mit 5 Spalten")  
  
     Beachten Sie, dass die Währungsangabe (in der Spalte Line Total) sechs Stellen nach dem Dezimaltrennzeichen aufweist und dass das Datum einen Zeitstempel enthält. Diese Formatierung wird in der nächsten Lektion korrigiert.  
  
> [!NOTE]  
>  Klicken Sie im Menü **Datei** auf **Alle Speichern** , um den Bericht zu speichern.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben Ihrem Bericht erfolgreich einen Tabellendatenbereich hinzugefügt, dem Datenbereich Felder hinzugefügt und den Bericht in der Vorschau angezeigt. Anschließend formatieren Sie Spaltenheader sowie Datums- und Währungswerte. Weitere Informationen finden Sie unter [Lektion 5: Formatieren eines Berichts (Reporting Services)](../reporting-services/lesson-5-formatting-a-report-reporting-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellen &#40;Berichts-Generator und SSRS&#41;](report-design/tables-report-builder-and-ssrs.md)   
 [Datasetfeld-Sammlung &#40;Berichts-Generator und SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
  
  
