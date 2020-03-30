---
title: NYC Taxi-Demodaten für Tutorials
description: Erstellen Sie eine Datenbank mit Beispieldaten zu Taxis in New York City. Dieses Dataset wird in R- und Python-Tutorials für SQL Server Machine Learning Services verwendet.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/31/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e55076a539cb2a932c2f1e0c432daf774899518f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "74908923"
---
# <a name="nyc-taxi-demo-data-for-sql-server-python-and-r-tutorials"></a>NYC Taxi-Demodaten für Python- und R-Tutorials in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird beschrieben, wie eine Beispieldatenbank mit öffentlichen Daten von der [New York City Taxi and Limousine Commission](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml) eingerichtet wird. Diese Daten werden in verschiedenen R- und Python-Tutorials für datenbankinterne Analysen unter SQL Server verwendet. Damit der Beispielcode schneller ausgeführt werden kann, haben wir ein repräsentatives 1 %-Sampling der Daten erstellt. In unserem System ist die Datenbanksicherungsdatei etwas größer als 90 MB, wobei sich in der primären Datentabelle 1,7 Millionen Datensätze befinden.

Für diese Übung benötigen Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) oder ein anderes Tool zum Wiederherstellen einer Datenbanksicherungsdatei sowie zum Ausführen von T-SQL-Abfragen.

Dieses Dataset wird in folgenden Tutorials und Schnellstarts verwendet:

+ [Kennenlernen der datenbankinternen Analyse mithilfe von R in SQL Server](sqldev-in-database-r-for-sql-developers.md)
+ [Kennenlernen der datenbankinternen Analyse mithilfe von Python in SQL Server](sqldev-in-database-python-for-sql-developers.md)

## <a name="download-files"></a>Herunterladen von Dateien

Bei der Beispieldatenbank handelt es sich um eine von Microsoft gehostete SQL Server 2016-BAK-Datei. Sie kann unter SQL Server 2016 und höher wiederhergestellt werden. Der Download der Datei beginnt sofort, wenn Sie auf den Link klicken. 

Die Dateigröße beträgt ungefähr 90 MB.

1. Klicken Sie auf [NYCTaxi_Sample.bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak), um die Datenbanksicherungsdatei herunterzuladen.

2. Kopieren Sie die Datei in den Ordner „C:\Programme\Microsoft SQL Server\MSSQL-Instanzname\MSSQL\Backup“.

3. Klicken Sie in Management Studio mit der rechten Maustaste auf **Datenbanken**, und wählen Sie **Dateien und Dateigruppen wiederherstellen** aus.

4. Geben Sie als Datenbanknamen *NYCTaxi_Sample* ein.

5. Klicken Sie auf **Von Gerät**, und öffnen Sie anschließend die Seite zum Auswählen von Dateien, um die Sicherungsdatei auszuwählen. Klicken Sie auf **Hinzufügen**, um die Datei „NYCTaxi_Sample.bak“ auszuwählen.

6. Aktivieren Sie das Kontrollkästchen **Wiederherstellen**, und klicken Sie auf **OK**, um die Datenbank wiederherzustellen.

## <a name="review-database-objects"></a>Überprüfen von Datenbankobjekten
   
Vergewissern Sie sich mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dass die Datenbankobjekte in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz vorhanden sind. Dabei sollten Datenbank, Tabellen, Funktionen und gespeicherte Prozeduren angezeigt werden.
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

### <a name="objects-in-nyctaxi_sample-database"></a>Objekte in der Datenbank „NYCTaxi_Sample“

In der folgenden Tabelle finden Sie eine Übersicht über die in der Demodatenbank „NYCTaxi_Sample“ erstellten Objekte.

|**Objektname**|**Objekttyp**|**Beschreibung**|
|----------|------------------------|---------------|
|**NYCTaxi_Sample** | database | Erstellt eine Datenbank und zwei Tabellen:<br /><br />Tabelle „dbo.nyctaxi_sample“: Enthält das Hauptdataset von NYC Taxi. Einer Tabelle wird ein gruppierter Columnstore-Index hinzugefügt, um den Speicher und die Abfrageleistung zu verbessern. Die 1 %-Stichprobe des NYC Taxi-Datasets wird in diese Tabelle eingefügt.<br /><br />Tabelle „dbo.nyc_taxi_models“: Wird zum Speichern des trainierten Modells für die erweiterte Analyse verwendet.|
|**fnCalculateDistance** |Skalarwertfunktion | Berechnet die direkte Entfernung zwischen Abhol- und Ablageorten. Diese Funktion wird in den Lektionen [Erstellen von Datenfeatures](sqldev-create-data-features-using-t-sql.md), [Trainieren und Speichern eines Modells](sqldev-train-and-save-a-model-using-t-sql.md) und [Operationalisieren des R-Modells](sqldev-operationalize-the-model.md) verwendet.|
|**fnEngineerFeatures** |Tabellenwertfunktion | Erstellt neue Datenfeatures für das Modelltraining. Diese Funktion wird in den Lektionen [Erstellen von Datenfeatures](sqldev-create-data-features-using-t-sql.md) und [Operationalisieren des R-Modells](sqldev-operationalize-the-model.md) verwendet.|


Gespeicherte Prozeduren werden mithilfe von R- und Python-Skripts erstellt, die sich in verschiedenen Tutorials befinden. In der folgenden Tabelle finden Sie eine Übersicht über die gespeicherten Prozeduren, die Sie der NYC Taxi-Demodatenbank optional hinzufügen können, wenn Sie die Skripts in den verschiedenen Lektion ausführen.

|**Gespeicherte Prozedur**|**Sprache**|**Beschreibung**|
|-------------------------|------------|---------------|
|**RxPlotHistogram** |R | Ruft die RevoScaleR-Funktion „rxHistogram“ auf, um das Histogramm einer Variablen zu zeichnen und gibt anschließend das Diagramm als binäres Objekt zurück. Diese gespeicherte Prozedur wird in der Lektion [Untersuchen und Visualisieren von Daten](sqldev-explore-and-visualize-the-data.md) verwendet.|
|**RPlotRHist** |R| Erstellt eine Grafik mithilfe einer Hist-Funktion, und speichert die Ausgabe als lokale PDF-Datei. Diese gespeicherte Prozedur wird in der Lektion [Untersuchen und Visualisieren von Daten](sqldev-explore-and-visualize-the-data.md) verwendet.|
|**RxTrainLogitModel**  |R| Trainiert ein logistisches Regressionsmodell durch Aufrufen eines R-Pakets. Das Modell sagt den Wert der tipped-Spalte voraus und wird mithilfe von zufällig ausgewählten 70 % der Daten trainiert. Die Ausgabe der gespeicherten Prozedur ist das trainierte Modell, das in der Tabelle nyc_taxi_models gespeichert wird. Diese gespeicherte Prozedur wird in der Lektion [Trainieren und Speichern eines Modells](sqldev-train-and-save-a-model-using-t-sql.md).|
|**RxPredictBatchOutput**  |R | Ruft das trainierte Modell zum Erstellen von Vorhersagen mit dem Modell auf. Die gespeicherte Prozedur akzeptiert eine Abfrage als Eingabeparameter und gibt eine Spalte mit numerischen Werten zurück, die die Bewertungen für die Eingabezeilen enthält. Diese gespeicherte Prozedur wird in der Lektion [Vorhersagen potenzieller Ergebnisse](sqldev-operationalize-the-model.md) verwendet.|
|**RxPredictSingleRow**  |R| Ruft das trainierte Modell zum Erstellen von Vorhersagen mit dem Modell auf. Diese gespeicherte Prozedur akzeptiert als Eingabe eine neue Beobachtung mit einzelnen Funktionswerten, die als Inlineparameter übergeben werden, und gibt einen Wert zurück, der das Ergebnis für die neue Beobachtung vorhersagt. Diese gespeicherte Prozedur wird in der Lektion [Vorhersagen potenzieller Ergebnisse](sqldev-operationalize-the-model.md) verwendet.|

## <a name="query-the-data"></a>Abfragen der Daten

Führen Sie eine Abfrage aus, um zu prüfen, ob die Daten hochgeladen wurden.

1. Klicken Sie in Objekt-Explorer unter „Datenbanken“ mit der rechten Maustaste auf die Datenbank **NYCTaxi_Sample**, und starten Sie eine neue Abfrage.

2. Führen Sie einige einfache Abfragen aus:

    ```sql
    SELECT TOP(10) * FROM dbo.nyctaxi_sample;
    SELECT COUNT(*) FROM dbo.nyctaxi_sample;
    ```
Die Datenbank enthält 1,7 Millionen Datensätze.

3. In der Datenbank befindet sich die Tabelle **nyctaxi_sample**, die das Dataset enthält. Die Tabelle wurde für setbasierte Berechnungen optimiert, indem ein [Columnstore-Index](../../relational-databases/indexes/columnstore-indexes-overview.md) hinzugefügt wurde. Führen Sie diese Anweisung aus, um eine schnelle Zusammenfassung für die Tabelle zu generieren.

    ```sql
    SELECT DISTINCT [passenger_count]
        , ROUND (SUM ([fare_amount]),0) as TotalFares
        , ROUND (AVG ([fare_amount]),0) as AvgFares
    FROM [dbo].[nyctaxi_sample]
    GROUP BY [passenger_count]
    ORDER BY  AvgFares DESC
    ````
Die Ergebnisse sollten ähnlich aussehen wie die im folgenden Screenshot.

  ![Zusammenfassungsinformationen der Tabelle](media/nyctaxidatatablesummary.png "Abfrageergebnisse")

## <a name="next-steps"></a>Nächste Schritte

Die NYC Taxi-Beispieldaten sind nun für die praktischen Übungen verfügbar.

+ [Kennenlernen der datenbankinternen Analyse mithilfe von R in SQL Server](sqldev-in-database-r-for-sql-developers.md)
+ [Kennenlernen der datenbankinternen Analyse mithilfe von Python in SQL Server](sqldev-in-database-python-for-sql-developers.md)