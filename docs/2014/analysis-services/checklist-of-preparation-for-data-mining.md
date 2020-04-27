---
title: Prüfliste zur Vorbereitung für Data Mining | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e056c95-ba06-413e-8dc1-4d411a447c3b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9a20fde7ebe09a3e57af504846cf010c8120ffbc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66088153"
---
# <a name="checklist-of-preparation-for-data-mining"></a>Prüfliste der Vorbereitung für Data Mining
  Data Mining-Add-Ins stellen eine einfache und unkomplizierte Methode zum Erstellen und Testen von Modellen dar. Wenn es Ihnen jedoch auf wiederholbare und aussagekräftige Ergebnisse ankommt, müssen Sie genügend Zeit einplanen, um grundlegende Geschäftsanforderungen zu formulieren und die erforderlichen Daten zu beschaffen und bereitzustellen. Dieser Abschnitt enthält eine Prüfliste, die Sie beim Planen Ihrer Untersuchung unterstützen soll. Darüber hinaus werden häufig auftretende Probleme beschrieben.  
  
## <a name="checklist-of-data-preparation"></a>Prüfliste für die Datenvorbereitung  
 **Identifikation klar definierter Ausgabedaten**  
 Erstellen Sie einen Plan für die Verwendung der Ergebnisse. Verschiedene Modelltypen haben unterschiedliche Ausgaben. Ein Zeitreihenmodell generiert Werte für eine in der Zukunft liegende Reihe; diese ist leicht verständlich und verwertbar. Andere Modelle generieren komplexe Ergebnisse, die von Sachverständigen analysiert werden müssen, um den größtmöglichen Nutzen daraus zu ziehen.  
  
-   Welche Ausgabe wünschen Sie?  
  
-   Können Sie die Ausgabe als einzelne Spalte oder als einzelnen Wert oder anderweitig als verwertbares Ergebnis definieren?  
  
-   Anhand welcher Kriterien können Sie beurteilen, ob das Modell nützlich war?  
  
-   Wie nutzen und interpretieren Sie diese Ergebnisse?  
  
-   Können Sie den erwarteten Ergebnissen neue Eingabedaten zuordnen?  
  
 **Grundlegendes Verständnis der Bedeutung, Datentypen und Verteilung von Eingabedaten**  
 Nehmen Sie sich ausreichend Zeit, um die Quelldaten zu untersuchen und zu verstehen. Die Personen, die mit dem Modell arbeiten, müssen wissen, welche Eingabedaten verwendet wurden und wie die Datentypen und die Variabilität sowie Ausgewogenheit und Qualität zu interpretieren sind.  
  
-   Wie viele Daten besitzen Sie? Ist eine ausreichende Menge von Daten für die Modellierung vorhanden?  
  
     Es muss nicht sehr groß sein, und es kann besser werden.  
  
-   Stammen die Daten aus mehreren Quellen oder aus einer einzigen Quelle?  
  
-   Sind die Daten bereits verarbeitet und bereinigt? Sind weitere Eingabedaten verfügbar?  
  
-   Wissen Sie, wie Sie bearbeitet wurde, bevor Sie Sie erhalten haben. wie können Daten abgeschnitten, zusammengefasst oder konvertiert werden?  
  
-   Enthalten die Eingabedaten einige Beispielergebnisse, die für das Training verwendet werden können?  
  
 **Genaue Vorstellungen von der Datenintegrität – wie ist der aktuelle Zustand und welcher Zustand soll erreicht werden?**  
 Fehlerhafte Daten können die Qualität des Modells beeinträchtigen oder die Modellerstellung von vornherein verhindern. Sie sollten weit reichende Kenntnisse sowohl über die Verteilung als auch über die Bedeutung der Daten haben und wissen, wie der aktuelle Zustand erreicht wurde. Sie müssen sich darüber im klaren sein, ob es möglich oder sinnvoll ist, die Daten zu vereinfachen, indem Sie die Bezeichnung, die abkürzen numerischer Datentypen oder eine Zusammenfassung durch fassen.  
  
-   Sind die Datenbeschriftungen deutlich und richtig?  
  
-   Sind die Datentypen geeignet, und wurden sie ggf. geändert?  
  
-   Haben Sie falsche Daten aussortiert, bereinigt oder verworfen?  
  
     Haben Sie sich vergewissert, dass keine Duplikate vorhanden sind?  
  
-   Wie gehen Sie mit fehlenden Werten um? Was bedeuten fehlende Daten?  
  
-   Haben Sie die Quellen überprüft, um festzustellen, ob sich während des Importvorgangs eventuell Fehler eingeschlichen haben?  
  
     Wo ist die Eingabe gespeichert? Wie lange bleibt sie verfügbar?  
  
     Ist ein Datenwörterbuch vorhanden? Können Sie ein solches erstellen?  
  
-   Wenn Sie Datasets kombiniert haben: Haben Sie eine Überprüfung auf mehrere Spalten durchgeführt, die dieselben Daten darstellen?  
  
 **Ich weiß, wo Quelldaten gespeichert werden, woher Sie stammen und wie Sie verarbeitet werden. Der Prozess kann bei Bedarf problemlos wiederholt werden.**  
 Einmalige Datasets sind für Experimente gut, aber wenn Sie das Modell jemals in die Produktion verschieben möchten, sollten Sie sich im Voraus Gedanken darüber machen, wie der Reinigungsprozess auf operative Daten angewendet werden kann. Wenn Sie über operative Daten verfügen, müssen Sie sich darüber informieren, wie diese möglicherweise geändert wurden, bevor Sie Sie erhalten. Sie müssen wissen, wie Sie gerundet oder zusammengefasst wurden.  
  
-   Möchten Sie in der Lage sein, das Experiment zu wiederholen?  
  
-   Welche Tools verwenden Sie, um Daten in einem Format vorzubereiten, das Datenanalysen unterstützt? Kann der Vorgang automatisiert werden, oder benötigen Sie jemanden, der die Daten in Excel überprüft und bereinigt?  
  
-   Sind Sie bei der Datenbeschaffung aus einem anderen System in der Lage, die angewendeten Filter zu erfassen und zu verfolgen?  
  
-   Ist Ihr Datenverarbeitungs-Framework in der Lage, Algorithmen für maschinelles Lernen anzuwenden, Tests auszuführen und Ergebnisse zu visualisieren?  
  
 **Festlegen der gewünschten Detailgenauigkeit von Vorhersagen und Anpassung der Daten an die Ausgabeeinheiten**  
 Legen Sie vor der Vorbereitung von Daten fest, wie detailliert die Ergebnisse sein sollen. Möchten Sie Umsatzvorhersagen pro Tag oder Quartal erstellen? Sie können auch unterschiedliche Datenstrukturen für dieselben Daten einrichten, um verschiedene Zusammenfassungsebenen zu erhalten.  
  
-   Welche Maßeinheit oder Zeiteinheit wird derzeit verwendet?  
  
     Welche Einheit möchten Sie in den Ergebnissen verwenden?  
  
-   Ist es möglich, eine grundlegende Einheit (z. b. Tag/Stunde/Minute/Anweisungs Befehl) für alle Eingabedaten zu definieren?  
  
     Möchten Sie ein Rollup auf übergeordnete Einheiten durchführen?  
  
-   Sind Kategorien einheitlich beschriftet? Können Kategorien einfach hinzugefügt oder entfernt werden?  
  
 **Wiederholbare und reproduzierbare Versuchsanordnung**  
 Überdenken Sie Strategien zum Analysieren und Überprüfen der Ergebnisse, und planen Sie das Aufzeichnen einer Momentaufnahme der Daten, um sicherzustellen, dass Sie Auswirkungen zu den Daten zurückverfolgen können. Wenn ein zufälliger Ausgangswert verwendet wird, können sich die Ergebnisse leicht unterscheiden. Dadurch können sich der Vergleich und die Validierung der Modelle schwierig gestalten.  
  
-   Wie wirken sich zahlreiche benutzerdefinierte Änderungen an den Daten auf das nächste Erstellen des Modells aus?  
  
-   Wurde bereits ein manuelles Verfahren oder ein genehmigter Prozess definiert, mit dem die Eingabe verarbeitet und die gewünschten Ausgaben abgerufen werden sollen?  
  
-   Haben Sie festgelegt, dass ein Ausgangswert für das Modell verwendet werden soll?  
  
 **Fundiertes Fachwissen, um die Ergebnisse überprüfen zu können, oder fachliche Unterstützung von Experten**  
 Nehmen Sie sich ausreichend Zeit, um die Variablen, das Modell und die Ergebnisse zu überprüfen. Nehmen Sie beim Bewerten von Interaktionen und Ergebnissen die Unterstützung von Experten in Anspruch. Lassen Sie jedoch keine Annahmen über Regel Beweise aus. Seien Sie offen für neue und unerwartete Ergebnisse.  
  
-   Ist Domänenwissen vorhanden, welches das Filtern von Daten und das Mindern von Eingaberauschen erleichtert?  
  
-   Können Domänenexperten dazu beitragen, die Ergebnisse zu verstehen und zu interpretieren, und können sie Verbesserungen vorschlagen?  
  
## <a name="see-also"></a>Weitere Informationen  
 [Auswählen von Daten für das Data Mining](choosing-data-for-data-mining.md)  
  
  
