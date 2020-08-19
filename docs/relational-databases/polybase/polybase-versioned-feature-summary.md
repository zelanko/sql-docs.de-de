---
description: Features und Einschränkungen von PolyBase
title: Features und Einschränkungen von PolyBase | Microsoft-Dokumentation
descriptions: This article summarizes PolyBase features available for SQL Server products and services. It lists T-SQL operators supported for pushdown and known limitations.
ms.date: 09/24/2018
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: ''
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4d3d6021b34f5804f33cd784bc9b7fd38c7eb1f5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427992"
---
# <a name="polybase-features-and-limitations"></a>Features und Einschränkungen von PolyBase

[!INCLUDE[appliesto-ss2016-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

In diesem Artikel werden die PolyBase-Features zusammengefasst, die für SQL Server-Produkte und -Dienste verfügbar sind.  
  
## <a name="feature-summary-for-product-releases"></a>Zusammenfassung der Features einzelner Produktreleases

In dieser Tabelle werden die wichtigsten Features für PolyBase sowie die Produkte aufgeführt, in denen diese verfügbar sind.  

|**Feature** |**SQL Server 2016** |**Azure SQL-Datenbank** |**Azure Synapse Analytics** |**Parallel Data Warehouse** |
|---------|---------|---------|---------|---------|
|Hadoop-Daten abfragen mit [!INCLUDE[tsql](../../includes/tsql-md.md)]|Ja|Nein|Nein|Ja|
|Daten aus Hadoop importieren|Ja|Nein|Nein|Ja|
|Daten für Hadoop exportieren  |Ja|Nein|Nein| Ja|
|Abfragen von, Importieren aus und Exportieren in Microsoft Azure HDInsights |Nein|Nein|Nein|Nein
|Abfrageberechnungen auf Hadoop verlagern|Ja|Nein|Nein|Ja|  
|Daten aus Azure Blob Storage importieren|Ja|Nein|Ja|Ja|
|Daten aus Azure Blob Storage exportieren|Ja|Nein|Ja|Ja|  
|Daten aus Azure Data Lake Store importieren|Nein|Nein|Ja|Nein|
|Daten aus Azure Data Lake Store exportieren|Nein|Nein|Ja|Nein|
|PolyBase-Abfragen über Microsoft BI-Tools ausführen|Ja|Nein|Ja|Ja|

## <a name="pushdown-computation-supported-by-t-sql-operators"></a>Von der Weitergabeberechnung unterstützte T-SQL-Operatoren

In SQL Server und APS können nicht alle T-SQL-Operatoren an den Hadoop-Cluster weitergegeben werden. In der folgenden Tabelle werden alle unterstützten und eine Teilmenge der nicht unterstützten Operatoren aufgelistet.

|**Operatortyp** |**Weitergabe an Hadoop möglich** |**Weitergabe an Blob Storage möglich** |
|---------|---------|---------|
|Spaltenprojektionen|Ja|Nein|
|Prädikate|Ja|Nein|
|Aggregate|Teilweise|Nein|
|Joins zwischen externen Tabellen|Nein|Nein|
|Joins zwischen externen und lokalen Tabellen|Nein|Nein|
|Sortierungen|Nein|Nein|

Bei einer partiellen Aggregation muss eine endgültige Aggregation vorhanden sein, nachdem die Daten SQL Server erreicht haben. Ein Teil dieser Aggregation ist in Hadoop verfügbar. Dies ist eine häufig verwendete Methode zum Berechnen von Aggregationen in MPP-Systemen (Massively Parallel Processing = massive Parallelverarbeitung).  

## <a name="known-limitations"></a>Bekannte Einschränkungen

PolyBase weist folgende Einschränkungen auf:

- Damit Sie PolyBase verwenden können, müssen Sie über Berechtigungen auf Systemadministrator- oder CONTROL SERVER-Ebene für die Datenbank verfügen.

- Die maximale Zeilengröße, einschließlich der vollständigen Länge der Spalten mit variabler Länge, darf in SQL Server nicht mehr als 32 KB und in Azure Synapse Analytics nicht mehr als 1 MB betragen.

- Wenn Daten aus SQL Server oder Azure Synapse Analytics in ein ORC-Dateiformat exportiert werden, wird die Anzahl an Spalten mit viel Text möglicherweise eingeschränkt. Es dürfen aufgrund von Java-Fehlermeldungen zu nicht genügend Arbeitsspeicher ggf. nur 50 Spalten vorhanden sein. Exportieren Sie nur eine Teilmenge der Spalten, um dieses Problem zu umgehen.

- PolyBase kann keine Verbindung mit einer Hortonworks-Instanz herstellen, wenn Knox aktiviert ist.

- Wenn Sie Hive-Tabellen mit „transactional = true“ verwenden, kann PolyBase nicht auf die Daten im Verzeichnis der Hive-Tabelle zugreifen.

<!--SQL Server 2016-->
::: moniker range="= sql-server-2016 || =sqlallproducts-allversions"

- [PolyBase wird nicht installiert, wenn Sie einem SQL Server 2016-Failovercluster einen Knoten hinzufügen.](https://support.microsoft.com/help/3173087/fix-polybase-feature-doesn-t-install-when-you-add-a-node-to-a-sql-server-2016-failover-cluster)

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PolyBase finden Sie im [PolyBase-Leitfaden](polybase-guide.md).
