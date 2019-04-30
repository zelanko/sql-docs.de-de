---
title: Verwendung von SQL Notebooks in Azure Data Studio
titleSuffix: Azure Data Studio
description: Erfahren Sie, wie SQL-Notebooks in Azure Data Studio verwenden.
ms.custom: seodec18
ms.date: 03/17/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: achatter; alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 9aad778475649280e5472f80ad96973d09803375
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63312787"
---
# <a name="how-to-use-notebooks-in-azure-data-studio"></a>Verwendung von Notebooks in Azure Data Studio

In diesem Artikel wird beschrieben, wie Sie der Notebook-Umgebung in Azure Data Studio starten und zum Starten, erstellen Ihre eigenen Notebooks. Außerdem wird veranschaulicht, Notebooks verwenden unterschiedlicher Kernel zu schreiben.


## <a name="connect-to-sql-server"></a>Verbindung mit SQL Server herstellen

Sie können in den Microsoft SQL Server-Verbindungstyp in Azure Data Studio verbinden.
In Azure Data Studio, Sie können auch F1 drücken, und klicken Sie auf **neue Verbindung** und eine Verbindung mit Ihrer SQL Server.

![Image1](media/sql-notebooks/connection-info.png)

## <a name="launch-notebooks"></a>Starten des Notebooks

Es gibt mehrere Möglichkeiten, um ein neues Notebook zu starten.

1. Wechseln Sie zu der **Menü "Datei"** in Azure Data Studio, und klicken Sie dann auf **neues Notizbuch**.

    ![image3](media/sql-notebooks/file-new-notebook.png)

3. Klicken Sie mit der rechten Maustaste auf die **SQL Server** Verbindung, und klicken Sie dann starten **neues Notizbuch**. 
    ![image3](media/sql-notebooks/server-new-notebook.png)

4. Öffnen Sie die befehlspalette (**STRG + UMSCHALT + P**)) und geben Sie im **neues Notizbuch**. Eine neue Datei namens `Notebook-1.ipynb` wird geöffnet.

## <a name="supported-kernels-and-attach-to-context"></a>Kernels unterstützt, und fügen Sie zum Kontext

SQL-Kernel wird von der Notebook-Installation in Studio für Azure Data nativ unterstützt. Wenn Sie eine SQL-Entwickler sind und Notebooks verwenden möchten, wäre dies der gewählten Kernel. 

Der SQL-Kernel kann auch verwendet werden, für die Verbindung mit PostgreSQL-Server-Instanzen. Wenn Sie eine PostgreSQL-Entwickler sind und mit Ihrem PostgreSQL-Server herstellen möchten, laden die [ **PostgreSQL Erweiterung** ](postgres-extension.md) im Studio für Azure Data Marketplace-Erweiterung.

![image7](media/sql-notebooks/sql-kernel-dropdown.png)

### <a name="sql-kernel"></a>SQL Kernel

In den codezellen im Notebook, ähnlich wie der Abfrage-Editor unterstützt moderne SQL codierumgebung, der Ihre alltäglichen Aufgaben mit integrierten Features wie z. B. einen umfangreichen SQL-Editor, IntelliSense und integrierten Codeausschnitte einfacher macht. Codeausschnitte können Sie die richtige SQL-Syntax zum Erstellen von Datenbanken, Tabellen, Sichten, gespeicherte Prozeduren usw., und klicken Sie zum Aktualisieren vorhandener Datenbankobjekte generiert wird. Verwenden von Codeausschnitten schnell Kopien einer Datenbank für Entwicklungs- oder Testzwecke erstellen und zu generieren und Ausführen von Skripts.

Klicken Sie auf **ausführen** um jede Zelle auszuführen.

SQL-Kernel, um die Verbindung mit SQL Server-Instanz

![image7](media/sql-notebooks/intellisense-code-cell.png)

Abfrageergebnisse

![Image19](media/sql-notebooks/sql-cell-results.png)

SQL-Kernel, um die Verbindung mit PostgreSQL-Server-Instanz 

![Image18](media/sql-notebooks/pgsql-code-cell.png)

Abfrageergebnisse

![Image20](media/sql-notebooks/pgsql-cell-results.png)

### <a name="configure-python-for-notebooks"></a>Konfigurieren von Python-Notebooks

Wenn Sie eine der anderen Kernel abgesehen von SQL aus der Dropdownliste "Kernel" auswählen, werden Sie dazu aufgefordert **Konfigurieren von Python für Notebooks**. Die Notebook-Abhängigkeiten im angegebenen Speicherort installiert, aber Sie können entscheiden, ob der Speicherort der Installation festgelegt. Diese Installation kann einige Zeit dauern, und es wird empfohlen, die die Anwendung nicht zu schließen, bis die Installation abgeschlossen ist. Sobald die Installation abgeschlossen ist, können Sie das Schreiben von Code in die unterstützte Sprache starten.

![Image21](media/sql-notebooks/configure-python.png)

Wenn die Installation erfolgreich war, finden Sie eine Benachrichtigung in der Geschichte der Aufgabe sowie den Speicherort des Jupyter-Back-End-Servers in der Ausgabe-Terminal ausführen.

![Image22](media/sql-notebooks/jupyter-backend.png)

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

![image8](media/sql-notebooks/notebook-toolbar.png)

Zelle ändert Bearbeitungsmodus, und geben Sie nun Markdown und Sie sehen die Vorschau zur gleichen Zeit

![image9](media/sql-notebooks/notebook-markdown-cell.png)

Klicken außerhalb der Textzelle wird den markdowntext angezeigt.

![Image10](media/sql-notebooks/notebook-markdown-preview.png)

### <a name="trusted-and-non-trusted"></a>Vertrauenswürdige und nicht vertrauenswürdigen

Notebooks in Azure Data Studio geöffnet sind, standardmäßig **vertrauenswürdige**.

Wenn Sie ein Notebook von einer anderen Quelle öffnen, wird es in geöffnet **nicht vertrauenswürdige** Modus aus, und klicken Sie dann Sie stellen **vertrauenswürdige**.

### <a name="save"></a>Speichern 

Sie können das Notebook durch Speichern **STRG + S** oder durch Klicken auf die **Datei speichern**, **Datei speichern unter...**  und **Datei Alles speichern** Befehle über das Menü Datei und **Datei: Speichern Sie** Befehle in der befehlspalette den Befehl eingegeben wurden.

### <a name="pyspark3pyspark-kernel"></a>Pyspark3/PySpark kernel

Wählen Sie die `PySpark Kernel` und in den Zellentyp in den folgenden Code.

Klicken Sie auf **Ausführen**.

Der Spark-Anwendung wird gestartet, und gibt die folgende Ausgabe zurück:

![Image12](media/sql-notebooks/pyspark.png)

### <a name="spark-kernel--scala-language"></a>Spark-Kernel | Sprache Scala

Wählen Sie die `Spark|Scala Kernel` und in den Zellentyp in den folgenden Code.

![Image13](media/sql-notebooks/spark-scala.png)

Sie können auch die Optionen"Zelle" anzeigen, wenn Sie auf unten auf das Symbol "Optionen" klicken:

![Image14](media/sql-notebooks/scala-cell-options.png)

### <a name="spark-kernel--r-language"></a>Spark-Kernel | R-Sprache

Wählen Sie die Spark | R in der Dropdownliste für den Kernel. Geben Sie oder fügen Sie in den Code, in der Zelle. Klicken Sie auf **ausführen** auf die folgende Ausgabe angezeigt.

![Image15](media/sql-notebooks/spark-r.png)

### <a name="local-python-kernel"></a>Lokaler Python-kernel

Wählen Sie die lokalen Python-Kernel und in den Zellentyp unter ""

![Image16](media/sql-notebooks/local-python.png)

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

Arbeiten mit der ein vorhandenes Notebook finden Sie unter [so verwalten Sie Notebooks in Azure Data Studio](https://docs.microsoft.com/sql/big-data-cluster/notebooks-how-to-manage?view=sqlallproducts-allversions).