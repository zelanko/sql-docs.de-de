---
title: Fragen Sie ab und ändern Sie die SQL Server-Daten mithilfe von RevoScaleR - SQL Server-Machine Learning
description: Exemplarische Vorgehensweise im Lernprogramm zum Abfragen und Ändern von Daten mit der Sprache R auf SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 191dd7237307d33d3cdaca5872fee9a09d27f321
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645409"
---
# <a name="query-and-modify-the-sql-server-data-sql-server-and-revoscaler-tutorial"></a>Fragen Sie ab und ändern Sie die SQL Server-Daten (SQL Server und die RevoScaleR-Lernprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil der [RevoScaleR Tutorial](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In der vorherigen Lektion haben Sie die Daten geladen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In diesem Schritt können Sie untersuchen und Bearbeiten von Daten mit **RevoScaleR**:

> [!div class="checklist"]
> * Grundlegende Informationen zu den Variablen zurück
> * Erstellen Sie aus Rohdaten kategorische Daten

Kategorische Daten oder *faktorvariablen*, eignen sich für explorative datenvisualisierungen. Sie können sie als Eingaben für Histogramme erhalten einen Überblick darüber, welche Variablendaten aussieht.

## <a name="query-for-columns-and-types"></a>Abfragen von Spalten und Typen

Verwenden Sie eine R-IDE oder RGui.exe, um R-Skript ausführen. 

Rufen Sie zunächst eine Liste der Spalten und ihrer Datentypen ab. Sie können mithilfe der Funktion [RxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) , und geben Sie die Datenquelle, die Sie analysieren möchten. Abhängig von Ihrer Version von **RevoScaleR**, außerdem können Sie [RxGetVarNames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames). 
  
```R
rxGetVarInfo(data = sqlFraudDS)
```

**Ergebnisse**

```R
Var 1: custID, Type: integer
Var 2: gender, Type: integer
Var 3: state, Type: integer
Var 4: cardholder, Type: integer
Var 5: balance, Type: integer
Var 6: numTrans, Type: integer
Var 7: numIntlTrans, Type: integer
Var 8: creditLine, Type: integer
Var 9: fraudRisk, Type: integer
```

## <a name="create-categorical-data"></a>Erstellen Sie kategorische Daten

Alle Variablen werden als Integer gespeichert, aber einige Variablen darstellen, aus kategorische Daten sollten namens *faktorvariablen* in r Z. B. die Spalte *Zustand* Zahlen, die als Bezeichner verwendet werden, für die 50 US-Bundesstaaten sowie das District Of Columbia enthält. Um das Verständnis der Daten zu erleichtern, ersetzen Sie die Zahlen durch eine Liste der Abkürzungen der US-Bundesstaaten.

In diesem Schritt erstellen einen Zeichenfolgenvektor, die die Abkürzungen enthält, und ordnen Sie dann diese kategorischen Werte den ursprünglichen integerbezeichnern. Verwenden Sie die neue Variable in der *ColInfo* Argument auf, um anzugeben, dass diese Spalte als Faktor behandelt werden. Wenn Sie die Daten analysieren, oder verschieben Sie es, die Abkürzungen verwendet werden, und die Spalte wird als Faktor behandelt.

Wenn die Spalte vor der Verwendung als Faktor zu Abkürzungen zugeordnet wird, verbessert dies auch die Leistung. Weitere Informationen finden Sie unter [R und Data-Optimierung](../r/r-and-data-optimization-r-services.md).

1. Erstellen eine R-Variable, zunächst *StateAbb*, und den Zeichenfolgenvektor Definieren von Zeichenfolgen, die wie folgt hinzufügen.
  
    ```R
    stateAbb <- c("AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC",
        "DE", "FL", "GA", "HI","IA", "ID", "IL", "IN", "KS", "KY", "LA",
        "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NB", "NC", "ND",
        "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI","SC",
        "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY")
    ```

2. Als Nächstes erstellen Sie ein Spaltenobjekt namens *ccColInfo*, das die Zuordnung der vorhandenen Integer-Werte zu den Kategorieebenen angibt (Abkürzungen der US-Bundesstaaten).
  
    Diese Anweisung erstellt auch Faktorvariablen für „gender“ (Geschlecht) und „cardholder“ (Karteninhaber).
  
    ```R
    ccColInfo <- list(
    gender = list(
              type = "factor",
              levels = c("1", "2"),
              newLevels = c("Male", "Female")
              ),
    cardholder = list(
                  type = "factor",
                  levels = c("1", "2"),
                  newLevels = c("Principal", "Secondary")
                   ),
    state = list(
             type = "factor",
             levels = as.character(1:51),
             newLevels = stateAbb
             ),
    balance = list(type = "numeric")
    )
    ```
  
3. Zum Erstellen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenquelle, die aktualisierten Daten Aufruf verwendet, die **RxSqlServerData** wie zuvor funktionieren, aber fügen die *ColInfo* Argument.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
    table = sqlFraudTable, colInfo = ccColInfo,
    rowsPerRead = sqlRowsPerRead)
    ```
  
    - Übergeben Sie für den *table* -Parameter die Variable *sqlFraudTable*, die die zuvor erstellte Datenquelle enthält.
    - Übergeben Sie für den *colInfo* -Parameter die Variable *ccColInfo* , die die Spaltendatentypen und Faktorebenen enthält.

4.  Sie können die **rxGetVarInfo** -Funktion nun dazu verwenden, um die Variablen in der neuen Datenquelle anzuzeigen.
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **Ergebnisse**
    
    ```R
    Var 1: custID, Type: integer
    Var 2: gender  2 factor levels: Male Female
    Var 3: state   51 factor levels: AK AL AR AZ CA ... VT WA WI WV WY
    Var 4: cardholder  2 factor levels: Principal Secondary
    Var 5: balance, Type: integer
    Var 6: numTrans, Type: integer
    Var 7: numIntlTrans, Type: integer
    Var 8: creditLine, Type: integer
    Var 9: fraudRisk, Type: integer
    ```

Die drei von Ihnen angegebenen Variablen (*gender*, *state*und *cardholder*) werden nun wie Faktoren verarbeitet.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Definieren und Verwenden von Rechenkontexten](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)