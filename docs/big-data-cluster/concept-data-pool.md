---
title: Was ist ein Datenpool von SQL big Data-Cluster? | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 3a75f47148ff59d58d0d0d1397ba445b064c028f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796029"
---
# <a name="what-is-a-sql-big-data-clusters-data-pool"></a>Was ist ein Datenpool von SQL big Data-Cluster?

Dieser Artikel beschreibt die Rolle des *Daten SQL Server-Ressourcenpools* in einer SQL Server-2019 Vorschau Big Data-Cluster. In den folgenden Abschnitten wird beschrieben, die Architektur und die Funktionalität von einem Pool der SQL-Daten.

## <a name="data-pool-architecture"></a>Data-Pool-Architektur

Ein Datenpool besteht aus einer oder mehreren Pools-Instanzen der SQL Server-Daten. SQL-Pool-Dateninstanzen geben beständigen Speicher von SQL Server für den Cluster. Ein Datenpool wird zum Erfassen von Daten aus SQL-Abfragen oder Spark-Aufträgen verwendet. Um eine bessere Leistung für umfangreiche Datasets bereitzustellen, werden Daten in einem Datenpool in Shards auf Datenmember-SQL-Pool-Instanzen verteilt.

## <a name="scale-out-data-marts"></a>Horizontales Skalieren Datamarts

Datenpools ermöglichen die Erstellung von horizontaler Datamarts, in denen externe Daten aus mehreren Quellen in den Datenpool für die erfasst werden. Da die Daten auf die Daten-poolinstanzen verteilt sind, sind die parallele Abfragen für die ausgewählten Daten effizienter.

![Scale-Out-Datamart](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter der Übersicht über die folgenden:

- [Was ist SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
