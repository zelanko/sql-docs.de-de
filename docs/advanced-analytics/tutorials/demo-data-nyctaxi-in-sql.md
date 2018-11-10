---
title: Herunterladen von NYC Taxi-Demo-Daten und Skripts für eingebettete R und Python (SQL Server-Machine Learning) | Microsoft-Dokumentation
description: Anweisungen zum Herunterladen von New York City Taxi-Beispieldaten und eine Datenbank erstellen. Daten werden in SQL Server Python und R-Sprache-Tutorials, die Ihnen zum Einbetten von Skript in SQL Server gespeicherte Prozeduren und T-SQL-Funktionen verwendet.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/31/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3618504d0db8003df7787778d84d62990c83b8fb
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51217798"
---
# <a name="nyc-taxi-demo-data-for-sql-server-python-and-r-tutorials"></a>NYC-taxidaten-Demo für SQL Server Python und R-tutorials
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel erläutert das Einrichten einer Beispieldatenbank bestehend aus öffentlichen Daten aus der [New York City-Taxi and Limousine Commission](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml). Diese Daten werden in mehrere R- und Python-Tutorials für die datenbankinternen Analysen für SQL Server verwendet. Um den Beispielcode schneller ausgeführt werden soll, haben wir einen repräsentativen Querschnitt von 1 % der Daten erstellt. Auf Ihrem System ist die Datenbanksicherungsdatei etwas mehr als 90 MB, 1,7 Millionen Zeilen in der primären Datentabelle bereitstellen.

Um in dieser Übung abgeschlossen haben, müssen Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) oder ein anderes Tool, das Wiederherstellen einer Datenbank-Sicherungsdatei und T-SQL-Abfragen ausführen kann.

Lernprogramme und dieses DataSet mit Schnellstarts umfassen Folgendes:

+ [Erfahren Sie mehr in-Database-Analyse, die mithilfe von R in SQL Server](sqldev-in-database-r-for-sql-developers.md)
+ [Erfahren Sie mehr in-Database-Analyse, die mithilfe von Python in SQL Server](sqldev-in-database-python-for-sql-developers.md)

## <a name="download-files"></a>Herunterladen von Dateien

Die Beispieldatenbank ist eine SQL Server 2016 BAK-Datei, die von Microsoft gehostet wird. Sie können diese wiederherstellen, auf SQL Server 2016 und höher. Dateidownload beginnt sofort bei der Sie den Link klicken. 

Dateigröße beträgt ca. 90 MB.

1. Klicken Sie auf [NYCTaxi_Sample.bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak) Sicherungsdatei der Datenbank herunterladen.

2. Kopieren Sie die Datei zu c:\Programme\Microsoft SQL Server\MSSQL-Instanz-Name\MSSQL\Backup Folder.

3. In Management Studio, mit der Maustaste **Datenbanken** , und wählen Sie **Wiederherstellen von Dateien und Dateigruppen**.

4. Geben Sie *NYCTaxi_Sample* als Datenbankname verwendet.

5. Klicken Sie auf **vom Gerät** und öffnen Sie dann auf der Auswahlseite für die Datei um die Sicherungsdatei auszuwählen. Klicken Sie auf **hinzufügen** NYCTaxi_Sample.bak auswählen.

6. Wählen Sie die **wiederherstellen** Kontrollkästchen und klicken Sie auf **OK** zum Wiederherstellen der Datenbank.

## <a name="review-database-objects"></a>Überprüfen Sie die Datenbankobjekte
   
Vergewissern Sie sich die Datenbankobjekte vorhanden sind, auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Zielinstanz [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Daraufhin sollte die Datenbank, Tabellen, Funktionen und gespeicherten Prozeduren.
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

### <a name="objects-in-nyctaxisample-database"></a>Objekte in NYCTaxi_Sample-Datenbank

Die folgende Tabelle enthält die Objekte, die in der NYC Taxi-Demodatenbank erstellt.

|**Objektname**|**Objekttyp**|**Beschreibung**|
|----------|------------------------|---------------|
|**NYCTaxi_Sample** | Datenbank | Erstellt eine Datenbank und zwei Tabellen:<br /><br />Tabelle der nyctaxi_sample: enthält das hauptdataset von NYC Taxi. Einer Tabelle wird ein gruppierter Columnstore-Index hinzugefügt, um den Speicher und die Abfrageleistung zu verbessern. Das 1 %-Beispiel des Datasets NYC Taxi wird in dieser Tabelle eingefügt.<br /><br />dbo.nyc_taxi_models-Tabelle: verwendet, um das trainierte advanced Analytics-Modell dauerhaft speichern.|
|**fnCalculateDistance** |Skalarwertfunktion | Wird die direkte Entfernung zwischen den Abhol-und Zielorten berechnet. Diese Funktion dient [Erstellen von Datenfunktionen](sqldev-create-data-features-using-t-sql.md), [trainieren und Speichern eines Modells](sqldev-train-and-save-a-model-using-t-sql.md) und [Operationalisieren des R-Modells](sqldev-operationalize-the-model.md).|
|**fnEngineerFeatures** |Tabellenwertfunktion | Erstellt neue Datenfunktionen für das Trainieren des Modells an. Diese Funktion dient [Erstellen von Datenfunktionen](sqldev-create-data-features-using-t-sql.md) und [Operationalisieren des R-Modells](sqldev-operationalize-the-model.md).|


Gespeicherte Prozeduren werden mit R und Python-Skript finden Sie in den verschiedenen Tutorials erstellt. Die folgende Tabelle enthält die gespeicherten Prozeduren, die Sie optional auf die NYC Taxi-Demo-Datenbank, beim Ausführen von Skripts aus verschiedenen Lektionen hinzufügen können.

|**gespeicherte Prozedur**|**Sprache**|**Beschreibung**|
|-------------------------|------------|---------------|
|**RxPlotHistogram** |R | Ruft die RevoScaleR-RxHistogram-Funktion, um das Histogramm einer Variablen zu zeichnen, und gibt dann das Diagramm als binäres Objekt zurück. Diese gespeicherte Prozedur wird verwendet, [untersuchen und Visualisieren von Daten](sqldev-explore-and-visualize-the-data.md).|
|**RPlotRHist** |R| Erstellt eine Grafik, die mithilfe der HIS-Funktion, und speichert die Ausgabe als lokale PDF-Datei. Diese gespeicherte Prozedur wird verwendet, [untersuchen und Visualisieren von Daten](sqldev-explore-and-visualize-the-data.md).|
|**RxTrainLogitModel**  |R| Trainiert ein Logistisches Regressionsmodell durch Aufrufen eines R-Pakets. Das Modell sagt den Wert der tipped-Spalte voraus und wird mithilfe von zufällig ausgewählten 70 % der Daten trainiert. Die Ausgabe der gespeicherten Prozedur ist das trainierte Modell, das in der Tabelle nyc_taxi_models gespeichert wird. Diese gespeicherte Prozedur wird verwendet, [trainieren und Speichern eines Modells](sqldev-train-and-save-a-model-using-t-sql.md).|
|**RxPredictBatchOutput**  |R | Ruft das trainierte Modell zum Erstellen von Vorhersagen mit dem Modell an. Die gespeicherte Prozedur akzeptiert eine Abfrage als Eingabeparameter und gibt eine Spalte mit numerischen Werten zurück, die die Bewertungen für die Eingabezeilen enthält. Diese gespeicherte Prozedur wird verwendet, [potenzielle Vorhersageergebnisse](sqldev-operationalize-the-model.md).|
|**RxPredictSingleRow**  |R| Ruft das trainierte Modell zum Erstellen von Vorhersagen mit dem Modell an. Diese gespeicherte Prozedur akzeptiert als Eingabe eine neue Beobachtung mit einzelnen Funktionswerten, die als Inlineparameter übergeben werden, und gibt einen Wert zurück, der das Ergebnis für die neue Beobachtung vorhersagt. Diese gespeicherte Prozedur wird verwendet, [potenzielle Vorhersageergebnisse](sqldev-operationalize-the-model.md).|

## <a name="query-the-data"></a>Abfragen der Daten

Führen Sie als Schritt zur Überprüfung eine Abfrage aus, um sicherzustellen, dass die Daten hochgeladen wurden.

1. Im Objekt-Explorer unter "Datenbanken", mit der Maustaste der **NYCTaxi_Sample** Datenbank, und starten Sie eine neue Abfrage.

2. Führen Sie einige einfachen Abfragen:

    ```sql
    SELECT TOP(10) * FROM dbo.nyctaxi_sample;
    SELECT COUNT(*) FROM dbo.nyctaxi_sample;
    ```
Die Datenbank enthält 1.7 Millionen Zeilen.

3. In der Datenbank ist eine **Nyctaxi_sample** Tabelle, die das DataSet enthält. Die Tabelle wurde für setbasierte Vorgänge durch das Hinzufügen von optimiert eine [columnstore-Index](../../relational-databases/indexes/columnstore-indexes-overview.md). Führen Sie diese Anweisung aus, um eine kurze Zusammenfassung für die Tabelle zu generieren.

    ```SQL
    SELECT DISTINCT [passenger_count]
        , ROUND (SUM ([fare_amount]),0) as TotalFares
        , ROUND (AVG ([fare_amount]),0) as AvgFares
    FROM [dbo].[nyctaxi_sample]
    GROUP BY [passenger_count]
    ORDER BY  AvgFares DESC
    ````
Ergebnisse sollten ähnlich im folgenden Screenshot angezeigt sein.

  ![Zusammenfassung der Informationen in der Tabelle](media/nyctaxidatatablesummary.png "Abfrageergebnisse")

## <a name="next-steps"></a>Nächste Schritte

Beispieldaten für die NYC Taxi ist jetzt verfügbar, praxisnahe Lerninhalte.

+ [Erfahren Sie mehr in-Database-Analyse, die mithilfe von R in SQL Server](sqldev-in-database-r-for-sql-developers.md)
+ [Erfahren Sie mehr in-Database-Analyse, die mithilfe von Python in SQL Server](sqldev-in-database-python-for-sql-developers.md)