---
title: Schritt 2 importieren von Daten in SQL Server mithilfe von PowerShell | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f8b90a18c0cdce9c4c2c73db4b599e488570f018
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461866"
---
# <a name="step-2-import-data-to-sql-server-using-powershell"></a>Schritt 2: Importieren von Daten in SQL Server mithilfe von PowerShell
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil eines Tutorials, [In-Database Python Analytics für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md). 

In diesem Schritt führen Sie eines der heruntergeladenen Skripts zum Erstellen der Datenbankobjekte, die für die exemplarische Vorgehensweise erforderlich. Das Skript auch mehrere gespeicherte Prozeduren erstellt, und lädt die Beispieldaten in eine Tabelle in der Datenbank, die Sie angegeben haben.

## <a name="create-database-objects-and-load-data"></a>Erstellen von Datenbankobjekten und Daten laden

Unter den heruntergeladenen Dateien sollte ein PowerShell-Skript, `RunSQL_SQL_Walkthrough.ps1`. Dieses Skript dient zum Vorbereiten der Umgebung für die exemplarische Vorgehensweise.

Das Skript führt folgende Aktionen aus:

- Die SQL Native Client und der SQL-Befehlszeilenprogramme, installiert werden, sofern nicht bereits installiert. Diese Hilfsprogramme werden für das Massenladen der Daten in die Datenbank mithilfe von **bcp**benötigt.

- Erstellt eine Datenbank und eine Tabelle für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz und masseneinfügungen Daten in die Tabelle.

- Mehrere SQL-Funktionen und gespeicherten Prozeduren erstellt.

Wenn Probleme auftreten, können Sie das Skript als Referenz verwenden, die Schritte manuell ausführen.

### <a name="modify-the-script-to-use-a-trusted-windows-identity"></a>Ändern Sie das Skript aus, um einen vertrauenswürdigen Windows-Identität zu verwenden.

Standardmäßig nimmt das Skript einen SQL Server-Datenbank-Benutzeranmeldung und ein Kennwort. Wenn Sie unter Ihrem Windows-Benutzerkonto Db_owner sind, können Sie Ihre Windows-Identität, zum Erstellen der Objekte. Öffnen Sie zu diesem Zweck `RunSQL_SQL_Walkthrough.ps1` in einem Codeeditor zum Anfügen **`-T`** Bulk insert die BCP-Befehl:

```text
bcp $db_tb in $csvfilepath -t ',' -S $server -f taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U $u -P $p -T
```

### <a name="run-the-script"></a>Führen Sie das Skript

1. Öffnen Sie eine PowerShell-Eingabeaufforderung als Administrator an. Wenn Sie noch nicht in den Ordner, der im vorherigen Schritt erstellt sind, navigieren Sie zu dem Ordner, und führen Sie dann den folgenden Befehl aus:
  
    ```ps
    .\RunSQL_SQL_Walkthrough.ps1
    ```

2. Das Skript fordert die folgenden Informationen:

    - Der Name oder die Adresse von einem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Instanz, in denen Machine Learning-Dienste mit Python installiert wurde.
    - Den Benutzernamen und das Kennwort für ein Konto auf der Instanz. Das Konto, das Sie verwenden, müssen die Möglichkeit zum Erstellen von Datenbanken, Tabellen und gespeicherte Prozeduren erstellen und Massenimport von Daten in Tabellen laden. 
    - Wenn Sie den Benutzernamen und das Kennwort nicht angeben, wird Ihre Windows-Identität für die Anmeldung bei SQL Server verwendet.
    - Der Pfad und der Dateiname der Beispieldatendatei, die Sie zuvor heruntergeladen haben. Beispielsweise `C:\temp\pysql\nyctaxi1pct.csv`

    > [!NOTE]
    > Um die Daten erfolgreich geladen wird, muss die Bibliothek ' xmlrw.dll ' in demselben Ordner wie bcp.exe sein.

3. Das Skript auch ändert die [!INCLUDE[tsql](../../includes/tsql-md.md)] Skripts, die Sie zuvor heruntergeladen haben, und nennen Sie ersetzt die Platzhalter mit dem Datenbanknamen und die Benutzer, die Sie bereitstellen.
  
4. Wenn das Skript abgeschlossen ist, melden Sie sich bei der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz, die mit dem Anmeldenamen, die Sie angegeben haben, um sicherzustellen, dass die Datenbank, Tabellen, Funktionen und gespeicherte Prozeduren erstellt wurden. Die folgende Abbildung zeigt die Objekte im [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].

    ![Suchen von Tabellen in SSMS](media/sqldev-python-browsetables1.png "Tabellen in SSMS anzeigen")

    > [!NOTE]
    > Wenn die Datenbankobjekte bereits vorhanden, können sie erneut erstellt werden.
    > 
    > Wenn eine vorhandene Tabelle mit dem gleichen Namen und Schema gefunden wird, werden die Daten werden angefügt, nicht überschrieben. Achten Sie daher darauf gelöscht oder abgeschnitten vorhandene Tabellen vor dem Ausführen des Skripts.

## <a name="list-of-stored-procedures-and-functions"></a>Liste der gespeicherten Prozeduren und Funktionen

Die folgenden SQL Server-Objekte werden vom Skript erstellt:

|**Name der SQL-Skriptdatei**|**Funktion**|
|------|------|
|create-db-tb-upload-data.sql|Erstellt eine Datenbank und zwei Tabellen:<br /><br />nyctaxi_sample: enthält das Hauptdataset von NYC Taxi Einer Tabelle wird ein gruppierter Columnstore-Index hinzugefügt, um den Speicher und die Abfrageleistung zu verbessern. Das 1 %-Beispiel des Hauptdataset von NYC Taxi wird in diese Tabelle eingefügt.<br /><br />nyc_taxi_models: wird verwendet, um das trainierte Modell für die erweiterte Analyse zu speichern|
|fnCalculateDistance.sql|Erstellt eine Skalarwertfunktion, die die direkte Entfernung zwischen Abhol-und Zielorten berechnet|
|fnEngineerFeatures.sql|Erstellt eine Tabellenwertfunktion, die neue Datenfunktionen für das Modelltraining erstellt|
|TrainingTestingSplit.sql|Die Daten in die Tabelle Nyctaxi_sample in zwei Bereiche aufgeteilt: Nyctaxi_sample_training und Nyctaxi_sample_testing.|
|PredictTipSciKitPy.sql|Erstellt eine gespeicherte Prozedur, die das trainierte Modell aufruft (Scikit-Informationen) zum Erstellen von Vorhersagen mit dem Modell. Die gespeicherte Prozedur akzeptiert eine Abfrage als Eingabeparameter und gibt eine Spalte mit numerischen Werten zurück, die die Bewertungen für die Eingabezeilen enthält.|
|PredictTipRxPy.sql|Erstellt eine gespeicherte Prozedur, die das trainierte Modell (Revoscalepy) zum Erstellen von Vorhersagen mit dem Modell aufruft. Die gespeicherte Prozedur akzeptiert eine Abfrage als Eingabeparameter und gibt eine Spalte mit numerischen Werten zurück, die die Bewertungen für die Eingabezeilen enthält.|
|PredictTipSingleModeSciKitPy.sql|Erstellt eine gespeicherte Prozedur, die das trainierte Modell aufruft (Scikit-Informationen) zum Erstellen von Vorhersagen mit dem Modell. Diese gespeicherte Prozedur akzeptiert als Eingabe eine neue Beobachtung mit einzelnen Funktionswerten, die als Inlineparameter übergeben werden, und gibt einen Wert zurück, der das Ergebnis für die neue Beobachtung vorhersagt.|
|PredictTipSingleModeRxPy.sql|Erstellt eine gespeicherte Prozedur, die das trainierte Modell (Revoscalepy) zum Erstellen von Vorhersagen mit dem Modell aufruft. Diese gespeicherte Prozedur akzeptiert als Eingabe eine neue Beobachtung mit einzelnen Funktionswerten, die als Inlineparameter übergeben werden, und gibt einen Wert zurück, der das Ergebnis für die neue Beobachtung vorhersagt.|

In den letzten Teil dieser exemplarischen Vorgehensweise erstellen Sie diesen zusätzlichen gespeicherten Prozeduren:
    
|**Name der SQL-Skriptdatei**|**Funktion**|
|------|------|
|SerializePlots.sql|Erstellt eine gespeicherte Prozedur zum Durchsuchen von Daten. Diese gespeicherte Prozedur erstellt eine Grafik, die mithilfe von Python und dann die Graph-Objekte zu serialisieren.|
|TrainTipPredictionModelSciKitPy.sql|Erstellt eine gespeicherte Prozedur, die ein Logistisches Regressionsmodell trainiert (Scikit-Informationen). Das Modell sagt für den Wert der tipped-Spalte, und wird mit einem zufällig ausgewählten 60 % der Daten trainiert. Die Ausgabe der gespeicherten Prozedur ist das trainierte Modell, das in der Tabelle nyc_taxi_models gespeichert wird.|
|TrainTipPredictionModelRxPy.sql|Erstellt eine gespeicherte Prozedur, die ein Logistisches Regressionsmodell (Revoscalepy) trainiert. Das Modell sagt für den Wert der tipped-Spalte, und wird mit einem zufällig ausgewählten 60 % der Daten trainiert. Die Ausgabe der gespeicherten Prozedur ist das trainierte Modell, das in der Tabelle nyc_taxi_models gespeichert wird.|

## <a name="next-step"></a>Nächster Schritt

[Schritt 3: Durchsuchen und Visualisieren der Daten](sqldev-py3-explore-and-visualize-the-data.md)

## <a name="previous-step"></a>Vorherigen Schritt

[Schritt 1: Herunterladen der Beispieldaten](demo-data-nyctaxi-in-sql.md)

