---
title: Erste Schritte mit Data Mining (Data Mining-Add-ins für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: cbe10a19-e194-408e-a65b-5fdf3fb1e880
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3e5a24a158681c3f596355b1b9abca6ada990531
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66080938"
---
# <a name="getting-started-with-data-mining-data-mining-add-ins-for-excel"></a>Erste Schritte mit dem Data Mining (Data Mining-Add-Ins für Excel)
  Data Mining ist ein Vorgang zum Ermitteln wichtiger Muster in Daten. Data Mining ergänzt auf natürliche Weise das Untersuchen und Auswerten Ihrer Daten durch herkömmliche Business Intelligence. Mit Computeralgorithmen können große Datenmengen verarbeitet und Muster und Trends entdeckt werden, die andernfalls verborgen bleiben würden.  
  
 Um Datamining zu tun, erfassen Sie Daten, die relevant für eine bestimmte Frage, wie z. B. "Wer"sind meine Kunden?" oder "welche Produkte wurden gekauft?" und wenden dann einen Algorithmus, um statistische Korrelationen in den Daten zu suchen. Die durch die Analyse ermittelten Muster und Trends werden als Miningmodell gespeichert. Anschließend können Sie das Miningmodell auf neue Daten anwenden, z. B. in Geschäftsszenarien wie den Folgenden:  
  
-   Verwenden früherer Trends, um Umsätze für das nächste Quartal, den Bestandsbedarf oder die Kundenzufriedenheit zu prognostizieren.  
  
-   Anwenden von Kenntnissen über aktuelle Kunden, um Profile für neue Kunden aufzustellen und neue Produkte oder Chancen zu empfehlen.  
  
-   Auffinden von Beziehungen zwischen früheren Ereignissen, um Serverfehler oder -ausfallzeiten vorherzusagen.  
  
-   Analysieren, welche Produkte Kunden zusammen erwerben und Nutzen dieser Informationen, um Paketkäufe zu empfehlen oder Produktwerbungen zu planen.  
  
 Die gewählte Analysemethode hängt jeweils von Ihren Zielen ab. Die Data Mining-Add-Ins unterstützen diese Arten der Analyse:  
  
-   Überwachtes und unüberwachtes Lernen  
  
-   Clustering (Segmentierung)  
  
-   Faktoranalyse, mithilfe von Bayesschen Netzwerken und neuronalen Netzwerken  
  
-   Zeitreihenanalyse  
  
-   Zuordnungsanalyse, Empfehlungen und Warenkorbanalyse  
  
-   Bewerten binärer Ergebnisse  
  
-   Lineare Regression  
  
 Darüber bieten die Add-Ins Unterstützung in der Datenaufbereitungsphase: Auswählen der Daten, Durchsuchen und Analysieren der Daten.  
  
## <a name="define-your-goal"></a>Definieren Ihres Ziels  
 Nehmen Sie sich zunächst einen Moment Zeit, um sich über die Frage klar zu werden, auf die Sie eine Antwort suchen. Das Durchsuchen von Daten an sich ist aufschlussreich, wenn Sie jedoch Ihre Erkenntnisse auf neue Daten anwenden möchten, müssen Sie in der Lage sein, klar zu umreißen, welche Ergebnisse Sie vom Modell erwarten und wie Sie bewerten können, ob das Modell Ihren Zielen gerecht wird.  
  
 Klären Sie z. B. als Ziel "Gewinnen neuer Kunden", nicht Ihr Ziel etwas konkreter, z. B. "Bestimmen des demografischen Hintergrunds potenzieller Kunden, die wahrscheinlich unser Produkt mit einer Wahrscheinlichkeit von mindestens 65 % kaufen werden".  
  
-   Ihr Dataset sollte mindestens ein "Ergebnisattribut" enthalten, die Sie für Training und Vorhersage verwenden können. Ist kein solches Attribut vorhanden, können Sie Trainingsdaten manuell so kennzeichnen oder andere Spalten nutzen, um eine Proxy-Variable für das Ergebnis zu erhalten.  
  
     Z. B. Wenn Sie "die besten potenziellen Kunden" vorhersagen möchten, sollten Sie einer Geschäftsregel zuvor vorhandene Kunden, anwenden, damit Sie Datamining von den Beispielen lernen kann, die Sie bereitstellen.  
  
-   Wenn Sie mit einem Wert arbeiten, der sich im Laufe der Zeit verändert und Sie ggf. zukünftige Trends vorhersagen möchten, denken Sie über die gewünschte Granularität der Ergebnisse nach. Möchten Sie Vorhersagen auf Grundlage eines Tages, Monats oder Jahres erstellen? Ihre Daten müssen mit den gleichen Einheiten analysiert werden, die Sie auch vorhersagen möchten.  
  
     Bei zyklischen Mustern, wenn Sie keine aussagekräftigen Ergebnisse mit täglichen Daten erhalten, versuchen Sie es anderen zeitlichen Segmenten, oder versuchen Sie es mit der Wochentage, Monate oder sogar Feiertage.  
  
-   Ehe Sie einen Assistenten starten, um neue Korrelationen in den Daten aufzudecken, nehmen Sie Ihre Daten eingehender unter die Lupe, und überlegen Sie, welche Art von bestehenden Beziehungen u. U. im Dataset vorhanden ist. Gibt es uneindeutige Variablen? Gibt es Duplikate oder Proxys?  
  
-   Was sind die Metriken, die mit denen der Erfolg des Modells ausgewertet werden soll? Wie wissen Sie, dass das Modell "gut genug"?  
  
-   Möchten Sie mit dem Data Mining-Modell Vorhersagen machen oder nur interessante Muster oder Zusammenhänge aufdecken?  
  
## <a name="explore-your-data-and-explore-the-model"></a>Untersuchen der Daten und Untersuchen des Modells  
 Möglicherweise sind Ihnen die Daten und die Domäne bereits sehr geläufig. Selbst wenn dies der Fall ist, sollten Sie einige Zeit aufwenden, Ihre Daten in Bezug auf die Modellierung aufzubereiten.  
  
 Nehmen Sie sich etwas Zeit, um die Verteilung der Werte zu überprüfen und potenzielle Probleme wie fehlende Werte oder Platzhalter zu bestimmen.  
  
 Wenn Sie zum Ausführen von Datamining für ein Dataset, das war zu groß oder komplex, dass Sie sie mit anderen Methoden analysieren konnte nicht planen, sollten Sie Sie Sampling oder eine Reduzierung der Datenmenge.  
  
-   Wie sind die Daten gestreut?  
  
-   Wie sind die Spalten miteinander verknüpft, oder (wenn es mehrere Tabellen gibt) wie sind die Tabellen miteinander verknüpft?  
  
-   Gibt es fehlende Werte? Gibt es Werte, die konvertiert oder vorverarbeitet werden müssen?  
  
-   Bestehen die Daten hauptsächlich aus Text, Zahlen oder beidem?  
  
-   Liegen genügend Daten für die Analyse der Zielergebnisse vor? Wenn Sie Zuordnungen zwischen Produkten analysieren, benötigen Sie u. U. weitaus mehr Daten. Bei der Vorhersage eines binären Ergebnisses kommen Sie mit weniger Daten aus, vorausgesetzt, das Dataset ist ausgeglichen.  
  
 Nach dem Abschluss des Modells sollten Sie die Ergebnisse eingehend überprüfen und Möglichkeiten ermitteln, die Daten zu ergänzen oder bessere Ergebnisse zu erzielen. Es ist außerordentlich selten, dass das erste Modell bereits alle Antworten liefert. Das Data Mining ist normalerweise ein iterativer Prozess.  
  
 Wenn Sie versuchen, Ihre Daten anders zu klassifizieren, oder Hinzufügen neuer Spalten zu verwenden, denken Sie daran den **Dokumentmodell** Assistenten, um eine Momentaufnahme der Metadaten und die Ergebnisse jedes einzelnen Modells aufzuzeichnen. Auf der Grundlage lückenloser Aufzeichnungen können Sie den Fortschritt Ihrer Untersuchungen besser nachverfolgen.  
  
 [Durchsuchen und Bereinigen von Daten](exploring-and-cleaning-data.md)  
  
## <a name="validate-your-model"></a>Überprüfen des Modells  
 Wenn Sie die einzelnen Assistenten und Tools ausführen, analysiert der Algorithmus die Inhalte der Daten und bestimmt, ob ein statistisch gültiges Muster vorliegt. Wenn der Algorithmus keine gültigen Muster finden kann, erhalten Sie eine Fehlermeldung angezeigt. Auch wenn ein Modell erfolgreich erstellt wurde, sollten Sie jedoch testen, um festzustellen, ob Ihre Annahmen bestätigt. Können Sie Tools wie z. B. die [Genauigkeitsdiagramm &#40;SQL Server Data Mining-Add-ins&#41; ](accuracy-chart-sql-server-data-mining-add-ins.md) oder [Kreuzvalidierung &#40;SQL Server Data Mining-Add-ins&#41; ](cross-validation-sql-server-data-mining-add-ins.md) um statistische zu erzeugen. Measures zur modellqualität.  
  
 Stellen Sie sich Fragen wie die Folgenden, während Sie die Ergebnisse des ersten Modells beurteilen:  
  
-   Welche Arten von Mustern wurden gefunden? Welche Wahrscheinlichkeiten und Unterstützungswerte liegen vor?  
  
-   Waren unsere Vermutungen zu Trends zutreffend, oder gibt es überraschende Korrelationen?  
  
-   Wurde eine ausreichende Datenmenge gesammelt? Würden durch Klassifizieren der Daten deutlichere Muster erzeugt?  
  
-   Ist das Dataset ausgeglichen? Mit der Kreuzvalidierung können Sie den repräsentativen Charakter der Daten testen.  
  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)  
  
 [Datamining-Client für Excel &#40;SQL Server Data Mining-Add-ins&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
 [Auswählen eines Modells](choosing-a-model.md)  
  
## <a name="explore-and-refine"></a>Durchsuchen und Optimieren  
 Wenn das Modell offensichtlich gültig ist, können Sie es verwenden, um Vorhersagen und Empfehlungen zu erstellen, um Erkenntnisse abzuleiten oder Geschäftsstrategien zu planen.  
  
-   Verwenden Sie den Data Mining-Browser im Data Mining-Client für Excel, um das Modell zu untersuchen und mit ihm zu interagieren.  
  
-   In Excel können Sie die Ergebnisse neu anordnen und filtern.  
  
-   Verwenden Sie Visio, um Präsentationen zu erstellen und die in den Daten festgestellten Beziehungen hervorzuheben.  
  
 Vom ersten Analyseergebnis lässt sich häufig ableiten, dass die Analyse noch verbessert werden kann oder dass neue, bessere Daten erforderlich sind. Da die mit den Data Mining-Add-Ins für Excel erstellten Modelle in einer Analysis Services-Instanz gespeichert werden können, ist es relativ einfach, das Modell mit neuen Daten zu aktualisieren, weiter zu verfeinern und erfolgreiche Modelle wiederzuverwenden.  
  
 Eine wichtige Aufgabe von Data Mining-Modellen besteht in der Erstellung von Vorhersagen und Empfehlungen. Die Data Mining-Add-Ins für Excel umfassen Tools, mit denen sich sogar komplexe Vorhersageabfragen auf einfache Weise erstellen lassen, um fundierte Einblicke in verwertbare Ergebnisse zu verwandeln. Alle Tools sind vollständig in Excel integriert.  
  
 [Anzeigen von Modellen &#40;Data Mining-Add-ins für Office&#41;](viewing-models-data-mining-add-ins-for-office.md)  
  
 [Validieren von Modellen und Verwenden von Modellen für Vorhersagen &#40;Data Mining-Add-ins für Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Was ist in der Data Mining-Add-Ins für Office enthalten](what-s-included-in-the-data-mining-add-ins-for-office.md)   
 [Technische Referenz für den &#40;Data Mining-Add-ins für Excel&#41;](technical-reference-data-mining-add-ins-for-excel.md)  
  
  
