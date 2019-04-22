---
title: Was sind Datenpools?
titleSuffix: SQL Server big data clusters
description: Dieser Artikel beschreibt die Datenpool in einer SQL Server-2019 big Data-Cluster.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 8345ae06280458e7fa479ad95ffa20383e429267
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860121"
---
# <a name="what-are-data-pools-in-a-sql-server-big-data-cluster"></a>Was sind Datenpools in eine SQL Server-big Data-Cluster?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel beschreibt die Rolle des *Daten SQL Server-Ressourcenpools* in einer SQL Server-2019 big Data-Cluster (Vorschau). In den folgenden Abschnitten wird beschrieben, die Architektur und die Funktionalität von einem Pool der SQL-Daten.

## <a name="data-pool-architecture"></a>Data-Pool-Architektur

Ein Datenpool besteht aus einer oder mehreren Pools-Instanzen der SQL Server-Daten. SQL-Pool-Dateninstanzen geben beständigen Speicher von SQL Server für den Cluster. Ein Datenpool wird zum Erfassen von Daten aus SQL-Abfragen oder Spark-Aufträgen verwendet. Um eine bessere Leistung für umfangreiche Datasets bereitzustellen, werden Daten in einem Datenpool in Shards auf Datenmember-SQL-Pool-Instanzen verteilt.

## <a name="scale-out-data-marts"></a>Horizontales Skalieren Datamarts

Datenpools ermöglichen die Erstellung von horizontaler Datamarts, in denen externe Daten aus mehreren Quellen in den Datenpool für die erfasst werden. Da die Daten auf die Daten-poolinstanzen verteilt sind, sind die parallele Abfragen für die ausgewählten Daten effizienter.

![Scale-Out-Datamart](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter den folgenden Ressourcen:

- [Was sind SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
- [Workshop: Microsoft SQL Server-big Data-Cluster Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
