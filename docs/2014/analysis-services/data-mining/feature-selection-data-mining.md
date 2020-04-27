---
title: Funktionsauswahl (Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], feature selections
- attributes [data mining]
- feature selection algorithms [Analysis Services]
- data mining [Analysis Services], feature selections
- neural network algorithms [Analysis Services]
- naive bayes algorithms [Analysis Services]
- decision tree algorithms [Analysis Services]
- datasets [Analysis Services]
- clustering algorithms [Analysis Services]
- coding [Data Mining]
ms.assetid: b044e785-4875-45ab-8ae4-cd3b4e3033bb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a1d79bb3810a56e8a1769845131312eab306f223
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66084414"
---
# <a name="feature-selection-data-mining"></a>Funktionsauswahl (Data Mining)
  Die *Featureauswahl* ist ein Begriff, der in Data Mining häufig verwendet wird, um die Tools und Techniken zu beschreiben, die für die Reduzierung von Eingaben auf eine verwaltbare Größe für die Verarbeitung Die Featureauswahl impliziert nicht nur die *kardinalitätsreduzierung*. Dies bedeutet, dass ein beliebiges oder vordefiniertes Umstellungs Verhalten für die Anzahl der Attribute, die bei der Erstellung eines Modells berücksichtigt werden können, auferlegt wird, aber auch die Auswahl der Attribute, d. h., dass der Analyst oder das Modellierungs Tool basierend auf der Nützlichkeit der Analyse aktiv Attribute auswählt  
  
 Die Möglichkeit, eine Funktionsauswahl anzuwenden, ist wichtig für eine effiziente Analyse, da Datasets häufig wesentlich mehr Informationen enthalten, als für die Modellerstellung erforderlich ist. Ein Dataset kann z. B. 500 Spalten mit Kundenmerkmalen enthalten. Wenn die Daten in einigen Spalten jedoch nur einen geringen Informationswert haben, würden diese Spalten, wenn sie dem Modell hinzugefügt würden, nur einen sehr geringen Nutzen bringen. Wenn Sie die nicht verwendeten Spalten beim Erstellen des Modells beibehalten, ist während des Trainingsprozesses mehr CPU und Arbeitsspeicher erforderlich, und das fertige Modell erfordert mehr Speicherplatz.  
  
 Auch wenn die Ressourcen kein Problem sind, empfiehlt es sich, nicht verwendete Spalten zu entfernen, da sie die Qualität der erkannten Muster aus folgenden Gründen beeinträchtigen können:  
  
-   Manche Spalten enthalten stark abweichende oder redundante Werte. Dies erschwert es, in den Daten sinnvolle Muster zu erkennen.  
  
-   Zur Erkennung qualitativ hochwertiger Muster benötigen die meisten Data Mining-Algorithmen ein viel größeres Trainingsdataset für mehrdimensionale Datasets. In einigen Data Mining-Anwendungen ist das Trainingsdataset jedoch sehr klein.  
  
 Wenn von den 500 Spalten in der Datenquelle nur 50 Spalten Informationen enthalten, die bei der Modellerstellung von Nutzen sind, könnten Sie sie einfach nicht in das Modell einbeziehen. Alternativ könnten Sie mithilfe der Funktionsauswahl automatisch die besten Funktionen ermitteln und Werte ausschließen, die statistisch unbedeutend sind. Die Funktionsauswahl ist hilfreich bei der Lösung des doppelten Problems, dass zu viele Daten mit geringem Wert oder zu wenige hochwertige Daten vorhanden sind.  
  
## <a name="feature-selection-in-analysis-services-data-mining"></a>Die Funktionsauswahl bei Analysis Services Data Mining  
 Normalerweise wird die Funktionsauswahl in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] automatisch ausgeführt. Jeder Algorithmus verfügt über eine Reihe von Standardtechniken für die intelligente Anwendung der Funktionsreduzierung. Die Funktionsauswahl wird stets durchgeführt, bevor das Modell trainiert wird, um automatisch die Attribute in einem Dataset auszuwählen, die im Modell am wahrscheinlichsten Verwendung finden. Sie können jedoch auch manuell Parameter festlegen, um das Verhalten der Funktionsauswahl zu beeinflussen.  
  
 Im Allgemeinen wird bei der Funktionsauswahl ein Wert für jedes Attribut berechnet, und dann werden nur diejenigen Attribute ausgewählt, die über die besten Werte verfügen. Sie können den Schwellenwert für die besten Ergebnisse auch anpassen. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bietet mehrere Methoden zum Berechnen dieser Ergebnisse. Welche spezifische Methode auf das jeweilige Modell angewendet wird, hängt von folgenden Faktoren ab:  
  
-   Im Modell verwendeter Algorithmus  
  
-   Datentyp des Attributs  
  
-   Für das Modell festgelegte Parameter  
  
 Die Funktionsauswahl wird auf Eingaben, vorhersagbare Attribute und Statuswerte in einer Spalte angewandt. Nachdem die Bewertung für die Funktionsauswahl abgeschlossen ist, werden nur die vom Algorithmus ausgewählten Attribute und Statusangaben bei der Modellerstellung berücksichtigt und für Vorhersagen zur Verfügung gestellt. Bei Auswahl eines vorhersagbaren Attributs, das den Schwellenwert für die Funktionsauswahl nicht erfüllt, kann das Attribut zwar trotzdem für die Vorhersage verwendet werden, in diesem Fall basieren die Vorhersagen jedoch ausschließlich auf den globalen, im Modell vorhandenen Statistiken.  
  
> [!NOTE]  
>  Die Funktionsauswahl betrifft nur die Spalten, die im Modell verwendet werden, und wirkt sich nicht auf die Speicherung der Miningstruktur aus. Die Spalten, die nicht in das Miningmodell aufgenommen werden, sind in der Struktur weiterhin verfügbar, und die Daten der Miningstrukturspalten werden zwischengespeichert.  
  
### <a name="definition-of-feature-selection-methods"></a>Definition von Funktionsauswahlmethoden  
 Abhängig vom Typ der Daten, mit denen Sie arbeiten, und dem für die Analyse gewählten Algorithmus, kann die Funktionsauswahl auf vielerlei Weise implementiert werden. SQL Server Analysis Services stellt mehrere gängige und bekannte Methoden zum Bewerten von Attributen bereit. Die Methode, die bei Algorithmen oder Datasets angewendet wird, hängt von den Datentypen und der Spaltenverwendung ab.  
  
 Die Bewertung des *Interessantheitsgrads* wird zum Festlegen der Rangfolge und zum Sortieren von Attributen in Spalten verwendet, die nicht binäre, kontinuierliche, numerische Daten enthalten.  
  
 Für Spalten, die diskrete und diskretisierte Daten enthalten, sind die*Shannon-Entropie* und zwei *Bayes* -Werte verfügbar. Wenn das Modell jedoch kontinuierliche Spalten enthält, wird der Interessantheitsgrad zur Bewertung aller Eingabespalten herangezogen, um die Konsistenz sicherzustellen.  
  
 Im folgenden Abschnitt werden die Methoden der Funktionsauswahl einzeln beschrieben.  
  
#### <a name="interestingness-score"></a>Interessantheitsgrad  
 Eine Funktion ist interessant, wenn sie eine nützliche Information offenbart. Da die Definition der nützlichen variiert, hängt vom jeweiligen Szenario ab. die Data Mining Branche hat verschiedene Möglichkeiten zum Messen der *Interessantheit*entwickelt. Beispielsweise könnte die *Neuheit* bei der Ausreißererkennung interessant sein, aber die Möglichkeit zur Unterscheidung zwischen eng verknüpften Elementen oder der *Gewichtungs Gewichtung*kann für die Klassifizierung interessanter sein.  
  
 Das in SQL Server Analysis Services verwendete Maß für Interessantheit ist *Entropie basiert*, d. h., dass Attribute mit zufälligen Verteilungen eine höhere Entropie und einen geringeren Informationsgewinn aufweisen. Daher sind solche Attribute weniger interessant. Die Entropie eines bestimmten Attributs wird wie folgt mit der Entropie aller anderen Attribute verglichen:  
  
 Interessantheit(Attribut) = - (m - Entropie(Attribut)) * (m - Entropie(Attribut))  
  
 Die zentrale Entropie oder m steht für die Entropie des gesamten Featuresatzes. Durch Abziehen der Entropie des Zielattributs von der zentralen Entropie lässt sich einschätzen, wie viele Informationen das Attribut bereitstellt.  
  
 Dieses Ergebnis wird standardmäßig immer dann verwendet, wenn die Spalte nicht binäre, kontinuierliche, numerische Daten enthält.  
  
#### <a name="shannons-entropy"></a>Shannon-Entropie  
 Die Shannon-Entropie stellt ein Maß für die Ungewissheit einer zufälligen Variable für ein bestimmtes Ergebnis dar. Beispielsweise kann die Entropie einen Münzwurfs als Funktion der Wahrscheinlichkeit des Ergebnisses "Kopf" dargestellt werden.  
  
 In Analysis Services wird die folgende Formel zur Berechnung der Shannon-Entropie verwendet:  
  
 H(X) = -∑ P(xi) log(P(xi))  
  
 Diese Bewertungsmethode ist für diskrete und diskretisierte Attribute verfügbar.  
  
#### <a name="bayesian-with-k2-prior"></a>Bayes-Methode mit K2-A-priori-Verteilung  
 Analysis Services stellt zwei Funktionsauswahlwerte bereit, die auf Bayes-Netzwerken basieren. Ein Bayes-Netzwerk ist ein *gerichteter* oder *azyklischer* Graph von Zuständen und Übergängen zwischen Zuständen. Das heißt, dass einige Zustände immer vor dem aktuellen Status liegen, andere Zustände sind nachgelagert, und der Graph stellt keine Wiederholungen oder Schleifen dar. Definitionsgemäß ermöglichen Bayes-Netzwerke die Verwendung vorherigen Wissens. Allerdings ist die Frage, welche der früheren Zustände zur Berechnung der Wahrscheinlichkeit nachfolgender Zustände verwendet werden sollen, für den Algorithmusentwurf, die Leistung und die Genauigkeit wichtig.  
  
 Der K2-Algorithmus zum Lernen von Bayes-Netzwerken wurde von Cooper und Herskovits entwickelt und wird häufig im Data Mining eingesetzt. Er ist skalierbar und kann mehrere Variablen analysieren, erfordert jedoch eine Sortierung der als Eingabe verwendeten Variablen. Weitere Informationen finden Sie in [Learning Bayesian Networks](https://go.microsoft.com/fwlink/?LinkId=105885) von Chickering, Geiger, und Heckerman.  
  
 Diese Bewertungsmethode ist für diskrete und diskretisierte Attribute verfügbar.  
  
#### <a name="bayesian-dirichlet-equivalent-with-uniform-prior"></a>Bayes-Dirichlet-Äquivalent mit uniformer A-priori-Verteilung  
 Bei der Bayes-Dirichlet-Äquivalent-Bewertung wird auch die Bayes-Analyse zur Bewertung eines Netzwerks anhand eines gegebenen Datasets verwendet. Diese Bewertungsmethode wurde von Heckerman entwickelt und basiert auf der von Cooper und Herskovits entwickelten BD-Metrik. Bei der Dirichlet-Verteilung handelt es sich um eine Multinominalverteilung, die die bedingte Wahrscheinlichkeit jeder Netzwerkvariablen beschreibt und über viele für das Lernen nützliche Eigenschaften verfügt.  
  
 Die Methode Bayes-Dirichlet-Äquivalent mit uniformer A-priori-Verteilung setzt einen Sonderfall der Dirichlet-Verteilung voraus, in dem eine mathematische Konstante zur Erstellung einer festen oder einheitlichen Verteilung von A-priori-Zuständen verwendet wird. Die Bayes-Dirichlet-Äquivalent-Bewertung unterstellt außerdem Likelihood-Äquivalenz, d. h. es wird nicht erwartet, dass die Daten äquivalente Strukturen unterscheiden können. Anders ausgedrückt bedeutet dies, wenn der Score von „Wenn A dann B“ dem Score von „Wenn B dann A“ entspricht, dann lassen sich die Strukturen nicht anhand der Daten unterscheiden, und die Kausalität kann nicht aus den Daten gefolgert werden.  
  
 Weitere Informationen zu Bayes-Netzwerken und der Implementierung dieser Bewertungsmethoden finden Sie in [Learning Bayesian Networks](https://go.microsoft.com/fwlink/?LinkId=105885).  
  
### <a name="feature-selection-methods-used-by-analysis-services-algorithms"></a>Von Analysis Services-Algorithmen verwendete Funktionsauswahlmethoden  
 Die folgende Tabelle enthält die Algorithmen, welche die Funktionsauswahl unterstützen, die von einem Algorithmus verwendeten Funktionsauswahlmethoden und die Parameter, mit denen sich das Funktionsauswahlverhalten steuern lässt:  
  
|Algorithmus|Analysemethode|Kommentare|  
|---------------|------------------------|--------------|  
|Naive Bayes|Shannon-Entropie<br /><br /> Bayes-Methode mit K2-A-priori-Verteilung<br /><br /> Bayes-Dirichlet mit uniformer A-priori-Verteilung (Standard)|Der Microsoft Naive Bayes-Algorithmus akzeptiert nur diskrete oder diskretisierte Attribute, daher kann er den Interessantheitsgrad nicht verwenden.<br /><br /> Weitere Informationen zu diesem Algorithmus finden Sie unter [Microsoft Naive Bayes Algorithm Technical Reference](microsoft-naive-bayes-algorithm-technical-reference.md).|  
|Entscheidungsstrukturen|Interessantheitsgrad<br /><br /> Shannon-Entropie<br /><br /> Bayes-Methode mit K2-A-priori-Verteilung<br /><br /> Bayes-Dirichlet mit uniformer A-priori-Verteilung (Standard)|Wenn irgendeine Spalte nicht binäre kontinuierliche Werte enthält, wird der Interessantheitsgrad für alle Spalten verwendet, um die Konsistenz zu gewährleisten. Andernfalls wird die StandardFunktionsauswahlmethode oder die Methode angewendet, die Sie angegeben haben, als Sie das Modell erstellt haben.<br /><br /> Weitere Informationen zu diesem Algorithmus finden Sie unter [Microsoft Decision Trees Algorithm Technical Reference](microsoft-decision-trees-algorithm-technical-reference.md).|  
|Neuronales Netzwerk|Interessantheitsgrad<br /><br /> Shannon-Entropie<br /><br /> Bayes-Methode mit K2-A-priori-Verteilung<br /><br /> Bayes-Dirichlet mit uniformer A-priori-Verteilung (Standard)|Der Microsoft Neural Networks-Algorithmus kann sowohl die Bayes- als auch die Entropie-basierte Methode verwenden, sofern die Daten kontinuierliche Spalten enthalten.<br /><br /> Weitere Informationen zu diesem Algorithmus finden Sie unter [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md).|  
|Logistische Regression|Interessantheitsgrad<br /><br /> Shannon-Entropie<br /><br /> Bayes-Methode mit K2-A-priori-Verteilung<br /><br /> Bayes-Dirichlet mit uniformer A-priori-Verteilung (Standard)|Obwohl der Microsoft Logistic Regression-Algorithmus auf dem Microsoft Neural Network-Algorithmus basiert, können Sie keine logistischen Regressionsmodelle anpassen, um das Funktionsauswahlverhalten zu steuern. Deshalb wird die Funktionsauswahl immer standardmäßig nach der Methode ausgeführt, die für das Attribut am besten geeignet ist.<br /><br /> Wenn alle Attribute diskret oder diskretisiert sind, wird als Standardmethode Bayes-Dirichlet mit uniformer A-priori-Verteilung eingesetzt.<br /><br /> Weitere Informationen zu diesem Algorithmus finden Sie unter [Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md).|  
|Clustering|Interessantheitsgrad|Der Microsoft Clustering-Algorithmus kann diskrete oder diskretisierte Daten verwenden. Da das Ergebnis jedes Attributs jedoch als Entfernung berechnet wird und als kontinuierliche Zahl dargestellt wird, muss der Interessantheitsgrad verwendet werden.<br /><br /> Weitere Informationen zu diesem Algorithmus finden Sie unter [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md).|  
|Lineare Regression|Interessantheitsgrad|Der Microsoft Linear Regression-Algorithmus kann nur den Interessantheitsgrad verwenden, da dieser nur kontinuierliche Spalten unterstützt.<br /><br /> Weitere Informationen zu diesem Algorithmus finden Sie unter [Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md).|  
|Zuordnungsregeln<br /><br /> Sequenzclustering|Nicht verwendet|Die Funktionsauswahl wird nicht mit diesen Algorithmen aufgerufen.<br /><br /> Durch Festlegen der Parameter MINIMUM_SUPPORT und MINIMUM_PROBABILIITY lässt sich jedoch das Verhalten des Algorithmus steuern und die Größe der Eingabedaten falls notwendig reduzieren.<br /><br /> Weitere Informationen finden Sie unter [Microsoft Association Algorithm Technical Reference](microsoft-association-algorithm-technical-reference.md) und [Microsoft Sequence Clustering Algorithm Technical Reference](microsoft-sequence-clustering-algorithm-technical-reference.md).|  
|Zeitreihe|Nicht verwendet|Die Funktionsauswahl gilt nicht für Zeitreihenmodelle.<br /><br /> Weitere Informationen zu diesem Algorithmus finden Sie unter [Microsoft Time Series Algorithm Technical Reference](microsoft-time-series-algorithm-technical-reference.md).|  
  
## <a name="feature-selection-parameters"></a>Parameter für die Funktionsauswahl  
 In Algorithmen, die die Funktionsauswahl unterstützen, können Sie mithilfe der folgenden Parameter steuern, wann die Funktionsauswahl aktiviert wird. Jeder Algorithmus verfügt über einen Standardwert für die Anzahl zulässiger Eingaben, Sie können diesen Standardwert jedoch überschreiben und die Anzahl der Attribute angeben. In diesem Abschnitt sind die Parameter zur Verwaltung der Funktionsauswahl aufgeführt.  
  
#### <a name="maximum_input_attributes"></a>MAXIMUM_INPUT_ATTRIBUTES  
 Falls ein Modell mehr Spalten enthält als durch die im *MAXIMUM_INPUT_ATTRIBUTES* -Parameter angegebene Zahl, ignoriert der Algorithmus alle Spalten, die er als irrelevant errechnet.  
  
#### <a name="maximum_output_attributes"></a>MAXIMUM_OUTPUT_ATTRIBUTES  
 Entsprechend gilt: Falls ein Modell mehr vorhersagbare Spalten enthält als durch die im *MAXIMUM_OUTPUT_ATTRIBUTES* -Parameter angegebene Zahl, ignoriert der Algorithmus gleichermaßen alle Spalten, die er als irrelevant errechnet.  
  
#### <a name="maximum_states"></a>MAXIMUM_STATES  
 Wenn ein Modell mehr Fälle enthält, als im *MAXIMUM_STATES* -Parameter angegeben sind, werden die am wenigsten verbreiteten Status in einer Gruppe zusammengefasst und als fehlend behandelt. Wird einer dieser Parameter auf 0 festgelegt, ist die Funktionsauswahl ausgeschaltet. Dies wirkt sich auf die Verarbeitungszeit und die Leistung aus.  
  
 Neben diesen Methoden für die Funktionsauswahl können Sie den Algorithmus bei der Identifizierung oder Heraufstufung aussagekräftiger Attribute unterstützen, indem Sie *Modellierungsflags* für das Modell oder *Verteilungsflags* für die Struktur festlegen. Weitere Informationen zu diesen Konzepten finden Sie unter [Modellierungsflags &#40;Data Mining&#41;](modeling-flags-data-mining.md) und [Spaltenverteilungen &#40;Data Mining&#41;](column-distributions-data-mining.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anpassen von Miningmodellen und -strukturen](customize-mining-models-and-structure.md)  
  
  
