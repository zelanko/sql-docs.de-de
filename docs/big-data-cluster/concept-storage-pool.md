---
title: Was ist der Speicherpool?
titleSuffix: SQL Server big data clusters
description: Erfahren Sie mehr über die Rolle des SQL Server-Speicherpools in einem Big Data-Cluster in SQL Server 2019 sowie über die Architektur und die Funktionalität eines SQL-Speicherpools.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 10/01/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e8bc204c3f93d4a4ebbd26876bc8c3e23bad8047
ms.sourcegitcommit: ab9ddcc16fdfc245cf9a49d1e90bb1ffe3958c38
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92914290"
---
# <a name="what-is-the-storage-pool-in-a-sql-server-big-data-cluster"></a>Was ist der Speicherpool in einem SQL Server-Big Data-Cluster?

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel ist die Rolle beschrieben, die der *SQL Server-Speicherpool* in einem SQL Server-Big Data-Cluster spielt. In den folgenden Abschnitten sind die Architektur und die Funktionalität eines Speicherpools beschrieben.

## <a name="storage-pool-architecture"></a>Speicherpoolarchitektur

Der Speicherpool ist der lokale HDFS-Cluster (Hadoop) in einem SQL Server-Big Data-Cluster. Er bietet beständigen Speicher für unstrukturierte und semistrukturierte Daten. Datendateien, z. B. Parquet-Dateien oder durch Trennzeichen getrennte Textdateien, können im Speicherpool gespeichert werden. Für die beständige Speicherung wird jedem Pod im Pool ein persistentes Volume zugeordnet. Der Zugriff auf die Speicherpooldateien ist über [PolyBase](../relational-databases/polybase/polybase-guide.md) in SQL Server oder direkt mithilfe einer Apache Knox Gateway-Instanz möglich.

Ein klassisches HDFS-Setup besteht aus einer Gruppe von Standardhardwarecomputern mit zugeordnetem Speicher. Die Daten werden in Blöcken auf die Knoten verteilt, um Fehlertoleranz und die Verwendung von Parallelverarbeitung zu ermöglichen. Einer der Knoten im Cluster fungiert als Namensknoten und enthält die Metadateninformationen zu den Dateien in den Datenknoten.

![Klassisches HDFS-Setup](media/concept-storage-pool/classic-hdfs-setup.png)

Der Speicherpool besteht aus Speicherknoten, die Mitglieder eines HDFS-Clusters sind. Er führt einen oder mehrere Kubernetes-Pods aus, wobei jeder dieser Pods die folgenden Container hostet:

- Einen Hadoop-Container, der mit einem persistenten Volume (Speicher) verknüpft ist. Alle Container dieses Typs bilden zusammen den Hadoop-Cluster. In diesem Hadoop-Container befindet sich ein YARN-Knotenverwaltungsprozess, der bedarfsgesteuerte Apache Spark-Workerprozesse erstellen kann. Der Spark-Hauptknoten hostet die Container für den Hive-Metastore, den Spark-Verlauf und den YARN-Auftragsverlauf.
- Eine SQL Server-Instanz zum Lesen von Daten aus dem HDFS mithilfe der OpenRowSet-Technologie
- `collectd` zum Erfassen von Metrikdaten
- `fluentbit` zum Erfassen von Protokolldaten

![Speicherpoolarchitektur](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Aufgaben

Speicherknoten werden für folgende Aufgaben verwendet:

- Datenerfassung über Apache Spark
- Datenspeicherung in HDFS (Parquet-Format und durch Trennzeichen getrenntes Textformat). Das HDFS bietet auch Datenbeständigkeit, da HDFS-Daten auf alle Speicherknoten in SQL Server BDC verteilt werden.
- Datenzugriff über HDFS und SQL Server-Endpunkte.

## <a name="accessing-data"></a>Datenzugriff (Accessing data)

Die Hauptmethoden für den Zugriff auf die Daten im Speicherpool sind die folgenden:

- Spark-Aufträge
- Verwendung von externen SQL Server-Tabellen, um das Abfragen der Daten mithilfe von PolyBase-Serverknoten und der SQL Server-Instanzen zu ermöglichen, die auf den HDFS-Knoten ausgeführt werden

Sie können auch Folgendes verwenden, um mit dem HDFS zu interagieren:

- Azure Data Studio.
- [!INCLUDE [azure-data-cli-azdata](../includes/azure-data-cli-azdata.md)].
- kubectl zum Senden von Befehlen an den Hadoop-Container
- HDFS-HTTP-Gateway

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie in den folgenden Ressourcen:

- [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Workshop: Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]-Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
