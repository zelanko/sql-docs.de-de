---
title: Ausführen von Spark-Aufträgen im Azure-Toolkit für IntelliJ auf SQL Server-Cluster für Big Data
titleSuffix: SQL Server Big Data Clusters
description: Übermitteln von Spark-Aufträgen in SQL Server-Clustern in Big Data im Azure-Toolkit für IntelliJ.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.openlocfilehash: 06ce1d325caa0835381fd6f9ecd5428d2bbb6f66
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018476"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-clusters-in-intellij"></a>Übermitteln von Spark-Aufträgen in SQL Server-Clustern in Big Data in IntelliJ

Einer der wichtigsten Szenarios für die SQL Server-Cluster für Big Data ist die Möglichkeit zum Übermitteln von Spark-Aufträgen. Die Spark Job Submission-Funktion können Sie eine lokale JAR- oder Py-Dateien mit Verweisen auf SQL Server-Cluster für Big Data zu übermitteln. Darüber hinaus können Sie zum Ausführen von einer JAR-Datei oder Py-Dateien, die sich bereits in das HDFS-Dateisystem befinden. 

## <a name="prerequisites"></a>Erforderliche Komponenten

- SQL Server-Big Data-Cluster.
- Oracle Java Development Kit. Sie können die Installation über die [Oracle-Website](https://aka.ms/azure-jdks).
- IntelliJ IDEA. Sie können die Installation über die [JetBrains-Website](https://www.jetbrains.com/idea/download/).
- Azure-Toolkit für IntelliJ-Erweiterung. Installationsanweisungen finden Sie unter [Installieren des Azure-Toolkits für IntelliJ](https://docs.microsoft.com/azure/azure-toolkit-for-intellij-installation).

## <a name="link-sql-server-big-data-cluster"></a>Link SQL Server-Big Data-Cluster
1. Öffnen Sie das IntelliJ IDEA-Tool.

2. Wenn Sie selbst signiertes Zertifikat verwenden, deaktivieren Sie die Überprüfung des SSL-Zertifikat von **Tools** , wählen Sie im Menü **Azure**, **Spark-Cluster SSL-Zertifikat überprüfen**, klicken Sie dann **Deaktivieren**.

    ![Verknüpfen von SQL Server-Cluster für Big Data – Deaktivieren von SSL](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-disableSSL.png)

3. Öffnen Sie Azure-Explorer aus **Ansicht** , wählen Sie im Menü **Tool Windows**, und wählen Sie dann **Azure Explorer**.
4. Klicken Sie mit der rechten Maustaste auf **SQL Server-Cluster für Big Data**Option **Link SQL Server-Cluster für Big Data**. Geben Sie die **Server**, **Benutzernamen**, und **Kennwort**, klicken Sie dann auf **OK**.

    ![Verknüpfen von Big Data-Cluster - Dialogfeld](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-dialog.png)

5. Wenn der nicht vertrauenswürdigen Server-Dialogfeld "Zertifikat" angezeigt wird, klicken Sie auf **Accept**. Sie können das Zertifikat später zu verwalten, finden Sie unter [Serverzertifikate](https://www.jetbrains.com/help/idea/settings-tools-server-certificates.html).

6. Die verknüpfte Cluster listet unter **SQL Server-Cluster für Big Data**. Sie können Spark-Auftrag überwachen, indem Sie öffnen die Spark-verlaufsbenutzeroberfläche und die Yarn-Benutzeroberfläche, Sie können auch die Verknüpfung aufheben, indem Sie mit der rechten Maustaste auf dem Cluster.

    ![Verknüpfen von Big Data-Cluster - Kontextmenü](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-contextmenu.png)

## <a name="create-a-spark-scala-application-from-hdinsight-template"></a>Erstellen von Spark Scala-Anwendung aus HDInsight-Vorlage

1. Starten Sie IntelliJ IDEA, und erstellen Sie ein Projekt. In der **neues Projekt** (Dialogfeld), führen Sie folgende Schritte aus: 

   a. Wählen Sie **Azure Spark/HDInsight** > **Spark-Projekt mit Beispielen (Scala)**.

   b. In der **Buildtool** wählen Sie eines der folgenden, je nach Ihren Anforderungen:

      * **Maven**, für die Unterstützung des Scala-projekterstellungs-Assistenten
      * **SBT**, zum Verwalten von Abhängigkeiten, und erstellen für das Scala-Projekt

    ![Das Dialogfeld "Neues Projekt"](./media/spark-submit-job-intellij-tool-plugin/create-hdi-scala-app.png)

2. Wählen Sie **Weiter**aus.

3. Fügt der Scala-projekterstellungs-Assistent erkennt automatisch, ob das Scala-Plug-In installiert haben. Wählen Sie **Installieren**aus.

   ![Scala-Plug-in-Überprüfung](./media/spark-submit-job-intellij-tool-plugin/Scala-Plugin-check-Reminder.PNG) 

4. Wählen Sie zum Herunterladen des Scala-Plug-in **OK**. Befolgen Sie die Anweisungen zum Neustart von IntelliJ. 

   ![Dialogfeld für die Scala-Plug-in-installation](./media/spark-submit-job-intellij-tool-plugin/Choose-Scala-Plugin.PNG)

5. In der **neues Projekt** Fenster, gehen Sie folgendermaßen vor:  

    ![Auswählen des Spark-SDK](./media/spark-submit-job-intellij-tool-plugin/hdi-new-project.png)

   a. Geben Sie einen Projektnamen und einen Speicherort aus.

   b. In der **Projekt-SDK** Dropdown-Liste **Java 1.8** für Spark 2.x-Cluster oder Select **Java 1.7** für Spark 1.x-Cluster.

   c. In der **Spark-Version** Dropdown-Liste "," Scala-projekterstellungs-Assistent integriert die richtige Version von Spark-SDK und Scala-SDK. Wenn die Spark-Clusterversion niedriger als 2.0 ist, wählen Sie **Spark 1.x**. Wählen Sie andernfalls **Spark 2.x**. Dieses Beispiel verwendet **Spark 2.0.2 (Scala 2.11.8)**.

6. Wählen Sie **Fertig stellen** aus.

7. Das Spark-Projekt erstellt automatisch ein Artefakt für Sie. Um das Artefakt anzuzeigen, führen Sie folgende Schritte aus:

   a. Auf der **Datei** , wählen Sie im Menü **Projektstruktur**.

   b. In der **Projektstruktur** wählen Sie im Dialogfeld **Artefakte** um das standardartefakt anzuzeigen, die erstellt wird. Sie können auch eigene Artefakte erstellen, wählen Sie das Pluszeichen (**+**).

      ![Informationen zum Artefakt im Dialogfeld](./media/spark-submit-job-intellij-tool-plugin/default-artifact.png)
      

## <a name="submit-application-to-sql-server-big-data-cluster"></a>Übermitteln Sie für SQL Server-Cluster für Big Data-Anwendung
Nach der Verknüpfung einer SQL Server für Big Data-Cluster können Sie die Anwendung übermitteln.

1. Richten Sie die Konfiguration in **Ausführungs-/Debugkonfigurationen** Fenster, klicken Sie auf und ->**Apache Spark für SQL Server**auf Registerkarte **im Cluster Remote ausführen**, legen Sie die Parameter als Befolgen Sie die, dann klicken Sie auf OK.

    ![Interaktiver Konsole hinzufügen Konfigurationseintrag](./media/spark-submit-job-intellij-tool-plugin/interactive-console-add-config-entry.png)

    ![Verknüpfen von Big Data-Cluster - Konfiguration](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-config.png)

    * Für **Spark-Cluster (nur Linux)**, wählen Sie den Cluster, auf denen die Anwendung ausgeführt werden sollen.

    * Wählen Sie ein Artefakt aus dem IntelliJ-Projekt, oder wählen Sie eine von der Festplatte.

    * **Main-Klassennamen** Feld: Der Standardwert ist die Hauptklasse aus der ausgewählten Datei. Sie können die Klasse ändern, indem Sie auf die Auslassungspunkte (**...** ) und einer anderen Klasse auswählen.   

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

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu SQL Server-Cluster für Big Data und die zugehörigen Szenarien, finden Sie unter [was SQL Server-2019 big Data-Cluster sind](big-data-cluster-overview.md)?
