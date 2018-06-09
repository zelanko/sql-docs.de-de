---
title: Lektion 2 Vorbereiten R-Lernprogramm Umgebung mithilfe von PowerShell (SQL Server-Machine Learning) | Microsoft Docs
description: Lernprogramm zur Einbettung von R in SQL Server gespeicherte Prozeduren und Funktionen des T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 1280d7c82d48c8ed596271cd7a73fa13ec1664c7
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2018
ms.locfileid: "35249743"
---
# <a name="lesson-2-set-up-the-tutorial-environment-using-powershell"></a>Lektion 2: Einrichten der Tutorial Umgebung mithilfe von PowerShell
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil eines Lernprogramms für SQL-Entwicklern zum Verwenden von R in SQL Server.

In diesem Schritt führen Sie ein PowerShell-Skript zum Erstellen von Datenbankobjekten, die für die exemplarische Vorgehensweise erforderlich. Das Skript erstellt und lädt eine Datenbank mit Beispieldaten, die im vorherigen Schritt abgerufen haben. Außerdem erstellt es Funktionen und gespeicherten Prozeduren, die während des gesamten Lernprogramms verwendet.

## <a name="create-and-load-database-objects"></a>Erstellen und Laden von Datenbankobjekten

Zwischen den heruntergeladenen Dateien sehen Sie ein PowerShell-Skript (`RunSQL_SQL_Walkthrough.ps1`), die die Umgebung für die exemplarische Vorgehensweise vorbereiten. Die vom Skript ausgeführten Aktionen beinhalten:

- Installieren Sie SQL Native Client und SQL-Befehlszeilen-Hilfsprogramme, sofern nicht bereits installiert. Diese Hilfsprogramme werden für das Massenladen der Daten in die Datenbank mithilfe von **bcp**benötigt.

- Erstellen Sie eine Datenbank und Tabellen für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz und masseneinfügung-Daten stammen aus einer CSV-Datei.

- Erstellen Sie mehrere SQL-Funktionen und gespeicherten Prozeduren.

### <a name="modify-the-script-to-use-a-trusted-windows-identity"></a>Ändern Sie das Skript aus, um einen vertrauenswürdigen Windows-Identität verwenden

Standardmäßig nimmt das Skript an eine SQL Server-Datenbank-Benutzername und Kennwort. Wenn Sie unter Ihrem Windows-Benutzerkonto Db_owner sind, können Sie Ihre Windows-Identität, zum Erstellen der Objekte. Öffnen Sie hierzu `RunSQL_SQL_Walkthrough.ps1` in einem Code-Editor, und fügt **`-T`** die bcp Bulk insert-Befehl (Line 238):

```text
bcp $db_tb in $csvfilepath -t ',' -S $server -f taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U $u -P $p -T
```

### <a name="run-the-script-to-create-objects"></a>Ausführen des Skripts zum Erstellen von Objekten

Öffnen Sie ein PowerShell-Eingabeaufforderungsfenster als Administrator, und führen Sie den folgenden Befehl aus.
  
```ps
.\RunSQL_SQL_Walkthrough.ps1
```
Aufgefordert werden, geben Sie die folgende Informationen:

- Server-Instanz, auf [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] installiert wurde. Dies kann auf einer Standardinstanz so einfach wie der Computername sein.

- Datenbankname. In diesem Lernprogramm wird davon ausgegangen Skripts `TaxiNYC_Sample`.

- Benutzername und Kennwort. Geben Sie eine SQL Server-Datenbank-Anmeldung für diese Werte ein. Auch wenn Sie das Skript zum Akzeptieren von einer vertrauenswürdigen Windows-Identität geändert haben, drücken Sie EINGABETASTE, um diese Werte leer lassen. Ihre Windows-Identität wird für die Verbindung verwendet.

- Vollständig qualifizierte Dateiname für die Beispieldaten in der vorherigen Lektion heruntergeladen. Beispiel: `C:\tempRSQL\nyctaxi1pct.csv`

Nachdem Sie diese Werte angeben, wird das Skript sofort ausgeführt. Während der skriptausführung, alle Platzhalternamen in der [!INCLUDE[tsql](../../includes/tsql-md.md)] Skripts werden aktualisiert, um die Eingaben verwenden Sie bereitstellen.

## <a name="review-database-objects"></a>Überprüfen Sie die Datenbankobjekte
   
Bei der Ausführung des Skripts abgeschlossen ist, bestätigen Sie die Datenbankobjekte vorhanden, auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Zielinstanz [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Sie sollten die Datenbank, Tabellen, Funktionen und gespeicherten Prozeduren finden Sie unter.
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

> [!NOTE]
> Wenn das Datenbankprojekt schon vorhanden ist, dann kann es nicht noch einmal erstellt werden.
>   
> Wenn die Tabelle bereits vorhanden ist, werden die Daten angefügt, nicht überschrieben. Achten Sie daher darauf, vorhandene Objekte zu löschen, bevor Sie das Skript ausführen.

## <a name="objects-used-in-this-tutorial"></a>In diesem Lernprogramm verwendeten Objekte

In der folgenden Tabelle werden die in dieser Lektion erstellten Objekte zusammengefasst. Obwohl Sie nur ein PowerShell-Skript ausführen (`RunSQL_SQL_Walkthrough.ps1`), dieses Skript ruft die anderen SQL-Skripts wiederum auf die Objekte in der Datenbank zu erstellen. Skripts verwendet werden, um jedes Objekt zu erstellen, die in der Beschreibung erwähnt werden.

|**Objektname**|**Objekttyp**|**Beschreibung**|
|----------|------------------------|---------------|
|**TaxiNYC_Sample** | Datenbank |Durch die Create-Db-Tb-Upload-data.sql Skripts erstellt. Erstellt eine Datenbank und zwei Tabellen:<br /><br />dbo.nyctaxi_sample-Tabelle: das hauptdataset NYC Taxi enthält. Einer Tabelle wird ein gruppierter Columnstore-Index hinzugefügt, um den Speicher und die Abfrageleistung zu verbessern. Die % 1-Stichprobe des Datasets NYC Taxi wird in dieser Tabelle eingefügt.<br /><br />dbo.nyc_taxi_models-Tabelle: verwendet, um das Modell trainierten Erweiterte Analysen beizubehalten.|
|**fnCalculateDistance** |Skalarwertfunktion | Durch das Skript fnCalculateDistance.sql erstellt. Berechnet den direkten Abstand zwischen Standorten Pickup und Dropoff an. Diese Funktion dient [Data-Funktionen erstellen](../tutorials/sqldev-create-data-features-using-t-sql.md), [trainieren, und speichern Sie ein Modell](sqldev-train-and-save-a-model-using-t-sql.md) und [Operationalisieren von R-Modell](../tutorials/sqldev-operationalize-the-model.md).|
|**fnEngineerFeatures** |Tabellenwertfunktion | Durch das Skript fnEngineerFeatures.sql erstellt. Erstellt neue Features für das Modelltraining an. Diese Funktion dient [Data-Funktionen erstellen](../tutorials/sqldev-create-data-features-using-t-sql.md) und [Operationalisieren von R-Modell](../tutorials/sqldev-operationalize-the-model.md).|
|**PlotHistogram** |) | Durch das Skript PlotHistogram.sql erstellt. Ruft eine R-Funktion, um das Histogramm einer Variablen zu zeichnen, und gibt dann die Zeichnung als binäres Objekt zurück. Diese gespeicherte Prozedur wird verwendet, [durchsuchen und Visualisieren von Daten](../tutorials/sqldev-explore-and-visualize-the-data.md).|
|**PlotInOutputFiles** |)| Durch das Skript PlotInOutputFiles.sql erstellt. Erstellt eine Grafik, die mithilfe einer R-Funktion, und klicken Sie dann die Ausgabe als lokale PDF-Datei gespeichert. Diese gespeicherte Prozedur wird verwendet, [durchsuchen und Visualisieren von Daten](../tutorials/sqldev-explore-and-visualize-the-data.md).|
|**PersistModel** |) | Durch das Skript PersistModel.sql erstellt. Akzeptiert ein Modell, das in einen Varbinary-Datentyp serialisiert wurde, und schreibt sie in der angegebenen Tabelle an. |
|**PredictTip**  |) |Durch das Skript PredictTip.sql erstellt. Ruft das trainierte Modell zum Vorhersagen mit dem Modell zu erstellen. Die gespeicherte Prozedur akzeptiert eine Abfrage als Eingabeparameter und gibt eine Spalte mit numerischen Werten zurück, die die Bewertungen für die Eingabezeilen enthält. Diese gespeicherte Prozedur wird verwendet, [Operationalisieren von R-Modell](../tutorials/sqldev-operationalize-the-model.md).|
|**PredictTipSingleMode**  |)| Durch das Skript PredictTipSingleMode.sql erstellt. Ruft das trainierte Modell zum Vorhersagen mit dem Modell zu erstellen. Diese gespeicherte Prozedur akzeptiert als Eingabe eine neue Beobachtung mit einzelnen Funktionswerten, die als Inlineparameter übergeben werden, und gibt einen Wert zurück, der das Ergebnis für die neue Beobachtung vorhersagt. Diese gespeicherte Prozedur wird verwendet, [Operationalisieren von R-Modell](../tutorials/sqldev-operationalize-the-model.md).|
|**TrainTipPredictionModel**  |)|Durch das Skript TrainTipPredictionModel.sql erstellt. Trainiert ein Logistisches Regressionsmodell durch Aufrufen eines R-Pakets an. Das Modell sagt den Wert der tipped-Spalte voraus und wird mithilfe von zufällig ausgewählten 70 % der Daten trainiert. Die Ausgabe der gespeicherten Prozedur ist das trainierte Modell, das in der Tabelle nyc_taxi_models gespeichert wird. Diese gespeicherte Prozedur wird verwendet, [trainieren, und speichern Sie ein Modell](sqldev-train-and-save-a-model-using-t-sql.md).|

## <a name="next-lesson"></a>Nächste Lektion

[Lektion 3: Durchsuchen und Visualisieren von Daten](../tutorials/sqldev-explore-and-visualize-the-data.md)

## <a name="previous-lesson"></a>Vorherige Lektion

[Lektion 1: Herunterladen der Beispieldaten](../tutorials/sqldev-download-the-sample-data.md)
