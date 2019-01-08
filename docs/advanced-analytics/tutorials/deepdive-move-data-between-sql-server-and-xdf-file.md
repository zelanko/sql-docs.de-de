---
title: Verschieben von Daten zwischen SQL Server und einer XDF-Datei, die mithilfe von RevoScaleR - SQL Server-Machine Learning
description: Exemplarische Vorgehensweise im Lernprogramm zum Verschieben von Daten mithilfe von XDF und die Sprache R auf SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d0f097c64d48a3a2e87f01965914b3100c8a28dc
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645209"
---
# <a name="move-data-between-sql-server-and-xdf-file-sql-server-and-revoscaler-tutorial"></a>Verschieben von Daten zwischen SQL Server und einer XDF-Datei (SQL Server und die RevoScaleR-Lernprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil der [RevoScaleR Tutorial](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Erfahren Sie in diesem Schritt, eine XDF-Datei, die zum Übertragen von Daten zwischen lokalen und remote computekontexte verwenden. Die Daten in eine XDF-Datei speichern, können Sie Transformationen auf die Daten anwenden.

Wenn Sie fertig sind, Sie verwenden die Daten in der Datei zum Erstellen eines neuen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle. Die Funktion [RxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) Transformationen auf die Daten anwenden, und führt die Konvertierung zwischen Datenrahmen und xdf-Dateien.
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>Erstellen Sie eine SQL Server-Tabelle aus einer XDF-Datei

In dieser Übung verwenden Sie die Meldung von Betrug Kreditkartendaten erneut aus. In diesem Szenario wurden Sie gebeten, zusätzliche Analysen für Benutzer in den US-Bundesstaaten Kalifornien, Oregon und Washington durchzuführen. Genauer effizient und Sie möchte Daten für nur diese Zustände auf dem lokalen Computer speichern, und Arbeiten mit Variablen Geschlecht, Karteninhaberdaten, Status und Lastenausgleich.

1. Verwenden Sie erneut die `stateAbb` Variable, die Sie zuvor zum Identifizieren der Ebenen, um enthalten, und in eine neue Variable zu schreiben erstellt `statesToKeep`.
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **Ergebnisse**
    
    CA|oder|WA
    ----|----|----
    5|38|48
    
2. Definieren Sie die Daten zu übertragen und von SQL Server mit einem [!INCLUDE[tsql](../../includes/tsql-md.md)] Abfrage.  Später verwenden Sie diese Variable als das *InData* Argument für **RxImport**.
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    Stellen Sie sicher, dass keine ausgeblendeten Zeichen, wie z. B. Zeilenvorschübe oder Registerkarten, in der Abfrage vorhanden sind.
  
3. Definieren Sie als Nächstes die Spalten aus, verwenden Sie bei der Arbeit mit Daten in r Beispielsweise benötigen im kleineren Dataset, Sie nur drei Faktorebenen, da die Abfrage Daten für nur drei Bundesstaaten zurückgibt.  Anwenden der `statesToKeep` Variable, die die richtigen einzuschließenden Ebenen zu identifizieren.
  
    ```R
    importColInfo <- list(
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))
            )
    ```
  
4. Legen Sie den computekontext auf **lokalen**, da Sie alle verfügbaren Daten auf dem lokalen Computer möchten.
  
    ```R
    rxSetComputeContext("local")
    ```
    
    Die [RxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) Funktion kann Daten aus einer beliebigen unterstützten Datenquelle in eine lokale XDF-Datei importieren. Verwenden einer lokalen Kopie der Daten ist praktisch, wenn Sie verschiedene Analysen der Daten durchführen möchten, aber vermeiden, dieselbe Abfrage immer wieder ausführen möchten.

5. Das Datenquellenobjekt erstellen, übergeben Sie die Variablen als Argumente, die zuvor definierten **RxSqlServerData**.
  
    ```R
    sqlServerImportDS <- RxSqlServerData(
        connectionString = sqlConnString,
        sqlQuery = importQuery,
        colInfo = importColInfo)
    ```
  
6. Rufen Sie **RxImport** schreiben die Daten in eine Datei namens `ccFraudSub.xdf`, in das aktuelle Arbeitsverzeichnis.
  
    ```R
    localDS <- rxImport(inData = sqlServerImportDS,
        outFile = "ccFraudSub.xdf",
        overwrite = TRUE)
    ```
  
    Die `localDs` zurückgegebenes Objekt der **RxImport** -Funktion ist ein kompaktes **RxXdfData** -Datenquellenobjekt, das darstellt der `ccFraud.xdf` Datendatei, die lokal auf dem Datenträger gespeichert.
  
7. Rufen Sie [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) für die XDF-Datei auf, um zu überprüfen, ob das Schema identisch ist.
  
    ```R
    rxGetVarInfo(data = localDS)
    ```

    **Ergebnisse**
    
    ```R
    rxGetVarInfo(data = localDS)
    Var 1: gender, Type: factor, no factor levels available
    Var 2: cardholder, Type: factor, no factor levels available
    Var 3: balance, Type: integer, Low/High: (0, 22463)
    Var 4: state, Type: factor, no factor levels available
    ```

8. Sie können nun verschiedene R-Funktionen zum Analysieren von Aufrufen der **LocalDs** Objekt, wie Sie mit den Quelldaten in SQL Server. Sie können z. B. nach Geschlecht zusammenfassen:
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

## <a name="next-steps"></a>Nächste Schritte

In dieser Lektion schließt der mehrteiligen Tutorial-Reihe auf **RevoScaleR** und SQL Server. Es wurde Ihnen zahlreiche datenbezogene und COMPUTE Konzepte, bietet Ihnen eine Grundlage mit Ihren eigenen Daten und Projektdateien Anforderungen in Zukunft vorgestellt.

Um Ihre Kenntnisse vertiefen **RevoScaleR**, Sie können zurückkehren, um die Liste der R-Tutorials alle Übungen durchlaufen Sie möglicherweise übersehen haben. Überprüfen Sie alternativ die Gewusst-wie-Artikel in der Tabelle der Inhalte für Informationen zu allgemeinen Aufgaben aus.

> [!div class="nextstepaction"]
> [R-Tutorials für SQL Server](sql-server-r-tutorials.md)