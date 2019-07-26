---
title: Schnellstart zum Arbeiten mit Eingaben und Ausgaben in R
description: In dieser Schnellstartanleitung für R-Skript in SQL Server erfahren Sie, wie Sie Eingaben und Ausgaben in der gespeicherten System Prozedur sp_execute_external_script strukturieren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 4e9e7efe6143d35e627abef4272281aad4b5b184
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469156"
---
# <a name="quickstart-handle-inputs-and-outputs-using-r-in-sql-server"></a>Schnellstart: Behandeln von Eingaben und Ausgaben mithilfe von R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In dieser Schnellstartanleitung erfahren Sie, wie Sie Eingaben und Ausgaben bei Verwendung von r in SQL Server Machine Learning Services oder r Services verarbeiten.

Wenn Sie r-Code in SQL Server ausführen möchten, müssen Sie das r-Skript in einer gespeicherten Prozedur einschließen. Sie können ein Skript schreiben oder das R-Skript an [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)übergeben. Diese gespeicherte System Prozedur wird verwendet, um die r-Laufzeit im Kontext von SQL Server zu starten, der Daten an R übergibt, r-Benutzersitzungen sicher verwaltet und alle Ergebnisse an den Client zurückgibt.

Standardmäßig akzeptiert [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) ein einzelnes Eingabe DataSet, das in der Regel in Form einer gültigen SQL-Abfrage angegeben wird. Andere Eingabetypen können als SQL-Variablen übermittelt werden.

Die gespeicherte Prozedur gibt einen einzelnen R-Datenrahmen als Ausgabe zurück, aber Sie können auch skalare und Modelle als Variablen ausgeben. Beispielsweise können Sie ein trainiertes Modell als binäre Variable ausgeben und an eine T-SQL-INSERT-Anweisung übergeben, um das Modell in eine Tabelle zu schreiben. Sie können auch Diagramme (im Binärformat) oder skalare generieren (einzelne Werte, z. b. das Datum und die Uhrzeit, die verstrichene Zeit zum Trainieren des Modells usw.).

## <a name="prerequisites"></a>Vorraussetzungen

Eine vorherige Schnellstartanleitung, [überprüfen, ob R in SQL Server vorhanden](quickstart-r-verify.md)ist, enthält Informationen und Links zum Einrichten der r-Umgebung, die für diesen Schnellstart erforderlich ist.

## <a name="create-the-source-data"></a>Erstellen der Quelldaten

Erstellen Sie eine kleine Tabelle mit Testdaten, indem Sie die folgende T-SQL-Anweisung ausführen:

```sql
CREATE TABLE RTestData (col1 INT NOT NULL)
INSERT INTO RTestData VALUES (1);
INSERT INTO RTestData VALUES (10);
INSERT INTO RTestData VALUES (100);
GO
```

Wenn die Tabelle erstellt wurde, verwenden Sie die folgende Anweisung zum Abfragen der Tabelle:
  
```sql
SELECT * FROM RTestData
```

**Ergebnisse**

![Inhalt der rtestdata-Tabelle](./media/select-rtestdata.png)

## <a name="inputs-and-outputs"></a>Eingaben und Ausgaben

Betrachten wir nun die standardmäßigen Eingabe-und Ausgabevariablen von sp_execute_external_script `InputDataSet` : `OutputDataSet`und.

1. Sie können die Daten aus der Tabelle als Eingabe für das R-Skript erhalten. Führen Sie die folgende Anweisung aus. Er ruft die Daten aus der Tabelle ab, führt einen Roundtrip durch die R-Laufzeit durch und gibt die Werte mit dem Spaltennamen *newcolname*zurück.

    Die von der Abfrage zurückgegebenen Daten werden an die R-Laufzeit übermittelt, die die Daten als Datenrahmen an SQL-Datenbank zurückgibt. Die with Result Sets-Klausel definiert das Schema der zurückgegebenen Datentabelle für die SQL-Datenbank.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'R'
        , @script = N'OutputDataSet <- InputDataSet;'
        , @input_data_1 = N'SELECT * FROM RTestData;'
    WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    **Ergebnisse**

    ![Ausgabe des R-Skripts, das Daten aus einer Tabelle zurückgibt](./media/r-output-rtestdata.png)

2. Ändern Sie den Namen der Eingabe-oder Ausgabevariablen. Das obige Skript verwendet die Standardnamen für die Eingabe-und Ausgabevariablen, input _DataSet_ und _outputdataset_. Zum Definieren der Eingabedaten, die _inputdatset_zugeordnet sind, verwenden *@input_data_1* Sie die-Variable.

    In diesem Skript wurden die Namen der Ausgabe-und Eingabevariablen für die gespeicherte Prozedur in *SQL_out* und *SQL_in*geändert:

    ```sql
    EXECUTE sp_execute_external_script
      @language = N'R'
      , @script = N' SQL_out <- SQL_in;'
      , @input_data_1 = N'SELECT 12 as Col;'
      , @input_data_1_name  = N'SQL_in'
      , @output_data_1_name =  N'SQL_out'
      WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    Beachten Sie, dass bei R die Groß-/Kleinschreibung beachtet wird, sodass der Fall `@input_data_1_name` der `@output_data_1_name` Eingabe-und Ausgabevariablen in und mit denen im `@script`r-Code in identisch sein muss. 

    Nur eine Eingabedataset kann als Parameter übergeben werden, und Sie können nur ein Dataset zurückgeben. Allerdings können Sie andere Datasets innerhalb Ihres R-Codes aufrufen und Ausgaben und andere Typen zusätzlich zum Dataset zurückgeben. Sie können auch das Schlüsselwort OUTPUT zu einem beliebigen Parameter hinzufügen, damit es mit den Ergebnissen zurückgegeben wird. 

    Die `WITH RESULT SETS` -Anweisung definiert das Schema für die Daten, die in SQL Server verwendet werden. Sie müssen SQL-kompatible Datentypen für jede Spalte bereitstellen, die Sie von R zurückgeben. Sie können die Schema Definition auch zum Bereitstellen neuer Spaltennamen verwenden, da Sie die Spaltennamen aus dem R-Datenrahmen nicht verwenden müssen.

3. Sie können auch Werte mit dem R-Skript generieren und die Zeichenfolge _@input_data_1_ der Eingabe Abfrage leer lassen.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'R'
        , @script = N' mytextvariable <- c("hello", " ", "world");
            OutputDataSet <- as.data.frame(mytextvariable);'
        , @input_data_1 = N''
    WITH RESULT SETS (([Col1] CHAR(20) NOT NULL));
    ```

    **Ergebnisse**

    ![Abfragen von Ergebnissen @script mithilfe von als Eingabe](./media/r-data-generated-output.png)

## <a name="next-steps"></a>Nächste Schritte

Untersuchen Sie einige der Probleme, die auftreten können, wenn Sie Daten zwischen r und SQL Server übergeben, z. b. implizite Konvertierungen und Unterschiede in Tabellendaten zwischen r und SQL.

> [!div class="nextstepaction"]
> [Schnellstart: Verarbeiten von Datentypen und Objekten](quickstart-r-data-types-and-objects.md)