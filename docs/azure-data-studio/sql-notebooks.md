---
title: Verwenden von SQL-Notebooks
titleSuffix: Azure Data Studio
description: Informationen zur Verwendung von SQL-Notebooks in Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: achatter; alayu; maghan; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.custom: seodec18
ms.date: 06/28/2019
ms.openlocfilehash: df1e49af0378b6af4a3d82b5a5ec2a4293be5e35
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "74957084"
---
# <a name="how-to-use-notebooks-in-azure-data-studio"></a>Verwenden von Notebooks in Azure Data Studio

In diesem Artikel wird beschrieben, wie Sie die Notebookumgebung in Azure Data Studio starten und wie Sie mit der Erstellung eigener Notebooks beginnen. Außerdem wird gezeigt, wie Notebooks mithilfe verschiedener Kernel geschrieben werden.


## <a name="connect-to-sql-server"></a>Verbindung mit SQL Server herstellen

Sie können in Azure Data Studio eine Verbindung mit dem Microsoft SQL Server-Verbindungstyp herstellen.
In Azure Data Studio können Sie auch F1 drücken und auf **Neue Verbindung** klicken, um eine Verbindung mit dem SQL Server herzustellen.

![image1](media/sql-notebooks/connection-info.png)

## <a name="launch-notebooks"></a>Starten von Notebooks

Es gibt mehrere Möglichkeiten, ein neues Notebook zu starten.

1. Navigieren Sie in Azure Data Studio zum **Menü „Datei“** , und klicken Sie dann auf **New Notebook** (Neues Notebook).

    ![image3](media/sql-notebooks/file-new-notebook.png)

3. Klicken Sie mit der rechten Maustaste auf die **SQL Server**-Verbindung, und starten Sie dann **New Notebook** (Neues Notebook). 
    ![image3](media/sql-notebooks/server-new-notebook.png)

4. Öffnen Sie die Befehlspalette (**STRG+UMSCHALT+P**), und geben Sie dann **New Notebook** (Neues Notebook) ein. Eine neue Datei mit dem Namen `Notebook-1.ipynb` wird geöffnet.

## <a name="supported-kernels-and-attach-to-context"></a>Unterstützte Kernel und Anfügen an Kontext

SQL-Kernel werden von der Notebookinstallation in Azure Data Studio nativ unterstützt. Wenn Sie SQL-Entwickler sind und Notebooks verwenden möchten, wäre dies der ausgewählte Kernel. 

Der SQL-Kernel kann auch verwendet werden, um eine Verbindung mit PostgreSQL-Serverinstanzen herzustellen. Wenn Sie ein PostgreSQL-Entwickler sind und eine Verbindung mit Ihrem PostgreSQL-Server herstellen möchten, müssen Sie die [**PostgreSQL-Erweiterung** ](postgres-extension.md) im Marketplace der Azure Data Studio-Erweiterung herunterladen.

![image7](media/sql-notebooks/sql-kernel-dropdown.png)

### <a name="sql-kernel"></a>SQL-Kernel

In den Codezellen im Notebook unterstützen wir, ähnlich wie bei unserem Abfrage-Editor, moderne SQL-Codierungsfunktionen, die Ihre täglichen Aufgaben mit integrierten Funktionen, wie z. B. einem umfangreichen SQL-Editor, IntelliSense und integrierten Codeausschnitten, vereinfachen. Mit Codeausschnitten können Sie die richtige SQL-Syntax zum Erstellen von Datenbanken, Tabellen, Ansichten, gespeicherten Prozeduren usw. und zum Aktualisieren vorhandener Datenbankobjekte generieren. Verwenden Sie Codeausschnitte, um schnell Kopien der Datenbank zu Entwicklungs- oder Testzwecken zu erstellen und Skripts zu generieren und auszuführen.

Klicken Sie auf **Ausführen**, um jede Zelle auszuführen.

SQL-Kernel zum Herstellen einer Verbindung mit der SQL Server-Instanz

![image7](media/sql-notebooks/intellisense-code-cell.png)

Abfrageergebnisse

![image19](media/sql-notebooks/sql-cell-results.png)

SQL-Kernel zum Herstellen einer Verbindung mit der PostgreSQL-Serverinstanz 

![image18](media/sql-notebooks/pgsql-code-cell.png)

Abfrageergebnisse

![image20](media/sql-notebooks/pgsql-cell-results.png)

### <a name="configure-python-for-notebooks"></a>Konfigurieren von Python für Notebooks

Wenn Sie in der Dropdownliste „Kernel“ einen anderen Kernel als SQL auswählen, erhalten Sie die Aufforderung **Configure Python for Notebooks** (Konfigurieren von Python für Notebooks). Die Notebookabhängigkeiten werden an einem angegebenen Speicherort installiert, Sie können den Installationspfad jedoch auch festlegen. Diese Installation kann einige Zeit in Anspruch nehmen. Es wird empfohlen, die Anwendung erst zu schließen, wenn die Installation abgeschlossen ist. Nachdem die Installation abgeschlossen ist, können Sie mit dem Schreiben von Code in der unterstützten Sprache beginnen.

![image21](media/sql-notebooks/configure-python.png)

Nachdem die Installation erfolgreich abgeschlossen wurde, werden unter „Task History“ (Aufgabenverlauf) eine Benachrichtigung sowie der Speicherort des im Ausgabeterminal ausgeführten Jupyter-Back-End-Servers angegeben.

![image22](media/sql-notebooks/jupyter-backend.png)

|Kernel|Beschreibung
|:-----|:-----
| SQL-Kernel | Schreiben Sie SQL-Code für Ihre relationale Datenbank.
|PySpark3- und PySpark-Kernel| Schreiben Sie Python-Code mithilfe von Spark-Computing aus dem Cluster.
|Spark-Kernel|Schreiben Sie Scala- und R-Code mithilfe von Spark-Computing aus dem Cluster.
|Python-Kernel|Schreiben Sie Python-Code für die lokale Entwicklung.

`Attach to` stellt den Kontext für den anzufügenden Kernel bereit. Wenn Sie SQL-Kernel verwenden, können Sie `Attach to` für eine beliebige SQL Server-Instanz verwenden.

Wenn Sie Python3-Kernel verwenden, ist `Attach to``localhost`. Sie können diesen Kernel für Ihre lokale Python-Entwicklung verwenden.

Wenn Sie mit dem Big-Data-Cluster von SQL Server 2019 verbunden sind, ist `Attach to` standardmäßig der Endpunkt des Clusters und ermöglicht Ihnen das Übermitteln von Python-, Scala- und R-Code mithilfe von Spark-Computing des Clusters.

### <a name="code-cells-and-markdown-cells"></a>Codezellen und Markdownzellen

Fügen Sie eine neue Codezelle hinzu, indem Sie auf der Symbolleiste auf den Befehl **+Code** klicken.

Fügen Sie eine neue Codezelle hinzu, indem Sie auf der Symbolleiste auf den Befehl **+Text** klicken.

![image8](media/sql-notebooks/notebook-toolbar.png)

Die Zelle wechselt in den Bearbeitungsmodus. Geben Sie nun „Markdown“ ein, und Ihnen wird gleichzeitig die Vorschauversion angezeigt.

![image9](media/sql-notebooks/notebook-markdown-cell.png)

Wenn Sie außerhalb der Textzelle klicken, wird der Markdowntext angezeigt.

![image10](media/sql-notebooks/notebook-markdown-preview.png)

### <a name="trusted-and-non-trusted"></a>Vertrauenswürdig und nicht vertrauenswürdig

In Azure Data Studio geöffnete Notebooks gelten standardmäßig als **Vertrauenswürdig**.

Wenn Sie ein Notebook aus einer anderen Quelle öffnen, wird es im Modus **, Nicht vertrauenswürdig** geöffnet, und Sie können es dann als **Vertrauenswürdig** einstufen.

### <a name="save"></a>Speichern 

Sie können das Notebook durch Drücken von **STRG+S** oder durch Klicken auf die Befehle **Speichern**, **Speichern unter** und **Alles speichern** im Menü „Datei“ und auf die in der Befehlspalette eingegebenen **Befehle zum Speichern** speichern.

### <a name="pyspark3pyspark-kernel"></a>Pyspark3/PySpark-Kernel

Wählen Sie den `PySpark Kernel` aus, und geben Sie in der Zelle den folgenden Code ein.

Klicken Sie auf **Ausführen**.

Die Spark-Anwendung wird gestartet, und es wird die folgende Ausgabe zurückgegeben:

![image12](media/sql-notebooks/pyspark.png)

### <a name="spark-kernel--scala-language"></a>Spark-Kernel | Scala-Sprache

Wählen Sie den `Spark|Scala Kernel` aus, und geben Sie in der Zelle den folgenden Code ein.

![image13](media/sql-notebooks/spark-scala.png)

Sie können auch die Zelloptionen anzeigen, indem Sie auf das Symbol „Optionen“ unterhalb von „–“ klicken.

![image14](media/sql-notebooks/scala-cell-options.png)

### <a name="spark-kernel--r-language"></a>Spark-Kernel | R-Sprache

Wählen Sie in der Dropdownliste der Kernels „Spark | R“ aus. Geben Sie in der Zelle den Code ein, oder fügen Sie ihn ein. Klicken Sie auf **Ausführen**, um die folgende Ausgabe anzuzeigen.

![image15](media/sql-notebooks/spark-r.png)

### <a name="local-python-kernel"></a>Lokaler Python-Kernel

Wählen Sie den lokalen Python-Kernel aus, und geben Sie in der Zelle Folgendes ein:

![image16](media/sql-notebooks/local-python.png)

## <a name="manage-packages"></a>Verwalten von Paketen
Zu den Dingen, die wir für die lokale Python-Entwicklung optimiert haben, gehört die Möglichkeit, Pakete zu Installieren, die Kunden für Ihre Szenarios benötigen. Die allgemeinen Pakete wie `pandas`, `numpy` usw. sind standardmäßig integriert. Wenn Sie jedoch ein Paket erwarten, das nicht enthalten ist, schreiben Sie den folgenden Code in die Notebookzelle: 

```python
import <package-name>
```

Wenn Sie diesen Befehl ausführen, wird `Module not found` zurückgegeben. Wenn das Paket vorhanden ist, wird der Fehler nicht angezeigt.

Wenn der Fehler `Module not Found` zurückgegeben wird, klicken Sie auf **Pakete verwalten**, um den Assistenten zu starten. 

![image17](media/sql-notebooks/manage-packages.png)

In diesem Assistenten werden die **installierten** Pakete angezeigt. Sie können die Liste und die Versionen der einzelnen Pakete durchsuchen. Wenn Sie ein Paket **deinstallieren** möchten, klicken Sie auf dieses, und wählen Sie dann die Option **Uninstall selected packages** (Ausgewählte Pakete deinstallieren) aus.

Sie können auch auf **Add new packages** (Neue Pakete hinzufügen) klicken, um nach einem bestimmten Paket zu **suchen**. Wählen Sie die zugehörige Version aus, und klicken Sie dann auf **Installieren**. Standardmäßig wird die neueste Version des gesuchten Pakets ausgewählt. 

Nachdem das Paket installiert wurde, können Sie in die Notebookzelle wechseln und den folgenden Befehl eingeben:

```python
import <package-name>
```

Wenn Sie ein Paket **deinstallieren** möchten, klicken Sie dieses, und wählen Sie dann die Option **Uninstall selected packages** (Ausgewählte Pakete deinstallieren) aus.

## <a name="next-steps"></a>Nächste Schritte

Informationen zum Arbeiten mit einem vorhandenen Notebook finden Sie unter [Vorgehensweise: Verwalten von Notebooks in Azure Data Studio](https://docs.microsoft.com/sql/big-data-cluster/notebooks-how-to-manage?view=sqlallproducts-allversions).