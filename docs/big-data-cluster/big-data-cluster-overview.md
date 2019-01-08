---
title: Was sind big Data-Cluster?
titleSuffix: SQL Server 2019 big data clusters
description: Informationen Sie zu SQL Server-2019 big Data-Clustern (Vorschau), die auf Kubernetes ausgeführt, und geben Sie Optionen für horizontales Skalieren für relationale und HDFS-Daten.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: overview
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: 5a44fe9001b7a3bffb67cb3f213bed2ac1065970
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030044"
---
# <a name="what-are-sql-server-2019-big-data-clusters"></a>Was sind SQL Server-2019 big Data-Cluster?

Beginnend mit [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)], SQL Server-big Data-Cluster können Sie skalierbare HDFS, Spark und SQL Server-Container unter Kubernetes-Cluster bereitstellen. Diese Komponenten werden parallel ausgeführt, lesen, schreiben und Verarbeiten von big Data aus Transact-SQL oder Spark, kombinieren und analysieren Sie Ihre wertvollen relationale Daten mit hohem Volumen, big Data leicht zu können.

Weitere Informationen zu neuen Features und bekannten Probleme für die neueste Version finden Sie unter den [Anmerkungen zu dieser Version](big-data-cluster-release-notes.md).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="scenarios"></a>Szenarien

SQL Server-big Data-Cluster bieten die Flexibilität bei der Interaktion mit Ihrer big Data. Sie können Daten aus externen Quellen Abfragen, speichern Sie big Data in HDFS, die von SQL Server oder Abfragen von Daten aus mehreren externen Datenquellen durch den Cluster verwaltet werden. Sie können dann die Daten für KI, maschinelles lernen und andere Analyseaufgaben verwenden. Die folgenden Abschnitte enthalten weitere Informationen zu diesen Szenarien.

### <a name="data-virtualization"></a>Datenvirtualisierung

Durch die Nutzung [SQL Server PolyBase](../relational-databases/polybase/polybase-guide.md), SQL Server-big Data-Cluster können Daten aus externen Quellen Abfragen, ohne zu verschieben oder kopieren die Daten. [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] führt neue Connectors zu Datenquellen.

![Datenvirtualisierung](media/big-data-cluster-overview/data-virtualization.png)

### <a name="data-lake"></a>Data lake

Eine SQL Server-big Data-Cluster enthält einen skalierbaren HDFS *Speicherpool*. Dies kann verwendet werden, zum Speichern von big Data und möglicherweise über mehrere externe Quellen erfasst. Sobald der big Data in HDFS in die big Data-Cluster gespeichert sind, können Sie analysieren und die Daten abzufragen und mit Ihren relationalen Daten zu kombinieren.

![Data lake](media/big-data-cluster-overview/data-lake.png)

### <a name="scale-out-data-mart"></a>Scale-Out-Datamart

SQL Server-big Data-Cluster bieten die horizontale Skalierung von COMPUTE- und zur Verbesserung der Leistung der Analyse von Daten. Daten aus einer Vielzahl von Quellen erfasst und verteilt werden können, *Datenpool* Knoten als Cache für die spätere Analyse.

![Datamart](media/big-data-cluster-overview/data-mart.png)

### <a name="integrated-ai-and-machine-learning"></a>Integrierte künstliche Intelligenz und Machine Learning

SQL Server-big Data-Cluster aktivieren, künstliche Intelligenz und Machine learning-Aufgaben für die Daten in HDFS-Speicherpools und die Datenpools. Sie können Spark sowie der integrierten KI-Tools in SQL Server mithilfe von R, Python, Scala und Java verwenden.

![AI und ML](media/big-data-cluster-overview/ai-ml-spark.png)

### <a name="management-and-monitoring"></a>Verwaltung und Überwachung

Verwaltung und Überwachung werden durch eine Kombination von Befehlszeilentools, APIs, ein Administratorportal und dynamische Verwaltungssichten bereitgestellt.

Die [Cluster-Administratorportal](cluster-admin-portal.md) ist eine Weboberfläche, in dem Status und Integrität der Pods im Cluster angezeigt. Darüber hinaus Links zu anderen Dashboards für Log Analytics und Dashboards für die netzwerküberwachung.

Azure Data Studio können eine Vielzahl von Aufgaben für die big Data-Cluster ausführen. Dies erfolgt durch die neue **2019-Erweiterung für SQL Server (Vorschau)**. Diese Erweiterung bietet:

- Integrierten Codeausschnitte für allgemeine Verwaltungsaufgaben.
- Möglichkeit zum Durchsuchen von HDFS, Hochladen von Dateien, Dateien und Verzeichnisse erstellen.
- Möglichkeit zum Erstellen, öffnen, und führen die kompatiblen Jupyter-Notebooks.
- Data Virtualization Assistenten, um die Erstellung von Daten aus externen Quellen zu vereinfachen.

## <a id="architecture"></a> Architektur

Eine SQL Server-big Data-Cluster ist ein Cluster mit Linux-Container, die von orchestriert [Kubernetes](https://kubernetes.io/docs/concepts/).

### <a name="kubernetes-concepts"></a>Kubernetes-Konzepte

Kubernetes ist ein open-Source-containerorchestrator, die containerbereitstellungen je nach Anforderungen skaliert werden kann. In der folgende Tabelle werden einige wichtige Begriffe für Kubernetes definiert:

|||
|--|--|
| **Cluster** | Ein Kubernetes-Cluster ist eine Gruppe von Computern, die als Knoten bezeichnet. Ein Knoten den Cluster steuert und ist den Masterknoten festgelegt; die verbleibenden Knoten sind Worker-Knoten. Der Kubernetes-Master ist verantwortlich für die Verteilung von Arbeit zwischen den Workern sicherzustellen und für die Überwachung der Integrität des Clusters. |
| **Node** | Ein Knoten wird die Anwendungen in Containern ausgeführt. Es kann entweder auf einem physischen Computer oder auf einem virtuellen Computer sein. Ein Kubernetes-Cluster kann es sich um eine Mischung aus physischen Computer und VM-Knoten enthalten. |
| **Pod** | Ein Pod-Typ ist der atomare Bereitstellungseinheit von Kubernetes. Ein Pod-Typ ist eine logische Gruppe von einem oder mehreren Containern – und die zugehörigen Ressourcen zum Ausführen einer Anwendung benötigt. Jedem Pod auf einem Knoten ausgeführt wird; ein Knoten kann einem oder mehreren Pods ausgeführt. Der Kubernetes-Master wird der Knoten im Cluster automatisch Pods zugewiesen. |

In SQL Server-big Data-Cluster ist Kubernetes verantwortlich für den Status der SQL Server-big Data-Cluster. Kubernetes erstellt und konfiguriert die Clusterknoten, weist der Pods zu Knoten und überwacht die Integrität des Clusters.

### <a name="big-data-clusters-architecture"></a>Big Data-Cluster-Architektur

Knoten im Cluster werden in drei logische Ebenen angeordnet: die Steuerungsebene, die Compute-Ebene und die Datenebene. Jede Ebene hat verschiedene Aufgaben im Cluster. Alle Kubernetes-Knoten in einer SQL Server-big Data-Cluster hostet Pods für Komponenten, der mindestens eine Ebene.

![Übersicht über die Architektur](media/big-data-cluster-overview/architecture-diagram-planes.png)

### <a id="controlplane"></a> Steuerungsebene

Die Steuerungsebene ermöglicht eine Verwaltung und Sicherheit für den Cluster. Es enthält den Kubernetes-Master, der *SQL Server-Masterinstanz*, und andere Dienste Cluster-, z. B. die Hive-Metastore und den Spark-Treiber.

### <a id="computeplane"></a> Compute-Ebene

Die Compute-Ebene enthält die Compute-Ressourcen für den Cluster. Knoten mit SQL Server auf Linux-Pods enthält. Die Pods in der Compute-Ebene sind unterteilt in *computepools* für bestimmte Verarbeitungsaufgaben. Ein Compute-Pool kann als eine [PolyBase](../relational-databases/polybase/polybase-guide.md) Erweiterungsgruppe für verteilte Abfragen über verschiedene Quellen wie z. wie HDFS, Oracle, MongoDB oder Teradata.

### <a id="dataplane"></a> Datenebene

Die Datenebene wird für Dauerhaftigkeit von Daten und Zwischenspeichern verwendet. Es enthält die SQL Datenpool und Speicherpool.  Pool für die SQL-Daten bestehen aus einem oder mehreren Pods, die SQL Server unter Linux ausgeführt wird. Es wird zum Erfassen von Daten aus SQL-Abfragen oder Spark-Aufträgen. SQL Server-big Data-cluster Daten, die im Pool Data Marts beibehalten werden. Der Speicherpool besteht aus Storage Pool Pods bestehend aus SQL Server unter Linux, Spark und HDFS. Alle Speicherknoten in einer SQL Server-big Data-Cluster sind Mitglieder eines Clusters von HDFS.

## <a name="next-steps"></a>Nächste Schritte

SQL Server-big Data-Cluster ist zunächst als eingeschränkte öffentliche Vorschauversion mithilfe der SQL Server 2019 Early Adoption Program verfügbar. Um Zugriff zu beantragen, registrieren [hier](https://aka.ms/eapsignup), und geben Sie Ihr Interesse an, um big Data-Cluster zu versuchen. Microsoft alle Anforderungen selektieren und so bald wie möglich Antworten.
