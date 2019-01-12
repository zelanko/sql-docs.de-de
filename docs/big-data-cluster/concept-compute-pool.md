---
title: Was sind computepools?
titleSuffix: SQL Server 2019 big data clusters
description: Dieser Artikel beschreibt den Compute-Pool in einer SQL Server-2019 big Data-Cluster (Vorschau).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/07/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: d1e028781735b257b82f839571da5400c36c1e10
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241951"
---
# <a name="what-are-compute-pools-in-a-sql-server-2019-big-data-cluster"></a>Was sind computepools in einem SQL Server-2019 big Data-Cluster?

Dieser Artikel beschreibt die Rolle des *SQL Server-computepools* in einer SQL Server-2019 Vorschau big Data-Cluster. Computepools geben Compute horizontales hochskalieren von Ressourcen für big Data-Cluster. Die folgenden Abschnitte beschreiben die Architektur und die Funktionalität eines Compute-Pools.

## <a name="compute-pool-architecture"></a>Compute-Pool-Architektur

Ein Compute-Pool besteht aus einem oder mehr compute-Pods im Kubernetes ausgeführt wird. Die automatische Erstellung und Verwaltung von diesen Pods wird vom koordiniert die [SQL Server-Masterinstanz](concept-master-instance.md). Jedem Pod enthält einen Satz von Basisdienste und einer Instanz von SQL Server-Datenbank-Engine.

> [!NOTE]
> CTP-Version 2.2 unterstützt nur einen einzelnen Compute-Pool pro Cluster.

## <a name="scale-out-groups"></a>Erweiterungsgruppen

Ein Compute-Pool kann als eine PolyBase-Erweiterungsgruppe für verteilte Abfragen in verschiedenen Datenquellen – z. B. HDFS, Oracle, MongoDB oder Terradata fungieren. Big Data-Cluster können mithilfe von Compute-Pods im Kubernetes, automatisieren, erstellen und Konfigurieren von Compute Pods, die für PolyBase-Erweiterungsgruppen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter der Übersicht über die folgenden:

- [Was sind SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
