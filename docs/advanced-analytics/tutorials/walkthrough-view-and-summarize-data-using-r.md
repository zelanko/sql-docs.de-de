---
title: Anzeigen und Zusammenfassen von SQL Server Daten mithilfe von R-Funktionen
description: Tutorial, das zeigt, wie statistische Zusammenfassungen mithilfe von R-Funktionen für datenbankübergreifende Analysen auf SQL Server visualisiert und generiert werden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 47850bebcc20fdd357b2336a9597da067cd479ca
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715361"
---
# <a name="view-and-summarize-sql-server-data-using-r-walkthrough"></a>Anzeigen und Zusammenfassen von SQL Server Daten mithilfe von R (Exemplarische Vorgehensweise)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Diese Lektion enthält eine Einführung in die Funktionen im **revoscaler** -Paket und führt Sie durch die folgenden Aufgaben:

> [!div class="checklist"]
> * Verbindung mit SQL Server herstellen
> * Definieren Sie eine Abfrage mit den Daten, die Sie benötigen, oder geben Sie eine Tabelle oder Sicht an.
> * Definieren von einem oder mehreren Computekontexten, die beim Ausführen von R-Code verwendet werden sollen
> * Optional können Sie Transformationen definieren, die auf die Datenquelle angewendet werden, während Sie aus der Quelle gelesen wird.

## <a name="define-a-sql-server-compute-context"></a>Definieren eines SQL Server computekontexts

Führen Sie die folgenden r-Anweisungen in einer r-Umgebung auf der Client Arbeitsstation aus. In diesem Abschnitt wird davon ausgegangen, dass eine Data Science Arbeitsstation [mit Microsoft R Client](../r/set-up-a-data-science-client.md), da Sie alle revoscaler-Pakete sowie einen einfachen, einfachen Satz von R-Tools enthält. Beispielsweise können Sie "rgui. exe" verwenden, um das R-Skript in diesem Abschnitt auszuführen.

1. Wenn das **revoscaler** -Paket nicht bereits geladen ist, führen Sie die folgende Zeile des R-Codes aus:

    ```R
    library("RevoScaleR")
    ```

     Die Anführungszeichen sind optional, in diesem Fall jedoch empfohlen.
     
     Wenn Sie einen Fehler erhalten, stellen Sie sicher, dass Ihre R-Entwicklungsumgebung eine Bibliothek verwendet, die das revoscaler-Paket enthält. Verwenden `.libPaths()` Sie einen Befehl wie zum Anzeigen des aktuellen Bibliothekspfads.

2. Erstellen Sie die Verbindungs Zeichenfolge für SQL Server, und speichern Sie Siein einer R-Variablen, "".

   Sie müssen den Platzhalter "your_server_name" in einen gültigen SQL Server Instanznamen ändern. Für den Servernamen können Sie möglicherweise nur den Instanznamen verwenden, oder Sie müssen den Namen abhängig von Ihrem Netzwerk vollständig qualifizieren.
    
   Für SQL Server Authentifizierung lautet die Verbindungs Syntax wie folgt:

    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Uid=your-sql-login;Pwd=your-login-password"
    ```

    Bei der Windows-Authentifizierung ist die Syntax etwas anders:
    
    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Trusted_Connection=True"
    ```

    Im Allgemeinen empfiehlt es sich, nach Möglichkeit die Windows-Authentifizierung zu verwenden, um das Speichern von Kenn Wörtern in Ihrem R-Code zu vermeiden.

3. Definieren Sie Variablen, die beim Erstellen einesneuen computekontexts verwendet werden sollen. Nachdem Sie das computecontext-Objekt erstellt haben, können Sie es verwenden, um R-Code auf der SQL Server Instanz auszuführen.

    ```R
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```

    - R nutzt ein temporäres Verzeichnis, das bei der Serialisierung von R-Objekten zwischen Ihrer Arbeitsstation und dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Computer verwendet wird. Sie können das lokale Verzeichnis angeben, das als *SqlShareDir*verwendet wird, oder den Standardnamen übernehmen.
  
    - Verwenden Sie *sqlwait* , um anzugeben, ob R auf Ergebnisse vom Server warten soll.  Eine Erörterung von Wartezeiten im Vergleich zu nicht wartenden Aufträgen finden Sie unter [verteilte und parallele Berechnungen mit revoscaler in Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).
  
    - Verwenden Sie das Argument *sqlconsoleoutput* , um anzugeben, dass die Ausgabe der R-Konsole nicht angezeigt werden soll.

4. Rufen Sie den [rxinsqlserver](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinsqlserver) -Konstruktor auf, um das computecontext-Objekt mit den bereits definierten Variablen und Verbindungs Zeichenfolgen zu erstellen, und speichern Sie das neue Objekt in der R-Variablen *sqlcc*.
  
    ```R
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```

5. Standardmäßig ist der computekontext lokal, sodass Sie den *aktiven* computekontext explizit festlegen müssen.

    ```R
    rxSetComputeContext(sqlcc)
    ```

    + [rxsetcomputecontext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) gibt den zuvor aktiven computekontext unsichtbar zurück, damit Sie ihn verwenden können.
    + [rxgetcomputecontext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) gibt den aktiven computekontext zurück.
    
    Beachten Sie, dass das Festlegen eines computekontexts nur Vorgänge betrifft, die Funktionen im **revoscaler** -Paket verwenden. der computekontext wirkt sich nicht darauf aus, wie Open-Source-R-Vorgänge ausgeführt werden.

## <a name="create-a-data-source-using-rxsqlserver"></a>Erstellen einer Datenquelle mithilfe von rxsqlserver

Wenn Sie die Microsoft R-Bibliotheken wie revoscaler und microsoftml verwenden, ist eine *Datenquelle* ein Objekt, das Sie mithilfe von revoscaler-Funktionen erstellen. Das Datenquellen Objekt gibt einen Satz von Daten an, die Sie für einen Task verwenden möchten, z. b. Modell Training oder featureextraktion. Sie können Daten aus einer Vielzahl von Quellen, einschließlich SQL Server, erhalten. Eine Liste der derzeit unterstützten Quellen finden Sie unter [rxdatasource](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource).

Zuvor haben Sie eine Verbindungs Zeichenfolge definiert und diese Informationen in einer R-Variablen gespeichert. Sie können diese Verbindungsinformationen wieder verwenden, um die Daten anzugeben, die Sie erhalten möchten.

1. Speichern Sie eine SQL-Abfrage als Zeichen folgen Variable. Die Abfrage definiert die Daten zum Trainieren des Modells.

    ```R
    sampleDataQuery <- "SELECT TOP 1000 tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"
    ```

    Wir haben hier eine Top-Klausel verwendet, um die Arbeit schneller auszuführen, aber die tatsächlichen Zeilen, die von der Abfrage zurückgegeben werden, können je nach Reihenfolge variieren. Daher können sich die Zusammenfassungs Ergebnisse auch von den unten aufgeführten unterscheiden. Sie können die Top-Klausel entfernen.

2. Übergeben Sie die Abfragedefinition als Argument an die [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata)-Funktion.

    ```R
    inDataSource <- RxSqlServerData(
      sqlQuery = sampleDataQuery,
      connectionString = connStr,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
      dropoff_longitude = "numeric", dropoff_latitude = "numeric"),
      rowsPerRead=500
      )
    ```
    
    + Das Argument  *colClasses* gibt die zu verwendenden Spaltentypen an, wenn die Daten zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und R verschoben werden. Das ist wichtig, da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] andere und mehr Datentypen als R verwendet. Weitere Informationen finden Sie unter [R-Bibliotheken und-Datentypen](../r/r-libraries-and-data-types.md).
  
    + Das Argument *rowsperread* ist wichtig, um die Speicherauslastung und effiziente Berechnungen zu verwalten.  Die meisten analytischen Funktionen in[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] verarbeiten Daten in Segmenten und sammeln Zwischenergebnisse an, die die endgültigen Berechnungen zurückgeben, nachdem alle Daten gelesen wurden.  Durch Hinzufügen des *rowsperread* -Parameters können Sie steuern, wie viele Daten Zeilen in die einzelnen Blöcke für die Verarbeitung eingelesen werden.  Wenn der Wert dieses Parameters zu groß ist, kann der Datenzugriff langsam sein, da Sie nicht über genügend Arbeitsspeicher verfügen, um einen solchen großen Datenblock effizient zu verarbeiten.  Auf einigen Systemen kann das Festlegen von *rowsperread* auf einen übermäßig kleinen Wert auch zu einer geringeren Leistung werden.

3. An diesem Punkt haben Sie das *indatasource* -Objekt erstellt, es enthält jedoch keine Daten. Die Daten werden erst dann aus der SQL-Abfrage in die lokale Umgebung abgerufen, wenn Sie eine Funktion wie [rximport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) oder [rxsummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary)ausführen.

    Nachdem Sie jedoch die Datenobjekte definiert haben, können Sie Sie als Argument für andere Funktionen verwenden.

## <a name="use-the-sql-server-data-in-r-summaries"></a>Verwenden der SQL Server Daten in R-Zusammenfassungen

In diesem Abschnitt Testen Sie mehrere der in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] bereitgestellten Funktionen, die remotecomputekontexte unterstützen. Indem Sie R-Funktionen auf die Datenquelle anwenden, können Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten untersuchen, zusammenfassen und Diagramme.

1. Aufrufen Sie die Funktion [rxgetvarinfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) , um eine Liste der Variablen in der Datenquelle und deren Datentypen abzurufen.

    **rxgetvarinfo** ist eine praktische Funktion. Sie können Sie in jedem beliebigen Datenrahmen oder für einen Satz von Daten in einem Remote-Datenobjekt zum Abrufen von Informationen, wie z. b. die maximalen und minimalen Werte, den Datentyp und die Anzahl der Ebenen in Faktor Spalten, abrufen.
    
    Ziehen Sie es in Erwägung, diese Funktion nach jeder Art von Dateneingabe, Funktionstransformation oder Featureentwicklung auszuführen. Auf diese Weise können Sie sicherstellen, dass alle Features, die Sie in Ihrem Modell verwenden möchten, den erwarteten Datentyp aufweisen und Fehler vermeiden.
  
    ```R
    rxGetVarInfo(data = inDataSource)
    ```

    **Ergebnisse**
    
    ```R
    Var 1: tipped, Type: integer
    Var 2: fare_amount, Type: numeric
    Var 3: passenger_count, Type: integer
    Var 4: trip_time_in_secs, Type: numeric, Storage: int64
    Var 5: trip_distance, Type: numeric
    Var 6: pickup_datetime, Type: character
    Var 7: dropoff_datetime, Type: character
    Var 8: pickup_longitude, Type: numeric
    Var 9: pickup_latitude, Type: numeric
    Var 10: dropoff_longitude, Type: numeric
    ```

2. Rufen Sie nun die revoscaler-Funktion [rxsummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary) auf, um ausführlichere Statistik Informationen zu einzelnen Variablen zu erhalten.

    rxsummary basiert auf der R `summary` -Funktion, bietet jedoch einige zusätzliche Features und Vorteile. rxsummary funktioniert in mehreren computekontexten und unterstützt segmentieren.  Sie können rxsummary auch verwenden, um Werte zu transformieren oder basierend auf den Faktor Ebenen zusammenzufassen.
    
    In diesem Beispiel fassen Sie den Fahrpreis basierend auf der Anzahl der Fahrgäste zusammen.
    
    ```R
    start.time <- proc.time()
    rxSummary(~fare_amount:F(passenger_count,1,6), data = inDataSource)
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2),
      " seconds to summarize the inDataSource.", sep=""))
    ```
    + Das erste Argument für rxsummary gibt die Formel oder den Begriff an, die zusammengefasst werden sollen. Hier wird die `F()` -Funktion verwendet, um die Werte in _der\_Anzahl der Fahrgäste_ vor dem zusammenfassen in Faktoren zu konvertieren. Sie müssen auch den minimalen Wert (1) und den maximalen Wert (6) für die Variable für den Faktor für die _Fahrgast\_Anzahl_ angeben.
    + Wenn Sie nicht angeben, welche Statistiken ausgegeben werden sollen, gibt rxsummary standardmäßig Mean, STDEV, min, Max und die Anzahl der gültigen und fehlenden Beobachtungen aus.
    + Dieses Beispiel enthält Code, um zu messen, wie viel Zeit zwischen dem Start der Funktion und dem Abschluss der Funktion vergangen ist, sodass Sie die Leistung vergleichen können.
  
    **Ergebnisse**

    Wenn die rxsummary-Funktion erfolgreich ausgeführt wird, sollten die Ergebnisse wie diese angezeigt werden, gefolgt von einer Liste von Statistiken nach Kategorie. 

    ```R
    rxSummary(formula = ~fare_amount:F(passenger_count, 1,6), data = inDataSource)
    Data: inDataSource (RxSqlServerData Data Source)
    Number of valid observations: 1000
    ```

### <a name="bonus-exercise-on-big-data"></a>Bonus Übung auf Big Data

Versuchen Sie, eine neue Abfrage Zeichenfolge mit allen Zeilen zu definieren. Es wird empfohlen, dass Sie für dieses Experiment ein neues Datenquellen Objekt einrichten. Sie können auch versuchen, den *rowstoread* -Parameter zu ändern, um zu sehen, wie er den Durchsatz beeinflusst.

```R
bigDataQuery  <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"

bigDataSource <- RxSqlServerData(
      sqlQuery = bigDataQuery,
      connectionString = connStr,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
      dropoff_longitude = "numeric", dropoff_latitude = "numeric"),
      rowsPerRead=500
      )

start.time <- proc.time()
rxSummary(~fare_amount:F(passenger_count,1,6), data = bigDataSource)
used.time <- proc.time() - start.time
print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
  Elapsed Time=", round(used.time[3],2),
  " seconds to summarize the inDataSource.", sep=""))
```

> [!TIP]
> Während dies ausgeführt wird, können Sie ein Tool wie den [Prozess-Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx) oder SQL Profiler verwenden, um zu sehen, wie die Verbindung hergestellt wird und der R-Code mithilfe von SQL Server Services ausgeführt wird.
> 
> Eine weitere Möglichkeit ist die Überwachung von R-Aufträgen, die mithilfe dieser [benutzerdefinierten Berichte](../r/monitor-r-services-using-custom-reports-in-management-studio.md) auf SQL Server ausgeführt werden.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen von Graphen und Plots mit R](walkthrough-create-graphs-and-plots-using-r.md)