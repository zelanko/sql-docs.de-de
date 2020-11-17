---
title: Konfigurieren des Clusters
titleSuffix: Configure a SQL Server big data cluster
description: Übersicht über das Konfigurieren eines Big Data-Clusters in SQL Server
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: rahul.ajmera
ms.date: 08/04/2020
ms.topic: overview
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b75f6946af9a13d6a8202c627d4c24a2225a51c1
ms.sourcegitcommit: 4545b502e3cae7136411fd9a7c15450315665f38
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94549988"
---
# <a name="configure-a-sql-server-big-data-cluster"></a>Konfigurieren eines Big Data-Clusters in SQL Server

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Sie können die Eigenschaften für die SQL Server-Masterinstanz, für Apache Spark und Apache Hadoop in Big Data-Clustern in SQL Server 2019 zum Zeitpunkt der Bereitstellung konfigurieren.

Nach der Bereitstellung wird das Ändern der Konfigurationseigenschaften von Big Data-Clustern nicht unterstützt.

## <a name="configuration-scopes"></a>Konfigurationsebenen
Big Data-Cluster können auf zwei Ebenen konfiguriert werden: `service`und `resource`. Auch die Hierarchie der Einstellungen entspricht dieser Reihenfolge, von oben nach unten. BDC-Komponenten übernehmen den Wert der Einstellung auf, der auf der niedrigsten Ebene definiert ist. Wenn die Einstellung nicht auf einer bestimmten Ebene definiert ist, wird der Wert der übergeordneten Ebene übernommen.

Angenommen, Sie möchten die Standardanzahl der Kerne definieren, die der Spark-Treiber im Storage Pool und Sparkhead `resources` verwenden soll. Hierzu stehen zwei Möglichkeiten zur Verfügung: 
- Standardwert für Kerne auf der Dienstebene `Spark` angeben  
- Standardwert für Kerne auf der Ressourcenebene `storage-0` und `sparkhead` angeben

Im ersten Szenario übernehmen alle Ressourcen auf niedrigeren Ebenen des Spark-Diensts (Storage Pool und Sparkhead) *die Standardanzahl der Kerne vom Standardwert des Spark-Diensts*.

Im zweiten Szenario nutzt jede Ressource den auf ihrer jeweiligen Ebene definierten Wert.

Wenn die Standardanzahl von Kernen sowohl auf Dienst- als auch auf Ressourcenebene konfiguriert ist, überschreibt der Wert für die Ressourcenebene den Wert für die Dienstebene, da dies die niedrigste **vom Benutzer konfigurierte** Ebene für die gegebene Einstellung ist.

Spezifische Informationen zur Konfiguration finden Sie in den folgenden entsprechenden Artikeln:

Gewusst wie: 
- [Konfigurieren der Masterinstanz von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](configure-sql-server-master-instance.md)
- [Konfigurieren von Apache Spark und Apache Hadoop in Big Data-Clustern](configure-spark-hdfs.md)

Referenz: 
- [Konfigurationseigenschaften der SQL Server-Masterinstanz](reference-config-master-instance.md)
- [Konfigurationseigenschaften von Apache Spark und Apache Hadoop (HDFS)](reference-config-spark-hadoop.md)
