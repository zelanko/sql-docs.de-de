---
title: Einfache R-Skripts erstellen und ausführen
titleSuffix: SQL Server Machine Learning Services
description: Erstellen und führen Sie einfache R-Skripts in einer SQL Server Instanz mit SQL Server Machine Learning Services aus.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/17/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d723fa9b90659eb31e96626a3a85c1299c17fa2f
ms.sourcegitcommit: 1661c3e1bb38ed12f8485c3860fc2d2b97dd2c9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71150313"
---
# <a name="quickstart-create-and-run-simple-r-scripts-with-sql-server-machine-learning-services"></a>Schnellstart: Erstellen und Ausführen einfacher R-Skripts mit SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In dieser Schnellstartanleitung erstellen Sie mithilfe [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md)eine Reihe einfacher R-Skripts und führen diese aus. Sie erfahren, wie Sie ein wohl geformtes R-Skript in die gespeicherte Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) einschließen und das Skript in einer SQL Server-Instanz ausführen.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Diese Schnellstartanleitung erfordert Zugriff auf eine Instanz von SQL Server mit [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) , auf der die R-Sprache installiert ist.

  Ihre SQL Server Instanz kann sich auf einem virtuellen Azure-Computer oder lokal befinden. Beachten Sie, dass das Feature für die externe Skripterstellung standardmäßig deaktiviert ist. Daher müssen Sie möglicherweise [externe Skripterstellung aktivieren](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) und überprüfen, ob **SQL Server-Launchpad-Dienst** ausgeführt wird, bevor Sie beginnen.

- Außerdem benötigen Sie ein Tool zum Ausführen von SQL-Abfragen, die R-Skripts enthalten. Sie können diese Skripts mit einem beliebigen Daten Bank Verwaltungs-oder Abfrage Tool ausführen, solange eine Verbindung mit einer SQL Server Instanz hergestellt und eine T-SQL-Abfrage oder eine gespeicherte Prozedur ausgeführt werden kann. In diesem Schnellstart wird [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)verwendet.

## <a name="run-a-simple-script"></a>Ausführen eines einfachen Skripts

Wenn Sie ein R-Skript ausführen möchten, übergeben Sie es als Argument an die gespeicherte System Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
Diese gespeicherte System Prozedur startet die r-Laufzeit im Kontext SQL Server, übergibt Daten an R, verwaltet r-Benutzersitzungen sicher und gibt alle Ergebnisse an den Client zurück.

In den folgenden Schritten führen Sie dieses R-Beispielskript in Ihrer SQL Server Instanz aus:

```r
a <- 1
b <- 2
c <- a/b
d <- a*b
print(c(c, d))
```

1. Öffnen Sie **SQL Server Management Studio** , und stellen Sie eine Verbindung mit Ihrer SQL Server Instanz her

1. Übergeben Sie das gesamte R-Skript `sp_execute_external_script` an die gespeicherte Prozedur.

   Das Skript wird durch das `@script` -Argument übermittelt. Alles innerhalb des `@script` Arguments muss gültiger R-Code sein.

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'
    a <- 1
    b <- 2
    c <- a/b
    d <- a*b
    print(c(c, d))
    '
    ```

1. Das korrekte Ergebnis wird berechnet, und die `print` R-Funktion gibt das Ergebnis an das Fenster **Meldungen** zurück.

   Dies sollte in etwa wie folgt aussehen.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script:
    0.5 2
    ```

## <a name="run-a-hello-world-script"></a>Ausführen eines Hallo Welt Skripts

Ein typisches Beispielskript ist ein Beispiel, das nur die Zeichenfolge "Hallo Welt" ausgibt. Führen Sie den folgenden Befehl aus.

```sql
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'OutputDataSet<-InputDataSet'
    , @input_data_1 = N'SELECT 1 AS hello'
WITH RESULT SETS(([Hello World] INT));
GO
```

Zu den Eingaben `sp_execute_external_script` für die gespeicherte Prozedur gehören:

| | |
|-|-|
| @language | definiert die aufzurufende Spracherweiterung, in diesem Fall R |
| @script | definiert die Befehle, die an die R-Laufzeit übermittelt werden. Ihr gesamtes R-Skript muss von diesem Argument als Unicode-Text umschlossen sein. Sie können den Text auch einer Variablen des Typs **nvarchar** hinzufügen und dann die Variable |
| @input_data_1 | von der Abfrage zurückgegebene Daten, die an die R-Laufzeit zurückgegeben werden, die die Daten zurückgibt, die als Datenrahmen SQL Server werden. |
|MIT RESULTSETS | Klausel definiert das Schema der zurückgegebenen Datentabelle für SQL Server, wobei "Hallo Welt" als Spaltenname " **int** " für den Datentyp hinzugefügt wird. |

Der Befehl gibt den folgenden Text aus:

| Hallo Welt |
|-------------|
| 1 |

## <a name="use-inputs-and-outputs"></a>Verwenden von Eingaben und Ausgaben

Standardmäßig `sp_execute_external_script` akzeptiert ein einzelnes Dataset als Eingabe, das in der Regel in Form einer gültigen SQL-Abfrage angegeben wird. Anschließend wird ein einzelner R-Datenrahmen als Ausgabe zurückgegeben.

Verwenden Sie vorerst die standardmäßigen Eingabe-und Ausgabevariablen von `sp_execute_external_script`: **Input DataSet** und **outputdataset**.

1. Erstellen Sie eine kleine Tabelle mit Testdaten.

    ```sql
    CREATE TABLE RTestData (col1 INT NOT NULL)
    
    INSERT INTO RTestData
    VALUES (1);
    
    INSERT INTO RTestData
    VALUES (10);
    
    INSERT INTO RTestData
    VALUES (100);
    GO
    ```

1. Verwenden Sie `SELECT` die-Anweisung, um die Tabelle abzufragen.
  
    ```sql
    SELECT *
    FROM RTestData
    ```

    **Ergebnisse**

    ![Inhalt der rtestdata-Tabelle](./media/select-rtestdata.png)

1. Führen Sie das folgende R-Skript aus. Die Daten werden mithilfe der `SELECT` -Anweisung aus der-Tabelle abgerufen, an die R-Laufzeit weitergeleitet, und die Daten werden als Datenrahmen zurückgegeben. Die `WITH RESULT SETS` -Klausel definiert das Schema der zurückgegebenen Datentabelle für SQL, wobei der Spaltenname *newcolname*hinzugefügt wird.

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'OutputDataSet <- InputDataSet;'
        , @input_data_1 = N'SELECT * FROM RTestData;'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    **Ergebnisse**

    ![Ausgabe des R-Skripts, das Daten aus einer Tabelle zurückgibt](./media/r-output-rtestdata.png)

1. Nun ändern wir die Namen der Eingabe-und Ausgabevariablen. Die Standardnamen für die Eingabe-und Ausgabevariablen sind input **DataSet** und **outputdataset**. mit diesem Skript werden die Namen in **SQL_in** und **SQL_out**geändert:

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N' SQL_out <- SQL_in;'
        , @input_data_1 = N' SELECT 12 as Col;'
        , @input_data_1_name = N'SQL_in'
        , @output_data_1_name = N'SQL_out'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    Beachten Sie, dass R groß-und Kleinschreibung beachtet. Die im R-Skript (**SQL_out**, **SQL_in**) verwendeten Eingabe-und Ausgabevariablen müssen mit den Namen, die `@input_data_1_name` mit `@output_data_1_name`und definiert sind, einschließlich Case

   > [!TIP]
   > Nur eine Eingabedataset kann als Parameter übergeben werden, und Sie können nur ein Dataset zurückgeben. Allerdings können Sie andere Datasets innerhalb Ihres R-Codes aufrufen und Ausgaben und andere Typen zusätzlich zum Dataset zurückgeben. Sie können auch das Schlüsselwort OUTPUT zu einem beliebigen Parameter hinzufügen, damit es mit den Ergebnissen zurückgegeben wird.

1. Sie können Werte auch nur mit dem R-Skript ohne Eingabedaten generieren (`@input_data_1` ist auf "blank" festgelegt).

   Das folgende Skript gibt den Text "Hello" und "World" aus.

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'
    mytextvariable <- c("hello", " ", "world");
    OutputDataSet <- as.data.frame(mytextvariable);
    '
        , @input_data_1 = N''
    WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
    ```

    **Ergebnisse**

    ![Abfragen von Ergebnissen @script mithilfe von als Eingabe](./media/r-data-generated-output.png)

## <a name="check-r-version"></a>R-Version überprüfen

Wenn Sie sehen möchten, welche Version von R in Ihrer SQL Server Instanz installiert ist, führen Sie das folgende Skript aus.

```sql
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(version)';
GO
```

Die R `print` -Funktion gibt die Version an das Fenster **Meldungen** zurück. In der folgenden Beispielausgabe sehen Sie, dass R Version 3.4.4 in diesem Fall installiert ist.

**Ergebnisse**

```text
STDOUT message(s) from external script:
                   _
platform       x86_64-w64-mingw32
arch           x86_64
os             mingw32
system         x86_64, mingw32
status
major          3
minor          4.4
year           2018
month          03
day            15
svn rev        74408
language       R
version.string R version 3.4.4 (2018-03-15)
nickname       Someone to Lean On
```

## <a name="list-r-packages"></a>Auflisten von R-Paketen

Microsoft stellt eine Reihe von R-Paketen bereit, die mit SQL Server Machine Learning Services vorinstalliert sind.

Führen Sie das folgende Skript aus, um eine Liste der installierten R-Pakete anzuzeigen, einschließlich Version, Abhängigkeiten, Lizenz und Bibliotheks Pfadinformationen.

```SQL
EXEC sp_execute_external_script @language = N'R'
    , @script = N'
OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
WITH result sets((
            Package NVARCHAR(255)
            , Version NVARCHAR(100)
            , Depends NVARCHAR(4000)
            , License NVARCHAR(1000)
            , LibPath NVARCHAR(2000)
            ));
```

Die Ausgabe erfolgt `installed.packages()` in R und wird als Resultset zurückgegeben.

**Ergebnisse**

![Installierte Pakete in R](./media/rsql-installed-packages.png) 

## <a name="next-steps"></a>Nächste Schritte

Um ein Machine Learning-Modell mithilfe von R in SQL Server zu erstellen, befolgen Sie diese Schnellstartanleitung:

> [!div class="nextstepaction"]
> [Erstellen und bewerten eines Vorhersagemodells in R mit SQL Server Machine Learning Services](quickstart-r-train-score-model.md)

Weitere Informationen zu SQL Server Machine Learning Services finden Sie in den folgenden Artikeln.

- [Verarbeiten von Datentypen und Objekten mithilfe von R in SQL Server Machine Learning Services](quickstart-r-data-types-and-objects.md)
- [Schreiben von erweiterten R-Funktionen mit SQL Server Machine Learning Services](quickstart-r-functions.md)
- [Was ist SQL Server Machine Learning Services (python und R)?](../what-is-sql-server-machine-learning.md)
