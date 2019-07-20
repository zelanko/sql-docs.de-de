---
title: Verschieben von Daten zwischen SQL Server und der Xdf-Datei mithilfe von revoscaler
description: 'Tutorial: Exemplarische Vorgehensweise zum Verschieben von Daten mithilfe von Xdf und der Programmiersprache R auf SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0e4c0fbdd9f625886a7d38fc80895e9f4407ce88
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344748"
---
# <a name="move-data-between-sql-server-and-xdf-file-sql-server-and-revoscaler-tutorial"></a>Verschieben von Daten zwischen SQL Server und der Xdf-Datei (SQL Server-und revoscaler-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil des [revoscaler-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In diesem Schritt erfahren Sie, wie Sie eine Xdf-Datei zum Übertragen von Daten zwischen Remote-und lokalen computekontexten verwenden. Durch das Speichern der Daten in einer Xdf-Datei können Sie Transformationen für die Daten durchführen.

Wenn Sie fertig sind, verwenden Sie die Daten in der Datei, um eine neue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle zu erstellen. Die Funktion [rxdatastep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) kann Transformationen auf die Daten anwenden und die Konvertierung zwischen Daten Frames und Xdf-Dateien durchführen.
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>Erstellen einer SQL Server Tabelle aus einer Xdf-Datei

In dieser Übung verwenden Sie die Kreditkarten-Betrugsdaten erneut. In diesem Szenario wurden Sie gebeten, zusätzliche Analysen für Benutzer in den US-Bundesstaaten Kalifornien, Oregon und Washington durchzuführen. Um effizienter zu sein, haben Sie entschieden, nur Daten für diese Zustände auf dem lokalen Computer zu speichern und nur mit den Variablen Geschlecht, Karteninhaber, Bundesland und Saldo zu arbeiten.

1. Verwenden Sie die `stateAbb` zuvor erstellte Variable erneut, um die einzuschließende Ebenen zu identifizieren, und schreiben Sie Sie in eine `statesToKeep`neue Variable.
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **Ergebnisse**
    
    CA|oder|WA
    ----|----|----
    5|38|48
    
2. Definieren Sie mithilfe einer [!INCLUDE[tsql](../../includes/tsql-md.md)] Abfrage die Daten, die Sie aus SQL Server übertragen möchten.  Später verwenden Sie diese Variable als das *InData* -Argument für **rximport**.
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    Stellen Sie sicher, dass keine ausgeblendeten Zeichen, wie z. B. Zeilenvorschübe oder Registerkarten, in der Abfrage vorhanden sind.
  
3. Definieren Sie als nächstes die Spalten, die beim Arbeiten mit den Daten in R verwendet werden sollen. Beispielsweise benötigen Sie im kleineren DataSet nur drei Faktor Ebenen, da die Abfrage nur Daten für drei Zustände zurückgibt.  Wenden Sie `statesToKeep` die Variable an, um die einzuschließenden Ebenen zu identifizieren.
  
    ```R
    importColInfo <- list(
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))
            )
    ```
  
4. Legen Sie den computekontext auf **local**fest, da Sie möchten, dass alle Daten auf dem lokalen Computer verfügbar sind.
  
    ```R
    rxSetComputeContext("local")
    ```
    
    Die [rximport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) -Funktion kann Daten aus einer beliebigen unterstützten Datenquelle in eine lokale Xdf-Datei importieren. Die Verwendung einer lokalen Kopie der Daten ist praktisch, wenn Sie viele verschiedene Analysen der Daten durchführen möchten, aber vermeiden möchten, dass dieselbe Abfrage immer wieder ausgeführt wird.

5. Erstellen Sie das Datenquellen Objekt, indem Sie die zuvor als Argumente definierten Variablen an **rxsqlserverdata**übergeben.
  
    ```R
    sqlServerImportDS <- RxSqlServerData(
        connectionString = sqlConnString,
        sqlQuery = importQuery,
        colInfo = importColInfo)
    ```
  
6. Ruft **rximport** auf, um die Daten in eine Datei `ccFraudSub.xdf`mit dem Namen im aktuellen Arbeitsverzeichnis zu schreiben.
  
    ```R
    localDS <- rxImport(inData = sqlServerImportDS,
        outFile = "ccFraudSub.xdf",
        overwrite = TRUE)
    ```
  
    Das `localDs` von der **rximport** -Funktion zurückgegebene Objekt ist ein leichtes **rxxdfdata** -Datenquellen Objekt, das `ccFraud.xdf` die lokal auf dem Datenträger gespeicherte Datendatei darstellt.
  
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

8. Sie können nun verschiedene R-Funktionen aufzurufen, um das **localds** -Objekt zu analysieren, genauso wie bei den Quelldaten in SQL Server. Beispielsweise können Sie nach Geschlecht zusammenfassen:
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

## <a name="next-steps"></a>Nächste Schritte

Diese Lektion schließt die mehrteilige tutorialreihe zu **revoscaler** und SQL Server ab. Es wurden zahlreiche Daten-und Berechnungs Konzepte vorgestellt, mit denen Sie Ihre eigenen Daten-und Projektanforderungen in den Weg bringen können.

Um Ihre Kenntnisse von **revoscaler**zu vertiefen, können Sie zur Liste R-Tutorials zurückkehren, um alle Übungen schrittweise auszuführen, die Sie möglicherweise übersehen haben. Weitere Informationen zu allgemeinen Aufgaben finden Sie in den Anleitungen im Inhaltsverzeichnis.

> [!div class="nextstepaction"]
> [R-Tutorials für SQL Server](sql-server-r-tutorials.md)