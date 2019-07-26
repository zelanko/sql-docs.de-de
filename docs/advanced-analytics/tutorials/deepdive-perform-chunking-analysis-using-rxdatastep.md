---
title: Durchführen der Segmentierungs Analyse mithilfe von revoscaler rxdatastep
description: 'Tutorial: Exemplarische Vorgehensweise zum Segmentieren von Daten für die verteilte Analyse mithilfe der Programmiersprache R auf SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 3aa0b42c9806e8d8972f31c69b1b33b222c43287
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469706"
---
# <a name="perform-chunking-analysis-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Durchführen einer Block enden Analyse mithilfe von rxdatastep (SQL Server-und revoscaler-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Diese Lektion ist Teil des [revoscaler-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In dieser Lektion verwenden Sie die **rxdatastep** -Funktion, um Daten in Blöcken zu verarbeiten, anstatt zu verlangen, dass das gesamte Dataset in den Arbeitsspeicher geladen und gleichzeitig verarbeitet wird, wie bei herkömmlichem R. Die **rxdatastep** -Funktionen liest die Daten in Block, wendet R-Funktionen auf jeden Datenblock an und speichert dann die Zusammenfassungs Ergebnisse für jeden Block in einer allgemeinen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquelle. Wenn alle Daten gelesen wurden, werden die Ergebnisse kombiniert.

> [!TIP]
> In dieser Lektion berechnen Sie mithilfe der **Table** -Funktion in R eine notfalltabelle. Dieses Beispiel ist nur für Unterrichtszwecke gedacht. 
> 
> Wenn Sie in der Lage sein müssen, reale Datasets zu verwenden, empfiehlt es sich, die Funktionen **rxcrostabs** oder **rxcube** in **revoscaler**zu verwenden, die für diese Art von Vorgang optimiert sind.

## <a name="partition-data-by-values"></a>Partitionieren von Daten nach Werten

1. Erstellen Sie eine benutzerdefinierte r-Funktion, die die r- **Tabellen** Funktion für jeden Datenblock aufruft, und benennen Sie die neue Funktion **processchunk**.
  
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
  
3. Definieren Sie eine SQL Server Datenquelle zum Speichern der Daten, die Sie verarbeiten. Beginnen Sie, indem Sie einer Variablen eine SQL-Abfrage zuweisen. Verwenden Sie diese Variable dann im *sqlQuery* -Argument einer neuen SQL Server Datenquelle.
  
    ```R
    dayQuery <-  "SELECT DayOfWeek FROM AirDemoSmallTest"
    inDataSource <- RxSqlServerData(sqlQuery = dayQuery,
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",
            levels = as.character(1:7))))
    ```

4. Optional können Sie **rxgetvarinfo** für diese Datenquelle ausführen. An dieser Stelle enthält Sie eine einzelne Spalte: *Var 1: Dayoatweek, Typ: Faktor, keine Faktor Ebenen verfügbar*
     
5. Erstellen Sie vor dem Anwenden dieser Faktorvariablen auf die Quelldaten eine separate Tabelle für die Zwischenergebnisse. Auch hier verwenden Sie die Funktion **rxsqlserverdata** , um die Daten zu definieren, um sicherzustellen, dass alle vorhandenen Tabellen mit demselben Namen gelöscht werden.
  
    ```R
    iroDataSource = RxSqlServerData(table = "iroResults",   connectionString = sqlConnString)
    # Check whether the table already exists.
    if (rxSqlServerTableExists(table = "iroResults",  connectionString = sqlConnString))  { rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString) }
    ```
  
7.  Aufrufen der benutzerdefinierten Funktion **processchunk** , um die zu lesenden Daten zu transformieren, indem Sie als *transformfunc* -Argument für die **rxdatastep** -Funktion verwendet werden.
  
    ```R
    rxDataStep( inData = inDataSource, outFile = iroDataSource, transformFunc = ProcessChunk, overwrite = TRUE)
    ```
  
8.  Um die Zwischenergebnisse von **processchunk**anzuzeigen, weisen Sie die Ergebnisse von **rximport** einer Variablen zu, und geben Sie dann die Ergebnisse an die Konsole aus.
  
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

10. Um die Tabelle mit den Zwischenergebnissen zu entfernen, führen Sie einen Aufrufe von **rxsqlserverdroptable**aus.
  
    ```R
    rxSqlServerDropTable( table = "iroResults", connectionString = sqlConnString)
    ```

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [R-Tutorials für SQL Server](sql-server-r-tutorials.md)