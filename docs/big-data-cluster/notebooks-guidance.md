---
title: Ausführen von Notebooks in Azure Data Studio
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird erläutert, wie Jupyter Notebooks in Azure Data Studio bei einer Verbindung mit einem SQL Server 2019-Big-Data-Cluster ausgeführt werden.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 05/08/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 166964f97f5201d906ea2d1f6262b7a221eb2cba
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958296"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>Verwenden von Notebooks in SQL Server 2019 (Vorschauversion)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie die Notebookumgebung in der neuesten Version von [**Azure Data Studio**](../azure-data-studio/download.md) starten und wie Sie mit der Erstellung eigener Notebooks beginnen. Außerdem wird gezeigt, wie Notebooks mithilfe verschiedener Kernel geschrieben werden.

## <a name="connect-to-sql-server"></a>Verbindung mit SQL Server herstellen

Sie können in Azure Data Studio eine Verbindung mit dem Microsoft SQL Server-Verbindungstyp herstellen.
In Azure Data Studio können Sie auch F1 drücken und auf **Neue Verbindung** klicken, um eine Verbindung mit dem SQL Server herzustellen.

![Verbindungsinformationen](media/notebooks-guidance/connection-info.png)

## <a name="launch-notebooks"></a>Starten von Notebooks

Es gibt mehrere Möglichkeiten, ein neues Notebook zu starten.

- Navigieren Sie in Azure Data Studio zum **Menü „Datei“** , und klicken Sie dann auf **New Notebook** (Neues Notebook).

    ![Neues Notebook](media/notebooks-guidance/file-new-notebook.png)

- Klicken Sie mit der rechten Maustaste auf die **SQL Server**-Verbindung, und starten Sie dann **New Notebook** (Neues Notebook).

    ![Neues Notebook](media/notebooks-guidance/server-new-notebook.png)

- Öffnen Sie die Befehlspalette (**STRG+UMSCHALT+P**), und geben Sie dann **New Notebook** (Neues Notebook) ein. Eine neue Datei mit dem Namen `Notebook-1.ipynb` wird geöffnet.

## <a name="supported-kernels-and-attach-to-context"></a>Unterstützte Kernel und Anfügen an Kontext

SQL-Kernel werden von der Notebookinstallation in Azure Data Studio nativ unterstützt. Wenn Sie SQL-Entwickler sind und Notebooks verwenden möchten, wäre dies der ausgewählte Kernel. 

Der SQL-Kernel kann auch verwendet werden, um eine Verbindung mit PostgreSQL-Serverinstanzen herzustellen. Wenn Sie ein PostgreSQL-Entwickler sind und eine Verbindung zwischen Ihren Notebooks und Ihrem PostgreSQL-Server herstellen möchten, müssen Sie die [**PostgreSQL-Erweiterung**](../azure-data-studio/postgres-extension.md) im Marketplace der Azure Data Studio-Erweiterung herunterladen und dann **New Notebook** (Neues Notebook) starten, um eine Notebookinstanz für die Verbindung mit dem PostgreSQL-Server zu öffnen.

![PostgreSQL-Verbindung](media/notebooks-guidance/sql-kernel-dropdown.png)

### <a name="sql-kernel"></a>SQL-Kernel

In den Codezellen im Notebook unterstützen wir, ähnlich wie bei unserem Abfrage-Editor, moderne SQL-Codierungsfunktionen, die Ihre täglichen Aufgaben mit integrierten Funktionen, wie z. B. einem umfangreichen SQL-Editor, IntelliSense und integrierten Codeausschnitten, vereinfachen. Mit Codeausschnitten können Sie die richtige SQL-Syntax zum Erstellen von Datenbanken, Tabellen, Ansichten, gespeicherten Prozeduren usw. und zum Aktualisieren vorhandener Datenbankobjekte generieren. Verwenden Sie Codeausschnitte, um schnell Kopien der Datenbank zu Entwicklungs- oder Testzwecken zu erstellen und Skripts zu generieren und auszuführen.

Klicken Sie auf **Ausführen**, um jede Zelle auszuführen.

SQL-Kernel zum Herstellen einer Verbindung mit der SQL Server-Instanz

![SQL-Kernel](media/notebooks-guidance/intellisense-code-cell.png)

Abfrageergebnisse

![Abfrageergebnisse](media/notebooks-guidance/sql-cell-results.png)

SQL-Kernel zum Herstellen einer Verbindung mit der PostgreSQL-Serverinstanz 

![PostgreSQL-Verbindung](media/notebooks-guidance/pgsql-code-cell.png)

Abfrageergebnisse

![Abfrageergebnisse](media/notebooks-guidance/pgsql-cell-results.png)

Klicken Sie in der Symbolleiste auf den Befehl **+Text**, wenn Sie dem vorhandenen Notebook, das an den SQL-Kernel angefügt ist, Textzellen hinzufügen möchten.

![Notebook-Symbolleiste](media/notebooks-guidance/notebook-toolbar.png)

Die Zelle wechselt in den Bearbeitungsmodus. Geben Sie nun „Markdown“ ein, und Ihnen wird gleichzeitig die Vorschauversion angezeigt.

![Markdown-Zelle](media/notebooks-guidance/notebook-markdown-cell.png)

Wenn Sie außerhalb der Textzelle klicken, wird der Markdowntext angezeigt.

![Markdown-Text](media/notebooks-guidance/notebook-markdown-preview.png)


### <a name="configure-python-for-notebooks"></a>Konfigurieren von Python für Notebooks

Wenn Sie in der Dropdownliste „Kernel“ einen anderen Kernel als SQL auswählen, erhalten Sie die Aufforderung **Configure Python for Notebooks** (Konfigurieren von Python für Notebooks). Die Notebookabhängigkeiten werden an einem angegebenen Speicherort installiert, Sie können den Installationspfad jedoch auch festlegen. Diese Installation kann einige Zeit in Anspruch nehmen. Es wird empfohlen, die Anwendung erst zu schließen, wenn die Installation abgeschlossen ist. Nachdem die Installation abgeschlossen ist, können Sie mit dem Schreiben von Code in der unterstützten Sprache beginnen.

![Konfigurieren von Python](media/notebooks-guidance/configure-python.png)

Nachdem die Installation erfolgreich abgeschlossen wurde, werden unter „Task History“ (Aufgabenverlauf) eine Benachrichtigung sowie der Speicherort des im Ausgabeterminal ausgeführten Jupyter-Back-End-Servers angegeben.

![Jupyter-Back-End](media/notebooks-guidance/jupyter-backend.png)

|Kernel|und Beschreibung
|:-----|:-----
| SQL-Kernel | Schreiben Sie SQL-Code für Ihre relationale Datenbank.
|PySpark3- und PySpark-Kernel| Schreiben Sie Python-Code mithilfe von Spark-Computing aus dem Cluster.
|Spark-Kernel|Schreiben Sie Scala- und R-Code mithilfe von Spark-Computing aus dem Cluster.
|Python-Kernel|Schreiben Sie Python-Code für die lokale Entwicklung.

`Attach to` stellt den Kontext für den anzufügenden Kernel bereit. Wenn Sie SQL-Kernel verwenden, können Sie `Attach to` für eine beliebige SQL Server-Instanz verwenden.

Wenn Sie Python3-Kernel verwenden, ist `Attach to` `localhost`. Sie können diesen Kernel für Ihre lokale Python-Entwicklung verwenden.

Wenn Sie mit dem Big-Data-Cluster von SQL Server 2019 verbunden sind, ist `Attach to` standardmäßig der Endpunkt des Clusters und ermöglicht Ihnen das Übermitteln von Python-, Scala- und R-Code mithilfe von Spark-Computing des Clusters.

### <a name="code-cells-and-markdown-cells"></a>Codezellen und Markdownzellen

Fügen Sie eine neue Codezelle hinzu, indem Sie auf der Symbolleiste auf den Befehl **+Code** klicken.

Fügen Sie eine neue Codezelle hinzu, indem Sie auf der Symbolleiste auf den Befehl **+Text** klicken.

![Notebook-Symbolleiste](media/notebooks-guidance/notebook-toolbar.png)

Die Zelle wechselt in den Bearbeitungsmodus. Geben Sie nun „Markdown“ ein, und Ihnen wird gleichzeitig die Vorschauversion angezeigt.

![Markdown-Zelle](media/notebooks-guidance/notebook-markdown-cell.png)

Wenn Sie außerhalb der Textzelle klicken, wird der Markdowntext angezeigt.

![Markdown-Text](media/notebooks-guidance/notebook-markdown-preview.png)

### <a name="trusted-and-non-trusted"></a>Vertrauenswürdig und nicht vertrauenswürdig

In Azure Data Studio geöffnete Notebooks gelten standardmäßig als **Vertrauenswürdig**.

Wenn Sie ein Notebook aus einer anderen Quelle öffnen, wird es im Modus **, Nicht vertrauenswürdig** geöffnet, und Sie können es dann als **Vertrauenswürdig** einstufen.

### <a name="run-cells"></a>Ausführen von Zellen
Klicken Sie auf der Symbolleiste auf die Schaltfläche **Run Cells** (Zellen ausführen), wenn Sie alle Zellen im Notebook ausführen möchten.

![Markdown-Text](media/notebooks-guidance/run-cell.png)


### <a name="clear-results"></a>Ergebnisse löschen

Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ergebnisse löschen**, wenn Sie die Ergebnisse aller ausgeführten Zellen im Notebook löschen möchten.

![Markdown-Text](media/notebooks-guidance/clear-results.png)

### <a name="save"></a>Speichern

Führen Sie zum Speichern des Notebooks eine der folgenden Aktionen aus:

- Drücken Sie STRG+S.
- Klicken Sie auf **Datei** > **Speichern**.
- Klicken Sie auf **Datei** > **Speichern unter**.
- Klicken Sie auf **Datei** > **Alle speichern**. 
- Geben Sie in der Befehlspalette **Datei: Speichern** ein. 

### <a name="pyspark3pyspark-kernel"></a>Pyspark3/PySpark-Kernel

Wählen Sie den `PySpark Kernel` aus, und geben Sie in der Zelle den folgenden Code ein.

Klicken Sie auf **Ausführen**.

Die Spark-Anwendung wird gestartet, und es wird die folgende Ausgabe zurückgegeben:

![Spark-Anwendung](media/notebooks-guidance/pyspark.png)

### <a name="spark-kernel--scala-language"></a>Spark-Kernel | Scala-Sprache

Wählen Sie den `Spark|Scala Kernel` aus, und geben Sie in der Zelle den folgenden Code ein.

![Spark-Kernel/Scala-Sprache](media/notebooks-guidance/spark-scala.png)

Sie können auch die Zelloptionen anzeigen, indem Sie auf das Symbol „Optionen“ unterhalb von „–“ klicken.

![Zelloptionen](media/notebooks-guidance/scala-cell-options.png)

### <a name="spark-kernel--r-language"></a>Spark-Kernel | R-Sprache

Wählen Sie in der Dropdownliste der Kernels „Spark | R“ aus. Geben Sie in der Zelle den Code ein, oder fügen Sie ihn ein. Klicken Sie auf **Ausführen**, um die folgende Ausgabe anzuzeigen.

![Spark R](media/notebooks-guidance/spark-r.png)

### <a name="local-python-kernel"></a>Lokaler Python-Kernel

Wählen Sie den lokalen Python-Kernel aus, und geben Sie in der Zelle Folgendes ein:

![Lokaler Python-Kernel](media/notebooks-guidance/local-python.png)

## <a name="manage-packages"></a>Verwalten von Paketen

Zu den Dingen, die wir für die lokale Python-Entwicklung optimiert haben, gehört die Möglichkeit, Pakete zu Installieren, die Kunden für Ihre Szenarios benötigen. Die allgemeinen Pakete wie `pandas`, `numpy` usw. sind standardmäßig integriert. Wenn Sie jedoch ein Paket erwarten, das nicht enthalten ist, schreiben Sie den folgenden Code in die Notebookzelle: 

```python
import <package-name>
```

Wenn Sie diesen Befehl ausführen, wird `Module not found` zurückgegeben. Wenn das Paket vorhanden ist, wird der Fehler nicht angezeigt.

Wenn der Fehler `Module not Found` (Modul nicht gefunden) zurückgegeben wird, klicken Sie auf **Manage Packages** (Pakete verwalten), um das Terminal zu starten. Sie können Pakete jetzt lokal installieren. Verwenden Sie die folgenden Befehle, um die Pakete zu installieren:

```bash
./pip install <package-name>
```

   > [!Tip]
   > Befolgen Sie zum Installieren von Paketen unter Mac die Anweisungen im Terminalfenster. 

Nachdem das Paket installiert wurde, können Sie in die Notebookzelle wechseln und den folgenden Befehl eingeben:

```python
import <package-name>
```

Verwenden Sie den folgenden Code aus dem Terminal, um Pakete zu deinstallieren:

```bash
./pip uninstall <package-name>
```

## <a name="next-steps"></a>Nächste Schritte

Informationen zum Arbeiten mit einem vorhandenen Notebook finden Sie unter [Vorgehensweise: Verwalten von Notebooks in Azure Data Studio](notebooks-how-to-manage.md).