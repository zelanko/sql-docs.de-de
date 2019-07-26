---
title: Transformieren von Daten mithilfe von revoscaler rxdatastep
description: 'Tutorial: Exemplarische Vorgehensweise zum Transformieren von Daten mit der Sprache R auf SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 752202a50222b67af659408c259ce29d9c65d703
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469763"
---
# <a name="transform-data-using-r-sql-server-and-revoscaler-tutorial"></a>Transformieren von Daten mithilfe von R (SQL Server-und revoscaler-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Diese Lektion ist Teil des [revoscaler-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In dieser Lektion erfahren Sie mehr über die **revoscaler** -Funktionen zum Transformieren von Daten in verschiedenen Phasen der Analyse.

> [!div class="checklist"]
> * Verwenden von **rxdatastep** zum Erstellen und Transformieren einer Daten Teilmenge
> * Verwenden von **rximport** zum Transformieren von Daten während der Übertragung in oder aus einer Xdf-Datei oder einem Datenrahmen im Arbeitsspeicher während des Imports

Obwohl die Funktionen **rxSummary**, **rxCube**, **rxLinMod**und **rxLogit** nicht speziell für die Datenverschiebung vorgesehen sind, unterstützen sie jedoch alle dynamische Datentransformationen.

## <a name="use-rxdatastep-to-transform-variables"></a>Verwenden von rxdatastep zum Transformieren von Variablen

Die Funktion [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) verarbeitet Daten abschnittsweise und liest aus einer Datenquelle und schreibt in eine andere. Sie können die Spalten angeben, die transformiert werden sollen, die zu ladenden Transformationen usw.

Um dieses Beispiel interessant zu machen, verwenden wir eine Funktion aus einem anderen R-Paket, um die Daten zu transformieren. Das Paket **boot** stellt eines der „empfohlenen“ Pakete dar, was bedeutet, dass **Start** in jeder Verteilung von R enthalten ist, jedoch nicht automatisch beim Starten geladen wird. Daher sollte das Paket bereits auf der Instanz verfügbar sein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die für die R-Integration konfiguriert ist.

Verwenden Sie aus dem **Start** Paket die Funktion **Inv. Logit**, die die Umkehrung einer Logit berechnet. Das bedeutet, dass die Funktion **inv.logit** ein Logit zurück zu einer Wahrscheinlichkeit auf der Skala [0,1] konvertiert.

> [!TIP] 
> Eine andere Möglichkeit, Vorhersagen auf dieser Skala zu erhalten, wäre den Parameter *type* auf **response** im ursprünglichen Aufruf von **rxPredict**festzulegen.

1. Erstellen Sie zunächst eine Datenquelle, die die für die Tabelle `ccScoreOutput`vorgesehenen Daten enthält.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. Fügen Sie eine weitere Datenquelle hinzu, die die Daten `ccScoreOutput2`für die Tabelle enthält.
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    Speichern Sie in der neuen Tabelle alle Variablen aus der vorherigen `ccScoreOutput` Tabelle sowie die neu erstellte Variable.
  
3. Legen Sie den Computekontext auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz fest.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Verwenden Sie die Funktion **rxsqlservertableist** , um zu überprüfen `ccScoreOutput2` , ob die Ausgabe Tabelle bereits vorhanden ist. wenn dies der Fall ist, verwenden Sie die Funktion **rxsqlserverdroptable** , um die Tabelle zu löschen.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput2"))     rxSqlServerDropTable("ccScoreOutput2")
    ```
  
5. Rufen Sie die Funktion **rxDataStep** auf, und geben Sie die gewünschten Transformationen in einer Liste an.
  
    ```R
    rxDataStep(inData = sqlOutScoreDS,
        outFile = sqlOutScoreDS2,
        transforms = list(ccFraudProb = inv.logit(ccFraudLogitScore)),
        transformPackages = "boot",
        overwrite = TRUE)
    ```

    Wenn Sie die Transformationen definieren, die für die einzelnen Spalten angewendet werden, können Sie auch alle zusätzlichen R-Pakete angeben, die für die Durchführung der Transformationen notwendig sind.  Weitere Informationen zu den Arten von Transformationen, die Sie ausführen können, finden Sie unter [transformieren und unterteilen von Daten mithilfe von revoscaler](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-transform).
  
6. Rufen Sie **rxGetVarInfo** auf, um eine Zusammenfassung der Variablen im neuen Dataset anzuzeigen.
  
```R
rxGetVarInfo(sqlOutScoreDS2)
```

**Ergebnisse**

```R
Var 1: ccFraudLogitScore, Type: numeric
Var 2: state, Type: character
Var 3: gender, Type: character
Var 4: cardholder, Type: character
Var 5: balance, Type: integer
Var 6: numTrans, Type: integer
Var 7: numIntlTrans, Type: integer
Var 8: creditLine, Type: integer
Var 9: ccFraudProb, Type: numeric
```

Die ursprünglichen Logit-Ergebnisse werden beibehalten, jedoch wurde eine neue Spalte, *ccFraudProb*, hinzugefügt, in der die Logit-Ergebnisse als Werte zwischen 0 und 1 dargestellt sind.

Beachten Sie, dass die Faktor Variablen als Zeichendaten in `ccScoreOutput2` die Tabelle geschrieben wurden. Um diese als Faktoren in nachfolgenden Analysen zu verwenden, geben Sie die Ebenen mit dem Parameter *colInfo* an.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Laden von Daten in den Arbeitsspeicher mit rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)