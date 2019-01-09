---
title: Erstellen von mehreren Modellen mit RxExecBy – SQL Server Machine Learning Services
description: Verwenden Sie die RxExecBy-Funktion von RevoScaleR-Bibliothek, um mehrere kleine Modelle in den Computerdaten in SQL Server zu erstellen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5d61d7fee7afbf28f4ef72b7ecbae02853f52d25
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645299"
---
# <a name="creating-multiple-models-using-rxexecby"></a>Erstellen von mehreren Modellen mit rxExecBy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Die **RxExecBy** -Funktion in RevoScaleR unterstützt die parallele Verarbeitung von mehrere zugehörige Modelle. Anstatt Train eines großen Modells auf der Grundlage von Daten aus mehreren ähnlich wie Entitäten, ein Data Scientist kann schnell erstellen viele Verwandte Modelle, von denen jeder Daten, die spezifisch für eine einzelne Entität. 

Nehmen wir beispielsweise an, dass Sie Gerätefehler, Erfassen von Daten für viele verschiedene Arten von Geräten überwachen. Mit RxExecBy, können Sie ein einzelnes großes Dataset als Eingabe bereitstellen, geben Sie eine Spalte, auf dem das Dataset, z. B. Gerätetyp stratify und erstellen Sie dann auf mehrere Modelle für die einzelnen Geräte.

In diesem Fall hat bezeichnet wurden ["pleasingly parallel"](https://en.wikipedia.org/wiki/Embarrassingly_parallel) da in Komponenten für die gleichzeitige Verarbeitung ein großes, komplizierten Problem beschädigt.

Typische Anwendungen dieses Ansatzes gehören Planung für einzelne household smart Meter, oder erstellen, basierenden Projektionen für separate Produktlinien Modelle für die Loan-Genehmigungen, die auf einzelne Bankfilialen zugeschnitten sind.

## <a name="how-rxexec-works"></a>Funktionsweise von rxExec

Die RxExecBy-Funktion in RevoScaleR dient für umfangreiche parallele Verarbeitung über eine große Anzahl von kleinen Datasets.

1. Sie rufen Sie die RxExecBy-Funktion als Teil des R-Code, und übergeben ein Dataset mit nicht sortierte Daten.
2. Geben Sie die Partition mit der die Daten gruppiert und sortiert werden soll.
3. Definieren Sie eine Transformation oder Modellierung von Funktion, die auf jede Datenpartition angewendet werden soll
4. Wenn die Funktion ausgeführt wird, werden die Datenabfragen parallel ausgeführt, wenn Ihre Umgebung unterstützt. Darüber hinaus sind die Modellierung oder Transformation Aufgaben auf einzelnen Kerne verteilt und parallel ausgeführt. Unterstützte computekontext für drei Vorgänge umfassen RxSpark und RxInSQLServer.
5. Es werden mehrere Ergebnisse zurückgegeben.

## <a name="rxexecby-syntax-and-examples"></a>RxExecBy Syntax und Beispiele

**RxExecBy** akzeptiert vier Eingaben, eine der Eingaben wird ein Dataset oder einem Quell-Objekt, das partitioniert werden kann für ein bestimmtes **Schlüssel** Spalte. Die Funktion gibt eine Ausgabe für jede Partition an. Die Form der Ausgabe hängt von der Funktion, die als Argument übergeben wird. Wenn Sie eine Modellierung-Funktion, z. B. RxLinMod übergeben haben, könnten Sie z. B. ein separates trainiertes Modell für jede Partition des Datasets zurückgeben.

### <a name="supported-functions"></a>Unterstützte Funktionen

Modeling: `rxLinMod`, `rxLogit`, `rxGlm`, `rxDtree`

Bewertung: `rxPredict`,

Transformation "oder" Analyse ": `rxCovCor`

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht das Erstellen mehrerer Modelle, die über das Fluglinien-Dataset, das für die Spalte [-DayOfWeek] partitioniert ist. Die benutzerdefinierte Funktion `delayFunc`, auf die Partitionen aufrufende RxExecBy angewendet wird. Die Funktion erstellt separate Modelle für jeden zweiten Montag, Dienstag, und so weiter.

```sql
EXEC sp_execute_external_script
@language = N'R'
, @script = N'
delayFunc <- function(key, data, params) { 
    df <- rxImport(inData = airlineData) 
    rxLinMod(ArrDelay ~ CRSDepTime, data = df) 
} 
OutputDataSet <- rxExecBy(airlineData, c("DayOfWeek"), delayFunc)
'
, @input_data_1 = N'select ArrDelay, DayOfWeek, CRSDepTime from AirlineDemoSmall]'
, @input_data_1_name = N'airlineData'

```

Wenn Sie die Fehlermeldung `varsToPartition is invalid`, überprüfen Sie, ob der Name der Spalte oder Spalten richtig eingegeben wurde. Die Sprache R ist die Groß-/Kleinschreibung beachtet.

Dieses Beispiel ist für SQL Server nicht optimiert, und Sie können in vielen Fällen eine bessere Leistung, zum Gruppieren der Daten mithilfe von SQL. Allerdings können mit RxExecBy können Sie parallele Aufträge von r erstellen

Das folgende Beispiel veranschaulicht den Prozess in R, SQL Server als Compute Context verwenden:

```R
sqlServerConnString <- "SERVER=hostname;DATABASE=TestDB;UID=DBUser;PWD=Password;"
inTable <- paste("airlinedemosmall")
sqlServerDataDS <- RxSqlServerData(table = inTable, connectionString = sqlServerConnString)

# user function
".Count" <- function(keys, data, params)
{
  myDF <- rxImport(inData = data)
  return (nrow(myDF))
}

# Set SQL Server compute context with level of parallelism = 2
sqlServerCC <- RxInSqlServer(connectionString = sqlServerConnString, numTasks = 4)
rxSetComputeContext(sqlServerCC)

# Execute rxExecBy in SQL Server compute context
sqlServerCCResults <- rxExecBy(inData = sqlServerDataDS, keys = c("DayOfWeek"), func = .Count)
```


