---
title: Was ist der Speicherpool?
titleSuffix: SQL Server big data clusters
description: Dieser Artikel enthält die Beschreibung des Speicherpools in einem Big Data-Cluster für SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 114296d0bad77c3bbbb088feed13bd6a4bd5a074
ms.sourcegitcommit: 594cee116fa4ee321e1f5e5206f4a94d408f1576
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2019
ms.locfileid: "70009334"
---
# <a name="what-is-the-storage-pool-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Was ist der Speicherpool ([!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)])?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

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
