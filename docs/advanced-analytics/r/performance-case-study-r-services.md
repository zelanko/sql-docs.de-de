---
title: Leistung für SQL Server R Services-Ergebnisse und-Ressourcen
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 8d7f046e961efb6129f807a7626e498062c415b6
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470159"
---
# <a name="performance-for-r-services-results-and-resources"></a>Leistung für R Services: Ergebnisse und Ressourcen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel ist der vierte und letzte in einer Reihe, in der die Leistungsoptimierung für R Services beschrieben wird. In diesem Artikel werden die Methoden, Ergebnisse und Schlussfolgerungen zweier Fallstudien zusammengefasst, die verschiedene Optimierungsmethoden getestet haben.

Die zwei Fallstudien hatten unterschiedliche Ziele:

+ Die erste Fallstudie vom R Services-Entwicklungsteam hat versucht, die Auswirkungen spezifischer Optimierungstechniken zu messen.
+ Die zweite Fallstudie von einem Data Scientist-Team hat mit mehreren Methoden experimentieren, um die besten Optimierungen für ein bestimmtes Bewertungs Szenario mit hohem Volumen zu ermitteln.

In diesem Thema werden die detaillierten Ergebnisse der ersten Fallstudie aufgeführt. In der zweiten Fallstudie werden die Gesamtergebnisse in einer Zusammenfassung beschrieben. Am Ende dieses Themas finden Sie Links zu allen Skripts und Beispiel Daten sowie zu den Ressourcen, die von den ursprünglichen Autoren verwendet werden.

## <a name="performance-case-study-airline-dataset"></a>Leistungs Fallstudie: Fluglinien-DataSet

Diese Fallstudie vom SQL Server R Services Entwicklungsteam hat die Auswirkungen verschiedener Optimierungen getestet. Es wurde ein einzelnes rxlogit-Modell erstellt und eine Bewertung für das Fluglinien DataSet durchgeführt. Während der Trainings-und Bewertungsprozesse wurden Optimierungen angewendet, um einzelne Auswirkungen zu bewerten.

- GitHub [Beispiel Daten und Skripts](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning) für SQL Server Optimierungen

### <a name="test-methods"></a>Test Methoden

1. Das Dataset für die Fluggesellschaft besteht aus einer einzelnen Tabelle mit 10 Mio. Zeilen. Sie wurde heruntergeladen und in SQL Server Massen geladen.
2. Es wurden sechs Kopien der Tabelle erstellt.
3. Es wurden verschiedene Änderungen auf die Kopien der Tabelle angewendet, um SQL Server Features wie Seiten Komprimierung, Zeilen Komprimierung, Indizierung, Spaltendaten Speicher usw. zu testen.
4. Die Leistung wurde vor und nach dem Anwenden jeder Optimierung gemessen.

| Tabellenname| Beschreibung|
|------|------|
| *airline* | Aus der ursprünglichen XDF-Datei mithilfe von `rxDataStep` konvertierte Daten.|                          |
| *airlineWithIntCol*   | *DayOfWeek* konvertiert in eine Ganzzahl anstatt in eine Zeichenfolge. Fügt auch eine *rowNum*-Spalte hinzu.|
| *airlineWithIndex*    | Die gleichen Daten wie in der *airlineWithIntCol*-Tabelle, jedoch mit einem einzigen gruppierten Index mit *rowNum*-Spalte.|
| *airlineWithPageComp* | Die gleichen Daten wie in der *airlineWithIndex*-Tabelle, jedoch mit aktivierter Seitenkomprimierung. Fügt auch die beiden Spalten *CRSDepHour* und *Late* hinzu, die aus *CRSDepTime* und *ArrDelay* berechnet werden. |
| *airlineWithRowComp*  | Die gleichen Daten wie in der *airlineWithIndex*-Tabelle, jedoch mit aktivierter Zeilenkomprimierung. Fügt auch die beiden Spalten *CRSDepHour* und *Late* hinzu, die aus *CRSDepTime* und *ArrDelay* berechnet werden. |
| *airlineColumnar*     | Ein spaltenbasierter Speicher mit einem einzigen gruppierten Index. Diese Tabelle wird mit Daten aus einer bereinigten CSV-Datei aufgefüllt.|

Jeder Test besteht aus den folgenden Schritten:

1. Die automatische Speicherbereinigung für R wurde vor jedem Test eingeleitet.
2. Basierend auf den Tabellendaten wurde ein logistisches Regressionsmodell erstellt. Der Wert von *rowsPerRead* wurde für jeden Test auf 500000 festgelegt.
3. Ergebnisse wurden mithilfe des trainierten Modells generiert.
4. Jeder Test wurde sechs Mal ausgeführt. Der Zeitpunkt der ersten Durchführung (der "kaltlauf") wurde gelöscht. Um gelegentlich Ausreißer zuzulassen, wurde die **Maximale** Zeit zwischen den verbleibenden fünf Ausführungen ebenfalls verworfen. Der Durchschnitt der vier verbleibenden Ausführungen wurde verwendet, um die durchschnittliche verstrichene Laufzeit jedes Tests zu berechnen.
5. Die Tests wurden mit dem *ReportProgress* -Parameter mit dem Wert 3 (= Berichts zeitliche und Fortschritt) ausgeführt. Jede Ausgabedatei enthält Informationen über die Zeit, die für e/a-Vorgänge, Übergangszeit und Compute-Zeit aufgewendet wird. Diese Zeiten sind nützlich für die Problembehandlung und Diagnose.
6. Die Konsolenausgabe wurde auch an eine Datei im Ausgabeverzeichnis weitergeleitet.
7. Die Test Skripts haben die Uhrzeiten in diesen Dateien verarbeitet, um die durchschnittliche Zeit für die Ausführung zu berechnen.

Die folgenden Ergebnisse sind z. b. die Zeiten eines einzelnen Tests. Die wichtigsten Zeiten sind **Gesamte Lesezeit** (E/A-Zeit) und **Übergangszeit** (Aufwand für das Einrichten von Prozessen für die Berechnung).

**Beispiel Zeitangaben**

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

Es wird empfohlen, die Test Skripts herunterzuladen und zu ändern, um Sie beim Beheben von Problemen mit R Services oder mit revoscaler-Funktionen zu unterstützen.

### <a name="test-results-all"></a>Test Ergebnisse (alle)

In diesem Abschnitt werden die Ergebnisse vor und nach für jeden der Tests verglichen.

#### <a name="data-size-with-compression-and-a-columnar-table-store"></a>Datengröße mit Komprimierung und einem Spalten förmigen Tabellen Speicher

Der erste Test verglich die Verwendung der Komprimierung und eine Spalten Tabelle, um die Größe der Daten zu reduzieren.

| Tabellenname            | Zeilen     | Reserviert.   | Daten       | index_size | Nicht verwendet  | % Gespeichert (reserviert) |
|-----------------------|----------|------------|------------|------------|---------|---------------------|
| *airlineWithIndex*    | 10000000 | 2\.978.816 KB | 2\.972.160 KB | 6\.128 KB    | 528 KB  | 0                   |
| *airlineWithPageComp* | 10000000 | 625.784 KB  | 623.744 KB  | 1\.352 KB    | 688 KB  | 79%                 |
| *airlineWithRowComp*  | 10000000 | 1\.262.520 KB | 1\.258.880 KB | 2\.552 KB    | 1\.088 KB | 58%                 |
| *airlineColumnar*     | 9999999  | 201.992 KB  | 201.624 KB  | –        | 368 KB  | 93%                 |

**Ergebnisse**

Die größte Verringerung der Datengröße wurde erreicht, indem ein columnstore--Index, gefolgt von der Seiten Komprimierung, angewendet wurde.

#### <a name="effects-of-compression"></a>Auswirkungen der Komprimierung

Mit diesem Test wurden die Vorteile der Zeilen Komprimierung, der Seiten Komprimierung und der Komprimierung nicht komprimiert. Ein Modell wurde mithilfe `rxLinMod` von Daten aus drei verschiedenen Datentabellen trainiert. Für alle Tabellen wurde dieselbe Formel und Abfrage verwendet.

| Tabellenname            | Testname       | numTasks | Durchschnittliche Zeit |
|-----------------------|-----------------|----------|--------------|
| *airlineWithIndex*    | NoCompression   | 1        | 5.6775       |
|                       | NoCompression-parallel| 4        | 5.1775       |
| *airlineWithPageComp* | PageCompression | 1        | 6.7875       |
|                       | Pagecompression-parallel | 4        | 5.3225       |
| *airlineWithRowComp*  | RowCompression  | 1        | 6.1325       |
|                       | Zeilen Komprimierung-parallel  | 4        | 5.2375       |

**Ergebnisse**

Die Komprimierung allein scheint nicht zu helfen. In diesem Beispiel kompensiert der Anstieg der CPU zur Behandlung der Komprimierung die Verringerung der e/a-Zeit.

Wenn der Test jedoch parallel ausgeführt wird, indem *numTasks* auf 4 festgelegt wird, verringert sich die durchschnittliche Zeit.

Bei größeren Datasets kann die Auswirkung der Komprimierung deutlicher bemerkbar sein. Die Komprimierung hängt ab von Dataset und Werten, sodass möglicherweise durch Ausprobieren festgestellt werden muss, welche Auswirkung die Komprimierung auf Ihr Dataset hat.

### <a name="effect-of-windows-power-plan-options"></a>Auswirkung der Optionen des Windows-Energie Sparplans

In diesem Experiment wurde `rxLinMod` mit der *airlineWithIntCol*-Tabelle verwendet. Für den Windows-Energie Sparplan wurde entweder eine **ausgeglichene** oder eine **hohe Leistung**festgelegt. Für alle Tests wurde *numTasks* auf 1 festgelegt. Der Test wurde sechs Mal ausgeführt und wurde unter beiden Energieoptionen zweimal ausgeführt, um die Variabilität der Ergebnisse zu untersuchen.

**Hohe Leistungsoption** :

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

**Ergebnisse**

Die Ausführungszeit ist bei Verwendung des **High Performance** -Energie Sparplans von Windows einheitlicher und schneller.

#### <a name="using-integer-vs-strings-in-formulas"></a>Verwenden von ganzzahligen und Zeichen folgen in Formeln

Dieser Test hat die Auswirkung der Änderung des R-Codes bewertet, um ein häufiges Problem mit Zeichen folgen Faktoren zu vermeiden. Insbesondere wurde ein Modell mit `rxLinMod` zwei Tabellen trainiert: in der ersten Tabelle werden Faktoren als Zeichen folgen gespeichert. in der zweiten Tabelle werden Faktoren als ganze Zahlen gespeichert.

+ In der Tabelle " *Airline* " enthält die Spalte [DayOfWeek] Zeichen folgen. Der _COLINFO_ -Parameter wurde verwendet, um die Faktor Ebenen anzugeben (Montag, Dienstag,...).

+  In der *airlinewithindex* -Tabelle ist [DayOfWeek] eine ganze Zahl. Der _COLINFO_ -Parameter wurde nicht angegeben.

+ In beiden Fällen wurde dieselbe Formel `ArrDelay ~ CRSDepTime + DayOfWeek` verwendet.

| Tabellenname          | Testname   | Durchschnittliche Zeit |
|---------------------|-------------|--------------|
| *Fluglinien*           | *FactorCol* | 10.72        |
| *airlineWithIntCol* | *IntCol*    | 3.4475       |

**Ergebnisse**

Es gibt einen deutlichen Vorteil, wenn Ganzzahlen anstelle von Zeichen folgen für Faktoren verwendet werden.

### <a name="avoiding-transformation-functions"></a>Vermeiden von Transformations Funktionen

In diesem Test wurde ein Modell mit `rxLinMod`trainiert, aber der Code wurde zwischen den beiden Ausführungen geändert:

+ Bei der ersten Durchführung wurde im Rahmen der Modellbildung eine Transformations Funktion angewendet. 
+ In der zweiten Testlauf waren die featurewerte voraus berechnet und verfügbar, sodass keine Transformations Funktion erforderlich war.

| Testname             | Durchschnittliche Zeit |
|-----------------------|--------------|
| WithTransformation    | 5.1675       |
| WithoutTransformation | 4.7          |

**Ergebnisse**

Die Trainingszeit war kürzer, wenn **keine** Transformations Funktion verwendet wurde. Das heißt, dass das Modell schneller trainiert wurde, wenn Spalten verwendet werden, die Voraus berechnet und in der Tabelle persistent gespeichert werden.

Es wird vorausgesetzt, dass die Einsparungen größer sind, wenn es viele weitere Transformationen gab und das DataSet größer war (\> 100 Mio.).

### <a name="using-columnar-store"></a>Verwenden eines Spalten-Speicher

In diesem Test wurden die Leistungsvorteile der Verwendung eines Spalten basierten Datenspeicher und eines Index bewertet. Das gleiche Modell wurde mit `rxLinMod` und ohne Daten Transformationen trainiert.

+ In der ersten Testlauf wurde in der Datentabelle ein Standard-Zeilen Speicher verwendet.
+ In der zweiten Testlauf wurde ein Spalten Speicher verwendet.

| Tabellenname         | Testname | Durchschnittliche Zeit |
|--------------------|-----------|--------------|
| *airlineWithIndex* | RowStore  | 4.67         |
| *airlineColumnar*  | ColStore  | 4.555        |

**Ergebnisse**

Die Leistung ist mit dem Spalten-Speicher besser als mit dem standardmäßigen Zeilen Speicher. Ein signifikanter Unterschied in der Leistung kann bei größeren Datasets\> (100 Mio.) erwartet werden.

### <a name="effect-of-using-the-cube-parameter"></a>Auswirkung der Verwendung des Cube-Parameters

Der Zweck dieses Tests bestand darin, zu bestimmen, ob die Option in revoscaler zum Verwenden des voraus berechneten **Cube** -Parameters die Leistung verbessern kann. Ein Modell wurde mit dieser `rxLinMod`Formel mit trainiert:

```R
ArrDelay ~ Origin:DayOfWeek + Month + DayofMonth + CRSDepTime
```

In der Tabelle wird die Faktoren " *DayOfWeek* " als Zeichenfolge gespeichert.

| Testname     | Cube-Parameter | numTasks | Durchschnittliche Zeit | Vorhersagen mit einer Zeile (ArrDelay_Pred) |
|---------------|----------------|----------|--------------|---------------------------------|
| CubeArgEffect | `cube = F`     | 1        | 91.0725      | 9.959204                        |
|               |                | 4        | 44.09        | 9.959204                        |
|               | `cube = T`     | 1        | 21.1125      | 9.959204                        |
|               |                | 4        | 8.08         | 9.959204                        |

**Ergebnisse**

Durch die Verwendung des Cube-Parameter Arguments wird die Leistung deutlich verbessert.

### <a name="effect-of-changing-maxdepth-for-rxdtree-models"></a>Auswirkung der Änderung von maxtiefe für rxdtree-Modelle

In diesem Experiment wurde der `rxDTree` Algorithmus verwendet, um ein Modell in der *airlinecolennar* -Tabelle zu erstellen. Für diesen Test wurde *numTasks* auf 4 festgelegt. Es wurden verschiedene Werte für *maxtiefe* verwendet, um zu veranschaulichen, wie sich die Änderung der Struktur Tiefe auf die Laufzeit auswirkt.

| Testname       | maxDepth | Durchschnittliche Zeit |
|-----------------|----------|--------------|
| TreeDepthEffect | 1        | 10.1975      |
|                 | 2        | 13.2575      |
|                 | 4        | 19.27        |
|                 | 8        | 45.5775      |
|                 | 16       | 339.54       |

**Ergebnisse**

Wenn sich die Tiefe der Struktur erhöht, erhöht sich die Gesamtzahl der Knoten exponentiell. Die verstrichene Zeit zum Erstellen des Modells hat sich ebenfalls erheblich gesteigert.

### <a name="prediction-on-a-stored-model"></a>Vorhersage für ein gespeichertes Modell

Der Zweck dieses Tests bestand darin, die Auswirkungen auf die Leistung bei der Bewertung zu ermitteln, wenn das trainierte Modell in einer SQL Server Tabelle gespeichert wird, anstatt als Teil des aktuell ausgeführten Codes generiert zu werden. Zur Bewertung wird das gespeicherte Modell aus der Datenbank geladen, und Vorhersagen werden mithilfe eines Daten Rahmens mit einer Zeile im Speicher (lokaler computekontext) erstellt.

Die Testergebnisse zeigen die Zeit zum Speichern des Modells und die Zeit, die zum Laden des Modells und der Vorhersage benötigt wird.

| Tabellenname | Testname | Durchschnittliche Zeit (Trainieren des Modells) | Zeit zum Speichern/Laden des Modells|
|------------|------------|------------|------------|
| airline    | SaveModel| 21.59| 2.08|
| airline    | LoadModelAndPredict | | 2,09 (einschließlich Zeit für Vorhersagen) |

**Ergebnisse**

Das Laden eines trainierten Modells aus einer Tabelle ist eine deutlich schnellere Möglichkeit zur Vorhersage. Es wird empfohlen, das Erstellen des Modells und das Ausführen der Bewertung im gleichen Skript zu vermeiden.

## <a name="case-study-optimization-for-the-resume-matching-task"></a>Fallstudie: Optimierung der Aufgabe zum Fortsetzen der Übereinstimmung

Das Modell zum Fortsetzen des Ablaufs wurde von Microsoft Data Scientists KE Huang entwickelt, um die Leistung von R-Code in SQL Server zu testen. auf diese Weise können Datenanalysten skalierbare Lösungen auf Unternehmensebene erstellen.

### <a name="methods"></a>Methoden

Sowohl das revoscaler-als auch das microsoftml-Paket wurde verwendet, um ein Vorhersagemodell in einer komplexen R-Lösung mit großen Datasets zu trainieren. SQL-Abfragen und R-Code waren in allen Tests identisch. Tests wurden auf einem einzelnen virtuellen Azure-Computer durchgeführt, auf dem SQL Server installiert ist. Der Autor hat dann Bewertungs Zeiten mit und ohne die folgenden Optimierungen verglichen, die von SQL Server bereitgestellt werden:

- In-Memory-Tabellen
- Soft-NUMA
- Resource Governor

Um die Auswirkung von Soft-NUMA auf die Ausführung von R-Skripts zu bewerten, testet das Data Science Team die Lösung auf einem virtuellen Azure-Computer mit 20 physischen Kernen. Auf diesen physischen Kernen wurden automatisch vier Soft-NUMA-Knoten erstellt, sodass jeder Knoten fünf Kerne enthielt.

Die CPU-affininitialisierung wurde im Szenario zum Fortsetzen des Ablaufs erzwungen, um die Auswirkungen auf R-Aufträge zu bewerten. Es wurden vier **SQL-Ressourcenpools** und vier **externe Ressourcenpools** erstellt, und es wurde eine CPU-Affinität angegeben, um sicherzustellen, dass die gleichen CPUs in jedem Knoten verwendet werden.

Jeder Ressourcenpool wurde einer anderen Arbeits Auslastungs Gruppe zugewiesen, um die Hardware Nutzung zu optimieren. Der Grund hierfür ist, dass Soft-NUMA und CPU-Affinität den physischen Speicher in den physischen NUMA-Knoten nicht aufteilen können. Daher müssen alle Soft-NUMA-Knoten, die auf demselben physischen NUMA-Knoten basieren, definitionsgemäß Arbeitsspeicher im gleichen Betriebssystem-Speicherblock verwenden. Anders ausgedrückt: Es gibt keine Speicher-zu-Prozessor-Affinität.

Der folgende Prozess wurde verwendet, um diese Konfiguration zu erstellen:

1. Reduzieren Sie die Menge an Arbeitsspeicher, der standardmäßig SQL Server zugeordnet wird.

2. Erstellen Sie vier neue Pools zum parallelen Ausführen der R-Aufträge.

3. Erstellen Sie vier Arbeits Auslastungs Gruppen, sodass jede Arbeits Auslastungs Gruppe einem Ressourcenpool zugeordnet ist.

4. Starten Sie Resource Governor mit den neuen Arbeits Auslastungs Gruppen und Zuweisungen neu.

5. Erstellen Sie eine benutzerdefinierte Klassifizierungs Funktion (UDF), um unterschiedlichen Arbeits Auslastungs Gruppen unterschiedliche Aufgaben zuzuweisen.

6. Aktualisieren Sie die Resource Governor Konfiguration, um die-Funktion für entsprechende Arbeits Auslastungs Gruppen zu verwenden

### <a name="results"></a>Ergebnisse

Die Konfiguration, die in der Studie zum Fortsetzen des Ablaufs die beste Leistung hatte, lautete wie folgt:

-   Vier interne Ressourcenpools (für SQL Server)

-   Vier externe Ressourcenpools (für externe Skript Aufträge)

-   Jeder Ressourcenpool ist einer bestimmten Arbeits Auslastungs Gruppe zugeordnet.

-   Jeder Ressourcenpool ist verschiedenen CPUs zugewiesen.

-   Maximale interne Speicherauslastung (für SQL Server) = 30%

-   Maximaler Arbeitsspeicher für die Verwendung durch R-Sitzungen = 70%

Für das Modell mit fortlaufendem Abgleich war die Verwendung externer Skripts sehr hoch, und es wurden keine anderen Datenbank-Engine-Dienste ausgeführt. Aus diesem Grund wurden die externen Skripts zugeordneten Ressourcen auf 70% erweitert, was die beste Konfiguration für die Skript Leistung erwies.

Diese Konfiguration wurde bei durch Experimentieren mit unterschiedlichen Werten erreicht. Wenn Sie andere Hardware oder eine andere Lösung verwenden, kann sich die optimale Konfiguration unterscheiden. Experimentieren Sie immer, um die beste Konfiguration für Ihren Fall zu finden!

In der optimierten Lösung wurden 1,1 Millionen Daten Zeilen (mit 100 Features) in weniger als 8,5 Sekunden auf einem 20-Kern-Computer bewertet. Optimierungen verbessern die Leistung im Hinblick auf die Bewertungszeit erheblich.

Die Ergebnisse haben auch vorgeschlagen, dass sich die **Anzahl der Features** erheblich auf die Bewertungszeit ausgewirkt hat. Die Verbesserung war noch deutlicher, wenn im Vorhersagemodell weitere Features verwendet wurden.

Es wird empfohlen, dass Sie diesen Blog Artikel und das begleitende Tutorial lesen, um ausführliche Informationen zu erhalten.

-   [Tipps und Tricks zur Optimierung für Machine Learning in SQL Server](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/)

Viele Benutzer haben festgestellt, dass es eine kleine Pause gibt, da die R-Laufzeit (oder python) zum ersten Mal geladen wird. Aus diesem Grund wird die Zeit für die erste Testlauf, wie in diesen Tests beschrieben, häufig gemessen, aber später verworfen. Die nachfolgende Zwischenspeicherung kann zu bedeutenden Leistungsunterschieden zwischen der ersten und der zweiten Ausführung führen. Es gibt auch einen gewissen Aufwand, wenn Daten zwischen SQL Server und der externen Laufzeit verschoben werden, insbesondere dann, wenn Daten über das Netzwerk übergeben werden, anstatt direkt aus SQL Server geladen zu werden.

Aus diesen Gründen gibt es keine einzige Lösung, mit der Sie diese anfängliche Lade Zeit verringern können, da sich die Auswirkungen auf die Leistung abhängig von der Aufgabe erheblich unterscheiden. Beispielsweise wird das Zwischenspeichern für die einzeilige Bewertung in Batches ausgeführt. Folglich sind aufeinander folgende Bewertungs Vorgänge wesentlich schneller, und weder das Modell noch die R-Laufzeit wird erneut geladen. Sie können auch die [native Bewertung](../sql-native-scoring.md) verwenden, um das vollständige Laden der R-Laufzeit zu vermeiden.

Zum Trainieren von großen Modellen oder zum Bewerten von großen Batches kann der Aufwand minimal sein, wenn die Daten Verschiebung oder das Streaming und die parallele Verarbeitung vermieden werden. Weitere Hinweise zur Leistung finden Sie in diesem Blogbeitrag:

+ [Verwenden von R zum Erkennen von Betrug bei 1 Million Transaktionen pro Sekunde](https://blog.revolutionanalytics.com/2016/09/fraud-detection.html/)

## <a name="resources"></a>Ressourcen

Im folgenden finden Sie Links zu Informationen, Tools und Skripts, die bei der Entwicklung dieser Tests verwendet werden.

+ Leistungstest Skripts und Links zu den Daten: [Beispiel Daten und Skripts für SQL Server Optimierungen](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning)

+ Artikel, der die Projekt Mappe zum Fortsetzen des Abgleich [Tipps und Tricks zur Optimierung für SQL Server R Services](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/)

+ Skripts, die bei der SQL-Optimierung für die Projekt Mappe zum Wiederherstellen [GitHub-Repository](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips)

### <a name="learn-about-windows-server-management"></a>Weitere Informationen zur Windows Server-Verwaltung

+ [Vorgehensweise: Bestimmen der geeigneten Auslagerungsdateigröße für 64-Bit-Versionen von Windows](https://support.microsoft.com/kb/2860880)

+ [Grundlegendes zu NUMA](https://technet.microsoft.com/library/ms178144.aspx)

+ [Unterstützung von NUMA durch SQL Server](https://technet.microsoft.com/library/ms180954.aspx)

+ [Soft-NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)

### <a name="learn-about-sql-server-optimizations"></a>Weitere Informationen zu SQL Server Optimierungen

+ [Neuorganisieren und Neuerstellen von Indizes](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)

+ [Einführung in Speicher optimierte Tabellen](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables)

+ [Demo: Leistungsverbesserung von in-Memory OLTP](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp)

+ [Datenkomprimierung](../../relational-databases/data-compression/data-compression.md)

+ [Aktivieren der Komprimierung für eine Tabelle oder einen Index](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [Deaktivieren der Komprimierung für eine Tabelle oder einen Index](../../relational-databases/data-compression/disable-compression-on-a-table-or-index.md)

### <a name="learn-about-managing-sql-server"></a>Weitere Informationen zum Verwalten von SQL Server

+ [Überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md)

+ [Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor.md)

+ [Einführung in Resource Governor](https://technet.microsoft.com/library/bb895232.aspx)

+ [Ressourcenkontrolle für R Services](resource-governance-for-r-services.md)

+ [Erstellen eines Ressourcenpools für R](how-to-create-a-resource-pool-for-r.md)

+ [Ein Beispiel für das Konfigurieren von Resource Governor](https://blog.sqlauthority.com/2012/06/04/sql-server-simple-example-to-configure-resource-governor-introduction-to-resource-governor/)

### <a name="tools"></a>Tools

+ [DISKSPD storage load generator/performance test tool (DISKSPD-Speicherladungsgenerator/Leistungstesttool)](https://github.com/microsoft/diskspd)

+ [Referenz zum Hilfsprogramm FSUtil](https://technet.microsoft.com/library/cc753059.aspx)


## <a name="other-articles-in-this-series"></a>Weitere Artikel in dieser Serie

[Leistungsoptimierung für R-Einführung](sql-server-r-services-performance-tuning.md)

[Leistungsoptimierung für R-SQL Server-Konfiguration](sql-server-configuration-r-services.md)

[Leistungsoptimierung für r-r-Code und Daten Optimierung](r-and-data-optimization-r-services.md)

[Leistungsoptimierung: Ergebnisse der Fallstudie](performance-case-study-r-services.md)
