---
title: Verwendung von Notebooks in der Vorschau von SQL Server-2019 | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 9f9db16431cd6c3befbb32383725ec008f5a9081
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221636"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>Verwendung von Notebooks in der Vorschau von SQL Server-2019

Dieser Artikel beschreibt, wie Sie Jupyter-Notebooks auf dem Cluster starten und erstellen Ihre eigenen Notebooks. Es wird gezeigt, wie Aufträge für den Cluster zu übermitteln.

## <a name="prerequisites"></a>Erforderliche Komponenten

Um Notebooks verwenden zu können, müssen Sie die folgenden erforderlichen Komponenten installieren:

- [Eine SQL Server-2019 big Data-cluster](deployment-guidance.md)
- [Azure Data Studio](../azure-data-studio/what-is.md)
- [Die Erweiterung für SQL Server-2019 (Vorschau)](../azure-data-studio/sql-server-2019-extension.md).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="connect-to-the-hadoop-gateway-knox-end-point"></a>Verbinden Sie mit der Hadoop-Gateway-Knox-Endpunkt

Sie können auf verschiedene Endpunkte im Cluster verbinden. Sie können in den Microsoft SQL Server-Verbindungstyp oder an den Endpunkt HDFS/Spark-Gateway verbinden.
Drücken von F1 in Azure Data Studio (Vorschau), und klicken Sie auf **neue Verbindung** und Sie können mit Ihren Endpunkt HDFS/Spark-Gateway verbinden.

![Image1](media/notebooks-guidance/image1.png)

## <a name="browse-hdfs"></a>Durchsuchen von HDFS

Nachdem Sie eine Verbindung herstellen, werden Sie Ihre HDFS-Ordner navigieren können. WebHDFS wird gestartet, wenn die Bereitstellung abgeschlossen ist, und Sie können **aktualisieren**, hinzufügen **neues Verzeichnis**, **hochladen** -Dateien und **löschen**.

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

  Geben Sie einen Namen für Ihre Notebook, z. B. `Test.ipynb`. Klicken Sie auf **Speichern**.

![Image6](media/notebooks-guidance/image6.png)

## <a name="supported-kernels-and-attach-to-context"></a>Kernels unterstützt, und fügen Sie zum Kontext

Die Notebook-Installation unterstützt die Pyspark- und Spark, Spark Magic Kernel, die Ihnen ermöglichen, Python- und Scala-Code mithilfe von Spark zu schreiben. Optional können Sie Python zu lokalen Entwicklungszwecken auswählen.

![image7](media/notebooks-guidance/image7.png)

Bei Auswahl einer Kernelversion installiert dieser Kernel wird in der virtuellen Umgebung aus, und Sie können beginnen, Schreiben von Code in die unterstützte Sprache.

|Kernel|Description
|:-----|:-----
|PySpark-Kernel|Für das Schreiben von Python-Code, die mit Spark Compute aus dem Cluster.
|Spark-Kernel|Für das Schreiben von Scala-Code, die mit Spark Compute aus dem Cluster.
|Python-Kernel|Für das Schreiben von Python-Code für die lokale Entwicklung.

Die `Attach to` liefert den Kontext für den Kernel anfügen. Wenn Sie am Ende HDFS/Spark-Gateway (Knox) verbunden sind, zeigen Sie die Standardeinstellung `Attach to` wird dieser Endpunkt des Clusters.

![image8](media/notebooks-guidance/image8.png)

## <a name="hello-world-in-different-contexts"></a>Hallo-Welt in unterschiedlichen Kontexten

### <a name="pyspark-kernel"></a>Pyspark-kernel

Wählen Sie den PySpark-Kernel und in den Zellentyp in den folgenden Code:

![image9](media/notebooks-guidance/image9.png)

Klicken Sie auf Ausführen, und Sie finden Sie unter der Spark-Anwendung gestartet wird und Sie die folgende Ausgabe angezeigt werden soll:

![Image10](media/notebooks-guidance/image10.png)

Die Ausgabe sollte in etwa wie in der folgenden Abbildung aussehen.

![Image11](media/notebooks-guidance/image11.png)

### <a name="spark-kernel"></a>Spark-kernel
Fügen Sie eine neue codezelle hinzu, indem Sie auf die **+ Code** Befehl in der Symbolleiste.

![Image12](media/notebooks-guidance/image12.png)

Sie können auch die Optionen"Zelle" anzeigen, wenn Sie auf unten auf das Symbol "Optionen" klicken:

![Image13](media/notebooks-guidance/image13.png)

Hier sind die Optionen für jede Zelle ein:

![Image14](media/notebooks-guidance/image14.png)-

Wählen Sie die Spark-Kernel nun in der Dropdownliste für den Kernel und in der Zelle geben/fügen Sie in:

![Image15](media/notebooks-guidance/image15.png)

Klicken Sie auf **ausführen** sollte die Spark-Anwendung gestartet wird, und dies die Spark-Sitzung als erstellen **Spark** und definieren die **HelloWorld** Objekt.

Das Notebook sollte in der folgenden Abbildung ähneln.

![Image16](media/notebooks-guidance/image16.png)

Nachdem Sie das Objekt dann in der nächsten Zelle des Notizbuchs definiert haben, geben Sie den folgenden Code:

![Image17](media/notebooks-guidance/image17.png)

Klicken Sie auf **ausführen** im Notebook, und Sie im Menü sollte die "Hello, World!" in der Ausgabe.

![Image18](media/notebooks-guidance/image18.png)

### <a name="local-python-kernel"></a>Lokale Python-kernel
Wählen Sie die lokalen Python-Kernel und in den Zellentyp unter ""

![Image19](media/notebooks-guidance/image19.png)

Daraufhin sollte die folgende Ausgabe angezeigt werden:

![Image20](media/notebooks-guidance/image20.png)

### <a name="markdown-text"></a>Markdowntext
Fügen Sie eine neue Textzelle hinzu, indem Sie auf die **+ Text** Befehl in der Symbolleiste.

![Image21](media/notebooks-guidance/image21.png)

Klicken Sie auf das vorschausymbol Markdown hinzufügen

![Image22](media/notebooks-guidance/image22.png)

Klicken Sie auf das Symbol "Vorschau" erneut aus, um umschalten, um nur das Markdown finden Sie unter

![Image23](media/notebooks-guidance/image23.png)

## <a name="manage-packages"></a>Verwalten von Paketen
Eines der Dinge, die wir für die lokale Python-Entwicklung optimiert, bestand darin, bieten die Möglichkeit, Pakete zu installieren, die Kunden für ihre Szenarien benötigt würde. Standardmäßig schließen wir die gängige Pakete wie Pandas, Numpy usw., aber wenn Sie ein Paket erwartet werden, die nicht enthalten ist dann schreiben den folgenden Code in die Zellen des Notebooks: 

```python
import <package-name>
```

Wenn Sie diesen Befehl ausführen, erhalten Sie eine `Module not found` Fehler. Wenn Ihr Paket vorhanden ist, erhalten Sie nicht den Fehler.

Wenn Sie finden eine `Module not Found` Fehler, klicken Sie auf **-Pakete verwalten** , starten Sie das Terminal mit dem Pfad für Ihre Virtualenv identifiziert. Sie können jetzt Pakete lokal installieren. Verwenden Sie die folgenden Befehle aus, um die Pakete zu installieren:

```bash
./pip install <package-name>
```

Nach der Installation des Pakets sollten Sie in der Lage, wechseln in den Zellen des Notebooks, und geben Sie in den folgenden Befehl aus:

```python
import <package-name>
```

Nutzen Sie jetzt beim Ausführen der Zelle nicht mehr sollte die `Module not found` Fehler.

Verwenden Sie zum Deinstallieren eines Pakets in Ihr Terminal den folgenden Befehl ein:

```bash
./pip uninstall <package-name>
```

## <a name="next-steps"></a>Nächste Schritte

Arbeiten mit der ein vorhandenes Notebook finden Sie unter [so verwalten Sie Notebooks in Azure Data Studio](notebooks-how-to-manage.md).