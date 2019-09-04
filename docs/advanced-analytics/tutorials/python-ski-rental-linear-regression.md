---
title: 'Python-Tutorial: Skiverleih (lineare Regression)'
description: In diesem Tutorial verwenden Sie die python-und lineare Regression in SQL Server Machine Learning Services, um die Anzahl der Ski-Vermietungen vorherzusagen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 718487ba55b2b8db8f16b59df5785cf78ff501f1
ms.sourcegitcommit: ecb19d0be87c38a283014dbc330adc2f1819a697
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2019
ms.locfileid: "70242508"
---
# <a name="python-tutorial-predict-ski-rental-with-linear-regression-in-sql-server-machine-learning-services"></a>Python-Tutorial: Vorhersagen eines Skirental mit linearer Regression in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In dieser vierteiligen tutorialreihe verwenden Sie python und lineare Regression in [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) , um die Anzahl der Ski-Vermietungen vorherzusagen. In diesem Tutorial wird ein [python-Notebook in Azure Data Studio](../../azure-data-studio/sql-notebooks.md)verwendet, Sie können jedoch auch Ihre eigene IDE-IDE (Integrated Development Environment) verwenden.

Stellen Sie sich vor, Sie sind ein Ski-Verleih-Geschäft und möchten Vorhersagen, wie viele Mietzeiten Sie an einem zukünftigen Datum haben werden. Diese Informationen helfen Ihnen, ihre Bestände, Mitarbeiter und Einrichtungen bereit zu machen.

Im ersten Teil dieser Reihe werden die Voraussetzungen erfüllt. In den zwei und drei Teilen werden Sie einige python-Skripts in einem jupyter-Notebook entwickeln, um Ihre Daten vorzubereiten und ein Machine Learning-Modell zu trainieren. Anschließend führen Sie die python-Skripts in Teil 3 in SQL Server mithilfe gespeicherter T-SQL-Prozeduren aus.

In diesem Artikel lernen Sie Folgendes:

> [!div class="checklist"]
> * Importieren einer Beispieldatenbank in SQL Server 

In [Teil 2](python-ski-rental-linear-regression-prepare-data.md)erfahren Sie, wie die Daten aus SQL Server in einen python-Datenrahmen geladen und die Daten in python vorbereitet werden.

In [Teil 3](python-ski-rental-linear-regression-train-model.md)erfahren Sie, wie Sie ein lineares Regressionsmodell in python trainieren.

In [Teil 4](python-ski-rental-linear-regression-deploy-model.md)erfahren Sie, wie Sie das Modell in SQL Server speichern und dann gespeicherte Prozeduren aus den python-Skripts erstellen, die Sie in den Teilen 2 und 3 entwickelt haben. Die gespeicherten Prozeduren werden in SQL Server ausgeführt, um Vorhersagen basierend auf neuen Daten zu treffen.

## <a name="prerequisites"></a>Erforderliche Komponenten

* SQL Server Machine Learning Services: Informationen zum Installieren Machine Learning Services finden Sie im [Windows-Installationshandbuch](../install/sql-machine-learning-services-windows-install.md) oder im [Linux-Installationshandbuch](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fadvanced-analytics%2Ftoc.json).

* Python-IDE: in diesem Tutorial wird ein python-Notebook in [Azure Data Studio](../../azure-data-studio/what-is.md)verwendet. Weitere Informationen finden Sie unter [Verwenden von Notebooks in Azure Data Studio](../../azure-data-studio/sql-notebooks.md). 

    Sie können auch Ihre eigene python-IDE verwenden, z. b. ein jupyter-Notebook oder [Visual Studio Code](https://code.visualstudio.com/docs) mit der [python-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-python.python) und der [MSSQL-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql). 

* [revoscalepy](../python/ref-py-revoscalepy.md) Package: das **revoscalepy** -Paket ist in SQL Server Machine Learning Services enthalten. Informationen zur Verwendung des Pakets auf einem Client Computer finden Sie unter [Einrichten eines Data Science Clients für die Python-Entwicklung](../python/setup-python-client-tools-sql.md) für Optionen zur lokalen Installation dieses Pakets.

    Wenn Sie ein python-Notebook in Azure Data Studio verwenden, führen Sie die folgenden zusätzlichen Schritte aus, um **revoscalepy**zu verwenden:

    1. Öffnen Sie Azure Data Studio
    1. Wählen Sie im Menü **Datei** die Option **Einstellungen** und dann **Einstellungen** aus.
    1. **Erweiterungen** erweitern und **Notebook-Konfiguration** auswählen
    1. Geben Sie unter **python-Pfad**den Pfad ein, in dem Sie die Bibliotheken installiert `C:\path-to-python-for-mls`haben (z. b.).
    1. Vergewissern Sie sich, dass **vorhandene python verwenden** aktiviert ist.
    1. Neustart Azure Data Studio

    Wenn Sie eine andere python-IDE verwenden, führen Sie ähnliche Schritte für die IDE aus.

* SQL-Abfrage Tool: in diesem Tutorial wird davon ausgegangen, dass Sie [Azure Data Studio](../../azure-data-studio/what-is.md)verwenden. Sie können auch [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) (SSMS) verwenden.

* Zusätzliche Python-Pakete: in den Beispielen in dieser tutorialreihe werden Python-Pakete verwendet, die Sie möglicherweise nicht installiert haben. Verwenden Sie die folgenden **PIP** -Befehle, um diese Pakete bei Bedarf zu installieren.

    ```console
    pip install pandas
    pip install sklearn
    pip install pickle
    ```

## <a name="restore-the-sample-database"></a>Wiederherstellen der Beispieldatenbank

Das in diesem Tutorial verwendete Beispiel DataSet wurde in einer **BAK** -Daten Bank Sicherungsdatei gespeichert, die Sie herunterladen und verwenden können.

1. Laden Sie die Datei " [tutorialdb. bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak)" herunter.

1. Befolgen Sie die Anweisungen unter [Wiederherstellen einer Datenbank aus einer Sicherungsdatei](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) in Azure Data Studio mit den folgenden Details:

   * Importieren aus der heruntergeladenen Datei " **tutorialdb. bak** "
   * Benennen Sie die Zieldatenbank "tutorialdb".

1. Sie können überprüfen, ob das DataSet vorhanden ist, nachdem Sie die Datenbank wieder hergestellt haben, indem Sie die Tabelle **dbo. rental_data** Abfragen:

    ```sql
    USE TutorialDB;
    SELECT * FROM [dbo].[rental_data];
    ```

## <a name="next-steps"></a>Nächste Schritte

In Teil 1 dieser tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Erforderliche Komponenten installiert
* Importieren einer Beispieldatenbank in eine SQL Server

Um die Daten aus der tutorialdb-Datenbank vorzubereiten, führen Sie den Teil der beiden folgenden tutorialreihe aus:

> [!div class="nextstepaction"]
> [Python-Tutorial: Vorbereiten von Daten zum Trainieren eines linearen Regressionsmodells](python-ski-rental-linear-regression-prepare-data.md)