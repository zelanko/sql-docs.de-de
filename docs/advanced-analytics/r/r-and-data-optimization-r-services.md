---
title: Leistung für SQL Server R Services - datenoptimierung | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3fda560aedb7a0e1119a0524ffefe42a476c4aed
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51699508"
---
# <a name="performance-for-r-services---data-optimization"></a>Leistung von R Services - Data-Optimierung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist der dritte einer Artikelreihe, die leistungsoptimierung für R-Dienste, die basierend auf zwei Fallstudien beschreibt. In diesem Artikel wird erläutert, eine leistungsoptimierung für R oder Python-Skripts, die in SQL Server ausgeführt. Darüber hinaus werden die Methoden, die Sie verwenden können, aktualisieren Sie Ihren R-Code sowohl zur Verbesserung der Leistung und zu bekannten Problemen vorbeugen beschrieben.

## <a name="choosing-a-compute-context"></a>Auswählen eines computekontexts

In SQL Server 2016 und 2017 verwenden Sie entweder die **lokalen** oder **SQL** compute Context verwenden, wenn R oder Python-Skript ausführen.

Bei Verwendung der **lokalen** Compute Context wird die Analyse wird ausgeführt, auf dem Computer und nicht auf dem Server. Wenn Sie Daten aus SQL Server für die Verwendung in Ihrem Code angezeigt werden, müssen daher die Daten über das Netzwerk abgerufen werden. Die Leistungseinbußen für diesen Netzwerkübertragung hängen von der Größe der übertragenen Daten, dem Geschwindigkeit des Netzwerks und anderen Netzwerkübertragungen ab, die zur gleichen Zeit auftreten.

Bei Verwendung der **SQL Server-computekontext**, der Code auf dem Server ausgeführt wird. Wenn Sie Daten aus SQL Server erhalten, die Daten lokal auf dem Server, der die Analyse ausgeführt werden sollen, und daher wird kein Netzwerkaufwand eingeführt. Wenn Sie Daten aus anderen Quellen importieren möchten, sollten Sie im Voraus Anordnen von ETL.

Bei der Arbeit mit großen Datenmengen sollten Sie immer den SQL Compute Context verwenden.

## <a name="factors"></a>Faktoren

Die R-Sprache wurde das Konzept der *Faktoren*, die spezielle Variable für kategorische Daten sind. Datenanalysten häufig faktorvariablen in der Formel verwenden, da kategorische Variablen als Faktoren Behandlung die Daten wird sichergestellt, dass ordnungsgemäß vom Machine Learning-Funktionen verarbeitet wird. Weitere Informationen finden Sie unter [R für Anfänger: Faktorvariablen](https://www.dummies.com/programming/r/how-to-look-at-the-structure-of-a-factor-in-r/).

Standardmäßig können faktorvariablen in ganze Zahlen "und" zurück, für das Speichern oder Verarbeiten von Zeichenfolgen konvertiert werden. Die R `data.frame` Funktion als faktorvariablen, alle Zeichenfolgen behandelt, es sei denn, das Argument *StringsAsFactors* nastaven NA hodnotu **"false"**. Das bedeutet, dass Zeichenfolgen, automatisch sind in eine ganze Zahl für die Verarbeitung konvertiert, und dann wieder die ursprüngliche Zeichenfolge zugeordnet.

Wenn die Quelldaten für Faktoren vor, als ganze Zahl gespeichert ist, kann Leistung beeinträchtigt, da es sich bei R die Faktor ganzen Zahlen in Zeichenfolgen konvertiert, zur Laufzeit, und führt dann eine eigene interne Konvertierung der Zeichenfolge zur ganzen Zahl.

Um solche Konvertierungen zur Laufzeit zu vermeiden, können Sie die Werte als ganze Zahlen in der SQL Server-Tabelle zu speichern und mithilfe der _ColInfo_ Argument zum Angeben der Ebenen für die Spalte als Faktor verwendet. Die meisten von Datenquellenobjekten in RevoScaleR übernehmen Sie den Parameter _ColInfo_. Sie können diesen Parameter verwenden, zum Benennen von Variablen, die von der Datenquelle verwendet, geben Sie ihre und definieren die Variablen Ebenen oder Transformationen auf die Werte der Spalte.

Z. B. der folgende Aufruf der R-Funktion ruft die ganzen Zahlen 1, 2 und 3 aus einer Tabelle, jedoch ordnet die Werte in einen Faktor mit "Apple", "Orange" und "Banane".

```R
c("fruit" = c(type = "factor", levels=as.character(c(1:3)), newLevels=c("apple", "orange", "banana")))
```

Wenn die Quellspalte Zeichenfolgen enthält, es ist immer mehr effizienten zum Angeben der Ebenen vor der Nutzung der _ColInfo_ Parameter. Die folgende R-Code behandelt z. B. die Zeichenfolgen als Faktoren, wie sie gelesen werden.

```R
c("fruit" = c(type = "factor", levels= c("apple", "orange", "banana")))
```

Ist kein semantischer Unterschied bei der modellgenerierung, kann der zweite Ansatz zu verbesserter Leistung führen.

## <a name="data-transformations"></a>Datentransformationen

Datenanalysten verwenden häufig Transformationsfunktionen, die als Teil der Analyse in R geschrieben werden. Die Transformationsfunktion gilt für jede Zeile aus der Tabelle abgerufen. In SQL Server werden diese Transformationen angewendet, auf alle Zeilen abgerufen, die in einem Batch, der Kommunikation zwischen R-Interpreter und die Engine für Datenanalyse erforderlich ist. Zum Ausführen der Umwandlungen werden die Daten von SQL an die Datenanalyse-Engine und dann an den Prozess der R-Interpreter verschoben und zurück.

Aus diesem Grund kann mithilfe von Transformationen als Teil des R-Codes eine erhebliche negative Auswirkung auf die Leistung des Algorithmus, abhängig von der Menge der betroffenen Daten haben.

Es ist effizienter, alle erforderliche Spalten in der Tabelle oder Sicht, bevor die Analyse durchgeführt haben, und vermeiden Transformationen während der Berechnung. Wenn es nicht möglich ist, zusätzliche Spalten zu vorhandenen Tabellen hinzuzufügen, können Sie eine andere Tabelle oder Ansicht mit den transformierten Spalten erstellen und eine entsprechende Abfrage zum Abrufen der Daten verwenden.

## <a name="batch-row-reads"></a>Batch-Zeile liest.

Bei Verwendung eine SQL Server-Datenquelle (`RxSqlServerData`) in Ihrem Code empfiehlt es sich, dass Sie versuchen, mithilfe des Parameters _RowsPerRead_ Batchgröße angeben. Dieser Parameter definiert die Anzahl der Zeilen, die abgefragt werden, und klicken Sie dann zur Verarbeitung an den externen Skript gesendet. Zur Laufzeit wird der Algorithmus nur die angegebene Anzahl von Zeilen in jedem Batch an.

Die Möglichkeit, die Menge der Daten zu steuern, die gleichzeitig verarbeitet werden können Sie zu lösen oder Probleme zu vermeiden. Wenn Ihre Eingabe-Dataset sehr breit ist z. B. (hat viele Spalten), oder wenn der Dataset wenigen große Spalten (z. B. Freitext) verfügt, können Sie reduzieren die Batchgröße, um Paging von Daten aus dem Arbeitsspeicher zu vermeiden.

Standardmäßig ist der Wert dieses Parameters auf 50000 festgelegt, um sicherzustellen, dass zufriedenstellende Leistung auch auf Computern mit wenig Arbeitsspeicher. Wenn der Server über genügend Speicherplatz verfügt, kann eine bessere Leistung, insbesondere bei großen Tabellen durch Erhöhen dieses Wertes auf 500.000 oder selbst auf eine Million erzielt werden.

Die Vorteile der höhere Batchgröße werden offensichtlich auf einem großen Dataset und in eine Aufgabe, die auf mehrere Prozesse ausgeführt werden kann. Allerdings ist durch Erhöhen dieses Wertes nicht immer die besten Ergebnisse erzielen. Es wird empfohlen, dass Sie sich mit Ihren Daten und den Algorithmus, um den optimalen Wert zu experimentieren.

## <a name="parallel-processing"></a>parallele Verarbeitung

Zur Verbesserung der Leistung von **Rx** Analysefunktionen, Sie können die Fähigkeit von SQL Server zum Ausführen von Tasks gleichzeitig mit der verfügbaren Kerne auf dem Servercomputer nutzen.

Es gibt zwei Möglichkeiten zum Erreichen der Parallelisierung mit R in SQL Server:

-   **Verwendung \@parallel.** Bei Verwendung der `sp_execute_external_script` gespeicherten Prozedur zur Ausführung eines R-Skripts legen Sie den `@parallel`-Parameter auf `1` fest. Dies ist die beste Methode, wenn Ihr R-Skript ist **nicht** verwenden der RevoScaleR-Funktionen, die andere Mechanismen für die Verarbeitung aufweisen. Wenn Ihr Skript RevoScaleR-Funktionen, die (in der Regel mit dem Präfix "Rx") verwendet, paralleler Verarbeitung wird automatisch ausgeführt, und Sie nicht explizit festgelegt müssen `@parallel` zu `1`.

    Wenn das R-Skript parallelisiert werden kann, und die SQL-Abfrage parallelisiert werden kann, wird die Datenbank-Engine mehrere parallele Prozesse erstellt. Die maximale Anzahl von Prozessen, die erstellt werden können, ist gleich der **Max. Grad an Parallelität** (MAXDOP) die Einstellung für die Instanz. Alle Prozesse klicken Sie dann das gleiche Skript ausführen, erhalten aber nur einen Teil der Daten.
    
    Diese Methode ist daher nicht nützlich für Skripts, die alle Daten, z. B. wenn sehen, müssen das Trainieren eines Modells. Es ist jedoch nützlich, wenn Tasks wie die Batchvorhersage parallel ausgeführt werden. Weitere Informationen zur Verwendung von Parallelität mit `sp_execute_external_script`, finden Sie unter der **Tipps für Fortgeschrittene: parallele Verarbeitung** Teil [mithilfe von R-Code in Transact-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).

-   **Verwenden Sie NumTasks = 1.** Bei Verwendung **Rx** Funktionen in einem SQL Server-rechenkontext, legen Sie den Wert, der die _NumTasks_ Parameter, um die Anzahl der Prozesse, die Sie erstellen möchten. Die Anzahl der erstellten Prozesse kann nie mehr als **MAXDOP**jedoch die tatsächliche Anzahl der erstellten Prozesse richtet sich nach der Datenbank-Engine und kleiner als Sie angefordert werden.

    Wenn das R-Skript parallelisiert werden kann, und die SQL-Abfrage parallelisiert werden kann, erstellt SQL Server mehrere parallele Prozesse, wenn die Rx-Funktionen ausgeführt. Die tatsächliche Anzahl der Prozesse, die erstellt werden, hängt von einer Vielzahl von Faktoren wie z.B. Ressourcenkontrolle, aktuelle Verwendung von Ressourcen, andere Sitzungen und der Abfrageausführungsplan für die Abfrage, die mit R-Skript verwendet ab.

## <a name="query-parallelization"></a>Parallelisierung von Abfragen

In Microsoft R können Sie mit SQL Server-Datenquellen arbeiten, indem Sie Ihre Daten als ein RxSqlServerData-Datenquellenobjekt definieren.

Erstellt eine Datenquelle basierend auf eine gesamte Tabelle oder Sicht:

```R
RxSqlServerData(table= "airline", connectionString = sqlConnString)
```

Erstellt eine Datenquelle basierend auf einer SQL-Abfrage:

```R
RxSqlServerData(sqlQuery= "SELECT [ArrDelay],[CRSDepTime],[DayOfWeek] FROM  airlineWithIndex WHERE rowNum <= 100000", connectionString = sqlConnString)
```

> [!NOTE]
> Wenn eine Tabelle in der Datenquelle anstatt einer Abfrage angegeben ist, verwendet R Services interner Heuristik, um die bestimmt, welche Spalten aus der Tabelle abrufen; Dieser Ansatz ist jedoch wahrscheinlich nicht in einer parallelen Ausführung führen.

Um sicherzustellen, dass die Daten parallel analysiert werden können, sollte die Abfrage zum Abrufen der Daten so eingeschlossen werden, dass die Datenbank-Engine einen parallelen Abfrageplan erstellen kann. Wenn der Code oder Algorithmus große Mengen von Daten verwendet wird, stellen sicher, dass die Abfrage übergeben, um `RxSqlServerData` ist für die parallele Ausführung optimiert. Eine Abfrage, die nicht zu einem parallelen Ausführungsplan führt, kann zu einem einzelnen Prozess für die Berechnung führen.

Wenn Sie mit großen Datasets arbeiten müssen, verwenden Sie Management Studio oder eine andere SQL Query Analyzer vor dem Ausführen von R-Code, um den Ausführungsplan zu analysieren. Anschließend werden Sie alle empfohlenen Schritte zur Verbesserung der Leistung der Abfrage. Ein fehlender Index für eine Tabelle kann z.B. die Zeit zum Ausführen einer Abfrage beeinträchtigen. Weitere Informationen finden Sie unter [überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md).

Ein häufiger Fehler, der die Leistung auswirken kann, ist, dass eine Abfrage mehr Spalten als erforderlich sind, abruft. Z. B. wenn eine Formel darauf, dass nur die drei Spalten basiert, aber Ihre Quelltabelle über 30 Spalten verfügt, verschieben Sie Daten unnötigerweise.

 + Verwenden Sie `SELECT *`!
 + Dauern Sie überprüfen die Spalten im Dataset, und identifizieren Sie nur die für die Analyse benötigt einige Zeit
 + Entfernen Sie aus Ihrer Abfragen alle Spalten mit Datentypen, die mit R-Code, z. B. GUIDS und Rowguids nicht kompatibel sind
 + Überprüfung auf nicht unterstützten Datums- und Zeitformate
 + Anstatt eine Tabelle zu laden, erstellen Sie eine Ansicht, die bestimmte Werte aktiviert bzw. deaktiviert das wandelt Spalten, um Fehler bei der Konvertierung zu vermeiden.

## <a name="optimizing-the-machine-learning-algorithm"></a>Optimieren von Machine Learning-Algorithmus

Dieser Abschnitt enthält verschiedene Tipps und Ressourcen, die für RevoScaleR und anderen Optionen in Microsoft R. spezifisch sind

> [!TIP]
> Eine allgemeine Erörterung der R-Optimierung ist nicht Gegenstand dieses Artikels. Jedoch wenn Sie Ihren Code schneller zu treffen müssen, sollten beliebten Artikel [The R Inferno](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf). Er umfasst Konstrukte der Programmierung in R und häufigen Problemen in anschaulichen Sprache und die Details und bietet viele spezifische Beispiele von R Programmierverfahren.

### <a name="optimizations-for-revoscaler"></a>Optimierungen für RevoScaleR

Relativ viele Algorithmen für RevoScaleR unterstützt Parameter, um zu steuern, wie das trainierte Modell generiert wird. Während die Genauigkeit und Richtigkeit des Modells wichtig ist, kann die Leistung des Algorithmus gleichermaßen wichtig sein. Um das richtige Gleichgewicht zwischen der Genauigkeit und Zeit für das Training zu erhalten, können Sie Parameter zum Erhöhen der Geschwindigkeit, der Berechnung und in vielen Fällen Verbessern der Leistung ohne Reduzierung der Genauigkeit oder die Richtigkeit ändern.

+ [rxDTree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)

    `rxDTree` unterstützt die `maxDepth` -Parameter, der die Tiefe der Entscheidungsstruktur steuert. Als `maxDepth` wird erhöht, die Leistung kann beeinträchtigt, daher es wichtig ist, um die Vorteile der Strukturtiefe im Vergleich zu beeinträchtigt die Leistung zu analysieren.

    Sie können auch steuern das Gleichgewicht zwischen der Zeit Zeitkomplexität und vorhersagegenauigkeit durch Anpassen von Parametern wie z. B. `maxNumBins`, `maxDepth`, `maxComplete`, und `maxSurrogate`. Das Erhöhen der Tiefe auf mehr als 10 oder 15 kann die Berechnung sehr teuer machen.

+ [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)

    Versuchen Sie es mit der `cube` Argument, wenn die erste abhängige Variable in der Formel eine faktorvariable ist.
    
    Wenn `cube` nastaven NA hodnotu `TRUE`, die Regression erfolgt mithilfe einer partitionierten Inverse, in denen möglicherweise schneller ausgeführt und belegen weniger Speicherplatz als standardregression. Wenn die Formel über eine große Anzahl von Variablen verfügt, kann die Leistungssteigerung erheblich sein.

+ [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)

    Verwenden der `cube` Argument, wenn die erste abhängige Variable über eine faktorvariable ist.
    
    Wenn `cube` nastaven NA hodnotu `TRUE`, verwendet der Algorithmus eine partitionierte Inverse, in denen möglicherweise schneller ausgeführt und belegen weniger Speicher. Wenn die Formel über eine große Anzahl von Variablen verfügt, kann die Leistungssteigerung erheblich sein.

Weitere Anleitungen zur Optimierung von RevoScaleR finden Sie in diesen Artikeln:

+ Support-Artikel: [Feineinstellungsoptionen für RxDForest- rxdtree](https://support.microsoft.com/kb/3104235)

+ Methoden zum Steuern des Modells in einem boosted Tree-Modell passen: [schätzen Modelle mithilfe von Stochastic Gradient Boosting](https://docs.microsoft.com/r-server/r/how-to-revoscaler-boosting)

+ Übersicht über das RevoScaleR verschiebt und verarbeitet Daten: [schreiben Sie benutzerdefinierte Algorithmen, die Aufteilung in ScaleR](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ Programmiermodell für RevoScaleR: [Verwalten von Threads in RevoScaleR](https://docs.microsoft.com/r-server/r/how-to-developer-manage-threads)

+ Funktionsreferenz für [RxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

+ Funktionsreferenz für [RxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)

### <a name="use-microsoftml"></a>Verwenden des MicrosoftML

Zudem wird empfohlen, dass Sie in das neue Aussehen **MicrosoftML** -Paket, das skalierbare Machine Learning-Algorithmen bereitstellt, mit dem die computekontexte und Transformationen von RevoScaleR bereitgestellt verwenden können.

+ [Erste Schritte mit MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)

+ [Gewusst wie: auswählen ein Algorithmus MicrosoftML](https://docs.microsoft.com/r-server/r/how-to-choose-microsoftml-algorithms-cheatsheet)

### <a name="operationalize-a-solution-using-microsoft-r-server"></a>Operationalisieren einer Lösung mit Microsoft R Server

Wenn Ihr Szenario umfasst schnelle Vorhersagen mithilfe eines gespeicherten Modells oder Machine Learning in einer Anwendung integrieren, Sie können die [operationalisierung](https://docs.microsoft.com/r-server/what-is-operationalization) Funktionen in Microsoft R Server (ehemals DeployR).

+ Als eine **Data scientists**, verwenden Sie die [Mrsdeploy-Paket](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package) zum Freigeben von R-Code mit anderen Computern aus, und integrieren R-Analysen in Anwendungen für Web-, Desktop-, Mobile und Dashboards: [veröffentlichen und Verwalten von R-Webdienste in R Server](https://docs.microsoft.com/r-server/operationalize/how-to-deploy-web-service-publish-manage-in-r)

+ Als ein **Administrator**, erfahren Sie, wie Sie Pakete verwalten, überwachen Sie Web-Knoten und compute-Knoten und Steuern der Sicherheit für R-Aufträge: [so interagieren, und Nutzen von Webdiensten in R](https://docs.microsoft.com/r-server/operationalize/how-to-consume-web-service-interact-in-r)

## <a name="articles-in-this-series"></a>Artikel in dieser Serie

[Leistung optimieren für R – Einführung](sql-server-r-services-performance-tuning.md)

[Leistungsoptimierung für R – SQL Server-Konfiguration](sql-server-configuration-r-services.md)

[Leistungsoptimierung für R – R-Code und Daten-Optimierung](r-and-data-optimization-r-services.md)

[Leistungsoptimierung - Fallstudie Ergebnisse](performance-case-study-r-services.md)
