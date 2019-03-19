---
title: Führen Sie Notebooks in Azure Data Studio
titleSuffix: SQL Server 2019 big data clusters
description: In diesem Artikel wird erläutert, wie Jupyter-Notebooks in Azure Data Studio Conneected eine SQL Server-2019 big Data-Cluster ausgeführt wird.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/12/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 44ba203fcd7445add8fce00dd64913f85bcf4cc1
ms.sourcegitcommit: 11ab8a241a6d884b113b3cf475b2b9ed61ff00e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2019
ms.locfileid: "58161657"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>Verwendung von Notebooks in der Vorschau von SQL Server-2019

Dieser Artikel beschreibt, wie Sie Jupyter Notebooks in einem big Data-Cluster zu starten und zum Starten, erstellen Ihre eigenen Notebooks. Es wird gezeigt, wie Aufträge für den Cluster zu übermitteln.

## <a name="prerequisites"></a>Erforderliche Komponenten

Um Notebooks verwenden zu können, müssen Sie die folgenden erforderlichen Komponenten installieren:

- [Eine SQL Server-2019 big Data-cluster](deployment-guidance.md)
- [SQL Server-2019 big Data-Tools](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **SQL Server-2019-Erweiterung**
   - **kubectl**

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="connect-to-the-sql-server-big-data-cluster-end-point"></a>Verbinden Sie mit der SQL Server big Data-Cluster-Endpunkt

Sie können auf verschiedene Endpunkte im Cluster verbinden. Sie können in den Microsoft SQL Server-Verbindungstyp oder an den Endpunkt von SQL Server big Data-Cluster verbinden.
Drücken von F1 in Azure Data Studio, und klicken Sie auf **neue Verbindung** und Sie können mit Ihren Endpunkt des SQL Server big Data-Cluster verbinden.

![Image1](media/notebooks-guidance/image1.png)

## <a name="browse-hdfs"></a>Durchsuchen von HDFS

Nachdem Sie eine Verbindung herstellen, werden Sie Ihre HDFS-Ordner navigieren können. SQL Server startet WebHDFS wird gestartet, wenn die Bereitstellung abgeschlossen ist. Klicken Sie mit WebHDFS, können Sie **aktualisieren**, hinzufügen **neues Verzeichnis**, **hochladen** -Dateien und **löschen**.

![image2](media/notebooks-guidance/image2.png)

Diese einfachen Vorgänge können Sie Ihre eigenen Daten in HDFS zu bringen.

## <a name="launch-new-notebooks"></a>Starten Sie neue Notebooks

>[!NOTE]
>Wenn Sie mehrere Python-Prozesse, die in Ihrer Umgebung ausgeführt haben, löschen Sie zuerst die `.scaleoutdata` Ordner im Verzeichnis installiert. Dies löst die `Reinstall Notebook dependencies` Aufgabe in Azure Data Studio. Es dauert einige Minuten, bis alle Abhängigkeiten installiert werden.

Gibt es Probleme bei der Installation der Notebook-Abhängigkeiten, klicken Sie auf STRG + UMSCHALT + P oder für Macintosh Cmd + UMSCHALT + P, und geben Sie `Reinstall Notebook dependencies` in der befehlspalette.

![image3](media/notebooks-guidance/image3.png)

Es gibt mehrere Möglichkeiten, um ein neues Notebook zu starten.

1. Von der **Management-Dashboard**. Treffen Sie eine neue Verbindung, und sehen Sie ein Dashboard. Klicken Sie auf **neues Notizbuch** Aufgabe über das Dashboard.
  
    ![image4](media/notebooks-guidance/image4.png)

1. Mit der rechten Maustaste in der HDFS/Spark-Verbindungs, und klicken Sie auf **neues Notizbuch** im Kontextmenü.

    ![image5](media/notebooks-guidance/image5.png)

    Eine neue Datei namens `Notebook-0.ipynb` wird geöffnet.

    ![Image6](media/notebooks-guidance/image6.png)

Wenn Sie das Notebook aus der Palette Befehl öffnen, wird als das Notebook geöffnet `Untitled-0.ipynb`.

## <a name="supported-kernels-and-attach-to-context"></a>Kernels unterstützt, und fügen Sie zum Kontext

Die Notebook-Installation unterstützt die Pyspark- und Spark, Spark Magic Kernel, die Ihnen ermöglichen, Python- und Scala-Code mithilfe von Spark zu schreiben. Optional können Sie Python zu lokalen Entwicklungszwecken auswählen.

![image7](media/notebooks-guidance/image7.png)

Bei Auswahl einer Kernelversion die Installation konfiguriert, Kernel in die virtuelle Umgebung aus, und Sie können das Schreiben von Code in die unterstützte Sprache, starten.

|Kernel|Description
|:-----|:-----
|PySpark3 und PySpark-Kernel| Schreiben Sie Python-Code, die mit Spark Compute aus dem Cluster.
|Spark-Kernel|Schreiben von Scala und R-Code, die mit Spark Compute aus dem Cluster.
|Python Kernel|Schreiben Sie Python-Code für die lokale Entwicklung.

`Attach to` Liefert den Kontext für den Kernel anfügen. Wenn Sie mit der SQL Server big Data-Cluster-Endpunkt, der Standardwert verbunden sind `Attach to` wird dieser Endpunkt des Clusters.

Wenn Sie nicht an den Endpunkt von SQL Server big Data-Cluster verbunden sind, ist die Standardeinstellung Kernel Python und `Attach to` ist `localhost`.

## <a name="hello-world-in-different-contexts"></a>Hallo-Welt in unterschiedlichen Kontexten

### <a name="pyspark3pyspark-kernel"></a>Pyspark3/PySpark kernel

Wählen Sie den PySpark-Kernel und in den Zellentyp in den folgenden Code.

Klicken Sie auf **Ausführen**.

Der Spark-Anwendung wird gestartet, und gibt die folgende Ausgabe zurück:

![image8](media/notebooks-guidance/image8.png)

### <a name="spark-kernel--scala-language"></a>Spark-Kernel | Sprache Scala

Wählen Sie die Spark | Scala-Kernel und in den Zellentyp in den folgenden Code.

![image9](media/notebooks-guidance/image9.png)

Fügen Sie eine neue codezelle hinzu, indem Sie auf die **+ Code** Befehl in der Symbolleiste.

Wählen Sie nun mit dem Spark | Scala, in der Dropdownliste für den Kernel und in der Zelle geben/fügen Sie in:

![Image10](media/notebooks-guidance/image10.png)

Sie können auch die Optionen"Zelle" anzeigen, wenn Sie auf unten auf das Symbol "Optionen" klicken:

![Image11](media/notebooks-guidance/image11.png)

### <a name="spark-kernel--r-language"></a>Spark-Kernel | R-Sprache

Wählen Sie die Spark | R in der Dropdownliste für den Kernel. Geben Sie oder fügen Sie in den Code, in der Zelle. Klicken Sie auf **ausführen** auf die folgende Ausgabe angezeigt.

![Image13](media/notebooks-guidance/image13.png)

### <a name="local-python-kernel"></a>Lokaler Python-kernel

Wählen Sie die lokalen Python-Kernel und in den Zellentyp unter ""

![Image14](media/notebooks-guidance/image14.png)

### <a name="markdown-text"></a>Markdowntext

Fügen Sie eine neue Textzelle hinzu, indem Sie auf die **+ Text** Befehl in der Symbolleiste.

![Image15](media/notebooks-guidance/image15.png)

Doppelklicken Sie in der Textzelle zu ändern, um die Sicht zu bearbeiten 

![Image16](media/notebooks-guidance/image16.png)

Ändert sich die Zelle in den Bearbeitungsmodus

![Image17](media/notebooks-guidance/image17.png)

Jetzt wird Typ Markdown und der Vorschau zur gleichen Zeit finden Sie unter

![Image18](media/notebooks-guidance/image18.png)

Klicken Sie auf **Ausführen**. Der Spark-Anwendung gestartet wird, erstellt die Spark-Sitzung als **Spark** und definiert die **HelloWorld** Objekt.

Das Notebook sollte in der folgenden Abbildung ähneln.

Klicken außerhalb der Textzelle ändert sich in den Vorschaumodus, und blendet das Markdown.

![Image19](media/notebooks-guidance/image19.png)


## <a name="manage-packages"></a>Verwalten von Paketen
Eines der Dinge, die wir für die lokale Python-Entwicklung optimiert, bestand darin, bieten die Möglichkeit, Pakete zu installieren, die Kunden für ihre Szenarien benötigt würde. Standardmäßig schließen wir die gängige Pakete wie `pandas`, `numpy` usw., aber wenn Sie erwarten ein Paket, das nicht enthalten ist, Schreiben Sie dann den folgenden Code, in die Zellen des Notebooks: 

```python
import <package-name>
```

Wenn Sie diesen Befehl ausführen `Module not found` zurückgegeben wird. Wenn Ihr Paket vorhanden ist, erhalten Sie nicht den Fehler.

Wenn zurückgegeben wird ein `Module not Found` Fehler, klicken Sie auf **-Pakete verwalten** , starten Sie das Terminal mit dem Pfad für Ihre Virtualenv identifiziert. Sie können jetzt Pakete lokal installieren. Verwenden Sie die folgenden Befehle aus, um die Pakete zu installieren:

```bash
./pip install <package-name>
```

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