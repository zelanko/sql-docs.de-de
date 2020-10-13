---
title: Transact-SQL-Unterstützung für In-Memory OLTP | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über Transact-SQL-Anweisungen, die Syntaxoptionen zur Unterstützung von In-Memory-OLTP enthalten. Außerdem finden Sie hier Links zu weiteren Referenzen über unterstützte Features.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dda00961f4d8aa7a5b220e2794105adbac74793b
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91868253"
---
# <a name="transact-sql-support-for-in-memory-oltp"></a>Transact-SQL-Unterstützung für In-Memory OLTP
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen enthalten Syntaxoptionen, um In-Memory-OLTP zu unterstützen:  
  
-   [ALTER DATABASE-Optionen für Dateien und Dateigruppen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md) (**MEMORY_OPTIMIZED_DATA** hinzugefügt)  
  
-   [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)  
  
-   [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-transact-sql.md) (**MEMORY_OPTIMIZED_DATA** hinzugefügt)  
  
-   [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)  
  
-   [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
  
-   [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)  
  
-   [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)  
  
-   [DEKLARIEREN SIE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
    In einer nativ kompilierten gespeicherten Prozedur können Sie eine Variable als **NOT NULL**deklarieren. Dies ist bei einer regulären gespeicherten Prozedur nicht möglich.  
  
 **AUTO_UPDATE_STATISTICS** kann ab SQL Server 2016 für speicheroptimierte Tabellen **ON** sein. Weitere Informationen finden Sie unter [sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md).  
  
 [SET STATISTICS XML &#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-xml-transact-sql.md) ON wird für nativ kompilierte gespeicherte Prozeduren nicht unterstützt.  
  
 Informationen zu nicht unterstützten Funktionen finden Sie unter [Von In-Memory-OLTP nicht unterstützte Transact-SQL-Konstrukte](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
 Informationen zu unterstützten Konstrukten und nativ kompilierten gespeicherten Prozeduren finden Sie unter [Unterstützte Funktionen für nativ kompilierte T-SQL-Module](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md) und [Unterstützte DDL für nativ kompilierte T-SQL-Module](../../relational-databases/in-memory-oltp/supported-ddl-for-natively-compiled-t-sql-modules.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)   
 [Migrationsprobleme bei systemintern kompilierten gespeicherten Prozeduren](./a-guide-to-query-processing-for-memory-optimized-tables.md)   
 [Nicht unterstützte SQL Server-Funktionen für In-Memory OLTP](../../relational-databases/in-memory-oltp/unsupported-sql-server-features-for-in-memory-oltp.md)   
 [Nativ kompilierte gespeicherte Prozeduren](./a-guide-to-query-processing-for-memory-optimized-tables.md)  
  
