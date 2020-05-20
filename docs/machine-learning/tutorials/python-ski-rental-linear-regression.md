---
title: 'Python-Tutorial: Ski-Verleih'
titleSuffix: SQL machine learning
description: Im dieser vierteiligen Tutorialreihe erstellen Sie ein lineares Regressionsmodell in Python, um mit SQL Machine Learning vorherzusagen, wie viele Ski verliehen werden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b34687440763f2c514016989542ae3f2d7c0e6ed
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606914"
---
# <a name="python-tutorial-predict-ski-rental-with-linear-regression-with-sql-machine-learning"></a>Python-Tutorial: Vorhersagen, wie viele Ski verliehen werden, mithilfe linearer Regression mit SQL Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
In diesem vierteiligen Tutorial verwenden Sie Python und die lineare Regression in [SQL Server-Machine Learning Services](../sql-server-machine-learning-services.md) oder in [Big Data-Clustern](../../big-data-cluster/machine-learning-services.md) zur Vorhersage der Verleihzahlen für einen Skiverleih. In diesem Tutorial wird ein [Python-Notebook in Azure Data Studio](../../azure-data-studio/sql-notebooks.md) verwendet.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
In diesem vierteiligen Tutorial verwenden Sie Python und die lineare Regression in [SQL Server-Machine Learning Services](../sql-server-machine-learning-services.md) zur Vorhersage von Verleihzahlen für einen Skiverleih. In diesem Tutorial wird ein [Python-Notebook in Azure Data Studio](../../azure-data-studio/sql-notebooks.md) verwendet.
::: moniker-end

Angenommen, Sie möchten für Ihren eigenen Skiverleih die Verleihzahlen für einen bestimmten Zeitpunkt in der Zukunft vorhersagen. Mit dieser Information können Sie den Bestand, die Mitarbeiter und die Räumlichkeiten besser vorausplanen.

Im ersten Teil der Reihe bereiten Sie die Voraussetzungen vor. Im zweiten und dritten Teil entwickeln Sie Python-Skripts in einem Notebook zur Vorbereitung Ihrer Daten und zum Trainieren eines Machine Learning-Modells. Im vierten Teil führen Sie die Python-Skripts mithilfe von gespeicherten T-SQL-Prozeduren in SQL Server aus.

In diesem Artikel lernen Sie Folgendes:

> [!div class="checklist"]
> * Importieren einer Beispieldatenbank in SQL Server 

In [Teil 2](python-ski-rental-linear-regression-prepare-data.md) lernen Sie, wie Sie die Daten aus einer Datenbank in einen Python-Datenrahmen laden und in Python vorbereiten.

In [Teil 3](python-ski-rental-linear-regression-train-model.md) trainieren Sie ein lineares Regressionsmodell in Python.

In [Teil 4](python-ski-rental-linear-regression-deploy-model.md) haben Sie gelernt, wie Sie das Modell in einer Datenbank speichern und gespeicherte Prozeduren aus den Python-Skripts erstellen, die Sie in Teil 2 und 3 entwickelt haben. Die gespeicherten Prozeduren werden auf dem Server ausgeführt, um Vorhersagen basierend auf neuen Daten treffen zu können.

## <a name="prerequisites"></a>Voraussetzungen

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
* SQL Server-Machine Learning Services: Informationen zur Installation von Machine Learning Services finden Sie im [Windows-Installationshandbuch](../install/sql-machine-learning-services-windows-install.md) oder im [Linux-Installationshandbuch](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fmachine-learning%2Ftoc.json). Sie können auch [Machine Learning Services in Big Data-Clustern unter SQL Server aktivieren](../../big-data-cluster/machine-learning-services.md).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
* SQL Server-Machine Learning Services: Informationen zur Installation von Machine Learning Services finden Sie im [Windows-Installationshandbuch](../install/sql-machine-learning-services-windows-install.md). 
::: moniker-end

* Python-IDE: In diesem Tutorial wird ein Python-Notebook in [Azure Data Studio](../../azure-data-studio/what-is.md) verwendet. Weitere Informationen finden Sie unter [Verwenden von Notebooks in Azure Data Studio](../../azure-data-studio/sql-notebooks.md).

* SQL-Abfragetool: In diesem Tutorial wird davon ausgegangen, dass Sie [Azure Data Studio](../../azure-data-studio/what-is.md) verwenden.

* Weitere Python-Pakete: In den Beispielen in dieser Tutorialreihe werden die folgenden Python-Pakete verwendet, die möglicherweise nicht standardmäßig installiert sind:

  * pandas
  * pyodbc
  * sklearn

  Installieren Sie diese Pakete wie folgt:
  1. Klicken Sie in Azure Data Studio auf **Manage Packages** (Pakete verwalten).
  2. Klicken Sie dann im Bereich **Manage Packages** (Pakete verwalten) auf die Registerkarte **Add new** (Neue hinzufügen).
  3. Geben Sie für jedes der folgenden Pakete den jeweiligen Paketnamen ein, klicken Sie auf **Suchen** und dann auf **Installieren**.

  Alternativ können Sie eine **Eingabeaufforderung** öffnen, zum Installationspfad für die Python-Version wechseln, die Sie in Azure Data Studio verwenden, (z. B. `cd %LocalAppData%\Programs\Python\Python37-32`) und dann für jedes Paket `pip install` ausführen.

## <a name="restore-the-sample-database"></a>Wiederherstellen der Beispieldatenbank

Die in diesem Tutorial verwendete Beispieldatenbank wurde in einer **BAK**-Datenbanksicherungsdatei gespeichert, die Sie herunterladen und verwenden können.

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!NOTE]
> Wenn Sie Machine Learning Services in Big Data-Clustern verwenden, finden Sie Informationen zum Wiederherstellen unter [Wiederherstellen einer Datenbank in der Masterinstanz eines Big Data-Clusters für SQL Server](../../big-data-cluster/data-ingestion-restore-database.md).
::: moniker-end

1. Laden Sie die Datei [TutorialDB.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak) herunter.

1. Befolgen Sie die Anweisungen unter [Wiederherstellen einer Datenbank aus einer Sicherungsdatei](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) in Azure Data Studio, und verwenden Sie hierzu die folgenden Details:

   * Importieren Sie aus der heruntergeladenen Datei **TutorialDB.bak**.
   * Geben Sie der Zieldatenbank den Namen „TutorialDB“.

1. Sie können überprüfen, ob die wiederhergestellte Datenbank vorhanden ist, indem Sie die Tabelle **dbo.rental_data** abfragen:

   ```sql
   USE TutorialDB;
   SELECT * FROM [dbo].[rental_data];
   ```

1. Aktivieren Sie externe Skripts, indem Sie die folgenden SQL-Befehle ausführen:

    ```sql
    sp_configure 'external scripts enabled', 1;
    RECONFIGURE WITH override;
    ```

## <a name="next-steps"></a>Nächste Schritte

Im ersten Teil dieser Tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Installieren der Voraussetzungen
* Importieren einer Beispieldatenbank in SQL Server

Fahren Sie mit Teil 2 dieser Tutorialreihe fort, um die Daten aus der Datenbank „TutorialDB“ vorzubereiten:

> [!div class="nextstepaction"]
> [Python-Tutorial: Vorbereiten von Daten zum Trainieren eines linearen Regressionsmodells](python-ski-rental-linear-regression-prepare-data.md)