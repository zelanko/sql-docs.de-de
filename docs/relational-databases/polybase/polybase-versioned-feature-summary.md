---
title: Features und Einschränkungen von PolyBase | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.technology: polybase
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 08d0b31d5ed0be4b3d9a5e766483f14e0653343e
ms.sourcegitcommit: 41979c9d511b3eeb45134d30ccb0dbc6bba70f1a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50757965"
---
# <a name="polybase-features-and-limitations"></a>Features und Einschränkungen von PolyBase

[!INCLUDE[appliesto-ss2016-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

In diesem Artikel werden die PolyBase-Features zusammengefasst, die für SQL Server-Produkte und -Dienste verfügbar sind.  
  
## <a name="feature-summary-for-product-releases"></a>Zusammenfassung der Features einzelner Produktreleases

In dieser Tabelle werden die wichtigsten Features für PolyBase sowie die Produkte aufgeführt, in denen diese verfügbar sind.  
  
||||||
|-|-|-|-|-|   
|**Feature**|**SQL Server 2016**|**Azure SQL-Datenbank**|**Azure SQL Data Warehouse**|**Parallel Data Warehouse**| 
|Hadoop-Daten abfragen mit [!INCLUDE[tsql](../../includes/tsql-md.md)]|Benutzerkontensteuerung|nein|nein|Benutzerkontensteuerung|
|Daten aus Hadoop importieren|Benutzerkontensteuerung|nein|nein|Benutzerkontensteuerung|
|Daten für Hadoop exportieren  |Benutzerkontensteuerung|nein|nein| Benutzerkontensteuerung|
|Abfragen von, Importieren aus und Exportieren in Microsoft Azure HDInsights |nein|nein|nein|nein
|Abfrageberechnungen auf Hadoop verlagern|Benutzerkontensteuerung|nein|nein|Benutzerkontensteuerung|  
|Daten aus Azure Blob Storage importieren|Benutzerkontensteuerung|nein|Benutzerkontensteuerung|Benutzerkontensteuerung| 
|Daten aus Azure Blob Storage exportieren|Benutzerkontensteuerung|nein|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Daten aus Azure Data Lake Store importieren|nein|nein|Benutzerkontensteuerung|nein|    
|Daten aus Azure Data Lake Store exportieren|nein|nein|Benutzerkontensteuerung|nein|
|PolyBase-Abfragen über Microsoft BI-Tools ausführen|Benutzerkontensteuerung|nein|Benutzerkontensteuerung|Benutzerkontensteuerung|   

## <a name="pushdown-computation-supported-by-t-sql-operators"></a>Von der Weitergabeberechnung unterstützte T-SQL-Operatoren

In SQL Server und APS können nicht alle T-SQL-Operatoren an den Hadoop-Cluster weitergegeben werden. In der folgenden Tabelle werden alle unterstützten und eine Teilmenge der nicht unterstützten Operatoren aufgelistet. 

||||
|-|-|-| 
|**Operatortyp**|**Weitergabe an Hadoop möglich**|**Weitergabe an Blob Storage möglich**|
|Spaltenprojektionen|Benutzerkontensteuerung|nein|
|Prädikate|Benutzerkontensteuerung|nein|
|Aggregate|Teilweise|nein|
|Joins zwischen externen Tabellen|nein|nein|
|Joins zwischen externen und lokalen Tabellen|nein|nein|
|Sortierungen|nein|nein|

Bei einer partiellen Aggregation muss eine endgültige Aggregation vorhanden sein, nachdem die Daten SQL Server erreicht haben. Ein Teil dieser Aggregation ist in Hadoop verfügbar. Dies ist eine häufig verwendete Methode zum Berechnen von Aggregationen in MPP-Systemen (Massively Parallel Processing = massive Parallelverarbeitung).  

## <a name="known-limitations"></a>Bekannte Einschränkungen

PolyBase weist folgende Einschränkungen auf:

- Die maximale Zeilengröße, einschließlich der vollständigen Länge der Spalten mit variabler Länge, darf in SQL Server nicht mehr als 32 KB und in Azure SQL Data Warehouse nicht mehr als 1 MB betragen.

- Wenn Daten aus SQL Server oder SQL Data Warehouse in ein ORC-Dateiformat exportiert werden, wird die Anzahl an Spalten mit viel Text möglicherweise eingeschränkt. Es dürfen aufgrund von Java-Fehlermeldungen zu nicht genügend Arbeitsspeicher ggf. nur 50 Spalten vorhanden sein. Exportieren Sie nur eine Teilmenge der Spalten, um dieses Problem zu umgehen.

- PolyBase kann keine Verbindung mit einer Hortonworks-Instanz herstellen, wenn Knox aktiviert ist.

- Wenn Sie Hive-Tabellen mit „transactional = true“ verwenden, kann PolyBase nicht auf die Daten im Verzeichnis der Hive-Tabelle zugreifen.

<!--SQL Server 2016-->
::: moniker range="= sql-server-2016 || =sqlallproducts-allversions"

- [PolyBase wird nicht installiert, wenn Sie einem SQL Server 2016-Failovercluster einen Knoten hinzufügen.](https://support.microsoft.com/en-us/help/3173087/fix-polybase-feature-doesn-t-install-when-you-add-a-node-to-a-sql-server-2016-failover-cluster)

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PolyBase finden Sie im [PolyBase-Leitfaden](polybase-guide.md).
