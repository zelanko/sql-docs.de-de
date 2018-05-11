---
title: Zusammenfassung der PolyBase-Funktionen mit Versionsangabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: polybase
ms.reviewer: ''
ms.suite: sql
ms.technology: database
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 589a9747347fb19a28488999d0eecd25af7de8bc
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="polybase-versioned-feature-summary"></a>Zusammenfassung der PolyBase-Funktionen mit Versionsangabe
[!INCLUDE[appliesto-ss2016-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-all-md.md)]
Zusammenfassung der PolyBase-Funktionen, die für SQL Server-Produkte und -Dienste verfügbar sind.  
  
## <a name="feature-summary-for-product-releases"></a>Zusammenfassung der Funktionen für Produktversionen  
 In dieser Tabelle sind die wichtigsten Funktionen für PolyBase sowie die Produkte zusammengefasst, in denen sie verfügbar sind.  
  
||||||
|-|-|-|-|-|   
|**Feature**|**SQL Server 2016**|**Azure SQL-Datenbank**|**Azure SQL Data Warehouse**|**Parallel Data Warehouse**| 
|Hadoop-Daten abfragen mit [!INCLUDE[tsql](../../includes/tsql-md.md)]|Ja|nein|nein|Ja|
|Daten aus Hadoop importieren|Ja|nein|nein|Ja|
|Daten für Hadoop exportieren  |ja|nein|nein| Ja|
|Abfragen, Importieren aus und Exportieren in HDInsights |nein|nein|nein|nein
|Abfrageberechnungen auf Hadoop verlagern|Ja|nein|nein|Ja|  
|Daten aus Azure-BLOB-Speicher importieren|Ja|nein|Ja|Ja| 
|Daten für Azure-BLOB-Speicher exportieren|Ja|nein|Ja|Ja|  
|Daten aus Azure Data Lake Store importieren|nein|nein|Ja|nein|    
|Daten aus Azure Data Lake Store exportieren|nein|nein|Ja|nein|
|PolyBase-Abfragen über Microsoft BI-Tools ausführen|Ja|nein|Ja|Ja|   


## <a name="pushdown-computation-supported-t-sql-operators"></a>Von der Weitergabeberechnung unterstützte T-SQL-Operatoren
In SQL Server und APS können nicht alle T-SQL-Operatoren an den Hadoop-Cluster weitergegeben werden. Die folgende Tabelle listet alle unterstützten und eine Teilmenge der nicht unterstützten Operatoren auf. 

||||
|-|-|-| 
|**Operatortyp**|**Weitergabe an Hadoop möglich**|**Weitergabe an Blob Storage möglich**|
|Spaltenprojektionen|Ja|nein|
|Prädikate|Ja|nein|
|Aggregate|Teilweise|nein|
|Joins zwischen externen Tabellen|nein|nein|
|Joins zwischen externen und lokale Tabellen|nein|nein|
|Sortierungen|nein|nein|

Partielle Aggregation bedeutet, dass eine endgültige Aggregation erfolgen muss, sobald die Daten SQL Server erreichen, aber ein Teil der Aggregation in Hadoop erfolgt. Dies ist eine häufig verwendete Methode zum Berechnen von Aggregationen in MPP-Systemen (Massively Parallel Processing).  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [PolyBase-Leitfaden](../../relational-databases/polybase/polybase-guide.md)  
  
  
