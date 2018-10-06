---
title: Was ist SQL Server-2019 big Data-Cluster? | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: overview
ms.prod: sql
ms.openlocfilehash: cf13ea198a5a40a5d67d41fea2f8f9b9b3b5434d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796417"
---
# <a name="what-is-sql-server-2019-big-data-clusters"></a>Was ist SQL Server-2019 big Data-Cluster?

Beginnend mit [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)], SQL Server-big Data-Cluster bieten die Möglichkeit zum Bereitstellen von skalierbarer Clusters von SQL Server, Spark und HDFS-Docker-Containern, die auf Kubernetes ausgeführt wird. Diese Komponenten werden parallel ausgeführt, um ermöglichen es Ihnen, lesen, schreiben und Verarbeiten von big Data aus Transact-SQL oder Spark. SQL Server-big Data-Cluster können Sie auf einfache Weise kombinieren und analysieren Sie Ihre wertvollen relationale Daten mit hohem Volumen, big Data.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="scenarios"></a>Szenarien

SQL Server-big Data-Cluster bieten die Flexibilität bei der Interaktion mit Ihrer big Data. Sie können Daten aus externen Quellen Abfragen, speichern Sie big Data in HDFS, die von SQL Server oder Pull Daten aus mehreren Datenquellen, die in den Cluster verwaltet werden. Sie können dann die Daten für künstliche Intelligenz, Machine Learning und andere Analyseaufgaben verwenden. Die folgenden Abschnitte enthalten weitere Informationen zu diesen Szenarien.

### <a name="data-virtualization"></a>Data virtualization

Durch die Nutzung [SQL Server PolyBase](../relational-databases/polybase/polybase-guide.md), SQL Server-big Data-Cluster können Daten aus externen Quellen Abfragen, ohne dass die Daten importiert. [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] führt neue Connectors zu Datenquellen.

![Data virtualization](media/big-data-cluster-overview/data-virtualization.png)

### <a name="data-lake"></a>Data lake

Eine SQL Server-big Data-Cluster enthält einen skalierbaren HDFS *Speicherpool*. Dies kann zum Speichern von big Data und möglicherweise über mehrere externe Quellen erfasst direkt verwendet werden. Einmal in der big Data-Cluster können Sie analysieren und die Daten abzufragen und mit Ihren relationalen Daten mit hohem Wert kombinieren.

![Data lake](media/big-data-cluster-overview/data-lake.png)

### <a name="scale-out-data-mart"></a>Scale-Out-Datamart

SQL Server-big Data-Cluster bieten die horizontale Skalierung von COMPUTE- und zur Verbesserung der Leistung der Analyse von Daten. Daten aus einer Vielzahl von Quellen erfasst und verteilt werden können, *Datenpool* Knoten zur weiteren Analyse.

![Datamart](media/big-data-cluster-overview/data-mart.png)

### <a name="integrated-ai-and-machine-learning"></a>Integrierte künstliche Intelligenz und Machine Learning

SQL Server-big Data-Cluster aktivieren, künstliche Intelligenz und Machine learning-Aufgaben für die Daten in Data HDFS-Speicherpools und der Datenpools. Sie können Spark sowie der integrierten KI-Tools in SQL Server mithilfe von R, Python oder Java verwenden.

![AI und ML](media/big-data-cluster-overview/ai-ml-spark.png)

### <a name="management-and-monitoring"></a>Verwaltung und Überwachung

Verwaltung und Überwachung werden durch eine Kombination aus Open Source-Komponenten, SQL Server-Tools und dynamischen Verwaltungssichten bereitgestellt.

Die [Cluster Admin Portal](cluster-admin-portal.md) ist eine Weboberfläche, in dem Status und Integrität der Pods im Cluster angezeigt. Darüber hinaus Links zu anderen Dashboards von Grafana und Kibana bereitgestellt werden.

Azure Data Studio können eine Vielzahl von Aufgaben für die big Data-Cluster ausführen. Dies erfolgt durch die neue **2019-Erweiterung für SQL Server (Vorschau)**. Diese Erweiterung bietet:

- Integrierten Codeausschnitte für allgemeine Verwaltungsaufgaben.
- Meldet die Anzahl der computepools und den Status der ausgeführten Aufträge.
- Berichte zum Status von HDFS und Spark-Aufträge.
- Möglichkeit zum Durchsuchen von HDFS, Hochladen von Dateien, Dateien und Verzeichnisse erstellen.
- Möglichkeit zum Erstellen, öffnen, und führen die kompatiblen Jupyter-Notebooks.
- Data Virtualization Assistenten, um die Erstellung von Daten aus externen Quellen zu vereinfachen.

## <a id="architecture"></a> Architektur

Eine SQL Server-big Data-Cluster ist ein Cluster mit Linux-Knoten, die von orchestriert [Kubernetes](https://kubernetes.io/docs/concepts/).

### <a name="kubernetes-concepts"></a>Kubernetes-Konzepte

Kubernetes ist ein open-Source-containerorchestrator, die containerbereitstellungen je nach Anforderungen skaliert werden kann. In der folgende Tabelle werden einige wichtige Begriffe für Kubernetes definiert:

|||
|--|--|
| **Cluster** | Ein Kubernetes-Cluster ist eine Gruppe von Computern, die als Knoten bezeichnet. Ein Knoten den Cluster steuert und ist den Masterknoten festgelegt; die verbleibenden Knoten sind Worker-Knoten. Der Kubernetes-Master ist verantwortlich für die Verteilung von Arbeit zwischen den Workern sicherzustellen und für die Überwachung der Integrität des Clusters. |
| **Node** | Ein Knoten wird die Anwendungen in Containern ausgeführt. Es kann entweder auf einem physischen Computer oder auf einem virtuellen Computer sein. Ein Kubernetes-Cluster kann es sich um eine Mischung aus physischen Computer und VM-Knoten enthalten. |
| **Pod** | Ein Pod-Typ ist die unteilbare Einheit von Kubernetes. Ein Pod-Typ ist eine logische Gruppe von einem oder mehreren Containern – und die zugehörigen Ressourcen – zum Ausführen einer Anwendung erforderlich sind. Jedem Pod auf einem Knoten ausgeführt wird; ein Knoten kann einem oder mehreren Pods ausgeführt. Der Kubernetes-Master wird der Knoten im Cluster automatisch Pods zugewiesen. |

In SQL Server-big Data-Cluster ist Kubernetes verantwortlich für den Status der SQL Server-big Data-Cluster. Kubernetes erstellt und konfiguriert die Clusterknoten, weist der Pods zu Knoten und überwacht die Integrität des Clusters.

### <a name="big-data-clusters-architecture"></a>Big Data-Cluster-Architektur

Knoten im Cluster werden in drei logische Ebenen angeordnet: die Steuerungsebene, die Compute-Bereich und die Datenebene. Jede Ebene hat verschiedene Aufgaben im Cluster. Alle Kubernetes-Knoten in einer SQL Server-big Data-Cluster mindestens eine Ebene gehört.

![Übersicht über die Architektur](media/big-data-cluster-overview/architecture-diagram-planes.png)

### <a id="controlplane"></a> Steuerungsebene

Die Steuerungsebene ermöglicht eine Verwaltung und Sicherheit für den Cluster. Es enthält den Kubernetes-Master, der *SQL Server-Masterinstanz*, und andere Dienste Cluster-, z. B. die Hive-Metastore und den Spark-Treiber.

### <a id="computeplane"></a> Compute-Ebene

Die Compute-Ebene enthält die Compute-Ressourcen für den Cluster. Knoten mit SQL Server auf Linux-Pods enthält. Die Pods in der Compute-Ebene sind unterteilt in *computepools* für bestimmte Verarbeitungsaufgaben. Ein Compute-Pool kann als eine [PolyBase](../relational-databases/polybase/polybase-guide.md) Erweiterungsgruppe für verteilte Abfragen in verschiedenen Datenquellen – z. B. HDFS, Oracle, MongoDB oder Teradata.

### <a id="dataplane"></a> Datenebene

Die Datenebene wird für Dauerhaftigkeit von Daten und Zwischenspeichern verwendet. Sie enthält die Datenpool SQL und Storage-Knoten.  Pool für die SQL-Daten besteht aus einem oder mehreren Knoten, die SQL Server unter Linux ausgeführt wird. Es wird zum Erfassen von Daten aus SQL-Abfragen oder Spark-Aufträgen. SQL Server-big Data-cluster Daten, die im Pool Data Marts beibehalten werden. Der Speicherpool besteht aus Speicher, die Knoten des SQL Server unter Linux, Spark und HDFS aus. Alle Speicherknoten in einer SQL Server-big Data-Cluster sind Mitglieder eines Clusters von HDFS.

## <a name="next-steps"></a>Nächste Schritte

SQL Server-big Data-Cluster ist zunächst als eingeschränkte öffentliche Vorschauversion mithilfe der SQL Server 2019 Early Adoption Program verfügbar. Um Zugriff zu beantragen, registrieren [hier](https://aka.ms/eapsignup), und geben Sie Ihr Interesse an, um big Data-Cluster zu versuchen. Microsoft alle Anforderungen selektieren und so bald wie möglich Antworten.