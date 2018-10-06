---
title: Was ist der Speicherpool für SQL Server big Data-Cluster? | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 100ce09f7066a6df33d7b1daaf50db50bda4ed03
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796038"
---
# <a name="what-is-the-sql-server-big-data-clusters-storage-pool"></a>Was ist der Speicherpool für SQL Server big Data-Cluster?

Dieser Artikel beschreibt die Rolle der *SQL Server-Speicherpool* in einer SQL Server-2019 Vorschau Big Data-Cluster. Die folgenden Abschnitte beschreiben die Architektur und die Funktionalität eines SQL-Speicherpools.

## <a name="storage-pool-architecture"></a>Pool-Speicherarchitektur

Der Speicherpool besteht aus Speicher, die Knoten des SQL Server unter Linux, Spark und HDFS aus. Alle Speicherknoten in einem SQL Big Data-Cluster sind Mitglieder eines Clusters von HDFS.

![Pool-Speicherarchitektur](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Zuständigkeiten

Storage-Knoten dienen:

- Datenerfassung über Spark.
- Speicherung von Daten in HDFS (Parquet-Format). HDFS bietet auch die Beständigkeit der Daten, wie Sie HDFS-Daten auf alle Speicherknoten im SQL Big Data-Cluster verteilt werden.
- Der Datenzugriff über Endpunkte mit HDFS und SQL Server.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter der Übersicht über die folgenden:

- [Was ist SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
