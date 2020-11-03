---
title: Was sind Computepools?
titleSuffix: SQL Server big data clusters
description: Dieser Artikel enthält die Beschreibung eines Computepools in einem Big Data-Cluster für SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 10/15/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b07b1480412dc8dd67535f58fcc4d223a9e91baa
ms.sourcegitcommit: ab9ddcc16fdfc245cf9a49d1e90bb1ffe3958c38
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92914319"
---
# <a name="what-are-compute-pools-in-a-sql-server-big-data-cluster"></a>Was sind Computepools in einem Big-Data-Cluster für SQL Server?

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel ist die Rolle beschrieben, die *SQL Server-Computepools* in einem Big Data-Cluster für SQL Server spielen. Computepools stellen horizontal skalierbare Computeressourcen für einen SQL Server-Big Data-Cluster bereit. Sie werden verwendet, um Berechnungsarbeit oder Zwischenresultsets aus der SQL Server-Masterinstanz auszulagern. In den folgenden Abschnitten werden die Architektur, die Funktionen und die Nutzungsszenarios eines Computepools beschrieben.

Dieses fünfminütige Video enthält eine Einführung in Computepools:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Overview-Big-Data-Cluster-Compute-Pool/player?WT.mc_id=dataexposed-c9-niner]

## <a name="compute-pool-architecture"></a>Computepoolarchitektur

Ein Computepool besteht aus mindestens einem Compute-Pod, der in Kubernetes ausgeführt wird. Das automatisierte Erstellen und Verwalten dieser Pods wird von der [SQL Server-Masterinstanz](concept-master-instance.md) koordiniert. Jeder Pod enthält eine Reihe von Basisdiensten und eine Instanz der SQL Server-Datenbank-Engine.

![Computepoolarchitektur](media/concept-compute-pool/compute-pool-architecture.png)

## <a name="scale-out-groups"></a>Erweiterungsgruppen

Ein Computepool kann als PolyBase-Erweiterungsgruppe für verteilte Abfragen über verschiedene externe Datenquellen fungieren, etwa SQL Server, Oracle, MongoDB, Teradata und HDFS. Durch Verwenden von Computepods in Kubernetes kann in einem SQL Server-Big Data-Cluster das Erstellen und Konfigurieren von Computepods für PolyBase-Erweiterungsgruppen automatisiert werden.

## <a name="compute-pool-scenarios"></a>Computepoolszenarien

In den folgenden Szenarien werden Computepools verwendet:

- Wenn bei der Masterinstanz eingereichte Abfragen Tabellen verwenden, die sich im [Speicherpool](concept-storage-pool.md) befinden.

- Wenn bei der Masterinstanz eingereichte Abfragen Tabellen verwenden, die sich im [Datenpool](concept-data-pool.md) befinden und Roundrobin-Verteilung verwenden.

- Wenn bei der Masterinstanz eingereichte Abfragen **partitionierte** Tabellen mit externen Datenquellen in SQL Server, Oracle, MongoDB oder Teradata verwenden. Für dieses Szenario muss der Abfragehinweis OPTION (FORCE SCALEOUTEXECUTION) aktiviert sein.

- Wenn bei der Masterinstanz eingereichte Abfragen Tabellen verwenden, die sich im [HDFS-Tiering](hdfs-tiering.md) befinden.

In den folgenden Szenarien werden **keine** Computepools verwendet:

- Wenn bei der Masterinstanz eingereichte Abfragen Tabellen verwenden, die sich in einem externen Hadoop HDFS-Cluster befinden.

- Wenn bei der Masterinstanz eingereichte Abfragen Tabellen verwenden, die sich in Azure Blob Storage befinden.

- Wenn bei der Masterinstanz eingereichte Abfragen **nicht partitionierte** Tabellen mit externen Datenquellen in SQL Server, Oracle, MongoDB oder Teradata verwenden.

- Wenn der Abfragehinweis OPTION (DISABLE SCALEOUTEXECUTION) aktiviert ist.

- Wenn bei der Masterinstanz eingereichte Abfragen sich auf Datenbanken beziehen, die sich auf der Masterinstanz befinden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie in den folgenden Ressourcen:

- [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Workshop: Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]-Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
