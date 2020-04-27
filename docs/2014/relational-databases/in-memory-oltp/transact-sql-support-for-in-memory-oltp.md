---
title: Transact-SQL-Unterstützung für In-Memory OLTP | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1db4c6895fb499458c198008319302a25b8cd34b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63156212"
---
# <a name="transact-sql-support-for-in-memory-oltp"></a>Transact-SQL-Unterstützung für In-Memory OLTP
  Der Zugriff auf speicheroptimierte Tabellen ist über beliebige Transact-SQL-Abfragen oder DML-Anweisungen (SELECT, INSERT, UPDATE oder DELETE), Ad-hoc-Anweisungen sowie über SQL-Module wie gespeicherte Prozeduren, Tabellenwertfunktionen, Skalarfunktionen, Trigger und Sichten möglich. Weitere Informationen finden [Sie unter Zugreifen auf Speicher optimierte Tabellen mit interpretiertem Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).  
  
 Gespeicherte Prozeduren, die nur auf speicheroptimierte Tabellen verweisen, können systemintern in Computercode kompiliert werden. Dies bietet in der Regel großen Leistungszuwachs über interpretierte (datenträgerbasierte) gespeicherte Prozeduren. Verwenden Sie für einen optimalen Zugriff auf die speicheroptimierten Tabellen die systemintern kompilierten gespeicherten Prozeduren. Weitere Informationen finden Sie unter [nativ kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md).  
  
 Beim Erstellen oder Ändern von Datenbankobjekten (DDL-Anweisungen) wurden die folgenden Anweisungen geändert:  
  
-   [ALTER DATABASE-Optionen für Dateien und Dateigruppen &#40;Transact-SQL](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) - `MEMORY_OPTIMIZED_DATA`&#41;(siehe)  
  
-   [Create Database &#40;SQL Server Transact-SQL-&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) ( `MEMORY_OPTIMIZED_DATA`siehe)  
  
-   [CREATE PROCEDURE &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-procedure-transact-sql) ( `NATIVE_COMPILATION`siehe `SCHEMABINDING`, `EXECUTE AS`, und `BEGIN ATOMIC`)  
  
-   [CREATE TABLE &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-table-transact-sql) ( `MEMORY_OPTIMIZED`siehe `DURABILITY`, `BUCKET_COUNT`, `INDEX`, und `HASH`)  
  
-   [Create Type &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-type-transact-sql) ( `MEMORY_OPTIMIZED`siehe `BUCKET_COUNT`, `INDEX`, und `HASH`)  
  
-   [Deklarieren @local_variable &#40;Transact-SQL](/sql/t-sql/language-elements/declare-local-variable-transact-sql) -&#41;`NULL`  |  `NOT NULL`(siehe)  
  
 Speicheroptimierte Tabelle unterstützen `PRIMARY KEY`- und `NOT NULL`-Einschränkungen. Informationen zum Implementieren von nicht unterstützten Einschränkungen finden [Sie unter Migrieren von Check-und FOREIGN KEY-Einschränkungen](../../database-engine/migrating-check-and-foreign-key-constraints.md).  
  
 Informationen zu nicht unterstützten Funktionen finden Sie unter [Von In-Memory-OLTP nicht unterstützte Transact-SQL-Konstrukte](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Unterstützte Datentypen](supported-data-types-for-in-memory-oltp.md)  
  
-   [Zugreifen auf speicheroptimierte Tabellen mit interpretiertem Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)  
  
-   [Systemsichten, gespeicherte Prozeduren, DMVs und Wartetypen für In-Memory-OLTP](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [In-Memory-OLTP &#40;in-Memory-Optimierung&#41;](in-memory-oltp-in-memory-optimization.md)   
 [Migrationsprobleme bei nativ kompilierten gespeicherten Prozeduren](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Unterstützte SQL Server Features](unsupported-sql-server-features-for-in-memory-oltp.md)   
 [System intern kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md)  
  
  
