---
title: Was ist der Speicherpool?
titleSuffix: SQL Server big data clusters
description: Dieser Artikel beschreibt den Speicherpool in einer SQL Server-2019 big Data-Cluster.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4d1ed459aa44de3855153f4316b82ca77db60049
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67729092"
---
# <a name="what-is-the-storage-pool-sql-server-big-data-clusters"></a>Was ist der Speicher-Pool (SQL Server-big Data-Cluster)?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel beschreibt die Rolle der *SQL Server-Speicherpool* in einer SQL Server-2019 big Data-Cluster (Vorschau). Die folgenden Abschnitte beschreiben die Architektur und die Funktionalität eines SQL-Speicherpools.

## <a name="storage-pool-architecture"></a>Pool-Speicherarchitektur

Der Speicherpool besteht aus Speicher, die Knoten des SQL Server unter Linux, Spark und HDFS aus. Alle Speicherknoten in einer SQL-big Data-Cluster sind Mitglieder eines Clusters von HDFS.

![Pool-Speicherarchitektur](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Zuständigkeiten

Storage-Knoten dienen:

- Datenerfassung über Spark.
- Speicherung von Daten in HDFS (Parquet-Format). HDFS bietet auch die Beständigkeit der Daten, wie Sie HDFS-Daten auf alle Speicherknoten in der SQL-big Data-Cluster verteilt werden.
- Der Datenzugriff über Endpunkte mit HDFS und SQL Server.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter den folgenden Ressourcen:

- [Was sind SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
- [Workshop: Microsoft SQL Server-big Data-Cluster Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
