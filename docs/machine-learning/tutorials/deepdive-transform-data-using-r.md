---
title: Transformieren von Daten mithilfe von RevoScaleR
description: 'Tutorial 9 zu RevoScaleR: Transformieren von Daten mithilfe der R-Programmiersprache in SQL Server'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 03f8b3f9cacd4faa77116cd560abfdb81596d074
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "81116733"
---
# <a name="transform-data-using-r-sql-server-and-revoscaler-tutorial"></a>Transformieren von Daten mithilfe von R (Tutorial zu SQL Server und RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Bei diesem Tutorial handelt es sich um das 9. Tutorial der [Tutorialreihe zu RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md). In diesem Tutorial erfahren Sie, wie Sie [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server verwenden.

In diesem Tutorial lernen Sie die **RevoScaleR**-Funktionen zum Transformieren von Daten in verschiedenen Phasen Ihrer Analyse kennen.

> [!div class="checklist"]
> * Verwenden von **rxDataStep** zur Erstellung und Transformation einer Datenteilmenge
> * Verwenden von **rxImport**, um während des Imports in der Übertragung befindliche Daten in oder aus einer XDF-Datei oder einem In-Memory-Datenrahmen zu transformieren

Obwohl die Funktionen **rxSummary**, **rxCube**, **rxLinMod**und **rxLogit** nicht speziell für die Datenverschiebung vorgesehen sind, unterstützen sie jedoch alle dynamische Datentransformationen.

## <a name="use-rxdatastep-to-transform-variables"></a>Verwenden von rxDataStep zum Transformieren von Variablen

Die Funktion [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) verarbeitet Daten abschnittsweise und liest aus einer Datenquelle und schreibt in eine andere. Sie können die Spalten angeben, die transformiert werden sollen, die zu ladenden Transformationen usw.

Wir verwenden eine Funktion aus einem anderen R-Paket zum Transformieren der Daten, um dieses Beispiel interessant zu gestalten. Das Paket **boot** stellt eines der „empfohlenen“ Pakete dar, was bedeutet, dass **Start** in jeder Verteilung von R enthalten ist, jedoch nicht automatisch beim Starten geladen wird. Aus diesem Grund sollte das Paket schon auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz verfügbar sein, die für die R-Integration konfiguriert ist.

Verwenden Sie aus dem Paket **boot** die Funktion **inv.logit**, die die Umkehrfunktion eines Logit berechnet. Das bedeutet, dass die Funktion **inv.logit** ein Logit zurück zu einer Wahrscheinlichkeit auf der Skala [0,1] konvertiert.

> [!TIP] 
> Eine andere Möglichkeit, Vorhersagen auf dieser Skala zu erhalten, wäre den Parameter *type* auf **response** im ursprünglichen Aufruf von **rxPredict**festzulegen.

1. Erstellen Sie zunächst eine Datenquelle, die die Daten aufnimmt, die für die Tabelle `ccScoreOutput` bestimmt sind.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. Fügen Sie eine weitere Datenquelle hinzu, um die Daten für die Tabelle `ccScoreOutput2` aufzunehmen.
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    Speichern Sie alle Variablen aus der vorherigen `ccScoreOutput`-Tabelle sowie die neu erstellte Variable in der neuen Tabelle.
  
3. Legen Sie den Computekontext auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz fest.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Verwenden Sie die Funktion **rxSqlServerTableExists**, um zu überprüfen, ob die Ausgabetabelle `ccScoreOutput2` bereits vorhanden ist, und verwenden Sie, falls dies der Fall ist, die Funktion **rxSqlServerDropTable** zum Löschen der Tabelle.
  
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

    Wenn Sie die Transformationen definieren, die für die einzelnen Spalten angewendet werden, können Sie auch alle zusätzlichen R-Pakete angeben, die für die Durchführung der Transformationen notwendig sind.  Weitere Informationen zu den Arten von Transformationen, die Sie ausführen können, finden Sie unter [Vorgehensweise beim Transformieren von Datenteilmengen mithilfe von RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-transform).
  
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

Beachten Sie, dass die Faktorvariablen als Zeichendaten in die Tabelle `ccScoreOutput2` geschrieben wurden. Um diese als Faktoren in nachfolgenden Analysen zu verwenden, geben Sie die Ebenen mit dem Parameter *colInfo* an.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Laden von Daten in den Arbeitsspeicher mit rxImport](../../machine-learning/tutorials/deepdive-load-data-into-memory-using-rximport.md)