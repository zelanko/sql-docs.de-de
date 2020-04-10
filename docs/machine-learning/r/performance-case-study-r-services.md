---
title: Leistungsoptimierung für Ergebnisse
description: In diesem Artikel werden die Methoden, Ergebnisse und Schlussfolgerungen zweier Fallstudien zusammengefasst, in denen verschiedene Optimierungsmethoden getestet wurden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 19935bbcaba9b856ff04b5c618de3b3643e48732
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "81117573"
---
# <a name="performance-for-r-services-results-and-resources"></a>Leistungsoptimierung für R Services: Ergebnisse und Ressourcen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel ist der vierte und letzte in einer Reihe, in der die Leistungsoptimierung für R Services beschrieben wird. In diesem Artikel werden die Methoden, Ergebnisse und Schlussfolgerungen zweier Fallstudien zusammengefasst, in denen verschiedene Optimierungsmethoden getestet wurden.

Die beiden Fallstudien besaßen unterschiedliche Ziele:

+ Die erste Fallstudie wurde vom R Services-Entwicklungsteam durchgeführt mit dem Ziel, die Auswirkungen bestimmter Techniken zur Leistungsoptimierung zu messen.
+ In der zweiten Fallstudie experimentierte ein Team aus Datenanalysten mit verschiedenen Methoden, um die besten Optimierungen für ein bestimmtes Bewertungsszenario mit hohem Volumen zu ermitteln.

In diesem Thema werden die Ergebnisse der ersten Fallstudie im Detail aufgeführt. Zudem werden die Gesamtergebnisse der zweiten Fallstudie zusammengefasst. Am Ende dieses Themas finden Sie Links zu allen Skripts und Beispieldaten sowie zu den Ressourcen, die von den ursprünglichen Autoren verwendet wurden.

## <a name="performance-case-study-airline-dataset"></a>Fallstudie zur Leistungsoptimierung: Airline-Dataset

In dieser Fallstudie testete das Entwicklungsteam von SQL Server R Services die Auswirkungen verschiedener Optimierungen. Es wurde ein einzelnes rxLogit-Modell erstellt und eine Bewertung für das Airline-Dataset durchgeführt. Während des Trainings- und Bewertungsprozesses wurden verschiedene Optimierungen angewendet und deren Auswirkungen bewertet.

- GitHub: [Beispieldaten und Skripts](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning) für die Studie zu SQL Server-Optimierungen

### <a name="test-methods"></a>Testmethoden

1. Das Airline-Dataset besteht aus einer einzelnen Tabelle mit 10 Millionen Zeilen. Sie wurde heruntergeladen und in einem Massenvorgang in SQL Server geladen.
2. Es wurden sechs Kopien der Tabelle erstellt.
3. Auf die Kopien der Tabelle wurden verschiedene Änderungen angewendet, um SQL Server-Funktionen wie Seitenkomprimierung, Zeilenkomprimierung, Indizierung, Spaltendatenspeicher usw. zu testen.
4. Die Leistung wurde jeweils vor und nach jeder Optimierung gemessen.

| Tabellenname| BESCHREIBUNG|
|------|------|
| *airline* | Aus der ursprünglichen XDF-Datei mithilfe von `rxDataStep` konvertierte Daten.|                          |
| *airlineWithIntCol*   | *DayOfWeek* konvertiert in eine Ganzzahl anstatt in eine Zeichenfolge. Fügt auch eine *rowNum*-Spalte hinzu.|
| *airlineWithIndex*    | Die gleichen Daten wie in der *airlineWithIntCol*-Tabelle, jedoch mit einem einzigen gruppierten Index mit *rowNum*-Spalte.|
| *airlineWithPageComp* | Die gleichen Daten wie in der *airlineWithIndex*-Tabelle, jedoch mit aktivierter Seitenkomprimierung. Fügt auch die beiden Spalten *CRSDepHour* und *Late* hinzu, die aus *CRSDepTime* und *ArrDelay* berechnet werden. |
| *airlineWithRowComp*  | Die gleichen Daten wie in der *airlineWithIndex*-Tabelle, jedoch mit aktivierter Zeilenkomprimierung. Fügt auch die beiden Spalten *CRSDepHour* und *Late* hinzu, die aus *CRSDepTime* und *ArrDelay* berechnet werden. |
| *airlineColumnar*     | Ein spaltenbasierter Speicher mit einem einzigen gruppierten Index. Diese Tabelle wird mit Daten aus einer bereinigten CSV-Datei aufgefüllt.|

Jeder Test bestand aus den folgenden Schritten:

1. Die automatische Speicherbereinigung für R wurde vor jedem Test eingeleitet.
2. Basierend auf den Tabellendaten wurde ein logistisches Regressionsmodell erstellt. Der Wert von *rowsPerRead* wurde für jeden Test auf 500000 festgelegt.
3. Bewertungen wurden mithilfe des trainierten Modells generiert.
4. Jeder Test wurde sechs Mal ausgeführt. Die Zeit der ersten Ausführung (des „Kaltlaufs“) wurde gelöscht. Damit gelegentliche Ausreißer das Ergebnis nicht verfälschen, wurde die **längste** Zeit der verbleibenden fünf Ausführungen ebenfalls gelöscht. Der Durchschnitt der vier verbleibenden Ausführungen wurde verwendet, um die durchschnittliche verstrichene Laufzeit jedes Tests zu berechnen.
5. Für die Ausführung der Tests wurde der Parameter *reportProgress* auf den Wert 3 festgelegt (= Zeiten und Fortschritt werden gemeldet). Jede Ausgabedatei enthielt Informationen über die E/A-Zeit, die Übergangszeit und die Computezeit. Diese Zeiten sind nützlich für die Problembehandlung und Diagnose.
6. Auch die Konsolenausgabe wurde in eine Datei im Ausgabeverzeichnis geleitet.
7. Mit den Testskripts wurden die Zeiten in den Dateien zur Berechnung der durchschnittlichen Zeit für die Ausführung verarbeitet.

Die folgenden Ergebnisse stellen beispielsweise die Zeiten eines einzelnen Tests dar. Die wichtigsten Zeiten sind **Gesamte Lesezeit** (E/A-Zeit) und **Übergangszeit** (Aufwand für das Einrichten von Prozessen für die Berechnung).

**Beispielzeiten**

```text
Running IntCol Test. Using airlineWithIntCol table.
run 1 took 3.66 seconds
run 2 took 3.44 seconds
run 3 took 3.44 seconds
run 4 took 3.44 seconds
run 5 took 3.45 seconds
run 6 took 3.75 seconds
  
Average Time: 3.4425
metric time pct
1 Total time 3.4425 100.00
2 Overall compute time 2.8512 82.82
3 Total read time 2.5378 73.72
4 Transition time 0.5913 17.18
5 Total non IO time 0.3134 9.10
```

Es wird empfohlen, die Testskripts herunterzuladen und zu ändern, um Probleme mit R Services oder RevoScaleR-Funktionen beheben zu können.

### <a name="test-results-all"></a>Testergebnisse (gesamt)

In diesem Abschnitt werden die Ergebnisse vor und nach der Ausführung der einzelnen Tests miteinander verglichen.

#### <a name="data-size-with-compression-and-a-columnar-table-store"></a>Datengröße bei Komprimierung und einem spaltenbasierten Tabellenspeicher

Im ersten Test wurden die Verwendung von Komprimierung und die Verwendung einer spaltenbasierten Tabelle zur Verringerung der Datengröße miteinander verglichen:

| Tabellenname            | Zeilen     | Reserved   | Daten       | index_size | Nicht verwendet  | % Gespeichert (reserviert) |
|-----------------------|----------|------------|------------|------------|---------|---------------------|
| *airlineWithIndex*    | 10000000 | 2\.978.816 KB | 2\.972.160 KB | 6\.128 KB    | 528 KB  | 0                   |
| *airlineWithPageComp* | 10000000 | 625.784 KB  | 623.744 KB  | 1\.352 KB    | 688 KB  | 79%                 |
| *airlineWithRowComp*  | 10000000 | 1\.262.520 KB | 1\.258.880 KB | 2\.552 KB    | 1\.088 KB | 58%                 |
| *airlineColumnar*     | 9999999  | 201.992 KB  | 201.624 KB  | –        | 368 KB  | 93%                 |

**Schlussfolgerungen**

Die Datengröße konnte am meisten durch Anwendung eines Columnstore-Index verringert werden, gefolgt von der Seitenkomprimierung.

#### <a name="effects-of-compression"></a>Auswirkungen von Komprimierung

In diesem Test wurden die Auswirkungen von Zeilenkomprimierung, Seitenkomprimierung und keiner Komprimierung miteinander verglichen. Ein Modell wurde mit `rxLinMod` für Daten aus drei verschiedenen Datentabellen trainiert. Für alle Tabellen wurde dieselbe Formel und Abfrage verwendet.

| Tabellenname            | Testname       | numTasks | Durchschnittliche Zeit |
|-----------------------|-----------------|----------|--------------|
| *airlineWithIndex*    | NoCompression   | 1        | 5.6775       |
|                       | NoCompression - parallel| 4        | 5.1775       |
| *airlineWithPageComp* | PageCompression | 1        | 6.7875       |
|                       | PageCompression - parallel | 4        | 5.3225       |
| *airlineWithRowComp*  | RowCompression  | 1        | 6.1325       |
|                       | RowCompression - parallel  | 4        | 5.2375       |

**Schlussfolgerungen**

Die Komprimierung allein scheint keine Vorteile zu bringen. In diesem Beispiel gleicht die Erhöhung der CPU zur Verarbeitung der Komprimierung die Verringerung der E/A-Zeit aus.

Wenn der Test jedoch parallel ausgeführt wird, indem *numTasks* auf 4 festgelegt wird, verringert sich die durchschnittliche Zeit.

Bei größeren Datasets kann die Auswirkung der Komprimierung deutlicher bemerkbar sein. Die Komprimierung hängt ab von Dataset und Werten, sodass möglicherweise durch Ausprobieren festgestellt werden muss, welche Auswirkung die Komprimierung auf Ihr Dataset hat.

### <a name="effect-of-windows-power-plan-options"></a>Auswirkungen der Optionen des Windows-Energiesparplans

In diesem Experiment wurde `rxLinMod` mit der *airlineWithIntCol*-Tabelle verwendet. Der Energiesparplan von Windows wurde einmal auf **Ausbalanciert** und einmal **Höchstleistung** festgelegt. Für alle Tests wurde *numTasks* auf 1 festgelegt. Der Test wurde sechsmal ausgeführt, davon je zweimal für jede Energiesparoption, um die Variabilität der Ergebnisse zu untersuchen.

Energiesparoption **Höchstleistung**:

| Testname | Ausführen von \# | Verstrichene Zeit | Durchschnittliche Zeit |
|-----------|--------|--------------|--------------|
| IntCol    | 1      | 3,57 Sekunden |              |
|           | 2      | 3,45 Sekunden |              |
|           | 3      | 3,45 Sekunden |              |
|           | 4      | 3,55 Sekunden |              |
|           | 5      | 3,55 Sekunden |              |
|           | 6      | 3,45 Sekunden |              |
|           |        |              | 3.475        |
|           | 1      | 3,45 Sekunden |              |
|           | 2      | 3,53 Sekunden |              |
|           | 3      | 3,63 Sekunden |              |
|           | 4      | 3,49 Sekunden |              |
|           | 5      | 3,54 Sekunden |              |
|           | 6      | 3,47 Sekunden |              |
|           |        |              | 3.5075       |

Energiesparoption **Ausgeglichen**:

| Testname | Ausführen von \# | Verstrichene Zeit | Durchschnittliche Zeit |
|-----------|--------|--------------|--------------|
| IntCol    | 1      | 3,89 Sekunden |              |
|           | 2      | 4,15 Sekunden |              |
|           | 3      | 3,77 Sekunden |              |
|           | 4      | 5 Sekunden    |              |
|           | 5      | 3,92 Sekunden |              |
|           | 6      | 3,8 Sekunden  |              |
|           |        |              | 3,91         |
|           | 1      | 3,82 Sekunden |              |
|           | 2      | 3,84 Sekunden |              |
|           | 3      | 3,86 Sekunden |              |
|           | 4      | 4,07 Sekunden |              |
|           | 5      | 4,86 Sekunden |              |
|           | 6      | 3,75 Sekunden |              |
|           |        |              | 3.88         |

**Schlussfolgerungen**

Die Ausführungszeit ist konsistenter und kürzer, wenn die Windows-Energiesparoption **Höchstleistung** verwendet wird.

#### <a name="using-integer-vs-strings-in-formulas"></a>Verwenden von ganzen Zahlen im Vergleich zu Zeichenfolgen in Formeln

In diesem Test wurden die Auswirkungen von Änderungen im R-Code zur Vermeidung eines gängigen Problems mit Zeichenfolgen als Faktoren bewertet. Ein Modell wurde mit `rxLinMod` für zwei Tabellen trainiert: In der ersten Tabelle wurden Faktoren als Zeichenfolgen gespeichert, in der zweiten als ganze Zahlen.

+ In der *Airline*-Tabelle enthielt die Spalte „[DayOfWeek]“ Zeichenfolgen. Der Parameter _colInfo_ wurde zur Angabe der Faktorebenen (Montag, Dienstag usw.) verwendet.

+  In der *AirlineWithIndex*-Tabelle enthielt die Spalte „[DayOfWeek]“ ganze Zahlen. Der Parameter _colInfo_ wurde nicht angegeben.

+ In beiden Fällen wurde dieselbe Formel `ArrDelay ~ CRSDepTime + DayOfWeek` verwendet.

| Tabellenname          | Testname   | Durchschnittliche Zeit |
|---------------------|-------------|--------------|
| *Airline*           | *FactorCol* | 10.72        |
| *airlineWithIntCol* | *IntCol*    | 3.4475       |

**Schlussfolgerungen**

Die Verwendung von ganzen Zahlen als Faktoren besitzt einen deutlichen Vorteil gegenüber der Verwendung von Zeichenfolgen.

### <a name="avoiding-transformation-functions"></a>Vermeiden von Transformationsfunktionen

In diesem Test wurde ein Modell mit `rxLinMod` trainiert, doch der Code wurde vor der zweiten Ausführung geändert:

+ Bei der ersten Ausführung wurde eine Transformationsfunktion als Teil der Modellbildung angewendet. 
+ Für die zweite Ausführung wurden die Funktionswerte vorausberechnet und waren verfügbar, weshalb keine Transformationsfunktion erforderlich war.

| Testname             | Durchschnittliche Zeit |
|-----------------------|--------------|
| WithTransformation    | 5.1675       |
| WithoutTransformation | 4,7          |

**Schlussfolgerungen**

Wenn **keine** Transformationsfunktion verwendet wurde, war die Trainingszeit kürzer. Das heißt, dass das Modell mit vorausberechneten und in der Tabelle gespeicherten Spalten schneller trainiert werden konnte.

Die Zeitersparnis sollte bei einer höheren Anzahl von Transformationen und einem umfangreicheren Dataset (\> 100 Millionen) größer ausfallen.

### <a name="using-columnar-store"></a>Verwenden von spaltenbasiertem Speicher

In diesem Test wurden die Leistungsvorteile bei Verwendung eines spaltenbasierten Datenspeichers und eines Index bewertet. Das Modell wurde einmal mit `rxLinMod` und einmal ohne Datentransformationen trainiert.

+ Bei der ersten Ausführung verwendete die Datentabelle einen Rowstore-Standardspeicher.
+ Bei der zweiten Ausführung wurde ein Columnstore verwendet.

| Tabellenname         | Testname | Durchschnittliche Zeit |
|--------------------|-----------|--------------|
| *airlineWithIndex* | RowStore  | 4.67         |
| *airlineColumnar*  | ColStore  | 4.555        |

**Schlussfolgerungen**

Mit dem spaltenbasierten Speicher konnte eine höhere Leistung erzielt werden als mit dem zeilenbasierten Standardspeicher. Bei größeren Datasets (\> 100 Millionen) ist ein deutlicher Leistungsunterschied zu erwarten.

### <a name="effect-of-using-the-cube-parameter"></a>Auswirkung des Cube-Parameters

Mit diesem Test sollte herausgefunden werden, ob die RevoScaleR-Option zur Verwendung des vorausberechneten **Cube**-Parameters die Leistung verbessert. Ein Modell wurde mit `rxLinMod` unter Verwendung der folgenden Formel trainiert:

```R
ArrDelay ~ Origin:DayOfWeek + Month + DayofMonth + CRSDepTime
```

In der Tabelle wurden die Faktoren *DayOfWeek* als Zeichenfolgen gespeichert.

| Testname     | Cube-Parameter | numTasks | Durchschnittliche Zeit | Vorhersage einzelner Zeile (ArrDelay_Pred) |
|---------------|----------------|----------|--------------|---------------------------------|
| CubeArgEffect | `cube = F`     | 1        | 91.0725      | 9.959204                        |
|               |                | 4        | 44.09        | 9.959204                        |
|               | `cube = T`     | 1        | 21.1125      | 9.959204                        |
|               |                | 4        | 8.08         | 9.959204                        |

**Schlussfolgerungen**

Durch Verwendung des Cube-Parameterarguments konnte die Leistung deutlich verbessert werden.

### <a name="effect-of-changing-maxdepth-for-rxdtree-models"></a>Auswirkung der Änderung von „maxDepth“ für rxDTree-Modelle

In diesem Experiment wurde mit dem `rxDTree`-Algorithmus ein Modell für die Tabelle *airlineColumnar* erstellt. Für diesen Test wurde *numTasks* auf 4 festgelegt. Es wurden verschiedene Werte für *maxDepth* verwendet, um zu veranschaulichen, wie eine Veränderung der Strukturtiefe die Laufzeit beeinflusst.

| Testname       | maxDepth | Durchschnittliche Zeit |
|-----------------|----------|--------------|
| TreeDepthEffect | 1        | 10.1975      |
|                 | 2        | 13.2575      |
|                 | 4        | 19.27        |
|                 | 8        | 45.5775      |
|                 | 16       | 339.54       |

**Schlussfolgerungen**

Mit zunehmender Strukturtiefe erhöhte sich die Gesamtzahl der Knoten exponentiell. Die für die Erstellung des Modells benötigte Zeit erhöhte sich ebenfalls erheblich.

### <a name="prediction-on-a-stored-model"></a>Vorhersage mithilfe eines gespeicherten Modells

Mit diesem Test sollte herausgefunden werden, wie sich die Leistung auf die Bewertung auswirkt, wenn das trainierte Modell in einer SQL Server-Tabelle gespeichert und nicht als Teil des aktuell ausgeführten Codes generiert wird. Für die Bewertung wurde das gespeicherte Modell aus der Datenbank geladen, und Vorhersagen wurden mit einem einzeiligen Datenrahmen im Arbeitsspeicher (lokaler Computekontext) erstellt.

Die Testergebnisse zeigen die Zeit, die für das Speichern und Laden des Modells sowie für die Vorhersage benötigt wird.

| Tabellenname | Testname | Durchschnittliche Zeit (Trainieren des Modells) | Zeit zum Speichern/Laden des Modells|
|------------|------------|------------|------------|
| Fluggesellschaft    | SaveModel| 21.59| 2,08|
| Fluggesellschaft    | LoadModelAndPredict | | 2,09 (einschließlich Zeit für Vorhersagen) |

**Schlussfolgerungen**

Durch Laden eines trainierten Modells aus einer Tabelle konnte eine deutlich schnellere Vorhersage erzielt werden. Es wird empfohlen, dasselbe Skript nicht gleichzeitig zum Erstellen des Modells und zur Bewertung zu verwenden.

## <a name="case-study-optimization-for-the-resume-matching-task"></a>Fallstudie: Optimierung der Aufgabe für den Abgleich von Lebensläufen

Das Modell für den Abgleich von Lebensläufen wurde vom Microsoft-Datenanalysten Ke Huang entwickelt, um die Leistung von R-Code in SQL Server zu testen. Dadurch sind Datenanalysten in der Lage, skalierbare Lösungen auf Unternehmensebene zu erstellen.

### <a name="methods"></a>Methoden

Ein Vorhersagemodell wurde mit den beiden Paketen RevoScaleR und MicrosoftML in einer komplexen R-Lösung mit großen Datasets trainiert. Dabei wurden in allen Tests dieselben SQL-Abfragen und derselbe R-Code verwendet. Die Tests wurden auf einem einzelnen virtuellen Azure-Computer ausgeführt, auf dem SQL Server installiert war. Anschließend verglich der Autor die Bewertungszeiten bei Verwendung der folgenden von SQL Server bereitgestellten Optimierungen mit denen ohne Optimierungen:

- In-Memory-Tabellen
- Soft-NUMA
- Resource Governor

Zur Bewertung der Auswirkung von Soft-NUMA auf die Ausführung von R-Skripts testete das Data Science-Team die Lösung auf einem virtuellen Azure-Computer mit zwanzig physischen Kernen. Auf den physischen Kernen wurden automatisch vier Soft-NUMA-Knoten erstellt, sodass jeder Knoten fünf Kerne enthielt.

Die CPU-Affinität wurde im Szenario für den Abgleich von Lebensläufen erzwungen, um die Auswirkungen auf R-Aufträge zu bewerten. Es wurden vier **SQL-Ressourcenpools** und vier **externe Ressourcenpools** erstellt. Dabei wurde die CPU-Affinität angegeben, um sicherzustellen, dass in jedem Knoten die gleichen CPUs verwendet werden.

Jeder Ressourcenpool wurde für eine optimale Hardwarenutzung einer anderen Arbeitsauslastungsgruppe zugewiesen. Der Grund hierfür liegt darin, dass die Soft-NUMA- und CPU-Affinitäten den physischen Speicher in den physischen NUMA-Knoten nicht aufteilen können. Daher müssen alle Soft-NUMA-Knoten, die auf demselben physischen NUMA-Knoten basieren, definitionsgemäß Arbeitsspeicher im selben Speicherblock des Betriebssystems verwenden. Anders ausgedrückt: Es gibt keine Affinität zwischen Speicher und Prozessor.

Erstellen Sie diese Konfiguration mit den folgenden Schritten:

1. Reduzieren Sie die Menge an Arbeitsspeicher, die SQL Server standardmäßig zugeordnet wird.

2. Erstellen Sie vier neue Pools zur parallelen Ausführung der R-Aufträge.

3. Erstellen Sie vier Arbeitsauslastungsgruppen, sodass jede Gruppe einem Ressourcenpool zugeordnet wird.

4. Starten Sie Resource Governor mit den neuen Arbeitsauslastungsgruppen und Zuordnungen neu.

5. Erstellen Sie eine benutzerdefinierte Klassifizierungsfunktion, um den einzelnen Arbeitsauslastungsgruppen unterschiedliche Aufgaben zuzuweisen.

6. Aktualisieren Sie die Konfiguration von Resource Governor, um die Funktion für die entsprechenden Arbeitsauslastungsgruppen zu verwenden.

### <a name="results"></a>Ergebnisse

Die beste Leistung in der Studie für den Abgleich von Lebensläufen erzielte die folgende Konfiguration:

-   Vier interne Ressourcenpools (für SQL Server)

-   Vier externe Ressourcenpools (für externe Skriptaufträge)

-   Jeder Ressourcenpool wird einer bestimmten Arbeitsauslastungsgruppe zugeordnet.

-   Jeder Ressourcenpool wird unterschiedlichen CPUs zugewiesen.

-   Maximale interne Speicherauslastung (für SQL Server) = 30 %

-   Maximaler Speicher für R-Sitzungen = 70 %

Das Modell für den Abgleich von Lebensläufen verwendete eine hohe Anzahl externer Skripts, und es wurden keine anderen Datenbank-Engine-Dienste ausgeführt. Daher wurden die den externen Skripts zugeordneten Ressourcen auf 70 % erhöht, was sich als die beste Konfiguration für die Skriptleistung erwies.

Diese Konfiguration wurde durch Experimentieren mit unterschiedlichen Werten ermittelt. Wenn Sie eine andere Hardware oder Lösung verwenden, kann die optimale Konfiguration davon abweichen. Probieren Sie mehrere Werte aus, um die für Sie beste Konfiguration zu finden.

In der optimierten Lösung wurden 1,1 Millionen Datenzeilen (mit 100 Funktionen) in weniger als 8,5 Sekunden auf einem Computer mit zwanzig Kernen bewertet. Durch die Optimierungen konnte die Leistung in Hinblick auf die Bewertungszeit erheblich gesteigert werden.

Die Ergebnisse legten auch nahe, dass die **Anzahl der Funktionen** erhebliche Auswirkungen auf die Bewertungszeit besaß. Die Leistungssteigerung fiel noch deutlicher aus, wenn im Vorhersagemodell eine höhere Anzahl von Funktionen verwendet wurde.

Ausführliche Informationen hierzu finden Sie im folgenden Blogartikel und dem zugehörigen Tutorial:

-   [Tipps und Tricks für die Optimierung von Machine Learning in SQL Server](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/)

Vielen Benutzern ist beim ersten Laden der R-Laufzeit (oder der Python-Laufzeit) eine kleine Pause aufgefallen. Aus diesem Grund wird die Zeit für die erste Ausführung wie in den Tests beschrieben zwar häufig gemessen, aber später verworfen. Durch die nachfolgende Zwischenspeicherung kann es zu erheblichen Leistungsunterschieden zwischen der ersten und der zweiten Ausführung kommen. Beim Verschieben von Daten zwischen SQL Server und der externen Laufzeit kommt es auch zu einem gewissen Mehraufwand, insbesondere dann, wenn Daten über das Netzwerk übergeben und nicht direkt aus SQL Server geladen werden.

Aus diesen Gründen gibt es zur Verringerung der anfänglichen Ladezeit nicht die eine Lösung, da sich die Leistungseinbußen je nach Aufgabe erheblich unterscheiden. Die Zwischenspeicherung wird für die Bewertung einer einzelnen Zeile beispielsweise in Batches ausgeführt. Folglich sind nachfolgende Bewertungsvorgänge wesentlich schneller, da weder das Modell noch die R-Laufzeit erneut geladen werden. Auch mit der [nativen Bewertung](../sql-native-scoring.md) können Sie vermeiden, dass die R-Laufzeit vollständig geladen wird.

Beim Trainieren von großen Modellen oder bei der Bewertung von großen Batches fällt der Mehraufwand verglichen mit den Vorteilen durch das Vermeiden von Datenverschiebung oder durch Streaming und eine parallele Verarbeitung möglicherweise geringer aus. Weitere Informationen zur Leistungssteigerung finden Sie in diesem Blogbeitrag:

+ [Verwenden von R zur Betrugserkennung bei 1 Million Transaktionen pro Sekunde](https://blog.revolutionanalytics.com/2016/09/fraud-detection.html/)

## <a name="resources"></a>Ressourcen

Nachstehend finden Sie Links zu Informationen, Tools und Skripts, die bei der Entwicklung der hier beschriebenen Tests verwendet wurden:

+ Skripts zu den Leistungstests und Links zu den Daten: [Beispieldaten und Skripts für die Studie zu SQL Server-Optimierungen](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning)

+ Artikel über die Lösung für den Abgleich von Lebensläufen: [Tipps und Tricks für die Optimierung von SQL Server R Services](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/)

+ Bei der SQL-Optimierung verwendete Skripts für die Lösung für den Abgleich von Lebensläufen: [GitHub-Repository](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips)

### <a name="learn-about-windows-server-management"></a>Informationen zu Windows Server Management

+ [Vorgehensweise: Bestimmen der geeigneten Auslagerungsdateigröße für 64-Bit-Versionen von Windows](https://support.microsoft.com/kb/2860880)

+ [Grundlegendes zu NUMA](https://technet.microsoft.com/library/ms178144.aspx)

+ [Unterstützung der NUMA-Funktionalität in SQL Server](https://technet.microsoft.com/library/ms180954.aspx)

+ [Soft-NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)

### <a name="learn-about-sql-server-optimizations"></a>Informationen zu SQL Server-Optimierungen

+ [Neuorganisieren und Neuerstellen von Indizes](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)

+ [Einführung in speicheroptimierte Tabellen](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables)

+ [Demo: Leistungsverbesserungen von In-Memory-OLTP](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp)

+ [Datenkomprimierung](../../relational-databases/data-compression/data-compression.md)

+ [Aktivieren der Komprimierung für eine Tabelle oder einen Index](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [Deaktivieren der Komprimierung für eine Tabelle oder einen Index](../../relational-databases/data-compression/disable-compression-on-a-table-or-index.md)

### <a name="learn-about-managing-sql-server"></a>Informationen zur Verwaltung von SQL Server

+ [Überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md)

+ [Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor.md)

+ [Einführung in Resource Governor](https://technet.microsoft.com/library/bb895232.aspx)

+ [Beispiel für die Konfiguration von Resource Governor](https://blog.sqlauthority.com/2012/06/04/sql-server-simple-example-to-configure-resource-governor-introduction-to-resource-governor/)

### <a name="tools"></a>Tools

+ [DISKSPD storage load generator/performance test tool (DISKSPD-Speicherladungsgenerator/Leistungstesttool)](https://github.com/microsoft/diskspd)

+ [Referenz zum Hilfsprogramm FSUtil](https://technet.microsoft.com/library/cc753059.aspx)


## <a name="other-articles-in-this-series"></a>Weitere Artikel in dieser Reihe

[Leistungsoptimierung für R – Einführung](sql-server-r-services-performance-tuning.md)

[Leistungsoptimierung für R – SQL Server-Konfiguration](sql-server-configuration-r-services.md)

[Leistungsoptimierung für R – R-Code und Datenoptimierung](r-and-data-optimization-r-services.md)

[Leistungsoptimierung – Ergebnisse der Fallstudie](performance-case-study-r-services.md)
