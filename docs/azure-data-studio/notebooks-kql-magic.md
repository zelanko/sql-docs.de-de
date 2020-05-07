---
title: Notebooks mit KQL Magic in Azure Data Studio
description: In diesem Tutorial erfahren Sie, wie Sie Kqlmagic in Azure Data Studio erstellen und ausführen.
author: markingmyname
ms.author: maghan
ms.reviewer: jukoesma
ms.topic: conceptual
ms.prod: sql
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 04/27/2020
ms.openlocfilehash: a3c4af3166d7c227af1846114321228af9ce7753
ms.sourcegitcommit: 69f93dd1afc0df76c3b4d9203adae0ad7dbd7bb2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2020
ms.locfileid: "82598726"
---
# <a name="kqlmagic-extension-in-azure-data-studio"></a>Kqlmagic-Erweiterung in Azure Data Studio

**Kqlmagic** ist ein Befehl, der die Funktionen des Python-Kernels in **[Azure Data Studio-Notebooks](notebooks-guidance.md)** erweitert. Sie können Python und die **[Kusto-Abfragesprache (KQL)](https://docs.microsoft.com/azure/data-explorer/kusto/query)** zum Abfragen und Visualisieren von Daten mithilfe der umfassenden Bibliothek „Plot.ly“ kombinieren, die mit `render`-Befehlen integriert ist. Kqlmagic bietet Ihnen die Vorteile von Notebooks, Datenanalysen und umfassenden Python-Funktionen über einen Ort. Zu den unterstützten Datenquellen mit Kqlmagic gehören **[Azure Data Explorer](https://docs.microsoft.com/azure/data-explorer/data-explorer-overview)** , **[Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview)** und **[Azure Monitor-Protokolle](https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-logs)** .

In diesem Artikel erfahren Sie, wie Sie ein Notebook in Azure Data Studio mithilfe der Kqlmagic-Erweiterung für Azure Data Explorer-Cluster, Application Insights-Protokolle und Azure Monitor-Protokolle erstellen.

## <a name="prerequisites"></a>Voraussetzungen

- [Azure Data Studio](download-azure-data-studio.md)
- [Python](https://www.python.org/downloads/)

## <a name="install-and-set-up-kqlmagic-in-a-notebook"></a>Installieren und Einrichten von Kqlmagic in einem Notebook

Alle Schritte dieses Abschnitts werden in einem Azure Data Studio-Notebook ausgeführt.

1. Erstellen Sie ein neues Notebook, und ändern Sie den **Kernel** in *Python 3*.

   ![Neues Notebook](media/notebooks-kql-magic/install-new-notebook.png)

2. Wenn Sie dazu aufgefordert werden, ein Upgrade für die Python-Pakete durchzuführen, wählen Sie **Ja** aus.

   ![Ja](media/notebooks-kql-magic/install-python-yes.png)

3. So installieren Sie Kqlmagic:

   ```python
   !pip install Kqlmagic --no-cache-dir --upgrade
   ```

   Überprüfen Sie die Installation:

   ```python
   !pip list
   ```

   ![List](media/notebooks-kql-magic/install-list.png)

4. So laden Sie Kqlmagic:

   ```python
   %reload_ext Kqlmagic
   ```

   > [!Note]
   > Wenn dieser Schritt fehlschlägt, schließen Sie die Datei, und öffnen Sie sie wieder.

   ![Laden der Kqlmagic-Erweiterung](media/notebooks-kql-magic/install-load-kql-magic-ext.png)

5. Sie können testen, ob Kqlmagic ordnungsgemäß geladen wurde, indem Sie die Hilfsdokumentation aufrufen oder die Version überprüfen.

   ```python
   %kql --help "help"
   ```

   > [!Note]
   > Wenn `Samples@help` ein Kennwort anfordert, können Sie das Feld leer lassen und die **EINGABETASTE** drücken.

   ![Hilfe](media/notebooks-kql-magic/install-help.png)

   Führen Sie den folgenden Befehl aus, um zu überprüfen, welche Version von Kqlmagic installiert ist.

   ```python
   %kql --version
   ```

## <a name="kqlmagic-with-an-azure-data-explorer-cluster"></a>Kqlmagic mit einem Azure Data Explorer-Cluster

In diesem Abschnitt wird das Ausführen der Datenanalyse mit Kqlmagic mit einem Azure Data Explorer-Cluster erläutert.

### <a name="load-and-authenticate-kqlmagic-for-azure-data-explorer"></a><a name="ade-load-auth"></a> Laden und Authentifizieren von Kqlmagic für Azure Data Explorer

   > [!Note]
   > Jedes Mal, wenn Sie ein neues Notebook in Azure Data Studio erstellen, müssen Sie die Kqlmagic-Erweiterung laden.

1. Stellen Sie sicher, dass der **Kernel** auf *Python 3* festgelegt ist.

   ![Neues Notebook](media/notebooks-kql-magic/change-kernel.png)

2. So laden Sie Kqlmagic:

   ```python
   %reload_ext Kqlmagic
   ```

   ![Laden der Kqlmagic-Erweiterung](media/notebooks-kql-magic/install-load-kql-magic-ext.png)

3. Stellen Sie eine Verbindung mit dem Cluster her, und führen Sie die Authentifizierung durch:

   ```python
   %kql azureDataExplorer://code;cluster='help';database='Samples'
   ```

   Verwenden Sie die Geräteanmeldung zum Authentifizieren. Kopieren Sie den Code aus der Ausgabe, und klicken Sie auf **Authentifizieren**. Daraufhin wird ein Browser geöffnet, in den Sie den Code einfügen müssen. Sobald Sie sich erfolgreich authentifiziert haben, können Sie zu Azure Data Studio zurückkehren, um mit dem Rest des Skripts fortzufahren.

   ![Azure Data Explorer-Authentifizierung](media/notebooks-kql-magic/ade-auth.png)

### <a name="query-and-visualize-for-azure-data-explorer"></a>Abfragen und Visualisieren von Azure Data Explorer

Fragen Sie Daten mit dem [Render-Operator](https://docs.microsoft.com/azure/data-explorer/kusto/query/renderoperator) ab, und visualisieren Sie Daten mithilfe der Bibliothek „ploy.ly“ Durch die Abfrage und Visualisierung wird eine integrierte Benutzeroberfläche bereitgestellt, die die native KQL verwendet.

1. Analysieren Sie die zehn häufigsten StormEvent-Ereignisse nach Zustand und Häufigkeit:

   ```python
   %kql StormEvents | summarize count() by State | sort by count_ | limit 10
   ```

   Wenn Sie mit KQL vertraut sind, können Sie die Abfrage nach `%kql` eingeben.

   ![Analysieren der StormEvent-Ereignisse](media/notebooks-kql-magic/ade-analyze-storm-events.png)

2. Visualisieren Sie ein Zeitachsendiagramm:

   ```python
   %kql StormEvents \
   | summarize event_count=count() by bin(StartTime, 1d) \
   | render timechart title= 'Daily Storm Events'
   ```

   ![Visualisierung eines Zeitdiagramms](media/notebooks-kql-magic/ade-visualize-timechart.png)

3. Beispiel für mehrzeilige Abfrage mit `%%kql`

   ```python
   %%kql
   StormEvents
   | summarize count() by State
   | sort by count_
   | limit 10
   | render columnchart title='Top 10 States by Storm Event count'
   ```

   ![Beispiel für mehrzeilige Abfrage](media/notebooks-kql-magic/ade-multiline-query-sample.png)

## <a name="kqlmagic-with-application-insights"></a>Kqlmagic mit Application Insights

### <a name="load-and-authenticate-kqlmagic-for-application-insights"></a><a name="appin-load-auth"></a> Laden und Authentifizieren von Kqlmagic für Application Insights

1. Stellen Sie sicher, dass der **Kernel** auf *Python 3* festgelegt ist.

   ![Neues Notebook](media/notebooks-kql-magic/change-kernel.png)

2. So laden Sie Kqlmagic:

   ```python
   %reload_ext Kqlmagic
   ```

   ![Laden der Kqlmagic-Erweiterung](media/notebooks-kql-magic/install-load-kql-magic-ext.png)

   > [!Note]
   > Jedes Mal, wenn Sie ein neues Notebook in Azure Data Studio erstellen, müssen Sie die Kqlmagic-Erweiterung laden.

3. Stellen Sie eine Verbindung her, und führen Sie die Authentifizierung durch.

   ```python
   %kql appinsights://appid='DEMO_APP';appkey='DEMO_KEY'
   ```

### <a name="query-and-visualize-for-application-insights"></a>Abfragen und Visualisieren von Application Insights

Fragen Sie Daten mit dem [Render-Operator](https://docs.microsoft.com/azure/data-explorer/kusto/query/renderoperator) ab, und visualisieren Sie Daten mithilfe der Bibliothek „ploy.ly“ Durch die Abfrage und Visualisierung wird eine integrierte Benutzeroberfläche bereitgestellt, die die native KQL verwendet.

1. Zeigen Sie die Seitenansichten an:

   ```python
   %%kql
   pageViews
   | limit 10
   ```

   ![Seitenaufrufe](media/notebooks-kql-magic/appin-page-views.png)

   > [!Note]
   > Ziehen Sie mit Ihrer Maus über einen Bereich des Diagramms, um das jeweilige Datum zu vergrößern.

2. Zeigen Sie die Seitenansichten in einem Zeitachsendiagramm an:

   ```python
   %%kql
   pageViews
   | summarize event_count=count() by name, bin(timestamp, 1d)
   | render timechart title= 'Daily Page Views'
   ```

   ![Zeitachsendiagramm](media/notebooks-kql-magic/appin-timechart.png)

## <a name="kqlmagic-with-azure-monitor-logs"></a>Kqlmagic mit Azure Monitor-Protokollen

### <a name="load-and-authenticate-kqlmagic-for-azure-monitor-logs"></a><a name="aml-load-auth"></a> Laden und Authentifizieren von Kqlmagic für Azure Monitor-Protokollen

1. Stellen Sie sicher, dass der **Kernel** auf *Python 3* festgelegt ist.

   ![Neues Notebook](media/notebooks-kql-magic/change-kernel.png)

2. So laden Sie Kqlmagic:

   ```python
   %reload_ext Kqlmagic
   ```

   ![Laden der Kqlmagic-Erweiterung](media/notebooks-kql-magic/install-load-kql-magic-ext.png)

   > [!Note]
   > Jedes Mal, wenn Sie ein neues Notebook in Azure Data Studio erstellen, müssen Sie die Kqlmagic-Erweiterung laden.

3. Stellen Sie eine Verbindung her, und führen Sie die Authentifizierung durch.

   ```python
   %kql loganalytics://workspace='DEMO_WORKSPACE';appkey='DEMO_KEY';alias='myworkspace'
   ```

   ![Authentifizierung der Protokollanalyse](media/notebooks-kql-magic/aml-auth.png)

### <a name="query-and-visualize-for-azure-monitor-logs"></a>Abfragen und Visualisieren von Azure Monitor-Protokollen

Fragen Sie Daten mit dem [Render-Operator](https://docs.microsoft.com/azure/data-explorer/kusto/query/renderoperator) ab, und visualisieren Sie Daten mithilfe der Bibliothek „ploy.ly“ Durch die Abfrage und Visualisierung wird eine integrierte Benutzeroberfläche bereitgestellt, die die native KQL verwendet.

1. Zeigen Sie ein Zeitachsendiagramm an:

   ```python
   %%kql
   KubeNodeInventory
   | summarize event_count=count() by Status, bin(TimeGenerated, 1d)
   | render timechart title= 'Daily Kubernetes Nodes'
   ```

   ![Protokollanalyse des Zeitdiagramms zu täglichen Kubernetes-Knoten](media/notebooks-kql-magic/aml-timechart-daily-kubernetes-nodes.png)

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über Notebooks und Kqlmagic:

- [Verwenden einer Jupyter Notebook-Instanz und der Kqlmagic-Erweiterung zum Analysieren von Daten in Azure Data Explorer](https://docs.microsoft.com/azure/data-explorer/Kqlmagic)
- [Magic-Erweiterung für Jupyter Notebook und Jupyter Lab zum Ermöglichen der Notebook-Funktion mit Daten von Kusto, Application Insights und der Protokollanalyse](https://github.com/Microsoft/jupyter-Kqlmagic)
- [Kqlmagic](https://pypi.org/project/Kqlmagic/)
- [KustoMagicSamples](https://notebooks.azure.com/RknDzgn/projects/KustoMagicSamples/html/Getting%20Started%20with%20Kqlmagic%20on%20Azure%20Data%20Explorer-Copy.ipynb)
- [Verwenden von Notebooks](notebooks-guidance.md)
- [How to manage notebooks in Azure Data Studio (Vorgehensweise: Verwalten von Notebooks in Azure Data Studio)](notebooks-manage-sql-server.md)
