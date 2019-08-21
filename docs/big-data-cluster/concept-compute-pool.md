---
title: Was sind Computepools?
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird der computepool in [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]einer beschrieben.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6156d23fa55690224cd6df82e5f4bafe10e4d1ab
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653084"
---
# <a name="what-are-compute-pools-in-a-sql-server-big-data-cluster"></a>Was sind Computepools in einem Big-Data-Cluster für SQL Server?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel ist die Rolle beschrieben, die *SQL Server-Computepools* in einem Big Data-Cluster für SQL Server 2019 (Vorschau) spielen. Computepools stellen horizontal skalierbare Computeressourcen für einen Big Data-Cluster bereit. In den folgenden Abschnitten sind die Architektur und die Funktionalität eines Computepools beschrieben.

## <a name="compute-pool-architecture"></a>Computepoolarchitektur

Ein Computepool besteht aus mindestens einem Compute-Pod, der in Kubernetes ausgeführt wird. Das automatisierte Erstellen und Verwalten dieser Pods wird von der [SQL Server-Masterinstanz](concept-master-instance.md) koordiniert. Jeder Pod enthält eine Reihe von Basisdiensten und eine Instanz der SQL Server-Datenbank-Engine.

## <a name="scale-out-groups"></a>Erweiterungsgruppen

Ein Computepool kann als PolyBase-Erweiterungsgruppe für verteilte Abfragen über verschiedene Datenquellen fungieren, etwa HDFS, Oracle, MongoDB oder TerradData. Durch Verwenden von Computepods in Kubernetes können Big Data-Cluster das Erstellen und Konfigurieren von Computepods für PolyBase-Erweiterungsgruppen automatisieren.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]zu finden Sie in den folgenden Ressourcen:

- [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Workshop: Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] -Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
