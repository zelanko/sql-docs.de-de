---
title: Was sind Datenpools?
titleSuffix: SQL Server 2019 big data clusters
description: Dieser Artikel beschreibt die Datenpool in einer SQL Server-2019 big Data-Cluster.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 906b27c186668518702c7ab3a757e6eeb4e5b278
ms.sourcegitcommit: 715683b5fc7a8e28a86be8949a194226b72ac915
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2019
ms.locfileid: "58478225"
---
# <a name="what-are-data-pools-in-a-sql-server-2019-big-data-cluster"></a>Was sind Datenpools in eine SQL Server-2019 big Data-Cluster?

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
