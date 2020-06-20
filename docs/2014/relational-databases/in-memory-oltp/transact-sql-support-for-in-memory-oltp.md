---
title: Transact-SQL-Unterstützung für In-Memory OLTP | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
author: rothja
ms.author: jroth
ms.openlocfilehash: bf3708a258e3bb97231e45b10bea2c59351a06a2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85025492"
---
# <a name="transact-sql-support-for-in-memory-oltp"></a>Transact-SQL-Unterstützung für In-Memory OLTP
  Der Zugriff auf speicheroptimierte Tabellen ist über beliebige Transact-SQL-Abfragen oder DML-Anweisungen (SELECT, INSERT, UPDATE oder DELETE), Ad-hoc-Anweisungen sowie über SQL-Module wie gespeicherte Prozeduren, Tabellenwertfunktionen, Skalarfunktionen, Trigger und Sichten möglich. Weitere Informationen finden [Sie unter Zugreifen auf Speicher optimierte Tabellen mit interpretiertem Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).  
  
 Gespeicherte Prozeduren, die nur auf speicheroptimierte Tabellen verweisen, können systemintern in Computercode kompiliert werden. Dies bietet in der Regel großen Leistungszuwachs über interpretierte (datenträgerbasierte) gespeicherte Prozeduren. Verwenden Sie für einen optimalen Zugriff auf die speicheroptimierten Tabellen die systemintern kompilierten gespeicherten Prozeduren. Weitere Informationen finden Sie unter [Nativ kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md).  
  
 Beim Erstellen oder Ändern von Datenbankobjekten (DDL-Anweisungen) wurden die folgenden Anweisungen geändert:  
  
-   [ALTER DATABASE-Optionen für Dateien und Dateigruppen &#40;Transact-SQL-&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) (siehe `MEMORY_OPTIMIZED_DATA` )  
  
-   [Create Database &#40;SQL Server Transact-SQL-&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) (siehe `MEMORY_OPTIMIZED_DATA` )  
  
-   [CREATE PROCEDURE &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-procedure-transact-sql) (siehe `NATIVE_COMPILATION` , `SCHEMABINDING` , `EXECUTE AS` und `BEGIN ATOMIC` )  
  
-   [CREATE TABLE &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-table-transact-sql) (siehe `MEMORY_OPTIMIZED` ,, `DURABILITY` `BUCKET_COUNT` , `INDEX` und `HASH` )  
  
-   [Create Type &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-type-transact-sql) (siehe `MEMORY_OPTIMIZED` , `BUCKET_COUNT` , `INDEX` und `HASH` )  
  
-   [Deklarieren @local_variable &#40;Transact-SQL-&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) (siehe `NULL`  |  `NOT NULL` )  
  
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
  
  
