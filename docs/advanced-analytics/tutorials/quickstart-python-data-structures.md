---
title: Schnellstart für die Arbeit mit Datenstrukturen in Python - SQL Server-Machine Learning
description: In dieser schnellstartanleitung verwenden erfahren Sie, Python-Skript in SQL Server, wie Datenstrukturen mit der gespeicherten Systemprozedur Sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 0105cf099bbee30d167c498646778520fcdbd805
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046793"
---
# <a name="quickstart-python-data-structures-in-sql-server"></a>Schnellstart: Python-Datenstrukturen in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Schnellstart veranschaulicht die Datenstrukturen verwenden, bei Verwendung von Python in SQL Server-Machine Learning-Dienste.

SQL Server ist abhängig von der Python **Pandas** -Paket, das ist großartig für die Arbeit mit Tabellendaten. Sie können nicht jedoch einen Skalarwert aus Python mit SQL Server zu übergeben und erwarten, dass es einfach "sauber arbeiten". In dieser schnellstartanleitung sehen wir uns einige grundlegende Datentypdefinitionen, um weitere Probleme zu vorzubereiten, denen Sie möglicherweise über beim Übergeben von Tabellendaten zwischen Python und SQL Server.

+ Ein Datenrahmen ist eine Tabelle mit _mehrere_ Spalten.
+ Eine einzelne Spalte mit den DataFrame ist eine Liste Objekt mit dem Namen einer Serie.
+ Ein einzelner Wert ist eine Zelle eines und nach Index aufgerufen werden muss.

Wie würden Sie das einzelne Ergebnis einer Berechnung als Datenrahmen, verfügbar machen, wenn für einen Datenrahmen (Data.Frame) eine tabellarischen Struktur erforderlich ist? Eine Antwort ist, um die einzelnen skalaren Wert als eine Reihe, darzustellen, die einfach zu einem Datenrahmen konvertiert wird. 

## <a name="prerequisites"></a>Erforderliche Komponenten

Einen vorherigen schnellstartanleitung [Python überprüfen, die in SQL Server vorhanden ist](quickstart-python-verify.md), enthält Informationen und links für das Einrichten der Python-Umgebung, die im Rahmen dieser schnellstartanleitung benötigt.

## <a name="scalar-value-as-a-series"></a>Skalarwert als eine Reihe

In diesem Beispiel werden einige einfache mathematische und konvertiert einen Skalar in eine Reihe.

1. Eine Reihe erfordert einen Index, die Sie wie folgt manuell oder programmgesteuert zuweisen können.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    print(c)
    s = pandas.Series(c, index =["simple math example 1"])
    print(s)
    '
    ```

2. Da der Reihe wurde nicht in eine data.frame konvertiert wurde, die Werte werden im Meldungsfenster zurückgegeben, aber Sie sehen, dass die Ergebnisse in einem Tabellenformat mehr sind.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    0.5
    simple math example 1    0.5
    dtype: float64
    ```

3. Um die Länge der Reihe zu erhöhen, können Sie neue Werte hinzufügen, mit einem Array. 

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    '
    ```

    Wenn Sie einen Index nicht angeben, wird ein Index generiert, die Werte, die mit 0 beginnt und endet mit der Länge des Arrays enthält.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    0    0.5
    1    2.0
    dtype: float64
    ```

4. Wenn Sie die Anzahl der erhöhen **Index** Werte jedoch nicht neu hinzufügen **Daten** Werte, die Datenwerte werden wiederholt, um die Reihen auszufüllen.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
    print(s)
    '
    ```

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    0.5
    simple math example 1    0.5
    simple math example 2    0.5
    dtype: float64
    ```

## <a name="convert-series-to-data-frame"></a>Reihe in Datenrahmen zu konvertieren.

Konvertiert unsere skalare mathematischen Ergebnisse müssen zu einer tabellarischen Struktur, müssen wir sie in ein Format zu konvertieren, die SQL Server verarbeiten kann. 

1. Um eine Reihe in eine data.frame zu konvertieren, rufen Sie die Pandas [DataFrame](https://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) Methode.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    df = pd.DataFrame(s)
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
    ```

2. Das Ergebnis ist unten dargestellt. Auch wenn Sie den Index verwenden, um bestimmte Werte aus den Datenrahmen (Data.Frame) zu erhalten, sind die Indexwerte in der Ausgabe nicht.

    **Ergebnisse**

    |ResultValue|
    |------|
    |0.5|
    |2|

## <a name="output-values-into-dataframe"></a>Ausgabewerte in Datenrahmen (Data.Frame)

Sehen wir uns an, wie die Konvertierung in einen Datenrahmen (Data.Frame) mit unseren zwei Reihen mit den Ergebnissen der einfachen mathematischen Vorgängen funktioniert. Die erste hat den Index von sequenziellen Werten, die von Python generiert. Der zweite verwendet einen beliebigen Index von Zeichenfolgenwerten.

1. In diesem Beispiel ruft einen Wert ab, aus der Reihe, die einen ganzzahligen Index verwendet.

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    df = pd.DataFrame(s, index=[1])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
    ```

    Denken Sie daran, dass der Index automatisch generierter bei 0 beginnt. Versuchen Sie es mit einem Wert außerhalb des Gültigkeitsbereichs Index, und sehen, was passiert.

2. Jetzt rufen wir einen einzelnen Wert aus anderen Datenrahmen, die einen String-Index verfügt. 

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
    print(s)
    df = pd.DataFrame(s, index=["simple math example 1"])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
    ```

    **Ergebnisse**

    |ResultValue|
    |------|
    |0.5|

    Wenn Sie versuchen, einen numerischen Index verwenden, um einen Wert aus dieser Reihe zu erhalten, erhalten Sie eine Fehlermeldung an.

## <a name="next-steps"></a>Nächste Schritte

Als Nächstes erstellen Sie ein Vorhersagemodell mithilfe von Python in SQL Server.

> [!div class="nextstepaction"]
> [Erstellen Sie, Trainieren Sie und verwenden Sie ein Python-Modell mit gespeicherten Prozeduren in SQL Server](quickstart-python-train-score-in-tsql.md)