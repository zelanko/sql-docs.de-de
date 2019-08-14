---
title: Was sind Datenpools?
titleSuffix: SQL Server big data clusters
description: Dieser Artikel enthält die Beschreibung eines Datenpools in einem Big Data-Cluster für SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f9355508e4d32dd9a6152781fba325ded2fa7425
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958737"
---
# <a name="what-are-data-pools-in-a-sql-server-big-data-cluster"></a>Was sind Datenpools in einem Big-Data-Cluster für SQL Server?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel ist die Rolle beschrieben, die *SQL Server-Datenpools* in einem Big Data-Cluster für SQL Server 2019 (Vorschau) spielen. In den folgenden Abschnitten sind die Architektur und die Funktionalität eines SQL-Datenpools beschrieben.

## <a name="data-pool-architecture"></a>Datenpoolarchitektur

Ein Datenpool besteht aus mindestens einer SQL Server-Datenpoolinstanz. SQL-Datenpoolinstanzen stellen persistenten SQL Server-Speicher für den Cluster bereit. Ein Datenpool wird verwendet, um Daten über SQL-Abfragen oder Spark-Aufträge einzulesen. Um eine bessere Leistung für große Datasets zu ermöglichen, werden Daten in einem Datenpool auf Shards in den zugehörigen SQL-Datenpoolinstanzen verteilt.

## <a name="scale-out-data-marts"></a>Data Marts mit horizontaler Skalierung

Datenpools ermöglichen das Erstellen von Data Marts mit horizontaler Skalierung, über die externe Daten aus mehreren Quellen in den Datenpool eingelesen werden. Da die Daten über die Datenpoolinstanzen verteilt sind, sind parallele Abfragen zu den zusammengestellten Daten effizienter.

![Data Mart mit horizontaler Skalierung](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>Nächste Schritte

In den folgenden Artikeln finden Sie weitere Informationen zu den Big-Data-Clustern für SQL Server:

- [Was sind Big Data-Cluster für SQL Server 2019?](big-data-cluster-overview.md)
- [Workshop: Microsoft SQL Server big data clusters Architecture (Workshop: Big-Data-Cluster für SQL Server – Architektur)](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
