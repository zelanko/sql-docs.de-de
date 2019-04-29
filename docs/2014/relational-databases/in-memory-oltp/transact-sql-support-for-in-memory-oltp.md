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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63156212"
---
# <a name="transact-sql-support-for-in-memory-oltp"></a>Transact-SQL-Unterstützung für In-Memory OLTP
  Der Zugriff auf speicheroptimierte Tabellen ist über beliebige Transact-SQL-Abfragen oder DML-Anweisungen (SELECT, INSERT, UPDATE oder DELETE), Ad-hoc-Anweisungen sowie über SQL-Module wie gespeicherte Prozeduren, Tabellenwertfunktionen, Skalarfunktionen, Trigger und Sichten möglich. Weitere Informationen finden Sie unter [zugreifen auf Speicheroptimierte Tabellen mit interpretiertem Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).  
  
 Gespeicherte Prozeduren, die nur auf speicheroptimierte Tabellen verweisen, können systemintern in Computercode kompiliert werden. Dies bietet in der Regel großen Leistungszuwachs über interpretierte (datenträgerbasierte) gespeicherte Prozeduren. Verwenden Sie für einen optimalen Zugriff auf die speicheroptimierten Tabellen die systemintern kompilierten gespeicherten Prozeduren. Weitere Informationen finden Sie unter [Nativ kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md).  
  
 Beim Erstellen oder Ändern von Datenbankobjekten (DDL-Anweisungen) wurden die folgenden Anweisungen geändert:  
  
-   [ALTER DATABASE File und Filegroup-Optionen &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) (finden Sie unter `MEMORY_OPTIMIZED_DATA`)  
  
-   [CREATE DATABASE &#40;SQL Server Transact-SQL&#41; ](/sql/t-sql/statements/create-database-sql-server-transact-sql) (finden Sie unter `MEMORY_OPTIMIZED_DATA`)  
  
-   [CREATE PROCEDURE &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-procedure-transact-sql) (finden Sie unter `NATIVE_COMPILATION`, `SCHEMABINDING`, `EXECUTE AS`, und `BEGIN ATOMIC`)  
  
-   [CREATE TABLE &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-table-transact-sql) (finden Sie unter `MEMORY_OPTIMIZED`, `DURABILITY`, `BUCKET_COUNT`, `INDEX`, und `HASH`)  
  
-   [CREATE TYPE &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-type-transact-sql) (finden Sie unter `MEMORY_OPTIMIZED`, `BUCKET_COUNT`, `INDEX`, und `HASH`)  
  
-   [Deklarieren Sie @local_variable &#40;Transact-SQL&#41; ](/sql/t-sql/language-elements/declare-local-variable-transact-sql) (finden Sie unter `NULL`  |  `NOT NULL`)  
  
 Speicheroptimierte Tabelle unterstützen `PRIMARY KEY`- und `NOT NULL`-Einschränkungen. Informationen zum Implementieren von nicht unterstützter Einschränkungen finden Sie unter [überprüfen Sie die Migration und Foreign Key-Einschränkungen](../../database-engine/migrating-check-and-foreign-key-constraints.md).  
  
 Informationen zu nicht unterstützten Funktionen finden Sie unter [Von In-Memory-OLTP nicht unterstützte Transact-SQL-Konstrukte](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Unterstützte Datentypen](supported-data-types-for-in-memory-oltp.md)  
  
-   [Zugreifen auf speicheroptimierte Tabellen mit interpretiertem Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)  
  
-   [Systemsichten, gespeicherte Prozeduren, DMVs und Wartetypen für In-Memory-OLTP](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)  
  
## <a name="see-also"></a>Siehe auch  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](in-memory-oltp-in-memory-optimization.md)   
 [Migrationsprobleme bei systemintern kompilierten gespeicherten Prozeduren](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Unterstützte SQL Server-Funktionen](unsupported-sql-server-features-for-in-memory-oltp.md)   
 [Nativ kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md)  
  
  
