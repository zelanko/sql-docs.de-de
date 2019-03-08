---
title: Ausführen von Spark-Aufträgen in Azure Data Studio
titleSuffix: SQL Server 2019 big data clusters
description: Übermitteln von Spark-Aufträgen in SQL Server-big Data-Clustern in Azure Data Studio an.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c1d439c13b06b305c814813eeca7cb9bf8aa53c5
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2019
ms.locfileid: "57578240"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-clusters-in-azure-data-studio"></a>Übermitteln von Spark-Aufträgen in SQL Server-big Data-Clustern in Azure Data Studio

Eines der Hauptszenarien für big Data-Cluster ist die Möglichkeit zum Übermitteln von Spark-Aufträgen für die Vorschau von SQL Server-2019. Die Spark Job Submission-Funktion können Sie eine lokale JAR- oder Py-Dateien mit Verweisen auf SQL Server-2019 big Data-Cluster zu übermitteln. Darüber hinaus können Sie zum Ausführen von einer JAR-Datei oder Py-Dateien, die sich bereits in das HDFS-Dateisystem befinden. 

## <a name="prerequisites"></a>Erforderliche Komponenten

- [SQL Server-2019 big Data-Tools](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **SQL Server-2019-Erweiterung**
   - **kubectl**

- [Herstellen einer Verbindung des Gateways HDFS/Spark Ihrer big Data-Cluster mit Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="open-spark-job-submission-dialog"></a>Öffnen des Dialogfelds "Senden" der Spark-Auftrag
Es gibt mehrere Methoden zum Öffnen des Dialogfelds "Senden" der Spark-Auftrag. Die Methoden enthalten Dashboards, wählen Sie im Objekt-Explorer, und die Palette der Befehl im Kontextmenü.

+ Klicken Sie auf **neue Spark-Auftrag** im Dashboard, um das Dialogfeld "Spark Job Submission" zu öffnen.

    ![Übermitteln Sie im Menü durch Klicken auf dashboard](./media/submit-spark-job/new-spark-job.png)
 
+ Mit der rechten Maustaste auf den Cluster im Objekt-Explorer, und wählen Sie **Submit Spark Job** aus dem Kontextmenü. Spark-Auftrag-Dialogfelds "Senden" wird geöffnet.  
 
    ![Menü mit der rechten Maustaste-Cluster übermitteln](./media/submit-spark-job/submit-spark-job.png)

+ Mit der rechten Maustaste auf eine JAR-Datei/Py-Datei im Objekt-Explorer, und wählen Sie **Submit Spark Job** aus dem Kontextmenü. Spark Job Submission Dialog durch die JAR-Datei/Py-Feld, das ausgefüllt wird geöffnet. 
 
    ![Übermitteln Sie im Menü mit der rechten Maustaste-Datei](./media/submit-spark-job/submit-spark-job-2.png)

+ Verwenden Sie Befehl **Submit Spark Job** über die befehlspalette, indem Sie STRG + UMSCHALT + P (in Windows) und Cmd + UMSCHALT + P (in Mac) eingeben.

    ![Übermitteln Sie die befehlspalette den Befehl im Menü in windows](./media/submit-spark-job/submit-spark-job-3.png)

    ![Übermitteln Sie die befehlspalette den Befehl im Menü unter mac](./media/submit-spark-job/submit-spark-job-4.png)
  
 
## <a name="submit-spark-job"></a>Übermitteln von Spark-Auftrag 
Das Dialogfeld "Spark Job Submission" wird wie folgt angezeigt. Geben Sie ein Auftragsname, Pfad der JAR-Datei/Py-Datei, main-Klasse und anderen Feldern. Die JAR-Datei / der Quelle der Py-Datei ist möglicherweise aus lokalen oder aus einem HDFS. Wenn die Spark-Auftrags JAR-Dateien, Py-Dateien oder zusätzliche Dateien verweisen, klicken Sie auf **erweitert** Registerkarte, und geben Sie die entsprechenden Dateipfade. Klicken Sie auf **senden** zum Übermitteln von Spark-Auftrag.
 
![Dialogfeld "neue Spark-Auftrag"](./media/submit-spark-job/submit-spark-job-section.png)

![Dialogfeld "Erweitert"](./media/submit-spark-job/submit-spark-job-section-1.png)

## <a name="monitor-spark-job-submission"></a>Überwachen von Spark-Auftragsübermittlung
Nachdem der Spark-Auftrag übermittelt wurde, werden Statusinformationen für den Spark-Auftrag Übermittlung und die Ausführung im Task-Verlauf auf der linken Seite angezeigt. Und Informationen zu den Fortschritt und die Protokolle werden ebenfalls angezeigt, der **Ausgabe** Fenster am unteren Rand.
+ Bei der Spark-Auftrag ausgeführt wird, wird die **Taskverlauf** Bereich und **Ausgabe** Fenster werden mit dem Status aktualisiert.

![Überwachen von Spark-Auftrags in Bearbeitung](./media/submit-spark-job/monitor-spark-job-submission.png)

+ Wenn Spark-Auftrag wird erfolgreich abgeschlossen ist, sehen Sie Links von Spark-Benutzeroberfläche und die Yarn-Benutzeroberfläche in der **Ausgabe** Fenster. Sie können die Links, um weitere Informationen klicken.

![Spark-Auftrag-Link in der Ausgabe](./media/submit-spark-job/monitor-spark-job-submission-2.png)

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu SQL Server-big Data-Cluster und die zugehörigen Szenarien, finden Sie unter [neuerungen von SQL Server-big Data-Cluster](big-data-cluster-overview.md)?

