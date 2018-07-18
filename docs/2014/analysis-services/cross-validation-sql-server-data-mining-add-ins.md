---
title: Kreuzvalidierung (SQL Server Data Mining-Add-ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cross-validation
- partitioning data [data mining]
- mining models, testing
ms.assetid: bf9483b3-4099-41c4-bbc5-da7005e07bcd
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 01876b099a764676eb82dd2ac8cea12cdabbc4b4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172101"
---
# <a name="cross-validation-sql-server-data-mining-add-ins"></a>Kreuzvalidierung (SQL Server Data Mining-Add-Ins)
  ![Schaltfläche "übergreifende Überprüfung" "," Data Mining-Menüband](media/dmc-xvalid.gif "Kreuzvalidierungs-Schaltfläche, Data Mining-Menüband")  
  
 Die Kreuzvalidierung ist ein Standardtool in der Analyse und eine wichtige Funktion, die Sie bei der Entwicklung und Feinabstimmung von Data Mining-Modellen unterstützt. Sie verwenden die Kreuzvalidierung nach der Erstellung eines Miningmodells, um die Gültigkeit des Modells sicherzustellen und die Ergebnisse mit anderen, ähnlichen Modellen zu vergleichen.  
  
 Die Kreuzvalidierung besteht aus zwei Phasen: Training und Berichtgenerierung. Sie führen die folgenden Schritte aus:  
  
-   Auswählen eines Zielminingmodells oder einer Zielminingstruktur  
  
-   Angeben des Zielwerts, sofern anwendbar  
  
-   Geben Sie die Anzahl von Querschnitten oder *Aufteilungen*, in die die Strukturdaten partitioniert.  
  
 Die **Kreuzvalidierung** -Assistenten und dann ein neues Modell für jeden fold erstellt das Modell mit den anderen Folds getestet und anschließend meldet die Genauigkeit des Modells. Nach Abschluss des Vorgangs die **Kreuzvalidierung** -Assistent erstellt einen Bericht, erfahren Sie, die Metriken für jeden Fold und enthält eine Zusammenfassung des aggregierten Modells. Diese Informationen können verwendet werden, um festzustellen, wie gut sich die zugrunde liegenden Daten für ein Modell eignen oder um verschiedene, auf den gleichen Daten beruhende Modelle zu vergleichen.  
  
## <a name="using-the-cross-validation-wizard"></a>Verwenden des Kreuzvalidierungs-Assistenten  
 Sie können Kreuzvalidierungen für temporäre Modelle und für Modelle verwenden, die auf in einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] gespeichert sind.  
  
#### <a name="to-create-a-cross-validation-report"></a>So erstellen Sie einen Kreuzvalidierungsbericht  
  
1.  In der **Genauigkeit und Überprüfung** Gruppe der **Data Mining** des Menübands, klicken Sie auf **Kreuzvalidierung**.  
  
2.  In der **Struktur oder Modell auswählen** Dialogfeld Feld, wählen Sie eine vorhandene Miningstruktur oder Miningmodell. Wenn Sie eine Struktur auswählen, wendet der Assistent die Kreuzvalidierung auf alle Modelle an, die auf dieser Struktur mit dem gleichen vorhersagbaren Attribut basieren. Wenn Sie ein Modell auswählen, wendet der Assistent die Kreuzvalidierung nur auf dieses Modell an.  
  
3.  In der **Kreuzvalidierungsparameter angeben** Dialogfeld die **Foldanzahl** wählen Sie die Anzahl von Folds an, auf dem das DataSet aufteilen. Ein Fold ist ein zufällig ausgewählter Querschnitt der Daten.  
  
4.  Legen Sie optional die maximale Anzahl von Zeilen in der übergreifenden Überprüfung durch Eingabe einer Zahl in die **maximale Zeilenanzahl** Textfeld.  
  
    > [!NOTE]  
    >  Je mehr Zeilen Sie verwenden, desto genauer sind die Ergebnisse. Die Verarbeitungszeit könnte allerdings auch bedeutend zunehmen. Welche Zahl Sie angeben sollten, hängt von Ihren Daten ab, im Allgemeinen sollte dies aber die maximale Anzahl sein, die Sie ohne Leistungseinbußen verwenden können. Um die Leistung zu verbessern, können Sie auch weniger Folds angeben.  
  
5.  Wählen Sie eine Spalte aus der **Zielattribut** Dropdown-Liste. Die Liste zeigt nur die Spalten an, die bei der ursprünglichen Erstellung des Modells als vorhersagbare Attribute konfiguriert wurden. Das Modell enthält möglicherweise mehrere vorhersagbare Attribute, aber Sie können nur eines auswählen.  
  
6.  Wählen Sie einen Wert aus der **Zielstatus** Dropdown-Liste.  
  
     Wenn die vorhersagbare Spalte fortlaufende numerische Daten enthält, ist diese Option nicht verfügbar.  
  
7.  Geben Sie optional einen Wert für die Verwendung als die **Zielschwellenwert** Vorhersagen als korrekt. Dieser Wert gibt eine Wahrscheinlichkeit wieder und ist eine Zahl zwischen 0 und 1, wobei 1 bedeutet, dass die Vorhersage genau ist, 0 bedeutet, dass die Vorhersage falsch ist, und 0,5 einer zufälligen Schätzung entspricht.  
  
     Wenn die vorhersagbare Spalte fortlaufende numerische Daten enthält, ist diese Option nicht verfügbar.  
  
8.  Klicken Sie auf **Fertig stellen**. Erstellt ein neues Arbeitsblatt, mit dem Namen **Kreuzvalidierung**.  
  
    > [!NOTE]  
    >  Microsoft Excel wird möglicherweise vorübergehend nicht reagieren, während das Modell in Folds partitioniert und jeder Fold getestet wird.  
  
### <a name="requirements"></a>Anforderungen  
 Um einen Kreuzvalidierungsbericht zu erstellen, müssen Sie bereits eine Data Mining-Struktur und verwandte Modelle erstellt haben. Der Assistent stellt ein Dialogfeld bereit, in dem Sie eine vorhandene Struktur oder ein vorhandendes Modell auswählen können.  
  
 Wenn Sie eine Miningstruktur auswählen, die mehrere Miningmodelle unterstützt, und die Modelle unterschiedliche vorhersagbare Attribute verwenden, testet der Kreuzvalidierung-Assistent nur die Modelle, die das gleiche vorhersagbare Attribut verwenden.  
  
 Wenn Sie eine Struktur auswählen, die sowohl Clustermodelle als auch andere Arten von Modellen unterstützt, werden die Clustermodelle nicht getestet.  
  
## <a name="understanding-cross-validation-results"></a>Grundlegendes zu Kreuzvalidierungsergebnissen  
 Die Ergebnisse der kreuzvalidierung werden angezeigt, in einem neuen Arbeitsblatt, mit dem Titel **Kreuzvalidierungsbericht für \<Attributname >**. Das neue Arbeitsblatt besteht aus mehreren Abschnitten: der erste Abschnitt enthält eine Zusammenfassung mit wichtigen Metadaten zum getesteten Modell, sodass Sie sehen, aus welchem Modell oder aus welcher Struktur die Ergebnisse stammen.  
  
 Der zweite Abschnitt enthält eine statistische Zusammenfassung, die angibt, wie gut das ursprüngliche Modell ist. In dieser Zusammenfassung werden die Unterschiede zwischen den Modellen, die für jeden Fold erstellt drei Hauptmeasures analysiert werden: *Wurzel des mittleren quadratischen Fehler*, *mittlerer absoluter Fehler*, und *protokollergebnis*. Dies sind statistische Standardmeasures, die nicht nur beim Data Mining verwendet werden, sondern auch in den meisten statistischen Analysen.  
  
 Für jedes dieser Measures berechnet der Kreuzvalidierungs-Assistent die mittlere und Standardabweichung für das Modell als ganzes. Dadurch können Sie ablesen, wie einheitlich dieses Modell ist, wenn Vorhersagen für verschiedene Teilmengen der Daten vorgenommen werden. Wenn die Standardabweichung z. B. sehr groß ist, weist dies darauf hin, dass die für die einzelen Folds erstellten Modelle sehr unterschiedliche Ergebnisse liefern und das Modell daher zu sehr auf eine bestimmte Datengruppe ausgerichtet ist und nicht auf andere Datensätze zutrifft.  
  
 Im folgenden Abschnitt werden die Measures erläutert, die zur Bewertung des Modells verwendet werden.  
  
### <a name="tests-and-measures"></a>Tests und Measures  
 Zusätzlich zu einigen grundlegenden Informationen über die Anzahl der Folds in den Daten und die Datenmenge in jedem Fold zeigt das Arbeitsblatt verschiedene, nach Testtyp geordnete Metriken für jedes Modell an. Die Genauigkeit eines Clustermodells wird z. B. durch andere Tests geprüft als die Genauigkeit eines Prognosemodells.  
  
 In der folgenden Tabelle werden die Tests und die Metriken zusammen mit einer Erklärung der Bedeutung der Metriken aufgeführt.  
  
#### <a name="aggregates-and-general-statistical-measures"></a>Aggregate und allgemeine statistische Measures  
 Die Aggregatmeasures im Bericht geben an, wie sehr die von Ihnen in den Daten erstellten Folds voneinander abweichen.  
  
-   Mittlere und Standardabweichung  
  
-   Durchschnitt der Abweichung vom Mittelwert für ein bestimmtes Measure für alle Partitionen in einem Modell.  
  
#### <a name="classification-passfail"></a>Klassifizierung: Erfolgreich/Fehler  
 Dieses Measure wird in Klassifizierungsmodellen verwendet, wenn Sie keinen Zielwert für das vorhersagbare Attribut angeben. Wenn Sie z. B. ein Modell zur Vorhersage verschiedener Möglichkeiten erstellen, gibt dieses Measure an, wie gut das Modell alle möglichen Werte vorausgesagt hat.  
  
 Erfolg/Misserfolg wird berechnet, indem die Zählung von Fällen, in denen die folgenden Bedingungen erfüllen: **übergeben** entspricht des vorhergesagten Status mit der höchsten Wahrscheinlichkeit dem Eingabestatus und die Wahrscheinlichkeit ist größer als der Wert, den Sie für angegeben **Statusschwellenwert**ist, andernfalls **fehlschlagen**.  
  
#### <a name="classification-true-or-false-positives-and-negatives"></a>Klassifikation: Richtig oder falsch positiv und negativ  
 Dieser Test wird für alle Klassifizierungsmodelle verwendet, die ein festgelegtes Ziel haben. Das Measure gibt an, wie die einzelnen Fälle entsprechend folgender Fragen klassifiziert werden: was hat das Modell vorhergesagt und wie lautete das tatsächliche Ergebnis.  
  
|Measure|Description|  
|-------------|-----------------|  
|Richtig positiv|Anzahl der Fälle, die diese Bedingungen erfüllen:<br /><br /> Fall enthält den Zielwert.<br /><br /> Modell hat vorhergesagt, dass der Fall den Zielwert enthält.|  
|Falsch positiv|Anzahl der Fälle, die diese Bedingungen erfüllen:<br /><br /> Tatsächlicher Wert ist gleich dem Zielwert.<br /><br /> Modell hat vorhergesagt, dass der Fall den Zielwert enthält.|  
|Richtig negativ|Anzahl der Fälle, die diese Bedingungen erfüllen:<br /><br /> Fall enthält den Zielwert nicht.<br /><br /> Modell hat vorhergesagt, dass der Fall den Zielwert nicht enthält.|  
|Falsch negativ|Anzahl der Fälle, die diese Bedingungen erfüllen:<br /><br /> Tatsächlicher Wert ist ungleich dem Zielwert.<br /><br /> Modell hat vorhergesagt, dass der Fall den Zielwert nicht enthält.|  
  
#### <a name="lift"></a>Lift  
 *Heben Sie* ist ein Measure, das mit der Wahrscheinlichkeit verknüpft ist. Wenn ein Ergebnis wahrscheinlicher bei Verwendung des Modells ist als wenn Sie eine zufällige Schätzung vornehmen, hört sich das Modell zu *positiven Lift*. Wenn jedoch das Modell Vorhersagen trifft, die weniger als zufällige Schätzungen wahrscheinlich, die Bewertung der prognosegüte ist *negative*. Dieses Measure gibt daher an, in welchem Maße Verbesserungen durch die Verwendung des Modells erreicht werden können. Je höher die Zahl, desto günstiger die Verwendung des Modells.  
  
 Der Lift wird berechnet als Verhältnis der tatsächlichen Vorhersagewahrscheinlichkeit zur Randwahrscheinlichkeit in den Testfällen.  
  
#### <a name="log-score"></a>Logarithmisches Ergebnis  
 Die *Logarithmisches Ergebnis*auch Namens der *Logarithmisches Ergebnis Wahrscheinlichkeit* für die Vorhersage, stellt das Verhältnis zwischen zwei Wahrscheinlichkeiten, konvertiert in eine logarithmische Skalierung. Da Wahrscheinlichkeit als Dezimalbruch dargestellt werden, ist das logarithmische Ergebnis immer eine negative Zahl. Je näher das Ergebnis an 0 liegt, desto besser ist es.  
  
 Während Rohergebnisse sehr unregelmäßige oder verfälschte Verteilungen aufweisen können, ist ein logarithmisches Ergebnis einem Prozentwert ähnlich.  
  
#### <a name="root-mean-square-error"></a>Wurzel des mittleren quadratischen Fehlers  
 *Wurzel des mittleren quadratischen Fehler* (RMSE) ist eine Standardmethode in der Statistik für Vergleich wie verschiedener Datensätze ansehen und Glättung der Unterschiede, die durch die Unterschiedlichkeit der Eingaben entstehen können.  
  
 RMSE stellt den durchschnittlichen Fehler des vorhergesagten Werts beim Vergleich mit dem tatsächlichen Wert dar. Es wird als Quadratwurzel der durchschnittlichen Fehler für alle Partitionsfälle geteilt durch die Anzahl der Fälle in der Partition berechnet. Zeilen mit fehlenden Werten für die Zielattribute werden ausgeschlossen.  
  
#### <a name="mean-absolute-error"></a>Mittlerer absoluter Fehler  
 Die *mittlerer absoluter Fehler* ist der durchschnittliche Fehler des vorhergesagten Werts mit dem tatsächlichen Wert. Er wird durch Ermitteln der absoluten Fehlersumme und Ermitteln des Mittelwerts dieser Fehler berechnet.  
  
 Dieser Wert gibt an, wie sehr sich Ergebnisse vom Mittelwert unterscheiden.  
  
#### <a name="case-likelihood"></a>Fallwahrscheinlichkeit  
 Dieses Measure wird nur für Clustermodelle verwendet und gibt an, wie wahrscheinlich es ist, dass ein neuer Fall zu einem bestimmten Cluster gehört.  
  
 In Clustermodellen gibt es zwei Arten der Clustermitgliedschaft je nach Methode, die Sie bei der Modellerstellung verwendet haben. In einigen auf dem K-Means-Algorithmus basierenden Modellen wird erwartet, dass ein neuer Fall nur zu einem Cluster gehört. Der Microsoft Clustering-Algorithmus verwendet standardmäßig jedoch die Expectation-Maximization-Methode, bei der davon ausgegangen wird, dass ein neuer Fall potenziell zu jedem Cluster gehören kann. In diesem Modellen kann ein Fall daher mehrere `CaseLikelihood`-Werte aufweisen, aber nur der standardmäßig zurückgegebene gibt die Wahrscheinlichkeit wieder, dass der Fall zu dem Cluster gehört, der am besten zum neuen Fall passt.  
  
## <a name="see-also"></a>Siehe auch  
 [Validieren von Modellen und Verwenden von Modellen für Vorhersagen &#40;Data Mining-Add-ins für Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
