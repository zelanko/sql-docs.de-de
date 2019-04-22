---
title: Ausführen eines Beispiel-Notebooks | Microsoft-Dokumentation
titleSuffix: SQL Server big data clusters
description: In diesem Tutorial wird gezeigt, wie Sie die einer Ausführung einer Beispiel-Spark-Notebook auf eine SQL Server-2019 big Data-Cluster (Vorschau) laden können.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 274f33590282f36454e6cdb6041dac3484b9bcc4
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860181"
---
# <a name="tutorial-run-a-sample-notebook-on-a-sql-server-big-data-cluster"></a>Tutorial: Führen Sie ein Beispiel-Notebook auf eine SQL Server-big Data-cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Tutorial wird veranschaulicht, wie Laden und Ausführen eines Notebooks in Azure Data Studio auf einem SQL Server-2019 big Data-Cluster (Vorschau). Dadurch können Datenanalysten und datentechniker, Python, R oder Scala-Code für den Cluster ausführen.

> [!TIP]
> Falls gewünscht, können Sie herunterladen und Ausführen eines Skripts für die Befehle in diesem Tutorial. Anweisungen finden Sie in der [Spark Beispiele](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark) auf GitHub.

## <a id="prereqs"></a> Erforderliche Komponenten

- [Big Data-tools](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server-2019-Erweiterung**
- [Laden Sie Beispieldaten in Ihre big Data-cluster](tutorial-load-sample-data.md)

## <a name="download-the-sample-notebook-file"></a>Laden Sie die Beispiel-Notebook-Datei

Gehen Sie folgendermaßen vor, um die Beispiel-Notebook-Datei laden **Spark-sql.ipynb** in Azure Data Studio.

1. Öffnen Sie ein Bash-Eingabeaufforderung (Linux) oder Windows PowerShell.

1. Navigieren Sie zu einem Verzeichnis, in dem Sie die Beispiel-Notebook-Datei zum herunterladen möchten.

1. Führen Sie den folgenden **curl** Befehl aus, um die Notebook-Datei von GitHub herunterzuladen:

   ```bash
   curl 'https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/spark-sql.ipynb' -o spark-sql.ipynb
   ```

## <a name="open-the-notebook"></a>Öffnen Sie das notebook

Die folgenden Schritte zeigen, wie die Notebook-Datei in Azure Data Studio zu öffnen:

1. Verbinden Sie in Azure Data Studio mit dem HDFS/Spark-Gateway von Ihrer big Data-Cluster. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit dem HDFS/Spark-Gateway](connect-to-big-data-cluster.md#hdfs).

1. Doppelklicken Sie auf das HDFS/Spark-Gateway-Verbindung in der **Server** Fenster. Wählen Sie dann **Notizbuch öffnen**.

   ![Notizbuch öffnen](media/tutorial-notebook-spark/azure-data-studio-open-notebook.png)

1. Warten, bis die **Kernel** und den Zielkontext (**Anfügen an**) aufgefüllt werden. Legen Sie die **Kernel** zu **PySpark3**, und legen Sie **Anfügen an** der IP-Adresse Ihres Endpunkts der big Data-Cluster.

   ![Kernel festlegen und Anfügen an](media/tutorial-notebook-spark/set-kernel-and-attach-to.png)

## <a name="run-the-notebook-cells"></a>Führen Sie die Notebook-Zellen

Sie können die einzelnen Zellen des Notebooks ausführen, durch Drücken der Schaltfläche "Play" auf der linken Seite der Zelle. Die Ergebnisse werden im Notebook angezeigt, wenn die Zelle die Ausführung beendet wurde.

![Führen Sie die Zellen des Notebooks](media/tutorial-notebook-spark/run-notebook-cell.png)

Führen Sie jede Zelle in der Beispiel-Notebooks nacheinander aus. Weitere Informationen zur Verwendung von Notebooks mit SQL Server-big Data-Clustern finden Sie unter den folgenden Ressourcen:

- [Verwendung von Notebooks in der Vorschau von SQL Server-2019](notebooks-guidance.md)
- [Gewusst wie: Verwalten von Notebooks in Azure Data Studio](notebooks-how-to-manage.md)

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über die Notebooks aus:
> [!div class="nextstepaction"]
> [Erfahren Sie mehr über die notebooks](notebooks-guidance.md)