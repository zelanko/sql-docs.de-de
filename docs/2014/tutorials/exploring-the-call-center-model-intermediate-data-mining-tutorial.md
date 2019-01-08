---
title: Untersuchen des Callcentermodells (Datamining-Lernprogramm für fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 9095212c-9068-4dd8-85ce-17a467adeabb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e6b1995ad715ea529da548f06e0643be076abe96
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52518902"
---
# <a name="exploring-the-call-center-model-intermediate-data-mining-tutorial"></a>Prüfen des Callcentermodells (Data Mining-Lernprogramm für Fortgeschrittene)
  Nachdem Sie nun das explorative Modell erstellt haben, können Sie es verwenden, um die Daten genauer zu untersuchen. Verwenden Sie dazu die folgenden Tools, die in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] bereitgestellt werden.  
  
-   [Microsoft-Viewer für neuronale Netzwerke](#bkmk_NNviewer) **:** Dieser Viewer steht in der **Miningmodell-Viewer** Data Mining-Designer auf der Registerkarte und soll helfen, Ihnen das Experimentieren mit Interaktionen in den Daten.  
  
-   [Microsoft Generic Content Tree-Viewer](#bkmk_genviewer) **:** Dieser Standardviewer stellt ausführliche Details zu den Mustern und Statistiken, die vom Algorithmus erkannt werden, wenn es sich um das Modell generiert.  
  
##  <a name="bkmk_NNviewer"></a> Microsoft-Viewer für neuronale Netzwerke  
 Der Viewer verfügt über drei Bereiche – **Eingabe**, **Ausgabe**, und **Variablen**.  
  
 Mithilfe der **Ausgabe** Bereich können Sie unterschiedliche Werte für das vorhersagbare Attribut oder die abhängige Variable auswählen. Wenn das Modell mehrere vorhersagbare Attribute enthält, können Sie auswählen, dass das Attribut aus der **Ausgabeattribut** Liste.  
  
 Die **Variablen** Bereich vergleicht die zwei Ergebnisse, die Sie in Bezug auf die angegebenen Attribute oder Variablen ausgewählt haben. Die farbigen Leisten stellen visuell dar, wie stark sich die Variable auf die Zielergebnisse auswirkt. Sie können auch Liftergebnisse für die Variablen anzeigen. Ein Liftergebnis wird abhängig vom verwendeten Miningmodelltyp unterschiedlich berechnet, gibt jedoch i. d. R. Aufschluss über die Verbesserung im Modell, die beim Verwenden dieses Attributs für die Vorhersage erreicht wird.  
  
 Die **Eingabe** Bereich können Sie das Modell in verschiedenen Szenarien testen Einflussfaktoren hinzufügen.  
  
### <a name="using-the-output-pane"></a>Verwenden des Ausgabebereichs  
 In diesem Modell soll zuerst der Einfluss verschiedener Faktoren auf die Dienstqualität dargestellt werden. Zu diesem Zweck können Sie Service Grade aus der Liste der Ausgabeattribute auswählen und anschließend verschiedene Dienstebenen vergleichen, durch Auswählen von Bereichen aus den Dropdownlisten für **Wert 1** und **Wert 2**.  
  
##### <a name="to-compare-lowest-and-highest-service-grades"></a>So vergleichen Sie die niedrigste und die höchste Dienstqualität  
  
1.  Für **Wert 1**, wählen Sie den Bereich mit den niedrigsten Werten. Zum Beispiel stellt der Bereich 0-0-0,7 die niedrigsten Abbruchraten dar und damit die bestmögliche Dienstqualität.  
  
    > [!NOTE]  
    >  Die genauen Werte in diesem Bereich variieren ggf. abhängig davon, wie Sie das Modell konfiguriert haben.  
  
2.  Für **Wert 2**, wählen Sie den Bereich mit den höchsten Werten. So stellt beispielsweise der Bereich mit dem Wert >= 0,12 die höchsten Abbruchraten dar und damit die schlechteste Dienstqualität. Der Wert bedeutet, dass 12% der eingehenden Kundenanrufe während dieser Schicht nicht durchgestellt werden konnten und der Kunde wieder aufgelegt hat.  
  
     Den Inhalt der **Variablen** Bereich werden aktualisiert, um Attribute zu vergleichen, die auf die Ergebniswerte beitragen. Die linke Spalte zeigt die Attribute an, die der besten Dienstqualität zugeordnet sind, und die rechte Spalte die Attribute für die schlechteste Dienstqualität.  
  
### <a name="using-the-variables-pane"></a>Verwenden des Variablenbereichs  
 In diesem Modell wird es angezeigt wird, `Average Time Per Issue` ist ein wichtiger Faktor. Diese Variable gibt die durchschnittliche Zeit an, nach der ein Aufruf beantwortet wird, unabhängig vom Anruftyp.  
  
##### <a name="to-view-and-copy-probability-and-lift-scores-for-an-attribute"></a>So können Sie Wahrscheinlichkeits- und Liftergebnisse für ein Attribut anzeigen und kopieren  
  
1.  In der **Variablen** Bereich, halten Sie die Maus auf die farbige Leiste in der ersten Zeile.  
  
     Diese farbige Leiste zeigt an, wie stark `Average Time Per Issue` auf die Dienstqualität beiträgt. Die QuickInfo zeigt das Gesamtergebnis, die Wahrscheinlichkeiten und die Liftergebnisse für jede Kombination einer Variablen mit einem Zielergebnis an.  
  
2.  In der **Variablen** , mit der rechten Maustaste, alle farbige Leiste, und wählen Sie im Bereich **Kopie**.  
  
3.  In einer Excel-Arbeitsblatt mit der rechten Maustaste in eine beliebige Zelle, und wählen Sie **einfügen**.  
  
     Der Bericht wird als HTML-Tabelle eingefügt und zeigt nur die Ergebnisse für jede Leiste an.  
  
4.  In einer anderen Excel-Arbeitsblatt mit der rechten Maustaste in eine beliebige Zelle, und wählen Sie **Inhalte einfügen**.  
  
     Der Bericht wird im Textformat eingefügt und enthält die verwandten Statistiken, die im nächsten Abschnitt beschrieben werden.  
  
### <a name="using-the-input-pane"></a>Verwenden des Eingabebereichs  
 Angenommen, Sie interessieren sich für die Auswirkungen eines bestimmten Faktors, z. B. für die Schicht oder die Anzahl der Telefonisten. Sie können eine bestimmte Variable auswählen, mit der **Eingabe** Bereich und die **Variablen** Bereich wird automatisch aktualisiert, um die beiden zuvor ausgewählten Gruppen basierend auf der angegebenen Variablen vergleichen.  
  
##### <a name="to-review-the-effect-on-service-grade-by-changing-input-attributes"></a>So überprüfen Sie die Auswirkungen auf die Dienstqualität beim Ändern von Eingabeattributen  
  
1.  In der **Eingabe** Bereich für **Attribut**, wählen Sie die UMSCHALTTASTE gedrückt.  
  
2.  Für **Wert**Option **Uhr**.  
  
     Die **Variablen** Bereich Updates und zeigt die Auswirkungen auf das Modell, die Schicht **Uhr**. Alle anderen Benutzerauswahlen bleiben unverändert, – Sie weiterhin die niedrigste und höchste Dienstqualität vergleichen.  
  
3.  Für **Wert**Option **"pm1"**.  
  
     Die **Variablen** Bereich Updates und zeigt die Auswirkungen auf das Modell, bei der Änderung der Schicht an.  
  
4.  In der **Eingabe** Bereich, klicken Sie auf die nächste leere Zeile unter **Attribut**, und wählen Sie die Aufrufe. Für **Wert**, wählen Sie den Bereich, der die größte Anzahl von Anrufen angibt.  
  
     Der Liste wird eine neue Eingabebedingung hinzugefügt. Die **Variablen** Bereich aktualisiert und zeigt die Auswirkungen auf das Modell für eine bestimmte Schicht das Anrufaufkommen am höchsten ist.  
  
5.  Ändern Sie weiter die Werte für Schicht und Anrufe, um ein genaues Bild der Wechselwirkungen zwischen den Werten für Schicht, Anrufaufkommen und Dienstqualität zu bekommen.  
  
    > [!NOTE]  
    >  Zum Löschen der **Eingabe** klicken im Bereich, damit Sie andere Attribute verwenden, können Sie auf **Viewerinhalt**.  
  
### <a name="interpreting-the-statistics-provided-in-the-viewer"></a>Interpretieren der im Viewer bereitgestellten Statistiken  
 Längere Wartezeiten sind ein wesentlicher Vorhersagefaktor für eine hohe Abbruchrate und bedeuten eine schlechte Dienstqualität. Diese Schlussfolgerung scheint zunächst offensichtlich. Das Miningmodell stellt Ihnen jedoch einige zusätzliche statistische Daten bereit, mit denen Sie diese Trends umfassender interpretieren können.  
  
-   **Bewertung**: Der Wert, der die Bedeutung dieser Variablen für die Unterscheidung zwischen Ergebnisse angibt. Je höher das Ergebnis, desto stärker wirkt sich die Variable auf das Ergebnis aus.  
  
-   **Wahrscheinlichkeit von Wert 1**: Der Prozentsatz, der die Wahrscheinlichkeit dieses Werts für dieses Ergebnis darstellt.  
  
-   **Wahrscheinlichkeit von Wert 2**: Der Prozentsatz, der die Wahrscheinlichkeit dieses Werts für dieses Ergebnis darstellt.  
  
-   **Lift für Wert 1** und **Lift für Wert 2**: Ergebnisse, die die Auswirkungen der Verwendung dieser bestimmten Variablen für die Vorhersage der Wert 1 und 2 angeben darstellt. Je höher das Ergebnis, desto besser sind die Ergebnisse, die mit dieser Variablen ermittelt werden können.  
  
 Die folgende Tabelle enthält einige Beispielwerte für die wichtigsten Einflussfaktoren. Z. B. die **Wahrscheinlichkeit von Wert 1** ist 60,6 % und **Wahrscheinlichkeit von Wert 2** ist 8,30 %, was bedeutet, dass wenn Average Time Per Issue im Bereich von 44-70 Minuten war, waren 60,6 % der Fälle in der Schicht mit den höchsten Dienstqualitäten (Wert 1) und 8,30 % der Fälle Waren in der Schicht mit den Dienstqualitäten (Wert 2).  
  
 Aus diesen Informationen lassen sich mehrere Schlussfolgerungen ableiten. Kürzere Antwortzeiten (der Bereich von 44-70) wirken sich sehr stark auf eine bessere Dienstqualität (der Bereich 0,00-0,07) aus. Das Ergebnis (92,35) besagt, dass diese Variable sehr wichtig ist.  
  
 Wenn Sie jedoch die Liste der Faktoren genauer überprüfen, finden Sie einige andere Faktoren, die weniger deutliche Auswirkungen haben und schwieriger zu interpretieren sind. Zum Beispiel scheint die Schicht die Dienstqualität zu beeinflussen, aber das Liftergebnis und die relativen Wahrscheinlichkeiten geben an, dass die Schicht kein Hauptfaktor ist.  
  
|Attribut|Wert|Begünstigt \< 0,07|Begünstigt >= 0,12|  
|---------------|-----------|--------------------|----------------------|  
|Average Time Per Issue|89.087-120.000||Testergebnis:  100<br /><br /> Wahrscheinlichkeit, dass Value1: 4,45 %<br /><br /> Die Wahrscheinlichkeit von Wert 2: 51.94 %<br /><br /> Lift für Value1: 0.19<br /><br /> Lift für Wert2: 1,94|  
|Average Time Per Issue|44.000-70.597|Testergebnis: 92,35<br /><br /> Wahrscheinlichkeit, dass Value1: 60,06 %<br /><br /> Die Wahrscheinlichkeit von Wert 2: 8,30 %<br /><br /> Lift für Value1: 2,61<br /><br /> Lift für Wert2: 0,31||  
  
 [Zurück zum Anfang](#bkmk_NNviewer)  
  
##  <a name="bkmk_genviewer"></a> Microsoft Generic Content Tree-Viewer  
 Mit diesem Viewer können Sie die vom Algorithmus bei der Modellverarbeitung erstellten Informationen noch ausführlicher untersuchen. Die **MicrosoftGeneric Content Tree Viewer** zeigt das Miningmodell als eine Reihe von Knoten, bei dem jeder Knoten das erlangte wissen über die Trainingsdaten repräsentiert. Dieser Viewer kann mit allen Modellen verwendet werden, die Inhalte der Knoten variieren jedoch abhängig vom Modelltyp.  
  
 Bei neuronalen Netzwerkmodellen oder logistischen Regressionsmodellen kann z. B. der `marginal statistics node` sehr nützlich sein. Dieser Knoten enthält abgeleitete Statistiken über die Werteverteilung in den Daten. Diese Informationen können nützlich sein, um ohne die Ausführung vieler T-SQL-Abfragen schnell eine Zusammenfassung der Daten zu erhalten. Das Diagramm mit Klassifizierungswerten im vorherigen Thema wurde aus dem Knoten für Randstatistiken abgeleitet.  
  
#### <a name="to-obtain-a-summary-of-data-values-from-the-mining-model"></a>So rufen Sie eine Zusammenfassung der Datenwerte aus dem Miningmodell ab  
  
1.  Im Data Mining-Designer in der **Miningmodell-Viewer** Registerkarte \<Miningmodellname >.  
  
2.  Von der **Viewer** Liste **Microsoft Generic Content Tree Viewer**.  
  
     Die Ansicht des Miningmodells wird aktualisiert und zeigt im linken Bereich eine Knotenhierarchie und im rechten Bereich eine HTML-Tabelle an.  
  
3.  In der **Knotenbeschriftung** Bereich, klicken Sie auf den Knoten mit dem Namen 10000000000000000.  
  
     Der oberste Knoten in jedem Modell ist immer der Modellstammknoten. In einem neuronalen Netzwerk oder logistischen Regressionsmodell ist der Knoten direkt unter diesem der Knoten für Randstatistiken.  
  
4.  In der **Knotendetails** Bereich einen Bildlauf nach unten, bis Sie zur Zeile NODE_DISTRIBUTION finden.  
  
5.  Führen Sie einen Bildlauf nach unten bis zur Tabelle NODE_DISTRIBUTION durch, um die Werteverteilung anzuzeigen, die vom Neural Network-Algorithmus berechnet wurde.  
  
 Wenn Sie diese Daten in einem Bericht verwenden möchten, können Sie die Informationen für bestimmte Zeilen auswählen und anschließend kopieren, oder Sie können mit der folgenden DMX-Abfrage (Data Mining Extensions) den gesamten Inhalt des Knotens extrahieren.  
  
```  
SELECT *   
FROM [Call Center EQ4].CONTENT  
WHERE NODE_NAME = '10000000000000000'  
```  
  
 Sie können auch die Knotenhierarchie und die Details in der Tabelle NODE_DISTRIBUTION verwenden, um einzelne Pfade im neuronalen Netzwerk zu durchlaufen und Statistiken in der verborgenen Ebene anzuzeigen. Weitere Informationen finden Sie unter [Abfragebeispiele neuronale Netzwerkmodelle](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md).  
  
 [Zurück zum Anfang](#bkmk_NNviewer)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Hinzufügen eines logistischen Regressionsmodells zur Call-Center-Struktur &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Miningmodellinhalt von neuronalen Netzwerkmodellen &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)   
 [Abfragebeispiele für neuronale Netzwerkmodelle](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)   
 [Technische Referenz für den Microsoft Neural Network-Algorithmus](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)   
 [Ändern der Diskretisierung von Spalten in einem Miningmodell](../../2014/analysis-services/data-mining/change-the-discretization-of-a-column-in-a-mining-model.md)  
  
  
