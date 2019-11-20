---
title: 'Python-Tutorial: Kategorisieren von Benutzern'
description: In dieser vierteiligen Tutorialreihe führen Sie mit dem K-Means-Algorithmus in einer SQL-Datenbank mithilfe von Python mit SQL Server Machine Learning Services ein Clustering von Kunden durch.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/30/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 245a1566bfbbf19821323d0b474669eaba1d2e6e
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727076"
---
# <a name="tutorial-categorizing-customers-using-k-means-clustering-with-sql-server-machine-learning-services"></a>Lernprogramm: Kategorisieren von Kunden mithilfe von K-Means-Clustering mit SQL Server Machine Learning Services

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

In [Teil 4](python-clustering-model-deploy.md) erfahren Sie, wie Sie eine gespeicherte Prozedur in einer SQL-Datenbank-Instanz erstellen, die in Python Clustering auf der Grundlage neuer Daten durchführen kann.

## <a name="prerequisites"></a>Voraussetzungen

* [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) mit der Python-Programmiersprachoption: Befolgen Sie die Installationsanweisungen im [Windows-Installationshandbuch](../install/sql-machine-learning-services-windows-install.md) oder im [Linux-Installationshandbuch](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-machine-learning?toc=%2fsql%2fadvanced-analytics%2ftoc.json&view=sql-server-linux-ver15).

* Python-IDE: In diesem Tutorial wird ein Python-Notebook in [Azure Data Studio](../../azure-data-studio/what-is.md) verwendet. Weitere Informationen finden Sie unter [Verwenden von Notebooks in Azure Data Studio](../../azure-data-studio/sql-notebooks.md). Sie können auch Ihre eigene Python-IDE verwenden, wie z. B. Jupyter Notebook oder [Visual Studio Code](https://code.visualstudio.com/docs) mit der [Python-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-python.python) und der [MSSQL-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql).

* [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)-Paket: Das **revoscalepy**-Paket ist in SQL Server-Machine Learning Services enthalten. Informationen zur Verwendung des Pakets auf einem Clientcomputer finden Sie unter [Einrichten eines Data Science-Clients für die Python-Entwicklung](../python/setup-python-client-tools-sql.md) mit Optionen für die lokale Installation dieses Pakets.

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
  pip install matplotlib
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

Wenn Sie mit diesem Tutorial nicht fortfahren möchten, löschen Sie die tpcxbb_1gb-Datenbank aus SQL Server.

## <a name="next-steps"></a>Nächste Schritte

Im ersten Teil dieser Tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Wiederherstellen einer Beispieldatenbank in einer SQL Server-Instanz

Fahren Sie mit dem zweiten Teil dieser Tutorialreihe fort, um die Daten für das Machine Learning-Modell vorzubereiten:

> [!div class="nextstepaction"]
> [Tutorial: Vorbereiten von Daten zum Clustern von Kunden in Python mit SQL Server Machine Learning Services](python-clustering-model-prepare-data.md)
