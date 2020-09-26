---
title: Was ist der Speicherpool?
titleSuffix: SQL Server big data clusters
description: Erfahren Sie mehr über die Rolle des SQL Server-Speicherpools in einem Big Data-Cluster in SQL Server 2019 sowie über die Architektur und die Funktionalität eines SQL-Speicherpools.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: fd7a38d555cbf6e2f64743f0907fbfbbdec4d41f
ms.sourcegitcommit: 6f49804b863fed44968ea5829e2c26edc5988468
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87806462"
---
# <a name="what-is-the-storage-pool-big-data-clusters-2019"></a>Was ist der Speicherpool ([!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)])?

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel ist die Rolle beschrieben, die der *SQL Server-Speicherpool* in einem [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] spielt. In den folgenden Abschnitten sind die Architektur und die Funktionalität eines SQL-Speicherpools beschrieben.

## <a name="storage-pool-architecture"></a>Speicherpoolarchitektur

Der Speicherpool besteht aus Speicherknoten, bestehend aus SQL Server für Linux, Spark und HDFS. Alle Speicherknoten in einem Big-Data-Cluster für SQL Server sind Mitglieder eines HDFS-Clusters.

![Speicherpoolarchitektur](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Aufgaben

Speicherknoten werden für folgende Aufgaben verwendet:

- Datenerfassung über Spark.
- Datenspeicherung in HDFS (Parquet-Format und durch Trennzeichen getrenntes Textformat). HDFS bietet auch Datenpersistenz, weil HDFS-Daten auf alle Speicherknoten im Big Data-Cluster für SQL Server verteilt werden.
- Datenzugriff über HDFS und SQL Server-Endpunkte.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie in den folgenden Ressourcen:

- [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Workshop: Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]-Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
