---
title: Algorithmusparameter (SQL Server Data Mining-Add-ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MAXIMUM_STATES
- FORCED_REGRESSOR
- PERIODICITY_HINT
- HOLDOUT_SEED
- MAXIMUM_ITEMSET_SIZE
- HIDDEN_NODE_RATIO
- CLUSTERING_METHOD
- FORECAST_METHOD
- STOPPING_TOLERANCE
- MISSING_VALUE_SUBSTITUTION
- MINIMUM_IMPORTANCE
- HISTORIC_MODEL_COUNT
- SPLIT_METHOD
- MAXIMUM_OUTPUT_ATTRIBUTES
- HOLDOUT_PERCENTAGE
- MINIMUM_PROBABILITY
- SAMPLE_SIZE
- HISTORICAL_MODEL_GAP
- CLUSTER_SEED
- SCORE_METHOD
- INSTABILITY_SENSITIVITY
- AUTO_DETECT_PERIODICITY
- MAXIMUM_SEQUENCE_STATES
- MINIMUM_DEPENDENCY_PROBABILITY
- MINIMUM_SUPPORT
- MAXIMUM_SUPPORT
- MINIMUM_ITEMSET_SIZE
- PREDICTION_SMOOTHING
- algorithm parameters
- MAXIMUM_SERIES_VALUE
- MODELLING_CARDINALITY
- MAXIMUM_INPUT_ATTRIBUTES
- MINIMUM_SERIES_VALUE
- MAXIMUM_ITEMSET_COUNT
- CLUSTER_COUNT
- COMPLEXITY_PENALTY
ms.assetid: fcdc3f85-813d-4279-90b0-16e26edd008d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e902272c58f1e841a3108199e53d51ac12f8ae4a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66062601"
---
# <a name="algorithm-parameters-sql-server-data-mining-add-ins"></a>Algorithmusparameter (SQL Server Data Mining-Add-Ins)
  Wenn Sie Data Mining mithilfe der Tabellenanalysetools für Excel durchführen, ist das Konfigurieren des Data Mining-Algorithmus oder der Data Mining-Parameter nicht erforderlich, da die Tools die Daten automatisch analysieren und die optimalen Parameter festlegen. Wenn Sie jedoch das Modell ändern oder ein ganz neues Miningmodell erstellen möchten, können Sie mit dem Data Mining-Client verschiedene Anpassungen vornehmen.  
  
-   Datamining-Modell manuell erstellen, indem Sie auf **erweitert** , und klicken Sie dann auf **Modell einer Struktur hinzufügen**.  
  
-   Verwenden Sie einen der modellierungsassistenten im Data Mining-Client, und klicken Sie auf **Parameter** zur Steuerung des Verhaltens von der [!INCLUDE[msCoName](../includes/msconame-md.md)] Datamining-Algorithmen.  
  
-   Klicken Sie auf **Abfrage** den Abfragemodell-Assistenten zu öffnen, und klicken Sie dann auf **erweitert** zum Öffnen der **erweiterten Data Mining Query Editor**. In diesem Editor können Sie Modelle anhand von DMX-Vorlagen erstellen.  
  
 Sie können auch das Verhalten bereits erstellter Miningmodelle ändern oder Ergebnisse filtern, indem Sie die entsprechenden Parameter im Miningmodell-Viewer festlegen.  
  
## <a name="list-of-algorithm-parameters"></a>Liste der Algorithmusparameter  
 Alle [!INCLUDE[msCoName](../includes/msconame-md.md)]-Algorithmen können mithilfe von Parametern angepasst werden. Da die optimalen Parametereinstellungen von der Zusammensetzung der Daten abhängen, würde eine detaillierte Erläuterung der Auswirkungen von Parameteränderungen über den Rahmen dieses Themas hinausgehen.  
  
 In der folgenden Tabelle sind die Parameter zusammen mit einer Beschreibung ihrer Funktionalität und Links zu technischen Informationen aufgelistet.  
  
|Parametername|Verwendung in|Description|  
|--------------------|-------------|-----------------|  
|AUTO_DETECT_PERIODICITY|Microsoft Time Series-Algorithmus|Gibt einen numerischen Wert zwischen 0 und 1 an, der zum Erkennen von Periodizität verwendet wird. Je näher dieser Wert bei 1 liegt, desto besser funktioniert die Ermittlung vieler fast periodischer Muster und die automatische Generierung von Periodizitätshinweisen. Die Verarbeitung einer großen Anzahl von Periodizitätshinweisen führt in der Regel zu erheblich längeren Modelltrainingszeiten und zu genaueren Modellen. Wenn der Wert nah bei 0 liegt, wird Periodizität nur bei stark periodischen Daten erkannt.<br /><br /> Der Standardwert ist 0,6.|  
|CLUSTER_COUNT|Microsoft Clustering-Algorithmus<br /><br /> Microsoft Sequence Clustering-Algorithmus|Gibt die ungefähre Anzahl der vom Algorithmus zu erstellenden Cluster an. Falls die ungefähre Anzahl von Clustern nicht aus den Daten erstellt werden kann, erstellt der Algorithmus so viele Cluster wie möglich. Durch Festlegen des CLUSTER_COUNT-Parameters auf 0 wird der Algorithmus zur Verwendung heuristischer Methoden veranlasst, um die Anzahl von zu erstellenden Clustern so gut wie möglich zu bestimmen.<br /><br /> Der Standardwert ist 10.|  
|CLUSTER_SEED|Microsoft Clustering-Algorithmus|Gibt den numerischen Ausgangswert für die zufällige Clustergenerierung in der Anfangsphase der Modellerstellung an.<br /><br /> Die Standardeinstellung ist 0.|  
|CLUSTERING_METHOD|Microsoft Clustering-Algorithmus|Gibt an, welche Clustermethode vom Algorithmus verwendet wird. Folgende Clustermethoden sind verfügbar: EM skalierbar (1), EM nicht skalierbar (2), K-Means skalierbar (3) oder K-Means nicht skalierbar (4).<br /><br /> Der Standardwert lautet 1.|  
|COMPLEXITY_PENALTY|Microsoft Decision Trees-Algorithmus<br /><br /> Microsoft Time Series-Algorithmus|Steuert das Anwachsen der Entscheidungsstruktur. Ein niedriger Wert führt zu einer größeren Anzahl von Teilungen, und ein hoher Wert führt zu einer niedrigeren Anzahl von Teilungen. Der Standardwert richtet sich nach der Anzahl von Attributen in einem bestimmten Modell und ist der nachstehenden Liste zu entnehmen:<br /><br /> Für die Attribute 1-9 lautet der Wert 0,5.<br /><br /> Für 10 bis 99 Attribute lautet der Wert 0,9.<br /><br /> Für 100 oder mehr Attribute lautet der Wert 0,99.<br /><br /> Hinweis: In zeitreihenmodellen trifft dieser Parameter auf, nur für Modelle, die mit dem ARTxp-Algorithmus erstellt wurden, oder auf gemischte Modelle.|  
|FORCED_REGRESSOR|Microsoft Decision Trees-Algorithmus<br /><br /> Microsoft Linear Regression-Algorithmus|Zwingt den Algorithmus, die angegebenen Spalten als Regressoren zu verwenden, und zwar unabhängig von ihrer durch den Algorithmus berechneten Bedeutung.<br /><br /> Hinweis: Dieser Parameter wird nur für Entscheidungsstrukturen verwendet, die ein kontinuierliches Attribut vorhersagen. Definitionsgemäß ist ein Linear Regression-Modell ein besonderer Fall von Entscheidungsstrukturen, mit der kontinuierliche Attribute vorhergesagt werden. Jedes Entscheidungsstrukturmodell kann jedoch einen Knoten enthalten, der eine Linear Regression-Formel darstellt.|  
|FORECAST_METHOD|Microsoft Time Series-Algorithmus|Gibt an, ob Vorhersagen mit dem ARTxp-Algorithmus, dem ARIMA-Algorithmus oder einer Kombination aus beiden durchgeführt werden sollen.<br /><br /> Der Standard lautet MIXED.|  
|HIDDEN_NODE_RATIO|Microsoft Neural Network Algorithm|Legt das Verhältnis von verborgenen Neuronen zu Eingabe- und Ausgabeneuronen fest. Die folgende Formel bestimmt die erste Anzahl von Neuronen in der verborgenen Ebene:<br /><br /> HIDDEN_NODE_RATIO * SQRT(Gesamtzahl der Eingabeneuronen \* Gesamtzahl der Ausgabeneuronen)<br /><br /> Der Standardwert ist 4.0.|  
|HISTORIC_MODEL_COUNT|Microsoft Time Series-Algorithmus|Gibt die Anzahl von Vergangenheitsmodellen an, die erstellt werden.<br /><br /> Der Standardwert lautet 1.|  
|HISTORICAL_MODEL_GAP|Microsoft Time Series-Algorithmus|Gibt die Zeitverzögerung zwischen zwei aufeinander folgenden Vergangenheitsmodellen an. Wenn Sie diesen Wert beispielsweise auf g festlegen, werden Vergangenheitsmodelle für Daten erstellt, die mit Intervallen von g, 2*g, 3\*g in Zeitscheiben aufgeteilt werden.<br /><br /> Der Standardwert ist 10.|  
|HOLDOUT_PERCENTAGE|Microsoft Logistic Regression-Algorithmus<br /><br /> Microsoft Neural Network Algorithm|Gibt den Prozentsatz von Fällen in den Trainingsdaten an, die zum Berechnen des Fehlers für zurückgehaltene Daten verwendet werden. Dieser dient als Teil des Beendigungskriteriums beim Trainieren des Miningmodells.<br /><br /> Der Standardwert ist 30.<br /><br /> Hinweis: Dieser Parameter unterscheidet sich vom Prozentsatz für Zurückgehaltene Daten, die auf eine Miningstruktur angewendet wird.|  
|HOLDOUT_SEED|Microsoft Logistic Regression-Algorithmus<br /><br /> Microsoft Neural Network Algorithm|Gibt eine Zahl an, die als Ausgangswert für den Pseudozufallszahlen-Generator zum zufälligen Generieren von zurückgehaltenen Daten verwendet wird. Wenn dieser Parameter auf 0 festgelegt ist, wird der Ausgangswert vom Algorithmus basierend auf dem Namen des Miningmodells generiert. So wird sichergestellt, dass der Inhalt bei erneuter Verarbeitung des Modells gleich bleibt.<br /><br /> Der Standardwert ist 0.<br /><br /> Hinweis: Dieser Parameter unterscheidet sich vom Ausgangswert für Zurückgehaltene Daten, der auf eine Miningstruktur angewendet wird.|  
|INSTABILITY_SENSITIVITY|Microsoft Time Series-Algorithmus|Legt den Punkt fest, bei dem die Vorhersagevarianz einen bestimmten Schwellenwert übersteigt, und der ARTxp-Algorithmus Vorhersagen unterdrückt. Der Standardwert ist 1.<br /><br /> Hinweis: Dieser Parameter gilt nur für gemischte Modelle oder Modelle, die den ARTxp-Algorithmus verwenden.|  
|MAXIMUM_INPUT_ATTRIBUTES|Microsoft Clustering-Algorithmus<br /><br /> Microsoft Decision Trees-Algorithmus<br /><br /> Microsoft Linear Regression-Algorithmus<br /><br /> Microsoft Naive Bayes-Algorithmus<br /><br /> Microsoft Neural Network Algorithm<br /><br /> Microsoft Logistic Regression-Algorithmus|Definiert die Anzahl von Eingabeattributen, die der Algorithmus verarbeiten kann, bevor die Funktionsauswahl aufgerufen wird. Legen Sie diesen Wert auf 0 fest, um die Funktionsauswahl zu deaktivieren.<br /><br /> Der Standardwert lautet 255.|  
|MAXIMUM_ITEMSET_COUNT|Microsoft Association-Algorithmus|Gibt die maximal zu erzeugende Anzahl von Itemsets an. Wenn keine Anzahl angegeben ist, werden vom Algorithmus alle Itemsets generiert, die potenziell erstellt werden können.<br /><br /> Der Standardwert ist 200000.|  
|MAXIMUM_ITEMSET_SIZE|Microsoft Association-Algorithmus|Gibt die maximale Anzahl von Elementen an, die in einem Itemset zulässig sind. Wenn Sie diesen Wert auf 0 festlegen, geben Sie dadurch an, dass es für die Größe des Itemsets keine Begrenzung gibt.<br /><br /> Der Standardwert lautet 3.|  
|MAXIMUM_OUTPUT_ATTRIBUTES|Microsoft Decision Trees-Algorithmus<br /><br /> Microsoft Linear Regression-Algorithmus<br /><br /> Microsoft Logistic Regression-Algorithmus<br /><br /> Microsoft Naive Bayes-Algorithmus<br /><br /> Microsoft Neural Network Algorithm|Definiert die Anzahl von Ausgabeattributen, die der Algorithmus verarbeiten kann, bevor die Funktionsauswahl aufgerufen wird. Legen Sie diesen Wert auf 0 fest, um die Funktionsauswahl zu deaktivieren.<br /><br /> Der Standardwert lautet 255.|  
|MAXIMUM_SEQUENCE_STATES|Microsoft Sequence Clustering-Algorithmus|Gibt die maximale Anzahl von Status an, die eine Sequenz annehmen kann. Das Festlegen dieses Werts auf eine Zahl größer 100 kann dazu führen, dass das vom Algorithmus erstellte Modell keine aussagekräftigen Informationen enthält.<br /><br /> Der Standardwert ist 64.|  
|MAXIMUM_SERIES_VALUE|Microsoft Time Series-Algorithmus|Gibt den maximalen Wert an, der für Vorhersagen verwendet werden soll. Dieser Parameter wird zusammen mit MINIMUM_SERIES_VALUE verwendet, um die Vorhersagen auf einen bestimmten Bereich einzuschränken. Sie können beispielsweise festlegen, dass die vorhergesagte Verkaufsmenge an einem Tag niemals die Anzahl der Produkte im Lager überschreiten darf.|  
|MAXIMUM_STATES|Microsoft Clustering-Algorithmus<br /><br /> Microsoft Neural Network Algorithm<br /><br /> Microsoft Sequence Clustering-Algorithmus|Gibt die maximale Anzahl der vom Algorithmus unterstützten Attributstatus an. Wenn die Anzahl der Status ein Attributs größer als die maximale Anzahl von Status ist, wird der Algorithmus verwendet das Attribut die gebräuchlichsten Status und ignoriert die restlichen Status.<br /><br /> Der Standardwert ist 100.|  
|MAXIMUM_SUPPORT|Microsoft Association-Algorithmus|Gibt die maximale Anzahl von Fällen, in denen ein Itemset über Unterstützungswerte verfügen kann. Wenn dieser Wert kleiner als 1 ist, entspricht er einem prozentualen Anteil an der Gesamtzahl von Fällen. Wenn dieser Wert größer als 1 ist, stellt der Wert die absolute Anzahl von Fällen, in denen das Itemset enthalten können.<br /><br /> Der Standardwert lautet 1.|  
|MINIMUM_IMPORTANCE|Microsoft Association-Algorithmus|Gibt den Wichtigkeitsschwellenwert für Zuordnungsregeln an. Regeln, die eine Wichtigkeit aufweisen, die geringer ist als dieser Wert, werden herausgefiltert.|  
|MINIMUM_ITEMSET_SIZE|Microsoft Association-Algorithmus|Gibt die Mindestanzahl von Elementen an, die in einem Itemset zulässig sind.<br /><br /> Der Standardwert lautet 1.|  
|MINIMUM_DEPENDENCY_PROBABILITY|Microsoft Naive Bayes-Algorithmus|Gibt die minimale Abhängigkeitswahrscheinlichkeit zwischen Eingabe- und Ausgabeattributen an. Dieser Wert wird verwendet, um die Größe der vom Algorithmus generierten Inhalte zu beschränken. Diese Eigenschaft kann Werte zwischen 0 und 1 annehmen. Größere Werte reduzieren die Anzahl von Attributen im Inhalt des Modells.<br /><br /> Der Standardwert ist 0,5.|  
|MINIMUM_PROBABILITY|Microsoft Association-Algorithmus|Gibt die Mindestwahrscheinlichkeit an, dass eine Regel wahr ist. Wenn Sie diesen Wert auf 0,5 festlegen, wird keine Regel mit einer Wahrscheinlichkeit von weniger als 50 Prozent generiert.<br /><br /> Der Standardwert ist 0,4.|  
|MINIMUM_SERIES_VALUE|Microsoft Time Series-Algorithmus|Gibt die untere Einschränkung für eine Zeitreihenvorhersage an. Vorhergesagte Werte werden nie kleiner sein als diese Einschränkung.|  
|MINIMUM_SUPPORT|Microsoft Association-Algorithmus|Gibt an, in wie vielen Fällen das Itemset mindestens enthalten sein muss, damit der Algorithmus eine Regel generiert. Wenn dieser Wert auf kleiner 1 festgelegt wird, wird damit die Mindestanzahl von Fällen als prozentualer Anteil an der Gesamtzahl von Fällen angegeben. Wird dieser Wert auf größer 1 festgelegt, wird damit die Mindestanzahl von Fällen als die absolute Anzahl von Fällen, die das Itemset enthalten müssen, angegeben. Der Wert wird möglicherweise vom Algorithmus erhöht, wenn der Speicher knapp ist.<br /><br /> Der Standardwert ist 0,03.|  
|MINIMUM_SUPPORT|Microsoft Clustering-Algorithmus|Gibt die Mindestanzahl von Fällen in jedem Cluster an.<br /><br /> Der Standardwert lautet 1.|  
|MINIMUM_SUPPORT|Microsoft Decision Trees-Algorithmus|Bestimmt die Mindestanzahl von Blattfällen, die zum Generieren einer Teilung in der Entscheidungsstruktur erforderlich sind.<br /><br /> Der Standardwert ist 10.|  
|MINIMUM_SUPPORT|Microsoft Sequence Clustering-Algorithmus|Gibt die Mindestanzahl von Fällen in jedem Cluster an.<br /><br /> Der Standardwert ist 10.|  
|MINIMUM_SUPPORT|Microsoft Time Series-Algorithmus|Gibt die Mindestanzahl von Zeitscheiben an, die erforderlich sind, um eine Teilung in jeder Zeitreihenstruktur zu generieren.<br /><br /> Der Standardwert ist 10.|  
|MISSING_VALUE_SUBSTITUTION|Microsoft Time Series-Algorithmus|Gibt die Methode an, die zum Füllen der Lücken in Vergangenheitsdaten verwendet wird. Standardmäßig sind unregelmäßige Lücken oder Ränder in Daten nicht zulässig. Mit folgenden Methoden können unregelmäßige Lücken oder Ränder ausgefüllt werden: mit dem vorherigen Wert, dem Mittelwert oder einer spezifischen numerischen Konstante.|  
|MODELLING_CARDINALITY|Microsoft Clustering-Algorithmus|Gibt die Anzahl von Stichprobenmodellen an, die während des Clusterprozesses erstellt werden.<br /><br /> Der Standardwert ist 10.|  
|PERIODICITY_HINT|Microsoft Time Series-Algorithmus|Stellt für den Algorithmus einen Periodizitätshinweis der Daten bereit. Beispiel: Wenn die Verkaufszahlen jahresabhängig variieren und als Maßeinheit für die Reihe Monate gewählt wurden, ist die Periodizität 12. Dieser Parameter weist das Format {n [, n]} auf, wobei n eine beliebige positive Zahl ist. Das n innerhalb der eckigen Klammern [] ist optional und kann so oft wie nötig wiederholt werden.<br /><br /> Die Standardeinstellung ist {1}.|  
|PREDICTION_SMOOTHING|Microsoft Time Series-Algorithmus|Steuert die Mischung aus ARTXP- und ARIMA-Zeitreihenalgorithmen. Der angegebene Wert ist nur gültig, wenn der FORECAST_METHOD-Parameter auf MIXED festgelegt ist. Werte müssen zwischen 0 und 1 liegen. Wenn der Wert 0 ist, verwendet das Modell nur ARTXP. Wenn der Wert 1 ist, verwendet das Modell nur ARIMA. Bei einem Wert, der nahe an 0 liegt, wird ARTXP stärker gewichtet. Bei einem Wert, der nahe an 1 liegt, wird ARIMA stärker gewichtet.|  
|SAMPLE_SIZE|Microsoft Clustering-Algorithmus|Gibt die Anzahl von Fällen an, die bei jedem Durchlauf des Algorithmus verwendet werden, wenn der CLUSTERING_METHOD-Parameter auf eine der skalierbaren Clustermethoden festgelegt ist. Das Festlegen des SAMPLE_SIZE-Parameters auf 0 bewirkt eine Clustererstellung für das gesamte Dataset in einem einzelnen Durchlauf. Dies kann zu Arbeitsspeicher- und Leistungsproblemen führen.<br /><br /> Der Standardwert ist 50.000.|  
|SAMPLE_SIZE|Microsoft Logistic Regression-Algorithmus<br /><br /> Microsoft Neural Network Algorithm|Gibt die Anzahl von Fällen an, die zum Trainieren des Modells verwendet werden. Der Algorithmusanbieter verwendet entweder diese Anzahl oder den Prozentsatz aller Fälle, die laut HOLDOUT_PERCENTAGE-Parameter nicht im Prozentsatz für zurückgehaltene Daten enthalten sind, je nachdem, welcher Wert kleiner ist.<br /><br /> Wenn also HOLDOUT_PERCENTAGE auf 30 festgelegt ist, verwendet der Algorithmus entweder den Wert dieses Parameters oder einen Wert, der 70 % der Gesamtanzahl der Fälle entspricht, je nachdem, welcher Wert kleiner ist.<br /><br /> Der Standardwert ist 10.000.|  
|SCORE_METHOD|Microsoft Decision Trees-Algorithmus|Bestimmt die zum Berechnen des Teilungsergebnisses zu verwendende Methode. Die folgenden Optionen stehen zur Verfügung: (1) Entropie, Bayes (2)-Methode mit K2 vor, oder (3) Bayes-Dirichlet-Äquivalent (BDE) vor.<br /><br /> Der Standardwert lautet 3.|  
|SPLIT_METHOD|Microsoft Decision Trees-Algorithmus|Bestimmt die zum Teilen des Knotens zu verwendende Methode. Die folgenden Optionen stehen zur Verfügung: Binär (1), vollständig (2) oder beide (3).<br /><br /> Der Standardwert lautet 3.|  
|STOPPING_TOLERANCE|Technische Referenz für den Microsoft Clustering-Algorithmus|Gibt den Wert an, mit dem bestimmt wird, wann Konvergenz erreicht ist und die Modellerstellung mit dem Algorithmus abgeschlossen ist. Konvergenz ist erreicht, wenn die Gesamtänderung der Clusterwahrscheinlichkeiten kleiner als das Verhältnis des STOPPING_TOLERANCE-Parameters geteilt durch die Modellgröße ist.<br /><br /> Der Standardwert ist 10.|  
  
### <a name="comments"></a>Kommentare  
 Weitere Einzelheiten zu den Algorithmen finden Sie in der SQL Server-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Algorithmen &#40;SQL Server Data Mining-Add-ins&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md)  
  
  
