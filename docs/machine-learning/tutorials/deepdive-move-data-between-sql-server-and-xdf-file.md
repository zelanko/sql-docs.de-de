---
title: Verschieben von Daten mit einer XDF-Datei
description: 'Tutorial 13 zu RevoScaleR: Tutorial zum Verschieben von Daten mit einer XDF-Datei und der Programmiersprache R in SQL Server'
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9c7e5ce4cbe995fd677acd406187dfaf264a7461
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85680003"
---
# <a name="move-data-between-sql-server-and-xdf-file-sql-server-and-revoscaler-tutorial"></a>Verschieben von Daten zwischen SQL Server und einer XDF-Datei (SQL Server und RevoScaleR-Tutorial)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Bei diesem Tutorial handelt es sich um das 13. Tutorial der [Tutorialreihe zu RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md). In diesem Tutorial erfahren Sie, wie Sie [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server verwenden.

In diesem Tutorial erfahren Sie, wie Sie eine XDF-Datei zum Übertragen von Daten zwischen Remote- und lokalen Computekontexten verwenden. Durch das Speichern der Daten in einer XDF-Datei können Sie Transformationen für die Daten durchführen.

Verwenden Sie die Daten in der Datei, um eine neue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle zu erstellen, wenn Sie fertig sind. Die [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep)-Funktion kann Transformationen auf die Daten anwenden und die Konvertierung zwischen Datenrahmen und XDF-Dateien durchführen.
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>Erstellen einer SQL Server-Tabelle aus einer XDF-Datei

Verwenden Sie für diese Übung wieder die Kreditkartenbetrugsdaten. In diesem Szenario wurden Sie gebeten, zusätzliche Analysen für Benutzer in den US-Bundesstaaten Kalifornien, Oregon und Washington durchzuführen. Aus Effizienzgründen haben Sie sich dazu entschieden, nur Daten für diese Bundesländer auf Ihrem lokalen Computer zu speichern und nur mit den Variablen „gender“ (Geschlecht), „cardholder“ (Karteninhaber/in), „state“ (Bundesland) und „balance“ (Kontostand) zu arbeiten.

1. Verwenden Sie erneut die zuvor erstellte Variable `stateAbb` zum Identifizieren der einzuschließenden Ebenen, und schreiben Sie diese in die neue Variable `statesToKeep`.
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **Ergebnisse**
    
    CA|oder|WA
    ----|----|----
    5|38|48
    
2. Definieren Sie die Daten, die mithilfe einer [!INCLUDE[tsql](../../includes/tsql-md.md)]-Abfrage von SQL Server übermittelt werden sollen.  Später verwenden Sie diese Variable als *inData*-Argument für **rxImport**.
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    Stellen Sie sicher, dass keine ausgeblendeten Zeichen, wie z. B. Zeilenvorschübe oder Registerkarten, in der Abfrage vorhanden sind.
  
3. Als nächstes definieren Sie die Spalten, die beim Arbeiten mit den Daten in R verwendet werden sollen. Im kleineren Dataset benötigen Sie beispielsweise nur drei Faktorenebenen, da die Abfrage nur Daten für drei Bundesländer zurückgibt.  Wenden Sie die `statesToKeep`-Variable an, um die richtigen Ebenen zu identifizieren, die eingeschlossen werden sollen.
  
    ```R
    importColInfo <- list(
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))
            )
    ```
  
4. Legen Sie den Computekontext auf **local** fest, da Sie möchten, dass alle Daten auf Ihrem lokalen Computer verfügbar sind.
  
    ```R
    rxSetComputeContext("local")
    ```
    
    Mit der Funktion [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)-Funktion können Sie Daten aus einer beliebigen unterstützten Datenquelle in eine lokale XDF-Datei importieren. Die Verwendung einer lokalen Kopie der Daten eignet sich dann, wenn Sie viele verschiedene Analysen der Daten durchführen, aber die wiederholte Ausführung der gleichen Abfrage vermeiden möchten.

5. Erstellen Sie das Datenquellenobjekt, indem Sie die zuvor als Argumente definierten Variablen an **RxSqlServerData** übergeben.
  
    ```R
    sqlServerImportDS <- RxSqlServerData(
        connectionString = sqlConnString,
        sqlQuery = importQuery,
        colInfo = importColInfo)
    ```
  
6. Rufen Sie **rxImport** auf, um die Daten im aktuellen Arbeitsverzeichnis in einer Datei namens `ccFraudSub.xdf` zu speichern.
  
    ```R
    localDS <- rxImport(inData = sqlServerImportDS,
        outFile = "ccFraudSub.xdf",
        overwrite = TRUE)
    ```
  
    Das von der **rxImport**-Funktion zurückgegebene Objekt `localDs` ist ein kompaktes **RxXdfData**-Datenquellenobjekt, das die lokal auf dem Datenträger gespeicherte `ccFraud.xdf`-Datendatei darstellt.
  
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

8. Sie können nun verschiedene R-Funktionen aufrufen, um das **localDs**-Objekt so wie die Quelldaten in SQL Server zu analysieren. Sie können beispielsweise nach Geschlecht zusammenfassen:
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

## <a name="next-steps"></a>Nächste Schritte

Dieses Tutorial schließt das mehrteilige Tutorial zu **RevoScaleR** und SQL Server ab. Es wurden zahlreiche datenbezogene Konzepte und Berechnungskonzepte vorgestellt, mit denen Sie Ihre eigenen Daten- und Projektanforderungen erfüllen können.

Sie können zur R-Tutorialsliste zurückkehren und nicht absolvierte Übungen schrittweise durcharbeiten, um so Ihr Wissen über **RevoScaleR** zu vertiefen. Alternativ finden Sie weitere Informationen zu allgemeinen Aufgaben in den Artikeln zur Vorgehensweise im Inhaltsverzeichnis.

> [!div class="nextstepaction"]
> [R-Tutorials für SQL Server](sql-server-r-tutorials.md)