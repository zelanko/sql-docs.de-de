---
title: Durchsuchen der Market Basket-Modells (mittleres Datamining-Lernprogramm) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: da1c9cb7-6c32-4b9b-96ec-ecea772aeb77
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7b3a2e70a8831bd31a8397ec57a71dbf1f5a3207
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36313068"
---
# <a name="exploring-the-market-basket-models-intermediate-data-mining-tutorial"></a>Prüfen des Market Basket-Modells (Mittleres Data Mining Tutorial)
  Nun, dass Sie erstellt haben die `Association` Modell durchsuchen können Sie es mithilfe der [!INCLUDE[msCoName](../includes/msconame-md.md)] Zuordnungsregeln-Viewer in die **Miningmodell-Viewer** des Data Mining-Designers. Dieses Lernprogramm führt Sie durch die Verwendung des Viewers, um Beziehungen zwischen Elementen zu untersuchen. Der Viewer hilft Ihnen, schnell zu erkennen, welche Produkte häufig zusammen angezeigt werden, und eine allgemeine Vorstellung von den so entstehenden Muster zu erhalten.  
  
 Die [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Viewer enthält drei Registerkarten: **Regeln**, **Itemsets**, und **Abhängigkeitsnetzwerk**. Da jede Registerkarte eine etwas andere Sicht der Daten zeigt, werden Sie bei der Untersuchung eines Modells in der Regel mehrmals zwischen den einzelnen Bereichen hin und her wechseln, während Sie die Einsichten verfolgen.  
  
-   [Registerkarte Abhängigkeitsnetzwerk](#bkmk_DepNet)  
  
-   [Registerkarte "Itemsets"](#bkmk_Itemsets)  
  
-   [Registerkarte "Regeln"](#bkmk_Rules)  
  
-   [Generische Inhaltssicht](#bkmk_ContentViewer)  
  
 In diesem Lernprogramm fangen Sie die **Abhängigkeitsnetzwerk** Registerkarte, und verwenden Sie dann die **Regeln** Registerkarte und **Itemsets** Tab, um Ihr Verständnis der Beziehungen zu vertiefen im Viewer angezeigt. Verwenden Sie ebenfalls die **Microsoft Generic Content Tree Viewer** detaillierte Statistiken für einzelne Regeln oder Itemsets abgerufen werden sollen.  
  
##  <a name="bkmk_DepNet"></a> Registerkarte Abhängigkeitsnetzwerk  
 Mit der **Abhängigkeitsnetzwerk** Registerkarte können Sie die Interaktion der verschiedenen Elemente im Modell untersuchen. Jeder Knoten im Viewer steht für ein Element, und die Linien zwischen diesen Knoten stellen Regeln dar. Wenn Sie einen Knoten auswählen, können Sie feststellen, welcher andere Knoten das ausgewählte Element vorhersagt oder welche Elemente von dem aktuellen Element vorhergesagt werden. In einigen Fällen besteht eine zweiseitige Beziehung zwischen Elementen, was bedeutet, dass sie häufig in der gleichen Transaktion auftreten. Mithilfe der Farblegende am unteren Rand der Registerkarte können Sie die Richtung der Beziehung feststellen.  
  
 Eine Zeile, die zwei Elemente verbindet, zeigt an, dass diese Elemente wahrscheinlich zusammen in einer Transaktion angezeigt werden. Anders ausgedrückt, kaufen Kunden wahrscheinlich beide Elemente. Der Schieberegler ist mit der Wahrscheinlichkeit der Regel verknüpft. Verschieben Sie den Schieberegler nach oben oder unten, um schwache Zuordnungen herauszufilten, das heißt Regeln mit niedriger Wahrscheinlichkeit.  
  
 Das Abhängigkeitsnetzwerkdiagramm zeigt paarweise Regeln an, die logisch als A->B dargestellt werden können: Wenn Produkt A gekauft wird, wird wahrscheinlich auch Produkt B gekauft. Das Diagramm kann keine Regeln des Typs AB->C anzeigen. Wenn Sie den Schieberegler verschieben, um alle Regeln anzuzeigen, jedoch immer noch keine keine Zeilen im Diagramm angezeigt werden, bedeutet dies, dass es keine paarweisen Regeln gibt, die die Kriterien der Algorithmusparameter erfüllen.  
  
 Sie können auch Knoten nach Namen suchen,indem sie die ersten Buchstaben des Attributnamens eingeben. Weitere Informationen finden Sie unter [Dialogfeld "Knoten suchen" &#40;Miningmodell-Viewer&#41;](../../2014/analysis-services/find-node-dialog-box-mining-model-viewer.md).  
  
#### <a name="to-open-the-association-mode-in-the-microsoft-assocaition-rules-viewer"></a>So öffnen Sie den Zuordnungsmodus im Microsoft Association Rules-Viewer  
  
1.  In **Projektmappen-Explorer**, doppelklicken Sie auf die Zuordnungsstruktur.  
  
2.  Klicken Sie im Data Mining-Designer auf die Registerkarte **Miningmodell-Viewer** .  
  
3.  Wählen Sie die Zuordnung aus der Liste der Miningmodelle in der **Miningmodell** Dropdown-Liste.  
  
#### <a name="to-navigate-the-dependency-graph-and-locate-specific-nodes"></a>So navigieren Sie im Abhängigkeitsdiagramm und suchen bestimmte Knoten  
  
1.  In der **Miningmodell-Viewer** Registerkarte, klicken Sie auf die **Abhängigkeitsnetzwerk** Registerkarte.  
  
2.  Klicken Sie auf **vergrößern** mehrere Male auf, bis Sie die Bezeichnungen für jeden Knoten leicht anzeigen können.  
  
     Standardmäßig wird das Diagramm mit allen Knoten angezeigt. In einem komplexen Modell gibt es möglicherweise viele Knoten, sodass die einzelnen Knoten möglicherweise sehr klein angezeigt werden.  
  
3.  Klicken Sie auf die **+** melden Sie in der unteren rechten Ecke des Viewers, und halten Sie die Maustaste gedrückt, um das Diagramm zu schwenken.  
  
4.  Auf der linken Seite des Viewers, ziehen Sie den Schieberegler nach unten, verschieben Sie ihn von **alle Links** (Standard) an das Ende der Schieberegler-Steuerelement.  
  
5.  Der Viewer aktualisiert das Diagramm, sodass jetzt nur die stärkste Zuordnung zwischen den Elementen "Touring Tire" und "Touring Tire Tube" angezeigt wird.  
  
6.  Klicken Sie auf den Knoten mit der Bezeichnung **Touring Tire Tube = Existing**.  
  
     Das Diagramm wird aktualisiert, sodass nur Elemente, die stark mit diesem Element verbunden sind, hervorgehoben werden. Beachten Sie die Richtung des Pfeils zwischen den beiden Elementen.  
  
7.  Ziehen Sie auf der linken Seite des Viewers den Schieberegler wieder nach oben, indem Sie ihn von unten bis etwa zur Mitte verschieben.  
  
     Beachten Sie die Änderungen im Pfeil, der die beiden Elemente verbindet.  
  
8.  Wählen Sie **nur Attributnamen anzeigen** aus der Dropdownliste am oberen Rand der Bereichs "Abhängigkeitsnetzwerk".  
  
     Die Beschriftungen im Diagramm werden aktualisiert, um nur den Modellnamen anzuzeigen.  
  
 [Zurück nach oben](#bkmk_DepNet)  
  
##  <a name="bkmk_Itemsets"></a> Registerkarte "Itemsets"  
 Nun erfahren Sie mehr über die Regeln und die Itemsets, die vom Modell für die Touring Tire- und Touring Tire Tube-Produkte generiert wurden. Die **Itemsets** Registerkarte zeigt drei wichtige Arten von Informationen, die sich auf Itemsets beziehen, die die [!INCLUDE[msCoName](../includes/msconame-md.md)] Association-Algorithmus ermittelt:  
  
-   **Unterstützung:** die Anzahl der Transaktionen, die in der das Itemset auftritt.  
  
-   **Größe:** die Anzahl der Elemente im Itemset.  
  
-   **Konfigurationselemente:** eine Liste der Elemente in jedem Itemset enthalten.  
  
 Abhängig davon, wie die Parameter für den Algorithmus festgelegt werden, generiert der Algorithmus möglicherweise zahlreiche Itemsets. Jedes Itemset, das im Viewer zurückgegeben wird, stellt Transaktionen dar, in denen das Element verkauft wurde. Mithilfe der Steuerelemente am oberen Rand der **Itemsets** Registerkarte Filtern Sie den Viewer, um nur die Itemsets anzuzeigen, die eine angegebene minimalen Unterstützungswert und der angegebenen Größe enthalten.  
  
 Wenn Sie mit einem anderen Miningmodell arbeiten, und es werden keine Itemsets aufgeführt, bedeutet dies, dass keine Itemsets vorhanden sind, die die Kriterien der Algorithmusparameter erfüllen. In einem solchen Szenario können Sie die Algorithmusparameter ändern, um Itemsets zuzulassen, die eine niedrigere Unterstützung haben.  
  
#### <a name="to-filter-the-itemsets-that-are-shown-in-the-viewer-by-name"></a>So filtern Sie die Itemsets, die im Viewer nach Namen angezeigt werden  
  
1.  Klicken Sie auf die **Itemsets** Registerkarte des Viewers.  
  
2.  In der **Filteritemset** geben `Touring Tire`, und klicken Sie dann außerhalb des Felds auf.  
  
     Der Filter gibt alle Elemente zurück, die diese Zeichenfolge enthalten.  
  
3.  In der **anzeigen** Liste **nur Attributnamen anzeigen**.  
  
4.  Wählen Sie die **langen Namen anzeigen** Kontrollkästchen.  
  
     Die Liste der Itemsets wird aktualisiert, um nur die Itemsets anzuzeigen, die die Zeichenfolge "Touring Tire" enthalten. Der lange Name des Itemsets enthält den Namen der Tabelle, die das Attribut und den Wert für jedes Element enthält.  
  
5.  Deaktivieren der **langen Namen anzeigen** Kontrollkästchen.  
  
     Die Liste der Itemsets wird aktualisiert, um nur den kurzen Namen anzuzeigen.  
  
 Die Werte in der **Unterstützung** die Spalte an, die Anzahl der Transaktionen für jedes Itemset. Eine Transaktion für ein Itemset bedeutet einen Kauf, der alle Elemente im Itemset enthält.  
  
 Standardmäßig werden im Viewer die Itemsets in absteigender Reihenfolge nach Unterstützung aufgelistet. Sie können auf die Spaltenheader klicken, um nach einer anderen Spalte zu sortieren, z. B. nach der Größe oder dem Namen des Itemsets. Wenn Sie mehr über die einzelnen Transaktionen erfahren möchten, die in einem Itemset enthalten sind, können Sie einen Drillthrough von den Itemsets zu den einzelnen Fällen ausführen. Die Strukturspalten in den Drillthroughergebnissen sind die Einkommensebene und die Kunden-ID des Kunden. Diese wurden im Modell nicht verwendet.  
  
#### <a name="to-view-details-for-an-itemset"></a>So zeigen Sie Details für ein Itemset an  
  
1.  Klicken Sie in der Liste der Itemsets, auf die **Itemset** Spaltenüberschrift, um nach Namen zu sortieren.  
  
2.  Suchen Sie das Element `Touring Tire` (mit ohne zweites Element).  
  
3.  Mit der rechten Maustaste in des Elements `Touring Tire`Option **Drillthrough**, und wählen Sie dann **Modell- und Strukturspalten**.  
  
     Die **Drillthrough** Dialogfeld zeigt die einzelnen Transaktionen, die als Unterstützung für dieses Itemset verwendet.  
  
4.  Erweitern Sie die geschachtelte Tabelle "vAssocSeqLineItems", um die tatsächliche Liste von Käufen in der Transaktion anzuzeigen.  
  
#### <a name="to-filter-itemsets-by-support-or-size"></a>So filtern Sie Itemsets nach Unterstützung oder Größe  
  
1.  Löschen Sie den Text, die möglicherweise in der **Filteritemset** Feld. Sie können einen Textfilter nicht zusammen mit einem numerischen Filter verwenden.  
  
2.  In der **minimaler Unterstützungswert** Feld, geben Sie 100 ein, und klicken Sie dann auf den Hintergrund des Viewers.  
  
     Die Liste der Itemsets wird aktualisiert, um nur Itemsets mit einer Unterstützung von mindestens 100 anzuzeigen.  
  
 [Zurück nach oben](#bkmk_DepNet)  
  
##  <a name="bkmk_Rules"></a> Registerkarte "Regeln"  
 Die **Regeln** Registerkarte zeigt die folgenden Informationen, die auf die Regeln beziehen, die der Algorithmus ermittelt.  
  
-   **Wahrscheinlichkeit:** der *Wahrscheinlichkeit* einer Regel, definiert als die Wahrscheinlichkeit des rechten Elements das Element der linken Seite angegeben.  
  
-   **Wichtigkeit:** ein Maß für die Nützlichkeit einer Regel. Ein höherer Wert bedeutet eine bessere Regel.  
  
     "Wichtigkeit" wird bereitgestellt, um Ihnen zu helfen, die Nützlichkeit einer Regel zu bewerten, da die Wahrscheinlichkeit alleine irreführend sein kann. Wenn jede Transaktion z. B. eine Flasche Mineralwasser enthält - wenn vielleicht dem Einkaufswagen jedes Kunden als Teil einer Werbeaktion die Flasche automatisch hinzugefügt wird - würde das Modell eine Regel erstellen, die vorhersagt, dass diese Flasche Mineralwasser eine Wahrscheinlichkeit von 1 hat. In Bezug auf die Wahrscheinlichkeit ist diese Regel sehr genau, enthält jedoch keine nützlichen Informationen.  
  
-   **Regel:** die Definition der Regel. Für ein Market Basket-Modell beschreibt eine Regel eine bestimmte Kombination von Elementen.  
  
 Jede Regel kann verwendet werden, um das Vorhandensein eines Elements in einer Transaktion abhängig vom Vorhandensein anderer Elemente vorherzusagen. Ebenso wie der **Itemsets** Registerkarte können Sie die Regeln filtern, sodass nur die interessantesten Regeln angezeigt werden. Wenn Sie mit einem Miningmodell arbeiten, das keine Regeln hat, möchten Sie die Algorithmusparameter möglicherweise ändern, um die Wahrscheinlichkeitsschwelle für Regeln zu senken.  
  
#### <a name="to-see-only-rules-that-include-the-mountain-200-bicycle"></a>So zeigen Sie nur Regeln an, die das Mountain-200-Fahrrad enthalten  
  
1.  In der **Miningmodell-Viewer** Registerkarte, klicken Sie auf die **Regeln** Registerkarte.  
  
2.  In der **Filterregel** geben `Mountain-200`.  
  
     Deaktivieren der **langen Namen anzeigen** Kontrollkästchen.  
  
3.  Aus der **anzeigen** Liste **nur Attributnamen anzeigen**.  
  
     Der Viewer zeigt dann nur die Regeln, die die Wörter "`Mountain-200`". Die Wahrscheinlichkeit der Regel Aufschluss darüber, wie wahrscheinlich es ist, wenn ein Benutzer kauft ein `Mountain-200` Fahrrad, diese Person wird auch das andere aufgelistete Produkt kaufen.  
  
 Die Regeln werden in absteigender Reihenfolge nach ihrer Wahrscheinlichkeit angeordnet, Sie können jedoch auf die Spaltenüberschriften klicken, um die Sortierreihenfolge zu ändern. Wenn Sie mehr über eine bestimmte Regel erfahren möchten, können Sie die unterstützenden Fälle mithilfe eines Drillthroughs anzeigen.  
  
#### <a name="to-view-cases-that-support-a-particular-rule"></a>So zeigen Sie Fälle an, die eine bestimmte Regel unterstützen  
  
1.  In der **Regeln** Registerkarte der rechten Maustaste auf die Regel, die Sie anzeigen möchten.  
  
2.  Wählen Sie **Drillthrough**, und wählen Sie dann **nur Modellspalten**, oder **Modell- und Strukturspalten**.  
  
     Die **Drillthrough** Dialogfeld enthält eine Zusammenfassung der Regel am oberen Rand der und eine Liste aller Fälle, die als unterstützende Daten für die Regel verwendet wurden.  
  
 [Zurück nach oben](#bkmk_DepNet)  
  
##  <a name="bkmk_ContentViewer"></a> Generic Content Tree Viewer  
 Dieser Viewer kann für alle Modelle verwendet werden, unabhängig vom Algorithmus oder Modelltyp. Die **Microsoft Generic Content Tree Viewer** steht über den **Viewer** Dropdown-Liste.  
  
 Eine Inhaltsstruktur ist die Darstellung eines Mining-Modells als eine Reihe von Knoten, in der jeder Knoten das erlangte Wissen über eine Teilmenge der Daten repräsentiert. Der Knoten kann ein Muster, ein Regelsatz, ein Cluster oder die Definition eines Datenbereichs mit gemeinsamen Merkmalen sein. Der genaue Inhalt des Knotens ist je nach Algorithmus und Typ des vorhersagbaren Attributs unterschiedlich, die allgemeine Darstellung des Inhalts ist jedoch gleich. Sie können jeden Knoten erweitern, um zunehmend mehr Details anzuzeigen, und Sie können den Inhalt eines Knotens in die Zwischenablage kopieren.  
  
#### <a name="to-view-details-about-the-rule-by-using-the-content-viewer"></a>So zeigen Sie Details der Regel mittels des Inhalts-Viewer an  
  
1.  In der **Miningmodell-Viewer** Registerkarte **Microsoft Generic Content Tree Viewer** aus der **Viewer** Liste.  
  
2.  Führen Sie im Bereich "Knotenbeschriftung" einen Bildlauf nach unten durch, und klicken Sie auf den letzten Knoten.  
  
     Der Viewer zeigt zuerst Itemsets und dann Regeln an, gruppiert diese jedoch nicht. Die einfachste Art, einen bestimmten Knoten zu finden, besteht in der Erstellung einer Inhaltsabfrage. Weitere Informationen finden Sie unter [Beispiele für Zuordnungsmodellabfragen](../../2014/analysis-services/data-mining/association-model-query-examples.md).  
  
3.  Überprüfen Sie im Bereich "Knotendetails" den Wert für NODE_TYPE und NODE_DESCRIPTION.  
  
     Ein Knotentyp von 8 ist eine Regel, und ein Knotentyp von 7 ist ein Itemset. Im Fall einer Regel nennt der Wert von NODE_DESCRIPTION Ihnen die Bedingungen, die die Regel bilden. Im Fall eines Itemsets nennt Ihnen der Wert von NODE_DESCRIPTION die im Itemset enthaltenen Elemente.  
  
 Sie können auch eine Inhaltsabfrage erstellen, um ausführliche Statistiken zu den Regeln abzurufen. Weitere Informationen über miningmodellinhalte und deren Interpretation finden Sie unter [Miningmodellinhalt für Zuordnungsmodelle &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md).  
  
 [Zurück nach oben](#bkmk_DepNet)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Filtern einer geschachtelten Tabelle in einem Miningmodell &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Lektion 3: Erstellen eines Warenkorbszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)   
 [Lektion 4: Erstellen eines Sequenzclusterszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)   
 [Microsoft Association-Algorithmus](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)   
 [Technische Referenz für den Microsoft Association-Algorithmus](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)  
  
  