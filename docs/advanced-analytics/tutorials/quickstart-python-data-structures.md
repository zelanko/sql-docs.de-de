---
title: 'Schnellstart: Python-Datenstrukturen'
description: In diesem Schnellstart erfahren Sie, wie Sie in Python und SQL Server Machine Learning Services mit Datenstrukturen und Datenobjekten arbeiten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/27/2020
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0f04e021664a92241c8c029d296a298b10c142d2
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "76831903"
---
# <a name="quickstart-data-structures-and-objects-using-python-in-sql-server-machine-learning-services"></a>Schnellstart: Verarbeiten von Datentypen und Objekten mithilfe von Python in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Schnellstart erfahren Sie, wie Sie Datenstrukturen mit Python in SQL Server Machine Learning Services verwenden.

SQL Server ist vom Python-Paket **pandas** abhängig, das hervorragend für die Arbeit mit Tabellendaten geeignet ist. Sie können allerdings nicht davon ausgehen, dass Sie nur einen Skalar von Python an SQL Server übergeben müssen, damit alles einwandfrei funktioniert. Im Rahmen dieses Schnellstarts überprüfen Sie einige grundlegende Datenstrukturdefinitionen. Dies soll Sie auf zusätzliche Probleme vorbereiten, die bei der Übergabe von Tabellendaten zwischen Python und SQL Server auftreten können.

Sie sollten sich im Vorfeld über die folgenden Konzepte informieren:

- Ein Datenrahmen ist eine Tabelle mit _mehreren_ Spalten.
- Eine einzelne Spalte eines Datenrahmens ist ein listenähnliches Objekt, das als Reihe bezeichnet wird.
- Ein einzelner Wert eines Datenrahmens wird als Zelle bezeichnet, und der Zugriff erfolgt über den Index.

Wie würden Sie das einzelne Ergebnis einer Berechnung als Datenrahmen verfügbar machen, wenn für data.frame ein Tabellenformat verlangt wird? Eine Möglichkeit ist die Darstellung des einzelnen Skalarwerts als Reihe, die ganz einfach in einen Datenrahmen konvertiert werden kann. 

> [!NOTE]
> Beim Zurückgeben von Datumsangaben verwendet Python in SQL DATETIME mit dem eingeschränkten Datumsbereich von 1753-01-01 (-53690) bis 9999-12-31 (2958463). 

## <a name="prerequisites"></a>Voraussetzungen

- Für diesen Schnellstart benötigen Sie Zugriff auf eine SQL Server-Instanz mit [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md), für die die Python-Sprache installiert ist.

- Außerdem benötigen Sie ein Tool zum Ausführen von SQL-Abfragen, die Python-Skripts enthalten. Sie können diese Skripts mit einem beliebigen Tool für die Datenbankverwaltung oder -abfrage verwalten, sofern dieses eine Verbindung mit SQL Server-Instanzen herstellen und T-SQL-Abfragen oder gespeicherte Prozeduren ausführen kann. Für diesen Schnellstart wird [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) verwendet.

## <a name="scalar-value-as-a-series"></a>Skalarwert als Reihe

In diesem Beispiel wird einfache Mathematik verwendet und ein Skalar in eine Reihe konvertiert.

1. Für eine Reihe wird ein Index benötigt, den Sie manuell (wie hier gezeigt) oder programmgesteuert zuweisen können.

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

   Da die Reihe nicht in ein data.frame-Format konvertiert wurde, werden die Werte im Fenster „Meldungen“angezeigt – und zwar in tabellarischer Form.

   **Ergebnisse**

   ```text
   STDOUT message(s) from external script: 
   0.5
   simple math example 1    0.5
   dtype: float64
   ```

1. Sie können Reihen verlängern, indem Sie mithilfe eines Arrays neue Werte hinzufügen. 

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

1. Wenn Sie die Anzahl der **Indexwerte** erhöhen, aber keine neuen **Datenwerte** hinzufügen, werden die Datenwerte mehrfach verwendet, um die Reihen auszufüllen.

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

## <a name="convert-series-to-data-frame"></a>Konvertieren von Reihen in Datenrahmen

Auch wenn Sie die mathematischen Skalarergebnisse in ein Tabellenformat konvertiert haben, müssen Sie sie in ein Format konvertieren, das SQL Server verarbeiten kann.

1. Sie können Reihe in ein data.frame-Format konvertieren, indem Sie die Pandas-Methode [DataFrame](https://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) aufrufen.

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

   Das Ergebnis wird unten angezeigt. Auch wenn Sie den Index verwenden, um bestimmte Werte aus data.frame zu erhalten, sind die Indexwerte nicht Teil der Ausgabe.

   **Ergebnisse**

   |ResultValue|
   |------|
   |0.5|
   |2|

## <a name="output-values-into-dataframe"></a>Ausgeben von Werten in data.frame

Im Folgenden sollten Sie spezifische Werte aus zwei Datenreihen der mathematischen Ergebnisse im data.frame-Format ausgeben. Die erste Datenreihe verfügt über einen Index von sequenziellen Werten, die von Python generiert werden. Die zweite Datenreihe verwendet einen beliebigen Index von Zeichenfolgenwerten.

1. Im folgenden Beispiel wird mithilfe eines ganzzahligen Index ein Wert aus der Reihe abgerufen.

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

   Wie bereits erwähnt, beginnt der automatisch generierte Index bei 0. Verwenden Sie einen Indexwert außerhalb des gültigen Bereichs, um zu prüfen, was dadurch passiert.

1. Rufen Sie nun mithilfe eines Zeichenfolgenindex einen einzelnen Wert aus dem anderen Datenrahmen ab.

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

   Wenn Sie versuchen, einen numerischen Index zu verwenden, um einen Wert aus dieser Reihe abzurufen, wird ein Fehler ausgelöst.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Schreiben von erweiterten Python-Funktionen in SQL Server finden Sie in diesem Schnellstart:

> [!div class="nextstepaction"]
> [Schreiben erweiterter Python-Funktionen mit SQL Server Machine Learning Services](quickstart-python-functions.md)

Weitere Informationen zur Verwendung von Python in SQL Server Machine Learning Services finden Sie in den folgenden Artikeln:

- [Erstellen und Bewerten eines Vorhersagemodells in Python](quickstart-python-train-score-model.md)
- [Was ist SQL Server Machine Learning Services (Python und R)?](../what-is-sql-server-machine-learning.md)
