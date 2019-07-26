---
title: Schnellstart zum Arbeiten mit Datenstrukturen in python
description: In diesem Schnellstart für das Python-Skript in SQL Server erfahren Sie, wie Sie Datenstrukturen mit der gespeicherten System Prozedur sp_execute_external_script verwenden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 17b2c150368b32960907d6fdd2e31b109f51d771
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469641"
---
# <a name="quickstart-python-data-structures-in-sql-server"></a>Schnellstart: Python-Datenstrukturen in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In dieser Schnellstartanleitung erfahren Sie, wie Sie Datenstrukturen verwenden, wenn Sie python in SQL Server Machine Learning Services verwenden.

SQL Server basiert auf dem python **Pandas** -Paket, das hervorragend für die Arbeit mit tabellarischen Daten geeignet ist. Allerdings ist es nicht möglich, einen Skalar von python an SQL Server zu übergeben, und es wird davon ausgegangen, dass er "just work" In dieser Schnellstartanleitung überprüfen wir einige grundlegende Datentyp Definitionen, um Sie auf zusätzliche Probleme vorzubereiten, die bei der Übergabe von Tabellendaten zwischen Python und SQL Server auftreten können.

+ Ein Datenrahmen ist eine Tabelle mit _mehreren_ Spalten.
+ Eine einzelne Spalte eines dataframes ist ein Listen ähnliches Objekt, das als Reihe bezeichnet wird.
+ Ein einzelner Wert ist eine Zelle eines Daten Rahmens und muss durch einen Index aufgerufen werden.

Wie würden Sie das einzelne Ergebnis einer Berechnung als Datenrahmen verfügbar machen, wenn ein Data. Frame eine tabellarische Struktur erfordert? Eine Antwort ist die Darstellung des einzelnen skalarwerts als Reihe, die leicht in einen Datenrahmen konvertiert werden kann. 

## <a name="prerequisites"></a>Vorraussetzungen

Eine vorherige Schnellstartanleitung: [überprüfen, ob python in SQL Server vorhanden](quickstart-python-verify.md)ist, enthält Informationen und Links zum Einrichten der für diese Schnellstartanleitung erforderlichen python-Umgebung.

## <a name="scalar-value-as-a-series"></a>Skalarwert als Reihe

In diesem Beispiel wird eine einfache Mathematik durchführt und ein Skalar in eine Reihe konvertiert.

1. Eine Reihe erfordert einen Index, den Sie manuell zuweisen können, wie hier gezeigt, oder Programm gesteuert.

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

2. Da die Reihe nicht in einen Data. Frame konvertiert wurde, werden die Werte im Fenster Meldungen zurückgegeben. Sie können jedoch sehen, dass die Ergebnisse in einem tabellarischen Format vorliegen.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    0.5
    simple math example 1    0.5
    dtype: float64
    ```

3. Um die Länge der Reihe zu erhöhen, können Sie mithilfe eines Arrays neue Werte hinzufügen. 

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

    Wenn Sie keinen Index angeben, wird ein Index mit Werten generiert, die mit 0 beginnen und mit der Länge des Arrays enden.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    0    0.5
    1    2.0
    dtype: float64
    ```

4. Wenn Sie die Anzahl der **Index** Werte erhöhen, aber keine neuen **Daten** Werte hinzufügen, werden die Datenwerte wiederholt, um die Reihen auszufüllen.

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

## <a name="convert-series-to-data-frame"></a>Reihen in Datenrahmen konvertieren

Nachdem wir unsere mathematischen skalarergebnisse in eine tabellarische Struktur konvertiert haben, müssen wir Sie trotzdem in ein Format konvertieren, das SQL Server verarbeiten kann. 

1. Um eine Reihe in einen Data. Frame zu konvertieren, rufen Sie die Pandas- [dataframe](https://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) -Methode auf.

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

2. Das Ergebnis ist unten dargestellt. Auch wenn Sie den Index verwenden, um bestimmte Werte aus der Datei "Data. Frame" zu erhalten, sind die Indexwerte nicht Teil der Ausgabe.

    **Ergebnisse**

    |ResultValue|
    |------|
    |0.5|
    |2|

## <a name="output-values-into-dataframe"></a>Ausgabewerte in "Data. Frame"

Sehen wir uns an, wie die Konvertierung in einen Data. Frame mit unseren beiden Reihen funktioniert, die die Ergebnisse von einfachen mathematischen Operationen enthalten. Der erste verfügt über einen Index von sequenziellen Werten, die von python generiert werden. Der zweite verwendet einen beliebigen Index von Zeichen folgen Werten.

1. In diesem Beispiel wird ein Wert aus der Reihe abgerufen, die einen ganzzahligen Index verwendet.

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

    Beachten Sie, dass der automatisch generierte Index bei 0 beginnt. Verwenden Sie einen Index Wert außerhalb des gültigen Bereichs, und sehen Sie sich an, was passiert.

2. Wir erhalten nun einen einzelnen Wert aus dem anderen Datenrahmen, der einen Zeichen folgen Index aufweist. 

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

    Wenn Sie versuchen, einen numerischen Index zu verwenden, um einen Wert aus dieser Reihe zu erhalten, erhalten Sie eine Fehlermeldung.

## <a name="next-steps"></a>Nächste Schritte

Als Nächstes erstellen Sie ein Vorhersagemodell mithilfe von python in SQL Server.

> [!div class="nextstepaction"]
> [Erstellen, trainieren und Verwenden eines python-Modells mit gespeicherten Prozeduren in SQL Server](quickstart-python-train-score-in-tsql.md)