---
title: Was sind Datenpools?
titleSuffix: SQL Server big data clusters
description: Erfahren Sie mehr über die Rolle von SQL Server-Datenpools in einem Big Data-Cluster in SQL Server sowie über die Architektur und die Funktionalität eines SQL-Datenpools.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4d9eaba636c2567d60dfc62ce37080717e9c32e9
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680575"
---
# <a name="what-are-data-pools-in-a-sql-server-big-data-cluster"></a>Was sind Datenpools in einem Big-Data-Cluster für SQL Server?

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel ist die Rolle beschrieben, die *SQL Server-Datenpools* in einem [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] spielen. In den folgenden Abschnitten sind die Architektur und die Funktionalität eines SQL-Datenpools beschrieben.

In diesem fünfminütigen Video werden Datenpools vorgestellt, und es wird gezeigt, wie Sie Daten aus Datenpools abfragen:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Querying-Data-from-Big-Data-Cluster-Data-Pool/player?WT.mc_id=dataexposed-c9-niner]

## <a name="data-pool-architecture"></a>Datenpoolarchitektur

Ein Datenpool besteht aus mindestens einer SQL Server-Datenpoolinstanz. SQL-Datenpoolinstanzen stellen persistenten SQL Server-Speicher für den Cluster bereit. Ein Datenpool wird verwendet, um Daten über SQL-Abfragen oder Spark-Aufträge einzulesen. Um eine bessere Leistung für große Datasets zu ermöglichen, werden Daten in einem Datenpool auf Shards in den zugehörigen SQL-Datenpoolinstanzen verteilt.

## <a name="scale-out-data-marts"></a>Data Marts mit horizontaler Skalierung

Datenpools ermöglichen das Erstellen von Data Marts mit horizontaler Skalierung, über die externe Daten aus mehreren Quellen in den Datenpool eingelesen werden. Da die Daten über die Datenpoolinstanzen verteilt sind, sind parallele Abfragen zu den zusammengestellten Daten effizienter.

![Data Mart mit horizontaler Skalierung](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie in den folgenden Ressourcen:

- [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Workshop: Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]-Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
