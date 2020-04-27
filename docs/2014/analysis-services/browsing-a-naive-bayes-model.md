---
title: Durchsuchen eines Naive Bayes-Modells | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f9160b48-3beb-439c-9694-f084e1afa625
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 65b8bb26a72903644b5985d69efc8adb362fe412
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66088482"
---
# <a name="browsing-a-naive-bayes-model"></a>Durchsuchen eines Naive Bayes-Modells
  Wenn Sie ein Naive Bayes-Modell mithilfe von **Durchsuchen**öffnen, wird das Modell in einem interaktiven Viewer mit vier verschiedenen Bereichen angezeigt. Verwenden Sie den Viewer, um Korrelationen zu untersuchen sowie um Informationen zum Modell und den zugrunde liegenden Daten abzurufen.  
  
-   [Abhängigkeitsnetzwerk](#bkmk_DepNet)  
  
-   [Attribut profile](#bkmk_AttProf)  
  
-   [Attributmerkmale](#bkmk_AttChar)  
  
-   [Attributunterscheidung](#bkmk_AttDisc)  
  
##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a>Untersuchen des Modells  
 Der Zweck des Viewers besteht darin, die Interaktion zwischen Eingabe- und Ausgabeattributen (Eingaben und abhängigen Variablen) zu untersuchen, die vom [!INCLUDE[msCoName](../includes/msconame-md.md)] Naïve Bayes-Modell ermittelt wurden.  
  
 Wenn Sie mit dem Naive Bayes-Viewer experimentieren möchten, verwenden Sie den Assistenten zum [klassifizieren &#40;Data Mining-Add-Ins für Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md) auf dem Menüband Data Mining, klicken Sie auf die Option **erweitert** , und ändern Sie den Algorithmus so, dass er den Naive Bayes-Algorithmus verwendet.  
  
 In diesen Beispielen haben wir die Quelldaten in der Beispiel Arbeitsmappe verwendet und die Spalte " **Jahreseinkommen**" in fünf Einkommensgruppen gruppiert (von **sehr niedrig** bis **sehr hoch**). Anhand des Naïve Bayes-Modells wurden anschließend die Faktoren analysiert, die mit den einzelnen Einkommenskategorien korrelierten.  
  
###  <a name="dependency-network"></a><a name="bkmk_DepNet"></a>Abhängigkeits Netzwerk  
 Das erste Fenster, das Sie verwenden, ist das **Abhängigkeits Netzwerk**. Es zeigt auf einen Blick, welche Eingaben eng mit dem ausgewählten Ergebnis korrelieren.  
  
 ![Abhängigkeitsnetzwerk in Naive Bayes-Viewer](media/dm13-nb.gif "Abhängigkeitsnetzwerk in Naive Bayes-Viewer")  
  
##### <a name="explore-the-dependency-network"></a>Untersuchen des Abhängigkeitsnetzwerks  
  
1.  Klicken Sie zuerst auf das Zielergebnis, **Jahreseinkommen**, das als Knoten im Diagramm dargestellt wird.  
  
     Die hervorgehobenen Knoten, die die Zielvariable umschließen, sind die Knoten, die statistisch mit diesem Ergebnis korrelieren. Verwenden Sie die Legende im unteren Bereich des Viewers, um die Art der Beziehung zu verstehen.  
  
2.  Klicken Sie auf den Schieberegler auf der linken Seite des Viewers, und ziehen Sie ihn nach unten.  
  
     Durch dieses Steuerelement werden die unabhängigen Variablen nach der Stärke der Abhängigkeiten gefiltert. Wenn Sie den Schieberegler nach unten ziehen, verbleiben nur die stärksten Links im Diagramm.  
  
3.  Nachdem Sie das Diagramm gefiltert haben, klicken Sie auf die Schaltfläche **Diagramm Ansicht kopieren**. Wählen Sie anschließend ein Arbeitsblatt in Excel aus, und drücken Sie STRG+V.  
  
     Durch diese Option wird die ausgewählte Ansicht einschließlich Filtern und Hervorhebungen kopiert.  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
###  <a name="attribute-profiles"></a><a name="bkmk_AttProf"></a> Attributprofile  
 Die Fenster " **Attribut profile** " geben Ihnen einen visuellen Hinweis darauf, wie alle anderen Variablen mit den einzelnen Ergebnissen verknüpft sind.  
  
##### <a name="explore-the-profiles"></a>Untersuchen der Profile  
  
1.  Um einige Werte ausblenden, sodass Sie die Ergebnisse besser vergleichen können, klicken Sie auf die Spaltenüberschrift, und ziehen diese unter eine andere Spalte.  
  
     ![Attributprofile in Naive Bayes-Viewer](media/dm13-nb-attprof.gif "Attributprofile in Naive Bayes-Viewer")  
  
2.  Klicken Sie in eine beliebige Zelle, um die Verteilung der Werte in der **Mining Legende**anzuzeigen.  
  
     Da die Attribute, die den verschiedenen Ergebnissen zugeordnet sind, visuell angezeigt werden, erkennen Sie auf Anhieb interessante Korrelationen, z. B. die Einkommensverteilung nach Region.  
  
3.  Zum Abrufen der Daten, die dieser Ansicht zugrunde liegen, klicken Sie auf **nach Excel kopieren**. Eine Tabelle wird in einem neuen Arbeitsblatt generiert, das die Korrelationen zwischen den einzelnen Attributen und Ergebnissen anzeigt. In dieser Excel-Tabelle können Sie Spalten einfach ausblenden oder filtern.  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
###  <a name="attribute-characteristics"></a><a name="bkmk_AttChar"></a>Attribut Merkmale  
 Die Ansicht " **Attribut Merkmale** " ist nützlich für eine ausführliche Untersuchung einer bestimmten Ergebnis Variablen und der zugehörigen Faktoren.  
  
 ![Attributmerkmale in Naive Bayes-Viewer](media/dm13-nb-viewer.gif "Attributmerkmale in Naive Bayes-Viewer")  
  
##### <a name="explore-the-attribute-characteristics"></a>Untersuchen der Attributeigenschaften  
  
1.  Klicken Sie auf **Wert** , und wählen Sie ein Element aus dem **Wert**aus.  
  
     Während Sie ein Zielergebnis auswählen, wird das Diagramm aktualisiert und zeigt nach Wichtigkeit sortiert die Faktoren an, die am stärksten mit dem Ergebnis verknüpft sind.  
  
     Beachten Sie Folgendes: Wenn Sie ein Modell mithilfe der Option [wichtige Einflussfaktoren analysieren &#40;Tabellenanalyse Tools für Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md) erstellen, können Sie Modelle erstellen, die mehr als ein vorhersagbares Attribut haben. In allen anderen Assistenten der Data Mining-Add-Ins sind Sie jedoch auf ein vorhersagbares Attribut beschränkt.  
  
2.  Klicken Sie auf **nach Excel kopieren** , um eine Tabelle in einem neuen Arbeitsblatt zu erstellen, in der die Ergebnisse für alle Attribute aufgelistet sind, die mit dem ausgewählten Zielergebnis verknüpft sind.  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
###  <a name="attribute-discrimination"></a><a name="bkmk_AttDisc"></a>Attribut Unterscheidung  
 Die Ansicht " **Attribut Unterscheidung** " unterstützt das Vergleichen zweier Ergebnisse oder eines Ergebnisses im Vergleich zu allen anderen Ergebnissen.  
  
 ![Attributunterscheidung in Naive Bayes-Viewer](media/dm13-nb-attdisc.gif "Attributunterscheidung in Naive Bayes-Viewer")  
  
##### <a name="explore-attribute-discrimination"></a>Untersuchen der Attributunterscheidung  
  
1.  Wählen Sie mit den Steuerelementen **Wert 1** und **Wert 2**die Ergebnisse aus, die Sie vergleichen möchten.  
  
     In diesem Modell gab es z. b. einige interessante Attribute in der Gruppe mit niedrigem Einkommen, daher haben wir die niedrigste Einkommensgruppe in der ersten Dropdown Liste ausgewählt und **alle anderen Zustände** in der zweiten Dropdown Liste ausgewählt.  
  
     Die Attribute werden nach Wichtigkeit sortiert (die auf Grundlage der Trainingsdaten berechnet wird). Daher ist der Beruf der Faktor, der am stärksten mit dem Einkommen korreliert (zumindest bei dieser Zielgruppe).  
  
     Um die genauen Abbildungen anzuzeigen, klicken Sie auf die farbige Leiste, und sehen Sie sich die **Mining Legende**an.  
  
2.  Beachten Sie, dass niedrigere Einkommen auch mit der Region Europa korreliert werden.  
  
     Das Naïve Bayes-Modell unterstützt keine Drilldowns. Wenn Sie jedoch den Fällen, die dieser Ergebnisgruppe zugeordnet sind, auf den Grund gehen möchten, können Sie eine Abfrage ausführen. Informationen zu Abfragen für diesen Modelltyp finden Sie unter [Beispiele für Naive Bayes-Modell Abfragen](data-mining/naive-bayes-model-query-examples.md).  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
