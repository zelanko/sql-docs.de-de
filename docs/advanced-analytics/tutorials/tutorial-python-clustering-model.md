---
title: 'Tutorial: Ausführen von Clustering in python'
description: In dieser vierteiligen tutorialreihe führen Sie das Clustering von Kunden in einer SQL-Datenbank mithilfe von Python mit SQL Server Machine Learning Services aus.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/30/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: abcd13b5db24f7ffd44a21b4690f14d97645cdd5
ms.sourcegitcommit: 3de1fb410de2515e5a00a5dbf6dd442d888713ba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2019
ms.locfileid: "70211924"
---
# <a name="tutorial-perform-clustering-in-python-with-sql-server-machine-learning-services"></a>Tutorial: Ausführen von Clustering in Python mit SQL Server Machine Learning Services

In dieser vierteiligen tutorialreihe verwenden Sie Python, um ein K-Means-Clustering-Modell in [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) zum Clustern von Kundendaten zu entwickeln und bereitzustellen.

In Teil 1 dieser Reihe richten Sie die Voraussetzungen für das Tutorial ein und importieren dann ein Beispiel DataSet in eine SQL-Datenbank. Später in dieser Reihe verwenden Sie diese Daten zum trainieren und Bereitstellen eines Clusteringmodells in Python mit SQL Server Machine Learning Services.

In den Teilen 2 und drei dieser Reihe entwickeln Sie einige python-Skripts in einem Azure Data Studio Notebook, um Ihre Daten zu analysieren und vorzubereiten und ein Machine Learning-Modell zu trainieren. In Teil 4 führen Sie dann diese python-Skripts in einer SQL-Datenbank mithilfe gespeicherter Prozeduren aus.

*Clustering* kann als organisieren von Daten in Gruppen erläutert werden, in denen Mitglieder einer Gruppe in irgendeiner Weise ähnlich sind. Stellen Sie sich für diese tutorialreihe vor, dass Sie ein Einzelhandelsgeschäft besitzen. Der **K-Means-** Algorithmus wird verwendet, um das Clustering von Kunden in einem DataSet von Produkt Käufen durchzuführen, und gibt zurück. Durch das Gruppieren von Kunden können Sie Ihre Marketingbemühungen effektiver auf bestimmte Gruppen ausrichten.
K-Means-Clustering ist ein *nicht überwachter Lern* Algorithmus, der auf der Grundlage von Ähnlichkeiten nach Mustern in Daten sucht.

In diesem Artikel lernen Sie Folgendes:

> [!div class="checklist"]
> * Importieren einer Beispieldatenbank in eine SQL Server Instanz

In [Teil 2](tutorial-python-clustering-model-prepare-data.md)erfahren Sie, wie Sie die Daten aus einer SQL-Datenbank für die Durchführung von Clustering vorbereiten.

In [Teil 3](tutorial-python-clustering-model-build.md)erfahren Sie, wie Sie ein K-Means-Clustering-Modell in python erstellen und trainieren.

In [Teil 4](tutorial-python-clustering-model-deploy.md)erfahren Sie, wie Sie eine gespeicherte Prozedur in einer SQL-Datenbank erstellen, die basierend auf neuen Daten Clustering in python durchführen kann.

## <a name="prerequisites"></a>Erforderliche Komponenten

* [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) mit der python-Sprachoption: Befolgen Sie die Installationsanweisungen im [Windows-Installationshandbuch](../install/sql-machine-learning-services-windows-install.md) oder im [Linux-Installationshandbuch](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-machine-learning?toc=%2fsql%2fadvanced-analytics%2ftoc.json&view=sql-server-linux-ver15).

* Python-IDE: in diesem Tutorial wird ein python-Notebook in [Azure Data Studio](../../azure-data-studio/what-is.md)verwendet. Weitere Informationen finden Sie unter [Verwenden von Notebooks in Azure Data Studio](../../azure-data-studio/sql-notebooks.md). Sie können auch Ihre eigene python-IDE verwenden, z. b. ein jupyter-Notebook oder [Visual Studio Code](https://code.visualstudio.com/docs) mit der [python-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-python.python) und der [MSSQL-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql).

* [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) Package: das **revoscalepy** -Paket ist in SQL Server Machine Learning Services enthalten. Informationen zur Verwendung des Pakets auf einem Client Computer finden Sie unter [Einrichten eines Data Science Clients für die Python-Entwicklung](../python/setup-python-client-tools-sql.md) für Optionen zur lokalen Installation dieses Pakets.

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
  pip install matplotlib
  pip install scipy
  pip install sklearn
  ```

## <a name="import-the-sample-database"></a>Importieren der Beispieldatenbank

Das in diesem Tutorial verwendete Beispiel DataSet wurde in einer **BAK** -Daten Bank Sicherungsdatei gespeichert, die Sie herunterladen und verwenden können. Dieses DataSet wird aus dem [TPCX-BB-](http://www.tpc.org/tpcx-bb/default.asp) DataSet abgeleitet, das vom [Transaction Processing Performance Council (TPC)](http://www.tpc.org/default.asp)bereitgestellt wird.

1. Laden Sie die Datei [tpcxbb_1gb. bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/tpcxbb_1gb.bak) in den SQL Server Sicherungsordner herunter. Für die Standarddaten Bank Instanz lautet der Ordner:

   `C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\Backup\`

1. Öffnen Sie Azure Data Studio, stellen Sie eine Verbindung mit Ihrer SQL Server Instanz her, und öffnen Sie ein neues Abfragefenster.

1. Führen Sie die folgenden Befehle aus, um die Datenbank wiederherzustellen.

   ```sql
   USE master;
   GO

   RESTORE DATABASE tpcxbb_1gb
   FROM DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\Backup\tpcxbb_1gb.bak'
   WITH MOVE 'tpcxbb_1gb' TO 'C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\DATA\tpcxbb_1gb.mdf'
      , MOVE 'tpcxbb_1gb_log' TO 'C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\DATA\tpcxbb_1gb.ldf';
   GO
   ```

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Wenn Sie dieses Tutorial nicht fortsetzen möchten, löschen Sie die tpcxbb_1gb-Datenbank aus SQL Server.

## <a name="next-steps"></a>Nächste Schritte

In Teil 1 dieser tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Importieren einer Beispieldatenbank in eine SQL Server Instanz

Um die Daten für das Machine Learning-Modell vorzubereiten, führen Sie den Teil der beiden folgenden tutorialreihe aus:

> [!div class="nextstepaction"]
> [Tutorial: Vorbereiten von Daten für die Durchführung von Clustering in Python mit SQL Server Machine Learning Services](tutorial-python-clustering-model-prepare-data.md)
