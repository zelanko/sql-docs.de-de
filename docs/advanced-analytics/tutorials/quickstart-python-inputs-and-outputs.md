---
title: Schnellstart für das Arbeiten mit Eingaben und Ausgaben in python
description: In dieser Schnellstartanleitung für das Python-Skript in SQL Server erfahren Sie, wie Sie Eingaben und Ausgaben in der gespeicherten System Prozedur sp_execute_external_script strukturieren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 10c62f78ff2ac23e33ad251a07ed8f3689f79843
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715463"
---
# <a name="quickstart-handle-inputs-and-outputs-using-python-in-sql-server"></a>Schnellstart: Behandeln von Eingaben und Ausgaben mithilfe von python in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In dieser Schnellstartanleitung erfahren Sie, wie Sie bei Verwendung von python in SQL Server Machine Learning Services Eingaben und Ausgaben verarbeiten.

Standardmäßig akzeptiert [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) ein einzelnes Eingabe DataSet, das in der Regel in Form einer gültigen SQL-Abfrage angegeben wird.

Andere Eingabetypen können als SQL-Variablen übergeben werden. Sie können z. b. ein trainiertes Modell als Variable übergeben, indem Sie eine Serialisierungsfunktion wie z. b. [Pickle](https://docs.python.org/3.0/library/pickle.html) oder [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) verwenden, um das Modell in einem binären Format zu schreiben.

Die gespeicherte Prozedur gibt einen einzelnen python [Pandas](https://pandas.pydata.org/pandas-docs/stable/index.html) -dataframe als Ausgabe zurück, aber Sie können auch skalare und Modelle als Variablen ausgeben. Beispielsweise können Sie ein trainiertes Modell als binäre Variable ausgeben und an eine T-SQL-INSERT-Anweisung übergeben, um das Modell in eine Tabelle zu schreiben. Sie können auch Diagramme (im Binärformat) oder skalare generieren (einzelne Werte, z. b. das Datum und die Uhrzeit, die verstrichene Zeit zum Trainieren des Modells usw.).

## <a name="prerequisites"></a>Vorraussetzungen

Eine vorherige Schnellstartanleitung: [überprüfen, ob python in SQL Server vorhanden](quickstart-python-verify.md)ist, enthält Informationen und Links zum Einrichten der für diese Schnellstartanleitung erforderlichen python-Umgebung.

## <a name="create-the-source-data"></a>Erstellen der Quelldaten

Erstellen Sie eine kleine Tabelle mit Testdaten, indem Sie die folgende T-SQL-Anweisung ausführen:

```sql
CREATE TABLE PythonTestData (col1 INT NOT NULL)
INSERT INTO PythonTestData VALUES (1);
INSERT INTO PythonTestData VALUES (10);
INSERT INTO PythonTestData VALUES (100);
GO
```

Wenn die Tabelle erstellt wurde, verwenden Sie die folgende Anweisung zum Abfragen der Tabelle:
  
```sql
SELECT * FROM PythonTestData
```

**Ergebnisse**

![Inhalt der Tabelle "pythontestdata"](./media/select-pythontestdata.png)

## <a name="inputs-and-outputs"></a>Eingaben und Ausgaben

Betrachten wir nun die standardmäßigen Eingabe-und Ausgabevariablen von sp_execute_external_script `InputDataSet` : `OutputDataSet`und.

1. Sie können die Daten aus der Tabelle als Eingabe für das Python-Skript erhalten. Führen Sie die folgende Anweisung aus. Er ruft die Daten aus der Tabelle ab, führt einen Roundtrip durch die python-Laufzeit durch und gibt die Werte mit dem Spaltennamen *newcolname*zurück.

    Die von der Abfrage zurückgegebenen Daten werden an die python-Laufzeit übergeben, die die Daten als Pandas-dataframe an SQL-Datenbank zurückgibt. Die with Result Sets-Klausel definiert das Schema der zurückgegebenen Datentabelle für die SQL-Datenbank.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    **Ergebnisse**

    ![Ausgabe des python-Skripts, das Daten aus einer Tabelle zurückgibt](./media/python-output-pythontestdata.png)

2. Ändern Sie den Namen der Eingabe-oder Ausgabevariablen. Das obige Skript verwendet die Standardnamen für die Eingabe-und Ausgabevariablen, input _DataSet_ und _outputdataset_. Verwenden Sie die *@input_data_1* -Variable, um die Eingabedaten zu definieren, die input _DataSet_zugeordnet sind.

    In diesem Skript wurden die Namen der Ausgabe-und Eingabevariablen für die gespeicherte Prozedur in *SQL_out* und *SQL_in*geändert:

    ```sql
    EXECUTE sp_execute_external_script
      @language = N'Python'
      , @script = N'SQL_out = SQL_in'
      , @input_data_1 = N' SELECT 12 as Col;'
      , @input_data_1_name  = N'SQL_in'
      , @output_data_1_name =  N'SQL_out'
      WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    Die Groß-/Kleinschreibung der Eingabe- `@input_data_1_name` und `@output_data_1_name` Ausgabevariablen in und muss mit der Groß-/Kleinschreibung des `@script`python-Codes in abgeglichen werden, da bei python die Groß-/Kleinschreibung beachtet

    Nur eine Eingabedataset kann als Parameter übergeben werden, und Sie können nur ein Dataset zurückgeben. Allerdings können Sie andere Datasets innerhalb Ihres python-Codes abrufen und können zusätzlich zum DataSet Ausgaben anderer Typen zurückgeben. Sie können auch das Schlüsselwort OUTPUT zu einem beliebigen Parameter hinzufügen, damit es mit den Ergebnissen zurückgegeben wird. 

    Die `WITH RESULT SETS` -Anweisung definiert das Schema für die Daten, die in SQL Server verwendet werden. Sie müssen SQL-kompatible Datentypen für jede Spalte bereitstellen, die Sie aus python zurückgeben. Sie können die Schema Definition auch zum Bereitstellen neuer Spaltennamen verwenden, da Sie die Spaltennamen nicht aus dem python Data. Frame verwenden müssen.

3. Sie können auch Werte mithilfe des python-Skripts generieren und die Zeichenfolge _@input_data_1_ der Eingabe Abfrage leer lassen.

    ```sql
    EXECUTE sp_execute_external_script
    @language = N'Python'
    , @script = N'
    import pandas as pd
    mytextvariable = pandas.Series(["hello", " ", "world"]);
    OutputDataSet = pd.DataFrame(mytextvariable);'
    , @input_data_1 = N''
    WITH RESULT SETS (([Col1] CHAR(20) NOT NULL));
    ```

    **Ergebnisse**

    ![Abfragen von Ergebnissen @script mithilfe von als Eingabe](./media/python-data-generated-output.png)

## <a name="next-steps"></a>Nächste Schritte

Untersuchen Sie einige der Probleme, die bei der Übergabe von Tabellendaten zwischen Python und SQL Server auftreten können.

> [!div class="nextstepaction"]
> [Schnellstart: Python-Datenstrukturen in SQL Server](quickstart-python-data-structures.md)
