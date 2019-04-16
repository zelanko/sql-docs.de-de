---
title: Schnellstart für das Arbeiten mit Eingaben und Ausgaben in Python - SQL Server-Machine Learning
description: Erfahren Sie in dieser schnellstartanleitung für die Python-Skript in SQL Server, wie Sie ein- und Ausgaben für die gespeicherte Systemprozedur Sp_execute_external_script strukturieren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: a778c4a65b9e3f4cbf4ed77cff46e9061d4b6a8a
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59583223"
---
# <a name="quickstart-handle-inputs-and-outputs-using-python-in-sql-server"></a>Schnellstart: Verarbeiten von Eingaben und Ausgaben, die mithilfe von Python in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Schnellstart wird gezeigt, wie Eingaben verarbeiten und gibt bei Verwendung von Python in SQL Server-Machine Learning-Dienste aus.

In der Standardeinstellung [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) akzeptiert ein einzelnes Eingabe-Dataset, das Sie in der Regel in Form von einer gültigen SQL-Abfrage zu geben.

Andere Arten von Eingaben, die als SQL-Variablen übergeben werden können: beispielsweise, Sie können übergeben ein trainiertes Modells als Variable mithilfe einer Serialisierungsfunktion wie [Pickle](https://docs.python.org/3.0/library/pickle.html) oder [Rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) , schreiben das Modell ein binäres Format.

Die gespeicherte Prozedur gibt ein einzelnen Python [Pandas](https://pandas.pydata.org/pandas-docs/stable/index.html) Datenrahmen als Ausgabe, aber Sie können auch skalare und Modelle als Variablen ausgeben. Sie können z. B. die Ausgabe eines trainierten Modells als binäre Variable und übergeben, um eine T-SQL INSERT-Anweisung, um das Modell in einer Tabelle zu schreiben. Sie können auch Diagramme (im binären Format) oder skalare generieren (einzelne Werte, z. B. Datum und Uhrzeit, die verstrichene Zeit zum Trainieren des Modells und so weiter).

## <a name="prerequisites"></a>Erforderliche Komponenten

Einen vorherigen schnellstartanleitung [Python überprüfen, die in SQL Server vorhanden ist](quickstart-python-verify.md), enthält Informationen und links für das Einrichten der Python-Umgebung, die im Rahmen dieser schnellstartanleitung benötigt.

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

![Inhalt der Tabelle PythonTestData](./media/select-pythontestdata.png)

## <a name="inputs-and-outputs"></a>Eingaben und Ausgaben

Sehen wir uns die standardmäßigen Eingabe- und Variablen von Sp_execute_external_script: `InputDataSet` und `OutputDataSet`.

1. Sie können die Daten aus der Tabelle als Eingabe für das R-Skript abrufen. Führen Sie folgende Anweisung ein. Ruft die Daten aus der Tabelle ab, gibt die Werte mit den Namen der Spalte zurück und macht einen Roundtrip über die R-Laufzeit *NewColName*.

    Die von der Abfrage zurückgegebenen Daten werden an die R-Laufzeit übergeben, die die Daten in SQL-Datenbank als dataframe zurückgibt. Die WITH RESULT SETS-Klausel definiert das Schema der zurückgegeben Datentabelle für SQL-Datenbank.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    **Ergebnisse**

    ![Ausgabe von Python-Skript, das Daten aus einer Tabelle zurückgegeben.](./media/python-output-pythontestdata.png)

2. Ändern wir den Namen der Eingabe- oder Variablen. Das obige Skript verwendet die Standardeingabe und eingabevariablennamen _"inputdataset"_ und _"outputdataset"_. Definieren Sie die Eingabedaten _InputDatSet_, Sie verwenden die *@input_data_1* Variable.

    In diesem Skript wurde die Namen der Ausgabe- und der Eingabevariablen für die gespeicherte Prozedur zu geändert *SQL_out* und *SQL_in*:

    ```sql
    EXECUTE sp_execute_external_script
      @language = N'Python'
      , @script = N'SQL_out = SQL_in'
      , @input_data_1 = N' SELECT 12 as Col;'
      , @input_data_1_name  = N'SQL_in'
      , @output_data_1_name =  N'SQL_out'
      WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    Im Fall von Eingabe- und Variablen in `@input_data_1_name` und `@output_data_1_name` muss die Groß-/Kleinschreibung in der Python-Code in entsprechen `@script`, wie Sie Python Groß-/Kleinschreibung beachtet wird.

    Nur eine Eingabedataset kann als Parameter übergeben werden, und Sie können nur ein Dataset zurückgeben. Allerdings können Sie andere Datasets innerhalb Ihres Python-Codes aufrufen, und Sie können die Ausgaben für andere Typen zusätzlich zum Dataset zurückgeben. Sie können auch das Schlüsselwort OUTPUT zu einem beliebigen Parameter hinzufügen, damit es mit den Ergebnissen zurückgegeben wird. 

    Die `WITH RESULT SETS` -Anweisung definiert das Schema für die Daten, die verwendet wird, in SQL Server. Sie müssen SQL-kompatible Datentypen für jede Spalte angeben, die Sie aus Python zurückgeben. Sie können die Schemadefinition verwenden, um neue Spaltennamen bereitzustellen zu verwenden, da Sie nicht benötigen, verwenden Sie die Spaltennamen aus der Python-Datenrahmen (Data.Frame).

3. Sie können auch Werte, die mit dem Python-Skript generieren, und lassen Sie die Zeichenfolge der Eingabeabfrage in _@input_data_1_ leer.

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

    ![Ergebnisse der Abfrage mit @script als Eingabe](./media/python-data-generated-output.png)

## <a name="next-steps"></a>Nächste Schritte

Überprüfen Sie einige der Probleme, die beim Übergeben von Tabellendaten zwischen Python und SQL Server auftreten können.

> [!div class="nextstepaction"]
> [Schnellstart: Python-Datenstrukturen in SQL Server](quickstart-python-data-structures.md)