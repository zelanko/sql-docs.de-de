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
ms.custom: seodec18
ms.openlocfilehash: f1e725580c98585ee86b401c0e8c12ea143cdab1
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53207719"
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
