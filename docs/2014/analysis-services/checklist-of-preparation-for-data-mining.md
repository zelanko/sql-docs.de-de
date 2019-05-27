---
title: Prüfliste der Vorbereitung für das Datamining | Microsoft-Dokumentation
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
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66088153"
---
# <a name="checklist-of-preparation-for-data-mining"></a>Prüfliste der Vorbereitung für Data Mining
  Data Mining-Add-Ins stellen eine einfache und unkomplizierte Methode zum Erstellen und Testen von Modellen dar. Wenn es Ihnen jedoch auf wiederholbare und aussagekräftige Ergebnisse ankommt, müssen Sie genügend Zeit einplanen, um grundlegende Geschäftsanforderungen zu formulieren und die erforderlichen Daten zu beschaffen und bereitzustellen. Dieser Abschnitt enthält eine Prüfliste, die Sie beim Planen Ihrer Untersuchung unterstützen soll. Darüber hinaus werden häufig auftretende Probleme beschrieben.  
  
## <a name="checklist-of-data-preparation"></a>Prüfliste für die Datenvorbereitung  
 **Ich haben eine eindeutig definierte Ausgabe identifiziert.**  
 Erstellen Sie einen Plan für die Verwendung der Ergebnisse. Verschiedene Modelltypen haben unterschiedliche Ausgaben. Ein Zeitreihenmodell generiert Werte für eine in der Zukunft liegende Reihe; diese ist leicht verständlich und verwertbar. Andere Modelle generieren komplexe Ergebnisse, die von Sachverständigen analysiert werden müssen, um den größtmöglichen Nutzen daraus zu ziehen.  
  
-   Welche Ausgabe wünschen Sie?  
  
-   Können Sie die Ausgabe als einzelne Spalte oder als einzelnen Wert oder anderweitig als verwertbares Ergebnis definieren?  
  
-   Anhand welcher Kriterien können Sie beurteilen, ob das Modell nützlich war?  
  
-   Wie nutzen und interpretieren Sie diese Ergebnisse?  
  
-   Können Sie den erwarteten Ergebnissen neue Eingabedaten zuordnen?  
  
 **Ich weiß der Bedeutung, Datentypen und Verteilung von Eingabedaten.**  
 Nehmen Sie sich ausreichend Zeit, um die Quelldaten zu untersuchen und zu verstehen. Die Personen, die mit dem Modell arbeiten, müssen wissen, welche Eingabedaten verwendet wurden und wie die Datentypen und die Variabilität sowie Ausgewogenheit und Qualität zu interpretieren sind.  
  
-   Wie viele Daten besitzen Sie? Ist eine ausreichende Menge von Daten für die Modellierung vorhanden?  
  
     Es muss keine riesige Menge – kleiner sein und mit Lastenausgleich kann besser sein.  
  
-   Stammen die Daten aus mehreren Quellen oder aus einer einzigen Quelle?  
  
-   Sind die Daten bereits verarbeitet und bereinigt? Sind weitere Eingabedaten verfügbar?  
  
-   Woher wissen Sie, wie bearbeitet wurden, bevor Sie empfangen – wie Daten gekürzt, zusammengefasst, konvertiert oder wurden möglicherweise?  
  
-   Enthalten die Eingabedaten einige Beispielergebnisse, die für das Training verwendet werden können?  
  
 **Ich habe verstanden, die Integrität der Daten, die wir haben und der benötigten Ebene.**  
 Fehlerhafte Daten können die Qualität des Modells beeinträchtigen oder die Modellerstellung von vornherein verhindern. Sie sollten weit reichende Kenntnisse sowohl über die Verteilung als auch über die Bedeutung der Daten haben und wissen, wie der aktuelle Zustand erreicht wurde. Sie müssen verstehen, ist es möglich oder angebracht, vereinfachen Sie die Daten durch beschriften, abschneiden numerischer Datentypen oder zusammenfassen.  
  
-   Sind die Datenbeschriftungen deutlich und richtig?  
  
-   Sind die Datentypen geeignet, und wurden sie ggf. geändert?  
  
-   Haben Sie falsche Daten aussortiert, bereinigt oder verworfen?  
  
     Haben Sie sich vergewissert, dass keine Duplikate vorhanden sind?  
  
-   Wie gehen Sie mit fehlenden Werten um? Was bedeuten fehlende Daten?  
  
-   Haben Sie die Quellen überprüft, um festzustellen, ob sich während des Importvorgangs eventuell Fehler eingeschlichen haben?  
  
     Wo ist die Eingabe gespeichert? Wie lange bleibt sie verfügbar?  
  
     Ist ein Datenwörterbuch vorhanden? Können Sie ein solches erstellen?  
  
-   Wenn Sie Datasets kombiniert haben: Haben Sie eine Überprüfung auf mehrere Spalten durchgeführt, die dieselben Daten darstellen?  
  
 **Ich weiß, in denen Quelldaten gespeichert sind, woher er stammt und wie sie verarbeitet wird. Der Prozess kann leicht wiederholt werden, bei Bedarf.**  
 Einmalige Datasets sind hervorragend für Experimente geeignet, aber wenn Sie jemals das Modell in der produktionsumgebung verschieben möchten, sollten Sie sich vorab Gedanken, wie der Bereinigungsprozess auf operative Daten angewendet werden kann. Wenn Sie operative Daten verfügen, müssen Sie auch wissen, wie sie geändert wurden möglicherweise bevor man es-müssen Sie wissen, wie sie gerundet oder zusammengefasst, natürlich.  
  
-   Möchten Sie in der Lage sein, das Experiment zu wiederholen?  
  
-   Welche Tools verwenden Sie, um Daten in einem Format vorzubereiten, das Datenanalysen unterstützt? Kann der Vorgang automatisiert werden, oder benötigen Sie jemanden, der die Daten in Excel überprüft und bereinigt?  
  
-   Sind Sie bei der Datenbeschaffung aus einem anderen System in der Lage, die angewendeten Filter zu erfassen und zu verfolgen?  
  
-   Ist Ihr Datenverarbeitungs-Framework in der Lage, Algorithmen für maschinelles Lernen anzuwenden, Tests auszuführen und Ergebnisse zu visualisieren?  
  
 **Wir haben vereinbart, auf der gewünschten detailgenauigkeit von Vorhersagen und unsere Daten wurde geändert, um diese Einheiten ausgegeben.**  
 Legen Sie vor der Vorbereitung von Daten fest, wie detailliert die Ergebnisse sein sollen. Möchten Sie Umsatzvorhersagen pro Tag oder Quartal erstellen? Sie können auch unterschiedliche Datenstrukturen für dieselben Daten einrichten, um verschiedene Zusammenfassungsebenen zu erhalten.  
  
-   Welche Maßeinheit oder Zeiteinheit wird derzeit verwendet?  
  
     Welche Einheit möchten Sie in den Ergebnissen verwenden?  
  
-   Ist es möglich, eine grundlegende aufgabeneinheit definieren (z. B. Tag / Stunde / Minute / Anweisungsaufruf) für alle Eingabedaten?  
  
     Möchten Sie ein Rollup auf übergeordnete Einheiten durchführen?  
  
-   Sind Kategorien einheitlich beschriftet? Können Kategorien einfach hinzugefügt oder entfernt werden?  
  
 **Unsere experimentelle wäre die wiederholbare und reproduzierbare.**  
 Überdenken Sie Strategien zum Analysieren und Überprüfen der Ergebnisse, und planen Sie das Aufzeichnen einer Momentaufnahme der Daten, um sicherzustellen, dass Sie Auswirkungen zu den Daten zurückverfolgen können. Wenn ein zufälliger Ausgangswert verwendet wird, können sich die Ergebnisse leicht unterscheiden. Dadurch können sich der Vergleich und die Validierung der Modelle schwierig gestalten.  
  
-   Wie wirken sich zahlreiche benutzerdefinierte Änderungen an den Daten auf das nächste Erstellen des Modells aus?  
  
-   Wurde bereits ein manuelles Verfahren oder ein genehmigter Prozess definiert, mit dem die Eingabe verarbeitet und die gewünschten Ausgaben abgerufen werden sollen?  
  
-   Haben Sie festgelegt, dass ein Ausgangswert für das Modell verwendet werden soll?  
  
 **Wir haben Fachwissen, um die Ergebnisse zu überprüfen, oder haben Zugriff auf den betrachteten Gegenstands-Experten beraten kann.**  
 Nehmen Sie sich ausreichend Zeit, um die Variablen, das Modell und die Ergebnisse zu überprüfen. Nehmen Sie beim Bewerten von Interaktionen und Ergebnissen die Unterstützung von Experten in Anspruch. Lassen Sie nicht jedoch Annahmen, die Beweise. Seien Sie offen für neue und unerwartete Ergebnisse.  
  
-   Ist Domänenwissen vorhanden, welches das Filtern von Daten und das Mindern von Eingaberauschen erleichtert?  
  
-   Können Domänenexperten dazu beitragen, die Ergebnisse zu verstehen und zu interpretieren, und können sie Verbesserungen vorschlagen?  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen von Daten für das Data Mining](choosing-data-for-data-mining.md)  
  
  
