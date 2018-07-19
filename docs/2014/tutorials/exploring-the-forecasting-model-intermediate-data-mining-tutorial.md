---
title: Untersuchen des Forecasting-Modells (mittleres Datamining Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0a00f409-050f-4b92-9763-ba31a6aa3052
caps.latest.revision: 52
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f3e41c8060a007e52af23c0637c744e72f0d1fb4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167763"
---
# <a name="exploring-the-forecasting-model-intermediate-data-mining-tutorial"></a>Prüfen des Planungserstellungsmodells (Data Mining-Lernprogramm für Fortgeschrittene)
  Nun, dass Sie das forecasting-Miningmodell erstellt haben, können Sie die Ergebnisse überprüfen, mit der **Miningmodell-Viewer** -Registerkarte des Data Mining-Designers. Die [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Viewer enthält zwei Registerkarten: **Diagramme** und **Modell**.  
  
 Zudem können Sie den Microsoft Generic Tree Viewer mit allen Modellen verwenden. Jede Sicht zeigt ein leicht unterschiedliches Bild der Informationen im Zeitreihenmodell.  
  
-   [Registerkarte "Diagramme"](#bkmk_Charts)  
  
-   [Registerkarte "Modell"](#bkmk_Model)  
  
-   [Microsoft Generic Content Viewer](#bkmk_Content)  
  
##  <a name="bkmk_Charts"></a> Registerkarte "Diagramme"  
 Die **Diagramme** Registerkarte die [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Viewer grafisch dargestellt alle Reihen, einschließlich der Vergangenheitsdaten und Vorhersagen. Jede Zeile im Zeitreihendiagramm stellt eine eindeutige Kombination von Produkt, Bereich und vorhersagbarem Attribut dar.  
  
 In der Legende auf der rechten Seite des Viewers sind die verfügbren Zeitreihen auf Grundlage der Auswahl in der Dropdownliste aufgeführt. Aktivieren und deaktivieren Sie die Kontrollkästchen in der Legende, um zu steuern, welche Zeitreihe im Diagramm angezeigt wird.  
  
 Sie können hier zudem die Anzeigeoptionen ändern, z. B. die für eine bestimmte Zeitreihe verwendete Farbe oder ob Werte an Punkten im Diagramm angezeigt werden.  
  
#### <a name="to-select-a-time-series"></a>So wählen Sie eine Zeitreihe aus  
  
1.  Klicken Sie auf die **Diagramme** Registerkarte die **Miningmodell-Viewer** Registerkarte, wenn es nicht angezeigt wird.  
  
2.  Klicken Sie auf die Dropdownliste rechts neben der Diagrammansicht, und aktivieren Sie alle Kontrollkästchen. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Das Diagramm sollte nun 24 Zeilen für die verschiedenen Reihen enthalten.  
  
3.  Deaktivieren Sie die Kontrollkästchen rechts vom Diagramm, um die Zeilen für alle auf dem Betrag basierenden Reihen vorübergehend auszublenden.  
  
     Deaktivieren Sie nun die Kontrollkästchen für die Fahrräder R750 und R250.  
  
     Das Diagramm enthält anschließend nur die folgenden sechs Reihenzeilen, sodass Sie die Trends für die Fahrräder M200 und T1000 besser vergleichen können.  
  
    -   **M200 Europe: Quantity**  
  
    -   **M200 North America: Menge**  
  
    -   **M200 Pacific: Menge**  
  
    -   **T1000 Europe: Quantity**  
  
    -   **T1000 North America: Menge**  
  
    -   **T1000 Pacific: Menge**  
  
 ![Reihenvorhersagen für Mengen M200 und T1000](../../2014/tutorials/media/6series-defaultforecasting.gif "Reihenvorhersagen für Mengen M200 und T1000")  
  
 Das Diagramm, das in diesem Viewer angezeigt wird, schließt sowohl Vergangenheitsdaten als auch vorhergesagte Daten ein. Die vorhergesagten Daten sind schattiert dargestellt, um sie von den Vergangenheitsdaten abzugrenzen. Um den Vergleich unterschiedlicher Reihen zu erleichtern, können Sie außerdem die jeder Zeile im Diagramm zugeordneten Farben ändern. Weitere Informationen finden Sie unter [Ändern der im Data Mining-Viewer verwendeten Farben](../../2014/analysis-services/data-mining/change-the-colors-used-in-the-data-mining-viewer.md).  
  
 Den Trendlinien können Sie entnehmen, dass der Gesamtumsatz für alle Regionen zunimmt, wobei alle 12 Monate im Dezember Spitzenwerte verzeichnet werden. Aus dem Diagramm sehen Sie auch, dass die Daten für das Fahrrad T1000 deutlich später als die Daten für die anderen Produktreihen beginnt. Grund hierfür ist die Tatsache, dass es sich um ein neueres Produkt handelt. Da diese Reihe eine deutlich geringere Datengrundlage hat, sind die Vorhersagen möglicherweise nicht so genau.  
  
 Standardmäßig werden fünf Vorhersageschritte jede Zeitreihe als gepunktete Linien angezeigt. Sie können diesen Wert jedoch ändern und mehr oder weniger Vorhersagen anzeigen. Sie können die Standardabweichung für die Vorhersagen zudem grafisch darstellen, indem Sie dem Diagramm Fehlerindikatoren hinzufügen.  
  
#### <a name="to-change-prediction-and-display-options-in-the-chart-view"></a>So ändern Sie die Vorhersage- und Anzeigeoptionen in der Diagrammansicht  
  
1.  Versuchen Sie es ändern des Werts für **Vorhersageschritte** , allmählich von **5** zu **10**, und klicken Sie dann zurück in **6**.  
  
     Wenn die Vergangenheitsdaten große Schwankungen haben, werden die Schwankungen meist wiederholt oder sogar vergrößert, wenn Sie die Anzahl der Vorhersagen erhöhen. Vermutlich müssen Sie an diesem Punkt ein wenig nachforschen, um die Ursache der großen Erhöhung in den Vergangenheitsdaten zu verstehen. Anschließend entscheiden Sie, ob Sie diese Ergebnisse akzeptieren, sich in den Quelldaten um Korrektur bemühen oder im Modell eiine gewisse Glättung vornehmen möchten.  
  
2.  Wählen Sie die **Abweichungen anzeigen** Kontrollkästchen.  
  
     Diese Option zeigt den geschätzten Fehler für jeden vorhergesagten Wert an.  
  
3.  Beachten Sie die Skala der X-Achse. Die Änderungen an Vergangenheits- und vorhergesagten Daten werden immer als Prozentsatz ausgedrückt; die Istwerte werden jedoch automatisch so angepasst, dass alle Werte in das Diagramm passen. Daher dürfen Sie beim Vergleichen von Modellen nicht nur die grafische Darstellung berücksichtigen. Den genauen Wert oder die prozentuale Steigerung und Wert, um vorhersagen zu erstellen, halten Sie die Maus über die gepunktete Linie oder durchgezogene Linien oder klicken Sie auf die Zeilen zum Anzeigen der Werte in der **Mininglegende**.  
  
     **Tipp**: Wenn die **Mininglegende** ist nicht sichtbar ist, wechseln Sie zur **Modell** anzuzeigen, mit der rechten Maustaste in einen beliebigen Knoten, und wählen **Legende anzeigen**.  
  
 Nach dem Durchsehen dieser Trends bleiben Ihnen Bedenken wegen der geringen Datenbasis für menache Reihen. Sie fragen sich, ob vielleicht verlässlichere Vorhersagen möglich wären, wenn Sie Umsatzdurchschnitte nach Modell oder auch nach Region ermittelten. Diesem Ansatz werden Sie in einer späteren Lektion in diesem Lernprogramm nachgehen.  
  
 [Zurück zum Anfang](#bkmk_Charts)  
  
##  <a name="bkmk_Model"></a> Registerkarte "Modell"  
 Die **Modell** Registerkarte die [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Viewer im Data Mining-Designer können Sie das forecasting-Modells in Form von ein Strukturdiagramm anzeigen.  
  
 Beachten Sie zuerst, dass das von Ihnen erstellte Modell eigentlich 24 verschiedene Strukturen enthält, da Ihre Daten zwei verschiedene Messwerte (Menge und Menge) für die Verkäufe mehrerer Produktlinien (T1000 usw.) in drei verschiedenen Bereichen (Europa, Nordamerika und Pazifik) beschreiben. Dabei stellt jede Struktur ein Modell der Verkaufsmuster für eine andere Kombination von Bereich, Produkt und vorhersagbarem Attribut dar.  
  
 Sie können auswählen, welche Kombination von Produktlinie, Bereich und umsatzmetrik Sie anzeigen, indem er eine Reihe von möchten die **Struktur** Dropdown-Liste auf die **Modell** Registerkarte.  
  
 Welche Einblicke gibt Ihnen also eine Anzeige des Modells als Struktur? Vergleichen wir als Beispiel zwei Modelle: eines hat mehrere Ebenen in der Struktur, und eines verfügt nur über einen einzelnen Knoten.  
  
-   Wenn ein Strukturdiagramm einen einzelnen Knoten enthält, bedeutet dies, dass der im Modell gefundene Trend im Zeitverlauf überwiegend homogen ist. Sie können diesen einzelnen Knoten mit der Bezeichnung **alle**, um die Formel anzuzeigen, die die Beziehung zwischen den Eingangsvariablen und dem Ergebnis beschreibt.  
  
-   Wenn ein Strukturdiagramm für eine Zeitreihe mehrere Verzweigungen hat, bedeutet dies, dass die erkannte Zeitreihe zu komplex für eine Darstellung als einzelne Gleichung ist. Stattdessen das Strukturdiagramm mehrere Verzweigungen, wobei jede Verzweigung, die die Bedingungen, die aufgrund die Struktur mit der Bezeichnung enthalten möglicherweise *teilen*. Wenn sich die Struktur teilt, stellt jede Verzweigung ein Zeitsegment dar, innerhalb dessen der Trend als einzelne Gleichung beschrieben werden kann.  
  
     Z. B. Wenn Sie das Diagramm ansehen und einen abrupten Sprung in Verkaufsvolumen ab irgendwann im September und der Vorgang fortgesetzt, bis ein Feiertag, Sie können zum Wechseln der **Modell** Ansicht finden in das genaue Datum der trendänderung. Die Verzweigungen in der Struktur, die "vor September" und "nach September" darstellen, enthalten unterschiedliche Formeln: eine Formel, die den Verkaufstrend bis zur Teilung mathematisch beschreibt, und eine andere Formel, die den Verkaufstrend von September bis zum Feiertag am Jahresende beschreibt.  
  
#### <a name="to-explore-the-decision-tree-for-a-time-series-model"></a>So untersuchen Sie die Entscheidungsstruktur für ein Zeitreihenmodell  
  
1.  In der **Struktur** auf in der Liste der **Modell** wählen auf der Registerkarte die **T1000 Europe: Amount** Reihe.  
  
     Klicken Sie auf den Knoten, die mit der Bezeichnung **alle**.  
  
     Für eine **alle** Knoten, die QuickInfo, die angezeigt wird enthält Informationen, z. B. die Anzahl der Fälle, in der gesamten Reihe und zeitreihenformeln, die von abgeleiteten Analyse der Daten.  
  
2.  Wenn die **Mininglegende** ist nicht sichtbar, mit der rechten Maustaste des Knotens, und wählen Sie **Legende anzeigen**.  
  
     Die **Mininglegende** größtenteils dieselbe Informationen, die in der QuickInfo enthält. Wenn eine Ihrer unabhängigen Variablen diskret ist, sehen Sie auch ein Histogramm, das die Verteilung der Variablen im Knoten anzeigt.  
  
3.  Wählen Sie jetzt eine andere Zeitreihe zur Anzeige aus. Mithilfe der **Struktur** auf in der Liste der **Modell** wählen auf der Registerkarte die **M200 North America: Menge** Reihe.  
  
     Das Strukturdiagramm enthält jetzt eine **alle** und zwei untergeordnete Knoten. Den Beschriftungen untergeordneten Knoten können Sie entnehmen, an welchem Punkt die Trendlinie sich geändert hat.  
  
     Für jeden untergeordneten Knoten, der Beschreibung in der **Mininglegende** enthält auch die Anzahl der Fälle in jeder Verzweigung der Struktur.  
  
 Die folgende Liste beschreibt einige zusätzliche Funktionen des Struktur-Viewers:  
  
-   Sie können ändern, dass die Variable, die im Diagramm, mithilfe dargestellt wird der **Hintergrund** Steuerelement. Standardmäßig enthalten dunklere Knoten mehr Fälle, da der Wert des **Hintergrund** nastaven NA hodnotu **Auffüllung**. Um anzuzeigen, wie viele Fälle gibt es nur in einem Knoten sind, halten Sie die Maus auf einen Knoten aus, und zeigen Sie die QuickInfo, die angezeigt wird, oder klicken Sie auf den Knoten aus, und zeigen Sie die Zahlen in der **Knotenlegende** Fenster.  
  
-   In der QuickInfo oder durch Klicken auf den Knoten kann zudem die Regressionsformel für den Knoten angezeigt werden. Wenn Sie ein gemischtes Modell erstellt haben, sehen Sie zwei Formeln, eine für ARTXP (in den Blattknoten) und eine für ARIMA (im Stammknoten der Struktur).  
  
-   Die kleinen Rauten werden in Knoten verwendet, die fortlaufende Nummern darstellen. Der Attributbreich wird in der Leiste angezeigt, auf der sich die Raute befindet. Die Raute befindet sich am Mittelwert des Knotens. Die Breite der Raute gibt die Varianz des Attributs an diesem Knoten an.  
  
 [Zurück zum Anfang](#bkmk_Charts)  
  
##  <a name="bkmk_Content"></a> (Optional) Generic Content Tree-Viewer  
 Zusätzlich zu den benutzerdefinierten Viewer für Zeitreihen stellt [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bietet die **MicrosoftGeneric Content Tree Viewer** für die Verwendung mit allen Datamining-Modellen. Dieser Viewer bietet einige Vorteile:  
  
-   **Microsoft Time Series-Viewer**: in dieser Ansicht werden die Ergebnisse der beiden Algorithmen zusammengeführt. Obwohl Sie jede Reihe getrennt anzeigen können, können Sie nicht bestimmen, wie die Ergebnisse jedes Algorithmus kombiniert wurden. Zudem zeigen die QuickInfos und die Mininglegende in dieser Sicht nur die wichtigsten Statistiken an.  
  
-   **Generic Content Tree Viewer**: ermöglicht Ihnen das Durchsuchen und Anzeigen der Datenreihen, die verwendet wurden alle auf einmal im Modell, und wenn Sie ein gemischtes erstellt haben, zu modellieren, die ARIMA- und ARTXP-Strukturen im gleichen Diagramm angezeigt.  
  
     Sie können mit diesem Viewer alle Statistiken aus beiden Algorithmen sowie die Verteilungen der Werte abrufen.  
  
     Empfohlen für sachkundige Benutzer von Data Mining, die mehr über ARIMA- und ARTXP-Analysen erfahren möchten.  
  
#### <a name="to-view-details-for-a-particular-data-series-in-the-generic-content-viewer"></a>So zeigen Sie Details für eine bestimmte Datenreihe im Generic Content Tree Viewer an  
  
1.  In der **Miningmodell-Viewer** Registerkarte **Microsoft Generic Content Tree Viewer** aus der **Viewer** Dropdown-Liste.  
  
2.  In der **Knotenbeschriftung** Bereich, klicken Sie den obersten Knoten (alle).  
  
3.  In der **Knotendetails** Bereich, zeigen Sie den Wert für ATTRIBUTE_NAME.  
  
     Dieser Wert zeigt an, welche Reihe oder Kombination von Produkt und Region in diesem Knoten enthalten ist. Im AdventureWorks-Beispiel beinhaltet der oberste Knoten die Reihe M200 Europe.  
  
4.  In der **Knotenbeschriftung** Bereich, suchen Sie den ersten Knoten, die über untergeordnete Knoten verfügt.  
  
     Wenn Sie ein Reihe Knoten untergeordnete Elemente verfügt, der Strukturansicht angezeigt, das angezeigt wird auf die **Modell** der Microsoft Time Series-Viewer auf der Registerkarte müssen auch eine Verzweigungsstruktur.  
  
5.  Erweitern Sie den Knoten, und klicken Sie auf einen der untergeordneten Knoten.  
  
     Die Spalte NODE_DESCRIPTION des Schemas enthält die Bedingung, die zur Teilung der Struktur führte.  
  
6.  In der **Knotenbeschriftung** Bereich, klicken Sie auf den obersten ARIMA-Knoten, und erweitern Sie den Knoten, bis alle untergeordneten Knoten sichtbar sind.  
  
7.  In der **Knotendetails** Bereich, zeigen Sie den Wert für ATTRIBUTE_NAME.  
  
     Dieser Wert sagt Ihnen, welche Zeitreihe in diesem Knoten enthalten ist. Der oberste Knoten im Abschnitt ARIMA sollte mit dem obersten Knoten im Abschnitt (Alle) übereinstimmen. Im AdventureWorks-Beispiel enthält dieser Knoten die ARIMA-Analyse für die Reihe M200 Europe.  
  
 Weitere Informationen finden Sie unter [Mingingmodellinhalt von Zeitreihenmodellen &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md).  
  
 [Zurück zum Anfang](#bkmk_Charts)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Erstellen von Zeitreihenvorhersagen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [Technische Referenz für den Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
