---
title: Laden von Daten mit rxImport
description: Tutorial zum Laden von Daten mithilfe der R-Programmiersprache unter SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ee0a1ddf8ccfdaf9c2b7b4f2ba5724451e7d71b8
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727226"
---
# <a name="load-data-into-memory-using-rximport-sql-server-and-revoscaler-tutorial"></a>Laden von Daten in den Arbeitsspeicher mithilfe von rxImport (SQL Server- und RevoScaleR-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Diese Lektion ist Teil des [RevoScaleR-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zum Verwenden von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Mithilfe der [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport)-Funktion können Daten aus einer Datenquelle in einen Datenrahmen im Arbeitsspeicher einer Sitzung oder in eine XDF-Datei auf einem Datenträger verschoben werden. Wenn Sie keine Datei als Ziel angeben, werden die Daten als Datenrahmen in den Arbeitsspeicher abgelegt.

In diesem Schritt erfahren Sie, wie Sie Daten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abrufen und anschließend die Funktion **rxImport** verwenden, um die relevanten Daten in einer lokalen Datei abzulegen. Auf diese Weise können Sie sie wiederholt im lokalen Computekontext analysieren, ohne die Datenbank erneut abfragen zu müssen.

## <a name="extract-a-subset-of-data-from-sql-server-to-local-memory"></a>Extrahieren einer Teilmenge von Daten von SQL Server in den lokalen Arbeitsspeicher

Sie haben sich dazu entschieden, nur die Hochrisikopersonen genauer zu untersuchen. Die Quelltabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist groß, weshalb Sie nur die Informationen zu den Hochrisikokunden extrahieren möchten. Anschließend laden Sie diese Daten in einen Datenrahmen im Arbeitsspeicher der lokalen Arbeitsstation.

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

3. Rufen Sie die Funktion [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) auf, um die Daten in einen Datenrahmen in der lokalen R-Sitzung zu lesen.

    ```R
    highRisk <- rxImport(sqlServerProbDS)
    ```

    Wenn der Vorgang erfolgreich war, sollte eine Statusmeldung wie die folgende angezeigt werden: „Gelesene Zeilen: 35, gesamte verarbeitete Zeilen: 35, gesamte Blockzeit: 0,036 Sekunden“

4. Da sich nun die risikoreichsten Beobachtungen in einem Datenrahmen im Arbeitsspeicher befinden, können Sie verschiedene R-Funktionen verwenden, um den Datenrahmen zu bearbeiten. Sie können Kunden z. B. nach ihrer Risikobewertung sortieren und eine Liste der Kunden ausgeben, die das größte Risiko darstellen.

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

Die **rxImport**-Funktion weist den Spalten während des Importprozesses Variablennamen zu. Sie können jedoch neue Variablennamen angeben, indem Sie den Parameter *colInfo* verwenden oder Datentypen ändern, indem Sie den Parameter *colClasses* verwenden.

Durch die Angabe zusätzlicher Vorgänge im Parameter *transforms* können Sie jeden Datenblock, der gelesen wird, elementar verarbeiten.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen einer neuen SQL Server-Tabelle mit rxDataStep](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)