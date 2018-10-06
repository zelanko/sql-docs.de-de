---
title: Was ist eine Compute-Pool von SQL big Data-Cluster? | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: c17f6ac604edc021299f473137dcf6c5e470e3d4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796656"
---
# <a name="what-is-a-sql-big-data-clusters-compute-pool"></a>Was ist eine Compute-Pool von SQL big Data-Cluster?

Dieser Artikel beschreibt die Rolle des *SQL Server-computepools* in einer SQL Server-2019 Vorschau Big Data-Cluster. Berechnen Sie, dass Pools für horizontales Skalieren von Berechnungsressourcen für einen Big Data-Cluster bereitstellen. Die folgenden Abschnitte beschreiben die Architektur und die Funktionalität eines Compute-Pools.

## <a name="compute-pool-architecture"></a>Compute-Pool-Architektur

Ein Compute-Pool besteht aus einem oder mehr compute-Pods im Kubernetes ausgeführt wird. Die automatische Erstellung und Verwaltung von diesen Pods wird vom koordiniert die [SQL Server-Masterinstanz](concept-master-instance.md). Jedem Pod enthält einen Satz von Basisdienste und einer Instanz von SQL Server-Datenbank-Engine.

> [!NOTE]
> CTP 2.0 unterstützt nur einen einzelnen Compute-Pool pro Cluster.

## <a name="scale-out-groups"></a>Erweiterungsgruppen

Ein Compute-Pool kann als eine PolyBase-Erweiterungsgruppe für verteilte Abfragen in verschiedenen Datenquellen – z. B. HDFS, Oracle, MongoDB oder Terradata fungieren. Big Data-Cluster können mithilfe von Compute-Pods im Kubernetes, automatisieren, erstellen und Konfigurieren von Compute Pods, die für PolyBase-Erweiterungsgruppen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter der Übersicht über die folgenden:

- [Was ist SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
