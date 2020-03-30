---
title: 'Python und T-SQL: Durchsuchen von Daten'
description: Tutorial zum Einbetten von Python in gespeicherte Prozeduren von SQL Server und T-SQL-Funktionen
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2aef2ed82803af2a6ca1966cde5f5bf6675ca016
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "74901848"
---
# <a name="explore-and-visualize-the-data"></a>Untersuchen und Visualisieren der Daten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel ist Teil des Tutorials [Python-Datenanalysen für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md). 

In diesem Schritt untersuchen Sie die Beispieldaten und generieren einige Plots. Im späteren Verlauf erfahren Sie, wie Sie Grafikobjekte in Python serialisieren, anschließend deserialisieren und Plots erstellen.

## <a name="review-the-data"></a>Überprüfen der Daten

Nehmen Sie sich zunächst eine Minute, um das Datenschema zu durchsuchen, da einige Änderungen daran vorgenommen wurden, um die Verwendung der NYC Taxi-Daten zu vereinfachen.

+ Im ursprünglichen Dataset wurden separate Dateien für die Taxi-IDs und die Fahrtendatensätze verwendet. Die zwei ursprünglichen Datasets in den Spalten _medallion_, _hack_license_ und _pickup_datetime_ wurden zusammengeführt.  
+ Das ursprüngliche Dataset umfasste viele Dateien und war ziemlich groß. Das Dataset wurde reduziert, sodass nun nur noch 1 % der ursprünglichen Anzahl von Datensätzen vorliegt. Die aktuelle Datentabelle enthält 1.703.957 Zeilen und 23 Spalten.

**Taxi-IDs**

Die Spalte _medallion_ stellt die eindeutige ID-Nummer des Taxis dar.

Die Spalte _hack_license_ enthält das (anonymisierte) Kennzeichen des Taxifahrers.

**Datensätze von Fahrten und Fahrpreisen**

Jeder Datensatz für Fahrten enthält den genauen Abhol- und Zielort und die Zeit sowie die Fahrstrecke.

Jeder Fahrpreisdatensatz enthält die Zahlungsinformationen wie die Zahlungsart, der Gesamtbetrag und den Fahrtpreis.

Die letzten drei Spalten können für verschiedene Machine Learning-Tasks verwendet werden.  Die Spalte _tip_amount_ enthält fortlaufende numerische Werte und kann als die **label** -Spalte für die Regressionsanalyse verwendet werden. Die Spalte _tipped_ verfügt nur über Ja/Nein-Werte und wird für die binäre Klassifikation verwendet. Die _tip_class_ -Spalte weist mehrere **Klassenbezeichnungen** auf und kann deshalb als Bezeichnung für mehrklassige Klassifizierungsaufgaben verwendet werden.

Die Werte für die Bezeichnungsspalten basieren alle auf der `tip_amount`-Spalte und verwenden folgende Geschäftsregeln:

+ Die Bezeichnungsspalte `tipped` kann die Werte „0“ (null) und „1“ enthalten.

    Wenn `tip_amount` > 0, `tipped` = 1; andernfalls `tipped` = 0

+ Die Bezeichnungsspalte `tip_class` kann Class-Werte von „0“ (null) bis „4“ enthalten.

    Class 0: `tip_amount` = 0 $

    Class 1: `tip_amount` > 0 $ und `tip_amount` <= 5 $
    
    Class 2: `tip_amount` > 5 $ und `tip_amount` <= 10 $
    
    Class 3: `tip_amount` > 10 $ und `tip_amount` <= 20 $
    
    Class 4: `tip_amount` > 20 $

## <a name="create-plots-using-python-in-t-sql"></a>Erstellen von Plots mit Python in T-SQL

Das Entwickeln einer Data Science-Lösung bringt normalerweise die intensive Untersuchung und Visualisierung von Daten mit sich. Da die Visualisierung ein leistungsfähiges Tool für das Verständnis der Verteilung von Daten und Ausreißern ist, stellt Python viele Pakete für die Visualisierung von Daten bereit. Das **matplotlib**-Modul ist eine der beliebteren Bibliotheken für die Visualisierung und umfasst viele Funktionen zum Erstellen von Histogrammen, Punktdiagrammen, Boxplots und anderen Graphen für die Datenuntersuchung.

In diesem Abschnitt erfahren Sie, wie Sie mithilfe von gespeicherten Prozeduren mit Plots arbeiten. Anstatt das Bild auf dem Server zu öffnen, speichern Sie das Python-Objekt `plot` als Daten vom Typ **varbinary** und schreiben diese dann in eine Datei, die anderswo freigegeben oder angezeigt werden kann.

### <a name="create-a-plot-as-varbinary-data"></a>Erstellen eines Plots als varbinary-Daten

Die gespeicherte Prozedur gibt ein serialisiertes `figure`-Pythonobjekt als **varbinary**-Datenstrom zurück. Sie können binäre Daten nicht direkt anzeigen, aber Sie können Python-Code auf dem Client verwenden, um die Abbildungen zu deserialisieren und anzuzeigen und um die Bilddatei anschließend auf einem Clientcomputer zu speichern.

1. Erstellen Sie die gespeicherte Prozedur **PyPlotMatplotlib**, wenn das PowerShell-Skript dies noch nicht getan hat.

    - Die Variable `@query` definiert den Abfragetext `SELECT tipped FROM nyctaxi_sample`, der als Argument für die Skripteingabevariable `@input_data_1` an den Python-Codeblock übergeben wird.
    - Das Python-Skript ist relativ einfach: `figure`-Objekte von **matplotlib** werden verwendet, um das Histogramm und das Punktdiagramm zu erstellen. Anschließend werden diese Objekte mithilfe der `pickle`-Bibliothek serialisiert.
    - Das Python-Grafikobjekt wird für die Ausgabe in einen **pandas**-Datenrahmen serialisiert.
  
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

2. Führen Sie die gespeicherte Prozedur jetzt ohne Argumente aus, um ein Plot aus den Daten zu generieren, die als Eingabeabfrage hartcodiert sind.

    ```sql
    EXEC [dbo].[PyPlotMatplotlib]
    ```

3. Die Ergebnisse sollten etwa wie folgt aussehen:
  
    ```sql
    plot
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    ```

  
4. Sie können nun über einen [Python-Client](../python/setup-python-client-tools-sql.md) einer Verbindung mit der SQL Server-Instanz herstellen, die die binären Plotobjekte generiert hat, und die Plots anzeigen. 

    Führen Sie hierzu den folgenden Python-Code aus. Fügen Sie dabei die entsprechenden Servernamen, Datenbanknamen und Anmeldeinformationen ein. Stellen Sie sicher, dass die Python-Versionen auf dem Client und dem Server identisch sind. Stellen Sie außerdem sicher, dass die Python-Bibliotheken auf Ihrem Client (z. B. matplotlib) eine identische oder höhere Version als die auf dem Server installierten Bibliotheken aufweisen.
  
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

5.  Wenn die Verbindung erfolgreich hergestellt wird, sollte eine Nachricht ähnlich der folgenden angezeigt werden:
  
    *Die Plots werden im folgenden Verzeichnis gespeichert: xxxx*
  
6.  Die Ausgabedatei wird im Python-Arbeitsverzeichnis erstellt. Suchen Sie das Python-Arbeitsverzeichnis, und öffnen Sie die Datei, um den Plot anzuzeigen. In der folgenden Abbildung sehen Sie einen Plot, der auf dem Clientcomputer gespeichert wurde.
  
    ![Vergleich zwischen Trinkgeldern und Fahrpreisen](media/sqldev-python-sample-plot.png "Vergleich zwischen Trinkgeldern und Fahrpreisen") 

## <a name="next-step"></a>Nächster Schritt

[Erstellen von Datenfunktionen mit T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>Vorheriger Schritt

[Herunterladen des NYC Taxi-Datasets](demo-data-nyctaxi-in-sql.md)

