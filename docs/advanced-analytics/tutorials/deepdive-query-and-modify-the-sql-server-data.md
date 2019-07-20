---
title: Abfragen und Ändern der SQL Server Daten mithilfe von revoscaler
description: 'Tutorial: Exemplarische Vorgehensweise zum Abfragen und Ändern von Daten mit der Sprache R auf SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0784f10bfc4405ce17e365b6afcb596fa534202d
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344656"
---
# <a name="query-and-modify-the-sql-server-data-sql-server-and-revoscaler-tutorial"></a>Abfragen und Ändern der SQL Server Daten (SQL Server-und revoscaler-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil des [revoscaler-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In der vorherigen Lektion haben Sie die Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]geladen. In diesem Schritt können Sie Daten mithilfe von **revoscaler**durchsuchen und ändern:

> [!div class="checklist"]
> * Grundlegende Informationen zu den Variablen zurückgeben
> * Erstellen von kategorischen Daten aus Rohdaten

Kategorische Daten oder *Faktor Variablen*sind für explorative Datenvisualisierungen nützlich. Sie können Sie als Eingaben für Histogramme verwenden, um eine Vorstellung davon zu erhalten, wie die Variablen Daten aussehen.

## <a name="query-for-columns-and-types"></a>Abfragen von Spalten und Typen

Verwenden Sie zum Ausführen von r-Skripts eine r-IDE oder rgui. exe. 

Rufen Sie zunächst eine Liste der Spalten und ihrer Datentypen ab. Sie können die [rxgetvarinfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) -Funktion verwenden und die Datenquelle angeben, die Sie analysieren möchten. Abhängig von Ihrer Version von **revoscaler**können Sie auch [rxgetvarnames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames)verwenden. 
  
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

## <a name="create-categorical-data"></a>Erstellen von kategorischen Daten

Alle Variablen werden als ganze Zahlen gespeichert, einige Variablen stellen jedoch kategorische Daten dar, die als *Faktor Variablen* in R bezeichnet werden. Der Spalten *Status* enthält z. b. Zahlen, die als Bezeichner für die 50-Zustände zuzüglich des Bezirks von Columbia verwendet werden. Um das Verständnis der Daten zu erleichtern, ersetzen Sie die Zahlen durch eine Liste der Abkürzungen der US-Bundesstaaten.

In diesem Schritt erstellen Sie einen Zeichen folgen Vektor, der die Abkürzungen enthält, und ordnen dann diese kategorischen Werte den ursprünglichen ganzzahligen bezeichchern zu. Anschließend verwenden Sie die neue Variable im *COLINFO* -Argument, um anzugeben, dass diese Spalte als Faktor behandelt werden soll. Wenn Sie die Daten analysieren oder verschieben, werden die Abkürzungen verwendet, und die Spalte wird als Faktor behandelt.

Wenn die Spalte vor der Verwendung als Faktor zu Abkürzungen zugeordnet wird, verbessert dies auch die Leistung. Weitere Informationen finden Sie unter [R und Daten Optimierung](../r/r-and-data-optimization-r-services.md).

1. Beginnen Sie, indem Sie eine R-Variable, *stateabb*, erstellen und den Zeichen folgen Vektor definieren, der der Zeichenfolge hinzugefügt werden soll.
  
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
  
3. Um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquelle zu erstellen, die die aktualisierten Daten verwendet, rufen Sie die **rxsqlserverdata** -Funktion wie zuvor auf, fügen jedoch das *COLINFO* -Argument hinzu.
  
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