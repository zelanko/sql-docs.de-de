---
description: STATS_DATE (Transact-SQL)
title: STATS_DATE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STATS_DATE_TSQL
- STATS_DATE
dev_langs:
- TSQL
helpviewer_keywords:
- statistical information [SQL Server], last time updated
- STATS_DATE function
- query optimization statistics [SQL Server], last time updated
- last time statistics updated
- stats update date
ms.assetid: f9ec3101-1e41-489d-b519-496a0d6089fb
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1bc07124925f28ea0114a95ec5a60319bd2112bf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88467828"
---
# <a name="stats_date-transact-sql"></a>STATS_DATE (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt das Datum des letzten Updates für die Statistik einer Tabelle oder indizierten Sicht zurück.  
  
 Weitere Informationen zum Aktualisieren von Statistiken finden Sie unter [Statistik](../../relational-databases/statistics/statistics.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
STATS_DATE ( object_id , stats_id )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *object_id*  
 Die ID der Tabelle oder der indizierten Sicht, die die Statistik beinhaltet.  
  
 *stats_id*  
 Die ID des Statistikobjekts.  
  
## <a name="return-types"></a>Rückgabetypen  
 Gibt **datetime** erfolgreich zurück. Gibt **NULL** zurück, wenn kein statistisches Blob erstellt wurde.  
  
## <a name="remarks"></a>Bemerkungen  
 Systemfunktionen können in der Auswahlliste, in der WHERE-Klausel und überall dort verwendet werden, wo ein Ausdruck verwendet werden kann.  
 
 Das Aktualisierungsdatum für die Statistiken befindet sich gemeinsam mit dem [Histogramm](../../relational-databases/statistics/statistics.md#histogram) und [Dichtevektor](../../relational-databases/statistics/statistics.md#density) nicht in den Metadaten, sondern im [Statistik-Blobobjekt](../../relational-databases/statistics/statistics.md#DefinitionQOStatistics). Wenn für das generieren von Statistikdaten keine Daten gelesen werden, wird das Statistikblob nicht erstellt und das Datum nicht verfügbar gemacht. Dies ist der Fall bei gefilterten Statistiken oder neuen und leeren Tabellen, für die das Prädikat keine Zeilen zurückgibt.
 
 Wenn Statistiken einem Index entsprechen, entspricht der *stats_id*-Wert in der [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)-Katalogsicht dem *index_id*-Wert in der [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)-Katalogsicht.
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle db_owner oder die Berechtigung, Metadaten für die Tabelle oder indizierte Sicht anzuzeigen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-return-the-dates-of-the-most-recent-statistics-for-a-table"></a>A. Zurückgeben der Datumsangaben der letzten Statistik für eine Tabelle  
 Im folgenden Beispiel wird das Datum des letzten Updates für jedes Statistikobjekt in der `Person.Address`-Tabelle zurückgegeben.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_update_date  
FROM sys.stats   
WHERE object_id = OBJECT_ID('Person.Address');  
GO  
```  
  
 Wenn Statistiken einem Index entsprechen, ist der *stats_id*-Wert in der [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)-Katalogsicht der gleiche wie der *index_id*-Wert in der [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)-Katalogsicht. Die folgende Abfrage gibt die gleichen Ergebnisse zurück wie die vorherige Abfrage. Wenn Statistiken keinem Index entsprechen, kommen sie in den sys.stats-Ergebnissen, nicht jedoch in den sys.indexes-Ergebnissen vor.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT name AS index_name,   
    STATS_DATE(object_id, index_id) AS statistics_update_date  
FROM sys.indexes   
WHERE object_id = OBJECT_ID('Person.Address');  
GO  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-learn-when-a-named-statistics-was-last-updated"></a>B. Abrufen des Datums des letzten Updates für eine benannte Statistik  
 Im folgenden Beispiel werden Statistiken für die LastName-Spalte der DimCustomer-Tabelle erstellt. Anschließend wird eine Abfrage ausgeführt, um das Datum der Statistiken anzuzeigen. Danach wird die Statistik aktualisiert und die Abfrage erneut ausgeführt, um das aktualisierte Datum anzuzeigen.  
  
```sql
--First, create a statistics object  
USE AdventureWorksPDW2012;  
GO  
CREATE STATISTICS Customer_LastName_Stats  
ON AdventureWorksPDW2012.dbo.DimCustomer (LastName)  
WITH SAMPLE 50 PERCENT;  
GO  
  
--Return the date when Customer_LastName_Stats was last updated  
USE AdventureWorksPDW2012;  
GO  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer')  
    AND s.name = 'Customer_LastName_Stats';  
GO  
  
--Update Customer_LastName_Stats so it will have a different timestamp in the next query  
GO  
UPDATE STATISTICS dbo.dimCustomer (Customer_LastName_Stats);  
  
--Return the date when Customer_LastName_Stats was last updated.  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer')  
    AND s.name = 'Customer_LastName_Stats';  
GO    
```  
  
### <a name="c-view-the-date-of-the-last-update-for-all-statistics-on-a-table"></a>C. Anzeigen des Datums des letzten Updates für alle Statistiken einer Tabelle  
 In diesem Beispiel wird das Datum des letzten Updates für jedes Statistikobjekt in der DimCustomer-Tabelle zurückgegeben.  
  
```sql  
--Return the dates all statistics on the table were last updated.  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer');  
GO  
```  
  
 Wenn Statistiken einem Index entsprechen, ist der *stats_id*-Wert in der [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)-Katalogsicht der gleiche wie der *index_id*-Wert in der [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)-Katalogsicht. Die folgende Abfrage gibt die gleichen Ergebnisse zurück wie die vorherige Abfrage. Wenn Statistiken keinem Index entsprechen, kommen sie in den sys.stats-Ergebnissen, nicht jedoch in den sys.indexes-Ergebnissen vor.  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
SELECT name AS index_name,   
    STATS_DATE(object_id, index_id) AS statistics_update_date  
FROM sys.indexes   
WHERE object_id = OBJECT_ID('dbo.DimCustomer');  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [Statistiken](../../relational-databases/statistics/statistics.md)    
 [sys.dm_db_stats_properties (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)   
 [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
  
  

