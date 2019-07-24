---
title: Was sind Big Data Cluster?
titleSuffix: SQL Server big data clusters
description: Erfahren Sie mehr über SQL Server 2019 Big Data Cluster (Vorschau), die auf Kubernetes ausgeführt werden, und stellen Sie Optionen für horizontales Skalieren für relationale und HDFS-Daten bereit
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: overview
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0beb4ea57ba6c2591e5b2c06a7775fc2d7e8b26c
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419495"
---
# <a name="what-are-sql-server-big-data-clusters"></a>Was sind SQL Server-Big Data-Cluster?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ab können [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]Sie mit SQL Server Big Data Clustern skalierbare Cluster von SQL Server-, Spark-und HDFS-Containern bereitstellen, die auf Kubernetes ausgeführt werden. Diese Komponenten werden nebeneinander ausgeführt, damit Sie Big Data von Transact-SQL oder Spark lesen, schreiben und verarbeiten können, sodass Sie Ihre wichtigen relationalen Daten mit hohem Volumen Big Data problemlos kombinieren und analysieren können.

Weitere Informationen zu neuen Features und bekannten Problemen bei der neuesten Version finden Sie in den Anmerkungen zu dieser [Version](release-notes-big-data-cluster.md).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="scenarios"></a>Szenarien

SQL Server Big Data Cluster bieten Flexibilität bei der Interaktion mit Ihrem Big Data. Sie können externe Datenquellen Abfragen, Big Data in von SQL Server verwalteten HDFS speichern oder Daten aus mehreren externen Datenquellen über den Cluster Abfragen. Anschließend können Sie die Daten für Ki-, Machine Learning-und andere Analyse Tasks verwenden. In den folgenden Abschnitten finden Sie weitere Informationen zu diesen Szenarien.

### <a name="data-virtualization"></a>Datenvirtualisierung

Durch die Nutzung [SQL Server polybase](../relational-databases/polybase/polybase-guide.md)können SQL Server Big Data Cluster externe Datenquellen Abfragen, ohne die Daten zu verschieben oder zu kopieren. [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]führt neue Connectors für Datenquellen ein.

![Datenvirtualisierung](media/big-data-cluster-overview/data-virtualization.png)

### <a name="data-lake"></a>Data Lake

Ein SQL Server Big Data-Cluster enthält einen skalierbaren HDFS- *Speicherpool*. Dies kann verwendet werden, um Big Data zu speichern, die möglicherweise von mehreren externen Quellen erfasst werden. Sobald die Big Data in HDFS im Big Data Cluster gespeichert ist, können Sie die Daten analysieren und Abfragen und mit ihren relationalen Daten kombinieren.

![Data Lake](media/big-data-cluster-overview/data-lake.png)

### <a name="scale-out-data-mart"></a>Horizontales hochskalieren Data Mart

SQL Server Big Data Cluster bieten COMPUTE-und Speicherkapazitäten für horizontales Skalieren, um die Leistung bei der Analyse von Daten zu verbessern. Daten aus einer Vielzahl von Quellen können erfasst und über *Daten Pool* Knoten hinweg als Cache zur weiteren Analyse verteilt werden.

![Data Mart](media/big-data-cluster-overview/data-mart.png)

### <a name="integrated-ai-and-machine-learning"></a>Integrierte Ki und Machine Learning

SQL Server Big Data Cluster ermöglichen AI-und Machine Learning-Aufgaben für die Daten, die in HDFS-Speicherpools und den Datenpools gespeichert werden. Sie können Spark und integrierte Ki-Tools in SQL Server mithilfe von R, Python, Scala oder Java verwenden.

![Ki und ml](media/big-data-cluster-overview/ai-ml-spark.png)

### <a name="management-and-monitoring"></a>Verwaltung und Überwachung

Verwaltung und Überwachung werden über eine Kombination von Befehlszeilen Tools, APIs, Portalen und dynamischen Verwaltungs Sichten bereitgestellt.

Sie können Azure Data Studio verwenden, um eine Vielzahl von Aufgaben im Big Data Cluster auszuführen. Dies wird durch die neue **SQL Server 2019-Erweiterung (Vorschauversion)** ermöglicht. Diese Erweiterung bietet Folgendes:

- Integrierte Code Ausschnitte für allgemeine Verwaltungsaufgaben.
- Möglichkeit zum Durchsuchen von HDFS, Hochladen von Dateien, Vorschau von Dateien und Erstellen von Verzeichnissen.
- Möglichkeit zum Erstellen, öffnen und Ausführen von jupyter-kompatiblen Notebooks.
- Der datenvirtualisierungsassistent zum Vereinfachen der Erstellung externer Datenquellen.

## <a id="architecture"></a>Architektur

Ein SQL Server Big Data-Cluster ist ein Cluster mit Linux-Containern, die von [Kubernetes](https://kubernetes.io/docs/concepts/)orchestriert werden.

### <a name="kubernetes-concepts"></a>Kubernetes-Konzepte

Kubernetes ist ein Open Source-containerorchestrator, mit dem Sie Container Bereitstellungen nach Bedarf skalieren können. In der folgenden Tabelle sind einige wichtige Kubernetes-Terminologie definiert:

|||
|:--|:--|
| **Cluster** | Ein Kubernetes-Cluster ist eine Gruppe von Computern, die als Knoten bezeichnet werden. Ein Knoten steuert den Cluster und wird als Master Knoten bezeichnet. die verbleibenden Knoten sind workerknoten. Der Kubernetes Master ist für die Verteilung der Arbeit zwischen den Workern und die Überwachung der Integrität des Clusters verantwortlich. |
| **Node** | Ein Knoten führt Container Anwendungen aus. Dabei kann es sich entweder um einen physischen oder einen virtuellen Computer handeln. Ein Kubernetes-Cluster kann eine Mischung aus physischen Computern und virtuellen Maschinen Knoten enthalten. |
| **Pfund** | Ein Pod ist die atomarische Bereitstellungs Einheit von Kubernetes. Ein Pod ist eine logische Gruppe von einem oder mehreren Containern und zugeordneten Ressourcen, die zum Ausführen einer Anwendung erforderlich sind. Jedes pod wird auf einem Knoten ausgeführt. ein Knoten kann einen oder mehrere Pods ausführen. Der Kubernetes-Master weist den Knoten im Cluster automatisch Pods zu. |
| &nbsp; ||

In SQL Server Big Data Clustern ist Kubernetes für den Zustand der SQL Server Big Data Cluster verantwortlich. Kubernetes erstellt und konfiguriert die Cluster Knoten, weist den Knoten Pods zu und überwacht die Integrität des Clusters.

### <a name="big-data-clusters-architecture"></a>Architektur von Big Data-Clustern

Das folgende Diagramm zeigt die Komponenten eines Big Data Clusters für SQL Server.

![Übersicht über die Architektur](media/big-data-cluster-overview/architecture-diagram-overview.png)

### <a id="controlplane"></a>Ern

Der Controller bietet Verwaltungs-und Sicherheitseinstellungen für den Cluster. Sie enthält den Cntrol-Dienst, den Konfigurations Speicher und andere Dienste auf Cluster Ebene, z. b. kibana, grafana und elastische Suche.

### <a id="computeplane"></a>Computepool

Der computepool bietet Rechenressourcen für den Cluster. Sie enthält Knoten, auf denen SQL Server für Linux Pods ausgeführt werden. Die Pods im computepool werden für bestimmte Verarbeitungsaufgaben in *SQL-COMPUTE-Instanzen* unterteilt. 

### <a id="dataplane"></a>Daten Pool

Der Daten Pool wird für Daten Persistenz und Caching verwendet. Der Daten Pool besteht aus mindestens einem Pods, auf dem SQL Server für Linux ausgeführt wird. Sie wird zum Erfassen von Daten aus SQL-Abfragen oder Spark-Aufträgen verwendet. SQL Server Big Data Cluster-Data Marts werden im Daten Pool persistent gespeichert. 

### <a name="storage-pool"></a>Speicherpool

Der Speicherpool besteht aus den Speicherpool-Pods, bestehend aus SQL Server für Linux, Spark und HDFS. Alle Speicher Knoten in einem SQL Server Big Data-Cluster sind Mitglieder eines HDFS-Clusters.

> [!TIP]
> Einen ausführlichen Einblick in Big Data Cluster Architektur und-Installation finden [Sie unter Workshop: Microsoft SQL Server Big Data Cluster Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters).

## <a name="next-steps"></a>Nächste Schritte

SQL Server Big Data Cluster als eine eingeschränkte öffentliche Vorschauversion durch das frühzeitige Einführungsprogramm SQL Server 2019 verfügbar. Um Zugriff anzufordern, registrieren Sie sich [hier](https://aka.ms/eapsignup), und geben Sie Ihr Interesse an, Big Data Cluster zu testen. Microsoft führt alle Anforderungen aus und antwortet so bald wie möglich.
