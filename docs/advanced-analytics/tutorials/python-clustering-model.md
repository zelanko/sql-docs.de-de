---
title: 'Python-Tutorial: Kategorisieren von Benutzern'
description: In dieser vierteiligen Tutorialreihe führen Sie mit dem K-Means-Algorithmus in einer SQL-Datenbank mithilfe von Python mit SQL Server Machine Learning Services ein Clustering von Kunden durch.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 12/17/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f5d1254c6b5c478c7bcad63da0902f21f4db70a9
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75306580"
---
# <a name="tutorial-categorizing-customers-using-k-means-clustering-with-sql-server-machine-learning-services"></a>Tutorial: Kategorisieren von Kunden mithilfe von K-Means-Clustering mit SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In dieser vierteiligen Tutorialreihe verwenden Sie Python zum Entwickeln und Bereitstellen eines K-Means-Clustermodells in [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) zum Clustern von Kundendaten.

Im ersten Teil dieser Reihe richten Sie die Voraussetzungen für das Tutorial ein und stellen dann ein Beispieldataset für eine SQL-Datenbank wieder her. Diese Daten verwenden Sie in einem späteren Teil dieser Reihe zum Trainieren und Bereitstellen eines Clustermodells in Python mit SQL Server Machine Learning Services.

Im zweiten und dritten Teil der Reihe entwickeln Sie Python-Skripte in einem Azure Data Studio-Notebook zum Analysieren und Vorbereiten der Daten und Trainieren eines Machine Learning-Modells. Im vierten Teil führen Sie diese Python-Skripte in einer SQL-Datenbank mithilfe gespeicherter Prozeduren aus.

*Clustering* kann als Organisieren von Daten in Gruppen beschrieben werden, in denen Mitglieder einer Gruppe in irgendeiner Weise ähnlich sind. Stellen Sie sich für diese Tutorialreihe vor, dass Sie ein Einzelhandelsgeschäft besitzen. Sie verwenden den **K-Means**-Algorithmus zum Durchführen des Clusterings von Kunden in einem Dataset von Produktkäufen und -rückgaben. Durch das Clustern von Kunden können Sie Ihre Marketingmaßnahmen effektiver auf bestimmte Gruppen ausrichten.
K-Means-Clustering ist ein *nicht überwachter Lernalgorithmus*, der auf der Grundlage von Ähnlichkeiten nach Mustern in Daten sucht.

In diesem Artikel lernen Sie Folgendes:

> [!div class="checklist"]
> * Wiederherstellen einer Beispieldatenbank in einer SQL Server-Instanz

In [Teil 2](python-clustering-model-prepare-data.md) lernen Sie, wie Sie die Daten aus einer SQL-Datenbank für das Clustering vorbereiten.

In [Teil 3](python-clustering-model-build.md) erfahren Sie, wie Sie ein K-Means-Clustermodell in Python erstellen und trainieren.

In [Teil 4](python-clustering-model-deploy.md) erfahren Sie, wie Sie eine gespeicherte Prozedur in einer SQL-Datenbank erstellen, die Clustering auf der Grundlage neuer Daten in Python durchführen kann.

## <a name="prerequisites"></a>Voraussetzungen

* [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) mit der Python-Programmiersprachoption: Befolgen Sie die Installationsanweisungen im [Windows-Installationshandbuch](../install/sql-machine-learning-services-windows-install.md) oder im [Linux-Installationshandbuch](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-machine-learning?toc=%2fsql%2fadvanced-analytics%2ftoc.json&view=sql-server-linux-ver15).

* [Azure Data Studio](../../azure-data-studio/what-is.md) Für Python und SQL verwenden Sie ein Notebook in Azure Data Studio. Weitere Informationen zu Notebooks finden Sie unter [Verwenden von Notebooks in Azure Data Studio](../../azure-data-studio/sql-notebooks.md).

  * Python: Sie können auch Ihre eigene Python-IDE verwenden, wie z. B. Jupyter Notebook oder [Visual Studio Code](https://code.visualstudio.com/docs) mit der [Python-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-python.python) und der [MSSQL-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql).
  * SQL: Sie können auch [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) (SSMS) verwenden.

* Weitere Python-Pakete: In den Beispielen dieser Tutorialreihe werden möglicherweise Python-Pakete verwendet, die Sie nicht installiert haben.

  Öffnen Sie eine **Eingabeaufforderung**, und ändern Sie den Installationspfad gemäß der Python-Version, die Sie in Azure Data Studio verwenden. Beispiel: `cd %LocalAppData%\Programs\Python\Python37-32`. Führen Sie anschließend die folgenden Befehle aus, um die Pakete zu installieren, die noch nicht installiert sind.

  ```console
  pip install matplotlib
  pip install pandas
  pip install pyodbc
  pip install scipy
  pip install sklearn
  ```

## <a name="restore-the-sample-database"></a>Wiederherstellen der Beispieldatenbank

Das in diesem Tutorial verwendete Beispieldataset wurde in einer **BAK**-Datenbanksicherungsdatei gespeichert, die Sie herunterladen und verwenden können. Dieses Dataset wird aus dem [tpcx-bb](http://www.tpc.org/tpcx-bb/default.asp)-Dataset abgeleitet, das von [TPC (Transaction Processing Performance Council)](http://www.tpc.org/default.asp) bereitgestellt wird.

1. Laden Sie die Datei [tpcxbb_1gb.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/tpcxbb_1gb.bak) herunter.

1. Befolgen Sie die Anweisungen unter [Wiederherstellen einer Datenbank aus einer Sicherungsdatei](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) in Azure Data Studio, und verwenden Sie hierzu die folgenden Details:

   * Importieren Sie aus der heruntergeladenen Datei **tpcxbb_1gb.bak**.
   * Geben Sie der Zieldatenbank den Namen „tpcxbb_1gb“.

1. Nach dem Wiederherstellen der Datenbank können Sie überprüfen, ob das Dataset vorhanden ist, indem Sie die Tabelle **dbo.customer** abfragen:

    ```sql
    USE tpcxbb_1gb;
    SELECT * FROM [dbo].[customer];
    ```

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Wenn Sie nicht mit diesem Tutorial fortfahren möchten, löschen Sie die Datenbank „tpcxbb_1gb“ aus SQL Server.

## <a name="next-steps"></a>Nächste Schritte

Im ersten Teil dieser Tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Wiederherstellen einer Beispieldatenbank in einer SQL Server-Instanz

Fahren Sie mit dem zweiten Teil dieser Tutorialreihe fort, um die Daten für das Machine Learning-Modell vorzubereiten:

> [!div class="nextstepaction"]
> [Tutorial: Vorbereiten von Daten zum Clustern von Kunden in Python mit SQL Server Machine Learning Services](python-clustering-model-prepare-data.md)
