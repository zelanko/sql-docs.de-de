---
title: Was ist der Speicherpool?
titleSuffix: SQL Server 2019 big data clusters
description: Dieser Artikel beschreibt den Speicherpool in einer SQL Server-2019 big Data-Cluster.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 7dfb89103bb83fc77c590e5c5b5984cbd96b197d
ms.sourcegitcommit: 715683b5fc7a8e28a86be8949a194226b72ac915
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2019
ms.locfileid: "58477925"
---
# <a name="what-is-the-storage-pool-sql-server-2019-big-data-clusters"></a>Was ist der Speicherpool (SQL Server-2019 big Data-Cluster)?

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
