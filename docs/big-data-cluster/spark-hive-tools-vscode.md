---
title: Ausführen von Spark-Aufträgen mit Spark & Hive Tools für VS Code in Big-Data-Clustern für SQL Server
titleSuffix: SQL Server big data clusters
description: Übermitteln Sie Spark-Aufträge mit der Erweiterung „Spark & Hive Tools“ für Visual Studio Code in Big-Data-Clustern für SQL Server.
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4458666792d7f4629b4e1820e98e2dbb9901c2b6
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68425980"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-cluster-in-visual-studio-code"></a>Übermitteln von Spark-Aufträgen an Big-Data-Cluster von SQL Server in Visual Studio Code

Hier erfahren Sie, wie Sie Spark & Hive Tools für VS Code verwenden, um PySpark-Skripts für Apache Spark zu erstellen und diese zu übermitteln. Zunächst wird beschrieben, wie Sie Spark & Hive Tools für VS Code installieren, anschließend wird die Vorgehensweise zum Übermitteln von Aufträgen an Spark erläutert.  

Die Spark & Hive Tools-Erweiterung kann auf allen von Visual Studio Code unterstützten Plattformen installiert werden. Dazu gehören Windows, Linux und macOS. Im Folgenden werden die Voraussetzungen für verschiedene Plattformen aufgeführt.


## <a name="prerequisites"></a>Voraussetzungen

Die folgenden Elemente sind zum Ausführen der Schritte in diesem Artikel erforderlich:

- Ein Big-Data-Cluster für SQL Server. Siehe [Was sind Big Data-Cluster für SQL Server?](https://docs.microsoft.com/sql/big-data-cluster/big-data-cluster-overview?view=sqlallproducts-allversions)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Mono](https://www.mono-project.com/docs/getting-started/install/). Mono ist nur für Linux und macOS erforderlich.
- [Einrichten einer interaktiven PySpark-Umgebung für Visual Studio Code](https://docs.microsoft.com/azure/hdinsight/set-up-pyspark-interactive-environment)
- Ein lokales Verzeichnis namens **HDexample**.  In diesem Artikel wird das Verzeichnis **C:\HD\HDexample** verwendet.

## <a name="install-spark--hive-tools"></a>Installieren von Spark & Hive Tools

Sobald die Voraussetzungen erfüllt sind, können Sie Spark & Hive Tools für Visual Studio Code installieren.  Führen Sie die folgenden Schritte durch, um Spark & Hive Tools zu installieren:

1. Öffnen Sie Visual Studio Code.

2. Navigieren Sie über die Menüleiste zu **Ansicht** > **Erweiterungen**.

3. Geben Sie **Spark & Hive** in das Suchfeld ein.

4. Wählen Sie **Spark & Hive Tools** aus den Ergebnissen aus, und klicken Sie dann auf **Installieren**.  

   ![Erweiterung installieren](./media/spark-hive-tools-vscode/extension.png)

5. Starten Sie Visual Studio Code bei Bedarf neu.

## <a name="open-work-folder"></a>Öffnen des Arbeitsordners

Führen Sie die folgenden Schritte aus, um einen Arbeitsordner zu öffnen und eine Datei in Visual Studio Code zu erstellen:

1. Navigieren Sie in der Menüleiste zu **Datei** > **Ordner öffnen...**  > **C:\HD\HDexample**, und klicken Sie dann auf **Ordner auswählen**. Daraufhin wird der Ordner links in der Ansicht **Explorer** angezeigt.

2. Wählen Sie den Ordner **HDexample** in der Ansicht **Explorer** aus, und klicken Sie dann auf das Symbol **Neue Datei** neben dem Arbeitsordner.

   ![Neue Datei](./media/spark-hive-tools-vscode/new-file.png)

3. Geben Sie der neuen Datei mit der Erweiterung `.py` (Spark-Skript) einen Namen.  In diesem Beispiel lautet der Name der Datei **HelloWorld.py**.
4. Kopieren Sie den folgenden Code, und fügen Sie ihn in die Skriptdatei ein:
   ```python
    import sys
    from operator import add
    from pyspark.sql import SparkSession, Row
    
    spark = SparkSession\
        .builder\
        .appName("PythonWordCount")\
        .getOrCreate()
    
    data = [Row(col1='pyspark and spark', col2=1), Row(col1='pyspark', col2=2), Row(col1='spark vs hadoop', col2=2), Row(col1='spark', col2=2), Row(col1='hadoop', col2=2)]
    df = spark.createDataFrame(data)
    lines = df.rdd.map(lambda r: r[0])

    counters = lines.flatMap(lambda x: x.split(' ')) \
        .map(lambda x: (x, 1)) \
        .reduceByKey(add)
    
    output = counters.collect()
    sortedCollection = sorted(output, key = lambda r: r[1], reverse = True)
    
    for (word, count) in sortedCollection:
        print("%s: %i" % (word, count))
   ```

## <a name="link-a-sql-server-big-data-cluster"></a>Verknüpfen eines Big-Data-Clusters für SQL Server

Bevor Sie Skripts an Ihre Cluster über Visual Studio Code übermitteln können, müssen Sie einen Big Data-Cluster für SQL Server verknüpfen.

1. Navigieren Sie in der Menüleiste zu **Ansicht** > **Befehlspalette...** , und geben Sie **Spark / Hive: Link a Cluster** (Spark / Hive: Cluster verknüpfen) ein.

   ![Befehl zum Verknüpfen eines Clusters](./media/spark-hive-tools-vscode/link-cluster-command.png)

2. Wählen Sie **SQL Server Big Data** (Big-Data-Cluster für SQL Server) als Typ für den verknüpften Cluster aus.

3. Geben Sie einen Big-Data-Endpunkt für SQL Server ein.

4. Geben Sie einen Benutzernamen für den Big-Data-Cluster für SQL Server ein.

5. Geben Sie ein Kennwort für den Benutzeradministrator ein.

6. Legen Sie einen Anzeigenamen für den Cluster fest (optional).

7. Listen Sie die Cluster auf, überprüfen Sie zur Verifizierung die **Ausgabe**.

## <a name="list-clusters"></a>Auflisten der Cluster

1. Navigieren Sie in der Menüleiste zu **Ansicht** > **Befehlspalette...** , und geben Sie **Spark / Hive: List Cluster** (Spark / Hive: Cluster auflisten).

2. Überprüfen Sie die Ansicht **Ausgabe**.  In der Ansicht werden Ihre verknüpften Cluster angezeigt.

    ![Legen Sie eine Standardkonfiguration für die Cluster fest.](./media/spark-hive-tools-vscode/list-cluster-result.png)

## <a name="set-default-cluster"></a>Festlegen eines Standardclusters

1. Öffnen Sie den Ordner **HDexample** erneut, den Sie [zuvor](#open-work-folder) erstellt haben, wenn Sie ihn geschlossen haben.  

2. Wählen Sie die Datei **HelloWorld.py** aus, die Sie [zuvor](#open-work-folder) erstellt haben, um sie im Skript-Editor zu öffnen.

3. Verknüpfen Sie einen Cluster, wenn Sie dies noch nicht getan haben.

4. Klicken Sie mit der rechten Maustaste in den Skript-Editor, und wählen Sie **Spark / Hive: Set Default Cluster** (Spark / Hive: Standardcluster festlegen) aus.   

5. Legen Sie einen Cluster als Standardcluster für die aktuelle Skriptdatei fest. Die Tools führen automatisch Updates für die Konfigurationsdatei **.VSCode\settings.json** durch. 

   ![Standardclusterkonfiguration festlegen](./media/spark-hive-tools-vscode/set-default-cluster-configuration.png)

## <a name="submit-interactive-pyspark-queries"></a>Übermitteln interaktiver PySpark-Abfragen

Sie können interaktive PySpark-Abfragen mithilfe der folgenden Schritte übermitteln:

1. Öffnen Sie den Ordner **HDexample** erneut, den Sie [zuvor](#open-work-folder) erstellt haben, wenn Sie ihn geschlossen haben.  

2. Wählen Sie die Datei **HelloWorld.py** aus, die Sie [zuvor](#open-work-folder) erstellt haben, um sie im Skript-Editor zu öffnen.

3. Verknüpfen Sie einen Cluster, wenn Sie dies noch nicht getan haben.

4. Wählen Sie den gesamten Code aus, und klicken Sie mit der rechten Maustaste in den Skript-Editor, wählen Sie dann **Spark: PySpark Interactive** aus, um die Abfrage zu übermitteln, oder verwenden Sie die Tastenkombination **STRG + ALT + I**.

   ![PySpark Interactive-Kontextmenü](./media/spark-hive-tools-vscode/pyspark-interactive-right-click.png)

5. Wählen Sie den Cluster aus, wenn Sie keinen Standardcluster festgelegt haben. Nach kurzer Zeit werden die **Python Interactive**-Ergebnisse in einer neuen Registerkarte angezeigt. Außerdem ermöglichen Ihnen die Tools, mithilfe des Kontextmenüs einen Codeblock anstelle einer ganzen Skriptdatei zu übermitteln. 

   ![PySpark Interactive: Python Interactive-Fenster](./media/spark-hive-tools-vscode/pyspark-interactive-python-interactive-window.png) 

6. Geben Sie **„%%info“** ein, und drücken Sie dann **UMSCHALT + EINGABETASTE**, um die Auftragsinformationen anzuzeigen. (Optional)

   ![Auftragsinformationen anzeigen](./media/spark-hive-tools-vscode/pyspark-interactive-view-job-information.png)

   > [!NOTE] 
   >
   > Wenn **Python Extension Enabled** (Python-Erweiterung aktiviert) nicht in den Einstellungen aktiviert ist (die Standardeinstellung ist aktiviert), werden die Ergebnisse der übermittelten PySpark-Interaktion im alten Fenster angezeigt.
   >
   > ![PySpark Interactive: Python-Erweiterung deaktiviert](./media/spark-hive-tools-vscode/pyspark-interactive-python-extension-disabled.png)


## <a name="submit-pyspark-batch-job"></a>Übermitteln von PySpark-Batchaufträgen

1. Öffnen Sie den Ordner **HDexample** erneut, den Sie [zuvor](#open-work-folder) erstellt haben, wenn Sie ihn geschlossen haben.  

2. Wählen Sie die Datei **HelloWorld.py** aus, die Sie [zuvor](#open-work-folder) erstellt haben, um sie im Skript-Editor zu öffnen.

3. Verknüpfen Sie einen Cluster, wenn Sie dies noch nicht getan haben.

4. Klicken Sie mit der rechten Maustaste in den Skript-Editor, und wählen Sie dann **Spark: PySpark Batch** aus, oder verwenden Sie die Tastenkombination **STRG + ALT + H**. 

5. Wählen Sie den Cluster aus, wenn Sie keinen Standardcluster festgelegt haben. Nachdem Sie einen Python-Auftrag übermittelt haben, werden Übermittlungsprotokolle im **Ausgabefenster** in Visual Studio Code angezeigt. Die **Spark UI URL** (Spark-Benutzeroberflächen-URL) und die **Yarn UI URL** (Yarn-Benutzeroberflächen-URL) werden ebenfalls angezeigt. Sie können die URL in einem Webbrowser öffnen, um den Status des Auftrags zu verfolgen.

   ![Python-Auftragsergebnis übermitteln](./media/spark-hive-tools-vscode/submit-pythonjob-result.png) 

## <a name="apache-livy-configuration"></a>Apache Livy-Konfiguration

Die [Apache Livy](https://livy.incubator.apache.org/)-Konfiguration wird unterstützt, diese kann im Arbeitsbereichsordner in der Datei **.VSCode\settings.json** festgelegt werden. Derzeit unterstützt die Livy-Konfiguration nur Python-Skript. Weitere Informationen finden Sie im [README für Livy](https://github.com/cloudera/livy/blob/master/README.rst ).

### <a id="triggerlivyconf"></a>**Auslösen der Livy-Konfiguration**

#### <a name="method-1"></a>Methode 1

1. Navigieren Sie in der Menüleiste zu **Datei** > **Einstellungen** > **Einstellungen**.  
2. Geben Sie im Textfeld **Einstellungen suchen** **HDInsight Job Submission: Livy Conf** (HDInsight-Auftragsübermittlung: Livy-Konfiguration) ein.  
3. Klicken Sie beim relevanten Suchergebnis auf **In „settings.json“ bearbeiten**.

#### <a name="method-2"></a>Methode 2

Übermitteln Sie eine Datei. Beachten Sie, dass der `.vscode`-Ordner automatisch zum Arbeitsordner hinzugefügt wird. Die Livy-Konfiguration finden Sie, indem Sie auf `.vscode\settings.json` klicken.

+ Die Projekteinstellungen:

    ![Livy-Konfiguration](./media/spark-hive-tools-vscode/hdi-livyconfig.png)

>[!NOTE]
>Legen Sie für die Einstellungen **driverMemory** und **executorMemory** Werte mit einer Einheit fest, z. B. 1 g oder 1.024 m. 

### <a name="supported-livy-configurations"></a>Unterstützte Livy-Konfigurationen

#### <a name="post-batches"></a>POST /batches

**Anforderungstext**

| NAME | description | Typ |
| :- | :- | :- |
| file | Die Datei, die die auszuführende Anwendung enthält | Pfad (erforderlich) |
| proxyUser | Der Benutzer, dessen Identität beim Ausführen des Auftrags angenommen werden soll | Zeichenfolge |
| className | Die Java-/Spark-Hauptklasse der Anwendung | Zeichenfolge |
| args | Die Befehlszeilenargumente für die Anwendung | Eine Liste von Zeichenfolgen |
| jars | Die JAR-Dateien, die in dieser Sitzung verwendet werden sollen | Eine Liste von Zeichenfolgen |
| pyFiles | Die Python-Dateien, die in dieser Sitzung verwendet werden sollen | Eine Liste von Zeichenfolgen |
| files | Die Dateien, die in dieser Sitzung verwendet werden sollen | Eine Liste von Zeichenfolgen |
| driverMemory | Die Menge an Arbeitsspeicher, die für den Treiberprozess verwendet werden soll | Zeichenfolge |
| driverCores | Die Anzahl der Kerne, die für den Treiberprozess verwendet werden soll | INT |
| executorMemory | Die Menge an Arbeitsspeicher, die pro Executorprozess verwendet werden soll | Zeichenfolge |
| executorCores | Die Anzahl von Kernen, die für jeden Executor verwendet werden sollen | INT |
| numExecutors | Die Anzahl der Executors, die für diese Sitzung gestartet werden sollen | INT |
| archives | Die Archive, die in dieser Sitzung verwendet werden sollen | Eine Liste von Zeichenfolgen |
| queue | Der Name der YARN-Warteschlange, an die übermittelt werden soll | Zeichenfolge |
| NAME | Der Name der Sitzung | Zeichenfolge |
| conf | Spark-Konfigurationseigenschaften | Zuordnung von Schlüsseln zu Werten |

#### <a name="response-body"></a>Antworttext

Das erstellte Batchobjekt

| NAME | description | Typ |
| :- | :- | :- |
| id | Die Sitzungs-ID | INT |
| appId | Die Anwendungs-ID der Sitzung | Zeichenfolge |
| appInfo | Die ausführliche Anwendungsinformationen | Zuordnung von Schlüsseln zu Werten |
| log | Die Protokollzeilen | Eine Liste von Zeichenfolgen |
| state | Der Batchzustand | Zeichenfolge |

>[!NOTE]
>Die zugewiesene Livy-Konfiguration wird im Ausgabebereich angezeigt, wenn das Skript übermittelt wird.

## <a name="additional-features"></a>Zusätzliche Features

Spark & Hive für Visual Studio Code unterstützt die folgenden Features:

- **Die automatische Vervollständigung von IntelliSense:** Für Schlüsselwörter, Methoden, Variablen usw. werden Vorschläge angezeigt. Verschiedene Symbole stellen verschiedene Objekttypen dar.

    ![IntelliSense-Objekttypen von Spark & Hive Tools für Visual Studio Code](./media/spark-hive-tools-vscode/hdinsight-for-vscode-auto-complete-objects.png)
- **IntelliSense-Fehlermarkierung:** Der Sprachdienst unterstreicht Fehler im Hive-Skript.     
- **Syntaxhervorhebungen:** Der Sprachdienst verwendet verschiedene Farben um zwischen Variablen, Schlüsselwörtern, Datentypen, Funktionen usw. zu unterscheiden. 

    ![Syntaxhervorhebungen in Spark & Hive Tools für Visual Studio Code](./media/spark-hive-tools-vscode/hdinsight-for-vscode-syntax-highlights.png)

## <a name="unlink-cluster"></a>Aufheben der Verknüpfung von Clustern

1. Navigieren Sie in der Menüleiste zu **Ansicht** > **Befehlspalette...** , und geben Sie dann **Spark / Hive: Unlink a Cluster** (Spark / Hive: Clusterverknüpfung aufheben) ein.  

2. Wählen Sie einen Cluster auf, dessen Verknüpfung aufgehoben werden soll.  

3. Überprüfen Sie die **Ausgabe**.  

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen über Big Data-Cluster für SQL Server und zugehörige Szenarios finden Sie unter [Was sind Big Data-Cluster für SQL Server?](https://docs.microsoft.com/sql/big-data-cluster/big-data-cluster-overview?view=sqlallproducts-allversions).
