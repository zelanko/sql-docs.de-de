---
title: Erstellen von mehreren Modellen mit rxExecBy
description: Verwenden Sie die rxexecby-Funktion aus der revoscaler-Bibliothek, um mehrere Mini Modelle auf den in SQL Server gespeicherten Computer Daten zu erstellen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1b2e6e1d546b9bbd1b3b3196c37716acbbe0ae74
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715712"
---
# <a name="creating-multiple-models-using-rxexecby"></a>Erstellen von mehreren Modellen mit rxExecBy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die **rxexecby** -Funktion in revoscaler unterstützt die parallele Verarbeitung von mehreren verbundenen Modellen. Anstatt ein großes Modell auf der Grundlage von Daten aus mehreren ähnlichen Entitäten zu trainieren, kann ein Daten Analyst schnell viele verwandte Modelle erstellen, die jeweils spezifische Daten für eine einzelne Entität verwenden. 

Nehmen Sie beispielsweise an, dass Sie Geräteausfälle überwachen und Daten für viele verschiedene Arten von Geräten erfassen. Mithilfe von rxexecby können Sie ein einzelnes großes Dataset als Eingabe bereitstellen, eine Spalte angeben, für die das DataSet gestrachtet werden soll, z. b. den Gerätetyp, und dann mehrere Modelle für einzelne Geräte erstellen.

Dieser Anwendungsfall wurde als ["angenehm parallel"](https://en.wikipedia.org/wiki/Embarrassingly_parallel) bezeichnet, da er große komplizierte Probleme in Komponenten Teile für die gleichzeitige Verarbeitung unterbricht.

Typische Anwendungen dieses Ansatzes sind die Vorhersagen für einzelne Haushalts-smartmeter, das Erstellen von Umsatzprognosen für separate Produktlinien oder das Erstellen von Modellen für Kredit Genehmigungen, die auf einzelne Bank branches zugeschnitten sind.

## <a name="how-rxexec-works"></a>Funktionsweise von rxexec

Die rxexecby-Funktion in revoscaler ist für die parallele Verarbeitung mit hohem Volumen über eine große Anzahl kleiner Datasets konzipiert.

1. Die Funktion rxexecby wird als Teil des R-Codes aufgerufen, und ein DataSet mit unsortierter Daten wird übergeben.
2. Geben Sie die Partition an, nach der die Daten gruppiert und sortiert werden sollen.
3. Hiermit wird eine Transformation oder Modellierungs Funktion definiert, die auf jede Daten Partition angewendet werden soll.
4. Wenn die Funktion ausgeführt wird, werden die Daten Abfragen parallel verarbeitet, wenn Sie von Ihrer Umgebung unterstützt werden. Außerdem werden die Modellierungs-oder Transformations Aufgaben zwischen einzelnen Kernen verteilt und parallel ausgeführt. Unterstützte computekontext für Vorgänge sind rxspark und rxinsqlserver.
5. Es werden mehrere Ergebnisse zurückgegeben.

## <a name="rxexecby-syntax-and-examples"></a>rxexecby-Syntax und Beispiele

**rxexecby** nimmt vier Eingaben an, eine der Eingaben ist ein DataSet oder ein Datenquellen Objekt, das für eine angegebene **Schlüssel** Spalte partitioniert werden kann. Die-Funktion gibt eine Ausgabe für jede Partition zurück. Die Form der Ausgabe hängt von der Funktion ab, die als Argument weitergegeben wird. Wenn Sie z. b. eine Modellierungs Funktion wie rxlinmod übergeben, können Sie ein separates trainiertes Modell für jede Partition des Datasets zurückgeben.

### <a name="supported-functions"></a>Unterstützte Funktionen

Modellierung: `rxLinMod`, `rxLogit`, `rxGlm`,`rxDtree`

Bewertung: `rxPredict`,

Transformation oder Analyse:`rxCovCor`

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie mehrere Modelle mithilfe des Datasets für die Fluggesellschaft erstellt werden, das in der Spalte [DayOfWeek] partitioniert ist. Die benutzerdefinierte Funktion `delayFunc`wird auf jede Partition angewendet, indem rxexecby aufgerufen wird. Die-Funktion erstellt separate Modelle für Montag, Dienstag usw.

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

Wenn Sie den Fehler erhalten, `varsToPartition is invalid`überprüfen Sie, ob der Name der Schlüssel Spalte oder der Spalten ordnungsgemäß eingegeben wurde. Bei der Sprache R wird die Groß-/Kleinschreibung beachtet

Dieses spezielle Beispiel ist nicht für SQL Server optimiert, und Sie können in vielen Fällen eine bessere Leistung erzielen, indem Sie die Daten mithilfe von SQL gruppieren. Mithilfe von rxexecby können Sie jedoch parallele Aufträge aus R erstellen.

Das folgende Beispiel veranschaulicht den Prozess in R, wobei SQL Server als computekontext verwendet wird:

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


