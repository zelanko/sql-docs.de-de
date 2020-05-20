---
title: Was sind Computepools?
titleSuffix: SQL Server big data clusters
description: Dieser Artikel enthält die Beschreibung eines Computepools in einem Big Data-Cluster für SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: be8766f00a8c6b4d9fd47c976c5a2e1235cacd41
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606342"
---
# <a name="what-are-compute-pools-in-a-sql-server-big-data-cluster"></a>Was sind Computepools in einem Big-Data-Cluster für SQL Server?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel ist die Rolle beschrieben, die *SQL Server-Computepools* in einem Big Data-Cluster für SQL Server spielen. Computepools stellen horizontal skalierbare Computeressourcen für einen Big Data-Cluster bereit. In den folgenden Abschnitten sind die Architektur und die Funktionalität eines Computepools beschrieben.

Dieses fünfminütige Video enthält eine Einführung in Computepools:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Overview-Big-Data-Cluster-Compute-Pool/player?WT.mc_id=dataexposed-c9-niner]


## <a name="compute-pool-architecture"></a>Computepoolarchitektur

Ein Computepool besteht aus mindestens einem Compute-Pod, der in Kubernetes ausgeführt wird. Das automatisierte Erstellen und Verwalten dieser Pods wird von der [SQL Server-Masterinstanz](concept-master-instance.md) koordiniert. Jeder Pod enthält eine Reihe von Basisdiensten und eine Instanz der SQL Server-Datenbank-Engine.

## <a name="scale-out-groups"></a>Erweiterungsgruppen

Ein Computepool kann als PolyBase-Erweiterungsgruppe für verteilte Abfragen über verschiedene Datenquellen fungieren, etwa HDFS, Oracle, MongoDB oder Teradata. Durch Verwenden von Computepods in Kubernetes können Big Data-Cluster das Erstellen und Konfigurieren von Computepods für PolyBase-Erweiterungsgruppen automatisieren.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie in den folgenden Ressourcen:

- [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Workshop: Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]-Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
