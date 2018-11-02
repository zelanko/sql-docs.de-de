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
ms.openlocfilehash: 8f7520a4e9bdc346113e4777bd6899f5ccc0e01c
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "49460315"
---
# <a name="polybase-features-and-limitations"></a>Features und Einschränkungen von PolyBase

[!INCLUDE[appliesto-ss2016-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

Zusammenfassung der PolyBase-Funktionen, die für SQL Server-Produkte und -Dienste verfügbar sind.  
  
## <a name="feature-summary-for-product-releases"></a>Zusammenfassung der Funktionen für Produktversionen

In dieser Tabelle sind die wichtigsten Funktionen für PolyBase sowie die Produkte zusammengefasst, in denen sie verfügbar sind.  
  
||||||
|-|-|-|-|-|   
|**Feature**|**SQL Server 2016**|**Azure SQL-Datenbank**|**Azure SQL Data Warehouse**|**Parallel Data Warehouse**| 
|Hadoop-Daten abfragen mit [!INCLUDE[tsql](../../includes/tsql-md.md)]|ja|nein|nein|ja|
|Daten aus Hadoop importieren|ja|nein|nein|ja|
|Daten für Hadoop exportieren  |ja|nein|nein| ja|
|Abfragen, Importieren aus und Exportieren in HDInsights |nein|nein|nein|nein
|Abfrageberechnungen auf Hadoop verlagern|ja|nein|nein|ja|  
|Daten aus Azure-BLOB-Speicher importieren|ja|nein|ja|ja| 
|Daten für Azure-BLOB-Speicher exportieren|ja|nein|ja|ja|  
|Daten aus Azure Data Lake Store importieren|nein|nein|ja|nein|    
|Daten aus Azure Data Lake Store exportieren|nein|nein|ja|nein|
|PolyBase-Abfragen über Microsoft BI-Tools ausführen|ja|nein|ja|ja|   

## <a name="pushdown-computation-supported-t-sql-operators"></a>Von der Weitergabeberechnung unterstützte T-SQL-Operatoren

In SQL Server und APS können nicht alle T-SQL-Operatoren an den Hadoop-Cluster weitergegeben werden. Die folgende Tabelle listet alle unterstützten und eine Teilmenge der nicht unterstützten Operatoren auf. 

||||
|-|-|-| 
|**Operatortyp**|**Weitergabe an Hadoop möglich**|**Weitergabe an Blob Storage möglich**|
|Spaltenprojektionen|ja|nein|
|Prädikate|ja|nein|
|Aggregate|Teilweise|nein|
|Joins zwischen externen Tabellen|nein|nein|
|Joins zwischen externen und lokale Tabellen|nein|nein|
|Sortierungen|nein|nein|

Partielle Aggregation bedeutet, dass eine endgültige Aggregation erfolgen muss, sobald die Daten SQL Server erreichen, aber ein Teil der Aggregation in Hadoop erfolgt. Dies ist eine häufig verwendete Methode zum Berechnen von Aggregationen in MPP-Systemen (Massively Parallel Processing).  

## <a name="known-limitations"></a>Bekannte Einschränkungen

PolyBase weist folgende Einschränkungen auf:

- Die maximale Zeilengröße, einschließlich der vollständigen Länge der Spalten mit variabler Länge, darf in SQL Server nicht mehr als 32 KB und in Azure SQL Data Warehouse nicht mehr als 1 MB betragen.

- PolyBase unterstützt Hive 0.12 und Datentypen (z.B. Char(), VarChar()) nicht.

- Beim Exportieren von Daten aus SQL Server oder Azure SQL Data Warehouse in das Dateiformat ORC können umfangreiche Textspalten wegen Java-Fehlermeldungen aufgrund von nicht ausreichendem Arbeitsspeicher auf höchstens 50 Spalten begrenzt werden. Um das Problem zu umgehen, exportieren Sie nur eine Teilmenge der Spalten.

- Das Lesen oder Schreiben von verschlüsselten Daten im Ruhezustand in Hadoop ist nicht möglich. Dies schließt HDFS Encrypted Zones oder Transparent Encryption ein.

- PolyBase kann sich nicht mit einer Hortonworks-Instanz verbinden, wenn KNOX aktiviert ist.

- Wenn Sie Hive-Tabellen mit „transactional = true“ verwenden, kann PolyBase nicht auf die Daten im Verzeichnis der Hive-Tabelle zugreifen.

<!--SQL Server 2016-->
::: moniker range="= sql-server-2016 || =sqlallproducts-allversions"

- [PolyBase wird nicht installiert, wenn Sie einem SQL Server 2016-Failovercluster einen Knoten hinzufügen.](https://support.microsoft.com/en-us/help/3173087/fix-polybase-feature-doesn-t-install-when-you-add-a-node-to-a-sql-server-2016-failover-cluster)

::: moniker-end

- Integrierte Authentifizierung wird nicht unterstützt. Derzeit werden nur Benutzername und Kennwort unterstützt.  

- Die Verschlüsselung ist standardmäßig aktiviert.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PolyBase finden Sie unter [Was ist PolyBase?](polybase-guide.md).
