---
title: Einfache python-Skripts erstellen und ausführen
titleSuffix: SQL Server Machine Learning Services
description: Erstellen und führen Sie einfache python-Skripts in einer SQL Server Instanz mit SQL Server Machine Learning Services aus.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/17/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a6f7fe62f746a8f6e74ebdf9f766b76c0edc720a
ms.sourcegitcommit: 9221a693d4ab7ae0a7e2ddeb03bd0cf740628fd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71204297"
---
# <a name="quickstart-create-and-run-simple-python-scripts-with-sql-server-machine-learning-services"></a>Schnellstart: Erstellen und Ausführen einfacher python-Skripts mit SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In dieser Schnellstartanleitung erstellen Sie mithilfe [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md)eine Reihe einfacher python-Skripts und führen diese aus. Sie erfahren, wie Sie ein wohl geformtes Python-Skript in die gespeicherte Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) einschließen und das Skript in einer SQL Server-Instanz ausführen.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Diese Schnellstartanleitung erfordert Zugriff auf eine Instanz von SQL Server mit [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) , auf der die Python-Sprache installiert ist.

- Außerdem benötigen Sie ein Tool zum Ausführen von SQL-Abfragen, die python-Skripts enthalten. Sie können diese Skripts mit einem beliebigen Daten Bank Verwaltungs-oder Abfrage Tool ausführen, solange eine Verbindung mit einer SQL Server Instanz hergestellt und eine T-SQL-Abfrage oder eine gespeicherte Prozedur ausgeführt werden kann. In diesem Schnellstart wird [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)verwendet.

## <a name="run-a-simple-script"></a>Ausführen eines einfachen Skripts

Wenn Sie ein Python-Skript ausführen möchten, übergeben Sie es als Argument an die gespeicherte System Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
Diese gespeicherte System Prozedur startet die python-Laufzeit im Kontext SQL Server, übergibt Daten an Python, verwaltet python-Benutzersitzungen sicher und gibt alle Ergebnisse an den Client zurück.

In den folgenden Schritten führen Sie das python-Beispielskript in Ihrer SQL Server Instanz aus:

```python
a = 1
b = 2
c = a/b
d = a*b
print(c, d)
```

1. Öffnen Sie ein neues Abfragefenster in **SQL Server Management Studio** , das mit Ihrer SQL Server-Instanz verbunden ist.

1. Übergeben Sie das gesamte Python-Skript `sp_execute_external_script` an die gespeicherte Prozedur.

   Das Skript wird durch das `@script` -Argument übermittelt. Alles innerhalb des `@script` Arguments muss gültiger Python-Code sein.

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

1. Das korrekte Ergebnis wird berechnet, und die `print` python-Funktion gibt das Ergebnis an das Fenster **Meldungen** zurück.

   Dies sollte in etwa wie folgt aussehen.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script:
    0.5 2
    ```

## <a name="run-a-hello-world-script"></a>Ausführen eines Hallo Welt Skripts

Ein typisches Beispielskript ist ein Beispiel, das nur die Zeichenfolge "Hallo Welt" ausgibt. Führen Sie den folgenden Befehl aus.

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'OutputDataSet = InputDataSet'
    , @input_data_1 = N'SELECT 1 AS hello'
WITH RESULT SETS(([Hello World] INT));
GO
```

Zu den Eingaben `sp_execute_external_script` für die gespeicherte Prozedur gehören:

| | |
|-|-|
| @language | definiert die aufzurufende Spracherweiterung, in diesem Fall python. |
| @script | definiert die Befehle, die an die python-Laufzeit geleitet werden<br>Das gesamte Python-Skript muss in dieses Argument als Unicode-Text eingeschlossen werden. Sie können den Text auch einer Variablen des Typs **nvarchar** hinzufügen und dann die Variable |
| @input_data_1 | von der Abfrage zurückgegebene Daten, die an die python-Laufzeit zurückgegeben werden, die die Daten zurückgibt, die als Datenrahmen SQL Server werden. |
|WITH RESULT SETS | Klausel definiert das Schema der zurückgegebenen Datentabelle für SQL Server. in diesem Fall wird "Hallo Welt" als Spaltenname und " **int** " für den Datentyp hinzugefügt. |

Der Befehl gibt den folgenden Text aus:

| Hallo Welt |
|-------------|
| 1 |

## <a name="use-inputs-and-outputs"></a>Verwenden von Eingaben und Ausgaben

Standardmäßig `sp_execute_external_script` akzeptiert ein einzelnes Dataset als Eingabe, das in der Regel in Form einer gültigen SQL-Abfrage angegeben wird. Anschließend wird ein einzelner python-Datenrahmen als Ausgabe zurückgegeben.

Verwenden Sie vorerst die standardmäßigen Eingabe-und Ausgabevariablen von `sp_execute_external_script`: **Input DataSet** und **outputdataset**.

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

1. Verwenden Sie `SELECT` die-Anweisung, um die Tabelle abzufragen.
  
    ```sql
    SELECT *
    FROM PythonTestData
    ```

    **Ergebnisse**

    ![Inhalt der Tabelle "pythontestdata"](./media/select-pythontestdata.png)

1. Führen Sie das folgende Python-Skript aus. Die Daten werden mithilfe der `SELECT` -Anweisung aus der-Tabelle abgerufen, an die python-Laufzeit weitergeleitet, und die Daten werden als Datenrahmen zurückgegeben. Die `WITH RESULT SETS` -Klausel definiert das Schema der zurückgegebenen Datentabelle für SQL, wobei der Spaltenname *newcolname*hinzugefügt wird.

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    **Ergebnisse**

    ![Ausgabe des python-Skripts, das Daten aus einer Tabelle zurückgibt](./media/python-output-pythontestdata.png)

1. Ändern Sie nun die Namen der Eingabe-und Ausgabevariablen. Die Standardnamen für die Eingabe-und Ausgabevariablen sind input **DataSet** und **outputdataset**. das folgende Skript ändert die Namen in **SQL_in** und **SQL_out**:

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'SQL_out = SQL_in;'
        , @input_data_1 = N'SELECT 12 as Col;'
        , @input_data_1_name  = N'SQL_in'
        , @output_data_1_name = N'SQL_out'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    Beachten Sie, dass bei Python die Groß-/Kleinschreibung unterschieden wird. Die im Python-Skript verwendeten Eingabe-und Ausgabevariablen (**SQL_out**, **SQL_in**) müssen mit den in `@input_data_1_name` bzw. `@output_data_1_name` definierten Namen einschließlich Groß-/Kleinschreibung übereinstimmen.

   > [!TIP]
   > Nur eine Eingabedataset kann als Parameter übergeben werden, und Sie können nur ein Dataset zurückgeben. Allerdings können Sie andere Datasets innerhalb Ihres python-Codes abrufen und können zusätzlich zum DataSet Ausgaben anderer Typen zurückgeben. Sie können auch das Schlüsselwort OUTPUT zu einem beliebigen Parameter hinzufügen, damit es mit den Ergebnissen zurückgegeben wird.

1. Sie können Werte auch nur mit dem Python-Skript ohne Eingabedaten generieren (`@input_data_1` ist auf "blank" festgelegt).

   Das folgende Skript gibt den Text "Hello" und "World" aus.

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

   ![Abfragen von Ergebnissen @script mithilfe von als Eingabe](./media/python-data-generated-output.png)

> [!NOTE]
> Python verwendet führende Leerzeichen, um-Anweisungen zu gruppieren. Wenn das imeingebetteten Python-Skript mehrere Zeilen umfasst, wie im vorangehenden Skript, versuchen Sie daher nicht, die python-Befehle als Übereinstimmung mit den SQL-Befehlen einzuschließen. Dieses Skript erzeugt z. b. einen Fehler:

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

## <a name="check-python-version"></a>Python-Version überprüfen

Wenn Sie sehen möchten, welche Python-Version in Ihrer SQL Server Instanz installiert ist, führen Sie das folgende Skript aus.

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import sys
print(sys.version)
'
GO
```

Die python `print` -Funktion gibt die Version an das Fenster **Meldungen** zurück. In der folgenden Beispielausgabe können Sie sehen, dass die Python-Version 3.5.2 in diesem Fall installiert ist.

**Ergebnisse**

```text
STDOUT message(s) from external script: 
3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
```

## <a name="list-python-packages"></a>Auflisten von Python-Paketen

Microsoft stellt eine Reihe von Python-Paketen bereit, die mit SQL Server Machine Learning Services in Ihrer SQL Server Instanz vorinstalliert sind.

Führen Sie das folgende Skript aus, um eine Liste der installierten Python-Pakete anzuzeigen, einschließlich der Version.

```SQL
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import pip
for i in pip.get_installed_distributions():
    print(i)
'
GO
```

Die Ausgabe erfolgt `pip.get_installed_distributions()` in Python und wird als `STDOUT` Nachrichten zurückgegeben.

**Ergebnisse**

```text
STDOUT message(s) from external script:
xlwt 1.2.0
XlsxWriter 0.9.6
xlrd 1.0.0
win-unicode-console 0.5
widgetsnbextension 2.0.0
wheel 0.29.0
Werkzeug 0.12.1
wcwidth 0.1.7
unicodecsv 0.14.1
traitlets 4.3.2
tornado 4.4.2
toolz 0.8.2
. . .
```

## <a name="next-steps"></a>Nächste Schritte

Um ein Machine Learning-Modell mithilfe von python in SQL Server zu erstellen, befolgen Sie diese Schnellstartanleitung:

> [!div class="nextstepaction"]
> [Erstellen und bewerten eines Vorhersagemodells in Python mit SQL Server Machine Learning Services](quickstart-python-train-score-model.md)

Weitere Informationen zu SQL Server Machine Learning Services finden Sie in den folgenden Artikeln.

- [Verarbeiten von Datentypen und Objekten mithilfe von python in SQL Server Machine Learning Services](quickstart-python-data-structures.md)
- [Was ist SQL Server Machine Learning Services (python und R)?](../what-is-sql-server-machine-learning.md)
