---
title: Herunterladen von NYC Taxi-Demo-Daten und Skripts für eingebettete R und Python (SQL Server-Machine Learning) | Microsoft-Dokumentation
description: Anweisungen zum Herunterladen von New York City Taxi-Beispieldaten und eine Datenbank erstellen. Daten werden in SQL Server-Tutorials, die Ihnen das Einbetten von R und Python in SQL Server von gespeicherten Prozeduren und T-SQL-Funktionen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/22/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 58a996ae500a27a6878b30fc072bf09a75d4ba43
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "46712753"
---
# <a name="nyc-taxi-demo-data-for-sql-server"></a>NYC-taxidaten-Demo für SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird Ihr System für die Lernprogramme zum Verwenden von R und Python für in-Database-Analyse in SQL Server vorbereitet.

In dieser Übung Laden Sie Beispieldaten, ein PowerShell-Skript für die Vorbereitung der Umgebung herunter und [!INCLUDE[tsql](../../includes/tsql-md.md)] Skriptdateien, die in mehrere Tutorials verwendet. Wenn Sie fertig sind, sind ein **NYCTaxi_Sample** -Datenbank auf der lokalen Instanz, die Demodaten bereitstellt, praxisnahe Lerninhalte verfügbar ist. 

## <a name="prerequisites"></a>Erforderliche Komponenten

Sie benötigen eine Internetverbindung besteht, PowerShell und lokale Administratorrechte auf dem Computer. Sie müssen [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) oder ein anderes Tool, um zu überprüfen, ob Objekt-und Arrayerstellung.

## <a name="download-nyc-taxi-demo-data-and-scripts-from-github"></a>NYC Taxi-Demo-Daten und Skripts von Github herunterladen

1.  Öffnen Sie eine Windows PowerShell-Befehlskonsole.
  
    Verwenden der **als Administrator ausführen** Option, um das Zielverzeichnis zu erstellen oder zum Schreiben von Dateien in das angegebene Ziel.
  
2.  Führen Sie die folgenden PowerShell-Befehle aus, die den Wert des Parameters *DestDir* auf jedem beliebigen lokalen Verzeichnis ändern. Wir haben in diesem Fall **TempRSQL**verwendet.
  
    ```ps
    $source = ‘https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_SQL_Walkthrough.ps1’  
    $ps1_dest = “$pwd\Download_Scripts_SQL_Walkthrough.ps1”
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir ‘C:\tempRSQL’
    ```
  
    Wenn der von Ihnen angegebene Ordner in *DestDir* nicht existiert, wird er vom PowerShell-Skript erstellt.
  
    > [!TIP]
    > Wenn Sie eine Fehlermeldung erhalten, legen Sie vorübergehend die Richtlinie für die Ausführung von PowerShell-Skripts zum **uneingeschränkten** nur für diese exemplarische Vorgehensweise, indem Sie das Bypass-Argument und Bereichsauswahl die Änderungen an der aktuellen Sitzung.
    >   
    >````
    > Set\-ExecutionPolicy Bypass \-Scope Process
    >````
    > Das Ausführen dieses Befehls führt zu keiner Konfigurationsänderung.
  
    Abhängig von Ihrer Internetverbindung kann der Download eine Weile dauern.
  
3.  Wenn alle Dateien heruntergeladen wurden, das PowerShell-Skript wird geöffnet, um die *DestDir* Ordner. Führen Sie den folgenden Befehl in der PowerShell-Eingabeaufforderung aus, und überprüfen Sie die Dateien, die heruntergeladen wurden.
  
    ```
    ls
    ```
  
    **Ergebnisse:**
  
    ![Liste der von PowerShell-Skript heruntergeladenen Dateien](media/rsql-devtut-filelist.png "Liste der von PowerShell-Skript heruntergeladenen Dateien")

## <a name="create-nyctaxisample-database"></a>NYCTaxi_Sample Datenbank erstellen

Unter den heruntergeladenen Dateien, sehen Sie ein PowerShell-Skript (**RunSQL_SQL_Walkthrough.ps1**), der eine Datenbank erstellt, und lädt Daten in einem Massenvorgang. Die vom Skript ausgeführten Aktionen beinhalten:

+ Die SQL Native Client und der SQL-Befehlszeilenprogramme, installiert werden, sofern nicht bereits installiert. Diese Hilfsprogramme werden für das Massenladen der Daten in die Datenbank mithilfe von **bcp**benötigt.

+ Erstellen Sie eine Datenbank und Tabellen auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz, und die masseneinfügung für Daten, die eine CSV-Datei stammen.

+ Erstellen Sie mehrere SQL-Funktionen und gespeicherten Prozeduren, die in mehrere Tutorials verwendet.

### <a name="modify-the-script-to-use-a-trusted-windows-identity"></a>Ändern Sie das Skript aus, um einen vertrauenswürdigen Windows-Identität zu verwenden.

Standardmäßig nimmt das Skript einen SQL Server-Datenbank-Benutzeranmeldung und ein Kennwort. Wenn Sie unter Ihrem Windows-Benutzerkonto Db_owner sind, können Sie Ihre Windows-Identität, zum Erstellen der Objekte. Öffnen Sie zu diesem Zweck `RunSQL_SQL_Walkthrough.ps1` in einem Codeeditor, und fügen Sie **`-T`** die bcp masseneinfügung Befehl (Zeile 238):

```text
bcp $db_tb in $csvfilepath -t ',' -S $server -f taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U $u -P $p -T
```

### <a name="run-the-script-to-create-objects"></a>Führen Sie das Skript zum Erstellen von Objekten

Verwenden eine Administrator-PowerShell-Eingabeaufforderung auf C:\tempRSQL, führen Sie den folgenden Befehl aus.
  
```ps
.\RunSQL_SQL_Walkthrough.ps1
```
Sie werden aufgefordert, die folgende Informationen einzugeben:

- Server-Instanz, auf [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] installiert wurde. Auf einer Standardinstanz kann dies so einfach wie der Name des Computers sein.

- Datenbankname. In diesem Tutorial wird davon ausgegangen Skripts `NYCTaxi_Sample`.

- Benutzername und Benutzerkennwort. Geben Sie eine SQL Server-Datenbank-Anmeldung für diese Werte ein. Auch wenn Sie das Skript zum Akzeptieren von einer vertrauenswürdigen Windows-Identität geändert haben, drücken Sie EINGABETASTE, um diese Werte leer lassen. Ihre Windows-Identität wird für die Verbindung verwendet.

- Ein vollqualifizierter Dateiname für die Beispieldaten in der vorherigen Lektion heruntergeladen. Beispiel: `C:\tempRSQL\nyctaxi1pct.csv`

Nachdem Sie diese Werte angeben, wird das Skript sofort ausgeführt. Während der Ausführung des Skripts die Platzhalternamen in den [!INCLUDE[tsql](../../includes/tsql-md.md)] Skripts werden aktualisiert, um Eingaben zu verwenden, geben Sie Sie.

## <a name="review-database-objects"></a>Überprüfen Sie die Datenbankobjekte
   
Bei der Ausführung des Skripts abgeschlossen ist, bestätigen Sie die Datenbankobjekte vorhanden sind, auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Zielinstanz [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Daraufhin sollte die Datenbank, Tabellen, Funktionen und gespeicherten Prozeduren.
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

> [!NOTE]
> Wenn das Datenbankprojekt schon vorhanden ist, dann kann es nicht noch einmal erstellt werden.
>   
> Wenn die Tabelle bereits vorhanden ist, werden die Daten angefügt, nicht überschrieben. Achten Sie daher darauf, vorhandene Objekte zu löschen, bevor Sie das Skript ausführen.

### <a name="objects-in-nyctaxisample-database"></a>Objekte in NYCTaxi_Sample-Datenbank

Die folgende Tabelle enthält die Objekte, die in der NYC Taxi-Demodatenbank erstellt. Obwohl Sie nur ein PowerShell-Skript ausführen (`RunSQL_SQL_Walkthrough.ps1`), das Skript ruft die andere SQL-Skripts, die Objekte in der Datenbank zu erstellen. Skripts für jedes Objekt erstellen, werden in der Beschreibung erwähnt.

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

1. Erweitern Sie im Objekt-Explorer unter dem Datenbanken, die **NYCTaxi_Sample** Datenbank, und öffnen Sie dann den Ordner "Tabellen".

2. Mit der rechten Maustaste die **nyctaxi_sample** , und wählen Sie **oberste 1000 Zeilen auswählen** , einige Daten zurückzugeben.

## <a name="next-steps"></a>Nächste Schritte

Beispieldaten für die NYC Taxi ist jetzt verfügbar, praxisnahe Lerninhalte.

+ [Erfahren Sie mehr in-Database-Analyse, die mithilfe von R in SQL Server](sqldev-in-database-r-for-sql-developers.md)