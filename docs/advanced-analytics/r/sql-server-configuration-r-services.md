---
title: SQL Server-Konfiguration (R Services)
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: feb59ac529b0a66603d9e8b901e9755588ac0379
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344849"
---
# <a name="sql-server-configuration-for-use-with-r"></a>SQL Server Konfiguration für die Verwendung mit R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist der zweite in einer Reihe, in der die Leistungsoptimierung für R Services basierend auf zwei Fallstudien beschrieben wird.  Dieser Artikel enthält Anleitungen zur Hardware-und Netzwerkkonfiguration des Computers, der zum Ausführen von SQL Server R Services verwendet wird. Außerdem enthält es Informationen zu Methoden zum Konfigurieren der SQL Server Instanz, der Datenbank oder der Tabellen, die in einer Lösung verwendet werden. Da die Verwendung von NUMA in SQL Server die Linie zwischen Hardware-und Daten Bank Optimierungen wiederholt, werden in einem dritten Abschnitt die CPU-affininitialisierung und die Ressourcenkontrolle ausführlich erläutert.

> [!TIP]
> Wenn Sie noch nicht mit SQL Server vertraut sind, wird dringend empfohlen, dass Sie auch das Handbuch für die SQL Server Leistungsoptimierung lesen: [Überwachen und optimieren](https://docs.microsoft.com/sql/relational-databases/performance/monitor-and-tune-for-performance)Sie die Leistung.

## <a name="hardware-optimization"></a>Hardware Optimierung

Die Optimierung des Server Computers ist wichtig, um sicherzustellen, dass Sie über die Ressourcen zum Ausführen externer Skripts verfügen. Wenn Ressourcen eingeschränkt sind, werden möglicherweise folgende Symptome angezeigt:

- Die Auftragsausführung wurde verzögert oder abgebrochen, um andere Daten Bank Vorgänge zu priorisieren.
- Fehler "Kontingent Überschreitung" bewirkt, dass das R-Skript ohne Abschluss beendet wird
- In den R-Speicher geladene Daten werden für unvollständige Ergebnisse gekürzt

### <a name="memory"></a>Speicher

Der auf einem Computer verfügbare Arbeitsspeicher kann sich stark auf die Leistung komplexerer analytischer Algorithmen auswirken. Nicht genügend Arbeitsspeicher kann den Grad der Parallelität beeinflussen, wenn der SQL-computekontext verwendet wird. Ebenso kann dadurch die verarbeitbare Segmentgröße (Zeilen pro Lesevorgang) beeinträchtigt werden sowie die Anzahl gleichzeitiger Sitzungen, die unterstützt werden kann.

Mindestens 32 GB werden dringend empfohlen. Wenn mehr als 32 GB verfügbar sind, können Sie die SQL-Datenquelle so konfigurieren, dass bei jedem Lesevorgang mehr Zeilen verwendet werden, um die Leistung zu verbessern.

Sie können auch den von der-Instanz verwendeten Arbeitsspeicher verwalten. Standardmäßig wird SQL Server bei externen Skript Prozessen priorisiert, wenn Arbeitsspeicher zugewiesen wird. In einer Standardinstallation von r Services werden r nur 20% des verfügbaren Arbeitsspeichers zugeordnet.

Dies ist in der Regel nicht ausreichend für Data Science Tasks, aber weder möchten Sie den SQL Server-Speicher beeinträchtigen. Sie sollten experimentieren und die Speicher Belegung zwischen der Datenbank-Engine, den zugehörigen Diensten und externen Skripts optimieren, um zu verstehen, dass die optimale Konfiguration groß-und Kleinschreibung unterscheidet.

Für das Modell zum Fortsetzen des Ablaufs war die externe Skript Verwendung sehr umfangreicher, und es wurden keine anderen Datenbank-Engine-Dienste ausgeführt. Daher wurden Ressourcen, die externen Skripts zugeordnet sind, auf 70% erweitert. Dies war die beste Konfiguration für die Skript Leistung.

### <a name="power-options"></a>Energieoptionen

Unter dem Windows-Betriebssystem sollte die Option **hohe Leistungsfähigkeit** verwendet werden. Die Verwendung einer anderen Energie Einstellung führt bei Verwendung SQL Server zu einer verringerten oder inkonsistenten Leistung.

### <a name="disk-io"></a>Eingabe bzw. Ausgabe von Laufwerken

Trainings-und Vorhersage Aufträge mithilfe von R Services sind grundsätzlich e/a-gebunden und hängen von der Geschwindigkeit der Datenträger ab, auf denen die Datenbank gespeichert ist. Schnellere Laufwerke, wie z. b. Solid-State-Laufwerke (SSD), sind möglicherweise hilfreich.

Die Laufwerk-E/A hängt auch von anderen Anwendungen ab, die auf das Laufwerk zugreifen: z.B. von Lesevorgängen in einer Datenbank anderer Clients. Die E/A-Leistung des Laufwerks kann auch von den Einstellungen für das verwendete Dateisystem beeinträchtigt werden, wie z.B. von der vom Dateisystem verwendeten Blockgröße.

Wenn mehrere Laufwerke verfügbar sind, speichern Sie die Datenbanken auf einem anderen Laufwerk als SQL Server, damit Anforderungen für die Datenbank-Engine nicht denselben Datenträger wie Anforderungen für Daten, die in der Datenbank gespeichert sind, erreichen.

Die Laufwerk-E/A kann die Leistung deutlich beeinträchtigen, wenn analytische RevoScaleR-Funktionen ausgeführt werden, die während des Trainings mehrere Iterationen verwenden. Beispielsweise `rxLogit`verwenden, `rxDTree`, `rxDForest`und `rxBTrees` mehrere Iterationen. Wenn die Datenquelle SQL Server ist, verwenden diese Algorithmen temporäre Dateien, die zum Erfassen der Daten optimiert sind. Diese Dateien werden nach dem Abschluss der Sitzung automatisch bereinigt. Ein Hochleistungs Datenträger für Lese-/Schreibvorgänge kann die insgesamt verstrichene Zeit für diese Algorithmen erheblich verbessern.

> [!NOTE]
> Frühe Versionen von R Services erforderten die Unterstützung von 8,3-Dateinamen auf Windows-Betriebssystemen. Diese Einschränkung wurde nach Service Pack 1 aufgehoben. Sie können jedoch fsutil. exe verwenden, um zu bestimmen, ob ein Laufwerk 8,3-Dateinamen unterstützt, oder um Unterstützung zu aktivieren, wenn dies nicht der Fall ist.

### <a name="paging-file"></a>Auslagerungs Datei

Das Windows-Betriebssystem verwendet eine Auslagerungsdatei, um Abstürze zu verwalten und virtuelle Arbeitsspeicherseiten zu speichern. Wenn Sie eine exzessive Auslagerung bemerken, ziehen Sie in Betracht, den physischen Arbeitsspeicher des Computers zu erweitern. Auch wenn mehr physischer Arbeitsspeicher die Auslagerung nicht vollständig eliminiert, wird der Auslagerungsbedarf doch gesenkt.

Auch die Geschwindigkeit des Laufwerks, auf dem die Auslagerungsdatei gespeichert ist, kann die Leistung beeinträchtigen. Wenn Sie die Auslagerungsdatei auf einem SSD speichern oder mehrere Auslagerungsdateien SSD-übergreifend verwenden, kann dies die Leistung verbessern.

Informationen zum Anpassen der Größe der Auslagerungs Datei finden [Sie unter Bestimmen der geeigneten Auslagerungs Dateigröße für 64-Bit-Versionen von Windows](https://support.microsoft.com/kb/2860880).

## <a name="optimizations-at-instance-or-database-level"></a>Optimierungen auf Instanz-oder Datenbankebene

Die Optimierung der SQL Server Instanz ist der Schlüssel für die effiziente Ausführung externer Skripts.

> [!NOTE]
> Die optimalen Einstellungen unterscheiden sich abhängig von der Größe und dem Typ der Daten, der Anzahl von Spalten, die Sie für die Bewertung oder das Trainieren eines Modells verwenden.
> 
> Sie können die Ergebnisse spezifischer Optimierungen im letzten Artikel überprüfen: [Leistungsoptimierung: Ergebnisse der Fallstudie](../../advanced-analytics/r/performance-case-study-r-services.md)
> 
> Beispiel Skripts finden Sie im separaten [GitHub-Repository](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning).

### <a name="table-compression"></a>Tabellenkomprimierung

Die e/a-Leistung kann häufig durch Komprimierung oder einen Spalten basierten Datenspeicher verbessert werden. Im Allgemeinen werden Daten häufig in mehreren Spalten innerhalb einer Tabelle wiederholt, sodass die Verwendung eines columnstore-diese Wiederholungen beim Komprimieren der Daten nutzt.

Ein columnstore-ist möglicherweise nicht so effizient, wenn es zahlreiche Einfügungen in die Tabelle gibt, ist aber eine gute Wahl, wenn die Daten statisch sind oder nur selten geändert werden. Wenn sich ein spaltenbasierter Speicher nicht eignet, können Sie die E/A verbessern, indem Sie die Komprimierung in einer überwiegend zeilenorientierten Tabelle aktivieren.

Weitere Informationen finden Sie in folgenden Dokumenten:

+ [Datenkomprimierung](../../relational-databases/data-compression/data-compression.md)

+ [Aktivieren der Komprimierung für eine Tabelle oder einen Index](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [Columnstore-Indizes: Übersicht](../../relational-databases/indexes/columnstore-indexes-overview.md)

### <a name="memory-optimized-tables"></a>Speicheroptimierte Tabellen

Heutzutage ist der Arbeitsspeicher für moderne Computer nicht mehr problematisch. Da Hardware Spezifikationen weiterhin verbessern, ist es relativ einfach, RAM mit guten Werten zu erzielen. Gleichzeitig werden Daten jedoch schneller als je zuvor erstellt, und die Daten müssen mit geringer Latenz verarbeitet werden.

Speicher optimierte Tabellen stellen eine Lösung dar, da Sie den großen Arbeitsspeicher nutzen, der auf den erweiterten Computern verfügbar ist, um das Problem der Big Data zu beheben. Speicher optimierte Tabellen befinden sich hauptsächlich im Arbeitsspeicher, sodass Daten aus dem Arbeitsspeicher gelesen und in diesen geschrieben werden. Bei Dauerhaftigkeit wird eine zweite Kopie der Tabelle auf dem Datenträger beibehalten, und die Daten werden nur während der Daten Bank Wiederherstellung vom Datenträger gelesen.

Wenn Sie häufig Lese-und Schreibzugriff auf Tabellen benötigen, können Speicher optimierte Tabellen bei hoher Skalierbarkeit und geringer Latenz helfen.  Im Szenario zum Fortsetzen des Abgleich Vorgangs konnten wir mit Speicher optimierten Tabellen alle Fortsetzungs Features aus der Datenbank lesen und im Hauptspeicher speichern, damit Sie mit neuen Auftrags Öffnungen übereinstimmen. Die Datenträger-e/a wurde erheblich reduziert

Zusätzliche Leistungssteigerungen wurden erzielt, indem eine Speicher optimierte Tabelle beim Schreiben von Vorhersagen aus mehreren gleichzeitigen Batches in die Datenbank zurückgeschrieben wurde. Die Verwendung Speicher optimierter Tabellen auf SQL Server aktivierte Lese-und Schreibvorgänge für Tabellen mit geringer Latenzzeit.

Die Darstellung war während der Entwicklung ebenfalls nahtlos. Dauerhafte Speicher optimierte Tabellen wurden zur gleichen Zeit erstellt, als die Datenbank erstellt wurde. Daher hat die Entwicklung denselben Workflow verwendet, unabhängig davon, wo die Daten gespeichert wurden.

### <a name="processor"></a>Prozessor

SQL Server können Aufgaben parallel ausführen, indem Sie die verfügbaren Kerne auf dem Computer verwenden. welche weiteren Kerne verfügbar sind, desto besser ist die Leistung. Das Erhöhen der Anzahl von Kernen ist möglicherweise nicht für e/a-gebundene Vorgänge hilfreich, CPU-gebundene Algorithmen profitieren jedoch von schnelleren CPUs mit vielen Kernen.

Da der Server normalerweise von mehreren Benutzern gleichzeitig verwendet wird, muss der Datenbankadministrator die ideale Anzahl von Kernen ermitteln, die zur Unterstützung von Spitzen workloadberechnungen benötigt werden.

### <a name="resource-governance"></a>Ressourcenkontrolle

In-Editionen, die Resource Governor unterstützen, können Sie mithilfe von Ressourcenpools angeben, dass bestimmten Arbeits Auslastungen eine bestimmte Anzahl von CPUs zugeordnet werden. Sie können auch die Menge an Arbeitsspeicher verwalten, die bestimmten Arbeits Auslastungen zugeordnet ist.

Mithilfe der Ressourcenkontrolle in SQL Server können Sie die Überwachung und Steuerung der verschiedenen Ressourcen, die von SQL Server und R verwendet werden, zentralisieren. Beispielsweise können Sie die Hälfte des verfügbaren Arbeitsspeichers für die Datenbank-Engine zuordnen, um sicherzustellen, dass die Kerndienste trotz vorübergehender Workloads immer ausgeführt werden können.

Der Standardwert für die Arbeitsspeicher Nutzung durch externe Skripts ist auf 20% des gesamten Arbeitsspeichers beschränkt, der für die SQL Server selbst verfügbar ist. Diese Beschränkung wird standardmäßig angewendet, um sicherzustellen, dass alle Tasks, die auf dem Datenbankserver basieren, nicht schwerwiegend von R-Aufträgen mit langer Laufzeit betroffen sind. Diese Einschränkungen können vom Datenbankadministrator angepasst werden. In vielen Fällen ist das Limit von 20% nicht ausreichend, um schwerwiegende Machine Learning-Workloads zu unterstützen.

Die unterstützten Konfigurationsoptionen sind **MAX_CPU_PERCENT**, **MAX_MEMORY_PERCENT**und **MAX_PROCESSES**. Verwenden Sie diese Anweisung, um die aktuellen Einstellungen anzuzeigen:`SELECT * FROM sys.resource_governor_external_resource_pools`

-  Wenn der Server hauptsächlich für R Services verwendet wird, ist es möglicherweise hilfreich, MAX_CPU_PERCENT auf 40% oder 60% zu erhöhen.

-  Wenn viele R-Sitzungen denselben Server gleichzeitig verwenden müssen, sollten alle drei Einstellungen erweitert werden.

Verwenden Sie T-SQL-Anweisungen, um die zugeordneten Ressourcen Werte zu ändern.

+ Diese Anweisung legt die Speicherauslastung auf 40% fest:`ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_MEMORY_PERCENT = 40)`

+ Mit dieser Anweisung werden alle drei konfigurierbaren Werte festgelegt:`ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_CPU_PERCENT = 40, MAX_MEMORY_PERCENT = 50, MAX_PROCESSES = 20)`

+ Wenn Sie eine Arbeitsspeicher-, CPU-oder Max-Prozess Einstellung ändern und die Einstellungen dann sofort anwenden möchten, führen Sie die folgende Anweisung aus:`ALTER RESOURCE GOVERNOR RECONFIGURE`

## <a name="soft-numa-hardware-numa-and-cpu-affinity"></a>Soft-NUMA, Hardware-NUMA und CPU-Affinität

Wenn Sie SQL Server als computekontext verwenden, können Sie mitunter eine bessere Leistung erzielen, indem Sie Einstellungen im Zusammenhang mit NUMA und Prozessor Affinität optimieren. 

Systeme mit _Hardware-NUMA_ verfügen über mehr als einen Systembus, von denen jeder eine kleine Gruppe von Prozessoren bedient. Jede CPU kann auf eine kohärente Weise auf Arbeitsspeicher zugreifen, der anderen Gruppen zugeordnet ist. Jede dieser Gruppen stellt einen NUMA-Knoten dar. Wenn Sie über NUMA-Hardware verfügen, können Sie sie ggf. so konfigurieren, dass anstelle von NUMA Interleave-Speicher verwendet wird. In diesem Fall wird Windows und somit SQL Server nicht als NUMA erkannt. 

Sie können die folgende Abfrage ausführen, um die Anzahl der für SQL Server verfügbaren Speicher Knoten zu ermitteln:

```sql
SELECT DISTINCT memory_node_id
FROM sys.dm_os_memory_clerks
```

Wenn die Abfrage einen einzelnen Speicher Knoten (Knoten 0) zurückgibt, verfügen Sie entweder nicht über eine Hardware-NUMA, oder die Hardware ist als verschachtelt (Non-NUMA) konfiguriert. SQL Server ignoriert auch Hardware-NUMA, wenn vier oder weniger CPUs vorhanden sind, oder wenn mindestens ein Knoten nur über eine CPU verfügt.

Wenn Ihr Computer über mehrere Prozessoren verfügt, jedoch nicht über Hardware-NUMA verfügt, können Sie auch [Soft-NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server) verwenden, um CPUs in kleinere Gruppen zu unterteilen.  In SQL Server 2016 und SQL Server 2017 wird das Soft-NUMA-Feature beim Starten des SQL Server Dienstanbieter automatisch aktiviert.

Wenn Soft-NUMA aktiviert ist, werden die Knoten von SQL Server automatisch verwaltet. Um jedoch für bestimmte Arbeits Auslastungen zu optimieren, können Sie die _Weiche Affinität_ deaktivieren und die CPU-Affinität für die Soft-NUMA-Knoten manuell konfigurieren. Dadurch können Sie besser steuern, welche Arbeits Auslastungen welchen Knoten zugewiesen werden, insbesondere, wenn Sie eine Edition von SQL Server verwenden, die die Ressourcenkontrolle unterstützt. Indem Sie die CPU-Affinität angeben und Ressourcenpools mit Gruppen von CPUs ausrichten, können Sie die Latenzzeit verringern und sicherstellen, dass verwandte Prozesse innerhalb desselben NUMA-Knotens ausgeführt werden.

Der Gesamtprozess zum Konfigurieren von Soft-NUMA und CPU-Affinität zur Unterstützung von R-Arbeits Auslastungen lautet wie folgt:

1. Soft-NUMA aktivieren, falls verfügbar
2. Definieren der Prozessor Affinität
3. Erstellen von Ressourcenpools für externe Prozesse mithilfe von [Resource Governor](../r/resource-governance-for-r-services.md)
4. Zuweisen der [Arbeits](../../relational-databases/resource-governor/resource-governor-workload-group.md) Auslastungs Gruppen zu bestimmten Affinitätsgruppen

Weitere Informationen, einschließlich Beispielcode, finden Sie in diesem Tutorial: [Tipps und Tricks zur SQL-Optimierung (KE Huang)](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**Weitere Ressourcen:**

+ [Soft-NUMA in SQL Server](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)
    
    Zuordnen von Soft-NUMA-Knoten zu CPUs

## <a name="task-specific-optimizations"></a>Aufgabenspezifische Optimierungen

In diesem Abschnitt werden die Methoden zusammengefasst, die in diesen Fallstudien und in anderen Tests zum Optimieren bestimmter Machine Learning-Workloads übernommen wurden. Zu den gängigen Workloads gehören Modell Schulungen, featureextraktion und Featureentwicklung sowie verschiedene Szenarien für die Bewertung: Einzel Zeilen, kleine Batches und große Batches.

### <a name="feature-engineering"></a>Featureentwicklung

Ein Problem bei R ist, dass es in der Regel auf einer einzelnen CPU verarbeitet wird. Dies ist ein wichtiger Leistungsengpass für viele Aufgaben, insbesondere für die Featureentwicklung. In der Projekt Mappe zum Fortsetzen des Ablaufs erstellte der Feature Engineering-Task allein 2.500-Produkt übergreifende Features, die mit den ursprünglichen 100-Features kombiniert werden mussten. Diese Aufgabe würde eine beträchtliche Zeit in Anspruch nehmen, wenn alles auf einer einzelnen CPU ausgeführt wird.

Es gibt mehrere Möglichkeiten, die Leistung der Featureentwicklung zu verbessern. Sie können den R-Code optimieren und die featureextraktion im Modellierungsprozess beibehalten oder den featureentwicklungsprozess in SQL verschieben.

- Verwenden von R. Sie definieren eine Funktion und übergeben Sie während des Trainings als Argument an [rxtransform](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxtransform) . Wenn das Modell die parallele Verarbeitung unterstützt, kann der featureentwicklungstask mithilfe mehrerer CPUs verarbeitet werden. Bei dieser Vorgehensweise hat das Data Science Team eine Leistungsverbesserung von 16% in Bezug auf die Bewertungszeit beobachtet. Dieser Ansatz erfordert jedoch ein Modell, das die Parallelisierung und eine Abfrage unterstützt, die mit einem parallelen Plan ausgeführt werden kann.

- Verwenden Sie R mit einem SQL-computekontext. In einer Multiprozessorumgebung mit isolierten Ressourcen, die für die Ausführung separater Batches verfügbar sind, können Sie eine höhere Effizienz erzielen, indem Sie die für die einzelnen Batches verwendeten SQL-Abfragen isolieren, Daten aus Tabellen extrahieren und die Daten in derselben Arbeits Auslastungs Gruppe einschränken. Zu den zum Isolieren der Batches verwendeten Methoden zählen die Partitionierung und die Verwendung von PowerShell, um separate Abfragen parallel auszuführen.

- Ad-hoc-parallele Ausführung: In einem SQL Server computekontext können Sie sich auf die SQL-Datenbank-Engine verlassen, um die parallele Ausführung zu erzwingen, wenn dies möglich ist, und wenn diese Option effizienter ist.

- Verwenden Sie T-SQL in einem separaten featureprozess. Das vorberechnen der Featuredaten mithilfe von SQL ist im Allgemeinen schneller.

### <a name="prediction-scoring-in-parallel"></a>Vorhersage (Bewertung) parallel

Einer der Vorteile von SQL Server ist die Möglichkeit, eine große Anzahl von Zeilen parallel zu verarbeiten. Im folgenden ist dieser Vorteil als in der Bewertung gekennzeichnet. Im allgemeinen benötigt das Modell keinen Zugriff auf alle Daten für die Bewertung, sodass Sie die Eingabedaten partitionieren können, wobei jede Arbeits Auslastungs Gruppe eine Aufgabe verarbeitet.

Sie können die Eingabedaten auch als einzelne Abfrage senden und SQL Server dann die Abfrage analysieren. Wenn ein paralleler Abfrageplan für die Eingabedaten erstellt werden kann, werden automatisch die den Knoten zugewiesenen Daten partitioniert und auch die erforderlichen Joins und Aggregationen parallel durchgeführt.

Wenn Sie an den Details zum Definieren einer gespeicherten Prozedur für die Bewertung interessiert sind, sehen Sie sich das Beispiel Projekt auf [GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips/SQLR) an, und suchen Sie nach der Datei "step5_score_for_matching. SQL". Das Beispielskript verfolgt auch die Start-und Endzeit der Abfrage nach und schreibt die Zeit in die SQL-Konsole, sodass Sie die Leistung bewerten können.

### <a name="concurrent-scoring-using-resource-groups"></a>Gleichzeitige Bewertung mithilfe von Ressourcengruppen

Um das Bewertungs Problem zentral hochzuskalieren, empfiehlt es sich, den Map-Reduce-Ansatz zu übernehmen, bei dem Millionen von Elementen in mehrere Batches aufgeteilt werden. Anschließend werden mehrere Bewertungs Aufträge gleichzeitig ausgeführt. In diesem Framework werden die Batches in verschiedenen CPU-Sätzen verarbeitet, und die Ergebnisse werden gesammelt und zurück in die Datenbank geschrieben.

Dies ist der Ansatz, der im Szenario zum Fortsetzen des Ablaufs verwendet wird. die Ressourcenkontrolle in SQL Server ist jedoch für die Implementierung dieses Ansatzes von entscheidender Bedeutung. Durch das Einrichten von Arbeits Auslastungs Gruppen für externe Skript Aufträge können Sie R-Bewertungs Aufträge an verschiedene Prozessor Gruppen weiterleiten und einen schnelleren Durchsatz erreichen.

Mithilfe der Ressourcenkontrolle können auch die verfügbaren Ressourcen auf dem Server (CPU und Arbeitsspeicher) aufgeteilt werden, um die workloadkonkurrenz zu minimieren. Sie können Klassifizierungs Funktionen einrichten, um zwischen verschiedenen Typen von R-Aufträgen zu unterscheiden: beispielsweise können Sie entscheiden, dass die Bewertung, die von einer Anwendung aufgerufen wird, immer Priorität hat, während Aufträge zum erneuten trainieren eine niedrige Priorität haben. Diese Ressourcen Isolation kann möglicherweise die Ausführungszeit verbessern und eine vorhersagbare Leistung bereitstellen.

### <a name="concurrent-scoring-using-powershell"></a>Gleichzeitige Bewertung mithilfe von PowerShell

Wenn Sie sich entscheiden, die Daten selbst zu partitionieren, können Sie PowerShell-Skripts verwenden, um mehrere gleichzeitige Bewertungsaufgaben auszuführen. Verwenden Sie hierzu das Cmdlet "Start-sqlcmd", und initiieren Sie die Bewertungsaufgaben parallel.

Im Szenario zum Fortsetzen des Ablaufs wurde die Parallelität wie folgt entworfen:

- 20 Prozessoren sind jeweils in vier Gruppen mit jeweils fünf CPUs unterteilt. Jede Gruppe von CPUs befindet sich im selben NUMA-Knoten.

- Die maximale Anzahl gleichzeitiger Batches wurde auf 8 festgelegt.

- Jede Arbeits Auslastungs Gruppe muss zwei Bewertungsaufgaben verarbeiten. Sobald eine Aufgabe das Lesen von Daten abgeschlossen und die Bewertung beginnt, kann die andere Aufgabe mit dem Lesen von Daten aus der Datenbank beginnen.

Um die PowerShell-Skripts für dieses Szenario anzuzeigen, öffnen Sie die Datei "Experiment. ps1" im [GitHub-Projekt](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips).

### <a name="storing-models-for-prediction"></a>Speichern von Modellen für die Vorhersage

Wenn das Training und die Evaluierung abgeschlossen sind und Sie ein bestes Modell ausgewählt haben, empfiehlt es sich, das Modell in der Datenbank zu speichern, damit es für Vorhersagen verfügbar ist. Das Laden des vorab berechneten Modells aus der Datenbank für die Vorhersage ist effizient, da SQL Server Machine Learning besondere serialisierungsalgorithmen zum Speichern und Laden von Modellen verwendet, wenn Sie zwischen R und der Datenbank wechseln.

> [!TIP]
> In SQL Server 2017 können Sie die Vorhersagefunktion verwenden, um die Bewertung selbst dann auszuführen, wenn R nicht auf dem Server installiert ist. Eingeschränkte Modelltypen werden vom revoscaler-Paket unterstützt.

Abhängig vom verwendeten Algorithmus können einige Modelle jedoch sehr groß sein, insbesondere, wenn Sie mit einem großen Dataset trainiert werden. Beispielsweise generieren Algorithmen, wie z. b. **LM** oder **GLM** , viele Zusammenfassungs Daten zusammen mit Regeln. Da die Größe eines Modells eingeschränkt ist, das in einer varbinary-Spalte gespeichert werden kann, wird empfohlen, unnötige Artefakte aus dem Modell zu entfernen, bevor das Modell in der Datenbank für die Produktion gespeichert wird.

## <a name="articles-in-this-series"></a>Artikel in dieser Reihe

[Leistungsoptimierung für R-Einführung](../r/sql-server-r-services-performance-tuning.md)

[Leistungsoptimierung für R-SQL Server-Konfiguration](../r/sql-server-configuration-r-services.md)

[Leistungsoptimierung für r-r-Code und Daten Optimierung](../r/r-and-data-optimization-r-services.md)

[Leistungsoptimierung: Ergebnisse der Fallstudie](../r/performance-case-study-r-services.md)
