---
title: Übermitteln von Spark-Aufträgen an Big Data-Cluster von SQL Server in Azure Data Studio
titleSuffix: SQL Server big data clusters
description: Übermitteln von Spark-Aufträgen an Big Data-Cluster von SQL Server in Azure Data Studio.
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6731a753c643512cd05dbc9d7b7de2c9a064576f
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68470665"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-clusters-in-azure-data-studio"></a>Übermitteln von Spark-Aufträgen an Big Data-Cluster von SQL Server in Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Eines der Hauptszenarios für Big Data-Cluster besteht darin, dass Spark-Aufträge für SQL Server 2019 (Vorschauversion) an diese übermittelt werden können. Mit dem Feature zum Übermitteln von Spark-Aufträgen können Sie lokale JAR- oder PY-Dateien mit Verweisen auf Big Data-Cluster für SQL Server 2019 übermitteln. Außerdem können Sie JAR- oder PY-Dateien ausführen, die sich bereits auf dem HDFS-Dateisystem befinden. 

## <a name="prerequisites"></a>Voraussetzungen

- [Big Data-Tools für SQL Server 2019](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **Erweiterung von SQL Server 2019**
   - **kubectl**

- [Stellen Sie eine Verbindung von Azure Data Studio mit dem HDFS/Spark-Gateway Ihres Big Data-Clusters her](connect-to-big-data-cluster.md).

## <a name="open-spark-job-submission-dialog"></a>Öffnen des Dialogfelds zum Übermitteln von Spark-Aufträgen

Es gibt mehrere Möglichkeiten zum Öffnen des Dialogfelds zum Übermitteln von Spark-Aufträgen. Zu den Möglichkeiten zählen das Dashboard, das Kontextmenü im Objekt-Explorer und die Befehlspalette.

- Klicken Sie zum Öffnen des Dialogfelds zum Übermitteln von Spark-Aufträgen im Dashboard auf **Neuer Spark-Auftrag**.

    ![Übermittlungsmenü bei Klicken auf Dashboard](./media/submit-spark-job/new-spark-job.png)

- Klicken Sie alternativ im Objekt-Explorer mit der rechten Maustaste auf den Cluster, und wählen Sie im Kontextmenü **Spark-Auftrag übermitteln** aus.

    ![Übermittlungsmenü bei Klicken auf eine Datei mit der rechten Maustaste](./media/submit-spark-job/submit-spark-job-1.png)


- Um das Dialogfeld zum Übermitteln von Spark-Aufträgen vorab mit den JAR/PY-Feldern zu füllen, klicken Sie mit der rechten Maustaste im Objekt-Explorer auf eine JAR/PY-Datei, und wählen Sie im Kontextmenü **Spark-Auftrag übermitteln** aus.  

    ![Übermittlungsmenü bei Klicken auf einen Cluster mit der rechten Maustaste](./media/submit-spark-job/submit-spark-job.png)

- Verwenden Sie **Spark-Auftrag übermitteln** aus der Befehlspalette, indem Sie **STRG+UMSCHALTTASTE+P** (unter Windows) oder **BEFEHLSTASTE+UMSCHALTTASTE+P** (unter Mac) drücken.

    ![Übermittlungsmenü-Befehlspalette in Windows](./media/submit-spark-job/submit-spark-job-3.png)

    ![Übermittlungsmenü-Befehlspalette in Mac](./media/submit-spark-job/submit-spark-job-4.png)
  
 
## <a name="submit-spark-job"></a>Übermitteln von Spark-Aufträgen 

Das Dialogfeld für die Übermittlung von Spark-Aufträgen wird wie folgt angezeigt. Geben Sie den Auftragsnamen, den JAR/PY-Dateipfad, die Hauptklasse und andere Felder ein. Die JAR/PY-Dateiquelle kann lokal sein oder sich im HDFS befinden. Wenn der Spark-Auftrag JAR-, PY- oder weitere Referenzdateien aufweist, klicken Sie auf die Registerkarte **ERWEITERT**, und geben Sie die entsprechenden Dateipfade ein. Klicken Sie zum Übermitteln des Spark-Auftrags auf **Übermitteln**.

![Dialog für neuen Spark-Auftrag](./media/submit-spark-job/submit-spark-job-section.png)

![Dialogfeld „Erweitert“](./media/submit-spark-job/submit-spark-job-section-1.png)

## <a name="monitor-spark-job-submission"></a>Überwachen der Übermittlung von Spark-Aufträgen

Nachdem der Spark-Auftrag übermittelt wurde, werden die Informationen zur Übermittlung und zum Ausführungsstatus des Spark-Auftrags im „Aufgabenverlauf“ auf der linken Seite angezeigt. Details zum Fortschritt und zu Protokollen werden ebenfalls im Fenster **AUSGABE** unten angezeigt.

- Wenn der Spark-Auftrag ausgeführt wird, werden der Bereich **Aufgabenverlauf** und das Fenster **AUSGABE** mit dem Fortschritt aktualisiert.

    ![Überwachen des Spark-Auftrags bei der Ausführung](./media/submit-spark-job/monitor-spark-job-submission.png)

- Nachdem der Spark-Auftrag erfolgreich abgeschlossen wurde, werden die Links zur Spark- und Yarn-Benutzeroberfläche im Fenster **AUSGABE** angezeigt. Klicken Sie auf die Links, um weitere Informationen zu erhalten.

    ![Spark-Auftragslink in der Ausgabe](./media/submit-spark-job/monitor-spark-job-submission-2.png)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum SQL Server-Cluster für Big Data und den entsprechenden Szenarios finden Sie unter [Was sind SQL Server-Cluster für Big Data?](big-data-cluster-overview.md).