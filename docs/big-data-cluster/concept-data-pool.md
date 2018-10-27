---
title: Was ist ein Datenpool von SQL big Data-Cluster? | Microsoft-Dokumentation
description: Dieser Artikel beschreibt die Datenpool in einer SQL Server-2019 big Data-Cluster.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: bf47aa1734e2b1a849fb8333da9c914ea4244f41
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050763"
---
# <a name="what-is-a-sql-big-data-clusters-data-pool"></a>Was ist ein Datenpool von SQL big Data-Cluster?

Dieser Artikel beschreibt die Rolle des *Daten SQL Server-Ressourcenpools* in einer SQL Server-2019 Vorschau big Data-Cluster. In den folgenden Abschnitten wird beschrieben, die Architektur und die Funktionalität von einem Pool der SQL-Daten.

## <a name="data-pool-architecture"></a>Data-Pool-Architektur

Ein Datenpool besteht aus einer oder mehreren Pools-Instanzen der SQL Server-Daten. SQL-Pool-Dateninstanzen geben beständigen Speicher von SQL Server für den Cluster. Ein Datenpool wird zum Erfassen von Daten aus SQL-Abfragen oder Spark-Aufträgen verwendet. Um eine bessere Leistung für umfangreiche Datasets bereitzustellen, werden Daten in einem Datenpool in Shards auf Datenmember-SQL-Pool-Instanzen verteilt.

## <a name="scale-out-data-marts"></a>Horizontales Skalieren Datamarts

Datenpools ermöglichen die Erstellung von horizontaler Datamarts, in denen externe Daten aus mehreren Quellen in den Datenpool für die erfasst werden. Da die Daten auf die Daten-poolinstanzen verteilt sind, sind die parallele Abfragen für die ausgewählten Daten effizienter.

![Scale-Out-Datamart](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter der Übersicht über die folgenden:

- [Was sind SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
