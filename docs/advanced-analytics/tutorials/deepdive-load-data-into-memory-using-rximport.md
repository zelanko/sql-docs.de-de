---
title: Laden von Daten in den Arbeitsspeicher mithilfe von revoscaler rximport
description: 'Tutorial: Exemplarische Vorgehensweise zum Laden von Daten mit der Sprache R auf SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 6e7e986b3d0ebd21527d730cb5b4bd5fa60d1c4f
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469733"
---
# <a name="load-data-into-memory-using-rximport-sql-server-and-revoscaler-tutorial"></a>Laden von Daten in den Arbeitsspeicher mit rximport (SQL Server-und revoscaler-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Diese Lektion ist Teil des [revoscaler-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Die [rximport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) -Funktion kann verwendet werden, um Daten aus einer Datenquelle in einen Datenrahmen im Sitzungs Speicher oder in eine Xdf-Datei auf einem Datenträger zu verschieben. Wenn Sie keine Datei als Ziel angeben, werden die Daten als Datenrahmen in den Arbeitsspeicher abgelegt.

In diesem Schritt erfahren Sie, wie Sie Daten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erhalten und dann die **rximport** -Funktion verwenden, um die zu überwachenden Daten in einer lokalen Datei zu platzieren. Auf diese Weise können Sie sie wiederholt im lokalen Computekontext analysieren, ohne die Datenbank erneut abfragen zu müssen.

## <a name="extract-a-subset-of-data-from-sql-server-to-local-memory"></a>Extrahieren einer Teilmenge der Daten aus SQL Server in den lokalen Arbeitsspeicher

Sie haben sich entschieden, nur die Hochrisiko-Einzelpersonen genauer zu untersuchen. Die Quell Tabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist groß, sodass Sie nur die Informationen zu den Kunden mit hohem Risiko erhalten möchten. Anschließend laden Sie diese Daten in einen Datenrahmen im Arbeitsspeicher der lokalen Arbeitsstation.

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

3. Ruft die Funktion [rximport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) auf, um die Daten in einem Datenrahmen in der lokalen R-Sitzung zu lesen.

    ```R
    highRisk <- rxImport(sqlServerProbDS)
    ```

    Wenn der Vorgang erfolgreich war, sollte eine Statusmeldung wie die folgende angezeigt werden: "Gelesene Zeilen: 35, verarbeitete Zeilen gesamt: 35, gesamte Segment Zeit: 0,036 Sekunden "

4. Nachdem sich die Beobachtungen mit hohem Risiko in einem Datenrahmen im Arbeitsspeicher befinden, können Sie verschiedene R-Funktionen verwenden, um den Datenrahmen zu bearbeiten. Beispielsweise können Sie Kunden nach ihrer Risikobewertung sortieren und eine Liste der Kunden drucken, die das größte Risiko darstellen.

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

Die **rximport** -Funktion weist den Spalten während des Import Vorgangs Variablennamen zu, Sie können jedoch neue Variablennamen angeben, indem Sie den *COLINFO* -Parameter verwenden, oder die Datentypen mithilfe des *colClasses* -Parameters ändern.

Durch die Angabe zusätzlicher Vorgänge im Parameter *transforms* können Sie jeden Datenblock, der gelesen wird, elementar verarbeiten.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen einer neuen SQL Server-Tabelle mit rxDataStep](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)