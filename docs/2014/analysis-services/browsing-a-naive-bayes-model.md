---
title: Durchsuchen eines Naive Bayes-Modells | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9160b48-3beb-439c-9694-f084e1afa625
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 36031bb080ff80c14a4f91bca102bd859df1f539
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046577"
---
# <a name="browsing-a-naive-bayes-model"></a>Durchsuchen eines Naive Bayes-Modells
  Beim Öffnen eines Naïve Bayes-Modells mit **Durchsuchen**, das Modell in einem interaktiven Viewer über vier unterschiedliche Bereiche angezeigt. Verwenden Sie den Viewer, um Korrelationen zu untersuchen sowie um Informationen zum Modell und den zugrunde liegenden Daten abzurufen.  
  
-   [Abhängigkeitsnetzwerk](#bkmk_DepNet)  
  
-   [Attributprofile](#bkmk_AttProf)  
  
-   [Attributmerkmale](#bkmk_AttChar)  
  
-   [Attributunterscheidung](#bkmk_AttDisc)  
  
##  <a name="BKMK_Tabs"></a> Untersuchen des Modells  
 Der Zweck des Viewers besteht darin, die Interaktion zwischen Eingabe- und Ausgabeattributen (Eingaben und abhängigen Variablen) zu untersuchen, die vom [!INCLUDE[msCoName](../includes/msconame-md.md)] Naïve Bayes-Modell ermittelt wurden.  
  
 Wenn Sie mit dem Naïve Bayes-Viewer ausprobieren möchten, verwenden Sie die [klassifizieren-Assistenten &#40;Data Mining-Add-ins für Excel&#41; ](classify-wizard-data-mining-add-ins-for-excel.md) Assistenten im Data Mining-Menüband, klicken Sie auf der **erweitert** aus, und ändern der Algorithmus zum Verwenden des Naïve Bayes-Algorithmus  
  
 Diesen Beispielen haben wir die Quelldaten in der Beispielarbeitsmappe verwendet, und die Spalte gruppiert **Yearly Income**, in fünf Einkommensgruppen von **sehr niedrig** auf **sehr hohen**. Anhand des Naïve Bayes-Modells wurden anschließend die Faktoren analysiert, die mit den einzelnen Einkommenskategorien korrelierten.  
  
###  <a name="bkmk_DepNet"></a> Abhängigkeitsnetzwerk  
 Ist das erste Fenster, das Sie verwenden die **Abhängigkeitsnetzwerk**. Es zeigt auf einen Blick, welche Eingaben eng mit dem ausgewählten Ergebnis korrelieren.  
  
 ![Abhängigkeitsnetzwerk in Naive Bayes-Viewer](media/dm13-nb.gif "Abhängigkeitsnetzwerk in Naive Bayes-Viewer")  
  
##### <a name="explore-the-dependency-network"></a>Untersuchen des Abhängigkeitsnetzwerks  
  
1.  Klicken Sie zuerst auf das zielergebnis **Yearly Income**, die als Knoten im Diagramm dargestellt wird.  
  
     Die hervorgehobenen Knoten, die die Zielvariable umschließen, sind die Knoten, die statistisch mit diesem Ergebnis korrelieren. Verwenden Sie die Legende im unteren Bereich des Viewers, um die Art der Beziehung zu verstehen.  
  
2.  Klicken Sie auf den Schieberegler auf der linken Seite des Viewers, und ziehen Sie ihn nach unten.  
  
     Durch dieses Steuerelement werden die unabhängigen Variablen nach der Stärke der Abhängigkeiten gefiltert. Wenn Sie den Schieberegler nach unten ziehen, verbleiben nur die stärksten Links im Diagramm.  
  
3.  Nachdem Sie das Diagramm gefiltert haben, klicken Sie auf die Schaltfläche **Diagrammsicht kopieren**. Wählen Sie anschließend ein Arbeitsblatt in Excel aus, und drücken Sie STRG+V.  
  
     Durch diese Option wird die ausgewählte Ansicht einschließlich Filtern und Hervorhebungen kopiert.  
  
 [Zurück nach oben](#BKMK_Tabs)  
  
###  <a name="bkmk_AttProf"></a> Attributprofile  
 Die **Attributprofile** Windows bietet Ihnen eine Übersicht des wie alle anderen Variablen mit den einzelnen Ergebnissen verknüpft sind.  
  
##### <a name="explore-the-profiles"></a>Untersuchen der Profile  
  
1.  Um einige Werte ausblenden, sodass Sie die Ergebnisse besser vergleichen können, klicken Sie auf die Spaltenüberschrift, und ziehen diese unter eine andere Spalte.  
  
     ![attributprofile in Naive Bayes-Viewer](media/dm13-nb-attprof.gif "attributprofile in Naive Bayes-Viewer")  
  
2.  Klicken Sie in eine Zelle, um die Verteilung der Werte im Anzeigen der **Mininglegende**.  
  
     Da die Attribute, die den verschiedenen Ergebnissen zugeordnet sind, visuell angezeigt werden, erkennen Sie auf Anhieb interessante Korrelationen, z. B. die Einkommensverteilung nach Region.  
  
3.  Klicken Sie zum Abrufen der Daten, die dieser Ansicht zugrunde liegen auf **nach Excel kopieren**. Eine Tabelle wird in einem neuen Arbeitsblatt generiert, das die Korrelationen zwischen den einzelnen Attributen und Ergebnissen anzeigt. In dieser Excel-Tabelle können Sie Spalten einfach ausblenden oder filtern.  
  
 [Zurück nach oben](#BKMK_Tabs)  
  
###  <a name="bkmk_AttChar"></a> Attributmerkmale  
 Die **Attributmerkmale** Ansicht ist für die gründliche Analyse einer bestimmten Ergebnisvariablen und Ihrer Einflussfaktoren hilfreich.  
  
 ![-Attribut Merkmale in Naive Bayes-Viewer](media/dm13-nb-viewer.gif "-Attribut Merkmale in Naive Bayes-Viewer")  
  
##### <a name="explore-the-attribute-characteristics"></a>Untersuchen der Attributeigenschaften  
  
1.  Klicken Sie auf **Wert** , und wählen Sie ein Element aus der **Wert**.  
  
     Während Sie ein Zielergebnis auswählen, wird das Diagramm aktualisiert und zeigt nach Wichtigkeit sortiert die Faktoren an, die am stärksten mit dem Ergebnis verknüpft sind.  
  
     Beachten Sie, dass bei der Erstellung eines Modells mit dem [wichtige Einflussfaktoren analysieren &#40;Tabellenanalysetools für Excel&#41; ](analyze-key-influencers-table-analysis-tools-for-excel.md) Option erstellen Sie Modelle, die mehr als einem vorhersagbaren Attribut anlegen. In allen anderen Assistenten der Data Mining-Add-Ins sind Sie jedoch auf ein vorhersagbares Attribut beschränkt.  
  
2.  Klicken Sie auf **nach Excel kopieren** zum Erstellen einer Tabelle in einem neuen Arbeitsblatt oder Auflisten der Ergebnisse für alle Attribute, die mit dem ausgewählten zielergebnis verknüpft sind.  
  
 [Zurück nach oben](#BKMK_Tabs)  
  
###  <a name="bkmk_AttDisc"></a> Attributunterscheidung  
 Die **Attributunterscheidung** Ansicht hilft zwei Ergebnisse oder ein Ergebnis im Vergleich zu allen anderen Ergebnissen vergleichen.  
  
 ![attributunterscheidung in Naive Bayes-Viewer-Attribut](media/dm13-nb-attdisc.gif "-Attribut attributunterscheidung in Naive Bayes-Viewer")  
  
##### <a name="explore-attribute-discrimination"></a>Untersuchen der Attributunterscheidung  
  
1.  Verwenden Sie die Steuerelemente **Wert 1** und **Wert 2**, um die Ergebnisse aus, die Sie vergleichen möchten.  
  
     Z. B. in diesem Modell wurden einige interessante Attribute in der niedrigen einkommensgruppe, so dass wir die niedrigste einkommensgruppe in der ersten Dropdownliste ausgewählt haben, und haben **alle anderen Staaten** in der zweiten Dropdownliste aus.  
  
     Die Attribute werden nach Wichtigkeit sortiert (die auf Grundlage der Trainingsdaten berechnet wird). Daher ist der Beruf der Faktor, der am stärksten mit dem Einkommen korreliert (zumindest bei dieser Zielgruppe).  
  
     Um die genauen Zahlen anzuzeigen, klicken Sie auf den Farbbalken und zeigen die **Mininglegende**.  
  
2.  Beachten Sie, dass niedrigere Einkommen auch mit der Region Europa korreliert werden.  
  
     Das Naïve Bayes-Modell unterstützt keine Drilldowns. Wenn Sie jedoch den Fällen, die dieser Ergebnisgruppe zugeordnet sind, auf den Grund gehen möchten, können Sie eine Abfrage ausführen. Weitere Informationen zu Abfragen für diesen Typ des Modells finden Sie unter [Beispiele für Naive Bayes-Modell](data-mining/naive-bayes-model-query-examples.md).  
  
 [Zurück nach oben](#BKMK_Tabs)  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  