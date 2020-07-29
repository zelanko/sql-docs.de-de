---
title: Erstellen von mehreren Modellen mit rxExecBy
description: Verwenden Sie die Funktion „rxExecBy“ aus der RevoScaleR-Bibliothek, um mehrere kleine Modelle aus den in SQL Server gespeicherte Computerdaten zu erstellen.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 04/15/2018
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f4f0da1fdee47d166fe1b06fd8ce6e8ddea64f4c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723852"
---
# <a name="creating-multiple-models-using-rxexecby"></a>Erstellen von mehreren Modellen mit rxExecBy
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Die Funktion **rxExecBy** in RevoScaleR unterstützt die Parallelverarbeitung von mehreren verwandten Modellen. Anstatt ein großes Modell auf der Grundlage von Daten aus mehreren ähnlichen Entitäten zu trainieren, kann ein Datenanalyst schnell viele verwandte Modelle erstellen, die jeweils spezifische Daten für eine einzelne Entität verwenden. 

Nehmen Sie beispielsweise an, dass Sie Geräteausfälle überwachen und Daten für viele verschiedene Arten von Geräten erfassen. Mithilfe von rxExecBy können Sie ein einzelnes großes Dataset als Eingabe bereitstellen, eine Spalte angeben, auf der das Dataset geschichtet wird (z. B. den Gerätetyp), und dann mehrere Modelle für einzelne Geräte erstellen.

Dieser Anwendungsfall wird als [angenehm parallel](https://en.wikipedia.org/wiki/Embarrassingly_parallel) bezeichnet, da er ein großes kompliziertes Problem in Einzelteile für die gleichzeitige Verarbeitung zerlegt.

Typische Anwendungen dieses Ansatzes sind Vorhersagen für einzelne intelligente Haushaltszähler, die Erstellung von Umsatzprognosen für einzelne Produktlinien oder die Erstellung von Modellen für Kreditgenehmigungen, die auf einzelne Bankfilialen zugeschnitten sind.

## <a name="how-rxexec-works"></a>Funktionsweise von rxExec

Die rxExecBy-Funktion in RevoScaleR ist für die Parallelverarbeitung mit hohem Volumen über eine große Anzahl kleiner Datasets konzipiert.

1. Rufen Sie die rxExecBy-Funktion als Teil des R-Codes auf, und übergeben Sie ein Dataset mit unsortierten Daten.
2. Geben Sie die Partition an, nach der die Daten gruppiert und sortiert werden sollen.
3. Definieren Sie eine Transformations- oder Modellierungsfunktion, die auf jede Datenpartition angewendet werden soll.
4. Beim Ausführen der Funktion werden die Datenabfragen parallel verarbeitet, wenn sie von Ihrer Umgebung unterstützt werden. Außerdem werden die Modellierungs- oder Transformationsaufgaben zwischen einzelnen Kernen verteilt und parallel ausgeführt. Unterstützte Computekontexte für die Vorgänge umfassen RxSpark und RxInSQLServer.
5. Es werden mehrere Ergebnisse zurückgegeben.

## <a name="rxexecby-syntax-and-examples"></a>rxExecBy-Syntax und Beispiele

**rxExecBy** benötigt vier Eingaben, wobei eine der Eingaben ein Dataset oder ein Datenquellenobjekt ist, das auf einer angegebenem **Schlüsselspalte** partitioniert werden kann. Die Funktion gibt für jede Partition eine Ausgabe zurück. Die Form der Ausgabe hängt von der Funktion ab, die als Argument weitergegeben wird. Wenn Sie z. B. eine Modellierungsfunktion wie rxLinMod übergeben, können Sie ein separates trainiertes Modell für jede Partition des Datasets zurückgeben.

### <a name="supported-functions"></a>Unterstützte Funktionen

Modellierung: `rxLinMod`, `rxLogit`, `rxGlm`, `rxDtree`

Bewertung: `rxPredict`

Transformation oder Analyse: `rxCovCor`

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie mehrere Modelle mithilfe des Airline-Datasets erstellt werden, das in der Spalte [DayOfWeek] partitioniert ist. Die benutzerdefinierte Funktion `delayFunc` wird durch Aufrufen von rxExecBy auf jede Partition angewendet. Die Funktion erstellt separate Modelle für Montag, Dienstag usw.

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

Wenn Sie den Fehler `varsToPartition is invalid` erhalten, überprüfen Sie, ob der Name der Schlüsselspalte oder -spalten ordnungsgemäß eingegeben wurde. Bei der R-Sprache wird Groß-/Kleinschreibung beachtet.

Dieses spezielle Beispiel ist nicht für SQL Server optimiert, und Sie können in vielen Fällen eine bessere Leistung erzielen, indem Sie die Daten mithilfe von SQL gruppieren. Mithilfe von rxExecBy können Sie jedoch parallele Aufträge aus R erstellen.

Das folgende Beispiel veranschaulicht den Prozess in R, wobei SQL Server als Computekontext verwendet wird:

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


