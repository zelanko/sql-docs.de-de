---
title: 'Python-Tutorial: Ski-Verleih'
description: In diesem Tutorial verwenden Sie Python und die lineare Regression in SQL Server-Machine Learning Services zur Vorhersage von Verleihzahlen für einen Skiverleih.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 927816988be8882d4149115f6d4aee38dd3a8f3f
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727038"
---
# <a name="python-tutorial-predict-ski-rental-with-linear-regression-in-sql-server-machine-learning-services"></a>Python-Tutorial: Vorhersagen von Verleihzahlen für einen Skiverleih unter Verwendung der linearen Regression in SQL Server-Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem vierteiligen Tutorial verwenden Sie Python und die lineare Regression in [SQL Server-Machine Learning Services](../what-is-sql-server-machine-learning.md) zur Vorhersage von Verleihzahlen für einen Skiverleih. Im Tutorial wird ein [Python-Notebook in Azure Data Studio](../../azure-data-studio/sql-notebooks.md) verwendet. Sie können jedoch auch Ihre eigene integrierte Entwicklungsumgebung (IDE) für Python verwenden.

Angenommen, Sie möchten für Ihren eigenen Skiverleih die Verleihzahlen für einen bestimmten Zeitpunkt in der Zukunft vorhersagen. Mit dieser Information können Sie den Bestand, die Mitarbeiter und die Räumlichkeiten besser vorausplanen.

Im ersten Teil der Reihe bereiten Sie die Voraussetzungen vor. Im zweiten und dritten Teil entwickeln Sie in Jupyter Notebook Python-Skripts zur Vorbereitung Ihrer Daten und zum Trainieren eines Machine Learning-Modells. Im vierten Teil führen Sie die Python-Skripts mithilfe von gespeicherten T-SQL-Prozeduren in SQL Server aus.

In diesem Artikel lernen Sie Folgendes:

> [!div class="checklist"]
> * Importieren einer Beispieldatenbank in SQL Server 

In [Teil 2](python-ski-rental-linear-regression-prepare-data.md) erfahren Sie, wie Sie die Daten aus SQL Server in einen Python-Datenrahmen laden und in Python vorbereiten.

In [Teil 3](python-ski-rental-linear-regression-train-model.md) trainieren Sie ein lineares Regressionsmodell in Python.

In [Teil 4](python-ski-rental-linear-regression-deploy-model.md) wird beschrieben, wie Sie das Modell in SQL Server speichern und gespeicherte Prozeduren aus den Python-Skripts erstellen, die Sie in Teil 2 und 3 entwickelt haben. Die gespeicherten Prozeduren werden in SQL Server ausgeführt, um Vorhersagen basierend auf neuen Daten treffen zu können.

## <a name="prerequisites"></a>Voraussetzungen

* SQL Server-Machine Learning Services: Informationen zur Installation von Machine Learning Services finden Sie im [Windows-Installationshandbuch](../install/sql-machine-learning-services-windows-install.md) oder im [Linux-Installationshandbuch](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fadvanced-analytics%2Ftoc.json).

* Python-IDE: In diesem Tutorial wird ein Python-Notebook in [Azure Data Studio](../../azure-data-studio/what-is.md) verwendet. Weitere Informationen finden Sie unter [Verwenden von Notebooks in Azure Data Studio](../../azure-data-studio/sql-notebooks.md). 

    Sie können auch Ihre eigene Python-IDE verwenden, wie z. B. Jupyter Notebook oder [Visual Studio Code](https://code.visualstudio.com/docs) mit der [Python-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-python.python) und der [MSSQL-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql). 

* [revoscalepy](../python/ref-py-revoscalepy.md)-Paket: Das **revoscalepy**-Paket ist in SQL Server-Machine Learning Services enthalten. Informationen zur Verwendung des Pakets auf einem Clientcomputer finden Sie unter [Einrichten eines Data Science-Clients für die Python-Entwicklung](../python/setup-python-client-tools-sql.md) mit Optionen für die lokale Installation dieses Pakets.

    Wenn Sie ein Python-Notebook in Azure Data Studio verwenden, führen Sie zusätzlich die folgenden Schritte aus, um **revoscalepy** verwenden zu können:

    1. Öffnen Sie Azure Data Studio.
    1. Klicken Sie im Menü **Datei** auf **Voreinstellungen** und anschließend auf **Einstellungen**.
    1. Erweitern Sie die Option **Erweiterungen**, und klicken Sie auf **Notebook-Konfiguration**.
    1. Geben Sie unter **Python-Pfad** den Pfad ein, in dem Sie die Bibliotheken installiert haben (z. B. `C:\path-to-python-for-mls`).
    1. Vergewissern Sie sich, dass das Kontrollkästchen bei **Vorhandene Python-IDE verwenden** aktiviert ist.
    1. Starten Sie Azure Data Studio neu.

    Wenn Sie eine andere Python-IDE verwenden, führen Sie die entsprechenden Schritte für Ihre IDE aus.

* SQL-Abfragetool: In diesem Tutorial wird davon ausgegangen, dass Sie [Azure Data Studio](../../azure-data-studio/what-is.md) verwenden. Sie können stattdessen auch [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) (SSMS) verwenden.

* Weitere Python-Pakete: In den Beispielen dieser Tutorialreihe werden möglicherweise Python-Pakete verwendet, die Sie nicht installiert haben. Installieren Sie diese Pakete ggf. mit den folgenden **PIP**-Befehlen:

    ```console
    pip install pandas
    pip install sklearn
    pip install pickle
    ```

## <a name="restore-the-sample-database"></a>Wiederherstellen der Beispieldatenbank

Das in diesem Tutorial verwendete Beispieldataset wurde in einer **BAK**-Datenbanksicherungsdatei gespeichert, die Sie herunterladen und verwenden können.

1. Laden Sie die Datei [TutorialDB.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak) herunter.

1. Befolgen Sie die Anweisungen unter [Wiederherstellen einer Datenbank aus einer Sicherungsdatei](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) in Azure Data Studio, und verwenden Sie hierzu die folgenden Details:

   * Importieren Sie aus der heruntergeladenen Datei **TutorialDB.bak**.
   * Geben Sie der Zieldatenbank den Namen „TutorialDB“.

1. Nach dem Wiederherstellen der Datenbank können Sie überprüfen, ob das Dataset vorhanden ist, indem Sie die Tabelle **dbo.rental_data** abfragen:

    ```sql
    USE TutorialDB;
    SELECT * FROM [dbo].[rental_data];
    ```

## <a name="next-steps"></a>Nächste Schritte

Im ersten Teil dieser Tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Installieren der Voraussetzungen
* Importieren einer Beispieldatenbank in SQL Server

Fahren Sie mit Teil 2 dieser Tutorialreihe fort, um die Daten aus der Datenbank „TutorialDB“ vorzubereiten:

> [!div class="nextstepaction"]
> [Python-Tutorial: Vorbereiten von Daten zum Trainieren eines linearen Regressionsmodells](python-ski-rental-linear-regression-prepare-data.md)