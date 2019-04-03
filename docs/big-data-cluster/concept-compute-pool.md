---
title: Was sind computepools?
titleSuffix: SQL Server big data clusters
description: Dieser Artikel beschreibt den Compute-Pool in einer SQL Server-2019 big Data-Cluster (Vorschau).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: d7965ff1f29310f39fb5b8b5994b3967b928ecde
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860242"
---
# <a name="what-are-compute-pools-in-a-sql-server-big-data-cluster"></a>Was sind computepools in einem SQL Server-big Data-Cluster?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel beschreibt die Rolle des *SQL Server-computepools* in einer SQL Server-2019 Vorschau big Data-Cluster. Computepools geben Compute horizontales hochskalieren von Ressourcen für big Data-Cluster. Die folgenden Abschnitte beschreiben die Architektur und die Funktionalität eines Compute-Pools.

## <a name="compute-pool-architecture"></a>Compute-Pool-Architektur

Ein Compute-Pool besteht aus einem oder mehr compute-Pods im Kubernetes ausgeführt wird. Die automatische Erstellung und Verwaltung von diesen Pods wird vom koordiniert die [SQL Server-Masterinstanz](concept-master-instance.md). Jedem Pod enthält einen Satz von Basisdienste und einer Instanz von SQL Server-Datenbank-Engine.

## <a name="scale-out-groups"></a>Erweiterungsgruppen

Ein Compute-Pool kann als eine PolyBase-Erweiterungsgruppe für verteilte Abfragen in verschiedenen Datenquellen – z. B. HDFS, Oracle, MongoDB oder Terradata fungieren. Big Data-Cluster können mithilfe von Compute-Pods im Kubernetes, automatisieren, erstellen und Konfigurieren von Compute Pods, die für PolyBase-Erweiterungsgruppen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter den folgenden Ressourcen:

- [Was sind SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
- [Workshop: Microsoft SQL Server-big Data-Cluster Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
