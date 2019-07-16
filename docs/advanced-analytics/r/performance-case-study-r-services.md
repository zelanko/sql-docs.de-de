---
title: Leistung für SQL Server R Services - Ergebnisse und Ressourcen – SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: ce4bb94efa8c8ffb1b0a3b0c52c29de74a2b966e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962557"
---
# <a name="performance-for-r-services-results-and-resources"></a>Leistung von R Services: Ergebnisse und Ressourcen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel ist die vierte und letzte in einer Reihe, die eine leistungsoptimierung für R Services beschreibt. Dieser Artikel beschreibt die Methoden, Ergebnisse und Erkenntnisse von zwei Fallstudien, die verschiedene Methoden zur Optimierung getestet.

Die zwei Fallstudien hatten unterschiedliche Ziele:

+ Die erste Fallstudie, durch das Entwicklungsteam von R Services gesucht wurde, zum Messen der Auswirkungen von bestimmten Optimierungstechniken
+ Die zweite Fallstudie, haben von einem Data Scientist-Team mit mehreren Methoden, um zu bestimmen, die bestmögliche Optimierung für ein bestimmtes Bewertung Szenario mit hohem Volumen experimentiert.

Dieses Thema enthält die ausführlichen Ergebnisse der ersten Fallstudie. Die zweite Fallstudie beschreibt eine Zusammenfassung die gesamten Ergebnisse. Sind Sie am Ende dieses Themas enthält Links zu allen Skripts und Beispieldaten und Ressourcen, die von den ursprünglichen Autoren verwendet.

## <a name="performance-case-study-airline-dataset"></a>Fallstudie zur Leistung: Fluglinien-dataset

Diese Fallstudie vom SQL Server R Services-Entwicklungsteam getestet, die Auswirkungen der verschiedenen Optimierungen. Ein einzelnes RxLogit-Modell erstellt wurde, und Bewertung für das Fluglinien-Dataset durchgeführt. Optimierungen wurden während der Trainings- und Bewertungsschritte für Prozesse, die zum Bewerten der Auswirkungen auf die einzelnen angewendet.

- Github: [Beispieldaten und Skripts](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning) für SQL Server-Optimierungen-Studie

### <a name="test-methods"></a>Testmethoden

1. Das Fluglinien-Dataset besteht aus einer einzelnen Tabelle mit 10 Millionen Zeilen. Es wurde heruntergeladen und in SQL Server geladen.
2. Sechs Kopien der Tabelle wurden vorgenommen.
3. Verschiedene Änderungen wurden die Kopien der Tabelle, zum Testen von SQL Server-Funktionen wie z. B. Page-Komprimierung, Row-Komprimierung, Indizierung, spaltenbasierte Datenspeicher usw. angewendet.
4. Vor und nach jeder Optimierung angewendet wurde, wurde die Leistung gemessen.

| Tabellenname| Beschreibung|
|------|------|
| *airline* | Aus der ursprünglichen XDF-Datei mithilfe von `rxDataStep` konvertierte Daten.|                          |
| *airlineWithIntCol*   | *DayOfWeek* konvertiert in eine Ganzzahl anstatt in eine Zeichenfolge. Fügt auch eine *rowNum*-Spalte hinzu.|
| *airlineWithIndex*    | Die gleichen Daten wie in der *airlineWithIntCol*-Tabelle, jedoch mit einem einzigen gruppierten Index mit *rowNum*-Spalte.|
| *airlineWithPageComp* | Die gleichen Daten wie in der *airlineWithIndex*-Tabelle, jedoch mit aktivierter Seitenkomprimierung. Fügt auch die beiden Spalten *CRSDepHour* und *Late* hinzu, die aus *CRSDepTime* und *ArrDelay* berechnet werden. |
| *airlineWithRowComp*  | Die gleichen Daten wie in der *airlineWithIndex*-Tabelle, jedoch mit aktivierter Zeilenkomprimierung. Fügt auch die beiden Spalten *CRSDepHour* und *Late* hinzu, die aus *CRSDepTime* und *ArrDelay* berechnet werden. |
| *airlineColumnar*     | Ein spaltenbasierter Speicher mit einem einzigen gruppierten Index. Diese Tabelle wird mit Daten aus einer bereinigten CSV-Datei aufgefüllt.|

Jeder Test umfasste die folgenden Schritte aus:

1. Die automatische Speicherbereinigung für R wurde vor jedem Test eingeleitet.
2. Ein Logistisches Regressionsmodell wurde auf Grundlage der Tabellendaten erstellt. Der Wert von *rowsPerRead* wurde für jeden Test auf 500000 festgelegt.
3. Bewertungen wurden mithilfe des trainierten Modells generiert
4. Jeder Test wurde sechsmal ausgeführt. Die Zeit der ersten Ausführung (das "kalte ausführen") wurde gelöscht. Um gelegentliche Ausreißer, ermöglichen die **maximale** Zeit für die verbleibenden fünf Ausführungen wurde ebenfalls gelöscht. Der Durchschnitt der vier verbleibenden Ausführungen wurde verwendet, um die durchschnittliche verstrichene Laufzeit jedes Tests zu berechnen.
5. Die Tests ausgeführt wurden, mit der *ReportProgress* Parameter mit dem Wert 3 (= Berichts Zeitangaben und Status). Jede Ausgabedatei enthält Informationen über die Zeit im e/a-, Übergangszeit und Rechenzeit. Diese Zeiten sind nützlich für die Problembehandlung und Diagnose.
6. Die Konsolenausgabe wurde auch in eine Datei im Ausgabeverzeichnis geleitet.
7. Die Testskripts verarbeitet die Zeiten, in diesen Dateien zum Berechnen der durchschnittlichen Zeit über ausgeführt wird.

Die folgenden Ergebnisse sind beispielsweise die Uhrzeiten von einer einzelnen Test. Die wichtigsten Zeiten sind **Gesamte Lesezeit** (E/A-Zeit) und **Übergangszeit** (Aufwand für das Einrichten von Prozessen für die Berechnung).

**Beispiel für Zeitangaben**

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

Es wird empfohlen, dass Sie herunterladen und ändern Sie die Testskripts, damit Sie Probleme mit R Services oder mit RevoScaleR-Funktionen behandeln können.

### <a name="test-results-all"></a>Testergebnisse (alle)

In diesem Abschnitt werden vor und nach der Ergebnisse aller Tests vergleicht.

#### <a name="data-size-with-compression-and-a-columnar-table-store"></a>Größe der Daten mit der Komprimierung und einer spaltenbasierten Tabellenspeicher

Der erste Test verglichen, die Verwendung von Komprimierung und einer spaltenbasierten Tabelle zum Verringern der Größe der Daten.

| Tabellenname            | Zeilen     | Reserviert.   | Daten       | index_size | Nicht verwendet  | % Gespeichert (reserviert) |
|-----------------------|----------|------------|------------|------------|---------|---------------------|
| *airlineWithIndex*    | 10000000 | 2\.978.816 KB | 2\.972.160 KB | 6\.128 KB    | 528 KB  | 0                   |
| *airlineWithPageComp* | 10000000 | 625.784 KB  | 623.744 KB  | 1\.352 KB    | 688 KB  | 79%                 |
| *airlineWithRowComp*  | 10000000 | 1\.262.520 KB | 1\.258.880 KB | 2\.552 KB    | 1\.088 KB | 58%                 |
| *airlineColumnar*     | 9999999  | 201.992 KB  | 201.624 KB  | –        | 368 KB  | 93%                 |

**Schlussfolgerungen**

Die größte Verringerung der Datengröße wurde erreicht, indem Sie einen columnstore-Index, gefolgt von der Page-Komprimierung anwenden.

#### <a name="effects-of-compression"></a>Auswirkungen der Komprimierung

Dieser Test verglichen, die Vorteile der zeilenkomprimierung, seitenkomprimierung und keine Komprimierung. Ein Modell trainiert wurde, mithilfe von `rxLinMod` auf Daten aus drei verschiedenen Tabellen. Für alle Tabellen wurde dieselbe Formel und Abfrage verwendet.

| Tabellenname            | Testname       | numTasks | Durchschnittliche Zeit |
|-----------------------|-----------------|----------|--------------|
| *airlineWithIndex*    | NoCompression   | 1        | 5.6775       |
|                       | "Nocompression" - parallel| 4        | 5.1775       |
| *airlineWithPageComp* | PageCompression | 1        | 6.7875       |
|                       | PageCompression - parallel | 4        | 5.3225       |
| *airlineWithRowComp*  | RowCompression  | 1        | 6.1325       |
|                       | RowCompression - parallel  | 4        | 5.2375       |

**Schlussfolgerungen**

Mit Komprimierung allein scheint nicht zu helfen. In diesem Beispiel kompensiert die Zunahme der CPU zur Komprimierung die Verringerung der e/a-Zeit.

Wenn der Test jedoch parallel ausgeführt wird, indem *numTasks* auf 4 festgelegt wird, verringert sich die durchschnittliche Zeit.

Bei größeren Datasets kann die Auswirkung der Komprimierung deutlicher bemerkbar sein. Die Komprimierung hängt ab von Dataset und Werten, sodass möglicherweise durch Ausprobieren festgestellt werden muss, welche Auswirkung die Komprimierung auf Ihr Dataset hat.

### <a name="effect-of-windows-power-plan-options"></a>Auswirkung der Energiesparoptionen für Windows

In diesem Experiment wurde `rxLinMod` mit der *airlineWithIntCol*-Tabelle verwendet. Die Energiesparoption für Windows wurde festgelegt, entweder **ausgeglichen** oder **hohe Leistung**. Für alle Tests wurde *numTasks* auf 1 festgelegt. Der Test wurde sechsmal und erfolgt zweimal unter beiden Power-Optionen, um die Variabilität der Ergebnisse zu untersuchen.

**Hohe Leistung** Energiesparoption:

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
|           |        |              | 3.91         |
|           | 1      | 3,82 Sekunden |              |
|           | 2      | 3,84 Sekunden |              |
|           | 3      | 3,86 Sekunden |              |
|           | 4      | 4,07 Sekunden |              |
|           | 5      | 4,86 Sekunden |              |
|           | 6      | 3,75 Sekunden |              |
|           |        |              | 3.88         |

**Schlussfolgerungen**

Die Ausführungszeit konsistenter und schneller ist, bei Verwendung der Windows **hohe Leistung** Energiesparplan.

#### <a name="using-integer-vs-strings-in-formulas"></a>Verwenden ganze Zahl im Vergleich zu Zeichenfolgen in Formeln

Dieser Test bewertet, die Auswirkungen der Änderung des R-Codes, um ein häufiges Problem mit Zeichenfolgen zu vermeiden. Insbesondere wurde ein Modell mit trainiert `rxLinMod` mithilfe von zwei Tabellen: in der ersten Faktoren als Zeichenfolgen gespeichert werden, in der zweiten Tabelle werden die Faktoren als Integer gespeichert.

+ Für die *Fluggesellschaft* Tabelle, für die Spalte [-DayOfWeek] Zeichenfolgen enthält. Die _ColInfo_ Parameter wurde verwendet, um die Faktorebenen (Montag, Dienstag,...) angeben.

+  Für die *AirlineWithIndex* [-DayOfWeek]-Tabelle ist eine ganze Zahl. Die _ColInfo_ Parameter wurde nicht angegeben.

+ In beiden Fällen wurde dieselbe Formel `ArrDelay ~ CRSDepTime + DayOfWeek` verwendet.

| Tabellenname          | Testname   | Durchschnittliche Zeit |
|---------------------|-------------|--------------|
| *Fluggesellschaft*           | *FactorCol* | 10.72        |
| *airlineWithIntCol* | *IntCol*    | 3.4475       |

**Schlussfolgerungen**

Besteht ein klarer Vorteil bei Verwendung von ganzen Zahlen anstatt als Zeichenfolgen für Faktoren vor.

### <a name="avoiding-transformation-functions"></a>Vermeiden von Transformationsfunktionen

In diesem Test wurde ein Modell trainiert, mit `rxLinMod`, aber der Code zwischen den zwei Testläufen geändert wurde:

+ In der ersten Ausführung wurde eine Transformationsfunktion als Teil der Modellerstellung angewendet. 
+ Waren in der zweiten Ausführung die featurewerte vorausberechnete und verfügbar ist, so, dass keine Transformationsfunktion erforderlich war.

| Testname             | Durchschnittliche Zeit |
|-----------------------|--------------|
| WithTransformation    | 5.1675       |
| WithoutTransformation | 4.7          |

**Schlussfolgerungen**

Die Trainingszeit kürzere bei wurde **nicht** mit Transformationsfunktion. Das heißt, wurde das Modell schneller trainiert, bei Verwendung von Spalten, die bereits berechnet und persistent in der Tabelle.

Die einsparungen muss größer sein, wenn gab es mehr Transformationen gäbe und das DataSet größer wurden (\> 100 Mio.).

### <a name="using-columnar-store"></a>Verwenden von spaltenbasiertem Speicher

Dieser Test bewertet die Leistungsvorteile mithilfe eines spaltenbasierten Datenspeicher und den Index. Das gleiche Modell trainiert wurde, mithilfe von `rxLinMod` und keine Datentransformationen.

+ In der ersten Ausführung verwendet die Datentabelle, einen standard Zeilenspeicher.
+ In der zweiten Ausführung wurde ein columnstore verwendet.

| Tabellenname         | Testname | Durchschnittliche Zeit |
|--------------------|-----------|--------------|
| *airlineWithIndex* | RowStore  | 4.67         |
| *airlineColumnar*  | ColStore  | 4.555        |

**Schlussfolgerungen**

Leistung ist besser, mit der spaltenbasierte Speicher als mit der standard-Zeilenspeicher. Bei größeren Datasets kann sich signifikant auf die Leistung erwartet werden (\> 100 Mio.).

### <a name="effect-of-using-the-cube-parameter"></a>Auswirkung des Cube-Parameters

Der Zweck dieses Tests wurde, um zu bestimmen, ob die Option in RevoScaleR für die Verwendung der vorausberechnete **Cube** Parameter kann die Leistung verbessern. Ein Modell trainiert wurde, mithilfe von `rxLinMod`, mit dieser Formel:

```R
ArrDelay ~ Origin:DayOfWeek + Month + DayofMonth + CRSDepTime
```

In der Tabelle, die Faktoren *DayOfWeek* als Zeichenfolge gespeichert wird.

| Testname     | Cube-Parameter | numTasks | Durchschnittliche Zeit | Einzelne Zeile Vorhersagen (ArrDelay_Pred) |
|---------------|----------------|----------|--------------|---------------------------------|
| CubeArgEffect | `cube = F`     | 1        | 91.0725      | 9.959204                        |
|               |                | 4        | 44.09        | 9.959204                        |
|               | `cube = T`     | 1        | 21.1125      | 9.959204                        |
|               |                | 4        | 8.08         | 9.959204                        |

**Schlussfolgerungen**

Die Verwendung von Cube Parameterargument verbessert die Leistung deutlich.

### <a name="effect-of-changing-maxdepth-for-rxdtree-models"></a>Auswirkungen der Änderung von MaxDepth für RxDTree-Modelle

In diesem Experiment wird das `rxDTree` Algorithmus wurde verwendet, um ein Modell zu erstellen, auf die *AirlineColumnar* Tabelle. Für diesen Test wurde *numTasks* auf 4 festgelegt. Verschiedene Werte für *MaxDepth* verwendet wurden, um zu veranschaulichen, wie das Ändern der Strukturtiefe zur Laufzeit beeinflusst.

| Testname       | maxDepth | Durchschnittliche Zeit |
|-----------------|----------|--------------|
| TreeDepthEffect | 1        | 10.1975      |
|                 | 2        | 13.2575      |
|                 | 4        | 19.27        |
|                 | 8        | 45.5775      |
|                 | 16       | 339.54       |

**Schlussfolgerungen**

Mit zunehmender die Tiefe des Baums, der die Gesamtzahl der Knoten exponentiell erhöht. Die verstrichene Zeit zum Erstellen des Modells auch erheblich erhöht.

### <a name="prediction-on-a-stored-model"></a>Vorhersagen für eines gespeicherten Modells

Der Zweck dieses Tests wurde, um zu bestimmen, die Auswirkungen auf die Leistung für die Bewertung, wenn das trainierte Modell in einer SQL Server-Tabelle gespeichert wird, anstatt als Teil der gerade ausgeführte Code generiert. Für die Bewertung, das gespeicherte Modell aus der Datenbank geladen wird, und Vorhersagen werden mit einem einzeilige Datenrahmen im Arbeitsspeicher (lokaler computekontext) erstellt.

Die Testergebnisse zeigen die Zeit zum Speichern des Modells, und die Zeit zum Laden des Modells und vorherzusagen.

| Tabellenname | Testname | Durchschnittliche Zeit (Trainieren des Modells) | Zeit zum Speichern/Laden des Modells|
|------------|------------|------------|------------|
| airline    | SaveModel| 21.59| 2.08|
| airline    | LoadModelAndPredict | | 2,09 (einschließlich Zeit für Vorhersagen) |

**Schlussfolgerungen**

Laden eines trainierten Modells aus einer Tabelle ist deutlich schnellerer Weg für die Vorhersage. Es wird empfohlen, dass Sie das Modell erstellen und Ausführen der Bewertung, die alle im selben Skript vermeiden.

## <a name="case-study-optimization-for-the-resume-matching-task"></a>Fallstudie: Optimierung für den Vorgang fortsetzen übereinstimmende

Die übereinstimmende Resume-Modell wurde entwickelt, von Microsoft Data scientists Ke Huang zum Testen der Leistung von R-Code in SQL Server, und klicken Sie dazu so Hilfedaten Datenanalysten skalierbarer erstellen, professionelle Lösungen.

### <a name="methods"></a>Methoden

Sowohl die MicrosoftML die RevoScaleR-Pakete wurden zum Trainieren eines prädiktiven Modells in einer komplexen R-Lösung, die im Zusammenhang mit großen Datasets verwendet. SQL-Abfragen und R-Code wurden alle Tests identisch. Tests wurden in einer einzelnen Azure-VM mit SQL Server ausgeführt. Klicken Sie dann verglichen, der Autor Bewertung Zeiten mit und ohne die folgenden Optimierungen, die von SQL Server bereitgestellt:

- In-Memory-Tabellen
- Soft-NUMA
- Resource Governor

Um die Auswirkungen von Soft-NUMA auf R-skriptausführung zu bewerten, getestet, die Data Science-Teams die Lösung auf virtuellen Azure-Computer mit 20 physischen Kernen. Auf diese physische Kerne wurden vier Soft-NUMA-Knoten automatisch erstellt, sodass jeder Knoten fünf Kerne enthalten.

CPU-Affinitization erzwungen wurde in diesem Szenario fortsetzen übereinstimmende bewerten die Auswirkung auf die R-Aufträge. Vier **SQL Ressourcenpools** und vier **externe Ressourcenpools** erstellt wurden, und der CPU-Affinität angegeben wurde, um sicherzustellen, dass die gleiche Satz CPUs in den einzelnen Knoten verwendet wird.

Aller Ressourcenpools wurde eine andere Arbeitsauslastungsgruppe, zugewiesen, um die Auslastung der Hardware optimieren. Der Grund dafür ist, Soft-NUMA und CPU-Affinität physischen Speicher in der physischen NUMA-Knoten kann nicht geteilt werden; aus diesem Grund müssen alle soft NUMA-Knoten, die auf dem gleichen physischen NUMA-Knoten beruhen per Definition Arbeitsspeicher in demselben Betriebssystem-Speicherblock verwenden. Das heißt, ist es keine Speicher-Prozessor-Affinität.

Der folgende Prozess wurde verwendet, um diese Konfiguration zu erstellen:

1. Verringern der Anzahl der Speichermenge, die standardmäßig für die SQL Server.

2. Erstellen Sie die vier neuen Pools für die R-Aufträge parallel ausgeführt.

3. Erstellen Sie vier Arbeitsauslastungsgruppen, sodass jede Arbeitsauslastungsgruppe einen Ressourcenpool zugeordnet ist.

4. Starten Sie die Ressourcenkontrolle mit dem neuen Arbeitsauslastungsgruppen und Zuweisungen neu.

5. Erstellen Sie eine benutzerdefinierte Klassifizierungsfunktion-Funktion (UDF), verschiedene Aufgaben für andere Arbeitsauslastungsgruppen zuweisen.

6. Aktualisieren Sie die Konfiguration der Ressourcenkontrolle, um die Funktion für die entsprechenden Arbeitsauslastungsgruppen zu verwenden.

### <a name="results"></a>Ergebnisse

Die Konfiguration, die die beste Leistung in der Resume-entsprechenden untersuchen mussten lautet wie folgt aus:

-   Vier interne Ressourcenpools (für SQL Server)

-   Vier externe Ressourcenpools (für externe Skripts für Aufträge)

-   Jeder Ressourcenpool bezieht sich auf einer bestimmten Arbeitsauslastungsgruppe

-   Unterschiedliche CPUs wird jedem Ressourcenpool zugewiesen.

-   Maximale interne speicherauslastung (für SQL Server) = 30 %

-   Maximaler Arbeitsspeicher für die Verwendung von R-Sitzungen = 70 %

Externe Skripts wurde hohe und gab es keine andere Datenbank-Engine-Dienste ausgeführt, für das Modell übereinstimmenden fortsetzen. Aus diesem Grund wurden die Ressourcen, die externe Skripts zugeordnet auf 70 % verbessert, die die beste Konfiguration für skriptleistung erwies.

Diese Konfiguration wurde beim Umgang mit unterschiedlichen Werten eingeht. Wenn Sie unterschiedliche Hardware- oder eine andere Lösung verwenden, kann die optimale Konfiguration abweichen. Probieren Sie immer die beste Konfiguration für Ihren Fall gefunden!

In der optimierten Lösung wurden 1.1 Millionen Datenzeilen (mit 100 Funktionen) in weniger als 8,5 Sekunden auf eine 20-Core-Computer bewertet. Optimierungen verbessert erheblich die Leistung in Hinblick auf Ihre Bewertung.

Die Ergebnisse außerdem empfohlen, die die **Anzahl von Features** hat erhebliche Auswirkungen auf die für die Bewertung Zeit. Wenn Sie weitere Features in das Vorhersagemodell verwendet wurden, war die leistungsverbesserung noch stärker akzentuiert.

Es wird empfohlen, dass Sie in diesem Blogartikel und die begleitenden Tutorials ausführliche Informationen zu lesen.

-   [Optimization-Tipps und Tricks für Machine Learning in SQL Server](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/)

Viele Benutzer haben bereits erwähnt, dass es eine kleine Pause ist, wie die Laufzeit von R (oder Python) zum ersten Mal geladen wird. Aus diesem Grund wie beschrieben in diesen Tests, ist die Zeit für die erste Ausführung häufig liegt diese jedoch später verworfen. Nachfolgende zwischenspeicherungen relevante Leistungsunterschiede zwischen dem ersten unter Umständen, und zweitens führt. Es gibt auch etwas Aufwand verbunden, wenn Daten zwischen SQL Server und der externen Runtime verschoben werden insbesondere dann, wenn Daten über das Netzwerk, anstatt direkt aus SQL Server geladenen übergeben werden.

Allen diesen Gründen ist keine einfache Lösung zum Beheben von diesem Zeitpunkt anfangsladevorgang da Auswirkungen auf die Leistung erheblich abhängig von der Aufgabe unterschiedlich ist. Beispielsweise wird das Zwischenspeichern für die einzelnen Zeile Bewertung in Batches durchgeführt; Daher aufeinander folgende Bewertung Operationen sind viel schneller, und weder für das Modell als auch für die R-Laufzeit wird erneut geladen. Sie können auch [nativen Bewertung](../sql-native-scoring.md) zu vermeiden, dass die R-Laufzeit vollständig geladen.

Für große Modelle trainieren oder große Batches zu bewerten, kann der Aufwand im Vergleich zu der durch den Einsatz von um datenbewegungen zu vermeiden oder von streaming und die parallelverarbeitung minimal sein. Lesen Sie diesen Blogbeitrag zusätzliche Leistung:

+ [Verwenden von R zum Erkennen von Betrug an 1 Millionen Transaktionen pro Sekunde](https://blog.revolutionanalytics.com/2016/09/fraud-detection.html/)

## <a name="resources"></a>Ressourcen

Im folgenden finden Links zu Informationen, Tools und Skripts, die bei der Entwicklung von Tests verwendet.

+ Die Leistung Testen von Skripts und Links zu den Daten: [Beispieldaten und Skripts für SQL Server-Optimierungen-Studie](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning)

+ Der Artikel beschreibt die Lösung fortsetzen übereinstimmende: [Optimierung Tipps und Tricks für die SQL Server R Services](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/)

+ Skripts, die in der SQL-Optimierung für übereinstimmende Resume-Lösung verwendet werden: [GitHub-repository](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips)

### <a name="learn-about-windows-server-management"></a>Erfahren Sie mehr über Windows Server-Verwaltung

+ [Vorgehensweise: Bestimmen der geeigneten Auslagerungsdateigröße für 64-Bit-Versionen von Windows](https://support.microsoft.com/kb/2860880)

+ [Grundlegendes zu NUMA](https://technet.microsoft.com/library/ms178144.aspx)

+ [Wie unterstützt SQL Server NUMA](https://technet.microsoft.com/library/ms180954.aspx)

+ [Soft-NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)

### <a name="learn-about-sql-server-optimizations"></a>Erfahren Sie mehr über SQL Server-Optimierungen

+ [Neuorganisieren und Neuerstellen von Indizes](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)

+ [Einführung in Speicheroptimierte Tabellen](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables)

+ [Demo: Leistungsverbesserungen von in-Memory-OLTP](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp)

+ [Datenkomprimierung](../../relational-databases/data-compression/data-compression.md)

+ [Aktivieren der Komprimierung für eine Tabelle oder einen Index](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [Deaktivieren der Komprimierung für eine Tabelle oder einen Index](../../relational-databases/data-compression/disable-compression-on-a-table-or-index.md)

### <a name="learn-about-managing-sql-server"></a>Erfahren Sie mehr über die Verwaltung von SQL Server

+ [Überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md)

+ [Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor.md)

+ [Einführung in die Ressourcenkontrolle](https://technet.microsoft.com/library/bb895232.aspx)

+ [Ressourcenkontrolle für R Services](resource-governance-for-r-services.md)

+ [Gewusst wie: Erstellen eines Ressourcenpools für R](how-to-create-a-resource-pool-for-r.md)

+ [Ein Beispiel zum Konfigurieren der Ressourcenkontrolle](https://blog.sqlauthority.com/2012/06/04/sql-server-simple-example-to-configure-resource-governor-introduction-to-resource-governor/)

### <a name="tools"></a>Tools

+ [DISKSPD storage load generator/performance test tool (DISKSPD-Speicherladungsgenerator/Leistungstesttool)](https://github.com/microsoft/diskspd)

+ [Referenz zum Hilfsprogramm FSUtil](https://technet.microsoft.com/library/cc753059.aspx)


## <a name="other-articles-in-this-series"></a>Anderen Artikeln dieser Serie

[Leistung optimieren, die für R – Einführung](sql-server-r-services-performance-tuning.md)

[Leistungsoptimierung für R – SQL Server-Konfiguration](sql-server-configuration-r-services.md)

[Leistungsoptimierung für R – R-Code und Daten-Optimierung](r-and-data-optimization-r-services.md)

[Leistungsoptimierung - Fallstudie Ergebnisse](performance-case-study-r-services.md)
