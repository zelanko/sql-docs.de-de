---
title: Kreuz Validierung (SQL Server Data Mining-Add-Ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cross-validation
- partitioning data [data mining]
- mining models, testing
ms.assetid: bf9483b3-4099-41c4-bbc5-da7005e07bcd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0cc3a132792cca8ecdf5a33a2fe4e4d40116c497
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66086649"
---
# <a name="cross-validation-sql-server-data-mining-add-ins"></a>Kreuzvalidierung (SQL Server Data Mining-Add-Ins)
  ![Schaltfläche "Übergreifende Überprüfung", Menüband "Data Mining"](media/dmc-xvalid.gif "Schaltfläche "Übergreifende Überprüfung", Menüband "Data Mining"")  
  
 Die Kreuzvalidierung ist ein Standardtool in der Analyse und eine wichtige Funktion, die Sie bei der Entwicklung und Feinabstimmung von Data Mining-Modellen unterstützt. Sie verwenden die Kreuzvalidierung nach der Erstellung eines Miningmodells, um die Gültigkeit des Modells sicherzustellen und die Ergebnisse mit anderen, ähnlichen Modellen zu vergleichen.  
  
 Die Kreuzvalidierung besteht aus zwei Phasen: Training und Berichtgenerierung. Sie führen die folgenden Schritte aus:  
  
-   Auswählen eines Zielminingmodells oder einer Zielminingstruktur  
  
-   Angeben des Zielwerts, sofern anwendbar  
  
-   Geben Sie die Anzahl der Querschnitte oder *folds*an, in die die Strukturdaten partitioniert werden sollen.  
  
 Der Assistent für die **Kreuz Validierung** erstellt dann ein neues Modell für die einzelnen Folds, testet das Modell auf den anderen folds und meldet dann die Genauigkeit des Modells. Nach Abschluss erstellt der **Kreuz Validierungs-** Assistent einen Bericht, in dem die Metriken für die einzelnen Fold angezeigt werden, und stellt eine Zusammenfassung des Modells in Aggregat bereit. Diese Informationen können verwendet werden, um festzustellen, wie gut sich die zugrunde liegenden Daten für ein Modell eignen oder um verschiedene, auf den gleichen Daten beruhende Modelle zu vergleichen.  
  
## <a name="using-the-cross-validation-wizard"></a>Verwenden des Kreuzvalidierungs-Assistenten  
 Sie können Kreuzvalidierungen für temporäre Modelle und für Modelle verwenden, die auf in einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] gespeichert sind.  
  
#### <a name="to-create-a-cross-validation-report"></a>So erstellen Sie einen Kreuzvalidierungsbericht  
  
1.  Klicken Sie im Menüband **Data Mining** in der Gruppe **Genauigkeit und Überprüfung** auf **Kreuz Validierung**.  
  
2.  Wählen Sie im Dialogfeld **Struktur oder Modell auswählen** eine vorhandene Mining Struktur oder ein vorhandenes Mining Modell aus. Wenn Sie eine Struktur auswählen, wendet der Assistent die Kreuzvalidierung auf alle Modelle an, die auf dieser Struktur mit dem gleichen vorhersagbaren Attribut basieren. Wenn Sie ein Modell auswählen, wendet der Assistent die Kreuzvalidierung nur auf dieses Modell an.  
  
3.  Wählen Sie im Dialogfeld **Kreuz Validierungs Parameter angeben** im Feld **foldanzahl** die Anzahl der Aufteilungen aus, unter denen das DataSet aufgeteilt werden soll. Ein Fold ist ein zufällig ausgewählter Querschnitt der Daten.  
  
4.  Legen Sie optional die maximale Anzahl von Zeilen fest, die bei der Kreuz Validierung verwendet werden sollen, indem Sie im Textfeld **Maximale Zeilen** Zahl eine Zahl eingeben.  
  
    > [!NOTE]  
    >  Je mehr Zeilen Sie verwenden, desto genauer sind die Ergebnisse. Die Verarbeitungszeit könnte allerdings auch bedeutend zunehmen. Welche Zahl Sie angeben sollten, hängt von Ihren Daten ab, im Allgemeinen sollte dies aber die maximale Anzahl sein, die Sie ohne Leistungseinbußen verwenden können. Um die Leistung zu verbessern, können Sie auch weniger Folds angeben.  
  
5.  Wählen Sie eine Spalte aus der Dropdown Liste **Ziel Attribut** aus. Die Liste zeigt nur die Spalten an, die bei der ursprünglichen Erstellung des Modells als vorhersagbare Attribute konfiguriert wurden. Das Modell enthält möglicherweise mehrere vorhersagbare Attribute, aber Sie können nur eines auswählen.  
  
6.  Wählen Sie einen Wert aus der Dropdown Liste **Ziel Status** aus.  
  
     Wenn die vorhersagbare Spalte fortlaufende numerische Daten enthält, ist diese Option nicht verfügbar.  
  
7.  Geben Sie optional einen Wert an, der als **Ziel Schwellen** Wert verwendet werden soll, wenn Vorhersagen als genau gezählt werden. Dieser Wert gibt eine Wahrscheinlichkeit wieder und ist eine Zahl zwischen 0 und 1, wobei 1 bedeutet, dass die Vorhersage genau ist, 0 bedeutet, dass die Vorhersage falsch ist, und 0,5 einer zufälligen Schätzung entspricht.  
  
     Wenn die vorhersagbare Spalte fortlaufende numerische Daten enthält, ist diese Option nicht verfügbar.  
  
8.  Klicken Sie auf **Fertig stellen**. Ein neues Arbeitsblatt mit dem Namen " **Kreuz Validierung**" wird erstellt.  
  
    > [!NOTE]  
    >  Microsoft Excel wird möglicherweise vorübergehend nicht reagieren, während das Modell in Folds partitioniert und jeder Fold getestet wird.  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
 Um einen Kreuzvalidierungsbericht zu erstellen, müssen Sie bereits eine Data Mining-Struktur und verwandte Modelle erstellt haben. Der Assistent stellt ein Dialogfeld bereit, in dem Sie eine vorhandene Struktur oder ein vorhandendes Modell auswählen können.  
  
 Wenn Sie eine Miningstruktur auswählen, die mehrere Miningmodelle unterstützt, und die Modelle unterschiedliche vorhersagbare Attribute verwenden, testet der Kreuzvalidierung-Assistent nur die Modelle, die das gleiche vorhersagbare Attribut verwenden.  
  
 Wenn Sie eine Struktur auswählen, die sowohl Clustermodelle als auch andere Arten von Modellen unterstützt, werden die Clustermodelle nicht getestet.  
  
## <a name="understanding-cross-validation-results"></a>Grundlegendes zu Kreuzvalidierungsergebnissen  
 Die Ergebnisse der Kreuz Validierung werden in einem neuen Arbeitsblatt mit dem Titel **Kreuz Validierungsbericht für \<Attribut Name>** angezeigt. Das neue Arbeitsblatt besteht aus mehreren Abschnitten: der erste Abschnitt enthält eine Zusammenfassung mit wichtigen Metadaten zum getesteten Modell, sodass Sie sehen, aus welchem Modell oder aus welcher Struktur die Ergebnisse stammen.  
  
 Der zweite Abschnitt enthält eine statistische Zusammenfassung, die angibt, wie gut das ursprüngliche Modell ist. In dieser Zusammenfassung werden die Unterschiede zwischen den Modellen, die für die einzelnen Fold erstellt werden, auf drei wichtige Measures analysiert: *Root Mean Square Error*, *Mean absolute Error*und *Log Score*. Dies sind statistische Standardmeasures, die nicht nur beim Data Mining verwendet werden, sondern auch in den meisten statistischen Analysen.  
  
 Für jedes dieser Measures berechnet der Kreuzvalidierungs-Assistent die mittlere und Standardabweichung für das Modell als ganzes. Dadurch können Sie ablesen, wie einheitlich dieses Modell ist, wenn Vorhersagen für verschiedene Teilmengen der Daten vorgenommen werden. Wenn die Standardabweichung z. B. sehr groß ist, weist dies darauf hin, dass die für die einzelen Folds erstellten Modelle sehr unterschiedliche Ergebnisse liefern und das Modell daher zu sehr auf eine bestimmte Datengruppe ausgerichtet ist und nicht auf andere Datensätze zutrifft.  
  
 Im folgenden Abschnitt werden die Measures erläutert, die zur Bewertung des Modells verwendet werden.  
  
### <a name="tests-and-measures"></a>Tests und Measures  
 Zusätzlich zu einigen grundlegenden Informationen über die Anzahl der Folds in den Daten und die Datenmenge in jedem Fold zeigt das Arbeitsblatt verschiedene, nach Testtyp geordnete Metriken für jedes Modell an. Die Genauigkeit eines Clustermodells wird z. B. durch andere Tests geprüft als die Genauigkeit eines Prognosemodells.  
  
 In der folgenden Tabelle werden die Tests und die Metriken zusammen mit einer Erklärung der Bedeutung der Metriken aufgeführt.  
  
#### <a name="aggregates-and-general-statistical-measures"></a>Aggregate und allgemeine statistische Measures  
 Die Aggregatmeasures im Bericht geben an, wie sehr die von Ihnen in den Daten erstellten Folds voneinander abweichen.  
  
-   Mittlere und Standardabweichung  
  
-   Durchschnitt der Abweichung vom Mittelwert für ein bestimmtes Measure für alle Partitionen in einem Modell.  
  
#### <a name="classification-passfail"></a>Klassifizierung: bestanden/fehlgeschlagen  
 Dieses Measure wird in Klassifizierungsmodellen verwendet, wenn Sie keinen Zielwert für das vorhersagbare Attribut angeben. Wenn Sie z. B. ein Modell zur Vorhersage verschiedener Möglichkeiten erstellen, gibt dieses Measure an, wie gut das Modell alle möglichen Werte vorausgesagt hat.  
  
 "Pass/Fail" wird berechnet, indem Fälle gezählt werden, die die folgenden Bedingungen erfüllen: " **Pass** ", wenn der vorhergesagte Status mit der höchsten Wahrscheinlichkeit mit dem Eingabe Status übereinstimmt und die Wahrscheinlichkeit größer als der Wert ist, den Sie für den **Status Schwellen**Wert angegeben haben. Andernfalls tritt ein Fehler **auf.**  
  
#### <a name="classification-true-or-false-positives-and-negatives"></a>Klassifikation: Richtig oder falsch positiv und negativ  
 Dieser Test wird für alle Klassifizierungsmodelle verwendet, die ein festgelegtes Ziel haben. Das Measure gibt an, wie die einzelnen Fälle entsprechend folgender Fragen klassifiziert werden: was hat das Modell vorhergesagt und wie lautete das tatsächliche Ergebnis.  
  
|"Measure"|BESCHREIBUNG|  
|-------------|-----------------|  
|Richtig positiv|Anzahl der Fälle, die diese Bedingungen erfüllen:<br /><br /> Fall enthält den Zielwert.<br /><br /> Modell hat vorhergesagt, dass der Fall den Zielwert enthält.|  
|Falsch positiv|Anzahl der Fälle, die diese Bedingungen erfüllen:<br /><br /> Tatsächlicher Wert ist gleich dem Zielwert.<br /><br /> Modell hat vorhergesagt, dass der Fall den Zielwert enthält.|  
|Richtig negativ|Anzahl der Fälle, die diese Bedingungen erfüllen:<br /><br /> Fall enthält den Zielwert nicht.<br /><br /> Modell hat vorhergesagt, dass der Fall den Zielwert nicht enthält.|  
|Falsch negativ|Anzahl der Fälle, die diese Bedingungen erfüllen:<br /><br /> Tatsächlicher Wert ist ungleich dem Zielwert.<br /><br /> Modell hat vorhergesagt, dass der Fall den Zielwert nicht enthält.|  
  
#### <a name="lift"></a>Lift  
 *Lift* ist ein Measure, das mit der Wahrscheinlichkeit verknüpft ist. Wenn ein Ergebnis wahrscheinlicher ist, wenn Sie das Modell verwenden, als wenn Sie eine zufällige Vermutung treffen, wird das Modell als *positiver Lift*bezeichnet. Wenn das Modell jedoch Vorhersagen trifft, die weniger wahrscheinlich sind als zufällige Wahrscheinlichkeit, ist das Lift Ergebnis *negativ*. Dieses Measure gibt daher an, in welchem Maße Verbesserungen durch die Verwendung des Modells erreicht werden können. Je höher die Zahl, desto günstiger die Verwendung des Modells.  
  
 Der Lift wird berechnet als Verhältnis der tatsächlichen Vorhersagewahrscheinlichkeit zur Randwahrscheinlichkeit in den Testfällen.  
  
#### <a name="log-score"></a>Logarithmisches Ergebnis  
 Das *Protokoll Ergebnis*, das auch als *Protokoll Wahrscheinlichkeits Bewertung* für die Vorhersage bezeichnet wird, stellt das Verhältnis zwischen zwei Wahrscheinlichkeiten dar, die in eine logarithmische Skala konvertiert werden. Da Wahrscheinlichkeit als Dezimalbruch dargestellt werden, ist das logarithmische Ergebnis immer eine negative Zahl. Je näher das Ergebnis an 0 liegt, desto besser ist es.  
  
 Während Rohergebnisse sehr unregelmäßige oder verfälschte Verteilungen aufweisen können, ist ein logarithmisches Ergebnis einem Prozentwert ähnlich.  
  
#### <a name="root-mean-square-error"></a>Wurzel des mittleren quadratischen Fehlers  
 *Root Mean Square Error* (RMSE) ist eine Standardmethode in der Statistik für die Betrachtung der verschiedenen Datasets und die Beseitigung der Unterschiede, die durch die Skalierung der Eingaben eingeführt werden können.  
  
 RMSE stellt den durchschnittlichen Fehler des vorhergesagten Werts beim Vergleich mit dem tatsächlichen Wert dar. Es wird als Quadratwurzel der durchschnittlichen Fehler für alle Partitionsfälle geteilt durch die Anzahl der Fälle in der Partition berechnet. Zeilen mit fehlenden Werten für die Zielattribute werden ausgeschlossen.  
  
#### <a name="mean-absolute-error"></a>Mittlerer absoluter Fehler  
 Der *mittlere absolute Fehler* ist der durchschnittliche Fehler des vorhergesagten Werts mit dem tatsächlichen Wert. Er wird durch Ermitteln der absoluten Fehlersumme und Ermitteln des Mittelwerts dieser Fehler berechnet.  
  
 Dieser Wert gibt an, wie sehr sich Ergebnisse vom Mittelwert unterscheiden.  
  
#### <a name="case-likelihood"></a>Fallwahrscheinlichkeit  
 Dieses Measure wird nur für Clustermodelle verwendet und gibt an, wie wahrscheinlich es ist, dass ein neuer Fall zu einem bestimmten Cluster gehört.  
  
 In Clustermodellen gibt es zwei Arten der Clustermitgliedschaft je nach Methode, die Sie bei der Modellerstellung verwendet haben. In einigen auf dem K-Means-Algorithmus basierenden Modellen wird erwartet, dass ein neuer Fall nur zu einem Cluster gehört. Der Microsoft Clustering-Algorithmus verwendet standardmäßig jedoch die Expectation-Maximization-Methode, bei der davon ausgegangen wird, dass ein neuer Fall potenziell zu jedem Cluster gehören kann. In diesem Modellen kann ein Fall daher mehrere `CaseLikelihood`-Werte aufweisen, aber nur der standardmäßig zurückgegebene gibt die Wahrscheinlichkeit wieder, dass der Fall zu dem Cluster gehört, der am besten zum neuen Fall passt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Validieren von Modellen und Verwenden von Modellen für Vorhersage &#40;Data Mining-Add-Ins für Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
