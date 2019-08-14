---
title: Was ist der Speicherpool?
titleSuffix: SQL Server big data clusters
description: Dieser Artikel enthält die Beschreibung des Speicherpools in einem Big Data-Cluster für SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 58e6f16a088d6dc6c1fc6bd32297e7bd698acbbf
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958657"
---
# <a name="what-is-the-storage-pool-sql-server-big-data-clusters"></a>Was ist der Speicherpool (Big Data-Cluster für SQL Server)?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel ist die Rolle beschrieben, die der *SQL Server-Speicherpool* in einem Big Data-Cluster für SQL Server 2019 (Vorschau) spielt. In den folgenden Abschnitten sind die Architektur und die Funktionalität eines SQL-Speicherpools beschrieben.

## <a name="storage-pool-architecture"></a>Speicherpoolarchitektur

Der Speicherpool besteht aus Speicherknoten, bestehend aus SQL Server für Linux, Spark und HDFS. Alle Speicherknoten in einem Big-Data-Cluster für SQL Server sind Mitglieder eines HDFS-Clusters.

![Speicherpoolarchitektur](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Aufgaben

Speicherknoten werden für folgende Aufgaben verwendet:

- Datenerfassung über Spark.
- Datenspeicherung in HDFS (Parquet-Format). HDFS bietet auch Datenpersistenz, weil HDFS-Daten auf alle Speicherknoten im Big Data-Cluster für SQL Server verteilt werden.
- Datenzugriff über HDFS und SQL Server-Endpunkte.

## <a name="next-steps"></a>Nächste Schritte

In den folgenden Artikeln finden Sie weitere Informationen zu den Big-Data-Clustern für SQL Server:

- [Was sind Big Data-Cluster für SQL Server 2019?](big-data-cluster-overview.md)
- [Workshop: Microsoft SQL Server big data clusters Architecture (Workshop: Big-Data-Cluster für SQL Server – Architektur)](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
