---
title: 'Schnellstart: Ausführen von Python-Skripts'
description: Ausführen einfacher Python-Skripts mit SQL Server Machine Learning Services In diesem Artikel erfahren Sie, wie Sie die gespeicherte Prozedur sp_execute_external_script verwenden, um das Skript in einer SQL Server-Instanz auszuführen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/27/2020
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8c1347d58f0b8a4014a51a220b6ecded5a343082
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "81116353"
---
# <a name="quickstart-run-simple-python-scripts-with-sql-server-machine-learning-services"></a>Schnellstart: Ausführen einfacher Python-Skripts mit SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Schnellstart führen Sie einige einfache Python-Skripts mithilfe von [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) aus. Sie erfahren, wie Sie die gespeicherte Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) verwenden, um das Skript in einer SQL Server-Instanz auszuführen.

## <a name="prerequisites"></a>Voraussetzungen

- Für diesen Schnellstart benötigen Sie Zugriff auf eine SQL Server-Instanz mit [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md), für die die Python-Sprache installiert ist.

- Außerdem benötigen Sie ein Tool zum Ausführen von SQL-Abfragen, die Python-Skripts enthalten. Sie können diese Skripts mit einem beliebigen Tool für die Datenbankverwaltung oder -abfrage verwalten, sofern dieses eine Verbindung mit SQL Server-Instanzen herstellen und T-SQL-Abfragen oder gespeicherte Prozeduren ausführen kann. Für diesen Schnellstart wird [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) verwendet.

## <a name="run-a-simple-script"></a>Ausführen eines einfachen Skripts

Sie können ein Python-Skript ausführen, indem Sie es als Argument an die gespeicherte Systemprozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) übergeben.
Diese gespeicherte Systemprozedur startet die Python-Runtime im Kontext von SQL Server, übergibt Daten an Python, verwaltet Sitzungen von Python-Benutzern sicher und gibt alle Ergebnisse an den Client zurück.

In den folgenden Schritten führen Sie dieses Python-Beispielskript in Ihrer SQL Server-Instanz aus:

```python
a = 1
b = 2
c = a/b
d = a*b
print(c, d)
```

1. Öffnen Sie ein neues Abfragefenster in **SQL Server Management Studio**, das mit Ihrer SQL Server-Instanz verbunden ist.

1. Übergeben Sie das gesamte Python-Skript an die gespeicherte Prozedur `sp_execute_external_script`.

   Das Skript wird durch das `@script`-Argument übergeben. Das `@script`-Argument darf nur aus zulässigem Python-Code bestehen.

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c, d)
    '
    ```

1. Das korrekte Ergebnis wird berechnet, und die Python-Funktion `print` gibt das Ergebnis im **Meldungsfenster** zurück.

   Die Ausgabe könnte beispielsweise wie folgt aussehen:

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script:
    0.5 2
    ```

## <a name="run-a-hello-world-script"></a>Ausführen eines „Hello World“-Skripts

In einem typischen Beispielskript wird nur die Zeichenfolge „Hallo Welt“ (oder „Hello World“) ausgegeben. Führen Sie den folgenden Befehl aus.

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'OutputDataSet = InputDataSet'
    , @input_data_1 = N'SELECT 1 AS hello'
WITH RESULT SETS(([Hello World] INT));
GO
```

Folgende Eingaben sind für die gespeicherte Prozedur `sp_execute_external_script` möglich:

| | |
|-|-|
| @language | definiert die aufzurufende Spracherweiterung (hier Python) |
| @script | definiert die Befehle, die an die Python-Runtime übergeben werden<br>Ihr gesamtes Python-Skript muss von diesem Argument als Unicode-Text umschlossen sein. Sie können den Text auch einer Variablen des Typs **nvarchar** hinzufügen und die Variable anschließend aufrufen. |
| @input_data_1 | Die von der Abfrage zurückgegebenen Daten werden an die Python-Runtime übergeben, die die Daten als Datenrahmen an SQL Server zurückgibt. |
|WITH RESULT SETS | Mit dieser Klausel wird das Schema der zurückgegebenen Datentabelle für SQL Server definiert und in diesem Fall „Hello World“ als Spaltenname und **int** als Datentyp hinzugefügt. |

Der Befehl gibt folgenden Text aus:

| Hello World |
|-------------|
| 1 |

## <a name="use-inputs-and-outputs"></a>Verwenden von Eingaben und Ausgaben

Standardmäßig akzeptiert `sp_execute_external_script` ein einzelnes Dataset als Eingabe, das in der Regel in Form einer gültigen SQL-Abfrage angegeben wird. Anschließend wird ein einzelner Python-Datenrahmen als Ausgabe zurückgegeben.

Verwenden Sie vorerst die standardmäßig festgelegten Eingabe- und Ausgabevariablen von `sp_execute_external_script`: **InputDataSet** und **OutputDataSet**.

1. Erstellen Sie eine kleine Tabelle mit Testdaten.

    ```sql
    CREATE TABLE PythonTestData (col1 INT NOT NULL)
    
    INSERT INTO PythonTestData
    VALUES (1);
    
    INSERT INTO PythonTestData
    VALUES (10);
    
    INSERT INTO PythonTestData
    VALUES (100);
    GO
    ```

1. Verwenden Sie die `SELECT`-Anweisung zum Abfragen der Tabelle.
  
    ```sql
    SELECT *
    FROM PythonTestData
    ```

    **Ergebnisse**

    ![Inhalt der PythonTestData-Tabelle](./media/select-pythontestdata.png)

1. Führen Sie folgendes Python-Skript aus. Es ruft die Daten mithilfe der `SELECT`-Anweisung aus der Tabelle ab, übergibt sie über die Python-Runtime und gibt sie anschließend als Datenrahmen zurück. Die Klausel `WITH RESULT SETS` definiert das Schema der zurückgegeben Datentabelle für SQL und fügt den Spaltennamen *NewColName* hinzu.

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    **Ergebnisse**

    ![Ausgabe des Python-Skripts, das Daten aus einer Tabelle zurückgibt](./media/python-output-pythontestdata.png)

1. Ändern Sie nun die Namen der Eingabe- und Ausgabevariablen. Standardmäßig werden die Eingabe- und Ausgabevariablen **InputDataSet** und **OutputDataSet** verwendet. In dem folgenden Skript werden die Namen in **SQL_in** und **SQL_out** geändert:

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'SQL_out = SQL_in;'
        , @input_data_1 = N'SELECT 12 as Col;'
        , @input_data_1_name  = N'SQL_in'
        , @output_data_1_name = N'SQL_out'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    Beachten Sie, dass Python Groß- und Kleinschreibung beachtet. Die im Python-Skript verwendeten Eingabe- und Ausgabevariablen (**SQL_out** und **SQL_in**) müssen mit den mit `@input_data_1_name` und `@output_data_1_name` definierten Namen (Groß-/Kleinschreibung beachten) übereinstimmen.

   > [!TIP]
   > Nur ein Eingabedataset kann als Parameter übergeben werden, und Sie können nur ein Dataset zurückgeben. Allerdings können Sie andere Datasets innerhalb Ihres Python-Codes aufrufen und Ausgaben und andere Typen zusätzlich zum Dataset zurückgeben. Außerdem können Sie auch allen Parametern das Schlüsselwort OUTPUT hinzufügen, damit es zusammen mit den Ergebnissen zurückgegeben wird.

1. Sie können über das Python-Skript auch Werte ohne Eingabedaten generieren, indem keine Eingabedaten für `@input_data_1` festgelegt werden.

   Das folgende Skript gibt den Text „hello“ und „world“ aus.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   import pandas as pd
   mytextvariable = pandas.Series(["hello", " ", "world"]);
   OutputDataSet = pd.DataFrame(mytextvariable);
   '
       , @input_data_1 = N''
   WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
   ```

   **Ergebnisse**

   ![Abfrageergebnisse mit @script als Eingabe](./media/python-data-generated-output.png)

> [!NOTE]
> Python verwendet führende Leerzeichen für Gruppenanweisungen. Wenn also das eingebettete Python-Skript mehrere Zeilen wie im vorhergehenden Skript umfasst, versuchen Sie nicht, die Python-Befehle einzuziehen, um mit den SQL-Befehlen übereinstimmen zu können. Dieses Skript erzeugt beispielsweise einen Fehler:

  ```text
  EXECUTE sp_execute_external_script @language = N'Python'
      , @script = N'
      import pandas as pd
      mytextvariable = pandas.Series(["hello", " ", "world"]);
      OutputDataSet = pd.DataFrame(mytextvariable);
      '
      , @input_data_1 = N''
  WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
  ```

## <a name="check-python-version"></a>Überprüfung der Python-Version

Wenn Sie herausfinden möchten, welche Version von Python auf Ihrer SQL Server-Instanz installiert ist, führen Sie folgendes Skript aus:

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import sys
print(sys.version)
'
GO
```

Die Python-Funktion `print` gibt die Version im **Meldungsfenster** zurück. In der folgenden Beispielausgabe sehen Sie, dass in diesem Fall Version 3.5.2 von Python installiert ist.

**Ergebnisse**

```text
STDOUT message(s) from external script: 
3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
```

## <a name="list-python-packages"></a>Auflistung der Python-Pakete

Microsoft bietet eine Reihe von Python-Pakete an, die mit SQL Server Machine Learning Services in Ihrer SQL Server-Instanz vorinstalliert sind.

Führen Sie das folgende Skript aus, um eine Liste der installierten Python-Pakete einschließlich der Version zu erhalten.

```SQL
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import pkg_resources
import pandas
dists = [str(d) for d in pkg_resources.working_set]
OutputDataSet = pandas.DataFrame(dists)
'
WITH RESULT SETS(([Package] NVARCHAR(max)))
GO
```

Die Liste stammt aus `pkg_resources.working_set` in Python und wird an SQL als Datenrahmen zurückgegeben.

**Ergebnisse**

:::image type="content" source="media/python-package-list.png" alt-text="Auflisten aller installierten Python-Pakete":::

## <a name="next-steps"></a>Nächste Schritte

Befolgen Sie diesen Schnellstart, um die Verwendung von Datenstrukturen mit Python in SQL Server Machine Learning Services zu erlernen:

> [!div class="nextstepaction"]
> [Schnellstart: Verarbeiten von Datentypen und Objekten mithilfe von Python in SQL Server Machine Learning Services](quickstart-python-data-structures.md)

Weitere Informationen zur Verwendung von Python in SQL Server Machine Learning Services finden Sie in den folgenden Artikeln:

- [Schreiben erweiterter Python-Funktionen mit SQL Server Machine Learning Services](quickstart-python-functions.md)
- [Erstellen und Bewerten eines Vorhersagemodells in Python mit SQL Server Machine Learning Services](quickstart-python-train-score-model.md)
- [Was ist SQL Server Machine Learning Services (Python und R)?](../what-is-sql-server-machine-learning.md)
