---
title: Untersuchen des Callcentermodells (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9095212c-9068-4dd8-85ce-17a467adeabb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a6aa4074aa04af86e478b57b1870fd0dd855bea8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63315079"
---
# <a name="exploring-the-call-center-model-intermediate-data-mining-tutorial"></a>Prüfen des Callcentermodells (Data Mining-Lernprogramm für Fortgeschrittene)
  Nachdem Sie nun das explorative Modell erstellt haben, können Sie es verwenden, um die Daten genauer zu untersuchen. Verwenden Sie dazu die folgenden Tools, die in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] bereitgestellt werden.  
  
-   [Microsoft-Viewer für neuronale Netzwerke](#bkmk_NNviewer) **:** dieser Viewer ist im Data Mining-Designer auf der Registerkarte **Mining Modell-Viewer** verfügbar und soll Ihnen helfen, mit Interaktionen in den Daten zu experimentieren.  
  
-   [Microsoft Generic Content Tree Viewer](#bkmk_genviewer) **:** dieser Standard-Viewer stellt ausführliche Details zu den Mustern und Statistiken bereit, die vom Algorithmus beim Generieren des Modells erkannt wurden.  
  
##  <a name="microsoft-neural-network-viewer"></a><a name="bkmk_NNviewer"></a>Microsoft-Viewer für neuronale Netzwerke  
 Der Viewer enthält drei Bereiche: **Eingabe**, **Ausgabe**und **Variablen**.  
  
 Mithilfe des **Ausgabe** Bereichs können Sie unterschiedliche Werte für das vorhersagbare Attribut oder die abhängige Variable auswählen. Wenn das Modell mehrere vorhersagbare Attribute enthält, können Sie das Attribut aus der Liste **Ausgabe Attribut** auswählen.  
  
 Der Bereich **Variablen** vergleicht die beiden Ergebnisse, die Sie bei der Bereitstellung von Attributen oder Variablen ausgewählt haben. Die farbigen Leisten stellen visuell dar, wie stark sich die Variable auf die Zielergebnisse auswirkt. Sie können auch Liftergebnisse für die Variablen anzeigen. Ein Liftergebnis wird abhängig vom verwendeten Miningmodelltyp unterschiedlich berechnet, gibt jedoch i. d. R. Aufschluss über die Verbesserung im Modell, die beim Verwenden dieses Attributs für die Vorhersage erreicht wird.  
  
 Im **Eingabe** Bereich können Sie dem Modell Einflussfaktoren hinzufügen, um verschiedene was-wäre-wenn-Szenarios auszuprobieren.  
  
### <a name="using-the-output-pane"></a>Verwenden des Ausgabebereichs  
 In diesem Modell soll zuerst der Einfluss verschiedener Faktoren auf die Dienstqualität dargestellt werden. Zu diesem Zweck können Sie die Dienst Qualität in der Liste der Ausgabe Attribute auswählen und anschließend verschiedene Dienst Ebenen vergleichen, indem Sie Bereiche in den Dropdown Listen für **Wert 1** und **Wert 2**auswählen.  
  
##### <a name="to-compare-lowest-and-highest-service-grades"></a>So vergleichen Sie die niedrigste und die höchste Dienstqualität  
  
1.  Wählen Sie für **Wert 1**den Bereich mit den niedrigsten Werten aus. Zum Beispiel stellt der Bereich 0-0-0,7 die niedrigsten Abbruchraten dar und damit die bestmögliche Dienstqualität.  
  
    > [!NOTE]  
    >  Die genauen Werte in diesem Bereich variieren ggf. abhängig davon, wie Sie das Modell konfiguriert haben.  
  
2.  Wählen Sie für **Wert 2**den Bereich mit den höchsten Werten aus. Beispielsweise steht der Bereich mit dem Wert >= 0,12 für die höchsten Abbruchraten und somit für die schlechteste Dienst Qualität. Der Wert bedeutet, dass 12% der eingehenden Kundenanrufe während dieser Schicht nicht durchgestellt werden konnten und der Kunde wieder aufgelegt hat.  
  
     Der Inhalt des Bereichs **Variablen** wird aktualisiert, um Attribute zu vergleichen, die zu den Ergebnis Werten beitragen. Die linke Spalte zeigt die Attribute an, die der besten Dienstqualität zugeordnet sind, und die rechte Spalte die Attribute für die schlechteste Dienstqualität.  
  
### <a name="using-the-variables-pane"></a>Verwenden des Variablenbereichs  
 In diesem Modell `Average Time Per Issue` ist es ein wichtiger Faktor. Diese Variable gibt die durchschnittliche Zeit an, nach der ein Aufruf beantwortet wird, unabhängig vom Anruftyp.  
  
##### <a name="to-view-and-copy-probability-and-lift-scores-for-an-attribute"></a>So können Sie Wahrscheinlichkeits- und Liftergebnisse für ein Attribut anzeigen und kopieren  
  
1.  Bewegen Sie den Mauszeiger im Bereich **Variablen** über die farbige Leiste in der ersten Zeile.  
  
     Diese farbige Leiste zeigt, wie stark `Average Time Per Issue` zur Dienst Qualität beiträgt. Die QuickInfo zeigt das Gesamtergebnis, die Wahrscheinlichkeiten und die Liftergebnisse für jede Kombination einer Variablen mit einem Zielergebnis an.  
  
2.  Klicken Sie im Bereich **Variablen** mit der rechten Maustaste auf eine farbige Leiste, und wählen Sie **Kopieren**aus.  
  
3.  Klicken Sie in einem Excel-Arbeitsblatt mit der rechten Maustaste auf eine Zelle, und wählen Sie **Einfügen**aus.  
  
     Der Bericht wird als HTML-Tabelle eingefügt und zeigt nur die Ergebnisse für jede Leiste an.  
  
4.  Klicken Sie in einem anderen Excel-Arbeitsblatt mit der rechten Maustaste auf eine beliebige Zelle, und wählen Sie **spezielle einfügen**  
  
     Der Bericht wird im Textformat eingefügt und enthält die verwandten Statistiken, die im nächsten Abschnitt beschrieben werden.  
  
### <a name="using-the-input-pane"></a>Verwenden des Eingabebereichs  
 Angenommen, Sie interessieren sich für die Auswirkungen eines bestimmten Faktors, z. B. für die Schicht oder die Anzahl der Telefonisten. Sie können eine bestimmte Variable mithilfe des **Eingabe** Bereichs auswählen. der Bereich **Variablen** wird automatisch aktualisiert, um die beiden zuvor ausgewählten Gruppen mit der angegebenen Variablen zu vergleichen.  
  
##### <a name="to-review-the-effect-on-service-grade-by-changing-input-attributes"></a>So überprüfen Sie die Auswirkungen auf die Dienstqualität beim Ändern von Eingabeattributen  
  
1.  Wählen Sie im Bereich **Eingabe** für **Attribut**die Option Shift aus.  
  
2.  Wählen Sie für **Wert**die Option **am**aus.  
  
     Der Bereich **Variablen** wird aktualisiert, um die Auswirkungen auf das Modell anzuzeigen, wenn die UMSCHALTTASTE **am**ist. Alle anderen Auswahlen bleiben unverändert, und Sie vergleichen immer noch die niedrigsten und höchsten Dienst Qualitäten.  
  
3.  Wählen Sie für **Wert**die Option **PM1**aus.  
  
     Der Bereich **Variablen** wird aktualisiert, um die Auswirkungen auf das Modell anzuzeigen, wenn sich die UMSCHALTTASTE ändert.  
  
4.  Klicken Sie im Bereich **Eingabe** unter **Attribut**auf die nächste leere Zeile, und wählen Sie dann Anrufe aus. Wählen Sie für **Wert**den Bereich aus, der die größte Anzahl von Aufrufen angibt.  
  
     Der Liste wird eine neue Eingabebedingung hinzugefügt. Der Bereich **Variablen** wird aktualisiert, um die Auswirkungen auf das Modell für eine bestimmte Schicht anzuzeigen, wenn das aufrufvolume am höchsten ist.  
  
5.  Ändern Sie weiter die Werte für Schicht und Anrufe, um ein genaues Bild der Wechselwirkungen zwischen den Werten für Schicht, Anrufaufkommen und Dienstqualität zu bekommen.  
  
    > [!NOTE]  
    >  Wenn Sie den **Eingabe** Bereich löschen möchten, sodass Sie unterschiedliche Attribute verwenden können, klicken Sie auf **Viewer-Inhalt aktualisieren**.  
  
### <a name="interpreting-the-statistics-provided-in-the-viewer"></a>Interpretieren der im Viewer bereitgestellten Statistiken  
 Längere Wartezeiten sind ein wesentlicher Vorhersagefaktor für eine hohe Abbruchrate und bedeuten eine schlechte Dienstqualität. Diese Schlussfolgerung scheint zunächst offensichtlich. Das Miningmodell stellt Ihnen jedoch einige zusätzliche statistische Daten bereit, mit denen Sie diese Trends umfassender interpretieren können.  
  
-   **Score**: Wert, der die Gesamt Wichtigkeit dieser Variablen für die Unterscheidung Zwischenergebnissen angibt. Je höher das Ergebnis, desto stärker wirkt sich die Variable auf das Ergebnis aus.  
  
-   **Wahrscheinlichkeit von Wert 1**: Prozentsatz, der die Wahrscheinlichkeit dieses Werts für dieses Ergebnis darstellt.  
  
-   **Wahrscheinlichkeit von Wert 2**: Prozentsatz, der die Wahrscheinlichkeit dieses Werts für dieses Ergebnis darstellt.  
  
-   **Lift für Wert 1** und **Lift für Wert 2**: Bewertungen, die die Auswirkung der Verwendung dieser speziellen Variablen auf die Vorhersage von Wert 1 und Wert 2 darstellen. Je höher das Ergebnis, desto besser sind die Ergebnisse, die mit dieser Variablen ermittelt werden können.  
  
 Die folgende Tabelle enthält einige Beispielwerte für die wichtigsten Einflussfaktoren. Beispielsweise ist die **Wahrscheinlichkeit von Wert 1** 60,6%, und die **Wahrscheinlichkeit von Wert 2** beträgt 8,30%. Dies bedeutet, dass bei einer durchschnittlichen Zeit pro Problem im Bereich von 44-70 Minuten 60,6% der Fälle in der Schicht mit den höchsten Dienst Qualitäten (Wert 1) und 8,30% der Fälle in der Schicht mit den schlechteren Dienst Qualitäten (Wert 2) waren.  
  
 Aus diesen Informationen lassen sich mehrere Schlussfolgerungen ableiten. Kürzere Antwortzeiten (der Bereich von 44-70) wirken sich sehr stark auf eine bessere Dienstqualität (der Bereich 0,00-0,07) aus. Das Ergebnis (92,35) besagt, dass diese Variable sehr wichtig ist.  
  
 Wenn Sie jedoch die Liste der Faktoren genauer überprüfen, finden Sie einige andere Faktoren, die weniger deutliche Auswirkungen haben und schwieriger zu interpretieren sind. Zum Beispiel scheint die Schicht die Dienstqualität zu beeinflussen, aber das Liftergebnis und die relativen Wahrscheinlichkeiten geben an, dass die Schicht kein Hauptfaktor ist.  
  
|attribute|Wert|Begünstigt \< 0,07|Begünstigt >= 0,12|  
|---------------|-----------|--------------------|----------------------|  
|Average Time Per Issue|89,087-120,000||Ergebnis: 100<br /><br /> Wahrscheinlichkeit von value1:4,45%<br /><br /> Wahrscheinlichkeit von Value2:51,94%<br /><br /> Lift für value1:0,19<br /><br /> Lift für Value2:1,94|  
|Average Time Per Issue|44,000-70,597|Ergebnis: 92,35<br /><br /> Wahrscheinlichkeit von Wert 1: 60,06 %<br /><br /> Wahrscheinlichkeit von Wert 2: 8,30 %<br /><br /> Lift für Wert 1: 2,61<br /><br /> Lift für Wert 2: 0,31||  
  
 [Zurück zum Anfang](#bkmk_NNviewer)  
  
##  <a name="microsoft-generic-content-tree-viewer"></a><a name="bkmk_genviewer"></a>Microsoft Generic Content Tree-Viewer  
 Mit diesem Viewer können Sie die vom Algorithmus bei der Modellverarbeitung erstellten Informationen noch ausführlicher untersuchen. Der **microsoftgeneric Content Tree Viewer** stellt das Mining Modell als eine Reihe von Knoten dar, in denen jeder Knoten gelernte Informationen über die Trainingsdaten repräsentiert. Dieser Viewer kann mit allen Modellen verwendet werden, die Inhalte der Knoten variieren jedoch abhängig vom Modelltyp.  
  
 Bei neuronalen Netzwerkmodellen oder logistischen Regressionsmodellen kann z. B. der `marginal statistics node` sehr nützlich sein. Dieser Knoten enthält abgeleitete Statistiken über die Werteverteilung in den Daten. Diese Informationen können nützlich sein, um ohne die Ausführung vieler T-SQL-Abfragen schnell eine Zusammenfassung der Daten zu erhalten. Das Diagramm mit Klassifizierungswerten im vorherigen Thema wurde aus dem Knoten für Randstatistiken abgeleitet.  
  
#### <a name="to-obtain-a-summary-of-data-values-from-the-mining-model"></a>So rufen Sie eine Zusammenfassung der Datenwerte aus dem Miningmodell ab  
  
1.  Wählen Sie \<im Data Mining-Designer auf der Registerkarte **Mining Modell-Viewer** die Option Mining Modellname> aus.  
  
2.  Wählen Sie in der Liste **Viewer** den Bereich **Microsoft Generic Content Tree Viewer**aus.  
  
     Die Ansicht des Miningmodells wird aktualisiert und zeigt im linken Bereich eine Knotenhierarchie und im rechten Bereich eine HTML-Tabelle an.  
  
3.  Klicken Sie im Bereich **Knoten Beschriftung** auf den Knoten mit dem Namen 10000000000000000.  
  
     Der oberste Knoten in jedem Modell ist immer der Modellstammknoten. In einem neuronalen Netzwerk oder logistischen Regressionsmodell ist der Knoten direkt unter diesem der Knoten für Randstatistiken.  
  
4.  Scrollen Sie im Bereich " **Knoten Details** " nach unten, bis Sie die Zeile NODE_DISTRIBUTION finden.  
  
5.  Führen Sie einen Bildlauf nach unten bis zur Tabelle NODE_DISTRIBUTION durch, um die Werteverteilung anzuzeigen, die vom Neural Network-Algorithmus berechnet wurde.  
  
 Wenn Sie diese Daten in einem Bericht verwenden möchten, können Sie die Informationen für bestimmte Zeilen auswählen und anschließend kopieren, oder Sie können mit der folgenden DMX-Abfrage (Data Mining Extensions) den gesamten Inhalt des Knotens extrahieren.  
  
```  
SELECT *   
FROM [Call Center EQ4].CONTENT  
WHERE NODE_NAME = '10000000000000000'  
```  
  
 Sie können auch die Knotenhierarchie und die Details in der Tabelle NODE_DISTRIBUTION verwenden, um einzelne Pfade im neuronalen Netzwerk zu durchlaufen und Statistiken in der verborgenen Ebene anzuzeigen. Weitere Informationen finden Sie unter [Beispiele für neuronale Netzwerkmodell Abfragen](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md).  
  
 [Zurück zum Anfang](#bkmk_NNviewer)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Hinzufügen eines logistischen Regressionsmodells zur Callcenterstruktur &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mining Modell Inhalt von neuronalen Netzwerkmodellen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)   
 [Beispiele für neuronale Netzwerkmodell Abfragen](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)   
 [Technische Referenz für den Microsoft Neural Network-Algorithmus](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)   
 [Ändern der Diskretisierung von Spalten in Miningmodellen](../../2014/analysis-services/data-mining/change-the-discretization-of-a-column-in-a-mining-model.md)  
  
  
