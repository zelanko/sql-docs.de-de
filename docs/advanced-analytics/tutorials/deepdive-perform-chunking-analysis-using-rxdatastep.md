---
title: Blockweises mithilfe von RxDataStep von RevoScaleR - SQL Server-Machine Learning
description: Exemplarische Vorgehensweise im Lernprogramm zum Aufteilen von Daten für die verteilte Analyse, die Verwendung der Sprache R auf SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c5d3b50af1f7db3a39dec0e475aa00582bc77e0a
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596031"
---
# <a name="perform-chunking-analysis-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Blockweises mithilfe von RxDataStep (SQL Server und die RevoScaleR-Lernprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil der [RevoScaleR Tutorial](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In dieser Lektion verwenden Sie die **RxDataStep** zum Verarbeiten von Daten in Blöcken von Funktion, statt Sie zu erfordern, dass das gesamte Dataset in den Arbeitsspeicher geladen und gleichzeitig ausführen möchten, wie in r traditionell der Fall verarbeitet werden Die **RxDataStep** Funktionen liest die Daten im Segment, gilt R-Funktionen für jeden Datenblock wiederum und speichert dann die Ergebnisse der Zusammenfassung für jeden Block in eine allgemeine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenquelle. Wenn alle Daten gelesen wurden, werden die Ergebnisse kombiniert.

> [!TIP]
> In dieser Lektion berechnen Sie eine kontingenztafel mithilfe der **Tabelle** -Funktion in R. In diesem Beispiel dient nur zu Lehrzwecken. 
> 
> Wenn Sie reale Datensätze tabellarisch ordnen müssen, sollten Sie verwenden die **RxCrossTabs** oder **RxCube** -Funktionen in **RevoScaleR**, optimiert sind für diese Art von der Vorgang.

## <a name="partition-data-by-values"></a>Partitionieren von Daten nach Werten

1. Erstellen Sie eine benutzerdefinierte R-Funktion, die R aufruft **Tabelle** -Funktion für jeden Datenblock, und nennen Sie die neue Funktion **ProcessChunk**.
  
    ```R
    ProcessChunk <- function( dataList) {
    # Convert the input list to a data frame and compute contingency table
    chunkTable <- table(as.data.frame(dataList))
  
    # Convert table output to a data frame with a single row
    varNames <- names(chunkTable)
    varValues <- as.vector(chunkTable)
    dim(varValues) <- c(1, length(varNames))
    chunkDF <- as.data.frame(varValues)
    names(chunkDF) <- varNames
  
    # Return the data frame, which has a single row
    return( chunkDF )
    }
    ```

2. Legen Sie den Computekontext auf den Server fest.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
3. Definieren Sie eine SQL Server-Datenquelle zum Speichern der Daten, die Sie verarbeiten können. Beginnen Sie, indem Sie einer Variablen eine SQL-Abfrage zuweisen. Verwenden Sie dann die Variable in der *SqlQuery* Argument einer neuen SQL Server-Datenquelle.
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```

4. Sie können optional ausführen **RxGetVarInfo** für diese Datenquelle. An diesem Punkt enthält es eine einzelne Spalte: *Var 1: DayOfWeek, Type: Factor, keine Faktorebenen verfügbar*
     
5. Erstellen Sie vor dem Anwenden dieser Faktorvariablen auf die Quelldaten eine separate Tabelle für die Zwischenergebnisse. In diesem Fall verwenden Sie einfach die **RxSqlServerData** Funktion zum Definieren der Daten, sodass Sie sicher, dass alle vorhandenen Tabellen mit demselben Namen zu löschen.
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  Rufen Sie die benutzerdefinierte Funktion **ProcessChunk** zum Transformieren der Daten, wie sie durch die Verwendung als gelesen wird, die *TransformFunc* Argument für die **RxDataStep** Funktion.
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  Um Zwischenergebnisse von anzuzeigen **ProcessChunk**, weisen Sie die Ergebnisse der **RxImport** auf eine Variable, und klicken Sie dann die Ergebnisse an die Konsole ausgegeben.
  
    ```R
    iroResults <- rxImport(iroDataSource)
    iroResults
    ```

    **Teilergebnisse**

    |      |    1  |   2   |  3   |  4   |  5  |   6   |  7 |
    | --- | ---  | --- | ---  |  ---  | ---  | ---  | --- |
    | 1 | 8228 | 8924 | 6916 | 6932 | 6944 | 5602 | 6454 |
    | 2  | 8321  | 5351 | 7329 | 7411 | 7409 | 6487 | 7692 |

9. Summieren Sie die Spalten, und zeigen Sie die Ergebnisse in der Konsole an, um die Endergebnisse aller Blöcke zu berechnen.

    ```R
    finalResults <- colSums(iroResults)
    finalResults
    ```

    **Ergebnisse**

    1  |   2  |   3  |   4  |   5  |   6  |   7
    ---  |   ---  |   ---  |   ---  |   ---  |   ---  |   ---
    97975 | 77725 | 78875 | 81304 | 82987 | 86159 | 94975 

10. Um die Tabelle mit Zwischenergebnissen zu entfernen, stellen Sie einen Aufruf von **RxSqlServerDropTable**.
  
    ```R
    rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString)
    ```

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [R-Tutorials für SQL Server](sql-server-r-tutorials.md)