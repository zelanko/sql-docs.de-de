---
title: Tutorial zum Erstellen von R-Modellen revoscaler
description: 'Tutorial: Exemplarische Vorgehensweise zum Erstellen eines Modells mit der Sprache R auf SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 7df044c641da5d8605e5bb25fafed9ea02af77f4
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344688"
---
# <a name="create-r-models-sql-server-and-revoscaler-tutorial"></a>Erstellen von R-Modellen (SQL Server-und revoscaler-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil des [revoscaler-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Nachdem Sie die Trainingsdaten erweitert haben, ist es Zeit, die Daten mithilfe der Regressions Modellierung zu analysieren. Lineare Modelle sind ein wichtiges Tool in der Welt der Predictive Analytics, und das **revoscaler** -Paket enthält Regressions Algorithmen, mit denen die Arbeitsauslastung unterteilt und parallel ausgeführt werden kann.

> [!div class="checklist"]
> * Erstellen eines linearen Regressionsmodells
> * Erstellen eines logistischen Regressionsmodells

## <a name="create-a-linear-regression-model"></a>Erstellen eines linearen Regressionsmodells

In diesem Schritt erstellen Sie ein einfaches lineares Modell, das den Kreditkarten Saldo der Kunden schätzt, die die Werte in den Spalten *Geschlecht* und *creditline* als unabhängige Variablen verwenden.
  
Verwenden Sie hierzu die Funktion [rxlinmod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) , die remotecomputekontexte unterstützt.
  
1. Erstellen Sie eine R-Variable, um das fertige Modell zu speichern, und rufen Sie **rxlinmod**auf, und übergeben Sie eine entsprechende Formel.
  
    ```R
    linModObj <- rxLinMod(balance ~ gender + creditLine,  data = sqlFraudDS)
    ```
  
2. Um eine Zusammenfassung der Ergebnisse anzuzeigen, müssen Sie die Standard-R- **Zusammenfassungs** Funktion für das Model-Objekt aufzurufen.
  
     ```R
     summary(linModObj)
     ```

Es mag Ihnen seltsam erscheinen, dass eine einfache R-Funktion wie **summary** hier funktioniert, da Sie im vorherigen Schritt den Server als Computekontext festgelegt haben. Auch wenn die Funktion **rxLinMod** den Remotecomputekontext zum Erstellen des Modells verwendet, gibt sie auch ein Objekt zurück, das das Modell für Ihre lokale Arbeitsstation enthält und es im freigegebenen Verzeichnis speichert.

Daher können Sie R-Standardbefehle für das Modell ausführen, als ob es mithilfe des „lokalen“ Kontexts erstellt wurde.

**Ergebnisse**

```R
Linear Regression Results for: balance ~ gender + creditLineData: sqlFraudDS (RxSqlServerData Data Source)
Dependent variable(s): balance
Total independent variables: 4 (Including number dropped: 1)
Number of valid observations: 10000
Number of missing observations: 0
Coefficients: (1 not defined because of singularities)

Estimate Std. Error t value Pr(>|t|) (Intercept)
3253.575 71.194 45.700 2.22e-16
gender=Male -88.813 78.360 -1.133 0.257
gender=Female Dropped Dropped Dropped Dropped
creditLine 95.379 3.862 24.694 2.22e-16
Signif. codes: 0  0.001  0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 3812 on 9997 degrees of freedom
Multiple R-squared: 0.05765
Adjusted R-squared: 0.05746
F-statistic: 305.8 on 2 and 9997 DF, p-value: < 2.2e-16
Condition number: 1.0184
```

## <a name="create-a-logistic-regression-model"></a>Erstellen eines logistischen Regressionsmodells

Erstellen Sie als nächstes ein logistisches Regressionsmodell, das angibt, ob ein bestimmter Kunde ein Betrugsrisiko darstellt. Sie verwenden die **revoscaler** [rxlogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) -Funktion, die die Anpassung von logistischen Regressionsmodellen in remotecomputekontexten unterstützt.

Lassen Sie den Computekontext wie er ist. Außerdem wird weiterhin dieselbe Datenquelle verwendet.

1. Rufen Sie die Funktion **rxLogit** auf, und übergeben Sie die Formel, die zum Definieren des Modells erforderlich ist.

    ```R
    logitObj <- rxLogit(fraudRisk ~ state + gender + cardholder + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS, dropFirst = TRUE)
    ```
  
    Da es ein großes Modell mit 60 unabhängigen Variablen ist, einschließlich der drei Dummy-Variablen, die gelöscht werden, müssen Sie möglicherweise ein paar Minuten warten, bis der Computekontext das Objekt zurückgibt.
    
    Der Grund für die Größe des Modells ist, dass in R und im **RevoScaleR** -Paket alle Ebenen einer kategorischen Faktor-Variable automatisch als separate Dummyvariablen behandelt werden.
  
2. Rufen Sie die **summary** -Funktion von R auf, um eine Zusammenfassung des zurückgegebenen Modells anzuzeigen.
  
    ```R
    summary(logitObj)
    ```
  
**Teilergebnisse**

```R
Logistic Regression Results for: fraudRisk ~ state + gender + cardholder + balance + numTrans + numIntlTrans + creditLine
Data: sqlFraudDS (RxSqlServerData Data Source)
Dependent variable(s): fraudRisk
Total independent variables: 60 (Including number dropped: 3)
Number of valid observations: 10000 -2

LogLikelihood: 2032.8699 (Residual deviance on 9943 degrees of freedom)

Coefficients:
Estimate Std. Error z value Pr(>|z|)     (Intercept)
-8.627e+00  1.319e+00  -6.538 6.22e-11
state=AK                Dropped    Dropped Dropped  Dropped
state=AL             -1.043e+00  1.383e+00  -0.754   0.4511

(other states omitted)

gender=Male             Dropped    Dropped Dropped  Dropped
gender=Female         7.226e-01  1.217e-01   5.936 2.92e-09
cardholder=Principal    Dropped    Dropped Dropped  Dropped
cardholder=Secondary  5.635e-01  3.403e-01   1.656   0.0977
balance               3.962e-04  1.564e-05  25.335 2.22e-16
numTrans              4.950e-02  2.202e-03  22.477 2.22e-16
numIntlTrans          3.414e-02  5.318e-03   6.420 1.36e-10
creditLine            1.042e-01  4.705e-03  22.153 2.22e-16

Signif. codes:  0 '\*\*\*' 0.001 '\*\*' 0.01 '\*' 0.05 '.' 0.1 ' ' 1
Condition number of final variance-covariance matrix: 3997.308
Number of iterations: 15
```

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Auswertung neuer Daten](../../advanced-analytics/tutorials/deepdive-score-new-data.md)