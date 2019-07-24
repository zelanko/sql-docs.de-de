---
title: Ausführen von Spark-Aufträgen mit Spark-& Hive-Tools für vs Code auf SQL Server Big Data Cluster
titleSuffix: SQL Server big data clusters
description: Übermitteln Sie Spark-Auftrag mit den Spark-& Hive-Tools für Visual Studio Code auf SQL Server Big Data Cluster.
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4458666792d7f4629b4e1820e98e2dbb9901c2b6
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425980"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-cluster-in-visual-studio-code"></a>Übermitteln von Spark-Aufträgen auf SQL Server Big Data-Cluster in Visual Studio Code

Erfahren Sie, wie Sie die Spark-& Hive-Tools für Visual Studio Code verwenden, um pyspark-Skripts für Apache Spark zu erstellen und zu übermitteln. Zunächst wird beschrieben, wie Sie die Spark & Hive-Tools in Visual Studio Code installieren. Anschließend werden die Schritte zum Übermitteln von Aufträgen an Spark erläutert.  

Spark-& Hive-Tools können auf Plattformen installiert werden, die von Visual Studio Code unterstützt werden, darunter Windows, Linux und macOS. Im folgenden finden Sie die Voraussetzungen für verschiedene Plattformen.


## <a name="prerequisites"></a>Vorraussetzungen

Zum Ausführen der Schritte in diesem Artikel sind die folgenden Elemente erforderlich:

- Ein SQL Server Big Data Cluster. Siehe [SQL Server Big Data Cluster](https://docs.microsoft.com/sql/big-data-cluster/big-data-cluster-overview?view=sqlallproducts-allversions).
- [Visual Studio Code](https://code.visualstudio.com/).
- [Mono](https://www.mono-project.com/docs/getting-started/install/). Mono ist nur für Linux und macOS erforderlich.
- [Richten Sie eine interaktive pyspark-Umgebung für Visual Studio Code](https://docs.microsoft.com/azure/hdinsight/set-up-pyspark-interactive-environment)ein.
- Ein lokales Verzeichnis namens **hdexample**.  In diesem Artikel wird **c:\hd\hdexample**verwendet.

## <a name="install-spark--hive-tools"></a>Installieren von Spark-& Hive-Tools

Nachdem Sie die Voraussetzungen erfüllt haben, können Sie Spark-& Hive-Tools für Visual Studio Code installieren.  Führen Sie die folgenden Schritte aus, um Spark & Hive-Tools zu installieren:

1. Öffnen Sie Visual Studio Code.

2. Navigieren Sie in der Menüleiste zu**Erweiterungen** **anzeigen** > .

3. Geben Sie im Suchfeld den Suchbegriff **Spark & Hive**ein.

4. Wählen Sie **Spark-& Hive-Tools** aus den Suchergebnissen aus, und klicken Sie dann auf **Installieren**.  

   ![Erweiterung installieren](./media/spark-hive-tools-vscode/extension.png)

5. Bei Bedarf erneut laden.

## <a name="open-work-folder"></a>Arbeitsordner öffnen

Führen Sie die folgenden Schritte aus, um einen Arbeitsordner zu öffnen und eine Datei in Visual Studio Code zu erstellen:

1. Navigieren Sie in der Menüleiste zu **Datei** > **Ordner öffnen...** C:\hd\hdexample, und wählen Sie dann die Schaltfläche **Ordner auswählen** aus.   >  Der Ordner wird in der **Explorer** -Ansicht auf der linken Seite angezeigt.

2. Wählen Sie in der Ansicht **Explorer** den Ordner **hdexample**aus, und klicken Sie dann auf das Symbol **neue Datei** neben dem Arbeitsordner.

   ![Neue Datei](./media/spark-hive-tools-vscode/new-file.png)

3. Benennen Sie die neue Datei mit `.py` der Dateierweiterung (Spark-Skript).  In diesem Beispiel wird **HelloWorld.py**verwendet.
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

## <a name="link-a-sql-server-big-data-cluster"></a>Verknüpfen eines SQL Server Big Data Clusters

Bevor Sie Skripts aus Visual Studio Code an Ihre Cluster übermitteln können, müssen Sie eine SQL Server Big Data Cluster verknüpfen.

1. Navigieren Sie in der Menüleiste  > zu**Befehls Palette anzeigen...** , und **geben Sie Spark/Hive ein: Verknüpfen Sie einen**Cluster.

   ![Link Cluster Befehl](./media/spark-hive-tools-vscode/link-cluster-command.png)

2. Wählen Sie den Typ des verknüpften Clusters **SQL Server Big Data**

3. Geben Sie SQL Server Big Data-Endpunkt ein.

4. Geben Sie SQL Server Big Data-Cluster Benutzernamen ein.

5. Geben Sie das Kennwort für Benutzer Administrator ein.

6. Legen Sie den anzeigen amen des Clusters fest (optional).

7. Auflisten von Clustern, Überprüfen der **Ausgabe** Ansicht für die Überprüfung.

## <a name="list-clusters"></a>Auflisten von Clustern

1. Navigieren Sie in der Menüleiste  > zu**Befehls Palette anzeigen...** , und **geben Sie Spark/Hive ein: Auflisten des**Clusters.

2. Überprüfen Sie die **Ausgabe** Ansicht.  In der Ansicht werden Ihre verknüpften Cluster angezeigt.

    ![Festlegen einer Standard Cluster Konfiguration](./media/spark-hive-tools-vscode/list-cluster-result.png)

## <a name="set-default-cluster"></a>Standard Cluster festlegen

1. Öffnen Sie den [zuvor](#open-work-folder) erstellten Ordner **hdexample** , wenn er geschlossen ist.  

2. Wählen Sie die [zuvor](#open-work-folder) erstellte Datei **HelloWorld.py** aus, die im Skript-Editor geöffnet wird.

3. Verknüpfen Sie einen Cluster, wenn Sie dies noch nicht getan haben.

4. Klicken Sie mit der rechten Maustaste auf den Skript **-Editor, und wählen Sie Spark/Hive: Legen Sie den**Standard Cluster fest.   

5. Wählen Sie einen Cluster als Standard Cluster für die aktuelle Skriptdatei aus. Die Konfigurationsdatei wird von den Tools automatisch aktualisiert **. Vscode \settings.JSON**. 

   ![Festlegen der Standard Cluster Konfiguration](./media/spark-hive-tools-vscode/set-default-cluster-configuration.png)

## <a name="submit-interactive-pyspark-queries"></a>Interaktive pyspark-Abfragen übermitteln

Sie können interaktive pyspark-Abfragen übermitteln, indem Sie die folgenden Schritte ausführen:

1. Öffnen Sie den [zuvor](#open-work-folder) erstellten Ordner **hdexample** , wenn er geschlossen ist.  

2. Wählen Sie die [zuvor](#open-work-folder) erstellte Datei **HelloWorld.py** aus, die im Skript-Editor geöffnet wird.

3. Verknüpfen Sie einen Cluster, wenn Sie dies noch nicht getan haben.

4. Wählen Sie den gesamten Code aus, **und klicken Sie mit der rechten Maustaste auf den Skript-Editor. Pyspark Interactive** , um die Abfrage zu übermitteln, oder verwenden Sie die Tastenkombination **STRG + ALT + I**.

   ![Interaktives Kontextmenü von pyspark](./media/spark-hive-tools-vscode/pyspark-interactive-right-click.png)

5. Wählen Sie den Cluster aus, wenn Sie keinen Standard Cluster angegeben haben. Nach einigen Augenblicken werden die **interaktiven python** -Ergebnisse in einer neuen Registerkarte angezeigt. Mit den Tools können Sie auch einen Codeblock anstelle der gesamten Skriptdatei über das Kontextmenü übermitteln. 

   ![Interaktives Python-Fenster in pyspark](./media/spark-hive-tools-vscode/pyspark-interactive-python-interactive-window.png) 

6. Geben Sie **"%% Info"** ein, und drücken Sie **UMSCHALT + Eingabe** , um die Auftrags Informationen anzuzeigen. (Optional)

   ![Anzeigen von Auftrags Informationen](./media/spark-hive-tools-vscode/pyspark-interactive-view-job-information.png)

   > [!NOTE] 
   >
   > Wenn die **aktivierte python-Erweiterung** in den Einstellungen deaktiviert ist (die Standardeinstellung ist aktiviert), werden die übermittelten pyspark-Interaktions Ergebnisse das alte Fenster verwenden.
   >
   > ![pyspark Interactive python-Erweiterung deaktiviert](./media/spark-hive-tools-vscode/pyspark-interactive-python-extension-disabled.png)


## <a name="submit-pyspark-batch-job"></a>Übermitteln eines pyspark-Batch Auftrags

1. Öffnen Sie den [zuvor](#open-work-folder) erstellten Ordner **hdexample** , wenn er geschlossen ist.  

2. Wählen Sie die [zuvor](#open-work-folder) erstellte Datei **HelloWorld.py** aus, die im Skript-Editor geöffnet wird.

3. Verknüpfen Sie einen Cluster, wenn Sie dies noch nicht getan haben.

4. Klicken Sie mit der rechten Maustaste auf den Skript- **Editor, und wählen Sie Spark aus: Pyspark-** Batch, oder verwenden Sie die Tastenkombination **STRG + ALT + H**. 

5. Wählen Sie den Cluster aus, wenn Sie keinen Standard Cluster angegeben haben. Nach dem Übermitteln eines python-Auftrags werden die Übermittlungs Protokolle in Visual Studio Code im Fenster **Ausgabe** angezeigt. Die URL der **Spark-Benutzeroberfläche** und die **Yarn-UI-URL** werden ebenfalls angezeigt. Sie können die URL in einem Webbrowser öffnen, um den Auftragsstatus zu verfolgen.

   ![Ergebnis des python-Auftrags übermitteln](./media/spark-hive-tools-vscode/submit-pythonjob-result.png) 

## <a name="apache-livy-configuration"></a>Apache Livy-Konfiguration

Die [Apache Livy](https://livy.incubator.apache.org/) -Konfiguration wird unterstützt und kann im festgelegt werden **. Vscode \settings.JSON** im Arbeitsbereich Ordner. Zurzeit unterstützt die Livy-Konfiguration nur python-Skripts. Weitere Informationen finden Sie in der [Livy](https://github.com/cloudera/livy/blob/master/README.rst )-Info.

### <a id="triggerlivyconf"></a>**Vorgehensweise beim Initiieren der Livy-Konfiguration**

#### <a name="method-1"></a>Methode 1

1. Navigieren Sie in der Menüleiste zu **Datei** > **Einstellungen** > **Einstellungen**.  
2. Geben Sie **im Textfeld **Sucheinstellungen** hdinsight Job sumission ein: Livy-** conf.  
3. Wählen Sie **in Settings. JSON bearbeiten** für das relevante Suchergebnis aus.

#### <a name="method-2"></a>Methode 2

Übermitteln Sie eine Datei. `.vscode` beachten Sie, dass der Ordner automatisch dem Arbeitsordner hinzugefügt wird. Sie finden die Livy-Konfiguration, indem `.vscode\settings.json`Sie auf klicken.

+ Die Projekteinstellungen:

    ![Livy-Konfiguration](./media/spark-hive-tools-vscode/hdi-livyconfig.png)

>[!NOTE]
>Legen Sie für die Einstellungen **drivermomory** und **executormomry**den Wert mit Unit fest, z. b. 1 g oder 1024 m. 

### <a name="supported-livy-configurations"></a>Unterstützte Livy-Konfigurationen

#### <a name="post-batches"></a>Nach/Batches

**Anforderungs Text**

| NAME | description | Typ |
| :- | :- | :- |
| file | Die Datei, die die auszuführende Anwendung enthält. | Pfad (erforderlich) |
| proxyUser | Benutzer, dessen Identität beim Ausführen des Auftrags angenommen werden soll | String |
| ClassName | Anwendungs-Java/Spark-Hauptklasse | String |
| args | Befehlszeilenargumente für die Anwendung | Liste der Zeichen folgen |
| à | in dieser Sitzung zu verwendende jar-Informationen | Liste der Zeichen folgen |
| pyFiles | In dieser Sitzung zu verwendende python-Dateien | Liste der Zeichen folgen |
| files | in dieser Sitzung zu verwendende Dateien | Liste der Zeichen folgen |
| drivermemory | Der für den Treiber Prozess zu verwendende Arbeitsspeicher. | String |
| driverkerne | Anzahl der für den Treiber Prozess zu verwendenden Kerne | ssNoversion |
| executormemory | Menge an Arbeitsspeicher, die pro Executor-Prozess verwendet werden soll | String |
| executorcores | Anzahl von Kernen, die für jeden Executor verwendet werden sollen. | ssNoversion |
| numexecutors | Anzahl der für diese Sitzung zu startenden Executors | ssNoversion |
| aufbewahrt | In dieser Sitzung zu verwendende Archive | Liste der Zeichen folgen |
| Warteschlange | Der Name der Yarn-Warteschlange, an die gesendet wurde. | String |
| NAME | Der Name dieser Sitzung. | String |
| behält | Spark-Konfigurations Eigenschaften | Zuordnung von Key = Val |

#### <a name="response-body"></a>Antworttext

Das erstellte Batch-Objekt.

| NAME | description | Typ |
| :- | :- | :- |
| id | Die Sitzungs-ID | ssNoversion |
| AppID | Die Anwendungs-ID dieser Sitzung. | Zeichenfolge |
| AppInfo | Ausführliche Anwendungsinformationen | Zuordnung von Key = Val |
| log | Die Protokoll Zeilen | Liste der Zeichen folgen |
| state | Der Batch Status | String |

>[!NOTE]
>Die zugewiesene Livy-Konfiguration wird beim Übermitteln des Skripts im Ausgabebereich angezeigt.

## <a name="additional-features"></a>Zusätzliche Features

Spark & Hive für Visual Studio Code unterstützt die folgenden Features:

- **IntelliSense-Auto Vervollständigen**. Vorschläge werden für Schlüsselwörter, Methoden, Variablen usw. angezeigt. Verschiedene Symbole stellen verschiedene Typen von Objekten dar.

    ![Spark-& Hive-Tools für Visual Studio Code IntelliSense-Objekttypen](./media/spark-hive-tools-vscode/hdinsight-for-vscode-auto-complete-objects.png)
- **IntelliSense-Fehler Marker**. Der Sprachdienst unterstreicht die Bearbeitungsfehler für das Hive-Skript.     
- **Syntax**Hervorhebung. Der Sprachdienst verwendet verschiedene Farben, um Variablen, Schlüsselwörter, Datentypen, Funktionen usw. zu unterscheiden. 

    ![Spark-& Hive-Tools für Visual Studio Code Syntax Highlights](./media/spark-hive-tools-vscode/hdinsight-for-vscode-syntax-highlights.png)

## <a name="unlink-cluster"></a>Verknüpfung des Clusters aufheben

1. Navigieren Sie in der Menüleiste  > zu**Befehls Palette anzeigen...** , und geben **Sie dann Spark/Hive ein: Aufheben der Verknüpfung eines**Clusters.  

2. Wählen Sie Cluster zum Aufheben der Verknüpfung aus.  

3. Überprüfen Sie die **Ausgabe** Ansicht zur Überprüfung.  

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu SQL Server Big Data-Cluster und verwandten Szenarien finden Sie unter [SQL Server Big Data Cluster](https://docs.microsoft.com/sql/big-data-cluster/big-data-cluster-overview?view=sqlallproducts-allversions).
