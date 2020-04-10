---
title: Konfiguration für die Verwendung mit R
description: Dieser Artikel enthält Anleitungen zur Hardware- und Netzwerkkonfiguration des Computers, der zum Ausführen von SQL Server R Services verwendet wird.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: cedc5c08f44da357da70f63b47676383f6f53675
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "81117343"
---
# <a name="sql-server-configuration-for-use-with-r"></a>SQL Server-Konfiguration für die Verwendung mit R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel ist der zweite in einer Reihe, in der die Leistungsoptimierung für R Services basierend auf zwei Fallstudien beschrieben wird.  Dieser Artikel enthält Anleitungen zur Hardware- und Netzwerkkonfiguration des Computers, der zum Ausführen von SQL Server R Services verwendet wird. Außerdem enthält er Informationen zu Methoden zum Konfigurieren der SQL Server-Instanz, der Datenbank oder der Tabellen, die in einer Lösung verwendet werden. Da bei Verwendung von NUMA in SQL Server die Trennlinie zwischen Hardware- und Datenbankoptimierungen unscharf ist, werden in einem dritten Abschnitt CPU-Affinität und Ressourcenkontrolle ausführlich erläutert.

> [!TIP]
> Wenn Sie noch nicht mit SQL Server vertraut sind, sollten Sie unbedingt das Handbuch zur SQL Server-Leistungsoptimierung lesen: [Überwachen und Optimieren der Leistung](https://docs.microsoft.com/sql/relational-databases/performance/monitor-and-tune-for-performance).

## <a name="hardware-optimization"></a>Hardwareoptimierung

Die Optimierung des Servercomputers ist wichtig, um sicherzustellen, dass Sie über die Ressourcen zum Ausführen externer Skripts verfügen. Wenn Ressourcen eingeschränkt sind, werden möglicherweise folgende Symptome angezeigt:

- Die Auftragsausführung wird verzögert oder abgebrochen, um andere Datenbankvorgänge zu priorisieren.
- Der Fehler „Kontingent wurde überschritten“ bewirkt, dass das R-Skript ohne Abschluss beendet wird.
- In den R-Speicher geladene Daten werden gekürzt, sodass Ergebnisse unvollständig sind.

### <a name="memory"></a>Arbeitsspeicher

Der auf einem Computer verfügbare Arbeitsspeicher kann sich stark auf die Leistung komplexerer analytischer Algorithmen auswirken. Nicht ausreichender Arbeitsspeicher könnte den Grad an Parallelität beeinträchtigen, wenn Sie den SQL-Rechenkontext verwenden. Ebenso kann dadurch die verarbeitbare Segmentgröße (Zeilen pro Lesevorgang) beeinträchtigt werden sowie die Anzahl gleichzeitiger Sitzungen, die unterstützt werden kann.

Eine Mindestgröße von 32 GB wird unbedingt empfohlen. Wenn Ihnen mehr als 32 GB zur Verfügung stehen, können Sie die SQL-Datenquelle so konfigurieren, dass sie mehr Zeilen in jedem Lesevorgang verwendet, um die Leistung zu verbessern.

Sie können auch den von der Instanz verwendeten Arbeitsspeicher verwalten. Standardmäßig wird SQL Server gegenüber Prozessen externer Skripts priorisiert, wenn Arbeitsspeicher zugewiesen wird. In einer Standardinstallation von R Services werden nur 20 % des verfügbaren Arbeitsspeichers zugeordnet.

Dies reicht in der Regel für Data Science-Aufgaben nicht aus, aber Sie möchten auch nicht den Arbeitsspeicher für SQL Server beeinträchtigen. Sie sollten experimentieren und die Speicherbelegungen für Datenbank-Engine, zugehörige Dienste und externe Skripts genau aufeinander abstimmen und dabei berücksichtigen, dass die optimale Konfiguration von Fall zu Fall variiert.

Für das Modell zum Abgleich von Lebensläufen lag der Schwerpunkt auf der Verwendung des externen Skripts, und es wurden keine anderen Datenbank-Engine-Dienste ausgeführt. Daher wurde die Zuordnung von Ressourcen zu externen Skripts auf 70 % heraufgesetzt. Dies war die beste Konfiguration für die Skriptleistung.

### <a name="power-options"></a>Leistungsoptionen

Sie sollten unter einem Windows-Betriebssystem die Option **Hohe Leistung** verwenden. Wenn Sie eine andere Leistungsoption verwenden, führt dies zu verminderter oder ungleichmäßiger Leistung beim Gebrauch von SQL Server.

### <a name="disk-io"></a>Datenträger-E/A

Trainings- und Prognoseaufträge mit R Services sind grundsätzlich E/A-abhängig; sie hängen von der Geschwindigkeit des Laufwerks bzw. der Laufwerke ab, auf dem/denen die Datenbank gespeichert ist. Schnellere Laufwerke wie Solid State Drives (SSD) helfen möglicherweise.

Die Laufwerk-E/A hängt auch von anderen Anwendungen ab, die auf das Laufwerk zugreifen: z.B. von Lesevorgängen in einer Datenbank anderer Clients. Die E/A-Leistung des Laufwerks kann auch von den Einstellungen für das verwendete Dateisystem beeinträchtigt werden, wie z.B. von der vom Dateisystem verwendeten Blockgröße.

Wenn mehrere Laufwerke zur Verfügung stehen, speichern Sie die Datenbanken auf einem Laufwerk, das nicht von SQL Server genutzt wird, damit an die Datenbank-Engine gerichtete Anforderungen nicht das gleiche Laufwerk wie Anforderungen in der Datenbank gespeicherter Daten betreffen.

Die Laufwerk-E/A kann die Leistung deutlich beeinträchtigen, wenn analytische RevoScaleR-Funktionen ausgeführt werden, die während des Trainings mehrere Iterationen verwenden. `rxLogit`, `rxDTree`, `rxDForest` und `rxBTrees` verwenden alle mehrere Iterationen. Wenn SQL Server die Datenquelle ist, verwenden diese Algorithmen temporäre Dateien, die für das Erfassen der Daten optimiert wurden. Diese Dateien werden nach dem Abschluss der Sitzung automatisch bereinigt. Wenn Sie über ein leistungsstarkes Laufwerk für Lese-/Schreibvorgänge verfügen, kann dies die insgesamt benötigte Zeit für diese Algorithmen verringern.

> [!NOTE]
> Frühe Versionen von R Services erforderten die Unterstützung von 8.3-Dateinamen auf Windows-Betriebssystemen. Diese Einschränkung wurde nach Service Pack 1 aufgehoben. Sie können jedoch „fsutil.exe“ verwenden, um zu bestimmen, ob ein Laufwerk 8.3-Dateinamen unterstützt, oder um die Unterstützung zu aktivieren, falls dies nicht zutrifft.

### <a name="paging-file"></a>Auslagerungsdatei

Das Windows-Betriebssystem verwendet eine Auslagerungsdatei, um Abstürze zu verwalten und virtuelle Arbeitsspeicherseiten zu speichern. Wenn Sie eine exzessive Auslagerung bemerken, ziehen Sie in Betracht, den physischen Arbeitsspeicher des Computers zu erweitern. Auch wenn mehr physischer Arbeitsspeicher die Auslagerung nicht vollständig eliminiert, wird der Auslagerungsbedarf doch gesenkt.

Auch die Geschwindigkeit des Laufwerks, auf dem die Auslagerungsdatei gespeichert ist, kann die Leistung beeinträchtigen. Wenn Sie die Auslagerungsdatei auf einem SSD speichern oder mehrere Auslagerungsdateien SSD-übergreifend verwenden, kann dies die Leistung verbessern.

Weitere Informationen zum Anpassen der Größe der Auslagerungsdatei finden Sie unter [Vorgehensweise: Bestimmen der geeigneten Auslagerungsdateigröße für 64-Bit-Versionen von Windows](https://support.microsoft.com/kb/2860880).

## <a name="optimizations-at-instance-or-database-level"></a>Optimierungen auf Instanz- oder Datenbankebene

Die Optimierung der SQL Server-Instanz ist der Schlüssel zur effizienten Ausführung externer Skripts.

> [!NOTE]
> Die optimalen Einstellungen unterscheiden sich abhängig von der Größe und dem Typ der Daten, sowie der Anzahl von Spalten, die Sie für Bewertung oder Training eines Modells verwenden.
> 
> Sie können die Ergebnisse spezifischer Optimierungen im letzten Artikel überprüfen: [Leistungsoptimierung – Ergebnisse der Fallstudie](../../machine-learning/r/performance-case-study-r-services.md)
> 
> Beispielskripts finden Sie im separaten [GitHub-Repository](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning).

### <a name="table-compression"></a>Tabellenkomprimierung

Die E/A-Leistung kann oft verbessert werden, indem Sie die Komprimierung oder einen einspaltigen Datenspeicher verwenden. Für gewöhnlich wiederholen sich Daten oft in mehreren Spalten in einer Tabelle; diese Wiederholungen werden bei Verwendung eines Columnstores bei der Datenkomprimierung genutzt.

Ein Columnstore ist möglicherweise nicht besonders effizient, wenn zahlreiche Einfügungen in der Tabelle vorhanden sind; er ist aber gut geeignet für statische Daten oder Daten, die sich nur selten verändern. Wenn sich ein spaltenbasierter Speicher nicht eignet, können Sie die E/A verbessern, indem Sie die Komprimierung in einer überwiegend zeilenorientierten Tabelle aktivieren.

Weitere Informationen finden Sie in den folgenden Dokumenten:

+ [Datenkomprimierung](../../relational-databases/data-compression/data-compression.md)

+ [Aktivieren der Komprimierung für eine Tabelle oder einen Index](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [Columnstore-Indizes: Übersicht](../../relational-databases/indexes/columnstore-indexes-overview.md)

### <a name="memory-optimized-tables"></a>Speicheroptimierte Tabellen

Der Arbeitsspeicher ist heute für moderne Computer unproblematisch. Da sich die Hardwarespezifikationen ständig verbessern, ist es relativ einfach, RAM mit guten Werten zu bekommen. Gleichzeitig werden Daten jedoch schneller als je zuvor erstellt und müssen mit geringer Latenz verarbeitet werden.

Speicheroptimierte Tabellen sind eine Lösung, da sie den in fortschrittlichen Computern verfügbaren großen Arbeitsspeicher nutzen, um dem Big Data-Problem zu begegnen. Speicheroptimierte Tabellen befinden sich hauptsächlich im Arbeitsspeicher, sodass Daten aus dem Arbeitsspeicher gelesen und dort hineingeschrieben werden. Zur Dauerhaftigkeit wird eine zweite Kopie der Tabelle auf dem Datenträger beibehalten, und die Daten werden während der Datenbankwiederherstellung nur vom Datenträger gelesen.

Wenn Sie häufig Lese- und Schreibzugriffe auf Tabellen ausführen müssen, können speicheroptimierte Tabellen mit hoher Skalierbarkeit und geringer Latenz hilfreich sein.  Im Szenario zum Abgleich von Lebensläufen konnten wir mit speicheroptimierten Tabellen alle Lebenslauffeatures aus der Datenbank lesen und im Hauptspeicher ablegen, um sie mit neuen Stellenangeboten abzugleichen. Die Datenträger-E/A wurde damit erheblich reduziert.

Zusätzliche Leistungssteigerungen wurden durch Verwendung einer speicheroptimierten Tabelle beim Zurückschreiben von Vorhersagen aus mehreren parallelen Batches in die Datenbank erzielt. Die Verwendung speicheroptimierter Tabellen in SQL Server ermöglichte geringe Latenz bei Lese- und Schreibvorgängen in Tabellen.

Die Erfahrung war auch während der Entwicklung nahtlos. Dauerhafte speicheroptimierte Tabellen wurden zur gleichen Zeit erstellt wie die Datenbank. Daher wurde bei der Entwicklung unabhängig davon, wo die Daten gespeichert wurden, derselbe Workflow verwendet.

### <a name="processor"></a>Prozessor

SQL Server kann Aufgaben mithilfe der auf dem Computer verfügbaren Kerne gleichzeitig ausführen. Je mehr Kerne zur Verfügung stehen, desto besser ist die Leistung. Während das Erhöhen der Anzahl von Kernen möglicherweise nicht bei E/A-abhängigen Operationen hilft, profitieren CPU-abhängige Algorithmen von schnelleren CPUs mit vielen Kernen.

Da der Server normalerweise von mehreren Benutzern gleichzeitig verwendet wird, muss der Datenbankadministrator die ideale Anzahl von Kernen bestimmen, die erforderlich sind, um die höchsten Workloadberechnungen zu unterstützen.

### <a name="resource-governance"></a>Ressourcengovernance

In Editionen, die den Resource Governor unterstützen, können Sie mithilfe von Ressourcenpools angeben, dass bestimmte Workloads einer bestimmten Anzahl von CPUs zugeordnet werden. Sie können auch die Arbeitsspeichermenge verwalten, die bestimmten Workloads zugeordnet wird.

Mithilfe der Ressourcenkontrolle in SQL Server können Sie die Überwachung und Steuerung der verschiedenen Ressourcen zentralisieren, die von SQL Server und R verwendet werden. Beispielsweise können Sie die Hälfte des verfügbaren Arbeitsspeichers für die Datenbank-Engine zuordnen, um sicherzustellen, dass die Kerndienste trotz vorübergehender umfangreicher Workloads immer ausgeführt werden können.

Der Standardwert für die Arbeitsspeichernutzung durch externe Skripts ist auf 20 % des gesamten für SQL Server selbst verfügbaren Arbeitsspeichers beschränkt. Diese Beschränkung wird standardmäßig angewendet, um sicherzustellen, dass alle Aufgaben, die auf dem Datenbankserver basieren, von zeitintensiven R-Aufträgen nicht schwerwiegend betroffen sind. Diese Einschränkungen können vom Datenbankadministrator angepasst werden. In vielen Fällen reicht das Limit von 20 % nicht aus, um umfangreiche Machine Learning-Workloads zu unterstützen.

Die unterstützten Konfigurationsoptionen sind **MAX_CPU_PERCENT**, **MAX_MEMORY_PERCENT** und **MAX_PROCESSES**. Verwenden Sie folgende `SELECT * FROM sys.resource_governor_external_resource_pools`-Anweisung, um die aktuellen Einstellungen anzuzeigen:

-  Wenn der Server primär für R Services verwendet wird, kann es sinnvoll sein, „MAX_CPU_PERCENT“ auf 40 oder 60 % zu erhöhen.

-  Wenn viele R-Sitzungen gleichzeitig denselben Server verwenden müssen, sollten alle drei Einstellungen erweitert werden.

Verwenden Sie T-SQL-Anweisungen, um zugewiesene Ressourcenwerte anzupassen.

+ Mit dieser Anweisung wird die Arbeitsspeichernutzung auf 40 % festgelegt: `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_MEMORY_PERCENT = 40)`

+ Mit dieser Anweisung werden alle drei konfigurierbaren Werte festgelegt: `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_CPU_PERCENT = 40, MAX_MEMORY_PERCENT = 50, MAX_PROCESSES = 20)`

+ Wenn Sie eine Einstellung für den Arbeitsspeicher, die CPU oder die maximale Anzahl von Prozessen ändern und die Einstellungen dann sofort anwenden möchten, führen Sie folgende Anweisung aus: `ALTER RESOURCE GOVERNOR RECONFIGURE`

## <a name="soft-numa-hardware-numa-and-cpu-affinity"></a>Soft-NUMA, Hardware-NUMA und CPU-Affinität

Wenn Sie SQL Server als Computekontext verwenden, können Sie mitunter eine bessere Leistung erzielen, indem Sie Einstellungen im Zusammenhang mit NUMA und Prozessoraffinität optimieren. 

Computer mit _Hardware-NUMA_ verfügen über mehrere Systembusse, von denen jeder eine kleine Gruppe von Prozessoren bedient. Jede CPU kann auf kohärente Weise auf Arbeitsspeicher zugreifen, der anderen Gruppen zugeordnet ist. Jede dieser Gruppen stellt einen NUMA-Knoten dar. Wenn Sie über NUMA-Hardware verfügen, können Sie sie ggf. so konfigurieren, dass anstelle von NUMA Interleave-Speicher verwendet wird. In diesem Fall erkennt Windows, und damit auch SQL Server, die Hardware nicht als NUMA. 

Sie können die folgende Abfrage ausführen, um die für SQL Server verfügbare Anzahl von Speicherknoten zu suchen:

```sql
SELECT DISTINCT memory_node_id
FROM sys.dm_os_memory_clerks
```

Wenn die Abfrage einen einzigen Speicherknoten (Knoten 0) zurückgibt, verfügen Sie entweder nicht über NUMA-Hardware, oder die Hardware ist als interleaved konfiguriert (Nicht-NUMA). SQL Server ignoriert auch Hardware-NUMA, wenn vier oder weniger CPUs vorhanden sind oder mindestens ein Knoten nur über eine CPU verfügt.

Wenn Ihr Computer über mehrere Prozessoren, jedoch nicht über Hardware-NUMA verfügt, können Sie auch [Soft-NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server) verwenden, um CPUs in kleinere Gruppen zu unterteilen.  In SQL Server 2016 und SQL Server 2017 wird das Soft-NUMA-Feature beim Starten des SQL Server-Diensts automatisch aktiviert.

Wenn Soft-NUMA aktiviert ist, werden die Knoten von SQL Server automatisch verwaltet. Zur Optimierung für bestimmte Workloads können Sie jedoch die _weiche Affinität_ deaktivieren und die CPU-Affinität für die Soft-NUMA-Knoten manuell konfigurieren. So können Sie besser steuern, welche Workloads welchen Knoten zugewiesen werden, insbesondere dann, wenn Sie eine Edition von SQL Server verwenden, die die Ressourcenkontrolle unterstützt. Indem Sie die CPU-Affinität angeben und Ressourcenpools an Gruppen von CPUs ausrichten, können Sie die Latenz verringern und sicherstellen, dass verwandte Prozesse innerhalb desselben NUMA-Knotens ausgeführt werden.

Der Gesamtprozess zum Konfigurieren von Soft-NUMA und CPU-Affinität zur Unterstützung von R-Workloads lautet wie folgt:

1. Soft-NUMA aktivieren, falls verfügbar
2. Prozessoraffinität definieren
3. Ressourcenpools für externe Prozesse mit [Resource Governor](../administration/resource-governor.md) erstellen
4. Die [Workloadgruppen](../../relational-databases/resource-governor/resource-governor-workload-group.md) bestimmten Affinitätsgruppen zuweisen

Weitere Informationen einschließlich Beispielcode finden Sie in diesem Tutorial: [Tipps und Tricks für die SQL-Optimierung (Ke Huang)](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**Andere Ressourcen:**

+ [Soft-NUMA in SQL Server](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)
    
    Gewusst wie: Zuordnen von Soft-NUMA-Knoten zu den CPUs

## <a name="task-specific-optimizations"></a>Aufgabenspezifische Optimierungen

In diesem Abschnitt werden Methoden zusammengefasst, die in diesen Fallstudien und in anderen Tests zum Optimieren bestimmter Machine Learning-Workloads übernommen wurden. Zu den gängigen Workloads gehören Modelltraining, Featureextraktion und Featureentwicklung sowie verschiedene Szenarien für die Bewertung: einzeilig, kleiner und großer Batch.

### <a name="feature-engineering"></a>Featureentwicklung

Ein Problem bei R ist die übliche Verarbeitung auf einer einzelnen CPU. Dies ist für viele Aufgaben, insbesondere für die Featureentwicklung, ein gravierender Leistungsengpass. In der Lösung zum Abgleich von Lebensläufen erstellte allein die Featureentwicklungsaufgabe 2.500 produktübergreifende Features, die mit den ursprünglichen 100 Features kombiniert werden mussten. Diese Aufgabe würde viel Zeit in Anspruch nehmen, wenn alles auf einer einzelnen CPU ausgeführt würde.

Es gibt mehrere Möglichkeiten, die Leistung der Featureentwicklung zu verbessern. Sie können entweder den R-Code optimieren und die Featureextraktion im Modellierungsprozess beibehalten oder den Featureentwicklungsprozess in SQL verschieben.

- Verwenden von R. Sie definieren eine Funktion und übergeben sie dann während des Trainings als Argument an [rxTransform](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxtransform). Wenn das Modell die parallele Verarbeitung unterstützt, kann die Featureentwicklungsaufgabe mithilfe mehrerer CPUs verarbeitet werden. Bei diesem Ansatz hat das Data Science-Team eine Leistungsverbesserung von 16 % bei der Bewertungszeit beobachtet. Dieser Ansatz erfordert jedoch ein Modell, das die Parallelisierung und eine Abfrage unterstützt, die mit einem parallelen Plan ausgeführt werden kann.

- Verwenden von R mit einem SQL-Computekontext. In einer Multiprozessorumgebung mit isolierten Ressourcen, die für die Ausführung separater Batches verfügbar sind, können Sie eine höhere Effizienz erzielen, indem Sie die für die einzelnen Batches verwendeten SQL-Abfragen isolieren, Daten aus Tabellen extrahieren und die Daten auf dieselbe Workloadgruppe beschränken. Zu den zum Isolieren der Batches verwendeten Methoden zählen die Partitionierung und die Verwendung von PowerShell, um separate Abfragen parallel auszuführen.

- Parallele Ad-hoc-Ausführung: In einem SQL Server-Computekontext können Sie sich darauf verlassen, dass die SQL-Datenbank-Engine die parallele Ausführung erzwingt, wenn dies möglich ist und diese Option als effizienter eingeschätzt wird.

- Verwenden von T-SQL in einem separaten Featurebereitstellungprozess. Das Vorabberechnen der Featuredaten mit SQL ist im Allgemeinen schneller.

### <a name="prediction-scoring-in-parallel"></a>Parallele Vorhersage (Bewertung)

Einer der Vorteile von SQL Server ist die Möglichkeit, eine große Anzahl von Zeilen parallel zu verarbeiten. Nirgendwo ist dieser Vorteil so markant wie in der Bewertung. Im Allgemeinen benötigt das Modell für die Bewertung keinen Zugriff auf alle Daten, sodass Sie die Eingabedaten so partitionieren können, dass jede Workloadgruppe eine Aufgabe verarbeitet.

Sie können die Eingabedaten auch als einzelne Abfrage senden, sodass SQL Server dann die Abfrage analysiert. Wenn ein paralleler Abfrageplan für die Eingabedaten erstellt werden kann, werden den Knoten automatisch Partitionsdaten zugewiesen und auch parallel die erforderlichen Verknüpfungen und Aggregationen durchgeführt.

Wenn Sie an den Details zum Definieren einer gespeicherten Prozedur für die Bewertung interessiert sind, sehen Sie sich das Beispielprojekt auf [GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips/SQLR) an, und suchen Sie nach der Datei „step5_score_for_matching.sql“. Das Beispielskript verfolgt auch die Start- und Endzeit der Abfrage nach und schreibt die Zeit in die SQL-Konsole, sodass Sie die Leistung bewerten können.

### <a name="concurrent-scoring-using-resource-groups"></a>Gleichzeitige Bewertung mithilfe von Ressourcengruppen

Um das Bewertungsproblem hochzuskalieren, empfiehlt es sich, den Zuordnen/Reduzieren-Ansatz zu übernehmen, bei dem Millionen von Elementen in mehrere Batches aufgeteilt werden. Anschließend werden mehrere Bewertungsaufträge gleichzeitig ausgeführt. In diesem Framework werden die Batches in verschiedenen CPU-Gruppen verarbeitet, und die Ergebnisse werden gesammelt und in die Datenbank zurückgeschrieben.

Dieser Ansatz wird im Szenario zum Abgleich von Lebensläufen verwendet. Die Ressourcenkontrolle in SQL Server ist jedoch für die Implementierung dieses Ansatzes von entscheidender Bedeutung. Durch das Einrichten von Workloadgruppen für Aufträge externer Skripts können Sie R-Bewertungsaufträge an verschiedene Prozessorgruppen weiterleiten und einen schnelleren Durchsatz erreichen.

Die Ressourcenkontrolle kann auch die Aufteilung der verfügbaren Ressourcen auf dem Server (CPU und Arbeitsspeicher) zur Minimierung der Konkurrenz der einzelnen Workloads erleichtern. Sie können Klassifizierungsfunktionen einrichten, um zwischen verschiedenen Typen von R-Aufträgen zu unterscheiden: Sie können beispielsweise entscheiden, dass die von einer Anwendung aufgerufene Bewertung immer Priorität hat, während Aufträge zum erneuten Trainieren eine niedrige Priorität haben. Diese Ressourcenisolation kann die Ausführungszeit potenziell verkürzen und eine besser vorhersagbare Leistung bieten.

### <a name="concurrent-scoring-using-powershell"></a>Gleichzeitige Bewertung mit PowerShell

Wenn Sie sich entscheiden, die Daten selbst zu partitionieren, können Sie PowerShell-Skripts verwenden, um mehrere gleichzeitige Bewertungsaufgaben auszuführen. Verwenden Sie hierzu das Invoke-SqlCmd-Cmdlet, und initiieren Sie die Bewertungsaufgaben parallel.

Im Szenario zum Abgleich von Lebensläufen wurde die Parallelität wie folgt entworfen:

- 20 Prozessoren sind in vier Gruppen mit jeweils fünf CPUs unterteilt. Jede Gruppe von CPUs befindet sich im selben NUMA-Knoten.

- Die maximale Anzahl gleichzeitig auszuführender Batches wurde auf acht gesetzt.

- Jede Workloadgruppe muss zwei Bewertungsaufgaben verarbeiten. Sobald eine Aufgabe das Lesen von Daten abgeschlossen hat und die Bewertung beginnt, kann die andere Aufgabe mit dem Lesen von Daten aus der Datenbank beginnen.

Um die PowerShell-Skripts für dieses Szenario anzuzeigen, öffnen Sie die Datei „experiment.ps1“ im [GitHub-Projekt](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips).

### <a name="storing-models-for-prediction"></a>Speichern von Modellen für die Vorhersage

Wenn Training und Auswertung abgeschlossen sind und Sie das beste Modell ausgewählt haben, sollten Sie das Modell in der Datenbank speichern, damit es für Vorhersagen verfügbar ist. Das Laden des vorab berechneten Modells aus der Datenbank für die Vorhersage ist effizient, da SQL Server Machine Learning besondere Serialisierungsalgorithmen zum Speichern und Laden von Modellen beim Wechsel zwischen R und der Datenbank verwendet.

> [!TIP]
> In SQL Server 2017 können Sie die PREDICT-Funktion verwenden, um die Bewertung selbst dann auszuführen, wenn R nicht auf dem Server installiert ist. Eingeschränkte Modelltypen werden vom RevoScaleR-Paket unterstützt.

Abhängig vom verwendeten Algorithmus können einige Modelle jedoch sehr groß sein, insbesondere, wenn sie mit einem großen Dataset trainiert werden. Beispielsweise generieren Algorithmen wie **lm** oder **glm** viele Zusammenfassungsdaten zusammen mit Regeln. Da die Größe eines Modells eingeschränkt ist, das in einer varbinary-Spalte gespeichert werden kann, sollten Sie unnötige Artefakte aus dem Modell entfernen, bevor das Modell in der Datenbank für die Produktion gespeichert wird.

## <a name="articles-in-this-series"></a>Artikel in dieser Reihe

[Leistungsoptimierung für R – Einführung](../r/sql-server-r-services-performance-tuning.md)

[Leistungsoptimierung für R – SQL Server-Konfiguration](../r/sql-server-configuration-r-services.md)

[Leistungsoptimierung für R – R-Code und Datenoptimierung](../r/r-and-data-optimization-r-services.md)

[Leistungsoptimierung – Ergebnisse der Fallstudie](../r/performance-case-study-r-services.md)
