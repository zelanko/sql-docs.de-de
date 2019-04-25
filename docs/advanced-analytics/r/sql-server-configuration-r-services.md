---
title: SQL Server-Konfiguration (R Services) – SQL Server Machine Learning-Dienste
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 9ad4d1a23a05db35e0c4b55473903dbf7e4265da
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641944"
---
# <a name="sql-server-configuration-for-use-with-r"></a>SQL Server-Konfiguration für die Verwendung mit R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist der zweite aus einer Reihe, die leistungsoptimierung für R-Dienste, die basierend auf zwei Fallstudien beschreibt.  Dieser Artikel enthält Anleitungen zur Konfiguration Hardware- und Netzwerkkonfiguration des Computers, der zum Ausführen von SQL Server R Services verwendet wird. Es enthält auch Informationen zu Verfahren zum Konfigurieren der SQL Server-Instanz, Datenbank oder Tabellen, die in einer Projektmappe verwendet. Da es sich bei Verwendung von NUMA in SQL Server auf die Linie zwischen Hardware und Datenbank-Optimierungen verwischt, werden Dritter Abschnitt CPU Affinitization und Ressourcenkontrolle ausführlich erläutert.

> [!TIP]
> Wenn Sie mit SQL Server vertraut sind, wird dringend empfohlen, auch die Optimierung Leistungsleitfaden zu SQL Server zu lesen: [Überwachen und Optimieren der Leistung](https://docs.microsoft.com/sql/relational-databases/performance/monitor-and-tune-for-performance).

## <a name="hardware-optimization"></a>Hardwareoptimierung

Optimierung des Server-Computers ist wichtig, um sicherzustellen, dass die Ressourcen zum Ausführen externer Skripts. Wenn die Ressourcen beschränkt sind, können Sie wie die folgenden Symptome auf:

- Auftragsausführung zurückgestellt oder abgebrochen wird, für die Priorisierung von anderen Datenbankvorgängen
- Fehler "das Kontingent wurde überschritten" zu R-Skript ohne Abschluss beendet werden soll.
- Die Daten in R-Speicher, die abgeschnitten werden, für unvollständige Ergebnisse geladen

### <a name="memory"></a>Speicher

Der auf einem Computer verfügbare Arbeitsspeicher kann sich stark auf die Leistung komplexerer analytischer Algorithmen auswirken. Nicht genügend Arbeitsspeicher kann den Grad an Parallelität beeinträchtigen, wenn Sie den SQL Compute Context verwenden. Ebenso kann dadurch die verarbeitbare Segmentgröße (Zeilen pro Lesevorgang) beeinträchtigt werden sowie die Anzahl gleichzeitiger Sitzungen, die unterstützt werden kann.

Mindestens 32 GB wird dringend empfohlen. Wenn Sie mehr als 32 GB zur Verfügung haben, können Sie die SQL-Datenquelle, um mehr Zeilen in jedem Lesevorgang zu verwenden, zur Verbesserung der Leistung konfigurieren.

Sie können auch von der Instanz verwendeten Arbeitsspeicher verwalten. Standardmäßig wird SQL Server über externe Skriptprozesse priorisiert, wenn Speicher belegt wird. In einer Standardinstallation von R Services wird nur 20 % des verfügbaren Arbeitsspeichers zu r zugeordnet.

Dies ist normalerweise nicht ausreichend für Data Science-Aufgaben, aber weder möchten Sie SQLServer-Speicher zu blockieren. Sie experimentieren und Optimieren der Speicherzuordnung zwischen Datenbank-Engine, verknüpfte Dienste und externe Skripts, unter der Voraussetzung, die die optimale Konfiguration von Fall zu Fall unterschiedlich.

Externe Skripts wurde hohe und gab es keine andere Datenbank-Engine-Dienste, die ausgeführt wird, für das Modell fortsetzen übereinstimmende; aus diesem Grund wurden externer Skripts, die zugeordneten Ressourcen auf 70 % gesenkt, erhöht die war die beste Konfiguration für die skriptleistung.

### <a name="power-options"></a>Power-Optionen

Auf dem Windows-Betriebssystem das **hohe Leistung** Energieoption sollte verwendet werden. Verwenden eine andere Energieoption führt verringert oder ungleichmäßiger Leistung bei Verwendung von SQL Server.

### <a name="disk-io"></a>Eingabe bzw. Ausgabe von Laufwerken

Training und Vorhersage, dass Aufträge mithilfe von R Services grundsätzlich e/a sind gebunden, und hängen von der Geschwindigkeit der Datenträger, denen auf die Datenbank gespeichert ist. Schnellere Laufwerke wie Solid State Drives (SSD) können hilfreich sein.

Die Laufwerk-E/A hängt auch von anderen Anwendungen ab, die auf das Laufwerk zugreifen: z.B. von Lesevorgängen in einer Datenbank anderer Clients. Die E/A-Leistung des Laufwerks kann auch von den Einstellungen für das verwendete Dateisystem beeinträchtigt werden, wie z.B. von der vom Dateisystem verwendeten Blockgröße.

Wenn mehrere Laufwerke verfügbar sind, fordert Speicher, die die Datenbanken auf einem anderen Laufwerk als SQL Server so, dass für die Datenbank-Engine die Anforderungen nicht einen anderen Datenträger als erreichen, für Daten, die in der Datenbank gespeichert.

Die Laufwerk-E/A kann die Leistung deutlich beeinträchtigen, wenn analytische RevoScaleR-Funktionen ausgeführt werden, die während des Trainings mehrere Iterationen verwenden. Z. B. `rxLogit`, `rxDTree`, `rxDForest`, und `rxBTrees` verwenden alle mehrere Iterationen. Wenn die Datenquelle SQL Server ist, verwenden diese Algorithmen temporäre Dateien, die zum Erfassen von Daten optimiert sind. Diese Dateien werden nach dem Abschluss der Sitzung automatisch bereinigt. Einen Hochleistungs-Datenträger für Lese-und Schreibvorgänge kann die insgesamt verstrichene Zeit für diese Algorithmen erheblich verbessern.

> [!NOTE]
> Frühe Versionen von R Services erforderlich 8.3-Dateinamen-Unterstützung auf Windows-Betriebssystemen. Diese Einschränkung wurde nach Service Pack 1 aufgehoben. Allerdings können Sie fsutil.exe verwenden, um zu bestimmen, ob ein Laufwerk 8.3-Dateinamen unterstützt, oder um Unterstützung zu aktivieren, wenn dies nicht der Fall.

### <a name="paging-file"></a>Auslagerungsdatei

Das Windows-Betriebssystem verwendet eine Auslagerungsdatei, um Abstürze zu verwalten und virtuelle Arbeitsspeicherseiten zu speichern. Wenn Sie eine exzessive Auslagerung bemerken, ziehen Sie in Betracht, den physischen Arbeitsspeicher des Computers zu erweitern. Auch wenn mehr physischer Arbeitsspeicher die Auslagerung nicht vollständig eliminiert, wird der Auslagerungsbedarf doch gesenkt.

Auch die Geschwindigkeit des Laufwerks, auf dem die Auslagerungsdatei gespeichert ist, kann die Leistung beeinträchtigen. Wenn Sie die Auslagerungsdatei auf einem SSD speichern oder mehrere Auslagerungsdateien SSD-übergreifend verwenden, kann dies die Leistung verbessern.

Informationen zum Anpassen der Größe der Auslagerungsdatei finden Sie unter [Vorgehensweise: Bestimmen der geeigneten Auslagerungsdateigröße für 64-Bit-Versionen von Windows](https://support.microsoft.com/kb/2860880).

## <a name="optimizations-at-instance-or-database-level"></a>Optimierungen auf Instanz- oder Datenbankebene

Die Optimierung der SQL Server-Instanz ist der Schlüssel für die effiziente Ausführung externer Skripts.

> [!NOTE]
> Die optimalen Einstellungen variieren je nach Größe und Typ der Daten, die Anzahl der Spalten, die Sie für die Bewertung oder Trainieren eines Modells verwenden.
> 
> Sie können die Ergebnisse der bestimmte Optimierungen im letzten Artikel überprüfen: [Leistungsoptimierung - Fallstudie Ergebnisse](../../advanced-analytics/r/performance-case-study-r-services.md)
> 
> Beispielskripts, finden Sie unter der separaten [GitHub-Repository](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning).

### <a name="table-compression"></a>Tabellenkomprimierung

E/a-Leistung kann oft verbessert werden, mithilfe von Komprimierung oder einem spaltenbasierten Datenspeicher. Im Allgemeinen werden Daten häufig wiederholt in mehreren Spalten in einer Tabelle, damit mit einem columnstore-diese Wiederholungen nutzt, wenn er Daten komprimiert.

Ein Columnstore möglicherweise nicht so effizient, wenn viele einfügungen in der Tabelle vorhanden sind, aber es ist eine gute Wahl, wenn die Daten statisch oder nur selten. Wenn sich ein spaltenbasierter Speicher nicht eignet, können Sie die E/A verbessern, indem Sie die Komprimierung in einer überwiegend zeilenorientierten Tabelle aktivieren.

Weitere Informationen finden Sie in folgenden Dokumenten:

+ [Datenkomprimierung](../../relational-databases/data-compression/data-compression.md)

+ [Aktivieren der Komprimierung für eine Tabelle oder einen index](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [Columnstore-Indizes: Übersicht](../../relational-databases/indexes/columnstore-indexes-overview.md)

### <a name="memory-optimized-tables"></a>Speicheroptimierte Tabellen

Speicher ist heutzutage nicht mehr ein Problem für moderne Computer. Wie Hardwarespezifikationen verbessern weiter, ist es relativ einfach, um RAM gute Werte zu erhalten. Allerdings zur gleichen Zeit, Daten schneller als je zuvor werden erstellt wird, und die Daten mit geringer Latenz verarbeitet werden müssen.

Speicheroptimierte Tabellen stellen eine Lösung dar, nutzen sie die großen Arbeitsspeicher, die im erweiterten Computer aus, um das Problem von big Data anzugehen verfügbar. Speicheroptimierte Tabellen befinden sich hauptsächlich im Arbeitsspeicher, sodass Daten auslesen und in den Speicher geschrieben. Für Stabilität eine zweite Kopie der Tabelle wird auf dem Datenträger beibehalten, und Daten werden nur während der datenbankwiederherstellung vom Datenträger gelesen.

Wenn Sie Lese- und Schreibvorgänge in Tabellen häufig müssen, können durch Speicheroptimierte Tabellen mit hoher Skalierbarkeit und niedriger Latenz.  In diesem Szenario fortsetzen übereinstimmende Speicheroptimierte Tabellen verwendet hatten wir alle fortsetzen Funktionen aus der Datenbank gelesen, und speichern diese im Hauptspeicher, mit der neuen Besetzung freier Positionen übereinstimmen muss. Dies verringert erheblich die Datenträger-e/a.

Zusätzliche Leistungsgewinne wurden mit einer speicheroptimierten Tabelle während der Verfassung Vorhersagen sichern mit der Datenbank aus mehreren gleichzeitigen Batches erreicht. Die Verwendung von speicheroptimierten Tabellen auf SQL Server werden mit geringer Latenz für Tabelle Lese- und Schreibvorgänge aktiviert.

Die Erfahrung war mir auch während der Entwicklung nahtlos. Dauerhafte Speicheroptimierte Tabellen wurden zur gleichen Zeit erstellt, die die Datenbank erstellt wurde. Daher verwendet die Entwicklung des gleichen Workflows, unabhängig davon, wo die Daten gespeichert wurde.

### <a name="processor"></a>Prozessor

SQL Server können Aufgaben parallel ausführen, indem mithilfe der verfügbaren Kerne auf dem Computer; Je mehr Kerne, die verfügbar sind, desto besser die Leistung. Erhöhen der Anzahl von Kernen für e/a-gebundene Vorgänge nicht helfen kann, gebunden CPU Vorteil von Algorithmen von schnelleren CPUs mit vielen Kernen.

Da der Server normalerweise gleichzeitig von mehreren Benutzern verwendet wird, muss der Datenbankadministrator die ideale Anzahl von Kernen bestimmen, die erforderlich sind, um die höchsten arbeitsauslastungsberechnungen zu unterstützen.

### <a name="resource-governance"></a>Ressourcenkontrolle

In den Editionen, die die Ressourcenkontrolle unterstützen, können Sie Ressourcenpools verwenden, um anzugeben, dass bestimmte Workloads eine Anzahl von CPUs zugeordnet werden. Sie können auch die Menge des Arbeitsspeichers für bestimmte Workloads verwalten.

Die Ressourcenkontrolle in SQL Server können Sie die Überwachung und die Kontrolle über die verschiedenen Ressourcen, die von SQL Server und r verwendeten zentralisieren Sie können z. B. zuordnen, dass die Hälfte der verfügbare Speicherplatz für die Datenbank-Engine, stellen Sie sicher, dass Kern, die Dienste immer trotz vorübergehender größere Workloads ausgeführt werden können.

Der Standardwert für die arbeitsspeichernutzung von externen Skripts ist auf 20 % des gesamten Speichers für SQL Server selbst beschränkt. Dieser Grenzwert wird angewendet, in der Standardeinstellung, um sicherzustellen, dass alle Aufgaben, die auf dem Datenbankserver basieren durch R-Aufträgen mit langer Ausführung nicht schwerwiegend beeinträchtigt werden. Diese Einschränkungen können vom Datenbankadministrator angepasst werden. In vielen Fällen ist das Limit von 20 % nicht ausreichend, um schwerwiegende Machine learning-Workloads zu unterstützen.

Die Konfigurationsoptionen unterstützt sind **MAX_CPU_PERCENT**, **MAX_MEMORY_PERCENT**, und **MAX_PROCESSES**. Um die aktuellen Einstellungen anzuzeigen, verwenden Sie diese Anweisung aus: `SELECT * FROM sys.resource_governor_external_resource_pools`

-  Wenn der Server für R Services in erster Linie verwendet wird, kann es hilfreich, MAX_CPU_PERCENT auf 40 oder 60 % zu erhöhen. sein.

-  Wenn viele R-Sitzungen auf den gleichen Server zur gleichen Zeit verwenden müssen, sollten alle drei Einstellungen erhöht werden.

Verwenden Sie T-SQL-Anweisungen, um zugewiesene Ressourcenwerte zu ändern.

+ Diese Anweisung wird die arbeitsspeichernutzung auf 40 %: `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_MEMORY_PERCENT = 40)`

+ Diese Anweisung legt alle drei konfigurierbaren Werte fest: `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_CPU_PERCENT = 40, MAX_MEMORY_PERCENT = 50, MAX_PROCESSES = 20)`

+ Wenn Sie einen Arbeitsspeicher, CPU oder maximalen Prozesse zu ändern, und klicken Sie dann auf die Einstellungen sofort angewendet werden soll, führen Sie diese Anweisung: `ALTER RESOURCE GOVERNOR RECONFIGURE`

## <a name="soft-numa-hardware-numa-and-cpu-affinity"></a>Soft-NUMA-Hardware-NUMA und CPU-Affinität

Wenn Sie SQL Server als Compute Context verwenden, können Sie manchmal eine bessere Leistung erzielen, durch das Optimieren der Einstellungen im Zusammenhang mit NUMA und prozessorzugehörigkeit. 

Systeme mit _NUMA-Hardware_ haben Sie mehrere Systembusse, von denen jeder eine kleine Gruppe von Prozessoren bedient. Jede CPU kann auf Arbeitsspeicher, die anderen Gruppen zugeordnet sind, auf kohärente Weise zugreifen. Jede dieser Gruppen stellt einen NUMA-Knoten dar. Wenn Sie über NUMA-Hardware verfügen, können Sie sie ggf. so konfigurieren, dass anstelle von NUMA Interleave-Speicher verwendet wird. In diesem Fall wird SQL Server, Windows und daher nicht als NUMA erkannt. 

Sie können die folgende Abfrage zum Ermitteln der Anzahl von Speicherknoten, die für SQL Server verfügbaren ausführen:

```sql
SELECT DISTINCT memory_node_id
FROM sys.dm_os_memory_clerks
```

Wenn die Abfrage einen einzigen Speicherknoten (Knoten 0) zurückgibt, Sie verfügen nicht über die NUMA-Hardware, oder die Hardware als verschachtelte (nicht-NUMA) konfiguriert ist. SQL Server ignoriert auch Hardware-NUMA bei der es maximal vier CPUs oder mindestens einem Knoten nur eine CPU aufweist.

Wenn der Computer verfügt über mehrere Prozessoren, jedoch keinen Hardware-NUMA, können Sie auch [Soft-NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server) CPUs in kleinere Gruppen unterteilen.  In SQL Server 2016 und SQL Server 2017 wird das Feature Soft-NUMA automatisch aktiviert, beim Starten des SQL Server-Diensts.

Wenn Soft-NUMA aktiviert ist, werden die Knoten für Sie automatisch von SQL Server verwaltet; Um für bestimmte arbeitsauslastungen zu optimieren, Sie können jedoch deaktivieren _weicher Affinität_ und CPU-Affinität für die soft-NUMA-Knoten manuell zu konfigurieren. Dies bietet Ihnen mehr Kontrolle über die arbeitsauslastungen, für die Knoten zugewiesen sind, insbesondere dann, wenn Sie eine Edition von SQL Server verwenden, die Unterstützung der Ressourcenkontrolle. Sie können durch Angabe der CPU-Affinität und zum Ausrichten von Ressourcenpools für Gruppen von CPUs, die Latenz verringern und stellen Sie sicher, dass verwandte Prozesse im selben NUMA-Knoten ausgeführt werden.

Der allgemeine Prozess zum Konfigurieren von Soft-NUMA und CPU-Affinität zur Unterstützung von R-arbeitsauslastungen lautet wie folgt aus:

1. Aktivieren von Soft-NUMA, falls verfügbar
2. Definieren von Prozessor-Affinität
3. Erstellen von Ressourcenpools für externe Prozesse, die mit [Resource Governor](../r/resource-governance-for-r-services.md)
4. Weisen Sie die [Arbeitsauslastungsgruppen](../../relational-databases/resource-governor/resource-governor-workload-group.md) mit bestimmten affinitätsgruppen

Weitere Informationen, einschließlich Beispielcode finden Sie im Tutorial: [SQL Optimization-Tipps und Tricks (Ke Huang)](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**Weitere Ressourcen:**

+ [Soft-NUMA in SQLServer](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)
    
    Zuordnen von Soft-NUMA-Knoten zu CPUs

## <a name="task-specific-optimizations"></a>Aufgabenspezifische-Optimierungen

In diesem Abschnitt werden die Methoden, die übernommen werden, in diese Fallstudien und in anderen Tests, zur Optimierung der bestimmten Machine learning-Workloads zusammengefasst. Gängige Workloads sind das Trainieren des Modells, featureextraktion und Feature-Engineering und verschiedene Szenarien für die Bewertung: einzeiliges, kleinen und großen Batches.

### <a name="feature-engineering"></a>Featureentwicklung

Ein ist Problem mit R, dass sie in der Regel mit einer CPU verarbeitet wird. Dies ist eine größte Leistungsengpass für viele Aufgaben, insbesondere die Featureentwicklung. In der Lösung fortsetzen übereinstimmende erstellt, die allein Feature-Entwicklungsaufgabe 2.500 Kreuzprodukt-Funktionen, die mit den ursprünglichen 100-Funktionen kombiniert werden musste. Diese Aufgabe kann viel Zeit, wenn alles, was mit einer CPU ausgeführt wurde.

Es gibt mehrere Möglichkeiten zur Verbesserung der Leistung der Featureentwicklung. Sie können entweder den R-Code zu optimieren und featureextraktion innerhalb des Prozesses für die datenmodellierung beibehalten, oder verschieben den Feature-engineering-Prozess in SQL.

- Mit R. Sie definieren eine Funktion, und übergeben Sie sie als Argument für [RxTransform](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxtransform) während des Trainings. Wenn das Modell die parallelen Verarbeitung unterstützt, kann die Feature-Entwicklungsaufgabe mit mehreren CPUs verarbeitet werden. Mit diesem Ansatz beobachtet der Data Science-Team eine leistungsverbesserung von 16 % in Bezug auf die Bewertung der Zeit. Dieser Ansatz erfordert jedoch ein Modell, das unterstützt Parallelisierung und eine Abfrage, die mit einem parallelen Plan ausgeführt werden kann.

- Verwenden von R mit SQL compute Context verwenden. In einer multiprozessorumgebung mit isolierten Ressourcen, die für die Ausführung separater Batches verfügbar können Sie höhere Effizienz erreichen, durch die SQL-Abfragen, die für jeden Batch verwendet wird, um Daten aus Tabellen extrahieren und Einschränken der Daten auf die gleiche Arbeitsauslastungsgruppe zu isolieren. Methoden zum Isolieren von Batches Partitionierung, und Verwenden von PowerShell separate Abfragen parallel ausgeführt.

- Ad-hoc-parallele Ausführung: In einem SQL Server-computekontext können Sie verlassen, auf die SQL-Datenbank-Engine zu erzwingen, wenn möglich die parallele Ausführung und wenn diese Option ist um noch effizienter zu werden.

- Verwenden Sie T-SQL in einem separaten featurebereitstellung-Prozess. Precomputing die Funktionsdaten mit SQL ist im Allgemeinen schneller.

### <a name="prediction-scoring-in-parallel"></a>Vorhersagen (Bewertung), parallel

Einer der Vorteile von SQL Server ist die Fähigkeit, eine große Anzahl von Zeilen, die parallel zu verarbeiten. Dieser Vorteil wird nicht einmal annähernd so wie bei der Bewertung markiert werden. In der Regel benötigt das Modell keine Berechtigung auf alle Daten für die Bewertung, damit Sie Partitionieren der Eingabedaten, mit jeder Arbeitsauslastungsgruppe, die eine Aufgabe verarbeiten können.

Sie können auch die eingegebenen Daten senden, als eine einzelne Abfrage und SQL Server analysiert die Abfrage. Wenn es sich bei ein parallelen Abfrageplan für die Eingabedaten erstellt werden kann, werden automatisch partitioniert Daten, die dem Knoten zugewiesen und führt die erforderlichen Joins und Aggregationen sowie Parallel.

Wenn Sie die Details eine gespeicherte Prozedur für die Verwendung in Wertung fest definieren möchten, sehen Sie das Beispielprojekt auf [GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips/SQLR) und suchen Sie nach der Datei "step5_score_for_matching.sql". Das Beispiel auch abfragestart verfolgt und Endzeiten und Skript schreibt die Zeit für die SQL-Konsole, damit Sie die Leistung bewerten können.

### <a name="concurrent-scoring-using-resource-groups"></a>Gleichzeitige Bewertung verwenden von Ressourcengruppen

Eine bewährte Methode werden zum Skalieren der Bewertung Problems der map-reduce-Ansatz verfolgen, in dem Millionen von Elementen in mehrere Batches aufgeteilt werden. Anschließend werden mehrere Bewertung Aufträge gleichzeitig ausgeführt werden. In diesem Framework die Batches sind auf verschiedene CPU-Gruppen verarbeitet, und die Ergebnisse werden gesammelt und zurück in die Datenbank geschrieben.

Dies ist der Ansatz, in dem Szenario fortsetzen übereinstimmende verwendet. Allerdings ist die Ressourcenkontrolle in SQL Server für die Implementierung dieser Vorgehensweise unerlässlich. Arbeitsauslastungsgruppen für externe Skripts für Aufträge festlegen können Sie R-Aufträge auf unterschiedlichen Prozessorgruppen Bewertung weiterleiten, und einen schnelleren Durchsatz erzielen.

Ressourcenkontrolle können auch die zuordnen Teilen Sie die verfügbaren Ressourcen auf dem Server (CPU und Arbeitsspeicher), um die arbeitsauslastung Wettbewerb zu minimieren. Sie können Klassifizierungsfunktionen einrichten, um zwischen verschiedenen Typen von R-Aufträge zu unterscheiden: Sie können beispielsweise festlegen, dass es sich bei Bewertung von einer Anwendung immer aufgerufen Priorität verwendet werden, während des erneuten Trainings Aufträge mit niedriger Priorität haben. Diese Isolierung von Ressourcen kann möglicherweise Ausführungszeit verbessern und besser vorhersagbaren Leistung bereitstellen.

### <a name="concurrent-scoring-using-powershell"></a>Gleichzeitige Bewertung mithilfe von PowerShell

Wenn Sie die Daten zu partitionieren möchten, können Sie PowerShell-Skripts, um mehrere gleichzeitige bewertungs-Aufgaben auszuführen. Zu diesem Zweck verwenden Sie das Invoke-SqlCmd-Cmdlet aus, und initiieren Sie die Bewertung Aufgaben parallel zu.

In diesem Szenario fortsetzen übereinstimmende wurde Parallelität wie folgt konzipiert:

- 20 Prozessoren, die in vier Gruppen von fünf CPUs unterteilt sind. Jede Gruppe von CPUs befindet sich auf dem gleichen NUMA-Knoten.

- Maximale Anzahl von gleichzeitigen Batches wurde auf acht festgelegt.

- Jede Arbeitsauslastungsgruppe muss zwei Bewertungsaufgaben behandeln. Sobald eine Aufgabe abgeschlossen, Lesen von Daten und die Bewertung beginnt, kann die andere Aufgabe Lesen von Daten aus der Datenbank starten.

Um die PowerShell-Skripts für dieses Szenario zu anzuzeigen, öffnen Sie die Datei experiment.ps1 in die [Github-Projekt](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips).

### <a name="storing-models-for-prediction"></a>Speichern von Modellen für Vorhersagen

Beim Training und Auswertung abgeschlossen ist und Sie einem bewährten Modell ausgewählt haben, wird empfohlen, das Modell in der Datenbank gespeichert, so, dass sie für Vorhersagen verfügbar ist. Laden das vorberechnete Modell aus der Datenbank für die Vorhersage ist effizient, da SQL Server-Machine Learning spezielle Serialisierung Algorithmen zum Speichern und Laden Modelle, beim Verschieben zwischen R und der Datenbank verwendet wird.

> [!TIP]
> In SQL Server 2017 können Sie die PREDICT-Funktion zum Durchführen von Bewertungen, auch wenn R nicht auf dem Server installiert ist. Eingeschränkte Modelltypen werden unterstützt, aus dem RevoScaleR-Paket.

Je nach Algorithmus, die, den Sie verwenden, kann einige Modelle sehr groß ist, jedoch insbesondere dann, wenn für eine große Menge von Daten trainiert. Z. B. Algorithmen wie **lm** oder **"glm"** generiert viele Zusammenfassungsdaten zusammen mit Regeln. Da-Einschränkungen in Bezug auf die Größe eines Modells, die in einen Varbinary-Spalte gespeichert werden können bestehen, empfehlen wir, dass Sie vor dem Speichern des Modells in der Datenbank für die Produktion von unnötigen Artefakte aus dem Modell entfernen.

## <a name="articles-in-this-series"></a>Artikel in dieser Serie

[Leistung optimieren, die für R – Einführung](../r/sql-server-r-services-performance-tuning.md)

[Leistungsoptimierung für R – SQL Server-Konfiguration](../r/sql-server-configuration-r-services.md)

[Leistungsoptimierung für R – R-Code und Daten-Optimierung](../r/r-and-data-optimization-r-services.md)

[Leistungsoptimierung - Fallstudie Ergebnisse](../r/performance-case-study-r-services.md)
