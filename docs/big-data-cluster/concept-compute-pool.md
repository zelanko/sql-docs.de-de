---
title: Was sind Computepools?
titleSuffix: SQL Server big data clusters
description: Dieser Artikel enthält die Beschreibung eines Computepools in einem Big Data-Cluster für SQL Server 2019 (Vorschau).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d9ae112369ddad91bec125ec19713040a5aae915
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958809"
---
# <a name="what-are-compute-pools-in-a-sql-server-big-data-cluster"></a>Was sind Computepools in einem Big-Data-Cluster für SQL Server?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel ist die Rolle beschrieben, die *SQL Server-Computepools* in einem Big Data-Cluster für SQL Server 2019 (Vorschau) spielen. Computepools stellen horizontal skalierbare Computeressourcen für einen Big Data-Cluster bereit. In den folgenden Abschnitten sind die Architektur und die Funktionalität eines Computepools beschrieben.

## <a name="compute-pool-architecture"></a>Computepoolarchitektur

Ein Computepool besteht aus mindestens einem Compute-Pod, der in Kubernetes ausgeführt wird. Das automatisierte Erstellen und Verwalten dieser Pods wird von der [SQL Server-Masterinstanz](concept-master-instance.md) koordiniert. Jeder Pod enthält eine Reihe von Basisdiensten und eine Instanz der SQL Server-Datenbank-Engine.

## <a name="scale-out-groups"></a>Erweiterungsgruppen

Ein Computepool kann als PolyBase-Erweiterungsgruppe für verteilte Abfragen über verschiedene Datenquellen fungieren, etwa HDFS, Oracle, MongoDB oder TerradData. Durch Verwenden von Computepods in Kubernetes können Big Data-Cluster das Erstellen und Konfigurieren von Computepods für PolyBase-Erweiterungsgruppen automatisieren.

## <a name="next-steps"></a>Nächste Schritte

In den folgenden Artikeln finden Sie weitere Informationen zu den Big-Data-Clustern für SQL Server:

- [Was sind Big Data-Cluster für SQL Server 2019?](big-data-cluster-overview.md)
- [Workshop: Microsoft SQL Server big data clusters Architecture (Workshop: Big-Data-Cluster für SQL Server – Architektur)](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
