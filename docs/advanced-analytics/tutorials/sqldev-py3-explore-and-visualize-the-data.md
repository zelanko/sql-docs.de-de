---
title: Lektion 1 durchsuchen und Visualisieren von Daten mithilfe von Python und T-SQL – SQL Server-Machine Learning
description: Tutorial zum Einbetten von gespeicherten Python in SQL Server Prozeduren und T-SQL-Funktionen
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e9dd0a0884c96a8f5b17948c21b7f891a2e997ab
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860491"
---
# <a name="explore-and-visualize-the-data"></a>Untersuchen und Visualisieren von Daten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil eines Tutorials, [In-Database Python Analytics für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md). 

In diesem Schritt Untersuchen der Beispieldaten und generieren einige Diagramme. Später erfahren Sie, wie Grafikobjekten in Python zu serialisieren und Deserialisieren von diesen Objekten und Plots stellen.

## <a name="review-the-data"></a>Überprüfen Sie die Daten

Nehmen Sie sich zunächst eine Minute Zeit, die das Datenschema zu durchsuchen, wie wir vereinfachen die NYC Taxi-Daten verwenden, einige Änderungen vorgenommen haben

+ Das ursprüngliche Dataset werden separate Dateien für die Taxi-IDs und die fahrtendatensätze verwendet. Wir haben die beiden ursprünglichen Datasets verknüpft, für die Spalten _"medallion"_, _"hack_license"_, und _Pickup_datetime_.  
+ Das ursprüngliche Dataset umfasst viele Dateien und war sehr groß. Wir haben Downsampled, um nur 1 % der ursprünglichen Anzahl von Datensätzen zu erhalten. Die aktuellen Datentabelle hat 1.703.957 Zeilen und 23 Spalten.

**Taxi-IDs**

Die _"medallion"_ Spalte stellt die eindeutige ID-Nummer des Taxis dar.

Die _"hack_license"_ Spalte enthält die Taxi Führerscheinnummer (anonymisierte).

**Datensätze von Fahrten und Fahrpreisen**

Jeder Datensatz für Fahrten enthält den genauen Abhol- und Zielort und die Zeit sowie die Fahrstrecke.

Jeder Fahrpreisdatensatz enthält die Zahlungsinformationen wie die Zahlungsart, der Gesamtbetrag und den Fahrtpreis.

Die letzten drei Spalten können für verschiedene Machine Learning-Tasks verwendet werden.  Die Spalte _tip_amount_ enthält fortlaufende numerische Werte und kann als die **label** -Spalte für die Regressionsanalyse verwendet werden. Die Spalte _tipped_ verfügt nur über Ja/Nein-Werte und wird für die binäre Klassifikation verwendet. Die _tip_class_ -Spalte weist mehrere **Klassenbezeichnungen** auf und kann deshalb als Bezeichnung für mehrklassige Klassifizierungsaufgaben verwendet werden.

Die Werte für die Bezeichnungsspalten basieren alle auf die `tip_amount` Spalte verwenden folgende Geschäftsregeln:

+ Spalte "Label" `tipped` verfügt über mögliche Werte 0 und 1

    Wenn `tip_amount` > 0, `tipped` = 1; andernfalls `tipped` = 0

+ Spalte "Label" `tip_class` verfügt über mögliche Klassenwerte 0 und 4

    Klasse 0: `tip_amount` = $0

    Klasse 1: `tip_amount` > $0 und `tip_amount` < = $5
    
    2-Klasse: `tip_amount` > $5 und `tip_amount` < = $10
    
    3-Klasse: `tip_amount` > 10 US -Dollar und `tip_amount` < = $20
    
    4-Klasse: `tip_amount` > $20

## <a name="create-plots-using-python-in-t-sql"></a>Erstellen von Diagrammen, die mithilfe von Python in T-SQL

Das Entwickeln einer Data Science-Lösung bringt normalerweise die intensive Untersuchung und Visualisierung von Daten mit sich. Da die Visualisierung ein leistungsfähiges Tool für das Verständnis der Verteilung von Daten- und Ausreißern ist, stellt Python viele Pakete für die Visualisierung von Daten bereit. Die **Matplotlib** Modul ist eine Weitere beliebte Bibliotheken für die datenvisualisierung und beinhaltet zahlreiche Funktionen zum Erstellen von Histogrammen, Punktdiagrammen, boxplots und andere Daten Diagramme.

In diesem Abschnitt erfahren Sie, wie mit Diagrammen, die mithilfe von gespeicherten Prozeduren arbeiten. Stattdessen als das Bild auf dem Server öffnen, speichern Sie das Python-Objekt `plot` als **Varbinary** Daten und Schreiben Sie dann, dass in einer Datei, können gemeinsam genutzt oder an anderer Stelle angezeigt.

### <a name="create-a-plot-as-varbinary-data"></a>Erstellen Sie eine Grafik als Varbinary-Daten

Die gespeicherte Prozedur gibt eine serialisierten Python `figure` Objekt als Datenstrom von **Varbinary** Daten. Sie können keine binären Daten direkt anzeigen, aber Sie können Python-Code auf dem Client verwenden, für die Deserialisierung und die Zahlen anzeigen und speichern Sie die Image-Datei auf einem Clientcomputer.

1. Erstellen der gespeicherten Prozedur **PyPlotMatplotlib**, wenn das PowerShell-Skript nicht bereits getan.

    - Die Variable `@query` definiert den Abfragetext `SELECT tipped FROM nyctaxi_sample`, die an den Python-Code-Block übergeben wird, als Argument für die skripteingabevariable `@input_data_1`.
    - Das Python-Skript ist recht einfach: **Matplotlib** `figure` Objekte verwendet, um das Histogramm und die XY-Diagramm, und diese Objekte werden dann serialisiert mithilfe der `pickle` Bibliothek.
    - Das Python-Graphics-Objekt serialisiert wird, um eine **Pandas** Dataframes für die Ausgabe.
  
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

2. Führen Sie nun die gespeicherte Prozedur ohne Argumente zum Generieren eines Plots aus den Daten, die als Eingabeabfrage hartcodiert.

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

  
4. Aus einem [Python-Client](../python/setup-python-client-tools-sql.md), können Sie jetzt eine Verbindung herstellen, mit der SQL Server-Instanz, die die binäre Darstellung Objekte generiert, und die Diagramme anzeigen. 

    Zu diesem Zweck führen Sie den folgenden Python-Code, und Ersetzen Sie dabei den Servernamen, Datenbanknamen und die Anmeldeinformationen nach Bedarf. Stellen Sie sicher, dass die Python-Version auf dem Client und dem Server identisch ist. Stellen Sie außerdem sicher, dass die Python-Bibliotheken auf dem Client (z.B. Matplotlib) die gleiche oder eine höhere Version relativ zu den Bibliotheken, die auf dem Server installiert sind.
  
    **Verwenden von SQL Server-Authentifizierung:**
    
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

5.  Wenn die Verbindung erfolgreich ist, sollte sinngemäß die folgende Meldung angezeigt werden:
  
    *Die Plots werden im Verzeichnis gespeichert: Xxxx*
  
6.  Die Ausgabedatei wird in der Python-Arbeitsverzeichnis erstellt. Wenn das Diagramm anzeigen möchten, suchen Sie das Python-Arbeitsverzeichnis, und öffnen Sie die Datei. Die folgende Abbildung zeigt eine Grafik, die auf dem Clientcomputer gespeichert.
  
    ![Menge im Vergleich "fare" trinkgeldbetrag](media/sqldev-python-sample-plot.png "\"fare\" die Höhe des Trinkgelds Menge im Vergleich") 

## <a name="next-step"></a>Nächster Schritt

[Erstellen von Datenfunktionen mit T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>Vorherigen Schritt

[Das NYC Taxi-DataSet herunterladen](demo-data-nyctaxi-in-sql.md)

