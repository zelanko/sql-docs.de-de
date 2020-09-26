---
title: 'Ausführen von Spark-Aufträgen: Azure Toolkit für IntelliJ'
titleSuffix: SQL Server Big Data Clusters
description: Erfahren Sie, wie Sie Spark-Aufträge an Big Data-Cluster in SQL Server in Azure-Toolkit für IntelliJ durch Übermitteln einer lokalen JAR- oder PY-Datei übermitteln.
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.topic: conceptual
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8ef3a0d73535061ef2c9f2ce32556a0a86202d70
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88778539"
---
# <a name="submit-spark-jobs-on-big-data-clusters-2019-in-intellij"></a>Übermitteln von Spark-Aufträgen auf [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] in IntelliJ

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Eines der Hauptszenarios für [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] besteht darin, dass Spark-Aufträge an diese übermittelt werden können. Mit dem Feature zum Übermitteln von Spark-Aufträgen können Sie lokale JAR- oder PY-Dateien mit Verweisen auf [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] übermitteln. Außerdem können Sie JAR- oder PY-Dateien ausführen, die sich bereits auf dem HDFS-Dateisystem befinden. 

## <a name="prerequisites"></a>Voraussetzungen

- Big-Data-Cluster für SQL Server.
- Java Development Kit von Oracle. Sie können dieses von der [Oracle-Website](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) herunterladen und installieren.
- IntelliJ IDEA. Sie können diese IDE von der [JetBrains-Website](https://www.jetbrains.com/idea/download/) herunterladen und installieren.
- Azure-Toolkit für IntelliJ-Erweiterung. Installationsanweisungen finden Sie unter [Installieren des Azure-Toolkits für IntelliJ](/azure/azure-toolkit-for-intellij-installation).

## <a name="link-sql-server-big-data-cluster"></a>Verknüpfen von Big-Data-Clustern für SQL Server
1. Öffnen Sie das IntelliJ IDEA-Tool.

2. Wenn Sie ein selbst signiertes Zertifikat verwenden, deaktivieren Sie die Überprüfung von TLS/SSL-Zertifikaten über **Tools** > **Azure** > **Validate Spark Cluster SSL Certificate** (SSL-Zertifikat für Spark-Cluster überprüfen) > **Disable** (Deaktivieren).

    ![Verknüpfen von Big-Data-Clustern für SQL Server: Deaktivieren von TLS/SSL](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-disableSSL.png)

3. Öffnen Sie den Azure-Explorer über **View** (Ansicht) > **Tool Windows** (Toolfenster) > **Azure Explorer** (Azure-Explorer).
4. Klicken Sie mit der rechten Maustaste auf **SQL Server big data cluster** (Big-Data-Cluster für SQL Server) und anschließend auf **Link SQL Server big data cluster** (Big-Data-Cluster für SQL Server verknüpfen). Geben Sie für **Server**, **User Name** (Benutzername) und **Password** (Kennwort) die entsprechenden Werte ein, und klicken Sie auf **OK**.

    ![Verknüpfen des Big-Data-Clusters: Dialogfeld](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-dialog.png)

5. Wenn das Dialogfeld für nicht vertrauenswürdige Serverzertifikate angezeigt wird, klicken Sie auf **Accept** (Akzeptieren). Sie können die Verwaltungseinstellungen für das Zertifikat später ändern. Weitere Informationen finden Sie unter [Serverzertifikate](https://www.jetbrains.com/help/idea/settings-tools-server-certificates.html).

6. Der verknüpfte Cluster wird unter **SQL Server big data cluster** (Big-Data-Cluster für SQL Server) aufgeführt. Hier können Sie Spark-Aufträge überwachen, indem Sie die Benutzeroberfläche für den Spark-Verlauf und die Yarn-Benutzeroberfläche öffnen. Sie können auch die Verknüpfung aufheben, indem Sie mit der rechten Maustaste auf den Cluster klicken.

    ![Verknüpfen des Big-Data-Clusters: Kontextmenü](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-contextmenu.png)

## <a name="create-a-spark-scala-application-from-spark-template"></a>Erstellen einer Spark Scala-Anwendung mithilfe einer Spark-Vorlage

1. Starten Sie IntelliJ IDEA, und erstellen Sie ein Projekt. Führen Sie im Dialogfeld **New Project** (Neues Projekt) die folgenden Schritte aus: 

   a. Klicken Sie auf **Azure Spark/HDInsight** > **Spark Project with Samples (Scala)** (Spark-Projekt mit Beispielen (Scala)).

   b. Wählen Sie in der Liste **Build tool** (Buildtool) eine der folgenden Optionen entsprechend Ihrer Anforderungen aus:

      * **Maven:** Bei dieser Auswahl wird der Scala-Projekterstellungsassistent unterstützt.
      * **SBT:** Bei dieser Auswahl werden Abhängigkeiten und der Buildvorgang für das Scala-Projekt verwaltet.

    ![Dialogfeld „New Project“ (Neues Projekt)](./media/spark-submit-job-intellij-tool-plugin/create-hdi-scala-app.png)

2. Wählen Sie **Weiter** aus.

3. Der Scala-Projekterstellungsassistent erkennt automatisch, ob Sie das Scala-Plug-In installiert haben. Wählen Sie **Installieren** aus.

   ![Überprüfung des Scala-Plug-Ins](./media/spark-submit-job-intellij-tool-plugin/Scala-Plugin-check-Reminder.PNG) 

4. Klicken Sie auf **OK**, um das Scala-Plug-In herunterzuladen. Folgen Sie den Anweisungen, um IntelliJ neu zu starten. 

   ![Dialogfeld für die Installation des Scala-Plug-Ins](./media/spark-submit-job-intellij-tool-plugin/Choose-Scala-Plugin.PNG)

5. Führen Sie im Fenster **New Project** (Neues Projekt) die folgenden Schritte aus:  

    ![Auswählen des Spark SDK](./media/spark-submit-job-intellij-tool-plugin/hdi-new-project.png)

   a. Geben Sie einen Projektnamen und einen Speicherort ein.

   b. Wählen Sie in der Dropdownliste **Project SDK** (SDK für Projekt) **Java 1.8** für den Spark 2.x-Cluster oder **Java 1.7** für den Spark 1.x-Cluster aus.

   c. Der Scala-Projekterstellungsassistent füllt die Dropdownliste **Spark version** (Spark-Version) mit der richtigen Version für das Spark SDK und das Scala SDK auf. Wenn Sie eine ältere Spark-Clusterversion als 2.0 verwenden, wählen Sie **Spark 1.x** aus. Wählen Sie andernfalls **Spark 2.x** aus. In diesem Beispiel wird **Spark 2.0.2 (Scala 2.11.8)** verwendet.

6. Wählen Sie **Fertig stellen** aus.

7. Das Spark-Projekt erstellt automatisch ein Artefakt. Führen Sie die folgenden Schritte aus, um sich das Artefakt anzeigen zu lassen:

   a. Klicken Sie im Menü **File** (Datei) auf **Project Structure** (Projektstruktur).

   b. Klicken Sie im Dialogfeld **Project Structure** (Projektstruktur) auf **Artifacts** (Artefakte), um sich das erstellte Standardartefakt anzeigen zu lassen. Sie können auch ein eigenes Artefakt erstellen, indem Sie auf das Pluszeichen ( **+** ) klicken.

      ![Artefaktinformationen im Dialogfeld](./media/spark-submit-job-intellij-tool-plugin/default-artifact.png)
      

## <a name="submit-application-to-sql-server-big-data-cluster"></a>Übermitteln der Anwendung an den Big-Data-Cluster für SQL Server
Nachdem Sie einen Big-Data-Cluster für SQL Server verknüpft haben, können Sie eine Anwendung an diesen übermitteln.

1. Nehmen Sie die Konfiguration im Fenster **Run/Debug Configurations** (Ausführen/Debugkonfigurationen) vor. Klicken Sie auf das Pluszeichen und anschließend auf **Apache Spark on SQL Server** (Apache Spark in SQL Server). Klicken Sie dann auf die Registerkarte **Remotely Run in Cluster** (Remoteausführung in Cluster), legen Sie die unten gezeigten Parameter fest, und klicken Sie auf OK.

    ![Interaktive Konsole: Hinzufügen eines Konfigurationseintrags](./media/spark-submit-job-intellij-tool-plugin/interactive-console-add-config-entry.png)

    ![Verknüpfen des Big-Data-Clusters: Konfiguration](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-config.png)

    * Wählen Sie für **Spark clusters (Linux only)** (Spark-Cluster (nur Linux)) den Cluster aus, auf dem Sie die Anwendung ausführen möchten.

    * Wählen Sie ein Artefakt aus, das sich im IntelliJ-Projekt oder auf der Festplatte befindet.

    * Feld **Main class name** (Name der Hauptklasse): Der Standardwert ist die Hauptklasse der ausgewählten Datei. Sie können eine andere Klasse auswählen, indem Sie auf die Schaltfläche mit den Auslassungspunkten ( **…** ) klicken.   

    * Feld **Job Configurations** (Auftragskonfigurationen):  Die Standardwerte sind auf dem obigen Screenshot abgebildet. Sie können für die Auftragsübermittlung die Werte ändern oder neue Schlüssel-Wert-Paare hinzufügen. Weitere Informationen finden Sie unter: [Apache Livy-REST-API](http://livy.incubator.apache.org./docs/latest/rest-api.html)

      ![Dialogfeld mit Übersicht über Auftragskonfigurationen zur Übermittlung von Spark-Aufträgen](./media/spark-submit-job-intellij-tool-plugin/submit-job-configurations.png)

    * Feld **Command line arguments** (Befehlszeilenargumente): Sie können bei Bedarf die Argumente getrennt durch Leerzeichen für die Hauptklasse eingeben.

    * Felder **Referenced Jars** (Verweise auf JAR-Dateien) und **Referenced Files** (Verweise auf Dateien): Sie können bei Bedarf die Pfade für die JAR-Dateien und für die anderen Dateien eingeben, auf die verwiesen wird. Weitere Informationen finden Sie unter: [Apache Spark-Konfiguration](https://spark.apache.org/docs/latest/configuration.html#runtime-environment) 

      ![Dialogfeld mit Übersicht über (JAR-)Dateien zur Übermittlung von Spark-Aufträgen](./media/spark-submit-job-intellij-tool-plugin/jar-files-meaning.png)

       > [!NOTE]  
       > Informationen zum Hochladen von JAR-Dateien und anderen Dateien, auf die verwiesen wird, finden Sie unter: [Hochladen von Ressourcen auf den Cluster](/azure/storage/blobs/storage-quickstart-blobs-storage-explorer).
                         
    * **Upload Path** (Uploadpfad): Sie können den Speicherort für die Übermittlung von JAR- oder Scala-Projektressourcen angeben. Es werden mehrere Speichertypen unterstützt: **Use Spark interactive session to upload** (Interaktive Spark-Sitzung für Upload verwenden) und **Use WebHDFS to upload** (WebHDFS für Upload verwenden).
    
2. Klicken Sie auf **SparkJobRun** (Spark-Auftrag ausführen), um das Projekt an den ausgewählten Cluster zu übermitteln. Auf der Registerkarte **Remote Spark Job in Cluster** (Remote-Spark-Auftrag auf Cluster) wird im unteren Bereich der Fortschritt der Auftragsausführung angezeigt. Sie können die Anwendung anhalten, indem Sie auf die rote Schaltfläche klicken.  

    ![Verknüpfen des Big-Data-Clusters: Ausführung](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-run.png)

## <a name="spark-console"></a>Spark-Konsole
Sie können „Spark Local Console(Scala)“ (Lokale Spark-Konsole (Scala)) oder „Spark Livy Interactive Session Console(Scala)“ (Spark-Livy-Konsole für interaktive Sitzungen) ausführen.

### <a name="spark-local-consolescala"></a>Spark Local Console(Scala)
Stellen Sie sicher, dass die Voraussetzungen von „WINUTILS.exe“ erfüllt sind.

1. Navigieren Sie in der Menüleiste zu **Run** (Ausführen) > **Edit Configurations...** (Konfigurationen bearbeiten…).

2. Navigieren Sie im Fenster **Run/Debug Configurations** (Ausführen/Debugkonfigurationen) im linken Bereich zu **Apache Spark on SQL Server big data cluster** (Apache Spark auf einem Big-Data-Cluster für SQL Server) >  **[Spark on SQL] myApp** ([Spark in SQL] meineApp).

3. Klicken Sie im Hauptfenster auf die Registerkarte **Locally Run** (Lokal ausführen).

4. Geben Sie die folgenden Werte an, und klicken Sie anschließend auf **OK**:

    |Eigenschaft |Wert |
    |----|----|
    |„Job main class“ (Hauptklasse des Auftrags)|Der Standardwert ist die Hauptklasse der ausgewählten Datei. Sie können eine andere Klasse auswählen, indem Sie auf die Schaltfläche mit den Auslassungspunkten ( **…** ) klicken.|
    |Umgebungsvariablen|Stellen Sie sicher, dass für HADOOP_HOME der richtige Wert festgelegt ist.|
    |„WINUTILS.exe location“ (Speicherort von „WINUTILS.exe“)|Stellen Sie sicher, dass der richtige Pfad festgelegt ist.|

    ![Konfigurieren der lokalen Konsole](./media/spark-submit-job-intellij-tool-plugin/console-set-configuration.png)

5. Navigieren Sie in „Project“ (Projekt) zu **myApp** > **src** > **main** > **scala** > **myApp**.  

6. Navigieren Sie in der Menüleiste zu **Tools** > **Spark Console (Spark-Konsole)**  > **Run Spark Local Console(Scala)** (Lokale Spark-Konsole ausführen (Scala)).

7. Zwei Dialogfelder werden möglicherweise angezeigt, in denen Sie gefragt werden, ob Probleme mit Abhängigkeiten automatisch behoben werden sollen. Klicken Sie ggf. auf **Auto Fix** (Automatisch beheben).

    ![Automatische Problembehebung in Spark (1)](./media/spark-submit-job-intellij-tool-plugin/console-auto-fix1.png)

    ![Automatische Problembehebung in Spark (2)](./media/spark-submit-job-intellij-tool-plugin/console-auto-fix2.png)

8. Die Konsole sollte in etwa wie auf dem folgenden Screenshot aussehen. Geben Sie im Konsolenfenster `sc.appName` ein, und drücken Sie STRG+EINGABETASTE.  Das Ergebnis wird angezeigt. Sie können die lokale Konsole beenden, indem Sie auf die rote Schaltfläche klicken.

    ![Ergebnis in der lokalen Konsole](./media/spark-submit-job-intellij-tool-plugin/local-console-result.png)


### <a name="spark-livy-interactive-session-consolescala"></a>Spark Livy Interactive Session Console (Scala)
Spark Livy Interactive Session Console(Scala) wird nur für IntelliJ 2018.2 und 2018.3 unterstützt.

1. Navigieren Sie in der Menüleiste zu **Run** (Ausführen) > **Edit Configurations...** (Konfigurationen bearbeiten…).

2. Navigieren Sie im Fenster **Run/Debug Configurations** (Ausführen/Debugkonfigurationen) im linken Bereich zu **Apache Spark on SQL Server big data cluster** (Apache Spark auf einem Big-Data-Cluster für SQL Server) >  **[Spark on SQL] myApp** ([Spark in SQL] meineApp).

3. Klicken Sie im Hauptfenster auf die Registerkarte **Remotely Run in Cluster** (Remoteausführung in Cluster).

4. Geben Sie die folgenden Werte an, und klicken Sie anschließend auf **OK**:

    |Eigenschaft |Wert |
    |----|----|
    |„Spark clusters (Linux only)“ (Spark-Cluster (nur Linux))|Wählen Sie den Big-Data-Cluster für SQL Server aus, auf dem Sie Ihre Anwendung ausführen möchten.|
    |„Main class name“ (Name der Hauptklasse)|Der Standardwert ist die Hauptklasse der ausgewählten Datei. Sie können eine andere Klasse auswählen, indem Sie auf die Schaltfläche mit den Auslassungspunkten ( **…** ) klicken.|

    ![Konfigurieren der interaktiven Konsole](./media/spark-submit-job-intellij-tool-plugin/interactive-console-configuration.png)

5. Navigieren Sie in „Project“ (Projekt) zu **myApp** > **src** > **main** > **scala** > **myApp**.  

6. Navigieren Sie in der Menüleiste zu **Tools** > **Spark Console (Spark-Konsole)**  > **Run Spark Livy Interactive Session Console(Scala)** (Spark-Livy-Konsole für interaktive Sitzungen ausführen).

7. Die Konsole sollte in etwa wie auf dem folgenden Screenshot aussehen. Geben Sie im Konsolenfenster `sc.appName` ein, und drücken Sie STRG+EINGABETASTE.  Das Ergebnis wird angezeigt. Sie können die lokale Konsole beenden, indem Sie auf die rote Schaltfläche klicken.

    ![Ergebnis in der interaktiven Konsole](./media/spark-submit-job-intellij-tool-plugin/interactive-console-result.png)

### <a name="send-selection-to-spark-console"></a>Senden einer Auswahl an die Spark-Konsole

Sie können sich ganz einfach die Ergebnisse eines Skripts ansehen, indem Sie Code an die lokale Konsole oder an die Livy-Konsole für interaktive Sitzungen senden. Markieren Sie dazu Code in der Scala-Datei, und klicken Sie mit der rechten Maustaste auf **Send Selection To Spark Console** (Auswahl an Spark-Konsole senden). Der ausgewählte Code wird an die Konsole gesendet und ausgeführt. Das Ergebnis wird nach dem Code in der Konsole angezeigt. Die Konsole überprüft, ob Fehler vorliegen.  

   ![Senden einer Auswahl an die Spark-Konsole](./media/spark-submit-job-intellij-tool-plugin/send-selection-to-console.png)

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu Big Data-Clustern für SQL Server und zugehörigen Szenarios finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)