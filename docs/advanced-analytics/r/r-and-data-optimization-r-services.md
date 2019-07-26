---
title: Leistungsoptimierung für die Daten Optimierung
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 95cbcd152e9f7665191e44b7c6d704d2b0c63037
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470035"
---
# <a name="performance-for-r-services---data-optimization"></a>Leistung für R Services-Daten Optimierung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel ist der dritte in einer Reihe, in der die Leistungsoptimierung für R Services basierend auf zwei Fallstudien beschrieben wird. In diesem Artikel werden Leistungsoptimierungen für R-oder python-Skripts erläutert, die in SQL Server ausgeführt werden. Außerdem werden Methoden beschrieben, mit denen Sie Ihren R-Code aktualisieren können, um die Leistung zu steigern und bekannte Probleme zu vermeiden.

## <a name="choosing-a-compute-context"></a>Auswählen eines computekontexts

In SQL Server 2016 und 2017 können Sie beim Ausführen von R-oder python-Skripts entweder den **lokalen** oder den **SQL** -computekontext verwenden.

Wenn Sie den **lokalen** computekontext verwenden, wird die Analyse auf dem Computer und nicht auf dem Server ausgeführt. Wenn Sie also Daten aus SQL Server abrufen, die Sie in Ihrem Code verwenden, müssen die Daten über das Netzwerk abgerufen werden. Die Leistungseinbußen für diesen Netzwerkübertragung hängen von der Größe der übertragenen Daten, dem Geschwindigkeit des Netzwerks und anderen Netzwerkübertragungen ab, die zur gleichen Zeit auftreten.

Wenn Sie den **SQL Server computekontext**verwenden, wird der Code auf dem Server ausgeführt. Wenn Sie Daten aus SQL Server erhalten, sollten die Daten für den Server, auf dem die Analyse ausgeführt wird, lokal sein, und es wird kein Netzwerk Aufwand eingeführt. Wenn Sie Daten aus anderen Quellen importieren müssen, sollten Sie ggf. ETL anordnen.

Bei der Arbeit mit großen Datenmengen sollten Sie immer den SQL Compute Context verwenden.

## <a name="factors"></a>Faktoren

Die Sprache R weist das Konzept der *Faktoren*auf, bei denen es sich um spezielle Variablen für kategorische Daten handelt. Datenanalysten verwenden in Ihrer Formel häufig Faktor Variablen, da durch die Handhabung von kategorischen Variablen als Faktoren sichergestellt wird, dass die Daten von Machine Learning-Funktionen ordnungsgemäß verarbeitet werden. Weitere Informationen finden [Sie unter R für Dummies: Faktor Variablen](https://www.dummies.com/programming/r/how-to-look-at-the-structure-of-a-factor-in-r/).

In der Entwurfszeit können Faktor Variablen für die Speicherung oder Verarbeitung von Zeichen folgen in ganze Zahlen und wieder zurück konvertiert werden. Die R `data.frame` -Funktion verarbeitet alle Zeichen folgen als Faktor Variablen, es sei denn, das *stringsasfactors* -Argument ist auf **false**festgelegt. Dies bedeutet, dass Zeichen folgen für die Verarbeitung automatisch in eine ganze Zahl konvertiert und dann der ursprünglichen Zeichenfolge wieder zugeordnet werden.

Wenn die Quelldaten für Faktoren als ganze Zahl gespeichert werden, kann die Leistung beeinträchtigt werden, da R die Faktor Integerzahlen zur Laufzeit in Zeichen folgen konvertiert und dann eine eigene interne Konvertierung von Zeichen folgen zu ganzzahligen Zeichen folgen ausführt.

Um derartige Lauf Zeit Konvertierungen zu vermeiden, sollten Sie die Werte als ganze Zahlen in der SQL Server Tabelle speichern und das _COLINFO_ -Argument verwenden, um die Ebenen für die Spalte anzugeben, die als Faktor verwendet wird. Die meisten Datenquellen Objekte in revoscaler nehmen den Parameter _COLINFO_an. Verwenden Sie diesen Parameter, um die von der Datenquelle verwendeten Variablen zu benennen, ihren Typ anzugeben und die Variablen Ebenen oder Transformationen für die Spaltenwerte zu definieren.

Beispielsweise ruft der folgende R-Funktionsaufrufe die ganzen Zahlen 1, 2 und 3 aus einer Tabelle ab, ordnet die Werte jedoch einem Faktor mit den Ebenen "Apple", "Orange" und "Banane" zu.

```R
c("fruit" = c(type = "factor", levels=as.character(c(1:3)), newLevels=c("apple", "orange", "banana")))
```

Wenn die Quell Spalte Zeichen folgen enthält, ist es immer effizienter, die Ebenen vorab mithilfe des _COLINFO_ -Parameters anzugeben. Der folgende R-Code behandelt z. b. die Zeichen folgen als Faktoren, während Sie gelesen werden.

```R
c("fruit" = c(type = "factor", levels= c("apple", "orange", "banana")))
```

Wenn die Modell Generierung keinen semantischen Unterschied hat, kann der letztere Ansatz zu einer besseren Leistung führen.

## <a name="data-transformations"></a>Daten Transformationen

Datenanalysten verwenden häufig Transformationsfunktionen, die als Teil der Analyse in R geschrieben werden. Die Transformations Funktion wird auf jede Zeile angewendet, die aus der Tabelle abgerufen wird. In SQL Server werden solche Transformationen auf alle in einem Batch abgerufenen Zeilen angewendet, für die eine Kommunikation zwischen dem R-Interpreter und der Analyse-Engine erforderlich ist. Zum Ausführen der Umwandlungen werden die Daten von SQL an die Datenanalyse-Engine und dann an den Prozess der R-Interpreter verschoben und zurück.

Aus diesem Grund kann die Verwendung von Transformationen als Teil des R-Codes eine erhebliche negative Auswirkung auf die Leistung des Algorithmus haben, abhängig von der Menge der beteiligten Daten.

Es ist effizienter, alle notwendigen Spalten in der Tabelle oder Sicht vor dem Ausführen von Analysen zu haben und Transformationen während der Berechnung zu vermeiden. Wenn es nicht möglich ist, zusätzliche Spalten zu vorhandenen Tabellen hinzuzufügen, können Sie eine andere Tabelle oder Ansicht mit den transformierten Spalten erstellen und eine entsprechende Abfrage zum Abrufen der Daten verwenden.

## <a name="batch-row-reads"></a>Zeilen Lesevorgänge in Batch

Wenn Sie im Code eine SQL Server Datenquelle`RxSqlServerData`() verwenden, wird empfohlen, dass Sie versuchen, die Batch Größe mit dem Parameter _rowsperread_ anzugeben. Dieser Parameter definiert die Anzahl der Zeilen, die abgefragt und dann zur Verarbeitung an das externe Skript gesendet werden. Zur Laufzeit sieht der Algorithmus nur die angegebene Anzahl von Zeilen in jedem Batch.

Die Möglichkeit, die Menge der Daten zu steuern, die gleichzeitig verarbeitet werden, kann Ihnen helfen, Probleme zu lösen oder zu vermeiden. Wenn das Eingabe DataSet z. b. sehr breit ist (viele Spalten aufweist) oder wenn das DataSet über einige große Spalten (z. b. den freien Text) verfügt, können Sie die Batch Größe verringern, um zu vermeiden, dass Auslagerungs Daten aus dem Arbeitsspeicher entfernt werden.

Standardmäßig ist der Wert dieses Parameters auf 50000 festgelegt, um eine angemessene Leistung zu gewährleisten, auch auf Computern mit wenig Arbeitsspeicher. Wenn der Server über genügend Arbeitsspeicher verfügt, kann die Erhöhung dieses Werts auf 500.000 oder sogar auf eine Million zu einer besseren Leistung führen, insbesondere bei großen Tabellen.

Die Vorteile der Vergrößerung der Batch Größe werden bei einem großen Dataset und in einer Aufgabe, die in mehreren Prozessen ausgeführt werden kann, deutlich. Wenn Sie diesen Wert erhöhen, erzielen Sie jedoch nicht immer die besten Ergebnisse. Es wird empfohlen, dass Sie mit Ihren Daten und dem Algorithmus experimentieren, um den optimalen Wert zu ermitteln.

## <a name="parallel-processing"></a>Parallele Verarbeitung

Um die Leistung von **RX** -analytischen Funktionen zu verbessern, können Sie die Möglichkeit SQL Server, Aufgaben parallel mithilfe der verfügbaren Kerne auf dem Server Computer auszuführen.

Es gibt zwei Möglichkeiten, die Parallelisierung mit R in SQL Server zu erreichen:

-   **Verwenden \@Sie parallel.** Bei Verwendung der `sp_execute_external_script` gespeicherten Prozedur zur Ausführung eines R-Skripts legen Sie den `@parallel`-Parameter auf `1` fest. Dies ist die beste Methode, wenn Ihr R-Skript **keine** revoscaler-Funktionen verwendet, die andere Mechanismen für die Verarbeitung aufweisen. Wenn Ihr Skript revoscaler-Funktionen verwendet (in der Regel als "RX" mit dem Präfix "RX"), wird die parallele Verarbeitung automatisch `@parallel` ausgeführt `1`, und Sie müssen nicht explizit auf festlegen.

    Wenn das R-Skript parallelisiert werden kann, und wenn die SQL-Abfrage parallelisiert werden kann, erstellt die Datenbank-Engine mehrere parallele Prozesse. Die maximale Anzahl von Prozessen, die erstellt werden können, entspricht der Einstellung **Max. Grad an Parallelität** (MAXDOP) für die-Instanz. Alle Prozesse führen dann dasselbe Skript aus, empfangen aber nur einen Teil der Daten.
    
    Daher ist diese Methode für Skripts, die alle Daten anzeigen müssen, z. b. beim Trainieren eines Modells, nicht nützlich. Es ist jedoch nützlich, wenn Tasks wie die Batchvorhersage parallel ausgeführt werden. Weitere Informationen zur Verwendung von Parallelität mit `sp_execute_external_script`finden Sie im Abschnitt **Erweiterte Tipps: parallele Verarbeitung** der [Verwendung von R-Code in Transact-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).

-   **Verwenden Sie "numtasks = 1".** Wenn Sie **RX** -Funktionen in einem SQL Server computekontext verwenden, legen Sie den Wert des _numtasks_ -Parameters auf die Anzahl der Prozesse fest, die Sie erstellen möchten. Die Anzahl der erstellten Prozesse darf nicht größer sein als **MAXDOP**. die tatsächliche Anzahl der erstellten Prozesse wird jedoch von der Datenbank-Engine bestimmt und ist möglicherweise kleiner als Sie angefordert haben.

    Wenn das R-Skript parallelisiert werden kann, und wenn die SQL-Abfrage parallelisiert werden kann, erstellt SQL Server beim Ausführen der RX-Funktionen mehrere parallele Prozesse. Die tatsächliche Anzahl von Prozessen, die erstellt werden, hängt von einer Vielzahl von Faktoren ab, z. b. der Ressourcenkontrolle, der aktuellen Verwendung von Ressourcen, anderen Sitzungen und dem Abfrage Ausführungsplan für die Abfrage, die mit dem R-Skript verwendet wird.

## <a name="query-parallelization"></a>Abfrage Parallelisierung

In Microsoft R können Sie mit SQL Server Datenquellen arbeiten, indem Sie die Daten als rxsqlserverdata-Datenquellen Objekt definieren.

Erstellt eine Datenquelle auf der Grundlage einer gesamten Tabelle oder Sicht:

```R
RxSqlServerData(table= "airline", connectionString = sqlConnString)
```

Erstellt eine Datenquelle auf der Grundlage einer SQL-Abfrage:

```R
RxSqlServerData(sqlQuery= "SELECT [ArrDelay],[CRSDepTime],[DayOfWeek] FROM  airlineWithIndex WHERE rowNum <= 100000", connectionString = sqlConnString)
```

> [!NOTE]
> Wenn eine Tabelle in der Datenquelle anstelle einer Abfrage angegeben wird, verwendet R Services interne Heuristik, um die erforderlichen Spalten zum Abrufen aus der Tabelle zu ermitteln. Dieser Ansatz führt jedoch wahrscheinlich nicht zu einer parallelen Ausführung.

Um sicherzustellen, dass die Daten parallel analysiert werden können, sollte die Abfrage, die zum Abrufen der Daten verwendet wird, so eingeschlossen werden, dass die Datenbank-Engine einen parallelen Abfrageplan erstellen kann. Wenn der Code oder Algorithmus große Datenmengen verwendet, stellen Sie sicher, dass die Abfrage, `RxSqlServerData` die an übergeben wird, für die parallele Ausführung optimiert ist. Eine Abfrage, die nicht zu einem parallelen Ausführungsplan führt, kann zu einem einzelnen Prozess für die Berechnung führen.

Wenn Sie mit großen Datasets arbeiten müssen, verwenden Sie Management Studio oder einen anderen SQL Query Analyzer, bevor Sie den R-Code ausführen, um den Ausführungsplan zu analysieren. Führen Sie dann die empfohlenen Schritte aus, um die Leistung der Abfrage zu verbessern. Ein fehlender Index für eine Tabelle kann z.B. die Zeit zum Ausführen einer Abfrage beeinträchtigen. Weitere Informationen finden Sie unter [überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md).

Ein weiterer häufiger Fehler, der sich auf die Leistung auswirken kann, besteht darin, dass eine Abfrage mehr Spalten als erforderlich abruft. Wenn eine Formel z. b. auf nur drei Spalten basiert, die Quell Tabelle jedoch 30 Spalten enthält, verschieben Sie die Daten unnötig.

 + Vermeiden Sie `SELECT *`die Verwendung!
 + Nehmen Sie sich etwas Zeit, um die Spalten im DataSet zu überprüfen und nur die für die Analyse benötigten Elemente zu identifizieren.
 + Entfernen Sie aus den Abfragen alle Spalten, die Datentypen enthalten, die mit R-Code nicht kompatibel sind, z. b. GUIDs und ROWGUIDS.
 + Auf nicht unterstützte Datums-und Uhrzeit Formate überprüfen
 + Anstatt eine Tabelle zu laden, erstellen Sie eine Sicht, mit der bestimmte Werte ausgewählt oder Spalten umgewandelt werden, um Konvertierungs Fehler zu vermeiden.

## <a name="optimizing-the-machine-learning-algorithm"></a>Optimieren des Machine Learning-Algorithmus

Dieser Abschnitt enthält verschiedene Tipps und Ressourcen, die für revoscaler und andere Optionen in Microsoft R spezifisch sind.

> [!TIP]
> Eine allgemeine Erläuterung der R-Optimierung ist der Rahmen dieses Artikels. Wenn Sie Ihren Code jedoch schneller machen müssen, empfiehlt es sich, den gängigen Artikel, [R-Inferno](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf), zu erhalten. Es behandelt Programmierkonstrukte in R und häufige Fehler in anschaulicher Sprache und Detail und bietet viele spezifische Beispiele für r-Programmiertechniken.

### <a name="optimizations-for-revoscaler"></a>Optimierungen für revoscaler

Viele revoscaler-Algorithmen unterstützen Parameter, um zu steuern, wie das trainierte Modell generiert wird. Obwohl die Genauigkeit und Richtigkeit des Modells wichtig ist, ist die Leistung des Algorithmus möglicherweise ebenso wichtig. Um das richtige Gleichgewicht zwischen der Genauigkeit und der Trainingszeit zu erzielen, können Sie Parameter ändern, um die Geschwindigkeit der Berechnung zu erhöhen, und in vielen Fällen die Leistung verbessern, ohne die Genauigkeit oder Richtigkeit zu verringern.

+ [rxDTree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)

    `rxDTree`unterstützt `maxDepth` den-Parameter, der die Tiefe der Entscheidungsstruktur steuert. Da `maxDepth` sich die Leistung erhöht, kann die Leistung beeinträchtigt werden. Daher ist es wichtig, die Vorteile der Erhöhung der Tiefe und der Leistungs Verletzung zu analysieren.

    Sie können auch das Gleichgewicht Zwischenzeit Komplexität und `maxNumBins`Vorhersagegenauigkeit steuern, indem Sie Parameter wie, `maxDepth`, `maxSurrogate` `maxComplete`und anpassen. Das Erhöhen der Tiefe auf mehr als 10 oder 15 kann die Berechnung sehr teuer machen.

+ [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)

    Verwenden Sie das `cube` -Argument, wenn die erste abhängige Variable in der Formel eine Faktor Variable ist.
    
    Wenn `cube` auf`TRUE`festgelegt ist, wird die Regression mithilfe einer partitionierten Umkehrung durchgeführt, die möglicherweise schneller ist und weniger Arbeitsspeicher beansprucht, als die Berechnung der Standard Regression. Wenn die Formel über eine große Anzahl von Variablen verfügt, kann die Leistungssteigerung erheblich sein.

+ [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)

    Verwenden Sie `cube` das-Argument, wenn die erste abhängige Variable eine Faktor Variable ist.
    
    Wenn `cube` auf`TRUE`festgelegt ist, verwendet der Algorithmus eine partitionierte Umkehrung, die möglicherweise schneller ist und weniger Arbeitsspeicher beansprucht. Wenn die Formel über eine große Anzahl von Variablen verfügt, kann die Leistungssteigerung erheblich sein.

Weitere Anleitungen zur Optimierung von revoscaler finden Sie in den folgenden Artikeln:

+ Support Artikel: [Optionen für die Leistungsoptimierung für rxdforest und rxdtree](https://support.microsoft.com/kb/3104235)

+ Methoden zum Steuern der Modellanpassung in ein verstärktem Strukturmodell: [Schätzen von Modellen mit Stochastic Gradient-Verstärkung](https://docs.microsoft.com/r-server/r/how-to-revoscaler-boosting)

+ Übersicht über die Verschiebung und Verarbeitung von Daten durch revoscaler: [Schreiben von benutzerdefinierten Segmentierungsalgorithmen in Scaler](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ Programmiermodell für revoscaler: [Verwalten von Threads in revoscaler](https://docs.microsoft.com/r-server/r/how-to-developer-manage-threads)

+ Funktionsreferenz für [rxdforest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

+ Funktionsreferenz für [rxbtrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)

### <a name="use-microsoftml"></a>Verwenden von microsoftml

Außerdem wird empfohlen, dass Sie sich das neue **microsoftml** -Paket ansehen, das skalierbare Machine Learning-Algorithmen bereitstellt, die die computekontexte und Transformationen verwenden können, die von revoscaler bereitgestellt werden.

+ [Einstieg in microsoftml](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)

+ [Auswählen eines microsoftml-Algorithmus](https://docs.microsoft.com/r-server/r/how-to-choose-microsoftml-algorithms-cheatsheet)

### <a name="operationalize-a-solution-using-microsoft-r-server"></a>Operationalisieren einer Lösung mithilfe von Microsoft R Server

Wenn Ihr Szenario eine schnelle Vorhersage mithilfe eines gespeicherten Modells oder das Integrieren von Machine Learning in eine Anwendung umfasst, können Sie die [operationalisierungsfunktionen](https://docs.microsoft.com/r-server/what-is-operationalization) in Microsoft R Server (ehemals deployr) verwenden.

+ Verwenden Sie als **Daten**Analysten das mrsbereitstellungs- [Paket](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package) , um r-Code für andere Computer freizugeben, und integrieren Sie r Analytics in Web-, Desktop-, Mobile und dashboardanwendungen: [Veröffentlichen und Verwalten von R-Webdiensten in R Server](https://docs.microsoft.com/r-server/operationalize/how-to-deploy-web-service-publish-manage-in-r)

+ Als **Administrator**erfahren Sie, wie Sie Pakete verwalten, webknoten und Computeknoten überwachen und die Sicherheit für R-Aufträge Steuern: [Interagieren mit und Verwenden von Webdiensten in R](https://docs.microsoft.com/r-server/operationalize/how-to-consume-web-service-interact-in-r)

## <a name="articles-in-this-series"></a>Artikel in dieser Reihe

[Leistungsoptimierung für R-Einführung](sql-server-r-services-performance-tuning.md)

[Leistungsoptimierung für R-SQL Server-Konfiguration](sql-server-configuration-r-services.md)

[Leistungsoptimierung für r-r-Code und Daten Optimierung](r-and-data-optimization-r-services.md)

[Leistungsoptimierung: Ergebnisse der Fallstudie](performance-case-study-r-services.md)
