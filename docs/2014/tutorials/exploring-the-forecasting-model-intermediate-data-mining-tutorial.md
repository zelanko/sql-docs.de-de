---
title: Erkunden des Vorhersagemodells (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a00f409-050f-4b92-9763-ba31a6aa3052
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 607f300fbf2138796bb02c66c62386fcc93e6a45
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62992264"
---
# <a name="exploring-the-forecasting-model-intermediate-data-mining-tutorial"></a>Prüfen des Planungserstellungsmodells (Data Mining-Lernprogramm für Fortgeschrittene)
  Nachdem Sie nun das Mining Modell für die Vorhersage erstellt haben, können Sie die Ergebnisse untersuchen, indem Sie die Registerkarte **Mining Modell-Viewer** des Data Mining-Designers verwenden. Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Viewer enthält zwei Registerkarten: **Diagramme** und **Modell**.  
  
 Zudem können Sie den Microsoft Generic Tree Viewer mit allen Modellen verwenden. Jede Sicht zeigt ein leicht unterschiedliches Bild der Informationen im Zeitreihenmodell.  
  
-   [Registerkarte Diagramme](#bkmk_Charts)  
  
-   [Registerkarte Modell](#bkmk_Model)  
  
-   [Microsoft Generic Content Viewer](#bkmk_Content)  
  
##  <a name="charts-tab"></a><a name="bkmk_Charts"></a>Registerkarte Diagramme  
 Die Registerkarte **Diagramme** des [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Viewers zeigt Ihnen grafisch alle einzelnen Reihen, einschließlich historischer Daten und Vorhersagen. Jede Zeile im Zeitreihendiagramm stellt eine eindeutige Kombination von Produkt, Bereich und vorhersagbarem Attribut dar.  
  
 In der Legende auf der rechten Seite des Viewers sind die verfügbren Zeitreihen auf Grundlage der Auswahl in der Dropdownliste aufgeführt. Aktivieren und deaktivieren Sie die Kontrollkästchen in der Legende, um zu steuern, welche Zeitreihe im Diagramm angezeigt wird.  
  
 Sie können hier zudem die Anzeigeoptionen ändern, z. B. die für eine bestimmte Zeitreihe verwendete Farbe oder ob Werte an Punkten im Diagramm angezeigt werden.  
  
#### <a name="to-select-a-time-series"></a>So wählen Sie eine Zeitreihe aus  
  
1.  Klicken Sie auf die Registerkarte **Diagramme** der Registerkarte **Mining Modell-Viewer** , wenn Sie nicht sichtbar ist.  
  
2.  Klicken Sie auf die Dropdownliste rechts neben der Diagrammansicht, und aktivieren Sie alle Kontrollkästchen. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Das Diagramm sollte nun 24 Zeilen für die verschiedenen Reihen enthalten.  
  
3.  Deaktivieren Sie die Kontrollkästchen rechts vom Diagramm, um die Zeilen für alle auf dem Betrag basierenden Reihen vorübergehend auszublenden.  
  
     Deaktivieren Sie nun die Kontrollkästchen für die Fahrräder R750 und R250.  
  
     Das Diagramm enthält anschließend nur die folgenden sechs Reihenzeilen, sodass Sie die Trends für die Fahrräder M200 und T1000 besser vergleichen können.  
  
    -   **M200 Europe: Quantity**  
  
    -   **M200 North America: Quantity**  
  
    -   **M200 Pacific: Quantity**  
  
    -   **T1000 Europe: Quantity**  
  
    -   **T1000 North America: Quantity**  
  
    -   **T1000 Pacific: Quantity**  
  
 ![Reihenvorhersagen für Mengen M200 und T1000](../../2014/tutorials/media/6series-defaultforecasting.gif "Reihenvorhersagen für Mengen M200 und T1000")  
  
 Das Diagramm, das in diesem Viewer angezeigt wird, schließt sowohl Vergangenheitsdaten als auch vorhergesagte Daten ein. Die vorhergesagten Daten sind schattiert dargestellt, um sie von den Vergangenheitsdaten abzugrenzen. Um den Vergleich unterschiedlicher Reihen zu erleichtern, können Sie außerdem die jeder Zeile im Diagramm zugeordneten Farben ändern. Weitere Informationen finden Sie unter [Ändern der im Data Mining-Viewer verwendeten Farben](../../2014/analysis-services/data-mining/change-the-colors-used-in-the-data-mining-viewer.md).  
  
 Den Trendlinien können Sie entnehmen, dass der Gesamtumsatz für alle Regionen zunimmt, wobei alle 12 Monate im Dezember Spitzenwerte verzeichnet werden. Im Diagramm können Sie auch sehen, dass die Daten für das T1000-Fahrrad viel später beginnen als die Daten für die andere Produktreihe. Grund hierfür ist die Tatsache, dass es sich um ein neueres Produkt handelt. Da diese Reihe eine deutlich geringere Datengrundlage hat, sind die Vorhersagen möglicherweise nicht so genau.  
  
 Standardmäßig werden fünf Vorhersageschritte jede Zeitreihe als gepunktete Linien angezeigt. Sie können diesen Wert jedoch ändern und mehr oder weniger Vorhersagen anzeigen. Sie können die Standardabweichung für die Vorhersagen zudem grafisch darstellen, indem Sie dem Diagramm Fehlerindikatoren hinzufügen.  
  
#### <a name="to-change-prediction-and-display-options-in-the-chart-view"></a>So ändern Sie die Vorhersage- und Anzeigeoptionen in der Diagrammansicht  
  
1.  Versuchen Sie, den Wert für **Vorhersage Schritte** schrittweise zu ändern, indem Sie ihn von **5** auf **10**und dann zurück auf **6**erhöhen.  
  
     Wenn die Vergangenheitsdaten große Schwankungen haben, werden die Schwankungen meist wiederholt oder sogar vergrößert, wenn Sie die Anzahl der Vorhersagen erhöhen. Vermutlich müssen Sie an diesem Punkt ein wenig nachforschen, um die Ursache der großen Erhöhung in den Vergangenheitsdaten zu verstehen. Anschließend entscheiden Sie, ob Sie diese Ergebnisse akzeptieren, sich in den Quelldaten um Korrektur bemühen oder im Modell eiine gewisse Glättung vornehmen möchten.  
  
2.  Aktivieren Sie das Kontrollkästchen **Abweichungen anzeigen** .  
  
     Diese Option zeigt den geschätzten Fehler für jeden vorhergesagten Wert an.  
  
3.  Beachten Sie die Skala der X-Achse. Die Änderungen an Vergangenheits- und vorhergesagten Daten werden immer als Prozentsatz ausgedrückt; die Istwerte werden jedoch automatisch so angepasst, dass alle Werte in das Diagramm passen. Daher dürfen Sie beim Vergleichen von Modellen nicht nur die grafische Darstellung berücksichtigen. Um den genauen Wert oder den Prozentsatz und den Wert für Vorhersagen zu erhalten, halten Sie den Mauszeiger auf die gepunktete Linie oder die gepunkteten Linien, oder klicken Sie auf die Zeilen, um die Werte in der **Mining Legende**anzuzeigen.  
  
     **Tipp**: Wenn die **Mining Legende** nicht sichtbar ist, wechseln Sie zur **Modell** Ansicht, klicken Sie mit der rechten Maustaste auf einen beliebigen Knoten, und wählen Sie **Legende anzeigen**aus.  
  
 Nach dem Durchsehen dieser Trends bleiben Ihnen Bedenken wegen der geringen Datenbasis für menache Reihen. Sie fragen sich, ob vielleicht verlässlichere Vorhersagen möglich wären, wenn Sie Umsatzdurchschnitte nach Modell oder auch nach Region ermittelten. Diesem Ansatz werden Sie in einer späteren Lektion in diesem Lernprogramm nachgehen.  
  
 [Zurück zum Anfang](#bkmk_Charts)  
  
##  <a name="model-tab"></a><a name="bkmk_Model"></a>Registerkarte Modell  
 Auf **Model** der Registerkarte Modell [!INCLUDE[msCoName](../includes/msconame-md.md)] des Time Series-Viewers im Data Mining-Designer können Sie das Vorhersagemodell in Form eines Struktur Diagramms anzeigen.  
  
 Beachten Sie zuerst, dass das von Ihnen erstellte Modell eigentlich 24 verschiedene Strukturen enthält, da Ihre Daten zwei verschiedene Messwerte (Menge und Menge) für die Verkäufe mehrerer Produktlinien (T1000 usw.) in drei verschiedenen Bereichen (Europa, Nordamerika und Pazifik) beschreiben. Dabei stellt jede Struktur ein Modell der Verkaufsmuster für eine andere Kombination von Bereich, Produkt und vorhersagbarem Attribut dar.  
  
 Sie können auswählen, welche Kombination aus Product Line, Region und Sales Metric Sie anzeigen möchten, indem Sie eine Reihe aus **der Dropdown** Liste Struktur auf der Registerkarte **Modell** auswählen.  
  
 Welche Einblicke gibt Ihnen also eine Anzeige des Modells als Struktur? Als Beispiel vergleichen wir zwei Modelle, eine mit mehreren Ebenen in der Struktur und eine mit einem einzelnen Knoten.  
  
-   Wenn ein Strukturdiagramm einen einzelnen Knoten enthält, bedeutet dies, dass der im Modell gefundene Trend im Zeitverlauf überwiegend homogen ist. Mit diesem einzelnen Knoten mit der Bezeichnung **alle**können Sie die Formel anzeigen, mit der die Beziehung zwischen den Eingabevariablen und dem Ergebnis beschrieben wird.  
  
-   Wenn ein Strukturdiagramm für eine Zeitreihe mehrere Verzweigungen hat, bedeutet dies, dass die erkannte Zeitreihe zu komplex für eine Darstellung als einzelne Gleichung ist. Stattdessen kann das Strukturdiagramm mehrere Verzweigungen enthalten, wobei jede Verzweigung mit den Bedingungen beschriftet ist, durch die die Struktur *geteilt*wurde. Wenn sich die Struktur teilt, stellt jede Verzweigung ein Zeitsegment dar, innerhalb dessen der Trend als einzelne Gleichung beschrieben werden kann.  
  
     Wenn Sie sich z. b. das Diagramm Diagramm ansehen und einen plötzlichen Anstieg des Vertriebs Volumens sehen, der in einem Jahr und in einem Jahresende beginnt, können Sie zur **Modell** Ansicht wechseln, um das genaue Datum anzuzeigen, an dem sich der Trend geändert hat. Die Verzweigungen in der Struktur, die "vor September" und "nach September" darstellen, enthalten unterschiedliche Formeln: eine Formel, in der die Verkaufstrends nach dem Teilen mathematisch beschrieben werden, und eine weitere Formel, die die Umsatz Trends für September bis zum Jahresende beschreibt.  
  
#### <a name="to-explore-the-decision-tree-for-a-time-series-model"></a>So untersuchen Sie die Entscheidungsstruktur für ein Zeitreihenmodell  
  
1.  Wählen Sie in **der Liste Struktur** auf der Registerkarte **Modell** des Viewers die Reihe **T1000 Europe: Amount** aus.  
  
     Klicken Sie auf den Knoten mit der Bezeichnung **alle**.  
  
     Bei einem Knoten **alle** enthält die QuickInfo, die angezeigt wird, z. b. die Anzahl der Fälle in der gesamten Reihe und Zeitreihen Gleichungen, die von der Analyse der Daten abgeleitet werden.  
  
2.  Wenn die **Mining Legende** nicht sichtbar ist, klicken Sie mit der rechten Maustaste auf den Knoten, und wählen Sie **Legende anzeigen**aus.  
  
     Die **Mining Legende** bietet viele Informationen, die in der QuickInfo angezeigt werden. Wenn eine Ihrer unabhängigen Variablen diskret ist, sehen Sie auch ein Histogramm, das die Verteilung der Variablen im Knoten anzeigt.  
  
3.  Wählen Sie jetzt eine andere Zeitreihe zur Anzeige aus. Wählen Sie in der Liste Struktur auf der Registerkarte **Modell** des **Viewers die Reihe** **M200 Nordamerika: Amount** aus.  
  
     Das Strukturdiagramm enthält jetzt einen Knoten " **alle** " und zwei untergeordnete Knoten. Den Beschriftungen untergeordneten Knoten können Sie entnehmen, an welchem Punkt die Trendlinie sich geändert hat.  
  
     Für jeden untergeordneten Knoten enthält die Beschreibung in der **Mining Legende** auch die Anzahl der Fälle in jeder Verzweigung der Struktur.  
  
 Die folgende Liste beschreibt einige zusätzliche Funktionen des Struktur-Viewers:  
  
-   Sie können die im Diagramm dargestellte Variable mit dem **Background** -Steuerelement ändern. Standardmäßig enthalten Knoten, die dunkler sind, mehr Fälle, da der Wert von **Background** auf **Population**festgelegt ist. Wenn Sie sehen möchten, wie viele Fälle in einem Knoten vorhanden sind, halten Sie den Mauszeiger auf einen Knoten, zeigen Sie die angezeigte QuickInfo an, oder klicken Sie auf den Knoten, und zeigen Sie die Zahlen im Fenster **Knoten Legende** an.  
  
-   In der QuickInfo oder durch Klicken auf den Knoten kann zudem die Regressionsformel für den Knoten angezeigt werden. Wenn Sie ein gemischtes Modell erstellt haben, sehen Sie zwei Formeln, eine für ARTXP (in den Blattknoten) und eine für ARIMA (im Stammknoten der Struktur).  
  
-   Die kleinen Rauten werden in Knoten verwendet, die fortlaufende Nummern darstellen. Der Attributbreich wird in der Leiste angezeigt, auf der sich die Raute befindet. Die Raute befindet sich am Mittelwert des Knotens. Die Breite der Raute gibt die Varianz des Attributs an diesem Knoten an.  
  
 [Zurück zum Anfang](#bkmk_Charts)  
  
##  <a name="optional-generic-content-tree-viewer"></a><a name="bkmk_Content"></a>Optionale Generischer Inhaltsstruktur-Viewer  
 Zusätzlich zum benutzerdefinierten Viewer für Zeitreihen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] stellt den **microsoftgeneric Content Tree Viewer** für die Verwendung mit allen Data Mining Modellen bereit. Dieser Viewer bietet einige Vorteile:  
  
-   **Microsoft Time Series-Viewer**: in dieser Ansicht werden die Ergebnisse der beiden Algorithmen zusammengeführt. Obwohl Sie jede Reihe getrennt anzeigen können, können Sie nicht bestimmen, wie die Ergebnisse jedes Algorithmus kombiniert wurden. Zudem zeigen die QuickInfos und die Mininglegende in dieser Sicht nur die wichtigsten Statistiken an.  
  
-   **Generic Content Tree Viewer**: ermöglicht Ihnen das Durchsuchen und Anzeigen aller Datenreihen, die im Modell gleichzeitig verwendet wurden. Wenn Sie ein gemischtes Modell erstellt haben, werden die ARIMA-und ARTxp-Strukturen im selben Diagramm angezeigt.  
  
     Sie können mit diesem Viewer alle Statistiken aus beiden Algorithmen sowie die Verteilungen der Werte abrufen.  
  
     Empfohlen für sachkundige Benutzer von Data Mining, die mehr über ARIMA- und ARTXP-Analysen erfahren möchten.  
  
#### <a name="to-view-details-for-a-particular-data-series-in-the-generic-content-viewer"></a>So zeigen Sie Details für eine bestimmte Datenreihe im Generic Content Tree Viewer an  
  
1.  Wählen Sie auf der Registerkarte **Mining Modell-Viewer** in der Dropdown Liste **Viewer** die Option **Microsoft Generic Content Tree Viewer** aus.  
  
2.  Klicken Sie im Bereich **Knoten Beschriftung** auf den obersten Knoten (alle).  
  
3.  Sehen Sie sich im Bereich **Knoten Details** den Wert für ATTRIBUTE_NAME an.  
  
     Dieser Wert zeigt an, welche Reihe oder Kombination von Produkt und Region in diesem Knoten enthalten ist. Im AdventureWorks-Beispiel beinhaltet der oberste Knoten die Reihe M200 Europe.  
  
4.  Suchen Sie im Bereich **Knoten Beschriftung** den ersten Knoten, der über untergeordnete Knoten verfügt.  
  
     Wenn ein Reihen Knoten über untergeordnete Elemente verfügt, verfügt die Strukturansicht, die auf der Registerkarte **Modell** im Microsoft Time Series-Viewer angezeigt wird, auch über eine Verzweigungs Struktur.  
  
5.  Erweitern Sie den Knoten, und klicken Sie auf einen der untergeordneten Knoten.  
  
     Die Spalte NODE_DESCRIPTION des Schemas enthält die Bedingung, die zur Teilung der Struktur führte.  
  
6.  Klicken Sie im Bereich **Knoten Beschriftung** auf den obersten ARIMA-Knoten, und erweitern Sie den Knoten, bis alle untergeordneten Knoten sichtbar sind.  
  
7.  Sehen Sie sich im Bereich **Knoten Details** den Wert für ATTRIBUTE_NAME an.  
  
     Dieser Wert sagt Ihnen, welche Zeitreihe in diesem Knoten enthalten ist. Der oberste Knoten im Abschnitt ARIMA sollte mit dem obersten Knoten im Abschnitt (Alle) übereinstimmen. Im AdventureWorks-Beispiel enthält dieser Knoten die ARIMA-Analyse für die Reihe M200 Europe.  
  
 Weitere Informationen finden Sie unter [Mingingmodellinhalt von Zeitreihenmodellen &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md).  
  
 [Zurück zum Anfang](#bkmk_Charts)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Erstellen von Zeitreihen Vorhersagen &#40;Data Mining-Tutorial für fortgeschrittene&#41;](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abfrage Beispiele für Zeitreihen Modelle](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
