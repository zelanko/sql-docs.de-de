---
title: Führen Sie Notebooks in Azure Data Studio
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird erläutert, wie zum Ausführen von Jupyter-Notebooks in Azure Data Studio, die mit einer SQL Server-2019 big Data-Cluster verbunden wird.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/27/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: a220b78fe93b286837e0e235b881ffd1a612e512
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "58859971"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>Verwendung von Notebooks in der Vorschau von SQL Server-2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie der Notebook-Umgebung in Azure Data Studio starten und zum Starten, erstellen Ihre eigenen Notebooks. Außerdem wird veranschaulicht, Notebooks verwenden unterschiedlicher Kernel zu schreiben.

## <a name="connect-to-sql-server"></a>Verbindung mit SQL Server herstellen

Sie können in den Microsoft SQL Server-Verbindungstyp in Azure Data Studio verbinden.
In Azure Data Studio, Sie können auch F1 drücken, und klicken Sie auf **neue Verbindung** und eine Verbindung mit Ihrer SQL Server.

![Verbindungsinformationen](media/notebooks-guidance/connection-info.png)

## <a name="launch-notebooks"></a>Starten des Notebooks

Es gibt mehrere Möglichkeiten, um ein neues Notebook zu starten.

- Wechseln Sie zu der **Menü "Datei"** in Azure Data Studio, und klicken Sie dann auf **neues Notizbuch**.

    ![Neuen Notebooks](media/notebooks-guidance/file-new-notebook.png)

- Klicken Sie mit der rechten Maustaste auf die **SQL Server** Verbindung, und klicken Sie dann starten **neues Notizbuch**.

    ![Neuen Notebooks](media/notebooks-guidance/server-new-notebook.png)

- Öffnen Sie die befehlspalette (**STRG + UMSCHALT + P**)) und geben Sie im **neues Notizbuch**. Eine neue Datei namens `Notebook-1.ipynb` wird geöffnet.

## <a name="supported-kernels-and-attach-to-context"></a>Kernels unterstützt, und fügen Sie zum Kontext

SQL-Kernel wird von der Notebook-Installation in Studio für Azure Data nativ unterstützt. Wenn Sie eine SQL-Entwickler sind und Notebooks verwenden möchten, wäre dies der gewählten Kernel. 

Der SQL-Kernel kann auch verwendet werden, für die Verbindung mit PostgreSQL-Server-Instanzen. Wenn Sie eine PostgreSQL-Entwickler sind und mit Ihrem PostgreSQL-Server herstellen möchten, laden die [ **PostgreSQL Erweiterung** ](../azure-data-studio/postgres-extension.md) im Studio für Azure Data Marketplace-Erweiterung.

![Verbindung mit PostgreSQL](media/notebooks-guidance/sql-kernel-dropdown.png)

### <a name="sql-kernel"></a>SQL Kernel

In den codezellen im Notebook, ähnlich wie der Abfrage-Editor unterstützt moderne SQL codierumgebung, der Ihre alltäglichen Aufgaben mit integrierten Features wie z. B. einen umfangreichen SQL-Editor, IntelliSense und integrierten Codeausschnitte einfacher macht. Codeausschnitte können Sie die richtige SQL-Syntax zum Erstellen von Datenbanken, Tabellen, Sichten, gespeicherte Prozeduren usw., und klicken Sie zum Aktualisieren vorhandener Datenbankobjekte generiert wird. Verwenden von Codeausschnitten schnell Kopien einer Datenbank für Entwicklungs- oder Testzwecke erstellen und zu generieren und Ausführen von Skripts.

Klicken Sie auf **ausführen** um jede Zelle auszuführen.

SQL-Kernel, um die Verbindung mit SQL Server-Instanz

![SQL Kernel](media/notebooks-guidance/intellisense-code-cell.png)

Abfrageergebnisse

![Abfrageergebnisse](media/notebooks-guidance/sql-cell-results.png)

SQL-Kernel, um die Verbindung mit PostgreSQL-Server-Instanz 

![Verbindung mit PostgreSQL](media/notebooks-guidance/pgsql-code-cell.png)

Abfrageergebnisse

![Abfrageergebnisse](media/notebooks-guidance/pgsql-cell-results.png)

### <a name="configure-python-for-notebooks"></a>Konfigurieren von Python-Notebooks

Wenn Sie eine der anderen Kernel abgesehen von SQL aus der Dropdownliste "Kernel" auswählen, werden Sie dazu aufgefordert **Konfigurieren von Python für Notebooks**. Die Notebook-Abhängigkeiten im angegebenen Speicherort installiert, aber Sie können entscheiden, ob der Speicherort der Installation festgelegt. Diese Installation kann einige Zeit dauern, und es wird empfohlen, die die Anwendung nicht zu schließen, bis die Installation abgeschlossen ist. Sobald die Installation abgeschlossen ist, können Sie das Schreiben von Code in die unterstützte Sprache starten.

![Konfigurieren von python](media/notebooks-guidance/configure-python.png)

Wenn die Installation erfolgreich war, finden Sie eine Benachrichtigung in der Geschichte der Aufgabe sowie den Speicherort des Jupyter-Back-End-Servers in der Ausgabe-Terminal ausführen.

![Jupyter-Back-End](media/notebooks-guidance/jupyter-backend.png)

|Kernel|Description
|:-----|:-----
| SQL Kernel | Schreiben Sie SQL-Code an Ihre relationale Datenbank gerichtet sind.
|PySpark3 und PySpark-Kernel| Schreiben Sie Python-Code, die mit Spark Compute aus dem Cluster.
|Spark-Kernel|Schreiben von Scala und R-Code, die mit Spark Compute aus dem Cluster.
|Python Kernel|Schreiben Sie Python-Code für die lokale Entwicklung.

`Attach to` Liefert den Kontext für den Kernel anfügen. Wenn Sie SQL-Kernel verwenden, können Sie `Attach to` eines SQL Server-Instanzen.

Bei Verwendung der Kernel für Python3 der `Attach to` ist `localhost`. Sie können diesen Kernel für Ihre lokalen Python-Entwicklung verwenden.

Wenn Sie verbunden sind SQL Server-2019 big Data-Cluster, der Standardwert `Attach to` wird dieser Endpunkt des Clusters und informiert Sie Python, Scala und R-Code mithilfe der Spark-COMPUTE-, der dem Cluster zu übermitteln.

### <a name="code-cells-and-markdown-cells"></a>Codezellen und Markdown-Zellen

Fügen Sie eine neue codezelle hinzu, indem Sie auf die **+ Code** Befehl in der Symbolleiste.

Fügen Sie eine neue Textzelle hinzu, indem Sie auf die **+ Text** Befehl in der Symbolleiste.

![Notebook-Symbolleiste](media/notebooks-guidance/notebook-toolbar.png)

Zelle ändert Bearbeitungsmodus, und geben Sie nun Markdown und Sie sehen die Vorschau zur gleichen Zeit

![Markdown-Zelle](media/notebooks-guidance/notebook-markdown-cell.png)

Klicken außerhalb der Textzelle wird den markdowntext angezeigt.

![Markdowntext](media/notebooks-guidance/notebook-markdown-preview.png)

### <a name="trusted-and-non-trusted"></a>Vertrauenswürdige und nicht vertrauenswürdigen

Notebooks in Azure Data Studio geöffnet sind, standardmäßig **vertrauenswürdige**.

Wenn Sie ein Notebook von einer anderen Quelle öffnen, wird es in geöffnet **nicht vertrauenswürdige** Modus aus, und klicken Sie dann Sie stellen **vertrauenswürdige**.

### <a name="save"></a>Speichern

Sie können das Notebook durch Speichern **STRG + S** oder durch Klicken auf die **Datei speichern**, **Datei speichern unter...**  und **Datei Alles speichern** Befehle über das Menü Datei und **Datei: Speichern Sie** Befehle in der befehlspalette den Befehl eingegeben wurden.

### <a name="pyspark3pyspark-kernel"></a>Pyspark3/PySpark kernel

Wählen Sie die `PySpark Kernel` und in den Zellentyp in den folgenden Code.

Klicken Sie auf **Ausführen**.

Der Spark-Anwendung wird gestartet, und gibt die folgende Ausgabe zurück:

![Spark-Anwendung](media/notebooks-guidance/pyspark.png)

### <a name="spark-kernel--scala-language"></a>Spark-Kernel | Sprache Scala

Wählen Sie die `Spark|Scala Kernel` und in den Zellentyp in den folgenden Code.

![Spark Scala](media/notebooks-guidance/spark-scala.png)

Sie können auch die Optionen"Zelle" anzeigen, wenn Sie auf unten auf das Symbol "Optionen" klicken:

![Zellenoptionen für die](media/notebooks-guidance/scala-cell-options.png)

### <a name="spark-kernel--r-language"></a>Spark-Kernel | R-Sprache

Wählen Sie die Spark | R in der Dropdownliste für den Kernel. Geben Sie oder fügen Sie in den Code, in der Zelle. Klicken Sie auf **ausführen** auf die folgende Ausgabe angezeigt.

![Spark, R](media/notebooks-guidance/spark-r.png)

### <a name="local-python-kernel"></a>Lokaler Python-kernel

Wählen Sie die lokalen Python-Kernel und in den Zellentyp unter ""

![Lokales python](media/notebooks-guidance/local-python.png)

## <a name="manage-packages"></a>Verwalten von Paketen

Eines der Dinge, die wir für die lokale Python-Entwicklung optimiert, bestand darin, bieten die Möglichkeit, Pakete zu installieren, die Kunden für ihre Szenarien benötigt würde. Standardmäßig schließen wir die gängige Pakete wie `pandas`, `numpy` usw., aber wenn Sie erwarten ein Paket, das nicht enthalten ist, Schreiben Sie dann den folgenden Code, in die Zellen des Notebooks: 

```python
import <package-name>
```

Wenn Sie diesen Befehl ausführen `Module not found` zurückgegeben wird. Wenn Ihr Paket vorhanden ist, erhalten Sie nicht den Fehler.

Wenn zurückgegeben wird ein `Module not Found` Fehler, klicken Sie auf **-Pakete verwalten** Terminal zu starten. Sie können jetzt Pakete lokal installieren. Verwenden Sie die folgenden Befehle aus, um die Pakete zu installieren:

```bash
./pip install <package-name>
```

   > [!Tip]
   > Befolgen Sie die Anweisungen zum Installieren von Paketen im Terminalfenster ein, auf Mac. 

Nach der Installation des Pakets sollten Sie in der Lage, wechseln in den Zellen des Notebooks, und geben Sie in den folgenden Befehl aus:

```python
import <package-name>
```

Verwenden Sie zum Deinstallieren eines Pakets in Ihr Terminal den folgenden Befehl ein:

```bash
./pip uninstall <package-name>
```

## <a name="next-steps"></a>Nächste Schritte

Arbeiten mit der ein vorhandenes Notebook finden Sie unter [so verwalten Sie Notebooks in Azure Data Studio](notebooks-how-to-manage.md).