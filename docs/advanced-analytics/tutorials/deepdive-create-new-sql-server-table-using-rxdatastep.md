---
title: Erstellen einer neuen SQL Server Tabelle mithilfe von revoscaler rxdatastep
description: 'Tutorial: Exemplarische Vorgehensweise zum Erstellen einer SQL Server Tabelle mit der Sprache R auf SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b18f2bd42070746551d21ff7508e7fce58b49037
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714911"
---
# <a name="create-new-sql-server-table-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Erstellen einer neuen SQL Server Tabelle mithilfe von rxdatastep (SQL Server-und revoscaler-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Diese Lektion ist Teil des [revoscaler-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In dieser Lektion erfahren Sie, wie Sie Daten zwischen Datenrahmen im Arbeitsspeicher, dem Kontext [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und den lokalen Dateien verschieben.

> [!NOTE]
> In dieser Lektion wird ein anderes Dataset verwendet. Das Dataset für die Verspätungen von Fluggesellschaften ist ein öffentliches DataSet, das für Machine Learning-Experimente häufig verwendet wird. Die in diesem Beispiel verwendeten Datendateien sind in demselben Verzeichnis wie andere Produktbeispiele verfügbar.

## <a name="load-data-from-a-local-xdf-file"></a>Laden von Daten aus einer lokalen Xdf-Datei

In der ersten Hälfte dieses Tutorials haben Sie die Funktion **rxtextdata** verwendet, um Daten aus einer Textdatei in R zu importieren. Anschließend haben Sie die Funktion **rxdatastep** verwendet, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Daten in zu verschieben.

In dieser Lektion wird ein anderer Ansatz verwendet, und es werden Daten aus einer Datei verwendet, die im [Xdf-Format](https://en.wikipedia.org/wiki/Extensible_Data_Format)gespeichert ist. Nachdem Sie einige Lightweight-Transformationen für die Daten mithilfe der Xdf-Datei durchgeführt haben, speichern Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transformierten Daten in einer neuen Tabelle.

**Was ist Xdf?**

Das Xdf-Format ist ein XML-Standard, der für hochdimensionale Daten entwickelt wurde, und ist das systemeigene Dateiformat, das von [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf)verwendet wird. Dies ist ein binäres Dateiformat mit einer R-Schnittstelle, die die Verarbeitung und Analyse von Zeilen und Spalten optimiert.  Sie können es für das Verschieben von Daten verwenden, um Teilmengen von Daten zu speichern, die für Analysen hilfreich sind.

1. Legen Sie den Computekontext auf die lokale Arbeitsstation fest. **Für diesen Schritt sind DDL-Berechtigungen erforderlich.**

    ```R
    rxSetComputeContext("local")
    ```
  
2. Definieren Sie ein neues Datenquellenobjekt mithilfe der **RxXdfData** -Funktion. Zum Definieren einer Xdf-Datenquelle geben Sie den Pfad zur Datendatei an.  

    Sie können den Pfad zur Datei mit einer Text Variablen angeben. In diesem Fall gibt es jedoch eine praktische Verknüpfung, d. h. die **rxgetoption** -Funktion zu verwenden und die Datei (airlinedemosmall. Xdf) aus dem Beispiel Datenverzeichnis zu erhalten.
  
    ```R
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))
    ```

3. Rufen Sie [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) für die Daten im Arbeitsspeicher auf, um eine Zusammenfassung des Datasets anzuzeigen.
  
    ```R
    rxGetVarInfo(xdfAirDemo)
    ```

**Ergebnisse**

```R
Var 1: ArrDelay, Type: integer, Low/High: (-86, 1490)
Var 2: CRSDepTime, Type: numeric, Storage: float32, Low/High: (0.0167, 23.9833)
Var 3: DayOfWeek 7 factor levels: Monday Tuesday Wednesday Thursday Friday Saturday Sunday
```

> [!NOTE]
> 
> Haben Sie bemerkt, dass Sie keine anderen Funktionen aufrufen mussten, um die Daten in die XDF-Datei zu laden, und die Funktion **rxGetVarInfo** sofort auf die Daten anwenden konnten? Dies liegt daran, dass Xdf die standardmäßige Zwischenspeicher Methode für **revoscaler**ist. Zusätzlich zu Xdf-Dateien unterstützt die **rxgetvarinfo** -Funktion nun mehrere Quell Typen.

## <a name="move-contents-to-sql-server"></a>Inhalt in SQL Server verschieben

Mit der Xdf-Datenquelle, die in der lokalen R-Sitzung erstellt wurde, können Sie diese Daten in eine Datenbanktabelle verschieben und *DayOfWeek* als ganze Zahl mit Werten von 1 bis 7 speichern.

1. Definieren Sie ein SQL Server Datenquellen Objekt, und geben Sie eine Tabelle an, die die Daten enthält, sowie eine Verbindung mit dem Remote Server.
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
2. Berücksichtigen Sie als Vorsichtsmaßnahme einen Schritt, der überprüft, ob eine Tabelle mit demselben Namen bereits vorhanden ist, und löschen Sie die Tabelle, falls vorhanden. Eine vorhandene Tabelle mit denselben Namen verhindert, dass eine neue Tabelle erstellt wird.
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
3. Laden Sie die Daten mithilfe von **rxdatastep**in die Tabelle. Diese Funktion verschiebt Daten zwischen zwei bereits definierten Datenquellen und kann optional die Daten auf der Route transformieren.
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
        transforms = list( DayOfWeek = as.integer(DayOfWeek),
        rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
        overwrite = TRUE )
    ```
  
    Dies ist eine ziemlich große Tabelle. warten Sie daher, bis eine abschließende Statusmeldung wie die folgende angezeigt wird: *Gelesene Zeilen: 200000, verarbeitete Zeilen gesamt: 600000*.
     
## <a name="load-data-from-a-sql-table"></a>Laden von Daten aus einer SQL-Tabelle

Sobald Daten in der Tabelle vorhanden sind, können Sie Sie mithilfe einer einfachen SQL-Abfrage laden. 

1. Erstellen Sie eine neue SQL Server Datenquelle. Die Eingabe ist eine Abfrage für die neue Tabelle, die Sie soeben erstellt und mit Daten geladen haben. Diese Definition fügt die Faktor Ebenen für die *DayOfWeek* -Spalte hinzu, wobei das *COLINFO* -Argument für **rxsqlserverdata**verwendet wird.
  
    ```R
    sqlServerAirDemo2 <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
2. Wieder aufzurufen, um eine Zusammenfassung der Daten in der Abfrage zu überprüfen.
  
    ```R
    rxSummary(~., data = sqlServerAirDemo2)
    ```

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Blockweises Analysieren mithilfe von rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)