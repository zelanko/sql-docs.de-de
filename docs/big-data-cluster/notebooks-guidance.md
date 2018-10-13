---
title: Verwendung von Notebooks in der Vorschau von SQL Server-2019 | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/05/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 137da00959f6f8d3498bb3d063ceb21337266aef
ms.sourcegitcommit: ce4b39bf88c9a423ff240a7e3ac840a532c6fcae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "48878013"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>Verwendung von Notebooks in der Vorschau von SQL Server-2019

In diesem Artikel zeigt, wie Sie Notebooks in einer SQL Server-2019 big Data-Cluster gestartet wird. Es zeigt auch starten, erstellen Ihre eigenen Notebooks und wie Sie Aufträge für den Cluster übermitteln.

## <a name="prerequisites"></a>Erforderliche Komponenten

Um Notebooks verwenden zu können, müssen Sie die folgenden erforderlichen Komponenten installieren:

- [Eine SQL Server-2019 big Data-cluster](deployment-guidance.md)
- [Azure Data Studio](../azure-data-studio/what-is.md)
- [Die Erweiterung für SQL Server-2019 (Vorschau)](../azure-data-studio/sql-server-2019-extension.md).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="connect-to-the-sql-server-big-data-cluster-end-point"></a>Verbinden Sie mit SQL Server-Endpunkt für die big Data-cluster

Sie können mit verschiedenen Endpunkte aufgeführt, in dem Cluster verbinden. Sie können den Verbindungstyp Microsoft SQL Server oder SQL Server-Endpunkt für die big Data-Cluster verbinden.

Geben Sie im Azure Data Studio (Vorschau), **F1** > **neue Verbindung**, und eine Verbindung mit Ihrer SQL Server-Endpunkt für big Data-Cluster.

![Image1](media/notebooks-guidance/image1.png)

## <a name="browse-hdfs"></a>Durchsuchen von HDFS
Nachdem Sie eine Verbindung herstellen, werden Sie Ihre HDFS-Ordner navigieren können. WebHDFS wird gestartet, wenn die Bereitstellung abgeschlossen ist, und Sie können **aktualisieren**, hinzufügen **neues Verzeichnis**, **hochladen** -Dateien und **löschen**.

![image2](media/notebooks-guidance/image2.png)

Diese einfachen Vorgänge können Sie Ihre eigenen Daten in HDFS zu bringen.

## <a name="launch-new-notebooks"></a>Starten Sie neue Notebooks

Es gibt mehrere Möglichkeiten, um ein neues Notebook zu starten.

1. Über das Dashboard verwalten. Auf der Sie eine neue Verbindung herstellen, sehen Sie ein Dashboard. Klicken Sie auf der neuen Notebook-Aufgabe aus dem Dashboard.

  ![image3](media/notebooks-guidance/image3.png)

1. Klicken Sie mit der rechten Maustaste auf das HDFS/Spark-Verbindung, und Sie haben neue Notizbuch im Kontextmenü

![image4](media/notebooks-guidance/image4.png)

Geben Sie einen Namen des Notizbuchs (Beispiel: *Test.ipynb*), und klicken Sie auf **speichern**.

![image5](media/notebooks-guidance/image5.png)

## <a name="supported-kernels-and-attach-to-context"></a>Kernels unterstützt, und fügen Sie zum Kontext

In unserer Notebook-Installation unterstützen wir die Pyspark- und Spark, Spark Magic Kernel, mit denen Benutzer Python- und Scala-Code, die mit Spark schreiben können. Darüber hinaus können Benutzer Python für ihre lokalen Entwicklungszwecken auswählen.

![Image6](media/notebooks-guidance/image6.png)

Bei Auswahl einer Kernelversion installiert dieser Kernel wird in der virtuellen Umgebung aus, und Sie können beginnen, Schreiben von Code in die unterstützte Sprache.

| Kernel | Description
|---- |----
|PySpark-Kernel| Berechnen Sie für das Schreiben von Python-Code mithilfe von Spark, aus dem Cluster.
|Spark-Kernel|Berechnen Sie für das Verwenden von Spark Scala-Code schreiben, aus dem Cluster.
|Python-Kernel|Für das Schreiben von Python-Code für die lokale Entwicklung.

Die Auswahl anfügen, bietet es sich um den Kontext für den Kernel anfügen. Wenn Sie mit der SQL Server-big Data-Cluster-Endpunkt verbunden sind, werden die standardmäßigen-anfügen-to-Auswahl, Endpunkt des Clusters.

![image7](media/notebooks-guidance/image7.png)

> [!NOTE]
> Standardmäßig wird die Spark-Anwendung mit 1-Treiber und 3 Executors, die dauert ca. 8,5 GB Arbeitsspeicher konfiguriert. Die empfohlene Konfiguration mehrerer Spark-Sitzungen ausgeführt wird, für jeden Server in den Cluster mindestens 32 GB Arbeitsspeicher verfügen (z. B. in einer Umgebung AKS verwenden **Standard_D8_v3** VM-Größen mit 32 GB Arbeitsspeicher).

## <a name="hello-world-in-the-different-contexts"></a>Hallo-Welt in unterschiedlichen Kontexten

### <a name="pyspark-kernel"></a>Pyspark-kernel

Wählen Sie den PySpark-Kernel und in den Zellentyp in den folgenden Code:

![image8](media/notebooks-guidance/image8.png)

Klicken Sie auf Ausführen, und Sie finden Sie unter der Spark-Anwendung gestartet wird und Sie die folgende Ausgabe angezeigt werden soll:

![image9](media/notebooks-guidance/image9.png)

Die Ausgabe sollte in etwa wie in der folgenden Abbildung aussehen.

![Image10](media/notebooks-guidance/image10.png)

### <a name="spark-kernel"></a>Spark-kernel
Fügen Sie eine neue codezelle hinzu, indem Sie auf die + -Befehl in der Symbolleiste Code.

![Image11](media/notebooks-guidance/image11.png)

Wählen Sie in der Dropdown-Liste für den Kernel und in der Zelle geben/fügen Sie in der Spark-Kernel 

![Image12](media/notebooks-guidance/image12.png)

Klicken Sie auf **ausführen** sollten die Spark-Anwendung gestartet wird und dies der Spark-Sitzung erstellen **Spark** und definieren die **HelloWorld** Objekt.

Das Notebook sollte in der folgenden Abbildung ähneln.

![Image13](media/notebooks-guidance/image13.png)

Einmal definieren Sie das Objekt dann in der Zelle-Typ des nächsten Notebook in den folgenden Code:

![Image14](media/notebooks-guidance/image14.png)

Klicken Sie auf **ausführen** im Notebook, und Sie im Menü sollte die "Hello, World!" in der Ausgabe.

![Image15](media/notebooks-guidance/image15.png)

### <a name="local-python-kernel"></a>Lokale Python-kernel
Wählen Sie die lokalen Python-Kernel und in den Zellentyp in **

![Image16](media/notebooks-guidance/image16.png)

Daraufhin sollte die folgende Ausgabe angezeigt werden:

![Image17](media/notebooks-guidance/image17.png)

### <a name="markdown-text"></a>Markdowntext
Fügen Sie eine neue Textzelle hinzu, indem Sie auf die + Textbefehl auf der Symbolleiste.

![Image18](media/notebooks-guidance/image18.png)

Klicken Sie auf das vorschausymbol Markdown hinzufügen

![Image19](media/notebooks-guidance/image19.png)

Klicken Sie auf das Symbol "Vorschau" erneut aus, um umschalten, um nur das Markdown finden Sie unter

![Image20](media/notebooks-guidance/image20.png)

## <a name="manage-packages"></a>Verwalten von Paketen
Eines der Dinge, die wir für die lokale Python-Entwicklung optimiert, bestand darin, bieten die Möglichkeit, Pakete zu installieren, die Kunden für ihre Szenarien benötigt würde. Standardmäßig schließen wir die gängige Pakete wie Pandas, Numpy usw., aber wenn Sie ein Paket erwartet werden, die nicht enthalten ist dann schreiben den folgenden Code in die Zellen des Notebooks

```python
import <package-name>
```

Wenn Sie diesen Befehl ausführen, erhalten Sie eine `Module not found` Fehler. Wenn Ihr Paket vorhanden ist, erhalten Sie nicht den Fehler.

Wenn Sie feststellen einer `Module not Found` Fehler, klicken Sie auf die **-Pakete verwalten** , starten Sie das Terminal mit dem Pfad für Ihre Virtualenv identifiziert. Sie können jetzt Pakete lokal installieren. Verwenden Sie den folgenden Befehl aus, um die Pakete zu installieren:

```
./pip install <package-name>
```

Nachdem das Paket installiert ist, sollten Sie in der Lage, wechseln in den Zellen des Notebooks, und geben Sie in den folgenden Befehl:

```python
import <package-name>
```

Nutzen Sie jetzt beim Ausführen der Zelle nicht mehr sollte die `Module not found` Fehler.

Wenn Sie ein Paket zu deinstallieren möchten, verwenden Sie in Ihrem Terminal den folgenden Befehl aus:

```
./pip uninstall <package-name>
```

## <a name="next-steps"></a>Nächste Schritte

Arbeiten mit der ein vorhandenes Notebook finden Sie unter [so verwalten Sie Notebooks in Azure Data Studio](notebooks-how-to-manage.md).