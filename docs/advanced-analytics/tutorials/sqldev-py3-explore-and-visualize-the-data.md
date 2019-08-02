---
title: 'Lektion 1: untersuchen und Visualisieren von Daten mithilfe von Python und T-SQL'
description: Tutorial zum Einbetten von python in SQL Server gespeicherte Prozeduren und T-SQL-Funktionen
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6ee82de1431a6bc21596505dc4b008b817b35830
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714704"
---
# <a name="explore-and-visualize-the-data"></a>Untersuchen und Visualisieren der Daten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel ist Teil eines Tutorials, [in-Database-python-Analyse für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md). 

In diesem Schritt untersuchen Sie die Beispiel Daten und generieren einige Plots. Später erfahren Sie, wie Sie Grafik Objekte in python serialisieren und anschließend diese Objekte deserialisieren und Plots erstellen.

## <a name="review-the-data"></a>Überprüfen der Daten

Nehmen Sie sich zunächst eine Minute Zeit, um das Datenschema zu durchsuchen, da wir einige Änderungen vorgenommen haben, um die Verwendung der NYC Taxi-Daten zu vereinfachen.

+ Das ursprüngliche DataSet verwendete separate Dateien für die Taxi-IDs und die Fahrt Datensätze. Wir haben die beiden ursprünglichen Datasets in den Spalten " _Medallion_", " _hack_license_" und " _pickup_datetime_" verknüpft.  
+ Das ursprüngliche DataSet umfasste viele Dateien und war sehr umfangreich. Wir haben ein Downsampling durchgeführt, um nur 1% der ursprünglichen Anzahl von Datensätzen zu erhalten. Die aktuelle Datentabelle enthält 1.703.957 Zeilen und 23 Spalten.

**Taxi-IDs**

Die Spalte " _Medallion_ " stellt die eindeutige ID-Nummer des Taxis dar.

Die _hack_license_ -Spalte enthält die Lizenznummer des Taxi Treibers (anonymisiert).

**Datensätze von Fahrten und Fahrpreisen**

Jeder Datensatz für Fahrten enthält den genauen Abhol- und Zielort und die Zeit sowie die Fahrstrecke.

Jeder Fahrpreisdatensatz enthält die Zahlungsinformationen wie die Zahlungsart, der Gesamtbetrag und den Fahrtpreis.

Die letzten drei Spalten können für verschiedene Machine Learning-Tasks verwendet werden.  Die Spalte _tip_amount_ enthält fortlaufende numerische Werte und kann als die **label** -Spalte für die Regressionsanalyse verwendet werden. Die Spalte _tipped_ verfügt nur über Ja/Nein-Werte und wird für die binäre Klassifikation verwendet. Die _tip_class_ -Spalte weist mehrere **Klassenbezeichnungen** auf und kann deshalb als Bezeichnung für mehrklassige Klassifizierungsaufgaben verwendet werden.

Die Werte, die für die Bezeichnungs Spalten verwendet werden, `tip_amount` basieren alle auf der Spalte, die diese Geschäftsregeln verwendet:

+ Die Bezeichnungs Spalte `tipped` hat die möglichen Werte 0 und 1.

    , `tip_amount` Wenn > 0 `tipped` , = 1, `tipped` andernfalls = 0

+ Die Bezeichnungs Spalte `tip_class` hat mögliche Klassen Werte 0-4

    Class 0: `tip_amount` = $0

    Klasse 1: `tip_amount` > $0 und `tip_amount` < = $5
    
    Klasse 2: `tip_amount` > $5 und `tip_amount` < = $10
    
    Klasse 3: `tip_amount` > $10 und `tip_amount` < = $20
    
    Klasse 4: `tip_amount` > $20

## <a name="create-plots-using-python-in-t-sql"></a>Erstellen von Plots mithilfe von python in T-SQL

Das Entwickeln einer Data Science-Lösung bringt normalerweise die intensive Untersuchung und Visualisierung von Daten mit sich. Da die Visualisierung ein leistungsfähiges Tool zum Verständnis der Verteilung der Daten und Ausreißer darstellt, bietet python viele Pakete zum Visualisieren von Daten. Das **matplotlib** -Modul ist eine der beliebtesten Bibliotheken für die Visualisierung und umfasst viele Funktionen zum Erstellen von Histogrammen, Punkt Diagrammen, Boxplots und anderen Diagrammen zum Durchsuchen von Daten.

In diesem Abschnitt erfahren Sie, wie Sie mit Diagrammen mithilfe gespeicherter Prozeduren arbeiten. Anstatt das Image auf dem Server zu öffnen, speichern Sie das Python- `plot` Objekt als **varbinary** -Daten, und schreiben Sie dieses in eine Datei, die an anderer Stelle freigegeben oder angezeigt werden kann.

### <a name="create-a-plot-as-varbinary-data"></a>Erstellen eines plotdiagramms als varbinary-Daten

Die gespeicherte Prozedur gibt ein serialisiertes python `figure` -Objekt als Datenstrom von **varbinary** -Daten zurück. Die Binärdaten können nicht direkt angezeigt werden. Sie können jedoch den Python-Code auf dem Client verwenden, um die Abbildungen zu deserialisieren und anzuzeigen, und dann die Bilddatei auf einem Client Computer speichern.

1. Erstellen Sie die gespeicherte Prozedur **pyplotmatplotlib**, wenn das PowerShell-Skript dies nicht bereits getan hat.

    - Die- `@query` Variable definiert den Abfrage `SELECT tipped FROM nyctaxi_sample`Text, der an den python-Codeblock als Argument für die Skript Eingabe Variable,, `@input_data_1`übermittelt wird.
    - Das Python-Skript ist recht einfach: **matplotlib** `figure` -Objekte werden verwendet, um das Histogramm und das Punkt Diagramm zu erstellen, und diese Objekte werden `pickle` dann mithilfe der-Bibliothek serialisiert.
    - Das python-Grafik Objekt wird zur Ausgabe in einen **Pandas** -dataframe serialisiert.
  
    ```sql
    DROP PROCEDURE IF EXISTS PyPlotMatplotlib;
    GO

    CREATE PROCEDURE [dbo].[PyPlotMatplotlib]
    AS
    BEGIN
        SET NOCOUNT ON;
        DECLARE @query nvarchar(max) =
        N'SELECT cast(tipped as int) as tipped, tip_amount, fare_amount FROM [dbo].[nyctaxi_sample]'
        EXECUTE sp_execute_external_script
        @language = N'Python',
        @script = N'
    import matplotlib
    matplotlib.use("Agg")
    import matplotlib.pyplot as plt
    import pandas as pd
    import pickle

    fig_handle = plt.figure()
    plt.hist(InputDataSet.tipped)
    plt.xlabel("Tipped")
    plt.ylabel("Counts")
    plt.title("Histogram, Tipped")
    plot0 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.hist(InputDataSet.tip_amount)
    plt.xlabel("Tip amount ($)")
    plt.ylabel("Counts")
    plt.title("Histogram, Tip amount")
    plot1 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.hist(InputDataSet.fare_amount)
    plt.xlabel("Fare amount ($)")
    plt.ylabel("Counts")
    plt.title("Histogram, Fare amount")
    plot2 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.scatter( InputDataSet.fare_amount, InputDataSet.tip_amount)
    plt.xlabel("Fare Amount ($)")
    plt.ylabel("Tip Amount ($)")
    plt.title("Tip amount by Fare amount")
    plot3 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    OutputDataSet = plot0.append(plot1, ignore_index=True).append(plot2, ignore_index=True).append(plot3, ignore_index=True)
    ',
    @input_data_1 = @query
    WITH RESULT SETS ((plot varbinary(max)))
    END
    GO
    ```

2. Führen Sie die gespeicherte Prozedur nun ohne Argumente aus, um einen Plot aus den Daten zu generieren, die als Eingabe Abfrage hart codiert sind.

    ```sql
    EXEC [dbo].[PyPlotMatplotlib]
    ```

3. Die Ergebnisse sollten in etwa wie folgt aussehen:
  
    ```sql
    plot
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    ```

  
4. Von einem [Python-Client](../python/setup-python-client-tools-sql.md)aus können Sie jetzt eine Verbindung mit der SQL Server-Instanz herstellen, die die binären plotobjekte generiert hat, und die Plots anzeigen. 

    Führen Sie hierzu den folgenden Python-Code aus, wobei Sie den Servernamen, den Datenbanknamen und die Anmelde Informationen nach Bedarf ersetzen. Stellen Sie sicher, dass die Python-Version auf dem Client und dem Server identisch ist. Stellen Sie außerdem sicher, dass die python-Bibliotheken auf Ihrem Client (z. b. matplotlib) mit der gleichen oder einer höheren Version identisch sind, die auf dem Server installiert ist.
  
    **Verwenden der SQL Server-Authentifizierung:**
    
    ```python
    %matplotlib notebook
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER=SQL Server;SERVER={SERVER_NAME};DATABASE={DB_NAME};UID={USER_NAME};PWD={PASSWORD}')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[PyPlotMatplotlib]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

    **Verwenden der Windows-Authentifizierung:**

    ```python
    %matplotlib notebook
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER=SQL Server;SERVER={SERVER_NAME};DATABASE={DB_NAME};Trusted_Connection=True;')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[PyPlotMatplotlib]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

5.  Wenn die Verbindung erfolgreich hergestellt wurde, sollte eine Meldung wie die folgende angezeigt werden:
  
    *Die Plots werden im folgenden Verzeichnis gespeichert: xxxx*
  
6.  Die Ausgabedatei wird im python-Arbeitsverzeichnis erstellt. Um das Diagramm anzuzeigen, suchen Sie das python-Arbeitsverzeichnis, und öffnen Sie die Datei. Die folgende Abbildung zeigt eine auf dem Client Computer gespeicherte Grafik.
  
    ![Trinkgeldbetrag im Vergleich zum Fahr Preis](media/sqldev-python-sample-plot.png "Trinkgeldbetrag im Vergleich zum Fahr Preis") 

## <a name="next-step"></a>Nächster Schritt

[Erstellen von Datenfunktionen mit T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>Vorheriger Schritt

[Herunterladen des NYC Taxi-Datasets](demo-data-nyctaxi-in-sql.md)

