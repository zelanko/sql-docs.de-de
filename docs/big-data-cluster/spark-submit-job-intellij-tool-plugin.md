---
title: Ausführen von Spark-Aufträgen im Azure-Toolkit für IntelliJ auf SQL Server-big Data-cluster
titleSuffix: SQL Server big data clusters
description: Übermitteln von Spark-Aufträgen in SQL Server-big Data-Clustern in Azure-Toolkit für IntelliJ.
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5d2bb4b55b578530a29490a0a1a284f338686c38
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728368"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-clusters-in-intellij"></a>Übermitteln von Spark-Aufträgen in SQL Server-big Data-Clustern in IntelliJ

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Einer der wichtigsten Szenarios für die SQL Server-big Data-Cluster ist die Möglichkeit zum Übermitteln von Spark-Aufträgen. Die Spark Job Submission-Funktion können Sie eine lokale JAR- oder Py-Dateien mit Verweisen auf SQL Server-big Data-Cluster zu übermitteln. Darüber hinaus können Sie zum Ausführen von einer JAR-Datei oder Py-Dateien, die sich bereits in das HDFS-Dateisystem befinden. 

## <a name="prerequisites"></a>Vorraussetzungen

- SQL Server-big Data-Cluster.
- Oracle Java Development Kit. Sie können die Installation über die [Oracle-Website](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).
- IntelliJ IDEA. Sie können die Installation über die [JetBrains-Website](https://www.jetbrains.com/idea/download/).
- Azure-Toolkit für IntelliJ-Erweiterung. Installationsanweisungen finden Sie unter [Installieren des Azure-Toolkits für IntelliJ](https://docs.microsoft.com/azure/azure-toolkit-for-intellij-installation).

## <a name="link-sql-server-big-data-cluster"></a>Link-SQL Server-big Data-cluster
1. Öffnen Sie das IntelliJ IDEA-Tool.

2. Wenn Sie selbst signiertes Zertifikat verwenden, deaktivieren Sie die Überprüfung des SSL-Zertifikat von **Tools** , wählen Sie im Menü **Azure**, **Spark-Cluster SSL-Zertifikat überprüfen**, dann  **Deaktivieren Sie**.

    ![SQL Server-big Data-Cluster verknüpfen – Deaktivieren von SSL](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-disableSSL.png)

3. Öffnen Sie Azure-Explorer aus **Ansicht** , wählen Sie im Menü **Tool Windows**, und wählen Sie dann **Azure Explorer**.
4. Klicken Sie mit der rechten Maustaste auf **SQL Server-big Data-Cluster**Option **Link SQL Server-big Data-Cluster**. Geben Sie die **Server**, **Benutzernamen**, und **Kennwort**, klicken Sie dann auf **OK**.

    ![Verknüpfen von Big Data-Cluster - Dialogfeld](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-dialog.png)

5. Wenn der nicht vertrauenswürdigen Server-Dialogfeld "Zertifikat" angezeigt wird, klicken Sie auf **Accept**. Sie können das Zertifikat später zu verwalten, finden Sie unter [Serverzertifikate](https://www.jetbrains.com/help/idea/settings-tools-server-certificates.html).

6. Die verknüpfte Cluster listet unter **SQL Server-big Data-Cluster**. Sie können Spark-Auftrag überwachen, indem Sie öffnen die Spark-verlaufsbenutzeroberfläche und die Yarn-Benutzeroberfläche, Sie können auch die Verknüpfung aufheben, indem Sie mit der rechten Maustaste auf dem Cluster.

    ![Verknüpfen von Big Data-Cluster - Kontextmenü](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-contextmenu.png)

## <a name="create-a-spark-scala-application-from-hdinsight-template"></a>Erstellen von Spark Scala-Anwendung aus HDInsight-Vorlage

1. Starten Sie IntelliJ IDEA, und erstellen Sie ein Projekt. In der **neues Projekt** (Dialogfeld), führen Sie folgende Schritte aus: 

   a. Wählen Sie **Azure Spark/HDInsight** > **Spark-Projekt mit Beispielen (Scala)** .

   b. In der **Buildtool** wählen Sie eines der folgenden, je nach Ihren Anforderungen:

      * **Maven**, für die Unterstützung des Scala-projekterstellungs-Assistenten
      * **SBT**, zum Verwalten von Abhängigkeiten, und erstellen für das Scala-Projekt

    ![Das Dialogfeld "Neues Projekt"](./media/spark-submit-job-intellij-tool-plugin/create-hdi-scala-app.png)

2. Wählen Sie **Weiter**aus.

3. Fügt der Scala-projekterstellungs-Assistent erkennt automatisch, ob das Scala-Plug-In installiert haben. Wählen Sie **Installieren**aus.

   ![Scala-Plug-in-Überprüfung](./media/spark-submit-job-intellij-tool-plugin/Scala-Plugin-check-Reminder.PNG) 

4. Wählen Sie zum Herunterladen des Scala-Plug-in **OK**. Befolgen Sie die Anweisungen zum Neustart von IntelliJ. 

   ![Dialogfeld für die Scala-Plug-in-installation](./media/spark-submit-job-intellij-tool-plugin/Choose-Scala-Plugin.PNG)

5. In der **neues Projekt** Fenster die folgenden Schritte aus:  

    ![Auswählen des Spark-SDK](./media/spark-submit-job-intellij-tool-plugin/hdi-new-project.png)

   a. Geben Sie einen Projektnamen und einen Speicherort aus.

   b. In der **Projekt-SDK** Dropdown-Liste **Java 1.8** für Spark 2.x-Cluster oder Select **Java 1.7** für Spark 1.x-Cluster.

   c. In der **Spark-Version** Dropdown-Liste "," Scala-projekterstellungs-Assistent integriert die richtige Version von Spark-SDK und Scala-SDK. Wenn die Spark-Clusterversion niedriger als 2.0 ist, wählen Sie **Spark 1.x**. Wählen Sie andernfalls **Spark 2.x**. Dieses Beispiel verwendet **Spark 2.0.2 (Scala 2.11.8)** .

6. Wählen Sie **Fertig stellen** aus.

7. Das Spark-Projekt erstellt automatisch ein Artefakt für Sie. Um das Artefakt anzuzeigen, führen Sie die folgenden Schritte aus:

   a. Auf der **Datei** , wählen Sie im Menü **Projektstruktur**.

   b. In der **Projektstruktur** wählen Sie im Dialogfeld **Artefakte** um das standardartefakt anzuzeigen, die erstellt wird. Sie können auch eigene Artefakte erstellen, wählen Sie das Pluszeichen ( **+** ).

      ![Informationen zum Artefakt im Dialogfeld](./media/spark-submit-job-intellij-tool-plugin/default-artifact.png)
      

## <a name="submit-application-to-sql-server-big-data-cluster"></a>Übermitteln der Anwendung in SQL Server-big Data-cluster
Nach der Verknüpfung einer SQL Server-big Data-Cluster können Sie die Anwendung übermitteln.

1. Richten Sie die Konfiguration in **Ausführungs-/Debugkonfigurationen** Fenster, klicken Sie auf und ->**Apache Spark für SQL Server**auf Registerkarte **im Cluster Remote ausführen**, legen Sie die Parameter als Befolgen Sie die, dann klicken Sie auf OK.

    ![Interaktiver Konsole hinzufügen Konfigurationseintrag](./media/spark-submit-job-intellij-tool-plugin/interactive-console-add-config-entry.png)

    ![Verknüpfen von Big Data-Cluster - Konfiguration](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-config.png)

    * Für **Spark-Cluster (nur Linux)** , wählen Sie den Cluster, auf denen die Anwendung ausgeführt werden sollen.

    * Wählen Sie ein Artefakt aus dem IntelliJ-Projekt, oder wählen Sie eine von der Festplatte.

    * **Main-Klassennamen** Feld: Der Standardwert ist die Hauptklasse aus der ausgewählten Datei. Sie können die Klasse ändern, indem Sie auf die Auslassungspunkte ( **...** ) und einer anderen Klasse auswählen.   

    * **Auftragskonfigurationen** Feld:  Die Standardwerte werden als Bild oben festgelegt. Sie können den Wert ändern oder Hinzufügen von neue Schlüssel-Wert zum Übermitteln von Aufträgen. Weitere Informationen:   [Apache Livy-REST-API](http://livy.incubator.apache.org./docs/latest/rest-api.html)

      ![Die Spark-Übermittlung Dialogfeld Feld Auftrag Konfiguration Bedeutung](./media/spark-submit-job-intellij-tool-plugin/submit-job-configurations.png)

    * **Befehlszeilenargumente** Feld: Sie können die Teilen, indem Sie Speicherplatz für die Hauptklasse, die bei Bedarf Argumente-Werte eingeben.

    * **JAR-Dateien verwiesen** und **referenzierten Dateien** Felder: Sie können die Pfade für den referenzierten JAR-Dateien und Dateien ggf. eingeben. Weitere Informationen:   [Apache Spark-Konfiguration](https://spark.apache.org/docs/latest/configuration.html#runtime-environment) 

      ![Die Spark-Übermittlung Dialogfeld Feld JAR-Dateien, die bedeutet](./media/spark-submit-job-intellij-tool-plugin/jar-files-meaning.png)

       > [!NOTE]  
       > Um Ihre JAR-Dateien auf die verwiesen wird und die referenzierten Dateien hochladen zu können, finden Sie unter: [Ressourcen für den cluster hochladen.](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-storage-explorer)
                         
    * **Hochladen von Pfad**: Sie können den Speicherort für die Übermittlung JAR- oder Scala-Projekt Ressourcen angeben. Es gibt verschiedene Speichertypen unterstützt: **Verwenden von interaktiven Spark-Sitzung zum Hochladen** und **verwenden WebHDFS hochladen**
    
2. Klicken Sie auf **SparkJobRun** um das Projekt für den ausgewählten Cluster zu übermitteln. Die **Remote-Spark-Auftrags im Cluster** Registerkarte zeigt den Status der auftragsausführung unten. Sie können die Anwendung beenden, indem Sie auf die rote Schaltfläche.  

    ![Link-Big Data-Cluster - Ausführung](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-run.png)

## <a name="spark-console"></a>Spark-Konsole
Sie können lokale Console(Scala) Spark ausführen oder Ausführen von interaktiven Livy-Sitzung-Console(Scala) von Spark.

### <a name="spark-local-consolescala"></a>Lokale Spark-Console(Scala)
Stellen Sie sicher, dass Sie die WINUTILS erfüllt haben. Voraussetzung der EXE-Datei.

1. Navigieren Sie in der Menüleiste zum **ausführen** > **Konfigurationen bearbeiten...** .

2. Von der **Ausführungs-/Debugkonfigurationen** Fenster im linken Bereich navigieren Sie zu **Apache Spark für SQL Server-big Data-Cluster** >  **[Spark-SQL] "MyApp"** .

3. Wählen Sie im Hauptfenster der **lokal** Registerkarte.

4. Geben Sie die folgenden Werte ein, und wählen Sie dann **OK**:

    |Eigenschaft |Wert |
    |----|----|
    |Auftrag main-Klasse|Der Standardwert ist die Hauptklasse aus der ausgewählten Datei. Sie können die Klasse ändern, indem Sie auf die Auslassungspunkte ( **...** ) und einer anderen Klasse auswählen.|
    |Umgebungsvariablen|Stellen Sie sicher, dass der Wert für HADOOP_HOME richtig ist.|
    |WINUTILS.exe location|Stellen Sie sicher, dass der Pfad richtig ist.|

    ![Lokale Konsole Festlegen der Konfiguration](./media/spark-submit-job-intellij-tool-plugin/console-set-configuration.png)

5. Navigieren Sie in-Projekt zu **"MyApp"**  > **Src** > **main** > **Scala**  >  **"MyApp"** .  

6. Navigieren Sie in der Menüleiste zum **Tools** > **Spark Konsole** > **lokale Spark-Console(Scala) ausführen**.

7. Klicken Sie dann möglicherweise zwei Dialogfelder angezeigt werden, um anzufordern, dass Sie das sollten Sie automatisch die Abhängigkeiten beheben. Wenn dies der Fall ist, wählen Sie **automatisch korrigieren**.

    ![Spark Auto Fix1](./media/spark-submit-job-intellij-tool-plugin/console-auto-fix1.png)

    ![Spark Auto Fix2](./media/spark-submit-job-intellij-tool-plugin/console-auto-fix2.png)

8. Die Konsole sollte ähnlich der folgenden Abbildung aussehen. In der Konsole Fenstertyp `sc.appName`, und drücken Sie STRG + EINGABETASTE.  Das Ergebnis wird angezeigt. Sie können die lokale Konsole beenden, indem Sie die rote Schaltfläche klicken.

    ![Ergebnis der lokalen Konsole](./media/spark-submit-job-intellij-tool-plugin/local-console-result.png)


### <a name="spark-livy-interactive-session-consolescala"></a>Die interaktive Sitzung Console(Scala) Livy Spark
Die interaktive Spark Livy-Sitzung Console(Scala) wird nur für IntelliJ 2018.2 und 2018.3 unterstützt.

1. Navigieren Sie in der Menüleiste zum **ausführen** > **Konfigurationen bearbeiten...** .

2. Von der **Ausführungs-/Debugkonfigurationen** Fenster im linken Bereich navigieren Sie zu **Apache Spark für SQL Server-big Data-Cluster** >  **[Spark-SQL] "MyApp"** .

3. Wählen Sie im Hauptfenster der **im Cluster Remote ausführen** Registerkarte.

4. Geben Sie die folgenden Werte ein, und wählen Sie dann **OK**:

    |Eigenschaft |Wert |
    |----|----|
    |Spark-Cluster (nur Linux)|Wählen Sie den SQL Server-Big Data-Cluster, die auf dem Sie Ihre Anwendung ausführen möchten.|
    |Name der Hauptklasse|Der Standardwert ist die Hauptklasse aus der ausgewählten Datei. Sie können die Klasse ändern, indem Sie auf die Auslassungspunkte ( **...** ) und einer anderen Klasse auswählen.|

    ![Interaktive Konsole Festlegen der Konfiguration](./media/spark-submit-job-intellij-tool-plugin/interactive-console-configuration.png)

5. Navigieren Sie in-Projekt zu **"MyApp"**  > **Src** > **main** > **Scala**  >  **"MyApp"** .  

6. Navigieren Sie in der Menüleiste zum **Tools** > **Spark Konsole** > **führen Sie Spark Livy interaktive Sitzung Console(Scala)** .

7. Die Konsole sollte ähnlich der folgenden Abbildung aussehen. In der Konsole Fenstertyp `sc.appName`, und drücken Sie STRG + EINGABETASTE.  Das Ergebnis wird angezeigt. Sie können die lokale Konsole beenden, indem Sie die rote Schaltfläche klicken.

    ![Ergebnis der interaktiven Konsole](./media/spark-submit-job-intellij-tool-plugin/interactive-console-result.png)

### <a name="send-selection-to-spark-console"></a>Auswahl an Spark-Konsole zu senden

Der Einfachheit halber sehen Sie das skriptergebnis durch das Senden von Code an die lokale Konsole oder interaktiven Livy-Sitzung-Console(Scala). Sie können Code in die Scala-Datei markieren und dann mit der rechten Maustaste **senden Auswahl zu Spark Konsole**. Der ausgewählte Code wird an die Konsole gesendet werden und ausgeführt werden. Das Ergebnis wird nach dem Code in der Konsole angezeigt werden. Die Konsole wird der Fehler überprüfen Sie, ob vorhandene.  

   ![Auswahl an Spark-Konsole zu senden](./media/spark-submit-job-intellij-tool-plugin/send-selection-to-console.png)

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu SQL Server-big Data-Cluster und die zugehörigen Szenarien, finden Sie unter [was SQL Server-2019 big Data-Cluster sind](big-data-cluster-overview.md)?
