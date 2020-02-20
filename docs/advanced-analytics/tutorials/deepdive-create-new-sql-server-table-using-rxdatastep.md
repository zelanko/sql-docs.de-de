---
title: Erstellen einer Tabelle mit rxDataStep
description: 'Tutorial 11 zu RevoScaleR: Erstellen einer SQL Server-Tabelle mithilfe der R-Programmiersprache in SQL Server'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 99f693210b567523b74f851d1db68470cae2891d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "74947251"
---
# <a name="create-new-sql-server-table-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Erstellen einer neuen SQL Server-Tabelle mithilfe von rxDataStep (Tutorial für SQL Server und RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Bei diesem Tutorial handelt es sich um das elfte Tutorial von [Lernprogramm: Verwenden von RevoScaleR-Funktionen für R mit SQL Server-Daten](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md). In diesem Lernprogramm erfahren Sie, wie Sie [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server verwenden.

In diesem Tutorial erfahren Sie, wie Sie Daten zwischen In-Memory-Datenrahmen, den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Kontext und lokale Dateien verschieben.

> [!NOTE]
> Für dieses Tutorial wird ein anderes Dataset verwendet. Das Dataset „Airline Delays“ für Verspätungen einer Fluggesellschaft ist ein öffentliches Dataset, das hauptsächlich für Machine-Learning-Experimente verwendet wird. Die Datendateien, die in diesem Beispiel verwendet werden, sind im selben Verzeichnis wie die anderen Produktbeispiele verfügbar.

## <a name="load-data-from-a-local-xdf-file"></a>Laden von Daten aus einer lokalen XDF-Datei

In der ersten Hälfte dieses Tutorials haben Sie die Funktion **RxTextData** zum Importieren von Daten aus einer Textdatei in R und anschließend die Funktion **RxDataStep** zum Verschieben der Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet.

In diesem Tutorial kommt eine andere Herangehensweise zum Einsatz. Es werden Daten aus einer Datei verwendet, die im [XDF-Format](https://en.wikipedia.org/wiki/Extensible_Data_Format) gespeichert ist. Nach einigen einfachen Transformationen der Daten mithilfe der XDF-Datei speichern Sie die transformierten Daten in einer neuen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle.

**Was ist XDF?**

Das XDF-Format ist ein XML-Standard, der für hochdimensionale Daten entwickelt wurde und von [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf) nativ als Dateiformat verwendet wird. Dies ist ein binäres Dateiformat mit einer R-Schnittstelle, die die Verarbeitung und Analyse von Zeilen und Spalten optimiert.  Sie können es für das Verschieben von Daten verwenden, um Teilmengen von Daten zu speichern, die für Analysen hilfreich sind.

1. Legen Sie den Computekontext auf die lokale Arbeitsstation fest. **Für diesen Schritt sind DDL-Berechtigungen erforderlich.**

    ```R
    rxSetComputeContext("local")
    ```
  
2. Definieren Sie ein neues Datenquellenobjekt mithilfe der **RxXdfData** -Funktion. Geben Sie zur Definition einer XDF-Datenquelle den Pfad zur Datendatei an.  

    Sie können den Pfad zur Datei mithilfe einer Textvariable angeben. In diesem Fall gibt es jedoch eine praktischere Methode: Verwenden Sie die **rxGetOption**-Funktion, und rufen Sie die Datei (AirlineDemoSmall.xdf) aus dem Beispieldatenverzeichnis ab.
  
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
> Haben Sie bemerkt, dass Sie keine anderen Funktionen aufrufen mussten, um die Daten in die XDF-Datei zu laden, und die Funktion **rxGetVarInfo** sofort auf die Daten anwenden konnten? Das liegt daran, dass XDF die Standardmethode für die Zwischenspeicherung für **RevoScaleR** ist. Die Funktion **rxGetVarInfo** unterstützt neben XDF-Dateien auch mehrere Quelltypen.

## <a name="move-contents-to-sql-server"></a>Verschieben von Inhalten in SQL Server

Mit der in der lokalen R-Sitzung erstellten XDF-Datenquelle können Sie diese Daten nun in eine Datenbanktabelle verschieben. Dabei wird *DayOfWeek* als Integer mit Werten von 1 bis 7 gespeichert.

1. Definieren Sie ein SQL Server-Datenquellobjekt, und geben Sie eine Tabelle für die Speicherung der Daten und eine Verbindung zum Remoteserver an.
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
2. Überprüfen Sie vorsichtshalber, ob eine Tabelle mit dem gleichen Namen bereits vorhanden ist, und löschen Sie sie gegebenenfalls. Wenn bereits eine Tabelle mit gleichem Namen vorhanden ist, kann keine neue erstellt werden.
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
3. Laden Sie die Daten mithilfe von **rxDataStep** in die Tabelle. Diese Funktion verschiebt Daten zwischen zwei bereits definierten Datenquellen und kann die Daten optional bei der Übertragung transformieren.
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
        transforms = list( DayOfWeek = as.integer(DayOfWeek),
        rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
        overwrite = TRUE )
    ```
  
    Diese Tabelle ist groß, also warten Sie, bis eine Statusmeldung wie die folgende angezeigt wird: *Gelesene Zeilen: 200000, gesamte verarbeitete Zeilen: 600000*.
     
## <a name="load-data-from-a-sql-table"></a>Laden von Daten aus einer SQL-Tabelle

Sobald Daten in der Tabelle vorhanden sind, können Sie diese mit einer einfachen SQL-Abfrage laden. 

1. Erstellen Sie eine neue SQL Server-Datenquelle. Die Eingabe ist eine Abfrage für die neue Tabelle, die Sie gerade erstellt und in die Sie Daten geladen haben. Diese Definition fügt Faktorebenen für die *DayOfWeek*-Spalte mithilfe des *colInfo*-Arguments zu **RxSqlServerData** hinzu.
  
    ```R
    sqlServerAirDemo2 <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
2. Rufen Sie **rxSummary** noch mal auf, um eine Zusammenfassung der Daten in der Abfrage anzuzeigen.
  
    ```R
    rxSummary(~., data = sqlServerAirDemo2)
    ```

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Blockweises Analysieren mithilfe von rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)