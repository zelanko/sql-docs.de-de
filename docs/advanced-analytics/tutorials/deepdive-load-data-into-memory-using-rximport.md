---
title: Laden von Daten in den Arbeitsspeicher mit RxImport von RevoScaleR - SQL Server-Machine Learning
description: Exemplarische Vorgehensweise im Lernprogramm zum Laden von Daten, die Verwendung der Sprache R auf SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 53d13c0771fd06ae8e91f4ad69fe4646a01fc770
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962225"
---
# <a name="load-data-into-memory-using-rximport-sql-server-and-revoscaler-tutorial"></a>Laden von Daten in den Arbeitsspeicher mit RxImport (SQL Server und die RevoScaleR-Lernprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil der [RevoScaleR Tutorial](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Die [RxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) Funktion kann verwendet werden, um Daten aus einer Datenquelle in einen Datenrahmen im Arbeitsspeicher der Sitzung oder in eine XDF-Datei auf dem Datenträger zu verschieben. Wenn Sie keine Datei als Ziel angeben, werden die Daten als Datenrahmen in den Arbeitsspeicher abgelegt.

In diesem Schritt erfahren Sie, wie zum Abrufen von Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und verwenden Sie dann die **RxImport** Funktion, um die relevanten Daten in einer lokalen Datei abzulegen. Auf diese Weise können Sie sie wiederholt im lokalen Computekontext analysieren, ohne die Datenbank erneut abfragen zu müssen.

## <a name="extract-a-subset-of-data-from-sql-server-to-local-memory"></a>Extrahieren einer Teilmenge von Daten aus SQL Server in den lokalen Arbeitsspeicher

Sie haben sich entschieden, dass Sie nur die hochrisiko-Personen genauer untersuchen möchten. Die Quelltabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist groß, daher sollten Sie die Informationen über die nur die hochrisiko-Kunden erhalten. Klicken Sie dann laden Sie die Daten in einen Datenrahmen im Arbeitsspeicher der lokalen Arbeitsstation.

1. Setzen Sie den Computekontext zurück auf die lokale Arbeitsstation.

    ```R
    rxSetComputeContext("local")
    ```

2. Erstellen Sie ein neues SQL Server-Datenquellenobjekt, indem Sie eine gültige SQL­-Anweisung im *sqlQuery* -Parameter bereitstellen. In diesem Beispiel wird eine Teilmenge der Beobachtungen mit den höchsten Risikobewertungen abgerufen. Auf diese Weise werden nur die wirklich benötigten Daten im lokalen Arbeitsspeicher abgelegt.

    ```R
    sqlServerProbDS \<- RxSqlServerData(
        sqlQuery = paste("SELECT * FROM ccScoreOutput2",
        "WHERE (ccFraudProb > .99)"),
        connectionString = sqlConnString)
    ```

3. Rufen Sie die Funktion [RxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) zum Lesen der Daten in einen Datenrahmen in der lokalen R-Sitzung.

    ```R
    highRisk <- rxImport(sqlServerProbDS)
    ```

    Wenn der Vorgang erfolgreich war, sehen Sie eine Statusmeldung wie die folgende: "Gelesene Zeilen: 35, total Zeilen verarbeitet: 35, total Chunk Time: 0.036 Seconds"

4. Nun, dass die hochrisiko-Beobachtungen in einen Datenrahmen im Arbeitsspeicher sind, können Sie verschiedene R-Funktionen, um den Datenrahmen zu bearbeiten. Sie können z. B. Kunden nach ihrer risikobewertung sortieren und gibt eine Liste der Kunden, die das größte Risiko darstellen.

    ```R
    orderedHighRisk <- highRisk[order(-highRisk$ccFraudProb),]
    row.names(orderedHighRisk) <- NULL
    head(orderedHighRisk)
    ```

**Ergebnisse**

```R
ccFraudLogitScore   state gender cardholder balance numTrans numIntlTrans creditLine ccFraudProb1
9.786345    SD   Male  Principal   23456       25            5 75   0.99994382
9.433040    FL Female  Principal   20629       24           28 75   0.99992003
8.556785    NY Female  Principal   19064       82           53 43   0.99980784
8.188668    AZ Female  Principal   19948       29            0 75   0.99972235
7.551699    NY Female  Principal   11051       95            0 75   0.99947516
7.335080    NV   Male  Principal   21566        4            6  75   0.9993482
```

## <a name="more-about-rximport"></a>Weitere Informationen zu rxImport

Sie können **rxImport** nicht nur zum Verschieben von Daten verwenden, sondern auch, um Daten während des Auslesens zu transformieren. Beispielsweise können Sie die Anzahl von Zeichen für Spalten mit fester Breite angeben, eine Beschreibung der Variablen bereitstellen, Ebenen für Faktorspalten festlegen und sogar neue Ebenen für die Verwendung nach dem Import erstellen.

Die **RxImport** Funktion weist Variablennamen auf die Spalten während des Importvorgangs, aber Sie können neue Variablennamen angeben, mit der *ColInfo* Parameter oder Datentypen ändern, die mit der *ColClasses* Parameter.

Durch die Angabe zusätzlicher Vorgänge im Parameter *transforms* können Sie jeden Datenblock, der gelesen wird, elementar verarbeiten.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen einer neuen SQL Server-Tabelle mit rxDataStep](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)