---
title: Microsoft Decision Trees-Algorithmus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- predictions [Analysis Services], discrete attributes
- predictions [Analysis Services], continuous attributes
- algorithms [data mining]
- discrete attributes [Analysis Services]
- classification algorithms [Analysis Services]
- discrete columns [Analysis Services]
- decision tree algorithms [Analysis Services]
- decision trees [Analysis Services]
- continuous columns
- regression algorithms [Analysis Services]
ms.assetid: 95ffe66f-c261-4dc5-ad57-14d2d73205ff
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7a9adfe74aef16e475d06eddfbe08852f7618518
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66084104"
---
# <a name="microsoft-decision-trees-algorithm"></a>Microsoft Decision Trees-Algorithmus
  Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus ist eine Klassifizierung und Regression-Algorithmus, die von bereitgestellten [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] für die Verwendung bei der vorhersagemodellierung von diskreten und kontinuierlichen Attributen.  
  
 Bei diskreten Attributen gründet der Algorithmus seine Vorhersagen auf die Beziehungen zwischen den Eingabespalten in einem Dataset Er verwendet die Werte oder Zustände aus diesen Spalten zur Vorhersage der Zustände einer von Ihnen als vorhersagbar bestimmten Spalte. Dabei identifiziert der Algorithmus die Eingabespalten, die von der vorhersagbaren Spalte abhängig sind. Wenn z. B. in einem Szenario zur Vorhersage der wahrscheinlichen Käufer eines Fahrrads neun von zehn jüngeren Kunden ein Fahrrad kaufen, dies jedoch nur bei zwei von zehn älteren Kunden zutrifft, folgert der Algorithmus daraus, dass das Alter ein gutes Vorhersagekriterium für den Fahrradkauf ist. Die von der Entscheidungsstruktur getroffenen Vorhersagen gründen auf dieser Tendenz hinsichtlich eines bestimmten Ergebnisses.  
  
 Bei kontinuierlichen Attributen bestimmt der Algorithmus anhand einer linearen Regression, wo sich die Entscheidungsstruktur teilt.  
  
 Wenn mehr als eine Spalte als vorhersagbar festgelegt ist, oder wenn die Eingabedaten eine als vorhersagbar festgelegte geschachtelte Tabelle enthalten, bildet der Algorithmus für jede vorhersagbare Spalte eine eigene Entscheidungsstruktur.  
  
## <a name="example"></a>Beispiel  
 Die Marketingabteilung der Firma [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] möchte die Merkmale früherer Kunden identifizieren, anhand derer sich die Wahrscheinlichkeit ermitteln lässt, mit der diese Kunden künftig als Käufer eines Produkts in Frage kommen. In der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] -Datenbank sind die demografischen Daten zur Beschreibung früherer Kunden gespeichert. Mithilfe des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus zur Analyse dieser Informationen kann die Marketingabteilung ein Vorhersagemodell entwickeln. Dieses Modell besagt, ob ein bestimmter Kunde als künftiger Käufer von Produkten in Frage kommt, wobei sich das Modell auf die Zustände bekannter Spalten zu diesem Kunden, wie z. B. demografische Muster oder frühere Kaufverhaltensmuster, stützt.  
  
## <a name="how-the-algorithm-works"></a>Funktionsweise des Algorithmus  
 Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus erstellt eine Reihe von Teilungen in der Entscheidungsstruktur, die zusammen ein Data Mining-Modell bilden. Diese Teilungen werden als *Knoten*dargestellt. Der Algorithmus fügt dem Modell jedes Mal einen Knoten hinzu, wenn eine Eingabespalte in erheblichem Ausmaß von der vorhersagbaren Spalte abhängig ist. Wie der Algorithmus eine Teilung bestimmt, unterscheidet sich danach, ob er eine Vorhersage zu einer kontinuierlichen Spalte oder zu einer diskreten Spalte trifft.  
  
 Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus verwendet die *Funktionsauswahl* als Rahmen für die Auswahl der nützlichsten Attribute. Die Funktionsauswahl wird von allen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Data Mining-Algorithmen zur Verbesserung der Leistung und der Analysequalität verwendet. Mit der Funktionsauswahl wird vermieden, dass unwichtige Attribute Prozessorzeit belegen. Wenn Sie beim Entwurf eines Data Mining-Modells zu viele Eingabe- und vorhersagbare Attribute verwenden, dauert die Verarbeitung des Modells u. U. sehr lange oder übersteigt sogar den vorhandenen Speicherplatz. Unter den Methoden zur Ermittlung, ob die Struktur geteilt werden sollte, gehören Metriken nach Industriestandard für *Entropie*- und Bayes-Netzwerke *.* Weitere Informationen zu den Methoden zur Auswahl nützlicher Attribute und zur Festlegung der Interessantheit und Rangfolge dieser finden Sie unter [Funktionsauswahl &#40;Data Mining&#41;](feature-selection-data-mining.md).  
  
 Ein häufiges Problem bei Datamining-Modellen ist, dass das Modell auf kleinen Unterschieden in den Trainingsdaten festgelegt wird, die in diesem Fall wird als *stark angepasst* oder *überladen*. Ein überangepasstes Modell kann nicht zu anderen Datasets verallgemeinert werden. Um die Überanpassung an ein bestimmtes Dataset zu vermeiden, verwendet der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus Techniken zur Steuerung des Strukturwachstums. Eine nähere Erläuterung zur Funktionsweise des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus finden Sie unter [Technische Referenz für den Microsoft Decision Trees-Algorithmus](microsoft-decision-trees-algorithm-technical-reference.md).  
  
### <a name="predicting-discrete-columns"></a>Vorhersagen diskreter Spalten  
 Auf welche Weise [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus eine Struktur für eine diskrete vorhersagbare Spalte erstellt, lässt sich anhand eines Histogramms verdeutlichen. Im folgenden Diagramm ist ein Histogramm abgebildet, in dem die vorhersagbare Spalte Bike Buyers (Fahrradkäufer) mit der Eingabespalte Age (Alter) abgeglichen wird. Aus dem Histogramm geht hervor, dass das Alter einer Person Rückschlüsse darauf zulässt, ob diese Person ein Fahrrad kaufen wird.  
  
 ![Histogramm aus Microsoft Decision Trees-Algorithmus](../media/dt-histogram.gif "Histogramm aus Microsoft Decision Trees-Algorithmus")  
  
 Die im Diagramm veranschaulichte Korrelation würde dazu führen, dass der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus einen neuen Knoten im Modell erstellt.  
  
 ![Entscheidungsstrukturknoten](../media/dt-tree.gif "entscheidungsstrukturknoten")  
  
 Durch das Hinzufügen neuer Knoten zu einem Modell bildet der Algorithmus eine Baumstruktur. Der oberste Knoten der Struktur beschreibt, wie sich die vorhersagbare Spalte für die Gesamtpopulation der Kunden unterteilt. Beim Anwachsen des Modells werden nach und nach alle Spalten vom Algorithmus einbezogen.  
  
### <a name="predicting-continuous-columns"></a>Vorhersagen kontinuierlicher Spalten  
 Bei Entscheidungsstrukturen, die der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus anhand einer kontinuierlichen vorhersagbaren Spalte erstellt, enthält jeder Knoten eine Regressionsformel. Teilungen finden an Stellen der Nichtlinearität in der Regressionsformel statt. Betrachten Sie beispielsweise das folgende Diagramm.  
  
 ![Mehrfachregression Zeilen mit Nichtlinearität](../media/regression-tree1.gif "mehrfachregression Zeilen mit Nichtlinearität")  
  
 Das Diagramm enthält Daten, die sowohl durch eine einzelne Linie als auch durch zwei verbundene Linien dargestellt werden können. Eine einzelne Linie würde die Daten jedoch nur unzureichend wiedergeben. Wenn Sie stattdessen zwei Linien verwenden, lassen sich die Daten im Modell wesentlich besser darstellen. Die Stelle, an der die beiden Linien zusammentreffen, ist die Stelle der Nichtlinearität und damit die Stelle, an der sich ein Knoten im Entscheidungsstrukturmodell teilen würde. So könnte beispielsweise der Knoten, der der Stelle der Nichtlinearität im obigen Graphen entspricht, durch folgendes Diagramm dargestellt werden. Die beiden Gleichungen stellen die Regressionsgleichungen der beiden Linien dar.  
  
 ![Formel, die einen Punkt der Nichtlinearität darstellt](../media/regression-tree2.gif "Gleichung, die einen Punkt der Nichtlinearität darstellt.")  
  
## <a name="data-required-for-decision-tree-models"></a>Erforderliche Daten für Entscheidungsstrukturmodelle  
 Wenn Sie Daten für die Verwendung in einem Entscheidungsstrukturmodell aufbereiten, müssen Sie sich mit den Anforderungen des jeweiligen Algorithmus, dessen Anforderungen an die Daten und der Verwendung der Daten vertraut machen.  
  
 Für Entscheidungsstrukturmodelle gelten folgende Anforderungen:  
  
-   **Nur eine Schlüsselspalte:** Jedes Modell muss eine numerische Spalte oder Textspalte enthalten, die jeden Datensatz eindeutig identifiziert. Verbundschlüssel sind nicht zulässig.  
  
-   **Eine vorhersagbare Spalte** Mindestens eine vorhersagbare Spalte ist erforderlich. Sie können mehrere vorhersagbare Attribute in ein Modell aufnehmen, die numerisch oder diskret sein müssen. Beachten Sie jedoch, dass sich mit steigender Anzahl an vorhersagbaren Attributen die Verarbeitungszeit erhöhen kann.  
  
-   **Eingabespalten** Eingabespalten sind erforderlich und können diskret oder kontinuierlich sein. Auch hier gilt, dass sich bei steigender Anzahl an Attributen die Verarbeitungszeit erhöht.  
  
 Detaillierte Informationen zu den in Entscheidungsstrukturmodellen unterstützten Inhaltstypen und Datentypen finden Sie im Abschnitt „Anforderungen“ unter [Technische Referenz für den Microsoft Decision Trees-Algorithmus](microsoft-decision-trees-algorithm-technical-reference.md).  
  
## <a name="viewing-a-decision-trees-model"></a>Anzeigen eines Entscheidungsstrukturmodells  
 Mit dem **Microsoft Struktur-Viewer**können Sie das Modell anzeigen. Wenn das Modell mehrere Strukturen generiert, wählen Sie eine Struktur aus. Daraufhin wird im Viewer eine Aufschlüsselung der Fallkategorien für jedes vorhersagbare Attribut angezeigt. Mit dem Abhängigkeitsnetzwerk-Viewer können Sie die Abhängigkeiten zwischen den Strukturen anzeigen. Weitere Informationen finden Sie unter [Durchsuchen eines Modells mit dem Microsoft Struktur-Viewer](browse-a-model-using-the-microsoft-tree-viewer.md).  
  
 Wenn Sie Näheres über die Verzweigungen bzw. Knoten in der Struktur in Erfahrung bringen möchten, können Sie das Modell im [Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)durchsuchen. Der für das Modell gespeicherte Inhalt umfasst die Verteilung der Werte an jedem Knoten, die Wahrscheinlichkeiten auf jeder Strukturebene und die Regressionsformeln für kontinuierliche Attribute. Weitere Informationen finden Sie unter [Miningmodellinhalt von Entscheidungsstrukturmodellen &#40;Analysis Services – Data Mining&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md).  
  
## <a name="creating-predictions"></a>Erstellen von Vorhersagen  
 Nachdem das Modell verarbeitet wurde, werden die Ergebnisse als Satz von Mustern und Statistiken gespeichert, die Sie zum Untersuchen von Beziehungen bzw. zum Erstellen von Vorhersagen verwenden können.  
  
 Beispiele zur Verwendung von Abfragen in Verbindung mit einem Entscheidungsstrukturmodell finden Sie unter [Beispiele für Entscheidungsstruktur-Modellabfragen](decision-trees-model-query-examples.md).  
  
 Allgemeine Informationen zum Erstellen von Abfragen für Miningmodelle finden Sie unter [Data Mining-Abfragen](data-mining-queries.md).  
  
## <a name="remarks"></a>Hinweise  
  
-   Unterstützt die Verwendung von PMML (Predictive Model Markup Language) zum Erstellen von Miningmodellen.  
  
-   Unterstützt Drillthrough.  
  
-   Unterstützt die Verwendung von OLAP-Miningmodellen und die Erstellung von Data Mining-Dimensionen.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Technische Referenz für den Microsoft Decision Trees-Algorithmus](microsoft-decision-trees-algorithm-technical-reference.md)   
 [Beispiele für Entscheidungsstruktur-Modellabfragen](decision-trees-model-query-examples.md)   
 [Miningmodellinhalt von Entscheidungsstrukturmodellen &#40;Analysis Services – Data Mining&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)  
  
  
