---
title: Herunterladen von NYC Taxi-Demodaten und Skripts für eingebettete R und python
description: Anweisungen zum Herunterladen von New York City Taxi-Beispiel Daten und zum Erstellen einer Datenbank. Daten werden in SQL Server python-und R-Lernprogrammen verwendet, die veranschaulichen, wie Skripts in SQL Server gespeicherten Prozeduren und T-SQL-Funktionen eingebettet werden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/31/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a5b60397bb3581ba2d210a6b4469184306145c8a
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714864"
---
# <a name="nyc-taxi-demo-data-for-sql-server-python-and-r-tutorials"></a>NYC Taxi-Demo Daten für SQL Server python-und R-Tutorials
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird erläutert, wie Sie eine Beispieldatenbank einrichten, die aus öffentlichen Daten aus der [New York City Taxi-und der Limousine-Kommission](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)besteht. Diese Daten werden in mehreren R-und Python-Tutorials für datenbankübergreifende Analysen auf SQL Server verwendet. Damit der Beispielcode schneller ausgeführt wird, haben wir eine repräsentative 1%-Stichprobe der Daten erstellt. Auf dem System ist die Daten Bank Sicherungsdatei etwas mehr als 90 MB groß und bietet 1,7 Millionen Zeilen in der primären Datentabelle.

Um diese Übung abzuschließen, sollten Sie über [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) oder ein anderes Tool verfügen, das eine Daten Bank Sicherungsdatei wiederherstellen und T-SQL-Abfragen ausführen kann.

Zu den Tutorials und Schnellstarts, die dieses DataSet verwenden, gehören die folgenden:

+ [Erlernen Sie Daten bankübergreifende Analysen mithilfe von R in SQL Server](sqldev-in-database-r-for-sql-developers.md)
+ [Informieren Sie sich in Daten Bank Analysen mithilfe von python in SQL Server](sqldev-in-database-python-for-sql-developers.md)

## <a name="download-files"></a>Dateien herunterladen

Die-Beispieldatenbank ist eine von Microsoft gehostete SQL Server 2016 BAK-Datei. Sie können Sie auf SQL Server 2016 und höher wiederherstellen. Der Download der Datei beginnt sofort, wenn Sie auf den Link klicken. 

Die Dateigröße beträgt ungefähr 90 MB.

1. Klicken Sie auf [NYCTaxi_Sample. bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak) , um die Daten Bank Sicherungsdatei herunterzuladen.

2. Kopieren Sie die Datei in den Ordner "c:\Programme\Microsoft SQL Server\MSSQL-instance-name\mssql\backup".

3. Klicken Sie in Management Studio mit der rechten Maustaste auf **Datenbanken** , und wählen Sie **Dateien und Dateigruppen wiederherstellen**.

4. Geben Sie *NYCTaxi_Sample* als Datenbanknamen ein.

5. Klicken Sie auf **von Gerät** , und öffnen Sie dann die Seite Dateiauswahl, um die Sicherungsdatei auszuwählen. Klicken Sie auf **Hinzufügen** , um NYCTaxi_Sample. bak auszuwählen.

6. Aktivieren Sie das Kontrollkästchen **Wiederherstellen** , und klicken Sie zum Wiederherstellen der Datenbank auf **OK**

## <a name="review-database-objects"></a>Datenbankobjekte überprüfen
   
Vergewissern Sie sich, dass die Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Bank Objekte [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]in der Instanz mit vorhanden sind Die Datenbank, die Tabellen, die Funktionen und die gespeicherten Prozeduren sollten angezeigt werden.
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

### <a name="objects-in-nyctaxisample-database"></a>Objekte in der NYCTaxi_Sample-Datenbank

In der folgenden Tabelle werden die in der NYC Taxi Demo-Datenbank erstellten Objekte zusammengefasst.

|**Objektname**|**Objekttyp**|**Beschreibung**|
|----------|------------------------|---------------|
|**NYCTaxi_Sample** | Datenbank | Erstellt eine Datenbank und zwei Tabellen:<br /><br />dbo. nyctaxi_sample-Tabelle: Enthält das Haupt DataSet von NYC Taxi. Einer Tabelle wird ein gruppierter Columnstore-Index hinzugefügt, um den Speicher und die Abfrageleistung zu verbessern. Das 1%-Beispiel des NYC Taxi-Datasets wird in diese Tabelle eingefügt.<br /><br />dbo. NYC _taxi_models Tabelle: Wird verwendet, um das trainierte Advanced Analytics-Modell beizubehalten.|
|**fnCalculateDistance** |Skalarwertfunktion | Berechnet den direkten Abstand zwischen Pickup-und Zielort-Speicherorten. Diese Funktion wird bei der [Erstellung von Daten Features](sqldev-create-data-features-using-t-sql.md), beim [trainieren und Speichern eines Modells](sqldev-train-and-save-a-model-using-t-sql.md) und [beim operationalisieren des R-Modells](sqldev-operationalize-the-model.md)verwendet.|
|**fnEngineerFeatures** |Tabellenwertfunktion | Erstellt neue Daten Features für das Modell Training. Diese Funktion wird in [Erstellen von Datenfunktionen](sqldev-create-data-features-using-t-sql.md) und [operationalisieren des R-Modells](sqldev-operationalize-the-model.md)verwendet.|


Gespeicherte Prozeduren werden mithilfe von R-und python-Skripts in verschiedenen Tutorials erstellt. In der folgenden Tabelle werden die gespeicherten Prozeduren zusammengefasst, die Sie optional der NYC Taxi Demo-Datenbank hinzufügen können, wenn Sie Skripts aus verschiedenen Lektionen ausführen.

|**Gespeicherte Prozedur**|**Sprache**|**Beschreibung**|
|-------------------------|------------|---------------|
|**Rxplothistogram** |R | Ruft die revoscaler rxhistogram-Funktion auf, um das Histogramm einer Variablen zu zeichnen, und gibt dann das Diagramm als binäres Objekt zurück. Diese gespeicherte Prozedur wird zum durch [Suchen und Visualisieren von Daten](sqldev-explore-and-visualize-the-data.md)verwendet.|
|**RPlotRHist** |R| Erstellt eine Grafik mithilfe der Hist-Funktion und speichert die Ausgabe als lokale PDF-Datei. Diese gespeicherte Prozedur wird zum durch [Suchen und Visualisieren von Daten](sqldev-explore-and-visualize-the-data.md)verwendet.|
|**Rxtrainlogitmodel**  |R| Trainiert ein logistisches Regressionsmodell durch Aufrufen eines R-Pakets. Das Modell sagt den Wert der tipped-Spalte voraus und wird mithilfe von zufällig ausgewählten 70 % der Daten trainiert. Die Ausgabe der gespeicherten Prozedur ist das trainierte Modell, das in der Tabelle nyc_taxi_models gespeichert wird. Diese gespeicherte Prozedur wird beim [trainieren und Speichern eines Modells](sqldev-train-and-save-a-model-using-t-sql.md)verwendet.|
|**RxPredictBatchOutput**  |R | Ruft das trainierte Modell auf, um Vorhersagen mit dem Modell zu erstellen. Die gespeicherte Prozedur akzeptiert eine Abfrage als Eingabeparameter und gibt eine Spalte mit numerischen Werten zurück, die die Bewertungen für die Eingabezeilen enthält. Diese gespeicherte Prozedur wird verwendet, um [potenzielle Ergebnisse vorherzusagen](sqldev-operationalize-the-model.md).|
|**RxPredictSingleRow**  |R| Ruft das trainierte Modell auf, um Vorhersagen mit dem Modell zu erstellen. Diese gespeicherte Prozedur akzeptiert als Eingabe eine neue Beobachtung mit einzelnen Funktionswerten, die als Inlineparameter übergeben werden, und gibt einen Wert zurück, der das Ergebnis für die neue Beobachtung vorhersagt. Diese gespeicherte Prozedur wird verwendet, um [potenzielle Ergebnisse vorherzusagen](sqldev-operationalize-the-model.md).|

## <a name="query-the-data"></a>Abfragen der Daten

Führen Sie als Überprüfungs Schritt eine Abfrage aus, um zu bestätigen, dass die Daten hochgeladen wurden.

1. Klicken Sie in Objekt-Explorer unter Datenbanken mit der rechten Maustaste auf die **NYCTaxi_Sample** -Datenbank, und starten Sie eine neue Abfrage.

2. Führen Sie einige einfache Abfragen aus:

    ```sql
    SELECT TOP(10) * FROM dbo.nyctaxi_sample;
    SELECT COUNT(*) FROM dbo.nyctaxi_sample;
    ```
Die Datenbank enthält 1,7 Millionen Zeilen.

3. In der Datenbank befindet sich eine **nyctaxi_sample** -Tabelle, die das DataSet enthält. Die Tabelle wurde für Satz basierte Berechnungen optimiert, wobei ein [columnstore--Index](../../relational-databases/indexes/columnstore-indexes-overview.md)hinzugefügt wurde. Führen Sie diese Anweisung aus, um eine kurze Zusammenfassung der Tabelle zu generieren.

    ```sql
    SELECT DISTINCT [passenger_count]
        , ROUND (SUM ([fare_amount]),0) as TotalFares
        , ROUND (AVG ([fare_amount]),0) as AvgFares
    FROM [dbo].[nyctaxi_sample]
    GROUP BY [passenger_count]
    ORDER BY  AvgFares DESC
    ````
Die Ergebnisse sollten ähnlich wie im folgenden Screenshot angezeigt werden.

  ![Tabellen Zusammenfassungs Informationen](media/nyctaxidatatablesummary.png "Abfrageergebnisse")

## <a name="next-steps"></a>Nächste Schritte

Die NYC Taxi-Beispiel Daten sind jetzt für praktische Lernmöglichkeiten verfügbar.

+ [Erlernen Sie Daten bankübergreifende Analysen mithilfe von R in SQL Server](sqldev-in-database-r-for-sql-developers.md)
+ [Informieren Sie sich in Daten Bank Analysen mithilfe von python in SQL Server](sqldev-in-database-python-for-sql-developers.md)