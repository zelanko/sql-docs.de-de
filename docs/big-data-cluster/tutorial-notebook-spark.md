---
title: Führen Sie ein Beispiel-Notebook auf eine SQL Server-2019 big Data-Cluster | Microsoft-Dokumentation
description: In diesem Tutorial wird gezeigt, wie Sie die einer Ausführung einer Beispiel-Spark-Notebook auf eine SQL Server-2019 big Data-Cluster (Vorschau) laden können.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/17/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: 811c94615f0d69886f0f538357529ad3125e2925
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644161"
---
# <a name="tutorial-run-a-sample-notebook-on-a-sql-server-2019-big-data-cluster"></a>Tutorial: Ausführen einer Beispiel-Notebook auf einem SQL Server-2019 big Data-cluster

In diesem Tutorial wird veranschaulicht, wie Laden und Ausführen eines Notebooks in Azure Data Studio auf einem SQL Server-2019 big Data-Cluster (Vorschau). Dadurch können Datenanalysten und datentechniker, Python, R oder Scala-Code für den Cluster ausführen.

> [!TIP]
> Falls gewünscht, können Sie herunterladen und Ausführen eines Skripts für die Befehle in diesem Tutorial. Anweisungen finden Sie in der [Spark Beispiele](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark) auf GitHub.

## <a id="prereqs"></a> Erforderliche Komponenten

* [Bereitstellen einen big Data-Cluster in Kubernetes](deployment-guidance.md).
* [Installieren Sie Studio für Azure Data und die Erweiterung für SQL Server-2019](deploy-big-data-tools.md).
* [Laden Sie Beispieldaten in den Cluster](#sampledata).

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

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

1. Verbinden Sie in Azure Data Studio mit dem HDFS/Spark-Gateway von Ihrer big Data-Cluster. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit dem HDFS/Spark-Gateway](deploy-big-data-tools.md#hdfs).

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