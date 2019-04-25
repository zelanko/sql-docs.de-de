---
title: Durchsuchen eines Naive Bayes-Modells | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: f9160b48-3beb-439c-9694-f084e1afa625
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 91d39b174a0febed1aa6fd57140412828adc843b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62466178"
---
# <a name="browsing-a-naive-bayes-model"></a>Durchsuchen eines Naive Bayes-Modells
  Beim Öffnen eines Naïve Bayes-Modells mit **Durchsuchen**, das Modell in einem interaktiven Viewer mit vier unterschiedlichen Bereichen angezeigt. Verwenden Sie den Viewer, um Korrelationen zu untersuchen sowie um Informationen zum Modell und den zugrunde liegenden Daten abzurufen.  
  
-   [Abhängigkeitsnetzwerk](#bkmk_DepNet)  
  
-   [Attributprofile](#bkmk_AttProf)  
  
-   [Attributmerkmale](#bkmk_AttChar)  
  
-   [Attributunterscheidung](#bkmk_AttDisc)  
  
##  <a name="BKMK_Tabs"></a> Durchsuchen des Modells  
 Der Zweck des Viewers besteht darin, die Interaktion zwischen Eingabe- und Ausgabeattributen (Eingaben und abhängigen Variablen) zu untersuchen, die vom [!INCLUDE[msCoName](../includes/msconame-md.md)] Naïve Bayes-Modell ermittelt wurden.  
  
 Wenn Sie mit dem Naïve Bayes-Viewer experimentieren möchten, verwenden Sie die [Assistent zum Klassifizieren &#40;Data Mining-Add-ins für Excel&#41; ](classify-wizard-data-mining-add-ins-for-excel.md) Assistenten im Data Mining-Menüband, klicken Sie auf die **erweitert** aus, und ändern der Algorithmus die Naïve Bayes-Algorithmus verwenden.  
  
 Diesen Beispielen haben wir die Daten in der Beispielarbeitsmappe verwendet, und die Spalte gruppiert **Yearly Income**, in fünf Einkommensgruppen von **sehr niedrig** zu **sehr hohe**. Anhand des Naïve Bayes-Modells wurden anschließend die Faktoren analysiert, die mit den einzelnen Einkommenskategorien korrelierten.  
  
###  <a name="bkmk_DepNet"></a> Abhängigkeitsnetzwerk  
 Das erste Fenster Sie verwenden die **Abhängigkeitsnetzwerk**. Es zeigt auf einen Blick, welche Eingaben eng mit dem ausgewählten Ergebnis korrelieren.  
  
 ![Abhängigkeitsnetzwerk in Naive Bayes-Viewer](media/dm13-nb.gif "Abhängigkeitsnetzwerk in Naive Bayes-Viewer")  
  
##### <a name="explore-the-dependency-network"></a>Untersuchen des Abhängigkeitsnetzwerks  
  
1.  Klicken Sie zunächst das zielergebnis **Yearly Income**, die als Knoten im Diagramm dargestellt wird.  
  
     Die hervorgehobenen Knoten, die die Zielvariable umschließen, sind die Knoten, die statistisch mit diesem Ergebnis korrelieren. Verwenden Sie die Legende im unteren Bereich des Viewers, um die Art der Beziehung zu verstehen.  
  
2.  Klicken Sie auf den Schieberegler auf der linken Seite des Viewers, und ziehen Sie ihn nach unten.  
  
     Durch dieses Steuerelement werden die unabhängigen Variablen nach der Stärke der Abhängigkeiten gefiltert. Wenn Sie den Schieberegler nach unten ziehen, verbleiben nur die stärksten Links im Diagramm.  
  
3.  Nachdem Sie das Diagramm gefiltert haben, klicken Sie auf die Schaltfläche **Diagrammsicht kopieren**. Wählen Sie anschließend ein Arbeitsblatt in Excel aus, und drücken Sie STRG+V.  
  
     Durch diese Option wird die ausgewählte Ansicht einschließlich Filtern und Hervorhebungen kopiert.  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
###  <a name="bkmk_AttProf"></a> Attributprofile  
 Die **Attributprofile** Windows erhalten Sie einen visuellen Hinweis wie alle anderen Variablen mit den einzelnen Ergebnissen verknüpft sind.  
  
##### <a name="explore-the-profiles"></a>Untersuchen der Profile  
  
1.  Um einige Werte ausblenden, sodass Sie die Ergebnisse besser vergleichen können, klicken Sie auf die Spaltenüberschrift, und ziehen diese unter eine andere Spalte.  
  
     ![attributprofile in Naive Bayes-Viewer](media/dm13-nb-attprof.gif "attributprofile in Naive Bayes-Viewer")  
  
2.  Klicken Sie auf eine beliebige Zelle zum Anzeigen der Verteilung der Werte in der **Mininglegende**.  
  
     Da die Attribute, die den verschiedenen Ergebnissen zugeordnet sind, visuell angezeigt werden, erkennen Sie auf Anhieb interessante Korrelationen, z. B. die Einkommensverteilung nach Region.  
  
3.  Um die Daten, die dieser Ansicht zugrunde liegen zu erhalten, klicken Sie auf **nach Excel kopieren**. Eine Tabelle wird in einem neuen Arbeitsblatt generiert, das die Korrelationen zwischen den einzelnen Attributen und Ergebnissen anzeigt. In dieser Excel-Tabelle können Sie Spalten einfach ausblenden oder filtern.  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
###  <a name="bkmk_AttChar"></a> Attributmerkmale  
 Die **Attributmerkmale** Ansicht ist für die gründliche Analyse einer bestimmten Ergebnisvariablen und Ihrer Einflussfaktoren hilfreich.  
  
 ![Attribut Merkmale in Naive Bayes-Viewer](media/dm13-nb-viewer.gif "Attribut Merkmale in Naive Bayes-Viewer")  
  
##### <a name="explore-the-attribute-characteristics"></a>Untersuchen der Attributeigenschaften  
  
1.  Klicken Sie auf **Wert** , und wählen Sie ein Element aus der **Wert**.  
  
     Während Sie ein Zielergebnis auswählen, wird das Diagramm aktualisiert und zeigt nach Wichtigkeit sortiert die Faktoren an, die am stärksten mit dem Ergebnis verknüpft sind.  
  
     Beachten Sie, dass bei der Erstellung eines Modells mit dem [wichtige Einflussfaktoren analysieren &#40;Tabellenanalysetools für Excel&#41; ](analyze-key-influencers-table-analysis-tools-for-excel.md) auswählen, können Sie Modelle mit mehr als ein vorhersagbares Attribut erstellen. In allen anderen Assistenten der Data Mining-Add-Ins sind Sie jedoch auf ein vorhersagbares Attribut beschränkt.  
  
2.  Klicken Sie auf **nach Excel kopieren** zum Erstellen einer Tabelle in einem neuen Arbeitsblatt, das Auflisten der Ergebnisse für alle Attribute, die mit dem ausgewählten zielergebnis verknüpft sind.  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
###  <a name="bkmk_AttDisc"></a> Attributunterscheidung  
 Die **Attributunterscheidung** Ansicht unterstützt zwei Ergebnisse oder ein Ergebnis im Vergleich zu allen anderen Ergebnissen vergleichen.  
  
 ![attributunterscheidung in Naive Bayes-Viewer Attribut](media/dm13-nb-attdisc.gif "Attribut attributunterscheidung in Naive Bayes-Viewer")  
  
##### <a name="explore-attribute-discrimination"></a>Untersuchen der Attributunterscheidung  
  
1.  Verwenden Sie die Steuerelemente, **Wert 1** und **Wert 2**, um die Ergebnisse aus, die Sie vergleichen möchten.  
  
     Zum Beispiel in diesem Modell gab es einige interessante Attribute in der niedrigen einkommensgruppe, damit wir die niedrigste einkommensgruppe in der ersten Dropdownliste ausgewählt, und wählen **alle anderen Staaten** in der zweiten Dropdownliste aus.  
  
     Die Attribute werden nach Wichtigkeit sortiert (die auf Grundlage der Trainingsdaten berechnet wird). Daher ist der Beruf der Faktor, der am stärksten mit dem Einkommen korreliert (zumindest bei dieser Zielgruppe).  
  
     Um die genauen Zahlen anzuzeigen, klicken Sie auf den Farbbalken und zeigen die **Mininglegende**.  
  
2.  Beachten Sie, dass niedrigere Einkommen auch mit der Region Europa korreliert werden.  
  
     Das Naïve Bayes-Modell unterstützt keine Drilldowns. Wenn Sie jedoch den Fällen, die dieser Ergebnisgruppe zugeordnet sind, auf den Grund gehen möchten, können Sie eine Abfrage ausführen. Weitere Informationen zu Abfragen für diesen Typ des Modells finden Sie unter [Beispiele für Naive Bayes-Modell](data-mining/naive-bayes-model-query-examples.md).  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
