---
title: Herunterladen von NYC Taxi-Demo-Daten und Skripts für eingebettete R und Python (SQL Server-Machine Learning) | Microsoft-Dokumentation
description: Anweisungen zum Herunterladen von New York City Taxi-Beispieldaten und eine Datenbank erstellen. Daten werden in SQL Server-Tutorials, die Ihnen das Einbetten von R und Python in SQL Server von gespeicherten Prozeduren und T-SQL-Funktionen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/02/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 700720f7538467dc3edc38414544eb2c402437a6
ms.sourcegitcommit: 615f8b5063aed679495d92a04ffbe00451d34a11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48232574"
---
# <a name="nyc-taxi-demo-data-for-sql-server"></a>NYC-taxidaten-Demo für SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie Sie Beispieldaten für R und Python-Tutorials für die datenbankinternen Analysen in SQL Server erhalten wird.

Daten stammen aus der [NYC Taxi and Limousine Commission](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml) öffentlichen DataSet. Wir haben eine Momentaufnahme des Datasets und die erfassten ein Prozent der verfügbaren Daten für unsere Demodatenbank. Auf Ihrem System ist die Datenbanksicherungsdatei etwas mehr als 90 MB, 1,7 Millionen Zeilen in der primären Datentabelle bereitstellen.

Wenn Sie mit den Schritten in diesem Artikel haben die **NYCTaxi_Sample** -Datenbank auf der lokalen Instanz, die Demodaten bereitstellt, praxisnahe Lerninhalte verfügbar ist. Der Datenbankname muss **NYCTaxi_Sample** , wenn Sie die demoskripts ohne weitere Änderungen ausführen möchten.

## <a name="prerequisites"></a>Erforderliche Komponenten

Sie benötigen eine Internetverbindung besteht, lokale Administratorrechte auf dem Computer, und eine Instanz der Datenbank-Engine.

Werden kann, [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) oder ein anderes Tool, um zu überprüfen, ob Objekt-und Arrayerstellung.

## <a name="download-demo-database"></a>Herunterladen von Demo-Datenbank

Die Beispieldatenbank ist eine Sicherungsdatei, die von Microsoft gehostet wird. Dateidownload beginnt sofort bei der Sie den Link klicken. 

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
|**NYCTaxi_Sample** | Datenbank |Durch das Skript Create-Db-Tb-Upload-data.sql erstellt. Erstellt eine Datenbank und zwei Tabellen:<br /><br />Tabelle der nyctaxi_sample: enthält das hauptdataset von NYC Taxi. Einer Tabelle wird ein gruppierter Columnstore-Index hinzugefügt, um den Speicher und die Abfrageleistung zu verbessern. Das 1 %-Beispiel des Datasets NYC Taxi wird in dieser Tabelle eingefügt.<br /><br />dbo.nyc_taxi_models-Tabelle: verwendet, um das trainierte advanced Analytics-Modell dauerhaft speichern.|
|**fnCalculateDistance** |Skalarwertfunktion | Durch das Skript fnCalculateDistance.sql erstellt. Wird die direkte Entfernung zwischen den Abhol-und Zielorten berechnet. Diese Funktion dient [Erstellen von Datenfunktionen](sqldev-create-data-features-using-t-sql.md), [trainieren und Speichern eines Modells](../r/sqldev-train-and-save-a-model-using-t-sql.md) und [Operationalisieren des R-Modells](sqldev-operationalize-the-model.md).|
|**fnEngineerFeatures** |Tabellenwertfunktion | Durch das Skript fnEngineerFeatures.sql erstellt. Erstellt neue Datenfunktionen für das Trainieren des Modells an. Diese Funktion dient [Erstellen von Datenfunktionen](sqldev-create-data-features-using-t-sql.md) und [Operationalisieren des R-Modells](sqldev-operationalize-the-model.md).|
|**PlotHistogram** |) | Durch das Skript PlotHistogram.sql erstellt. Ruft eine R-Funktion, um das Histogramm einer Variablen zu zeichnen, und gibt dann das Diagramm als binäres Objekt zurück. Diese gespeicherte Prozedur wird verwendet, [untersuchen und Visualisieren von Daten](sqldev-explore-and-visualize-the-data.md).|
|**PlotInOutputFiles** |)| Durch das Skript PlotInOutputFiles.sql erstellt. Erstellt eine Grafik mithilfe einer R-Funktion, und klicken Sie dann die Ausgabe als lokale PDF-Datei gespeichert. Diese gespeicherte Prozedur wird verwendet, [untersuchen und Visualisieren von Daten](sqldev-explore-and-visualize-the-data.md).|
|**PersistModel** |) | Durch das Skript PersistModel.sql erstellt. Wird ein Modell, das in einen Varbinary-Datentyp serialisiert wurde, und schreibt sie in der angegebenen Tabelle. |
|**PredictTip**  |) |Durch das Skript PredictTip.sql erstellt. Ruft das trainierte Modell zum Erstellen von Vorhersagen mit dem Modell an. Die gespeicherte Prozedur akzeptiert eine Abfrage als Eingabeparameter und gibt eine Spalte mit numerischen Werten zurück, die die Bewertungen für die Eingabezeilen enthält. Diese gespeicherte Prozedur wird verwendet, [Operationalisieren des R-Modells](sqldev-operationalize-the-model.md).|
|**PredictTipSingleMode**  |)| Durch das Skript PredictTipSingleMode.sql erstellt. Ruft das trainierte Modell zum Erstellen von Vorhersagen mit dem Modell an. Diese gespeicherte Prozedur akzeptiert als Eingabe eine neue Beobachtung mit einzelnen Funktionswerten, die als Inlineparameter übergeben werden, und gibt einen Wert zurück, der das Ergebnis für die neue Beobachtung vorhersagt. Diese gespeicherte Prozedur wird verwendet, [Operationalisieren des R-Modells](sqldev-operationalize-the-model.md).|
|**TrainTipPredictionModel**  |)|Durch das Skript TrainTipPredictionModel.sql erstellt. Trainiert ein Logistisches Regressionsmodell durch Aufrufen eines R-Pakets. Das Modell sagt den Wert der tipped-Spalte voraus und wird mithilfe von zufällig ausgewählten 70 % der Daten trainiert. Die Ausgabe der gespeicherten Prozedur ist das trainierte Modell, das in der Tabelle nyc_taxi_models gespeichert wird. Diese gespeicherte Prozedur wird verwendet, [trainieren und Speichern eines Modells](../r/sqldev-train-and-save-a-model-using-t-sql.md).|

## <a name="query-data-for-verification"></a>Abfragen von Daten für die Überprüfung

Führen Sie als Schritt zur Überprüfung eine Abfrage aus, um sicherzustellen, dass die Daten hochgeladen wurden.

1. Im Objekt-Explorer unter "Datenbanken", mit der Maustaste der **NYCTaxi_Sample** Datenbank, und starten Sie eine neue Abfrage.

2. Führen Sie **`select * from dbo.nyctaxi_sample`** zur Rückgabe aller 1,7 Millionen Zeilen.

## <a name="next-steps"></a>Nächste Schritte

Beispieldaten für die NYC Taxi ist jetzt verfügbar, praxisnahe Lerninhalte.

+ [Erfahren Sie mehr in-Database-Analyse, die mithilfe von R in SQL Server](sqldev-in-database-r-for-sql-developers.md)