---
title: Arbeiten mit Python-und SQL-Datentypen und-Objekten
titleSuffix: SQL Server Machine Learning Services
description: In dieser Schnellstartanleitung erfahren Sie, wie Sie mit Datentypen und Datenobjekten in Python arbeiten und SQL Server mit SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/17/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e3606072fefa9b74adcfdb914d02e4e82c11e0eb
ms.sourcegitcommit: 9221a693d4ab7ae0a7e2ddeb03bd0cf740628fd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71199435"
---
# <a name="quickstart-handle-data-types-and-objects-using-python-in-sql-server-machine-learning-services"></a>Schnellstart: Verarbeiten von Datentypen und Objekten mithilfe von python in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In dieser Schnellstartanleitung erfahren Sie, wie Sie Datenstrukturen verwenden, wenn Sie python in SQL Server Machine Learning Services verwenden.

SQL Server basiert auf dem python **Pandas** -Paket, das hervorragend für die Arbeit mit tabellarischen Daten geeignet ist. Allerdings ist es nicht möglich, einen Skalar von python an SQL Server zu übergeben, und es wird davon ausgegangen, dass er "just work" In dieser Schnellstartanleitung überprüfen Sie einige grundlegende Datentyp Definitionen, um Sie auf zusätzliche Probleme vorzubereiten, die bei der Übergabe von Tabellendaten zwischen Python und SQL Server auftreten können.

Folgende Konzepte sollten im Vordergrund aufgeführt werden:

+ Ein Datenrahmen ist eine Tabelle mit _mehreren_ Spalten.
+ Eine einzelne Spalte eines Daten Rahmens ist ein Listen ähnliches Objekt, das als Reihe bezeichnet wird.
+ Ein einzelner Wert eines Daten Rahmens wird als Zelle bezeichnet, und der Zugriff erfolgt über den Index.

Wie würden Sie das einzelne Ergebnis einer Berechnung als Datenrahmen verfügbar machen, wenn ein Data. Frame eine tabellarische Struktur erfordert? Eine Antwort ist die Darstellung des einzelnen skalarwerts als Reihe, die leicht in einen Datenrahmen konvertiert werden kann. 

## <a name="prerequisites"></a>Erforderliche Komponenten

- Diese Schnellstartanleitung erfordert Zugriff auf eine Instanz von SQL Server mit [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) , auf der die Python-Sprache installiert ist.

- Außerdem benötigen Sie ein Tool zum Ausführen von SQL-Abfragen, die python-Skripts enthalten. Sie können diese Skripts mit einem beliebigen Daten Bank Verwaltungs-oder Abfrage Tool ausführen, solange eine Verbindung mit einer SQL Server Instanz hergestellt und eine T-SQL-Abfrage oder eine gespeicherte Prozedur ausgeführt werden kann. In diesem Schnellstart wird [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)verwendet.

## <a name="scalar-value-as-a-series"></a>Skalarwert als Reihe

In diesem Beispiel wird eine einfache Mathematik durchführt und ein Skalar in eine Reihe konvertiert.

1. Eine Reihe erfordert einen Index, den Sie manuell zuweisen können, wie hier gezeigt, oder Programm gesteuert.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   a = 1
   b = 2
   c = a/b
   print(c)
   s = pandas.Series(c, index =["simple math example 1"])
   print(s)
   '
   ```

   Da die Reihe nicht in einen Data. Frame konvertiert wurde, werden die Werte im Fenster Meldungen zurückgegeben. Sie können jedoch sehen, dass die Ergebnisse in einem tabellarischen Format vorliegen.

   **Ergebnisse**

   ```text
   STDOUT message(s) from external script: 
   0.5
   simple math example 1    0.5
   dtype: float64
   ```

1. Um die Länge der Reihe zu erhöhen, können Sie mithilfe eines Arrays neue Werte hinzufügen. 

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
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

1. Wenn Sie die Anzahl der **Index** Werte erhöhen, aber keine neuen **Daten** Werte hinzufügen, werden die Datenwerte wiederholt, um die Reihen auszufüllen.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
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

Wenn Sie die mathematischen skalarergebnisse in eine tabellarische Struktur konvertiert haben, müssen Sie Sie dennoch in ein Format konvertieren, das SQL Server verarbeiten kann.

1. Um eine Reihe in einen Data. Frame zu konvertieren, rufen Sie die Pandas- [dataframe](https://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) -Methode auf.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
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
   WITH RESULT SETS((ResultValue FLOAT))
   ```

   Das Ergebnis ist unten dargestellt. Auch wenn Sie den Index verwenden, um bestimmte Werte aus der Datei "Data. Frame" zu erhalten, sind die Indexwerte nicht Teil der Ausgabe.

   **Ergebnisse**

   |ResultValue|
   |------|
   |0.5|
   |2|

## <a name="output-values-into-dataframe"></a>Ausgabewerte in "Data. Frame"

Nun geben Sie bestimmte Werte aus zwei Folge mathematischen Ergebnissen in einem Data. Frame aus. Der erste verfügt über einen Index von sequenziellen Werten, die von python generiert werden. Der zweite verwendet einen beliebigen Index von Zeichen folgen Werten.

1. Im folgenden Beispiel wird ein Wert aus der Reihe mithilfe eines ganzzahligen Indexes abgerufen.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
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
   WITH RESULT SETS((ResultValue FLOAT))
   ```

   **Ergebnisse**

   |ResultValue|
   |------|
   |2.0|

   Beachten Sie, dass der automatisch generierte Index bei 0 beginnt. Verwenden Sie einen Index Wert außerhalb des gültigen Bereichs, und sehen Sie sich an, was passiert.

1. Nun erhalten Sie einen einzelnen Wert aus dem anderen Datenrahmen, der einen Zeichen folgen Index verwendet.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   import pandas as pd
   a = 1
   b = 2
   c = a/b
   s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
   print(s)
   df = pd.DataFrame(s, index=["simple math example 1"])
   OutputDataSet = df
   '
   WITH RESULT SETS((ResultValue FLOAT))
   ```

   **Ergebnisse**

   |ResultValue|
   |------|
   |0.5|

   Wenn Sie versuchen, einen numerischen Index zu verwenden, um einen Wert aus dieser Reihe zu erhalten, erhalten Sie eine Fehlermeldung.

## <a name="next-steps"></a>Nächste Schritte

Als Nächstes erstellen Sie ein Vorhersagemodell mithilfe von python in SQL Server.

> [!div class="nextstepaction"]
> [Erstellen und bewerten eines Vorhersagemodells in python](quickstart-python-train-score-model.md)

Weitere Informationen zum SQL Server Machine Learning Services finden Sie unter:

- [Was ist SQL Server Machine Learning Services (python und R)?](../what-is-sql-server-machine-learning.md)
