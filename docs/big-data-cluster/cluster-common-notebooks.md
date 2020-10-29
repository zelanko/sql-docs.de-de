---
title: 'Häufiges Szenario: Arbeiten mit Big Data-Clustern (BDC) mit Jupyter-Notebooks und Azure Data Studio'
titleSuffix: SQL Server Big Data Clusters
description: 'Häufiges Szenario: Arbeiten mit BDC mit Jupyter-Notebooks und Azure Data Studio in einem SQL Server 2019 Big Data-Cluster.'
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 09/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 99e62be597e4ce08d38db199116f1bd4d5ab33f6
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92378427"
---
# <a name="common-notebooks-for-sql-server-big-data-clusters"></a>Allgemeine Notebooks für SQL Server-Big Data-Cluster

In diesem Artikel sind Notebooks für SQL Server-Big Data-Cluster aufgeführt. Die ausführbaren Notebooks (.ipynb) sind für SQL Server 2019 entwickelt, um beim Darstellen von häufigen Szenarien für Big Data-Cluster zu helfen.

Jedes Notebook überprüft seine eigenen Abhängigkeiten. Eine **Alle Zellen ausführen** -Option (run all cells) wird entweder erfolgreich abgeschlossen oder löst eine Ausnahme aus, die einen *Hinweis* mit einem Link zu einem anderen Notebook enthält, um die fehlende Abhängigkeit aufzulösen. Folgen Sie dem Link im Hinweis zu dem folgenden Notebook, klicken Sie auf **run all cells** , und wenn die Aktion erfolgreich ist, kehren Sie zum ursprünglichen Notebook zurück, und führen Sie **run all cells** aus.

Wenn alle Abhängigkeiten installiert wurden, **run all cells** aber fehlschlägt, analysiert jedes Notebook die Ergebnisse und erzeugt, wo möglich, einen Hinweis mit Link zu einem weiteren Notebook, um bei der weitergehenden Behandlung des Problems zu helfen.

## <a name="gathering-logs-from-big-data-cluster-bdc"></a>Sammeln von Protokollen von einem Big Data-Cluster (BDC)

Die Notebooks in diesem Abschnitt sind Voraussetzung für weitere Notebooks, die beispielsweise dazu verwendet werden, sich bei einem Cluster an- oder abzumelden.

|Name |Beschreibung |
|---|---|
|SOP005: az login|Verwenden Sie die Befehlszeilenschnittstelle az, um sich bei Azure anzumelden. |
|SOP006 – az logout|Verwenden Sie die Befehlszeilenschnittstelle az, um sich bei Azure abzumelden.|
|SOP007: Versionsinformationen (azdata, BDC, Kubernetes)|Definieren Sie Hilfsfunktionen, die im Notebook für Versionsverwaltungsinformationen verwendet werden.|
|SOP011: Festlegen des Kubernetes-Konfigurationskontexts|Legen Sie die Kubernetes-Konfiguration fest, die verwendet werden soll. |
|SOP028: azdata login|Verwenden Sie die Befehlszeilenschnittstelle azdata, um sich bei einem Big-Data-Cluster anzumelden. |
|SOP033: azdata logout|Verwenden Sie die Befehlszeilenschnittstelle azdata, um sich von einem Big-Data-Cluster abzumelden. |
|SOP034: Auf Fehlerfreiheit von BDC warten|Blockiert, bis der Big Data-Cluster fehlerfrei oder das angegebene Timeout abgelaufen ist. Der „min_pod_count“-Parameter bestimmt, dass die Integritätsprüfung erst bestanden wird, wenn mindestens diese Anzahl von Pods im Cluster vorhanden ist. Sind vorhandene Pods jenseits dieses Grenzwerts fehlerhaft, ist der Cluster nicht fehlerfrei.|
|OPR001: Erstellen einer App-Bereitstellung (App-Deploy)|Verwenden Sie dieses Notebook, um eine App in einem Big Data-Cluster zu erstellen. |
|OPR002: Ausführen einer App-Bereitstellung (App-Deploy)|Verwenden Sie dieses Notebook, um eine App in einem Big Data-Cluster auszuführen. |
|OPR003: Erstellen eines Cron-Auftrags|Verwenden Sie dieses Notebook, um einen Cron-Auftrag in einem Big Data-Cluster zu erstellen. |
|OPR004: Anhalten eines Cron-Auftrags|Verwenden Sie dieses Notebook, um einen Cron-Auftrag in einem Big Data-Cluster anzuhalten. |
|OPR005: Fortsetzen eines Cron-Auftrags|Verwenden Sie dieses Notebook, um einen Cron-Auftrag in einem Big Data-Cluster fortzusetzen. |
|OPR006: Löschen eines Cron-Auftrags|Verwenden Sie dieses Notebook, um einen Cron-Auftrag in einem Big Data-Cluster zu löschen. |
|OPR007: Löschen einer App-Bereitstellung|Verwenden Sie dieses Notebook, um eine App in einem Big Data-Cluster zu löschen. |
|OPR100: Bereitstellen und Planen von Notebooks|Verwenden Sie dieses Notebook, um eine Liste von Notebooks für einen App-Deploy-Pod bereitzustellen, die App-Deploy gemäß einem Zeitplan mit einem Kubernetes-Cron-Auftrag auszuführen und ein Grafana-Dashboard zu installieren, um Ergebnisse anzuzeigen.|
|OPR600: Überwachen der Infrastruktur (Kubernetes)|Verwenden Sie dieses Notebook, um die Infrastruktur zu überwachen.|
|OPR700: Erstellen eines Grafana-Dashboards für App-Deploy-Anwendungen|Verwenden Sie dieses Notebook, um in Grafana ein Dashboard zu erstellen, um App-Deploy-Ergebnisse zu überwachen und Warnungen zu generieren, wenn ein Canary oder eine Anwendung ausfällt.|
|OPR900: Problembehandlung beim Ausführen von App-Deploy|Verwenden Sie dieses Notebook, um das App-Deploy-Skript direkt im Container (mit kubectl exec) auszuführen. Damit können weitere Debuginformationen zur Problembehandlung bereitgestellt werden, insbesondere im Zusammenhang mit Problemen in der Startphase des Skripts.|
|OPR901: Problembehandlung für einen Cron-Auftrag|Verwenden Sie dieses Notebook, um das cronjob-Skript direkt im Container (mit kubectl exec) auszuführen. Damit können weitere Debuginformationen zur Problembehandlung bereitgestellt werden.|


## <a name="analyze-logs-from-big-data-clusters-bdc"></a>Analysieren von Protokollen von Big Data-Clustern (BDC)

Beispiel-Notebooks, die Big-Data-Cluster-Szenarios in SQL Server demonstrieren.

|Name |Beschreibung |
|---|---|
|SAM001a: Abfragen des Speicherpools aus dem SQL Server-Masterpool (1 von 3): Laden von Beispieldaten|In diesem dreiteiligen Tutorial laden Sie Daten über azdata in den Speicherpool (HDFS), konvertieren Sie die Daten in Parquet (mit Spark), und fragen Sie im dritten Teil die Daten mit dem Masterpool (SQL Server) ab. |
|SAM001b: Abfragen des Speicherpools aus dem SQL Server-Masterpool (2 von 3): Konvertieren der Daten in Parquet|In diesem zweiten Teil des dreiteiligen Tutorials verwenden Sie Spark, um eine CSV-Datei in eine Parquet-Datei zu konvertieren.|
|SAM001c: Abfragen des Speicherpools aus dem SQL Server-Masterpool (3 von 3): Abfragen von HDFS aus SQL Server|In diesem dritten Teil des Speicherpool-Tutorials erfahren Sie, wie Sie eine externe Tabelle erstellen, die auf HDFS-Daten in einem Big Data-Cluster verweist, und diese Daten mit hochwertigen Daten in der Masterinstanz verknüpfen.|
|SAM002: Speicherpool (2 von 2): Abfragen von HDFS-Daten|In diesem zweiten Teil des Speicherpool-Tutorials erfahren Sie, wie Sie eine externe Tabelle erstellen, die auf HDFS-Daten in einem Big Data-Cluster verweist, und diese Daten mit hochwertigen Daten in der Masterinstanz verknüpfen.|
|SAM003: Beispiel zu Datenpools|In diesem Tutorial erfahren Sie, wie Sie eine Datenpoolquelle und eine externe Tabelle im Datenpool erstellen, anschließend Daten in die Datenpooltabellen einfügen und Daten aus einer Datenpooltabelle in eine andere laden. Verknüpfen Sie Daten in der Datenpooltabelle mit anderen Datenpooltabellen, außerdem Abschneiden (truncate) von Tabellen und Bereinigung. |
|SAM004: Virtualisieren von MongoDB-Daten|Wenn Sie Daten aus einer externen MongoDB-Datenquelle abrufen möchten, müssen Sie externe Tabellen erstellen, um auf diese Daten verweisen zu können. Dieser Abschnitt enthält Beispielcode zum Erstellen dieser externen Tabellen.|
|SAM005: Virtualisieren von Oracle-Daten|Wenn Sie Daten aus einer externen Oracle-Datenquelle abrufen möchten, müssen Sie externe Tabellen erstellen, um auf diese Daten verweisen zu können. Dieser Abschnitt enthält Beispielcode zum Erstellen dieser externen Tabellen.|
|SAM006: Virtualisieren von SQL Server-Daten|Wenn Sie Daten virtuell aus einer anderen SQL Server-Datenquelle abrufen möchten, müssen Sie externe Tabellen erstellen, um auf diese Daten verweisen zu können. Dieser Abschnitt enthält Beispielcode zum Erstellen dieser externen Tabellen.|
|SAM007: Virtualisieren von Teradata-Daten|Wenn Sie Daten aus einer externen Teradata-Datenquelle abrufen möchten, müssen Sie externe Tabellen erstellen, um auf diese Daten verweisen zu können. Dieser Abschnitt enthält Beispielcode zum Erstellen dieser externen Tabellen.|
|SAM008: Spark mit azdata|azdata- und kubectl-Befehle zum Arbeiten mit Spark-Sitzungen.|
|SAM009: HDFS mit azdata|azdata- und kubectl-Befehle zum Arbeiten mit HDFS.|
|SAM010: App mit azdata|azdata- und kubectl-Befehle zum Arbeiten mit App-Bereitstellung (App-Deploy). |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
