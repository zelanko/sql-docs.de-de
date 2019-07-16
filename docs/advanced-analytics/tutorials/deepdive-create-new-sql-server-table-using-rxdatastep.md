---
title: Erstellen Sie neue SQL Server-Tabelle, die mithilfe von RxDataStep von RevoScaleR - SQL Server-Machine Learning
description: Exemplarische Vorgehensweise im Lernprogramm zum Erstellen einer SQL Server-Tabelle, die Verwendung der Sprache R auf SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 484f238e53db21030b04cdf46b86271236509989
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962269"
---
# <a name="create-new-sql-server-table-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Erstellen Sie neue SQL Server-Tabelle, die mithilfe von RxDataStep (SQL Server und die RevoScaleR-Lernprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil der [RevoScaleR Tutorial](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In dieser Lektion erfahren Sie, wie zum Verschieben von Daten zwischen in-Memory-Datenrahmen, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Kontext und lokale Dateien.

> [!NOTE]
> In dieser Lektion wird ein anderes DataSet verwendet. Verzögerungen bei der Fluggesellschaft Dataset ist ein öffentliches Dataset, das häufig für Machine learning-Experimente verwendet wird. In diesem Beispiel verwendeten Datendateien sind im selben Verzeichnis wie die anderen Produktbeispiele verfügbar.

## <a name="load-data-from-a-local-xdf-file"></a>Laden von Daten aus einer lokalen XDF-Datei

In der ersten Hälfte in diesem Tutorial verwendet Sie die **RxTextData** Funktion, um das Importieren von Daten aus einer Textdatei in R und anschließend verwendet der **RxDataStep** Funktion zum Verschieben der Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

In dieser Lektion verwendet einen anderen Ansatz, und verwendet Daten aus einer Datei gespeichert wird, der [XDF-Format](https://en.wikipedia.org/wiki/Extensible_Data_Format). Nach einigen einfachen Transformationen auf die Daten mithilfe der XDF-Datei, speichern Sie die transformierten Daten in eine neue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle.

**Was ist XDF?**

Das XDF-Format ist eine XML-Standard für hochdimensionaler Daten entwickelt und wird von das systemeigene Dateiformat verwendet [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf). Dies ist ein binäres Dateiformat mit einer R-Schnittstelle, die die Verarbeitung und Analyse von Zeilen und Spalten optimiert.  Sie können es für das Verschieben von Daten verwenden, um Teilmengen von Daten zu speichern, die für Analysen hilfreich sind.

1. Legen Sie den Computekontext auf die lokale Arbeitsstation fest. **DDL-Berechtigungen sind für diesen Schritt erforderlich.**

    ```R
    rxSetComputeContext("local")
    ```
  
2. Definieren Sie ein neues Datenquellenobjekt mithilfe der **RxXdfData** -Funktion. Um eine XDF-Datenquelle definieren möchten, geben Sie den Pfad zu der Datendatei.  

    Sie können den Pfad zu der Datei mit einer Textvariablen angeben. Allerdings in diesem Fall besteht eine praktische Kurzform, das ist die Verwendung der **RxGetOption** Funktion, und rufen Sie die Datei (AirlineDemoSmall.xdf) im Daten-Beispielverzeichnis aus.
  
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
> Haben Sie bemerkt, dass Sie keine anderen Funktionen aufrufen mussten, um die Daten in die XDF-Datei zu laden, und die Funktion **rxGetVarInfo** sofort auf die Daten anwenden konnten? Dies liegt daran XDF die Standardmethode für die Zwischenspeicherung für ist **RevoScaleR**. Zusätzlich zu XDF-Dateien die **RxGetVarInfo** -Funktion unterstützt jetzt mehrere Typen.

## <a name="move-contents-to-sql-server"></a>Verschieben von Inhalt in SQL Server

Sie können mit der XDF-Datenquelle in der lokalen R-Sitzung erstellt wurden, nun diese Daten verschieben, in einer Datenbanktabelle speichern *DayOfWeek* als ganze Zahl mit Werten von 1 bis 7.

1. Definieren Sie ein SQL Server-Objekt, eine Tabelle, um die Daten sowie die Verbindung mit dem Remoteserver enthalten angeben.
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
2. Als Vorsichtsmaßnahme enthalten Sie einen Schritt, der überprüft, ob eine Tabelle mit dem gleichen Namen bereits vorhanden ist, und löschen Sie in der Tabelle, sofern vorhanden. Eine vorhandene Tabelle mit den gleichen Namen wird verhindert, dass eine neue erstellt werden.
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
3. Laden der Daten in der Tabelle mit **RxDataStep**. Diese Funktion verschiebt Daten zwischen zwei bereits definierten Datenquellen und können optional die Daten dem Weg zu transformieren.
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
        transforms = list( DayOfWeek = as.integer(DayOfWeek),
        rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
        overwrite = TRUE )
    ```
  
    Dies ist eine ziemlich große Tabelle, also warten Sie, bis eine letzte Statusmeldung wie diesen: *Gelesene Zeilen: 200000, insgesamt Zeilen verarbeitet: 600000*.
     
## <a name="load-data-from-a-sql-table"></a>Laden von Daten aus einer SQL-Tabelle

Sobald Daten in der Tabelle vorhanden ist, können Sie es mit einer einfachen SQL-Abfrage laden. 

1. Erstellen Sie eine neue SQL Server-Datenquelle. Die Eingabe ist eine Abfrage für die neue Tabelle, die Sie gerade erstellt und mit Daten geladen werden. Diese Definition fügt Faktorebenen für die *DayOfWeek* Spalte mit der *ColInfo* Argument **RxSqlServerData**.
  
    ```R
    sqlServerAirDemo2 <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
2. Rufen Sie **RxSummary** noch einmal, um eine Zusammenfassung der Daten in der Abfrage zu überprüfen.
  
    ```R
    rxSummary(~., data = sqlServerAirDemo2)
    ```

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Blockweises Analysieren mithilfe von rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)