---
title: Durchsuchen eines Decision Trees-Modells | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- tree viewer
- mining model, decision tree
- decision tree [data mining]
- dependency network
ms.assetid: 6b3dd1ae-caff-41c3-817b-802dc020ff88
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 17b3a2765781813c832b0b654e4a02475b3ab623
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66064673"
---
# <a name="browsing-a-decision-trees-model"></a>Durchsuchen eines Entscheidungsstrukturmodells
  Wenn Sie ein Klassifizierungs Modell mithilfe von **Durchsuchen**öffnen, wird das Modell in einem interaktiven Entscheidungsstruktur-Viewer angezeigt, [!INCLUDE[msCoName](../includes/msconame-md.md)] der dem Decision Trees [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Viewer in ähnelt. Im Viewer werden die Ergebnisse der Klassifizierung als Diagramm angezeigt. Darin sind die Kriterien hervorgehoben, die verschiedene Datengruppen voneinander unterscheiden. Sie können auch einen Drilldown auf einzelne Teilmengen der Struktur ausführen und die zugrunde liegenden Daten abrufen.  
  
##  <a name="explore-the-model"></a><a name="bkmk_Top"></a>Untersuchen des Modells  
 Modelle, die auf dem Decision Trees-Algorithmus basieren, verfügen über eine große Menge aufschlussreicher Informationen, die Sie untersuchen können. Das Fenster **Durchsuchen** enthält die folgenden Registerkarten und Bereiche, die Sie beim Erlernen der Muster und Vorhersagen von Ergebnissen mithilfe des Diagramms unterstützen:  
  
-   [Entscheidungsstruktur](#BKMK_DecisionTree)  
  
-   [Abhängigkeitsnetzwerk](#BKMK_DNetwork)  
  
 Um mit einem Entscheidungsstrukturmodell zu experimentieren, können Sie die Beispieldaten auf der Registerkarte Trainingsdaten (oder Quelldaten) der Beispieldaten-Arbeitsmappe verwenden und ein Entscheidungsstrukturmodell erstellen, für das "Bike Buyer" als vorhersagbares Attribut verwendet wird.  
  
###  <a name="decision-tree"></a><a name="BKMK_DecisionTree"></a>Entscheidungsstruktur  
 Mithilfe dieser Ansicht sind Sie in der Lage, die Faktoren, die zu einem Ergebnis führen, zu verstehen und zu untersuchen.  
  
 Das Entscheidungsstrukturdiagramm kann wie folgt von links nach rechts ausgewertet werden:  
  
-   Die Rechtecke, die als *Knoten*bezeichnet werden, enthalten Teilmengen der Daten. Die Beschriftung des Knotens gibt die Unterscheidungsmerkmale dieser Teilmenge an.  
  
-   Der Knoten ganz links mit der Bezeichnung **all**stellt das vollständige DataSet dar. Alle nachfolgenden Knoten stellen Teilmengen der Daten dar.  
  
-   Eine Entscheidungsstruktur enthält viele Teilungen oder Orte, an denen die Daten auf der Grundlage von Attributen in mehrere Sätze unter *teilt*werden.  
  
     In der ersten Unterteilung des Beispielmodells ist das Dataset beispielsweise in drei Altersgruppen unterteilt.  
  
-   Die Teilung unmittelbar nach dem Knoten **alle** ist am wichtigsten, da Sie die primäre Bedingung anzeigt, die dieses DataSet dividiert.  
  
     Weitere Unterteilungen befinden sich rechts davon. Durch die Analyse der verschiedenen Struktursegmente können Sie verstehen, welche Attribute den größten Einfluss auf das Kaufverhalten haben.  
  
 ![Abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell](media/dm13-dec-tree-split-definition.gif "Abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell")  
  
 Anhand dieser Informationen können Sie eine zielgruppenorientierte Marketingkampagne für Kunden entwickeln, die durch bestimmte Anreize zum Kauf motiviert werden.  
  
##### <a name="explore-the-decision-tree"></a>Untersuchen der Entscheidungsstruktur  
  
1.  Klicken Sie auf den Knoten **alle** , und sehen Sie sich die **Mining Legende**an.  
  
     Darin finden Sie die genaue Anzahl der Fälle im Trainingsdataset sowie eine Aufschlüsselung der Ergebnisse.  
  
     Sie können die gleichen Informationen in einer QuickInfo anzeigen, wenn Sie den Mauszeiger auf einen Knoten bewegen.  
  
2.  Klicken Sie auf das Plus- oder Minuszeichen neben den einzelnen Knoten, um die Struktur zu erweitern oder zu reduzieren.  
  
     Sie können auch den Schieberegler **Ebene anzeigen** verwenden, um die Struktur zu vergrößern oder zu verkleinern.  
  
3.  Ist Ihnen aufgefallen, dass einige Knoten dunkler sind als andere?  
  
     Standardmäßig wird die Auffüllung als Schattierungs Variable verwendet, was **bedeutet, dass** die Intensität der Farbe Ihnen anzeigt, welche Knoten die meiste Unterstützung bieten.  
  
     Der äußerst linke Knoten, der das gesamte Dataset enthält, weist demnach die höchste Farbintensität auf.  
  
4.  Ändern Sie den Wert für **Hintergrund** von **allen Fällen** in **Ja**.  
  
     ![Ändern des Entscheidungsstrukturdiagramms zum Hervorheben der Käufer](media/dm13-dectreeshadedbuyer.gif "Ändern des Entscheidungsstrukturdiagramms zum Hervorheben der Käufer")  
  
5.  Jetzt erkennen Sie an der Intensität der Farbe, wie viele Kunden in jedem Knoten ein Fahrrad gekauft haben, also genau das Verhalten, das Sie untersuchen möchten.  
  
     Achten Sie auch auf die Farbbalken innerhalb jedes Knotens. Dies ist ein Histogramm, das die Verteilung von Ergebnissen innerhalb dieser Teilmenge von Daten anzeigt. Beispielsweise zeigt die farbige Leiste in der Beispiel-Entscheidungsstruktur für Bike Buyer den Anteil der Kunden an, die Fahrräder gekauft haben (Ja-Werte), und diejenigen, die keine (keine Werte). Um die genauen Werte zu erhalten, können Sie auf den Knoten klicken und die **Mining Legende**anzeigen.  
  
6.  Bei der Auswertung des Diagramms erkennen Sie, wie sich jede einzelne Teilmenge von Daten in kleinere Gruppen aufgliedert und welche Attribute am hilfreichsten sind, um ein Ergebnis vorherzusagen.  
  
     Allein die Intensität der Schattierung deutet bereits auf einige interessante Gruppierungen hin, die Sie anhand detaillierterer Daten vergleichen können. Diese Gruppen zeichnen sich durch eine relativ hohe Wahrscheinlichkeit aus, in Zukunft ein Fahrrad zu kaufen:  
  
    -   Alter >= 32 und \< 53 und Jahreseinkommen >= 26000 und Children = 0  
  
         Fälle gesamt: 1150  
  
         Bike Buyer-Wahrscheinlichkeit: 18%  
  
    -   Age >= 32 und \< 53 und Jahreseinkommen >= 26000 und Children not = 0 und Familien Status = ' Single '  
  
         Fälle gesamt: 402  
  
         Wahrscheinlichkeit eines Fahrradkaufs: 16 %  
  
7.  Ändern Sie den Wert für **Hintergrund** von **Ja** in **Nein** , und sehen Sie sich an, wie sich das Diagramm ändert.  
  
     ![Abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell](media/dm13-dec-tree-background-no.gif "Abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell")  
  
 **Tipps**  
  
-   Wenn die Daten in mehrere Reihen aufgeteilt werden können, wird für jedes Dataset, das Sie modellieren möchten, ein anderes Modell erstellt.  
  
-   Im Beispiel Datenmodell gibt es nur ein vorhersagbares Ergebnis: Bike Buyer, aber angenommen, Sie hatten Informationen dazu, ob der Kunde einen Serviceplan gekauft hat und auch Vorhersagen wollte. In diesem Fall würden sich die Daten in einer separaten Spalte befinden und zwei vorhersagbare Attribute aus dem Modell enthalten.  
  
     Klicken Sie in der oberen linken Ecke des Bereichs Entscheidungsstruktur auf die Option **Histogramm** , um die maximale Anzahl von Zuständen zu ändern, die in den Histogrammen in der Struktur vorkommen können. Dies ist sinnvoll, wenn die vorhersagbaren Attribute viele Status haben. Die Status werden von links nach rechts in einem Histogramm in Reihenfolge der Verwendungshäufigkeit angezeigt.  
  
-   Sie können auch die Optionen auf der Registerkarte **Entscheidungs** Struktur verwenden, um zu beeinflussen, wie die Struktur angezeigt wird, indem Sie Zoomen oder verkleinern oder die Größe des Diagramms anpassen.  
  
-   Verwenden Sie die Option **Standarderweiterung** , um die Standardzahl der für alle Strukturen im Modell angezeigten Ebenen festzulegen.  
  
-   Wählen Sie **langen Namen anzeigen** aus, um den vollständigen Namen des Attributs einschließlich der Datenquelle anzuzeigen. Kurze Namen und lange Namen sind identisch, solange die Fälle aus derselben Datenquelle wie die Attribute für jeden Fall abgefragt werden.  
  
 [Zurück zum Anfang](#bkmk_Top)  
  
###  <a name="dependency-network"></a><a name="BKMK_DNetwork"></a>Abhängigkeits Netzwerk  
 Die **Abhängigkeits Netzwerk** Ansicht zeigt die Verbindungen zwischen den Eingabe Attributen und den vorhersagbaren Attributen im Modell an.  
  
1.  Klicken und ziehen Sie den Schieberegler auf der linken Seite des Viewers.  
  
     Befindet sich dieser auf der obersten Position, werden alle Verbindungen angezeigt. Wenn Sie den Schieberegler nach unten ziehen, werden nur die stärksten Verbindungslinien im Viewer angezeigt.  
  
2.  Klicken Sie jetzt auf den Knoten Bike Buyer.  
  
     ![Abhängigkeitsnetzwerkansicht für Entscheidungsstrukturen](media/dm13-dectree-depnet.gif "Abhängigkeitsnetzwerkansicht für Entscheidungsstrukturen")  
  
     Wenn Sie einen Knoten auswählen, hebt der Viewer die Abhängigkeiten hervor, die knotenspezifisch sind. In diesem Fall werden im Viewer die einzelnen Knoten hervorgehoben, mit denen sich das Ergebnis vorhersagen lässt.  
  
3.  Wenn der Viewer zahlreiche Knoten enthält, können Sie mithilfe der Schaltfläche **Knoten** suchen nach bestimmten Knoten suchen. Durch Klicken auf **Knoten finden** wird das Dialogfeld **Knoten finden** geöffnet, in dem Sie mit einem Filter nach bestimmten Knoten suchen und diese auswählen können.  
  
4.  Die Legende im unteren Bereich des Viewers verknüpft Farbcodes mit dem Abhängigkeitstyp im Diagramm. Wenn Sie einen vorhersagbaren Knoten auswählen, wird dieser z. B. türkis schattiert, und die Knoten, die den ausgewählten Knoten vorhersagen, orange.  
  
 [Zurück zum Anfang](#bkmk_Top)  
  
### <a name="drill-through-to-underlying-data"></a>Ausführen eines Drillthroughs zu zugrunde liegenden Daten  
 Mehrere Modelltypen unterstützen die Möglichkeit, einen *Drillthrough* vom Modell zu den zugrunde liegenden Falldaten auszuführen. Dies kann sehr hilfreich sein, wenn Sie Kunden aus einem bestimmten Segment kontaktieren oder Daten für weiterführende Analysen extrahieren möchten.  
  
##### <a name="get-case-data"></a>Abrufen von Falldaten  
  
1.  Klicken Sie mit der rechten Maustaste auf den Strukturknoten, der die gewünschten Daten enthält, und wählen Sie eine der folgenden Optionen aus:  
  
    -   **Drillthrough des Modells**. Durch diese Option werden die zum ausgewählten Knoten gehörenden Fälle abgerufen und in einer Excel-Tabelle gespeichert. Sie rufen nur die Datenspalten ab, die tatsächlich zur Modellerstellung verwendet wurden.  
  
    -   **Drillthrough für Struktur Spalten**. Durch diese Option werden die zum ausgewählten Knoten gehörenden Fälle abgerufen und in einer Excel-Tabelle gespeichert. Sie erhalten alle Informationen, die während der Erstellung in den zugrunde liegenden Daten verfügbar waren, auch wenn eine Spalte nicht im Modell verwendet wurde. Möglicherweise haben Sie die Kundenadresse und die Postleitzahl ausgeschlossen, weil sie zu Analysezwecken nicht hilfreich sind; trotzdem wurden sie in der Struktur beibehalten.  
  
     Kehren Sie zu Excel zurück, um die Daten anzuzeigen. In der Anzeige Durchsuchen wird eine Abfrage ausgeführt, die Daten werden in einer Tabelle eines neuen Arbeitsblatts gespeichert und die Ergebnisse mit Beschriftungen versehen.  
  
     ![Drillthroughergebnisse werden in Excel gespeichert.](media/dm13-dectree-drillthroughresults.gif "Drillthroughergebnisse werden in Excel gespeichert.")  
  
## <a name="see-also"></a>Weitere Informationen  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
