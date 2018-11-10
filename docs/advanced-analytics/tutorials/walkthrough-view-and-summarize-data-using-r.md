---
title: Anzeigen und Zusammenfassen von Daten mithilfe von R (Exemplarische Vorgehensweise) | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/02/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 1d6c225b3ec6b2a7a80dea155b564b94ecab60fb
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51032887"
---
# <a name="view-and-summarize-data-using-r"></a>Anzeigen und Zusammenfassen von Daten mithilfe von R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Nun arbeiten wir mit den gleichen Daten mit R-Code. In dieser Lektion erfahren Sie, wie Sie mit den Funktionen in der **RevoScaleR** Paket.

Es wird ein R-Skript mit dieser exemplarischen Vorgehensweise bereitgestellt, das den gesamten Code enthält, der für die Erstellung des Datenobjekts, die Generierung von Zusammenfassungen und die Erstellung von Modellen erforderlich ist. Die R-Skriptdatei **RSQL_RWalkthrough.R**befindet sich an dem Speicherort, an dem Sie die Skriptdateien gespeichert haben.

+ Wenn Sie bereits über Erfahrung mit R verfügen, können Sie das Skript komplett auf einmal ausführen.
+ Für Personen, die revoscaler gerade erlernen durchläuft das Skript Zeile für Zeile mit in diesem Tutorial.
+ Um einzelne Zeilen des Skripts auszuführen, können Sie eine oder mehrere Zeilen in der Datei markieren und dann STRG+EINGABETASTE drücken.

> [!TIP]
> Speichern Sie Ihren R-Arbeitsbereich im Falle, dass Sie die restliche exemplarische Vorgehensweise später abschließen möchten.  Auf diese Weise können die Objekte und andere Variablen für die erneute Verwendung.

## <a name="define-a-sql-server-compute-context"></a>Definieren Sie einen SQL Server-computekontext

Microsoft R erleichtert Ihnen die zum Abrufen von Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Ihrem R-Code verwenden. Der Prozess sieht folgendermaßen aus:
  
- Stellen Sie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz her.
- Definieren Sie eine Abfrage mit den Daten, die Sie benötigen, oder geben Sie eine Tabelle oder Sicht an.
- Definieren von einem oder mehreren Computekontexten, die beim Ausführen von R-Code verwendet werden sollen
- Definieren Sie Transformationen, die an die Datenquelle angewendet werden, während sie aus der Quelle gelesen wird, ist optional,

Die folgenden Schritte sind alle Teil der R-Code und sollte in einer R-Umgebung ausgeführt werden kann. Es verwendet, Microsoft R Client, da es die RevoScaleR-Pakete sowie einen grundlegenden, einfachen Satz von R-Tools.

1. Wenn die **RevoScaleR** Paket noch nicht geladen, führen Sie diese Befehlszeile von R-Code:

    ```R
    library("RevoScaleR")
    ```

     Die Anführungszeichen sind in diesem Fall optional, obwohl empfohlen wird.
     
     Wenn Sie eine Fehlermeldung erhalten, stellen Sie sicher, dass Ihre R-Entwicklungsumgebung eine Bibliothek verwendet wird, die das RevoScaleR-Paket enthält. Verwenden Sie einen Befehl wie z. B. `.libPaths()` zum Anzeigen der aktuellen Bibliothek-Pfads.

2. Erstellen Sie die Verbindungszeichenfolge für SQL Server, und speichern Sie ihn in ein R-Variable, _ConnStr_.
    
    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Uid=your-sql-login;Pwd=your-login-password"
    ```

    Für den Servernamen ein möglicherweise nur den Namen der Instanz verwenden können oder müssen Sie möglicherweise den Namen, abhängig von Ihrem Netzwerk vollständig zu qualifizieren.

    Für die Windows-Authentifizierung ist die Syntax etwas anders:
    
    ```R
    connStr <- "Driver=SQL Server;Server=your_server_name;Database=nyctaxi_sample;Trusted_Connection=True"
    ```

    Das für den Download verfügbare R-Skript verwendet ausschließlich SQL-Anmeldungen. Im Allgemeinen empfehlen wir, dass Sie Windows-Authentifizierung möglichst zu vermeiden, das Speichern von Kennwörtern in Ihrem R-Code verwenden. Um sicherzustellen, dass der Code in diesem Tutorial, den Code von Github heruntergeladen entspricht, werden wir jedoch eine SQL-Anmeldung für den Rest der exemplarischen Vorgehensweise verwenden.

3. Definieren Sie Variablen für die beim Erstellen eines neuen *computekontext*. Nachdem Sie das computekontextobjekt erstellt haben, können Sie es zum Ausführen von R-Code für die SQL Server-Instanz verwenden.

    ```R
    sqlShareDir <- paste("C:\\AllShare\\",Sys.getenv("USERNAME"),sep="")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    ```

    - R nutzt ein temporäres Verzeichnis, das bei der Serialisierung von R-Objekten zwischen Ihrer Arbeitsstation und dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Computer verwendet wird. Sie können das lokale Verzeichnis angeben, das als *SqlShareDir*verwendet wird, oder den Standardnamen übernehmen.
  
    - Verwendung *SqlWait* , um anzugeben, ob R auf Ergebnisse vom Server gewartet werden soll.  Eine Erläuterung wartender im Vergleich zu nicht wartenden Aufträge, finden Sie unter [verteilte und parallelem computing mit ScaleR in Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).
  
    - Verwenden Sie das Argument *SqlConsoleOutput* um anzugeben, dass Sie nicht, um die Ausgabe der R-Konsole finden Sie unter möchten.


4. Rufen Sie die [RxInSqlServer](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxinsqlserver) Konstruktor, erstellen das computekontextobjekt mit den Variablen und Verbindungszeichenfolgen, die bereits definiert werden soll, und speichern das neue Objekt in der R-Variable *Sqlcc*.
  
    ```R
    sqlcc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```

5. Der computekontext ist standardmäßig lokal, daher Sie explizit festlegen müssen der *active* compute Context verwenden.

    ```R
    rxSetComputeContext(sqlcc)
    ```

    + `rxSetComputeContext` gibt den zuvor aktiven Computekontext im Hintergrund zurück, sodass Sie ihn verwenden können.
    + `rxGetComputeContext` gibt den aktiven Computekontext zurück.
    
    Beachten Sie, dass das Festlegen des Computekontexts nur Vorgänge betrifft, die Funktionen im **RevoScaleR** -Paket nutzen. Der Computekontext wirkt sich nicht darauf aus, wie Open-Source-R-Vorgänge erfolgen.

## <a name="create-a-data-source-using-rxsqlserver"></a>Erstellen Sie eine Datenquelle "rxsqlserver"

In Microsoft R eine *Datenquelle* ist ein Objekt, das Sie erstellen mithilfe der RevoScaleR-Funktionen. Das Datenquellenobjekt gibt einen Satz mit Daten, die Sie für eine Aufgabe, wie das Modell trainieren oder Funktion extrahieren verwenden möchten. Sie können Daten aus einer Vielzahl von Quellen abrufen; die Liste der derzeit unterstützten Datenquellen, finden Sie unter [RxDataSource](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource).

Früher Sie eine Verbindungszeichenfolge definiert und diese Informationen in einer R-Variablen gespeichert. Sie können erneut verwenden, Verbindungsinformationen, um die Daten anzugeben, dass Sie abrufen möchten.

1. Speichern Sie eine SQL-Abfrage als Zeichenfolgenvariable. Die Abfrage definiert die Daten zum Trainieren des Modells.

    ```R
    sampleDataQuery <- "SELECT TOP 1000 tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime, pickup_longitude, pickup_latitude, dropoff_longitude, dropoff_latitude FROM nyctaxi_sample"
    ```

    Wir haben hier eine TOP-Klausel verwendet, um schneller ausgeführt werden, Dinge zu machen, aber die tatsächlichen Zeilen, die von der Abfrage zurückgegebenen können variieren, je nach Reihenfolge. Daher können die Ergebnisse der Zusammenfassung auch andere als die unten aufgeführten sein. Die TOP-Klausel entfernen können.

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
  
    + Das Argument *RowsPerRead* ist wichtig für die Verwaltung von Speichermanagement und effiziente Berechnungen.  Die meisten analytischen Funktionen in[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] verarbeiten Daten in Segmenten und sammeln Zwischenergebnisse an, die die endgültigen Berechnungen zurückgeben, nachdem alle Daten gelesen wurden.  Durch Hinzufügen der *RowsPerRead* -Parameter können Sie steuern, wie viele Datenzeilen in jedes Segment für die Verarbeitung eingelesen werden.  Wenn der Wert dieses Parameters zu groß ist, könnte der Datenzugriff möglicherweise langsam sein, da Sie nicht über genügen Speicher verfügen, um einen solch großen Datenblock effizient zu verarbeiten.  Bei einigen Systemen festlegen *RowsPerRead* auf einen sehr kleinen Wert können auch bereitstellen, was zu Leistungseinbußen.

3. Sie haben an diesem Punkt erstellt die *InDataSource* -Objekt, aber es enthält keine Daten. Die Daten nicht per Pull abgerufen werden von der SQL-Abfrage in die lokale Umgebung, bis Sie eine Funktion, z. B. ausführen [RxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) oder [RxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary).

    Nun, da Sie die Datenobjekte definiert haben, können Sie es allerdings als Argument für andere Funktionen verwenden.

## <a name="use-the-sql-server-data-in-r-summaries"></a>Verwenden Sie die SQL Server-Daten in R-Zusammenfassungen

In diesem Abschnitt Testen Sie einige der Funktionen [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] , remotecomputekontexte unterstützen. Durch Anwenden von R-Funktionen mit der Datenquelle, Sie können untersuchen, zusammenzufassen und Diagramm der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten.

1. Rufen Sie die Funktion [RxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) um eine Liste der Variablen in der Datenquelle und deren Datentypen zu erhalten.

    **RxGetVarInfo** ist eine nützliche Funktion, können Sie ihn auf jedem beliebigen Datenrahmen aufrufen oder auf einem Satz von Daten in einem remote-Datenobjekt, zum Abrufen von Informationen, z. B. die maximale und minimale Werte, der Datentyp und die Anzahl der Ebenen in faktorspalten.
    
    Ziehen Sie es in Erwägung, diese Funktion nach jeder Art von Dateneingabe, Funktionstransformation oder Featureentwicklung auszuführen. Auf diese Weise können Sie sicherstellen, dass alles, was die Funktionen, die Sie verwenden, in Ihrem Modell möchten die erwarteten Daten sind geben, und Fehler vermeiden.
  
    ```R
    rxGetVarInfo(data = inDataSource)
    ```

    **Ergebnisse**
    
    ```
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

2. Rufen Sie die RevoScaleR-Funktion nun [RxSummary](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsummary) um weitere detaillierte Statistiken zu einzelnen Variablen abzurufen.

    RxSummary basiert auf dem R `summary` funktionieren, aber verfügt über einige zusätzliche Funktionen und Vorteile. RxSummary arbeitet in mehrere computekontexte und unterstützt die Segmentierung.  Sie können auch RxSummary transformieren Werte oder zusammengefasst auf der Grundlage von Faktorebenen.
    
    In diesem Beispiel werden Sie den Fahrpreis basierend auf der Anzahl der Fahrgäste zusammengefasst.
    
    ```R
    start.time <- proc.time()
    rxSummary(~fare_amount:F(passenger_count,1,6), data = inDataSource)
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds,
      Elapsed Time=", round(used.time[3],2),
      " seconds to summarize the inDataSource.", sep=""))
    ```
    + Das erste Argument für RxSummary gibt die Formel oder den Begriff, nach zusammenzufassen. Hier ist die `F()` Funktion wird verwendet, um die Werte in konvertieren _Fahrgäste\_Anzahl_ in Faktoren vor der Zusammenfassung. Müssen Sie auch den Mindestwert (1) und den Höchstwert (6) Geben Sie für die _Fahrgäste\_Anzahl_ Faktor-Variable.
    + Wenn Sie die Statistiken ausgegeben nicht angeben, gibt standardmäßig RxSummary Mean, StDev, Min, Max und die Anzahl der gültigen und Beobachtungen.
    + Dieses Beispiel enthält Code, um zu messen, wie viel Zeit zwischen dem Start der Funktion und dem Abschluss der Funktion vergangen ist, sodass Sie die Leistung vergleichen können.
  
    **Ergebnisse**

    Wenn die RxSummary-Funktion erfolgreich ausgeführt wurde, sollten Sie sehen, dass Ergebnisse wie diese, gefolgt von einer Liste von Statistiken nach Kategorie. 

    ```
    rxSummary(formula = ~fare_amount:F(passenger_count, 1,6), data = inDataSource)
    Data: inDataSource (RxSqlServerData Data Source)
    Number of valid observations: 1000
    ```

### <a name="bonus-exercise-on-big-data"></a>Zusatzübung für big data

Versuchen Sie es eine neuen Abfragezeichenfolge für die alle Zeilen zu definieren. Es wird empfohlen, dass Sie ein neues Datenquellenobjekt für dieses Experiment eingerichtet. Sie können auch versuchen, Ändern der *RowsToRead* Parameter, um zu sehen, wie sie den Durchsatz auswirkt.

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
> Während dieser ausgeführt wird, können Sie ein Tool wie [Process Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx) oder SQL Profiler, um festzustellen, wie die Verbindung hergestellt wird und der R-Code mithilfe von SQL Server-Dienste ausgeführt wird.
> 
> Eine andere Möglichkeit besteht, zum Überwachen von R-Aufträge, die unter SQL Server, die mit diesen [benutzerdefinierte Berichte](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="next-lesson"></a>Nächste Lektion

[Erstellen von Graphen und Plots mit R](walkthrough-create-graphs-and-plots-using-r.md)

## <a name="previous-lesson"></a>Vorherige Lektion

[Durchsuchen der Daten mithilfe von SQL](walkthrough-view-and-explore-the-data.md)
