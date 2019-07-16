---
title: Transformieren von Daten mithilfe von RxDataStep von RevoScaleR - SQL Server-Machine Learning
description: Exemplarische Vorgehensweise im Lernprogramm zum Transformieren von Daten, die Verwendung der Sprache R auf SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0da478798e87497da7828126b2168bbae5d980f7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962176"
---
# <a name="transform-data-using-r-sql-server-and-revoscaler-tutorial"></a>Transformieren von Daten mithilfe von R (SQL Server und die RevoScaleR-Lernprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil der [RevoScaleR Tutorial](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In dieser Lektion erfahren Sie mehr über die **RevoScaleR** Funktionen zum Transformieren von Daten in verschiedenen Phasen der Analyse.

> [!div class="checklist"]
> * Verwendung **RxDataStep** zum Erstellen und eine Datenteilmenge zu transformieren
> * Verwendung **RxImport** zum Transformieren von bei der Übertragung von Daten in oder aus einer XDF-Datei oder einen in-Memory-Datenrahmen während des Imports

Obwohl die Funktionen **rxSummary**, **rxCube**, **rxLinMod**und **rxLogit** nicht speziell für die Datenverschiebung vorgesehen sind, unterstützen sie jedoch alle dynamische Datentransformationen.

## <a name="use-rxdatastep-to-transform-variables"></a>Verwenden von RxDataStep zum Transformieren von Variablen

Die Funktion [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) verarbeitet Daten abschnittsweise und liest aus einer Datenquelle und schreibt in eine andere. Sie können die Spalten angeben, die transformiert werden sollen, die zu ladenden Transformationen usw.

Um dieses Beispiel interessant zu machen, verwenden Sie wir eine Funktion aus einem anderen R-Paket zum Transformieren der Daten. Das Paket **boot** stellt eines der „empfohlenen“ Pakete dar, was bedeutet, dass **Start** in jeder Verteilung von R enthalten ist, jedoch nicht automatisch beim Starten geladen wird. Aus diesem Grund das Paket muss bereits zur Verfügung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz, für die R-Integration konfiguriert ist.

Von der **Boot** packen, verwenden Sie die Funktion **inv.logit**, die die Umkehrfunktion eines Logit berechnet. Das bedeutet, dass die Funktion **inv.logit** ein Logit zurück zu einer Wahrscheinlichkeit auf der Skala [0,1] konvertiert.

> [!TIP] 
> Eine andere Möglichkeit, Vorhersagen auf dieser Skala zu erhalten, wäre den Parameter *type* auf **response** im ursprünglichen Aufruf von **rxPredict**festzulegen.

1. Zunächst erstellen Sie eine Datenquelle aus, um die Daten für die Tabelle `ccScoreOutput`.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. Hinzufügen einer anderen Datenquelle zum Speichern der Daten für die Tabelle `ccScoreOutput2`.
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    In der neuen Tabelle speichern Sie alle Variablen aus dem vorherigen `ccScoreOutput` Tabelle sowie die neu erstellte Variable.
  
3. Legen Sie den Computekontext auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz fest.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Verwenden Sie die Funktion **RxSqlServerTableExists** um zu überprüfen, ob die Ausgabetabelle `ccScoreOutput2` bereits vorhanden ist und wenn dies der Fall ist, verwenden Sie die Funktion **RxSqlServerDropTable** auf die Tabelle zu löschen.
  
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

    Wenn Sie die Transformationen definieren, die für die einzelnen Spalten angewendet werden, können Sie auch alle zusätzlichen R-Pakete angeben, die für die Durchführung der Transformationen notwendig sind.  Weitere Informationen zu den Arten von Transformationen, die Sie ausführen können, finden Sie unter [transformieren und die Teilmenge von Daten mithilfe von RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-transform).
  
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

Beachten Sie, die die faktorvariablen auf die Tabelle geschrieben wurden `ccScoreOutput2` als Zeichendaten. Um diese als Faktoren in nachfolgenden Analysen zu verwenden, geben Sie die Ebenen mit dem Parameter *colInfo* an.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Laden von Daten in den Arbeitsspeicher mit rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)