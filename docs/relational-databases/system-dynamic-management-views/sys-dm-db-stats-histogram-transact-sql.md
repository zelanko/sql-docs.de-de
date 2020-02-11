---
title: sys. dm_db_stats_histogram (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_db_stats_histogram
- sys.dm_db_stats_histogram_TSQL
- dm_db_stats_histogram
- dm_db_stats_histogram_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_stats_histogram dynamic management function
ms.assetid: 1897fd4a-8d51-461e-8ef2-c60be9e563f2
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9e5a79a4ab38fd1cb7d118624fd170219aa90a94
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096251"
---
# <a name="sysdm_db_stats_histogram-transact-sql"></a>sys.dm_db_stats_histogram (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Gibt das Statistik Histogramm für das angegebene Datenbankobjekt (Tabelle oder indizierte Sicht) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der aktuellen Datenbank zurück. Ähnlich wie `DBCC SHOW_STATISTICS WITH HISTOGRAM`.

> [!NOTE] 
> Dieser DMF ist ab [!INCLUDE[ssSQL15](../../includes/ssSQL15-md.md)] SP1 Cu2 verfügbar.

## <a name="syntax"></a>Syntax  
  
```  
sys.dm_db_stats_histogram (object_id, stats_id)  
```  
  
## <a name="arguments"></a>Argumente  
 *object_id*  
 ID des Objekts in der aktuellen Datenbank, für die Eigenschaften einer der enthaltenen Statistiken angefordert werden. *object_id* ist vom Datentyp **int**.  
  
 *stats_id*  
 ID der Statistik für die angegebene *object_id*. Die Statistik-ID kann aus der dynamischen Verwaltungssicht [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) abgerufen werden. *stats_id* ist vom Datentyp **int**.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|object_id |**int**|ID des Objekts (Tabelle oder indizierte Sicht), für das die Eigenschaften des Statistikobjekts zurückgegeben werden sollen.|  
|stats_id |**int**|Die ID des Statistikobjekts. Diese ist innerhalb der Tabelle oder indizierten Sicht eindeutig. Weitere Informationen finden Sie unter [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md).|  
|step_number |**int** |Die Anzahl der Schritte im Histogramm. |
|range_high_key |**sql_variant** |Oberer Spaltengrenzwert für einen Histogrammschritt. Der Spaltenwert wird auch als Schlüsselwert bezeichnet.|
|range_rows |**wirkliche** |Geschätzte Anzahl von Zeilen, deren Spaltenwerte innerhalb eines Histogrammschritts liegen, ohne den oberen Grenzwert. |
|equal_rows |**wirkliche** |Geschätzte Anzahl von Zeilen, deren Spaltenwerte der Obergrenze des Histogrammschritts entsprechen. |
|distinct_range_rows |**BIGINT** |Geschätzte Anzahl von Zeilen mit einem unterschiedlichen Spaltenwert innerhalb eines Histogrammschritts ohne den oberen Grenzwert. |
|average_range_rows |**wirkliche** |Die durchschnittliche Anzahl von Zeilen mit doppelten Spaltenwerten in einem Histogrammschritt, ohne die obere Grenze`RANGE_ROWS / DISTINCT_RANGE_ROWS` ( `DISTINCT_RANGE_ROWS > 0`für). |
  
 ## <a name="remarks"></a>Bemerkungen  
 
 Das Resultset für `sys.dm_db_stats_histogram` gibt Informationen zurück, `DBCC SHOW_STATISTICS WITH HISTOGRAM` die mit vergleichbar `object_id`sind `stats_id`, und `step_number`umfasst auch, und.

 Da es sich `range_high_key` bei der Spalte um einen sql_variant-Datentyp handelt, `CAST` müssen `CONVERT` Sie möglicherweise oder verwenden, wenn ein Prädikat mit einer nicht-Zeichen folgen Konstante verglichen wird.

### <a name="histogram"></a>Histogramm
  
 Ein Histogramm misst die Häufigkeit des Vorkommens für jeden unterschiedlichen Wert in einem Dataset. Der Abfrageoptimierer berechnet ein Histogramm für die Spaltenwerte in der ersten Schlüsselspalte des Statistikobjekts und wählt die Spaltenwerte aus, indem statistische Zeilenstichproben entnommen werden oder indem ein vollständiger Scan aller Zeilen in der Tabelle oder Sicht ausgeführt wird. Wenn das Histogramm anhand einer Gruppe von Zeilenstichproben erstellt wird, handelt es sich bei der gespeicherten Gesamtzahl von Zeilen und unterschiedlichen Werten um Schätzungen, die keine ganzen Zahlen sein müssen.  
  
 Zum Erstellen des Histogramms sortiert der Abfrageoptimierer die Spaltenwerte, berechnet die Anzahl der Werte, die den einzelnen unterschiedlichen Spaltenwerten entsprechen, und aggregiert die Spaltenwerte dann in maximal 200 zusammenhängenden Histogrammschritten. Jeder Schritt enthält einen Bereich von Spaltenwerten gefolgt von einem oberen Spaltengrenzwert. Der Bereich enthält alle möglichen Spaltenwerte zwischen den Begrenzungswerten, ohne die Begrenzungswerte selbst. Der niedrigste der sortierten Spaltenwerte ist der obere Grenzwert für den ersten Histogrammschritt.  
  
 Das folgende Diagramm zeigt ein Histogramm mit sechs Schritten. Der Bereich links vom ersten oberen Grenzwert ist der erste Schritt.  
  
 ![](../../relational-databases/system-dynamic-management-views/media/histogram_2.gif "Histogram")  
  
 Für jeden Histogrammschritt gilt:  
  
-   Eine fett formatierte Zeile stellt den oberen Grenzwert (*range_high_key*) und die Häufigkeit des Vorkommens (*equal_rows*) dar.  
  
-   Der einfarbige Bereich links von *range_high_key* stellt den Bereich der Spaltenwerte und die durchschnittliche Häufigkeit des Vorkommens der einzelnen Spaltenwerte (*average_range_rows*) dar. 
  *average_range_rows* ist für den ersten Histogrammschritt immer 0.  
  
-   Gepunktete Linien stellen die Stichprobenwerte dar, mit denen die Gesamtzahl der unterschiedlichen Werte im Bereich (*DISTINCT_RANGE_ROWS*) und die Gesamtzahl der Werte im Bereich (*RANGE_ROWS*) geschätzt wird. Der Abfrageoptimierer verwendet *range_rows* und *distinct_range_rows*, um *average_range_rows* zu berechnen. Die als Stichprobe entnommenen Werte werden nicht gespeichert.  
  
 Der Abfrageoptimierer definiert die Histogrammschritte gemäß ihrer statistischen Bedeutung. Dabei wird ein Algorithmus für die maximale Differenz verwendet, um die Anzahl der Schritte im Histogramm zu minimieren und gleichzeitig die Differenz zwischen den Begrenzungswerten zu maximieren. Die maximale Anzahl von Schritten ist 200. Die Anzahl von Histogrammschritten kann geringer sein als die Anzahl unterschiedlicher Werte, auch bei Spalten mit weniger als 200 Grenzpunkten. Beispielsweise kann eine Spalte mit 100 unterschiedlichen Werten ein Histogramm mit weniger als 100 Grenzpunkten aufweisen.  
  
## <a name="permissions"></a>Berechtigungen  

Erfordert, dass der Benutzer über SELECT-Berechtigungen für Statistikspalten verfügt, Besitzer der Tabelle oder Mitglied der festen Serverrolle `sysadmin`, der festen Datenbankrolle `db_owner` oder der festen Datenbankrolle `db_ddladmin` ist.

## <a name="examples"></a>Beispiele  

### <a name="a-simple-example"></a>A. Einfaches Beispiel    
Im folgenden Beispiel wird eine einfache Tabelle erstellt und aufgefüllt. Anschließend werden Statistiken für die `Country_Name` Spalte erstellt.

```sql
CREATE TABLE Country
(Country_ID int IDENTITY PRIMARY KEY,
Country_Name varchar(120) NOT NULL);
INSERT Country (Country_Name) VALUES ('Canada'), ('Denmark'), ('Iceland'), ('Peru');

CREATE STATISTICS Country_Stats  
    ON Country (Country_Name) ;  
```   
Der Primärschlüssel belegt `stat_id` die Zahl 1, also `sys.dm_db_stats_histogram` `stat_id` den Wert 2, um das Statistik Histogramm für die `Country` Tabelle zurückzugeben.    
```sql     
SELECT * FROM sys.dm_db_stats_histogram(OBJECT_ID('Country'), 2);
```

### <a name="b-useful-query"></a>B. Hilfreiche Abfrage:   
```sql  
SELECT hist.step_number, hist.range_high_key, hist.range_rows, 
    hist.equal_rows, hist.distinct_range_rows, hist.average_range_rows
FROM sys.stats AS s
CROSS APPLY sys.dm_db_stats_histogram(s.[object_id], s.stats_id) AS hist
WHERE s.[name] = N'<statistic_name>';
```

### <a name="c-useful-query"></a>C. Hilfreiche Abfrage:
Im folgenden Beispiel wird aus der `Country` -Tabelle mit einem Prädikat `Country_Name`für die-Spalte ausgewählt.

```sql  
SELECT * FROM Country 
WHERE Country_Name = 'Canada';
```

Im folgenden Beispiel wird die zuvor erstellte Statistik für Tabelle `Country` und Spalte `Country_Name` für den Histogrammschritt betrachtet, der mit dem Prädikat in der obigen Abfrage übereinstimmt.

```sql  
SELECT ss.name, ss.stats_id, shr.steps, shr.rows, shr.rows_sampled, 
    shr.modification_counter, shr.last_updated, sh.range_rows, sh.equal_rows
FROM sys.stats ss
INNER JOIN sys.stats_columns sc 
    ON ss.stats_id = sc.stats_id AND ss.object_id = sc.object_id
INNER JOIN sys.all_columns ac 
    ON ac.column_id = sc.column_id AND ac.object_id = sc.object_id
CROSS APPLY sys.dm_db_stats_properties(ss.object_id, ss.stats_id) shr
CROSS APPLY sys.dm_db_stats_histogram(ss.object_id, ss.stats_id) sh
WHERE ss.[object_id] = OBJECT_ID('Country') 
    AND ac.name = 'Country_Name'
    AND sh.range_high_key = CAST('Canada' AS CHAR(8));
```
  
## <a name="see-also"></a>Weitere Informationen  
[DBCC-SHOW_STATISTICS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
[Objektbezogene dynamische Verwaltungssichten und -funktionen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)  
[sys.dm_db_stats_properties (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)  
