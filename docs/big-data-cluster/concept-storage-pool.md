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
ms.openlocfilehash: ead6c2ceeecbdfb3466bd4475978b139a0d2ddde
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652245"
---
# <a name="what-is-the-storage-pool-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Was ist der Speicherpool ([!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)])?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird die Rolle des *SQL Server-Speicherpools* in [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]einer beschrieben. In den folgenden Abschnitten sind die Architektur und die Funktionalität eines SQL-Speicherpools beschrieben.

## <a name="storage-pool-architecture"></a>Speicherpoolarchitektur

Der Speicherpool besteht aus Speicherknoten, bestehend aus SQL Server für Linux, Spark und HDFS. Alle Speicherknoten in einem Big-Data-Cluster für SQL Server sind Mitglieder eines HDFS-Clusters.

![Speicherpoolarchitektur](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Aufgaben

Speicherknoten werden für folgende Aufgaben verwendet:

- Datenerfassung über Spark.
- Datenspeicherung in HDFS (Parquet-Format). HDFS bietet auch Datenpersistenz, weil HDFS-Daten auf alle Speicherknoten im Big Data-Cluster für SQL Server verteilt werden.
- Datenzugriff über HDFS und SQL Server-Endpunkte.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]zu finden Sie in den folgenden Ressourcen:

- [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Workshop: Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] -Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
