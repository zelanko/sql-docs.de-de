---
title: sp_createstats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_createstats_TSQL
- sp_createstats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_createstats
ms.assetid: 8204f6f2-5704-40a7-8d51-43fc832eeb54
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0cc6ff854079b740279127000a9edb04552245e1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820553"
---
# <a name="sp_createstats-transact-sql"></a>sp_createstats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Ruft die [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) -Anweisung auf, um einspaltige Statistiken für Spalten zu erstellen, die nicht bereits die erste Spalte in einem Statistik Objekt sind. Das Erstellen von Statistiken für einzelne Spalten erhöht die Anzahl von Histogrammen und kann zur Verbesserung von Kardinalitätsschätzungen, Abfrageplänen und Abfrageleistung führen. Die erste Spalte eines Statistikobjekts verfügt über ein Histogramm, während andere Spalten kein Histogramm enthalten.  
  
 sp_createstats ist für Anwendungen wie Vergleichstests hilfreich, wenn Abfrageausführungszeiten ein kritischer Faktor sind, und es zu lange dauert, bis der Abfrageoptimierer Statistiken für einzelne Spalten generiert hat. In den meisten Fällen ist es nicht erforderlich, sp_createstats zu verwenden; der-Abfrageoptimierer generiert bei Bedarf Statistiken für einzelne Spalten, um Abfrage Pläne zu verbessern, wenn die **AUTO_CREATE_STATISTICS** -Option aktiviert ist.  
  
 Weitere Informationen zu Statistiken finden Sie unter [Statistics](../../relational-databases/statistics/statistics.md). Weitere Informationen zum Erstellen von Statistiken für einzelne Spalten finden Sie in der **AUTO_CREATE_STATISTICS** -Option unter [ALTER DATABASE Set options &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_createstats   
    [   [ @indexonly =   ] { 'indexonly'   | 'NO' } ]   
    [ , [ @fullscan =    ] { 'fullscan'    | 'NO' } ]   
    [ , [ @norecompute = ] { 'norecompute' | 'NO' } ]  
    [ , [ @incremental = ] { 'incremental' | 'NO' } ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @indexonly = ] 'indexonly'`Erstellt Statistiken nur für Spalten, die sich in einem vorhandenen Index befinden und nicht der ersten Spalte in einer Index Definition entsprechen. **indexonly** ist vom Typ **char (9)**. Der Standardwert ist NO.  
  
`[ @fullscan = ] 'fullscan'`Verwendet die [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) -Anweisung mit der **FULLSCAN** -Option. **FULLSCAN** ist vom Typ **char (9)**.  Der Standardwert ist NO.  
  
`[ @norecompute = ] 'norecompute'`Verwendet die [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) -Anweisung mit der **NORECOMPUTE** -Option. **NORECOMPUTE** ist vom Typ **char (12)**.  Der Standardwert ist NO.  
  
`[ @incremental = ] 'incremental'`Verwendet die [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) -Anweisung mit der Option **inkrementelle = on** . **Inkrementell** ist **char (12)**.  Der Standardwert ist NO.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Jedes neue Statistikobjekt hat den gleichen Namen wie die Spalte, für die es erstellt wurde.  
  
## <a name="remarks"></a>Bemerkungen  
 sp_createstats erstellt oder aktualisiert keine Statistiken für Spalten, bei denen es sich um die erste Spalte in einem vorhandenen Statistik Objekt handelt.  Dies umfasst die erste Spalte von Statistiken, die für Indizes erstellt wurden, Spalten mit einspaltigen Statistiken, die mit AUTO_CREATE_STATISTICS Option generiert wurden, und die erste Spalte der Statistik, die mit der CREATE STATISTICS-Anweisung erstellt wurde. sp_createstats erstellt keine Statistiken für die ersten Spalten deaktivierter Indizes, es sei denn, diese Spalte wird in einem anderen aktivierten Index verwendet. sp_createstats erstellt keine Statistiken für Tabellen mit einem deaktivierten gruppierten Index.  
  
 Wenn die Tabelle einen Spaltensatz enthält, werden mit sp_createstats keine Statistiken für Sparsespalten erstellt. Weitere Informationen zu Spalten Sätzen und sparsespalten finden Sie unter Verwenden von Spalten [Sätzen](../../relational-databases/tables/use-column-sets.md) und [Verwenden von sparsespalten](../../relational-databases/tables/use-sparse-columns.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle "db_owner".  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-create-single-column-statistics-on-all-eligible-columns"></a>A. Erstellen von Statistiken für einzelne Spalten für alle geeigneten Spalten  
 Im folgenden Beispiel wird eine Statistik für einzelne Spalten für alle geeigneten Spalten in der aktuellen Datenbank erstellt.  
  
```  
EXEC sp_createstats;  
GO  
```  
  
### <a name="b-create-single-column-statistics-on-all-eligible-index-columns"></a>B. Erstellen von Statistiken für einzelne Spalten für alle geeigneten Indexspalten  
 Im folgenden Beispiel werden Statistiken für einzelne Spalten für alle geeigneten Spalten erstellt, die sich bereits in einem Index befinden und nicht der ersten Spalte im Index entsprechen.  
  
```  
EXEC sp_createstats 'indexonly';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kam](../../relational-databases/statistics/statistics.md)   
 [Erstellen von Statistiken &#40;Transact-SQL-&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL-&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [Aktualisieren von Statistiken &#40;Transact-SQL-&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
