---
title: Durchsuchen eine Entscheidung Trees-Modell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
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
ms.openlocfilehash: 257d193c84420a0c70ea99ef2a8cadfa9e11eec5
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52525559"
---
# <a name="browsing-a-decision-trees-model"></a>Durchsuchen eines Entscheidungsstrukturmodells
  Beim Öffnen ein klassifizierungsmodell mit **Durchsuchen**, das Modell wird angezeigt, in einem interaktiven Entscheidungsstruktur-Viewer, ähnlich wie die [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees-Viewer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Im Viewer werden die Ergebnisse der Klassifizierung als Diagramm angezeigt. Darin sind die Kriterien hervorgehoben, die verschiedene Datengruppen voneinander unterscheiden. Sie können auch einen Drilldown auf einzelne Teilmengen der Struktur ausführen und die zugrunde liegenden Daten abrufen.  
  
##  <a name="bkmk_Top"></a> Durchsuchen des Modells  
 Modelle, die auf dem Decision Trees-Algorithmus basieren, verfügen über eine große Menge aufschlussreicher Informationen, die Sie untersuchen können. Die **Durchsuchen** Fenster enthält die folgenden Registerkarten und Bereiche können Sie Muster erkennen und Vorhersageergebnisse, die Verwendung des Diagramms:  
  
-   [Entscheidungsstruktur](#BKMK_DecisionTree)  
  
-   [Abhängigkeitsnetzwerk](#BKMK_DNetwork)  
  
 Um mit einem Entscheidungsstrukturmodell zu experimentieren, können Sie die Beispieldaten auf der Registerkarte Trainingsdaten (oder Quelldaten) der Beispieldaten-Arbeitsmappe verwenden und ein Entscheidungsstrukturmodell erstellen, für das "Bike Buyer" als vorhersagbares Attribut verwendet wird.  
  
###  <a name="BKMK_DecisionTree"></a> Entscheidungsstruktur  
 Mithilfe dieser Ansicht sind Sie in der Lage, die Faktoren, die zu einem Ergebnis führen, zu verstehen und zu untersuchen.  
  
 Das Entscheidungsstrukturdiagramm kann wie folgt von links nach rechts ausgewertet werden:  
  
-   Die Rechtecke, die als bezeichnet *Knoten*, enthalten Teilmengen der Daten. Die Beschriftung des Knotens gibt die Unterscheidungsmerkmale dieser Teilmenge an.  
  
-   Der äußerst linke Knoten, die mit der Bezeichnung **alle**, stellt das vollständige DataSet. Alle nachfolgenden Knoten stellen Teilmengen der Daten dar.  
  
-   Eine Entscheidungsstruktur enthält viele *teilt*, oder stellen Sie die Daten, in dem abweicht, in mehrere Gruppen auf Grundlage von Attributen.  
  
     In der ersten Unterteilung des Beispielmodells ist das Dataset beispielsweise in drei Altersgruppen unterteilt.  
  
-   Die Aufteilung unmittelbar nach der **alle** Knoten ist am wichtigsten, da es sich um die hauptbedingung angezeigt, die dieses Dataset unterteilt.  
  
     Weitere Unterteilungen befinden sich rechts davon. Durch die Analyse der verschiedenen Struktursegmente können Sie verstehen, welche Attribute den größten Einfluss auf das Kaufverhalten haben.  
  
 ![Abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell](media/dm13-dec-tree-split-definition.gif "abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell")  
  
 Anhand dieser Informationen können Sie eine zielgruppenorientierte Marketingkampagne für Kunden entwickeln, die durch bestimmte Anreize zum Kauf motiviert werden.  
  
##### <a name="explore-the-decision-tree"></a>Untersuchen der Entscheidungsstruktur  
  
1.  Klicken Sie auf die **alle** Knoten, und sehen Sie sich die **Mininglegende**.  
  
     Darin finden Sie die genaue Anzahl der Fälle im Trainingsdataset sowie eine Aufschlüsselung der Ergebnisse.  
  
     Sie können die gleichen Informationen in einer QuickInfo anzeigen, wenn Sie den Mauszeiger auf einen Knoten bewegen.  
  
2.  Klicken Sie auf das Plus- oder Minuszeichen neben den einzelnen Knoten, um die Struktur zu erweitern oder zu reduzieren.  
  
     Sie können auch die **Ebene anzeigen** Schieberegler zum Erweitern oder verkleinern die Struktur.  
  
3.  Ist Ihnen aufgefallen, dass einige Knoten dunkler sind als andere?  
  
     In der Standardeinstellung **Auffüllung** dient als schattierungsvariable, was bedeutet, dass die Intensität der Farbe zeigt, welche Knoten die größte Unterstützung verfügen.  
  
     Der äußerst linke Knoten, der das gesamte Dataset enthält, weist demnach die höchste Farbintensität auf.  
  
4.  Ändern Sie den Wert für **Hintergrund** aus **allen Fällen** zu **Ja**.  
  
     ![Ändern der entscheidungsstrukturdiagramm zum Hervorheben der Käufer](media/dm13-dectreeshadedbuyer.gif "Ändern des entscheidungsstrukturdiagramms zum Hervorheben der Käufer")  
  
5.  Jetzt erkennen Sie an der Intensität der Farbe, wie viele Kunden in jedem Knoten ein Fahrrad gekauft haben, also genau das Verhalten, das Sie untersuchen möchten.  
  
     Achten Sie auch auf die Farbbalken innerhalb jedes Knotens. Dies ist ein Histogramm, das die Verteilung von Ergebnissen innerhalb dieser Teilmenge von Daten anzeigt. Die farbige Leiste zeigt z. B. in der Beispiel-Bike Buyer-Entscheidungsstruktur den Anteil der Kunden, die Fahrräder (Werte "Ja") im Vergleich zu den gekauft haben, die nicht der Fall (keine Werte). Um die genauen Werte zu erhalten, Sie können klicken Sie auf den Knoten und zeigen die **Mininglegende**.  
  
6.  Bei der Auswertung des Diagramms erkennen Sie, wie sich jede einzelne Teilmenge von Daten in kleinere Gruppen aufgliedert und welche Attribute am hilfreichsten sind, um ein Ergebnis vorherzusagen.  
  
     Allein die Intensität der Schattierung deutet bereits auf einige interessante Gruppierungen hin, die Sie anhand detaillierterer Daten vergleichen können. Diese Gruppen zeichnen sich durch eine relativ hohe Wahrscheinlichkeit aus, in Zukunft ein Fahrrad zu kaufen:  
  
    -   Age > = 32 und \< 53 und jährlichen Einkommen > = 26000 und Kinder = 0  
  
         Fälle gesamt: 1150  
  
         Bike Buyer Wahrscheinlichkeit: 18 %  
  
    -   Age > = 32 und \< 53 und jährlichen Einkommen > = 26000 und Kinder nicht = 0 und Familienstand = "Single"  
  
         Fälle gesamt: 402  
  
         Bike Buyer Wahrscheinlichkeit: 16 %  
  
7.  Ändern Sie den Wert für **Hintergrund** aus **Ja** zu **keine** und festzustellen, wie das Diagramm ändert.  
  
     ![Abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell](media/dm13-dec-tree-background-no.gif "abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell")  
  
 **Tipps**  
  
-   Wenn die Daten in mehrere Reihen aufgeteilt werden können, wird für jedes Dataset, das Sie modellieren möchten, ein anderes Modell erstellt.  
  
-   Im Daten-Beispielmodell gibt es nur ein vorhersagbares Ergebnis - Bike Buyer - aber nehmen wir an, dass Sie die Informationen, ob der Kunde einen Wartungsvertrag und vorhergesagt werden soll, die auch mussten. In diesem Fall würden sich die Daten in einer separaten Spalte befinden und zwei vorhersagbare Attribute aus dem Modell enthalten.  
  
     Klicken Sie auf die **Histogramm** Option in der oben links im Bereich Decision Tree so ändern Sie die maximale Anzahl von Zuständen, die im Histogramm der Struktur angezeigt werden können. Dies ist sinnvoll, wenn die vorhersagbaren Attribute viele Status haben. Die Status werden von links nach rechts in einem Histogramm in Reihenfolge der Verwendungshäufigkeit angezeigt.  
  
-   Sie können auch mithilfe der Optionen auf der **Entscheidungsstruktur** Tab, um die Auswirkungen auf die durch Vergrößern oder verkleinern, oder die Diagrammgröße an die Fenstergröße anpassen, wie die Struktur angezeigt wird.  
  
-   Verwenden Sie die Option **Standarderweiterung** , um die Standardzahl der für alle Strukturen im Modell angezeigten Ebenen festzulegen.  
  
-   Wählen Sie **langen Namen anzeigen** auf den vollständigen Namen des Attributs, einschließlich der Datenquelle anzuzeigen. Kurze Namen und lange Namen sind identisch, solange die Fälle aus derselben Datenquelle wie die Attribute für jeden Fall abgefragt werden.  
  
 [Zurück zum Anfang](#bkmk_Top)  
  
###  <a name="BKMK_DNetwork"></a> Abhängigkeitsnetzwerk  
 Die **Abhängigkeitsnetzwerk** zeigt die Verbindungen zwischen den Eingabeattributen und den vorhersagbaren Attributen im Modell.  
  
1.  Klicken Sie auf, und ziehen Sie den Schieberegler auf der linken Seite des Viewers  
  
     Befindet sich dieser auf der obersten Position, werden alle Verbindungen angezeigt. Wenn Sie den Schieberegler nach unten ziehen, werden nur die stärksten Verbindungslinien im Viewer angezeigt.  
  
2.  Klicken Sie jetzt auf den Knoten Bike Buyer.  
  
     ![Abhängigkeitsnetzwerkansicht für Entscheidungsstrukturen](media/dm13-dectree-depnet.gif "Abhängigkeitsnetzwerkansicht für Entscheidungsstrukturen")  
  
     Wenn Sie einen Knoten auswählen, hebt der Viewer die Abhängigkeiten hervor, die knotenspezifisch sind. In diesem Fall werden im Viewer die einzelnen Knoten hervorgehoben, mit denen sich das Ergebnis vorhersagen lässt.  
  
3.  Wenn der Viewer zahlreiche Knoten enthält, Sie können nach bestimmten Knoten Suchen mithilfe der **Knoten suchen** Schaltfläche. Durch Klicken auf **Knoten finden** wird das Dialogfeld **Knoten finden** geöffnet, in dem Sie mit einem Filter nach bestimmten Knoten suchen und diese auswählen können.  
  
4.  Die Legende im unteren Bereich des Viewers verknüpft Farbcodes mit dem Abhängigkeitstyp im Diagramm. Wenn Sie einen vorhersagbaren Knoten auswählen, wird dieser z. B. türkis schattiert, und die Knoten, die den ausgewählten Knoten vorhersagen, orange.  
  
 [Zurück zum Anfang](#bkmk_Top)  
  
### <a name="drill-through-to-underlying-data"></a>Ausführen eines Drillthroughs zu zugrunde liegenden Daten  
 Verschiedener Typen von Modellen unterstützen die Möglichkeit, *Drillthrough* aus dem Modell zu den zugrunde liegenden Falldaten. Dies kann sehr hilfreich sein, wenn Sie Kunden aus einem bestimmten Segment kontaktieren oder Daten für weiterführende Analysen extrahieren möchten.  
  
##### <a name="get-case-data"></a>Abrufen von Falldaten  
  
1.  Klicken Sie mit der rechten Maustaste auf den Strukturknoten, der die gewünschten Daten enthält, und wählen Sie eine der folgenden Optionen aus:  
  
    -   **Drillthrough für Modell**. Durch diese Option werden die zum ausgewählten Knoten gehörenden Fälle abgerufen und in einer Excel-Tabelle gespeichert. Sie rufen nur die Datenspalten ab, die tatsächlich zur Modellerstellung verwendet wurden.  
  
    -   **Drillthrough für Strukturspalten**. Durch diese Option werden die zum ausgewählten Knoten gehörenden Fälle abgerufen und in einer Excel-Tabelle gespeichert. Sie rufen alle Informationen, die zur Verfügung, in der zugrunde liegenden Daten, wenn Sie es noch eine Spalte erstellt wurde nicht im Modell verwendet. Möglicherweise haben Sie die Kundenadresse und die Postleitzahl ausgeschlossen, weil sie zu Analysezwecken nicht hilfreich sind; trotzdem wurden sie in der Struktur beibehalten.  
  
     Kehren Sie zu Excel zurück, um die Daten anzuzeigen. In der Anzeige Durchsuchen wird eine Abfrage ausgeführt, die Daten werden in einer Tabelle eines neuen Arbeitsblatts gespeichert und die Ergebnisse mit Beschriftungen versehen.  
  
     ![Drillthroughergebnisse werden in Excel gespeichert](media/dm13-dectree-drillthroughresults.gif "Drillthroughergebnisse werden in Excel gespeichert.")  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
